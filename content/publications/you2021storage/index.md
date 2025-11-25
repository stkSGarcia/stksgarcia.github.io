---
title: Storage Design of Tracing-logs for Application Performance Management System

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Yong You
  - Hao Wang
  - Tian Ren
  - Shenghui Gu
  - Jialin Sun

# Author notes (optional)
# author_notes:
#   - 'Equal contribution'
#   - 'Equal contribution'

date: "2021-05-01T00:00:00Z"

# Schedule page publish date (NOT publication's date).
# publishDate: '2017-01-01T00:00:00Z'

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ['article-journal']

# Publication name and optional abbreviated publication name.
publication: '_Journal of Software_, 32(5)'
publication_short: ''

abstract: >-
  With the software system becoming more and more complex and distributed, it is more and more important to provide monitoring services with complete functions for the system. APM (application performance management) system analyzes the running state of software by collecting various indicator data of software system, such as CPU, memory utilization, the consuming time of garbage collection, QPS. In addition, the APM system can also generate various types of logs during the operation of the software. Generally speaking, it can provide three types of monitoring data: statistic metrics, tracing data, and discrete event records. The data can help the maintenance personnel of the system or service understand the running state, so as to ensure the stable operation of the system or service. Based on the open-source APM monitoring system (i.e., CAT system), this study proposes a storage design scheme for tracing data. It improves the storage efficiency by memory block which is designed for batch writing logs, and query efficiency by the structure of the two-level index. Through analyzing the real on-line running data, the proposed scheme has sound performance in both write performance and query performance.

# Summary. An optional shortened abstract.
# summary:

tags:
  - Monitoring System
  - Log Storage
  - Two-Level Indexing

# Display this page in the Featured widget?
featured: true

# Standard identifiers for auto-linking
hugoblox:
  ids:
    doi: 10.13328/j.cnki.jos.006234

# Custom links
# links:
#   - type: pdf
#     url: ""
#   - type: code
#     url: https://github.com/HugoBlox/hugo-blox-builder
#   - type: dataset
#     url: https://github.com/HugoBlox/hugo-blox-builder
#   - type: slides
#     url: https://www.slideshare.net/
#   - type: source
#     url: https://github.com/HugoBlox/hugo-blox-builder
#   - type: video
#     url: https://youtube.com

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# image:
#   caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
#   focal_point: ''
#   preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---
