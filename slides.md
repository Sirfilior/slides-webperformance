---
theme: default
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: Web Performance
hideInToc: true
---

# Web Performance

Performance messen und verbessern

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
Dominik Albrecht | 15.08.2023
</div>

<!--
Slide note
https://googlechrome.github.io/lighthouse/scorecalc/
https://developer.chrome.com/docs/lighthouse/performance/performance-scoring/?utm_source=lighthouse&utm_medium=lr
-->

---
layout: default
hideInToc: true
---

# Ueberblick

<ul>
<li>Why</li>
<li>StatusQuo</li>
<li>Projektstart</li>
<li>Laufende Projekte</li>
<li class="dev">Metrics</li>
<li class="dev">Tools</li>
<li class="dev">Fragen/Antworten</li>
<li class="dev">Abschluss</li>
</ul>

<div class="abs-br m-6 flex gap-2 dev">
Relevant primaer Entwickler
</div>

<style>
.dev {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #007ecc 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: fade-out
hideInToc: true
---

# Why performance matters 



- 👩‍💼 **Usability** - Jegliches Warten auf einer Seite verschlechtert den Gesamteindruck
- 🚪 **Bounce** - Initial lange Wartezeiten fuehren zu einem Absprung
- 💰 **Conversion** Gerade bei WebShops zeigt sich, dass eine schlechte Performance auch die Konversationsrate negativ beeinflusst
- 🏆 **Image** - Kunden der Intesim verstehen unter Qualitaet auch eine gut performende Applikation
- 🤖 **SEO** - Schlechte Page-Metrics tragen zu einem verschlechtert Ranking bei Suchmaschine bei
- 📱 **Mobile** - Auch heute sind teils mobile Netze beschraenkt. Speed kann limitiert sein, oder teils kostet sogar der Datentransfer

<br>
<br>

Web Performance ist ein wichtiger Bestandteil einer qualitativ hochvertigen Loesung.
<!--
Notes
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #007ecc 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
here is another comment.
-->


---

# StatusQuo

Optimale Ergebnisse sind mit unserer aktuellen Arbeitsweise schwierig zu erzielen.

![Local Image](/bad.png)

Primaere Ursachen davon sind:
- 🏞️ **Bilder** - Bilder, geraude aus einem CMS, sind oft nicht optimiert.
- 📦 **JS Bundles** - Zu grosse und nicht optimierte JS Bundles laden lange, sind aber viel noch wichtiger ein Treiber der [T]ime[T]o[I]nteractive
- 🧮 **Server** - Server Responses teils langsam und nicht genuegend cecached

---

# Projektstart

Pro Projekt muss ein klares Ziel hinsichtlich Performance festgelegt werden. Dabei sind vorallem die Anwendungdzwecke ausschlaggebend.

![Local Image](/overview.png)


<!--
Was soll die Seite erreichen?
Was ist unser Target?
Wichtig immre bei der Umsetzung daran zu denken
-->

---

# Laufende Projekte

- Keine Garantie auf eine fixe Performance Zahl
- Seiten sind zu unterschiedlich, und werden zu stark durch den Kunden beeinflusst 
- Best-Effort wichtig, da wir unserem Image gerecht werden wollen
- Optimierungen auf unserer Seite sind oft nicht mit viel Aufwand verbunden. Und koennen gut bei Weiterentwicklungen eingebracht werden..
- Das sind zum Beispiel: <span class="hl hl1">Moderne Bildformate(webp)</span>, Bilder korrekt aus <span class="hl hl2">CMS verkleinern/optimieren</span>, Javascript Build verbessern. <span class="hl hl3">Caching</span> evaluieren

<style>
.hl {
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
.hl1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #db37d3 10%, #fa00ee 20%);
}
.hl2 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #de8116 10%, #f09c3c 20%);
}
.hl3 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #7f40c7 10%, #a35ef2 20%);
}
</style>

---
transition: slide-up
layout: cover
---

# Metrics: Overview

![Local Image](/metrics.png)

<style>
img {
  filter: brightness(1.5);
}
</style>

---
transition: slide-up
---

# Metrics: Key-Metrics

Wichtigste Page-Speed Metrics gemessen in Lighthouse

### Lighthouse Key-Metrics

|     |     |
| --- | --- |
| FCP| Erste Elemente werden auf der Website dargestellt  |
| LCP| Generelle Ladezeit. Hauptinhalt fertig geladen |
| TTI| Zeit ab Ladestart bis UserInput normal verarbeitet wird.  (No long tasks / main thread clear)|
| TBT | Totale Zeit, in welcher der main thread blockier ist |
| CLS| Stabilitaet des Seitenaufbaus |

