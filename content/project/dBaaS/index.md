---
title: Mini dBaaS for Rideshare APIs
summary: ' '
# tags:
#   - Deep Learning
date: '2021-06-01T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  # caption: Photo by rawpixel on Unsplash
  focal_point: Smart

links:
  - icon: github
    icon_pack: fab
    name: "Github"
    url: "https://github.com/dgdheeraj/Mini-dBaaS"
url_code: ''
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---


A Virtual Machine Instance is used as our Database-as-a-Service, which initially has five containers: 
- Orchestrator
- RabbitMQ 
- Zookeeper,
- Parent
- Child

The Orchestrator itself doesn’t have a database. Each of the Workers (Parent and Child) have their own copy of the database.Orchestrator uses AMQP with RabbitMQ to distribute incoming db requests to master and several slave containers. Four Queues are used for this purpose
- ReadQ
- WriteQ
- SyncQ
- ResponseQ

Orchestrator publishes all db write requests to WriteQ. All db read requests are published to ReadQ using the RPC pattern, which waits for a corresponding reply from ResponseQ.

Parent container consumes messages from WriteQ, and writes them to the database. Then the Parent publishes those messages to SyncQ which is a Fanout exchange. SyncQ is used to synchronise the child's database with parent. All incoming read requests in the orchestrator are saved in a .txt file. When a new child is spawned, its database is
synchronised using get_sql_stmts api in the Orchestrator, which retrieves the saved sql statements, all these statements are written into the database.

Child container consumes messages from ReadQ and SyncQ. All messages from SyncQ fanout exchange are written into the Database.The requests from the ReadQ are consumed by slaves in Round-Robin fashion. All read db requests from ReadQ are executed on the database, and result is sent back on the ResponseQ.

Auto-Scaling is implemented using BackgroundScheduler, which calls a function (auto_scale) every 2 minutes. The scheduler is started after the first Read Request. Scaling Up/Down is performed based on the number of read requests received in the previous interval.

Apache Zookeeper is used to implement Fault Tolerance in Parent and Child containers. A watch is kept on these containers and leader-election is performed if parent container is faulty.