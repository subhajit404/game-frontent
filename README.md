# 🐉 CSS Only — 3D Auto-Rotating Card Slider

A visually stunning **3D circular image carousel** built with **pure HTML & CSS** — no JavaScript required. Cards are arranged in a full 360° ring and spin automatically using CSS animations and 3D transforms.

---

## ✨ Demo Preview

> Cards rotate endlessly in a 3D perspective carousel, showcasing 10 dragon artworks in a mesmerizing infinite loop.

---

## 🚀 Features

- ✅ **Pure CSS Only** — zero JavaScript
- 🔄 **Infinite Auto-Rotation** — smooth `linear infinite` animation
- 🎴 **3D Perspective Transform** — `preserve-3d` + `perspective(1000px)`
- 📐 **Dynamic Card Positioning** — uses CSS custom properties (`--position`, `--quantity`)
- 🖼️ **10 Cards in Full 360° Ring** — evenly distributed using `rotateY` + `translateZ`
- 📱 **Responsive Layout** — centered with `calc(50% - 100px)` positioning

---

## 🗂️ Project Structure

```
📁 project-root/
├── index.html        # Markup — .banner > .slider > .item structure
├── style.css         # All animation & 3D transform logic
└── 📁 images/
    ├── dragon_1.jpg
    ├── dragon_2.jpg
    ├── dragon_3.jpg
    ├── dragon_4.jpg
    ├── dragon_5.jpg
    ├── dragon_6.jpg
    ├── dragon_7.jpg
    ├── dragon_8.jpg
    ├── dragon_9.jpg
    └── dragon_10.jpg
```

---

## 🧱 HTML Structure

```html
<div class="banner">
  <div class="slider">
    <div class="item"><img src="images/dragon_1.jpg" alt=""></div>
    <div class="item"><img src="images/dragon_2.jpg" alt=""></div>
    <div class="item"><img src="images/dragon_3.jpg" alt=""></div>
    <!-- ... up to dragon_10.jpg -->
  </div>
</div>
```

---

## 🎨 CSS Highlights

### Banner & Slider Container

```css
.banner {
  width: 100%;
  height: 100vh;
  text-align: center;
  overflow: hidden;
  position: relative;
}

.banner .slider {
  position: absolute;
  width: 200px;
  height: 250px;
  top: 10%;
  left: calc(50% - 100px);
  transform-style: preserve-3d;
  transform: perspective(1000px);
  animation: autoRun 20s linear infinite;
}
```

### 3D Card Positioning with CSS Custom Properties

```css
.banner .slider .item {
  position: absolute;
  inset: 0 0 0 0;
  transform:
    rotateY(calc((var(--position) - 1) * (360deg / var(--quantity))))
    translateZ(550px);
}
```

Each card gets its position via inline style:

```html
<div class="item" style="--position: 1"> ... </div>
<div class="item" style="--position: 2"> ... </div>
```

And the total count is set on the slider:

```html
<div class="slider" style="--quantity: 10"> ... </div>
```

### Images

```css
.banner .slider .item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

### Keyframe Animation

```css
@keyframes autoRun {
  from {
    transform: perspective(1000px) rotateX(-16deg) rotateY(0deg);
  }
  to {
    transform: perspective(1000px) rotateX(-16deg) rotateY(360deg);
  }
}
```

---

## ⚙️ How the Math Works

Each card is placed at an equal angular interval around the full 360° circle:

```
angle = (position - 1) × (360° ÷ quantity)
```

Combined with `translateZ(550px)`, this pushes each card outward from the center, forming the carousel ring.

---

## 🛠️ Getting Started

1. **Clone or download** this repository
2. Add your images inside the `images/` folder
3. Open `index.html` in your browser — no build tools needed!

```bash
# No installation required — just open in browser
open index.html
```

---

## 🎛️ Customization

| Property | Where | Effect |
|---|---|---|
| `--quantity` | `.slider` inline style | Total number of cards |
| `translateZ(550px)` | `.item` CSS | Radius of the carousel ring |
| `20s` in `animation` | `.slider` CSS | Rotation speed (lower = faster) |
| Card `width` / `height` | `.slider` CSS | Size of each card |
| `rotateX(-16deg)` | `@keyframes` | Tilt angle of the 3D ring |

---

## 🧰 Tech Stack

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

---

## 📺 Tutorial Credit

Based on the tutorial by **[LUN DEV](https://www.youtube.com/@LunDev)** — Web Design Channel.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

> Built with ❤️ using pure CSS — no frameworks, no JavaScript, just the power of modern CSS 3D transforms.
