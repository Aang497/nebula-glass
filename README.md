# Nebula Glass

A Spicetify theme in three variants — **Nebula**, **Ink** and **Haze** — with see-through glass tiles over a full-screen wallpaper. Built to work on **Spicetify for Android (Morphe)** as well as desktop.

| Variant | Wallpaper | Glass | Accent |
|---|---|---|---|
| Nebula | `assets/nebula.jpg` | violet, 55% | `#E879F9` |
| Ink | `assets/ink.jpg` | black, 50% | `#FFFFFF` |
| Haze | `assets/nebula.jpg` | deep teal, 50% | `#67E8F9` |

## Android (Spicetify for Morphe)

Needs Android 14 or later.

1. Open Spicetify's **Marketplace → Themes** and search for **Nebula Glass** (it appears once this repo has the `spicetify-themes` topic; the list refreshes every 6 hours, or tap Refresh).
2. Tap a variant, then pick its colour scheme. The wallpaper downloads with it.
3. Leave **Blur background image** off to keep the wallpaper sharp.

What Android uses from this theme: the colours in `color.ini` and the wallpaper named in `user.css`. The app dims the wallpaper by 50% itself. Everything else in `user.css` (fonts, blur behind tiles, borders) is desktop-only — Android can't apply CSS.

Some screens (e.g. Settings) and the Home filter chips keep Spotify's own colours.

## Desktop

```sh
cd "$(spicetify -c | xargs dirname)/Themes"
git clone https://github.com/Aang497/nebula-glass
```

Then pick one variant — Spicetify loads `color.ini` and `user.css` from the theme folder, so copy that variant's two files to the folder root:

```sh
cp nebula-glass/nebula/* nebula-glass/
spicetify config current_theme nebula-glass color_scheme Nebula
spicetify apply
```

On desktop the tiles get real frosted glass (`backdrop-filter`) and JetBrains Mono. Spotify renames its classes from time to time, so some selectors may need updating.

## Files

```
manifest.json        Marketplace listing (three variants)
assets/              wallpapers
nebula|ink|haze/     color.ini + user.css per variant
```

`card` in each `color.ini` uses `#AARRGGBB` for transparency — an Android-only format. Desktop misreads it, so each `user.css` sets the intended card colour again for desktop.
