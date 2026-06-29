---
theme: seriph
addons:
  - "@twitwi/slidev-addon-ultracharger"
addonsConfig:
  ultracharger:
    inlineSvg:
      markersWorkaround: false
    disable:
      - metaFooter
      - tocFooter
background: /logo/mountain.jpg
highlighter: shiki
routerMode: hash
lineNumbers: false

css: unocss
title: CHEP-2026 ML & AI Highlights
subtitle: LAMBDA seminar
date: 29/06/2026
venue: HSE
author: Alexey Boldyrev
---

<br>
<br>

# <span style="font-size:32.0pt" v-html="$slidev.configs.title?.replaceAll(' ', '<br/>')"></span>
# <span style="font-size:26.0pt" v-html="$slidev.configs.subtitle?.replaceAll(' ', '<br/>')"></span>
# <span style="font-size:18.0pt" v-html="$slidev.configs.author?.replaceAll(' ', '<br/>')"></span>

<span style="font-size:18.0pt" v-html="$slidev.configs.date?.replaceAll(' ', '<br/>')"></span>


<style>
  :deep(footer) { padding-bottom: 3em !important; }
</style>


---
src: ./slides/ml_at_chep2026.md
---