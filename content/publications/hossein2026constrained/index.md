---
title: 'Constrained Co-evolutionary Metamorphic Differential Testing for Autonomous Systems with an Interpretability Approach'

# Authors
# If you created a profile for a user (e.g. the default `me` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Hossein Yousefizadeh
  - me
  - Lionel C. Briand
  - Ali Nasr

# Author notes (optional)
author_notes:
  - 'Equal contribution'
  - 'Equal contribution'

date: '2026-05-16T00:00:00Z'

# Schedule page publish date (NOT publication's date).
# publishDate: '2017-01-01T00:00:00Z'

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ['article-journal']

# Publication metadata — structured fields used by citation styles and BibTeX export.
publication:
  name: "ACM Transactions on Software Engineering and Methodology"
  # volume: 0
  # issue: 0

peer_reviewed: true
# open_access: true
# license: CC-BY-4.0

# Awards, honors, and recognitions. Surfaced as badges on the page and in listings.
# Note: a Test of Time award years after publication uses an explicit `date` that differs from the page date.
# awards:
#   - name: "Test of Time Award"
#     level: winner
#     date: "2025"
#     note: "Awarded for sustained impact 10 years after publication."
#   - name: "Editor's Choice"
#     level: featured

# funding:
#   - funder: "National Science Foundation"
#     grant: "NSF-1234567"

abstract: >-
  Autonomous systems, such as autonomous driving systems, evolve rapidly through frequent updates, risking unintended behavioral degradations. Effective system-level testing is challenging due to the vast scenario space, the absence of reliable test oracles, and the need for practically applicable and interpretable test cases. We present CoCoMagic, a novel automated test case generation method that combines metamorphic testing, differential testing, and advanced search-based techniques to identify behavioral divergences between versions of autonomous systems. CoCoMagic formulates test generation as a constrained cooperative co-evolutionary search, evolving both source scenarios and metamorphic perturbations to maximize differences in violations of predefined metamorphic relations across versions. Constraints and population initialization strategies guide the search toward realistic, relevant scenarios. An integrated interpretability approach aids in diagnosing the root causes of divergences. We evaluate CoCoMagic on an end-to-end autonomous driving system, InterFuser, within the Carla virtual simulator. Results show significant improvements over baseline search methods, identifying more distinct high-severity behavioral differences while maintaining scenario realism. The interpretability approach provides actionable insights for developers, supporting targeted debugging and safety assessment. CoCoMagic offers an efficient, effective, and interpretable way for the differential testing of evolving autonomous systems across versions.

# Summary. An optional shortened abstract.
# summary:

tags:
  - Autonomous Driving
  - Metamorphic Testing
  - Differential Testing,
  - Cooperative Co-evolutionary Algorithm
  - Search-based Testing

# Display this page in the Featured widget?
featured: true

# Standard identifiers for auto-linking
hugoblox:
  ids:
    doi: 10.48550/arXiv.2509.16478

# Custom links
# links:
#   - type: pdf
#     url: ""
#   - type: code
#     url: https://github.com/HugoBlox/kit
#   - type: dataset
#     url: https://github.com/HugoBlox/kit
#   - type: slides
#     url: https://www.slideshare.net/
#   - type: source
#     url: https://github.com/HugoBlox/kit
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
