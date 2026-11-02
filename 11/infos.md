# Menu Slide Down

Menu de navigation plein écran qui descend depuis le haut de la page. Exemple adapté de [W3Schools - Fullscreen Overlay Navigation](https://www.w3schools.com/howto/howto_js_fullscreen_overlay.asp) (version « Slide Down »).

### Principe

L'overlay est un bloc en `position: fixed` qui couvre toute la largeur de l'écran. Au départ, sa hauteur est de `0%` : il est invisible. Au clic sur le bouton ☰, JavaScript passe sa hauteur à `100%`. La propriété CSS `transition` anime ce changement, ce qui donne l'effet de descente.

### HTML

Ajoutez le menu et le bouton d'ouverture juste après `<body>` :

```
<div id="myNav" class="overlay">
    <a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>
    <div class="overlay-content">
        <a href="#s01" onclick="closeNav()">Accueil</a>
        <a href="#s02" onclick="closeNav()">Projet</a>
        <a href="#s03" onclick="closeNav()">Citation</a>
        <a href="#s01" onclick="closeNav()">Contact</a>
    </div>
</div>

<span class="openbtn" onclick="openNav()">&#9776;</span>
```

- `&times;` affiche la croix de fermeture, `&#9776;` l'icône hamburger
- Les liens pointent vers les `id` des sections (`#s01`, `#s02`...) et referment le menu au clic

### CSS

```
.overlay {
    height: 0%;
    width: 100%;
    position: fixed;
    z-index: 100;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.9);
    overflow-y: hidden;
    transition: 0.5s;
}
```

- `height: 0%` cache le menu au départ
- `overflow-y: hidden` masque les liens qui dépassent pendant l'animation
- `transition: 0.5s` règle la durée de la descente et de la remontée
- `z-index: 100` place le menu au-dessus du contenu de la page

Le reste du CSS (`.overlay-content`, `.overlay a`, `.closebtn`) met en forme les liens et la croix. Une `@media (max-height: 450px)` réduit la taille des textes sur les écrans de faible hauteur.

### JavaScript

Ajoutez le code ci-dessous avant `</body>` :

```
<script>
    function openNav() {
        document.getElementById("myNav").style.height = "100%";
    }

    function closeNav() {
        document.getElementById("myNav").style.height = "0%";
    }
</script>
```

### Variantes

Sur la page W3Schools, d'autres variantes utilisent le même principe :
- **Slide in** depuis le côté : animer `width` de `0%` à `100%` au lieu de `height`
- **Fade in** : animer `opacity` et `visibility` sans changer la taille
