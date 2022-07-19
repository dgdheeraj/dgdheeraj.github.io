---
title: 'Detection of Morphed Face, Body, Audio signals  using Deep Neural Networks'

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - admin
  - Manoj Pissay A
  - Suryanarayan N
  - Srinivas K S

# Author notes (optional)
# author_notes:
#   - 'Equal contribution'
#   - 'Equal contribution'
#   - 'Equal contribution'

date: '2021-04-07T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
# publishDate: '2017-01-01T00:00:00Z'

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ['1']

# Publication name and optional abbreviated publication name.
publication: In *7th International Conference for Convergence in Technology 2022*
publication_short: In *I2CT*

abstract: Deepfakes have been a hot topic in the field of deep learning. It is typically used to alter the face or body of a person to create a fake image or video. With the rise of internet, the number of fake content especially deepfakes have increased exponentially. There have already been cases of these causing conflict and hatred among people. To keep this misinformation regulated, there needs to be a way to distinguish deepfakes from the rest. We therefore have come up with a model to classify deepfakes from pristine, accurately and quickly, so that anyone can upload an image/video to know whether it is genuine or not. The parameters taken into consideration for classifying deepfakes are face, audio and body language. The model for face consists of MMOD-CNN Face detector for pre-processing the input, which is then passed on to a Temporal Convolutional Network (TCN) to predict. For audio deepfake detection, audio converted into a spectrogram is passed to a ResNet50V2 followed by a TCN to predict. The Body Language model uses a vanilla TCN to predict if its a deepfake video or not.

# Summary. An optional shortened abstract.
summary: Implementation of 3 Deep Learning models to classify deepfakes based on face, audio and body language

tags: []

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: 'https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9825423&isnumber=9823960'
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  # caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
  # focal_point: ''
  # preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects:
  - deepfake

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---

<!-- {{% callout note %}}
Click the _Cite_ button above to demo the feature to enable visitors to import publication metadata into their reference management software.
{{% /callout %}} -->

<!-- {{% callout note %}}
Create your slides in Markdown - click the _Slides_ button to check out the example.
{{% /callout %}} -->

<!-- Supplementary notes can be added here, including [code, math, and images](https://wowchemy.com/docs/writing-markdown-latex/). -->
