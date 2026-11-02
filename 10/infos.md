# GSAP

Dessiner une illustration vectorielle (`01.svg`) au fil du défilement avec les plugins **ScrollTrigger** et **DrawSVGPlugin**.

### Mise en place

1. Le code du SVG est collé directement dans `content.html` (une balise `<img>` ne permet pas d'animer les `path`).
2. En CSS, les `path` n'ont pas de remplissage (`fill: transparent`) mais un contour (`stroke`).
3. `gsap.set(".drawing path", { drawSVG: "0%" })` masque tous les contours au départ.
4. Une timeline liée au scroll (`scrub`) dessine les contours de `0%` à `100%`, puis ajoute les remplissages.

```
gsap.registerPlugin(ScrollTrigger, DrawSVGPlugin);

var tl = gsap.timeline({
    scrollTrigger: {
        trigger: "#s02",
        start: "top top",
        end: "+=2000",
        scrub: 1,
        pin: true
    }
});

tl.to(".drawing path", { drawSVG: "100%", stagger: 0.15, ease: "none" });
```

- `pin: true` bloque la section à l'écran pendant le dessin
- `end: "+=2000"` règle la longueur du scroll nécessaire pour finir le dessin
- `stagger` décale le départ de chaque tracé
