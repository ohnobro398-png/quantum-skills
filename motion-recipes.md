# Motion Recipes (single file builds)

Paste ready CSS and JS. All recipes respect `prefers-reduced-motion` and touch devices.

## Scroll reveal (no library needed)

```css
.reveal { opacity: 0; translate: 0 24px; transition: opacity .8s ease, translate .8s cubic-bezier(.16,1,.3,1); }
.reveal.in { opacity: 1; translate: 0 0; }
@media (prefers-reduced-motion: reduce) { .reveal { opacity: 1; translate: none; transition: none; } }
```

```js
const io = new IntersectionObserver(es => es.forEach(e => {
  if (e.isIntersecting) { e.target.classList.add('in'); io.unobserve(e.target); }
}), { threshold: 0.15 });
document.querySelectorAll('.reveal').forEach(el => io.observe(el));
```

## Letter roll (nav links, button labels)

```html
<a class="roll" href="#"><span>কাজ</span><span aria-hidden="true">কাজ</span></a>
```

```css
.roll { display: inline-grid; overflow: clip; }
.roll > span { grid-area: 1 / 1; transition: translate .5s cubic-bezier(.165,.84,.44,1); }
.roll > span + span { translate: 0 105%; }
@media (hover: hover) {
  .roll:hover > span { translate: 0 -105%; }
  .roll:hover > span + span { translate: 0 0; }
}
.roll:focus-visible > span { translate: 0 -105%; }
.roll:focus-visible > span + span { translate: 0 0; }
@media (prefers-reduced-motion: reduce) {
  .roll > span { transition: none; translate: none !important; }
  .roll > span + span { visibility: hidden; }
  .roll:focus-visible { text-decoration: underline; text-underline-offset: .2em; }
}
```

## Button fill from pointer side

```html
<a class="btn" href="#" data-fill><span class="btn__fill" aria-hidden="true"></span>শুরু করো</a>
```

```css
.btn { position: relative; isolation: isolate; overflow: clip; transition: color .3s; }
.btn__fill { position: absolute; inset: 0; z-index: -1; background: var(--ink);
  clip-path: circle(0% at 50% 50%); transition: clip-path .5s cubic-bezier(.165,.84,.44,1); }
.btn:active { transform: scale(.97); }
.btn:active .btn__fill { clip-path: circle(150% at 50% 50%); }
@media (hover: hover) { .btn:hover .btn__fill { clip-path: circle(150% at 50% 50%); } }
@media (prefers-reduced-motion: reduce) { .btn__fill { transition: none; } }
```

## Shine CTA sweep

```css
.shine { position: relative; overflow: clip; }
.shine::after { content: ""; position: absolute; inset: 0;
  background: linear-gradient(105deg, transparent 40%, rgba(255,255,255,.5) 50%, transparent 60%);
  translate: -120% 0; }
.shine:hover::after { translate: 120% 0; transition: translate .8s ease; }
@media (prefers-reduced-motion: reduce) { .shine::after { display: none; } }
```

## Underline draw (nav) and rise (inline links)

```css
.draw { background: linear-gradient(currentColor 0 0) left bottom / 0% 2px no-repeat;
  transition: background-size .45s cubic-bezier(.165,.84,.44,1); padding-bottom: 2px; }
@media (hover: hover) { .draw:hover { background-size: 100% 2px; } }
.draw:focus-visible, .draw[aria-current="page"] { background-size: 100% 2px; }

.link { background: linear-gradient(var(--accent) 0 0) left bottom / 100% 2px no-repeat;
  transition: background-size .4s cubic-bezier(.165,.84,.44,1); }
@media (hover: hover) { .link:hover { background-size: 100% 100%; color: var(--ground); } }
@media (prefers-reduced-motion: reduce) { .draw, .link { transition: none; } }
```

## Velocity marquee

```html
<div class="marquee" data-marquee><div class="track" data-track>
  <span>শখবক্স • নতুন কালেকশন • </span><span aria-hidden="true">শখবক্স • নতুন কালেকশন • </span>
</div></div>
```

```css
.marquee { overflow: clip; white-space: nowrap; }
.track { display: inline-flex; animation: slide 22s linear infinite; }
@keyframes slide { to { translate: -50% 0; } }
@media (prefers-reduced-motion: reduce) { .track { animation: none; } }
```

## Animated counter (real numbers only)

```html
<span data-count="350">0</span>
```

```js
document.querySelectorAll('[data-count]').forEach(el => {
  const target = +el.dataset.count;
  const reduce = matchMedia('(prefers-reduced-motion: reduce)').matches;
  if (reduce) { el.textContent = target; return; }
  const t0 = performance.now();
  const tick = t => {
    const p = Math.min((t - t0) / 1400, 1);
    el.textContent = Math.round(target * (1 - Math.pow(1 - p, 4)));
    if (p < 1) requestAnimationFrame(tick);
  };
  new IntersectionObserver((es, o) => es.forEach(e => {
    if (e.isIntersecting) { requestAnimationFrame(tick); o.disconnect(); }
  }), { threshold: 0.5 }).observe(el);
});
```

## GSAP scroll choreography (CDN, for bigger builds)

```html
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/ScrollTrigger.min.js"></script>
```

```js
gsap.registerPlugin(ScrollTrigger);
const reduce = matchMedia('(prefers-reduced-motion: reduce)').matches;
if (!reduce) {
  gsap.utils.toArray('[data-scrub]').forEach(el => {
    gsap.fromTo(el, { y: 60, opacity: 0 },
      { y: 0, opacity: 1, ease: 'none',
        scrollTrigger: { trigger: el, start: 'top 90%', end: 'top 40%', scrub: true } });
  });
}
```

## Rules that keep motion fast

- Animate `translate`, `rotate`, `scale` and `opacity` only. Never animate blur or box shadow on scroll.
- Keep hover styles inside `@media (hover: hover)` and always add a `:focus-visible` twin.
- One signature moment per page. Everything else stays quiet.
