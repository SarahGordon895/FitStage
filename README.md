# FitStage

**The layout you designed for the computer is the layout every device sees.**

FitStage is a drop-in package from [TechMorah Solution LTD](https://techmorahsolutionltd.org) for websites, portals, admin systems, and web apps. It stops phones and tablets from crushing a designed UI into a tall single column. Instead, it keeps the **same placement, same columns, same hierarchy** as the PC — then scales that canvas to the device.

That is the gap most "mobile responsive" frameworks leave open: they reflow. FitStage **preserves**. There is no view switcher. Every device gets the computer layout, fitted to the screen.

---

## Install

### HTML / any portal (no build step)

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <script src="fitstage.js" data-design="1280"></script>
  <link rel="stylesheet" href="your-desktop-styles.css">
</head>
```

Put the script **in `<head>`, with no `defer` or `async`**, before your CSS. That way the first paint already uses the desktop layout.

### npm

```bash
npm install @techmorah/fitstage
```

```js
import "@techmorah/fitstage";
```

Or copy `dist/fitstage.js` into `public/js`.

### Composer (Laravel / PHP systems)

```bash
composer require techmorah/fitstage
```

Then publish or copy `dist/fitstage.js` to `public/js/fitstage.js` and include it in your layout the same way as HTML.

### Laravel Blade

```blade
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<script src="{{ asset('js/fitstage.js') }}" data-design="1280"></script>
```

### React / Vue / Next / Inertia

Load the file in the document head (root `index.html` or the Laravel layout that wraps the SPA). Do not mount it only inside a component — the viewport must be set before CSS media queries run.

### Flutter / native apps

FitStage is for **web**. For Flutter, use the same idea with a design-size scaler such as `flutter_screenutil` (`designSize: Size(1280, 800)`). For desktop-style software (Electron, WPF, Qt), keep a minimum window width or scale the root visual.

---

## How it works

1. Read the device width.
2. If it is narrower than the design width (default **1280px**), set the viewport to that design width.
3. CSS then sees a **computer-sized page**, so desktop rules apply — columns stay columns.
4. The browser scales the whole page to the physical screen, so it **fits** without restacking.
5. Pinch-zoom stays on, so a phone can magnify a control the same way a user would lean into a monitor.

This is intentional. Traditional responsive CSS *changes* the design. FitStage *fits* the design.

---

## Options

| Attribute | Default | Meaning |
|---|---|---|
| `data-design` | `1280` | PC artboard width in CSS pixels |
| `data-min-scale` | `0.25` | Smallest scale on very narrow phones |

```html
<script src="fitstage.js" data-design="1280"></script>
```

---

## When to use it

- Corporate sites and company profiles
- Admin portals, dashboards, and back-office systems
- Payment, SMS, ISP, and operations consoles
- Any UI you already love on a 13–27" monitor

---

## Live

Used on:

- [techmorahsolutionltd.org](https://techmorahsolutionltd.org)
- [sarah-gordon.org](https://sarah-gordon.org)

---

## License

MIT © TechMorah Solution LTD