---
transition: slide-up
---

# First Contentful Paint (FCP)

Benutzer sieht erste Rueckmeldung vom Server

<img src="/fcp.svg" class="h-40 rounded shadow" />

Main dirvers
- **Render Blocking Resources** - Rendering kann erst nach diesen geladenen Res gestartet werden
- **Server Response** - Schnelle Server Response wichtig fuer FCP bei SSR
- **Keine Preloads** - Fetches werden direkt gestartet. Gewinn = Execution Time VOR fetch
- **CSS Persing** - In Praxis Impact oft klein, allerdings auch einfach optimiert
- **Static Assets** - Caching und Edge CDN extremes Potenzial.

---
transition: slide-up
---

# Largest Contentful Paint (LCP)

Hauptinhalt geladen. Benutzer nimmt die Seite als "ready" war.

<div grid="~ cols-2 gap-2" m="-t-2">

<img border="rounded" src="/lcp.svg">

<img border="rounded" src="/lcprender.avif">

</div>

Debuggen von FCP und LCP
- Performance Waterfall in DevTools

---
transition: slide-up
---

# Time To Interactive (TTI)

Unterschied von Seite visuall ready zu bedienbar

<div style="background: white;">
<img src="/tti.svg" class="h-60 rounded shadow" />
</div>

**Wird hauptsaechlich durch JS verlangsamt!**


---
transition: slide-up
---

# Total Blocking Time (TBT)

Unterschied von Seite visuall ready zu bedienbar

<div style="background: white;">
<img src="/tbt.svg" class="h-60 rounded shadow" />
</div>

- Tasks > 50ms sind "blocking". User Inputs werden delayed
- TTI Unterschied 

---
transition: slide-up
---

# Cumulative Layout Shift (CLS)

Was ist LCP

![Local Image](/bad.png)

Main dirvers
- **Bilder** - Bilder, geraude aus einem CMS, sind oft nicht optimiert.


---
layout: iframe

# the web page source
url: https://googlechrome.github.io/lighthouse/scorecalc/
---

# Tools - Scoring

---
layout: image-right
image: /lighthouse.jpg
transition: slide-up
---

# Tools - Lighthouse & Pagespeed

Erste Anlaufstelle fuer Messungen

Lighthosue DevTools

[PageSpeed](https://pagespeed.web.dev/analysis/https-www-mpk-ch/g5v09db74p?form_factor=mobile)

---
layout: image-right
transition: slide-up
image: /ulh-side.png
---

# Tools - Unlighthouse

Unlighthouse zum kompletten Website Scan

```bash
npx unlighthouse --site https://mpk.ch
```

---
transition: slide-up
---

# Tools - WebVitals Extension

Extension praktisch fuer debugging

```bash
vitals.js:234 [Web Vitals Extension] LCP 327 ms (good)
vitals.js:234 [Web Vitals Extension] FCP 327 ms (good)
vitals.js:234 [Web Vitals Extension] TTFB 178 ms (good)
vitals.js:234 [Web Vitals Extension] CLS 0.00 (good)
```

---

# Tools -  PerformanceTools

Performance und Exp. Recorder&PerfInsights

![Local Image](/devtools.png)

---
class: px-20
---

# Themes

Slidev comes with powerful theming support. Themes can provide styles, layouts, components, or even configurations for tools. Switching between themes by just **one edit** in your frontmatter:

<div grid="~ cols-2 gap-2" m="-t-2">

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true">

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-seriph/01.png?raw=true">

</div>

Read more about [How to use a theme](https://sli.dev/themes/use.html) and
check out the [Awesome Themes Gallery](https://sli.dev/themes/gallery.html).

---
preload: false
---

# Animations

Animations are powered by [@vueuse/motion](https://motion.vueuse.org/).

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }">
  Slidev
</div>
```

<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

<div
  v-motion
  :initial="{ x:35, y: 40, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn More](https://sli.dev/guide/animations.html#motion)

</div>

---
layout: center
class: text-center
---

# Interne Links

[Testprozess](https://web.dev/metrics/) · [Blogartikel](https://unlighthouse.dev/) 

---
layout: fact
class: text-center
---

# Learn More

[Metrics by Google](https://web.dev/metrics/) · [LighthouseScore](https://googlechrome.github.io/lighthouse/scorecalc/) · [UnLighthouse](https://unlighthouse.dev/) · [WebVitals Ext](https://chrome.google.com/webstore/detail/web-vitals/ahfhijdlegdabablpippeagghigmibma)
