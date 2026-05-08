# JellySkin

### vibrant, modern CSS theme for Jellyfin — maintained by [LuppoDev](https://linktr.ee/aluppidev)
   
![npm (tag)](https://img.shields.io/npm/v/@luppodev/jellyskin/latest?style=for-the-badge) ![jsDelivr hits (npm)](https://img.shields.io/jsdelivr/npm/hm/@luppodev/jellyskin?label=Downloads&style=for-the-badge) ![GitHub](https://img.shields.io/github/license/luppodev/JellySkin?style=for-the-badge)\
![GitHub Repo stars](https://img.shields.io/github/stars/luppodev/JellySkin?style=social)

> JellySkin is a modern, vibrant CSS theme for Jellyfin. Originally created by [prayag17](https://github.com/prayag17), now actively maintained by **LuppoDev** with continued improvements, fluid typography, and JellyFrame support.

# ℹ️ Usage

> [!IMPORTANT]
> JellySkin requires Chrome (105 and above), Edge (105 and above), Safari (15.4 and above), Firefox (121 and above), Opera (91 and above) and any other Browser supporting Baseline 23 css features to work properly

## Method 1: Custom CSS (Dashboard)

### Main Theme
Copy the line below into **Dashboard → General → Custom CSS** and click save:

```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/main.css");
```

### Logos (optional)
```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/logo.css");
```

---

## Method 2: JellyFrame Plugin (Recommended for Jellyfin 10.11+)

> [!TIP]
> JellyFrame is the modern theme management system for Jellyfin 10.11+, replacing the legacy Skin Manager plugin. It provides a GUI for theme selection, configurable variables, and addon toggles directly from the dashboard.

1. Install the **File Transformation** and **JellyFrame** plugins from the Jellyfin plugin catalog
2. Navigate to **Dashboard → JellyFrame → Themes → Marketplace**
3. Enter this URL and click **Load Themes**:
   ```
   https://cdn.jsdelivr.net/gh/luppodev/JellySkin@master/themes.json
   ```
4. Click **Apply** on JellySkin — a configuration dialog will appear
5. Customize accent colors, toggle addons (blur removal, horizontal My Media, etc.)
6. Click **Save & Apply**, then hard-refresh with **Ctrl+Shift+R**

---

## Method 3: Skin Manager Plugin (Legacy)

> [!CAUTION]
> Jellyfin Skin Manager is not being actively maintained and might not load latest css themes. Use JellyFrame instead.

---

# 🧩 Addons

### Improve Performance

#### Remove BackdropFilter
Removes the frosted glass effect from every element to improve performance.
```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/addons/improvePerformance/removeBackdropFilter.css");
```

#### Remove Scroll Fade
Removes the gradient fade bar at the top of scrollable containers.
```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/addons/improvePerformance/removeFadingScroll.css");
```

### Horizontal My Media
Restores the horizontal section for My Media.
```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/addons/horizontalMyMedia.css");
```

### Gradient Accents
Change the default gradient accent colors. Put these imports **below** the main.css import.

#### Mauve
```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/addons/gradients/mauve.css");
```
![image](https://user-images.githubusercontent.com/55829513/200132732-d188392a-5642-47f7-bb62-f204a85d992e.png)

#### NightSky
```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/addons/gradients/nightSky.css");
```
![image](https://user-images.githubusercontent.com/55829513/200132808-5b02c8e9-29c1-4a6b-ad3c-514588cf717a.png)

#### Sea
```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/addons/gradients/sea.css");
```
![image](https://user-images.githubusercontent.com/55829513/200132840-984deaf3-c228-4092-be8f-44c325d57782.png)

#### Custom Gradient
Override the CSS custom properties directly:
```css
:root {
  --accent1-light: hsl(285, 46%, 56%);
  --accent1-dark: hsl(285, 35%, 21%);
  --accent1-light-opacity1: hsla(285, 46%, 56%, 0.4);
  --accent2-light: hsl(195, 100%, 43%);
  --accent2-dark: hsl(195, 100%, 16%);
}
```

### Video Theme Blur
Applies the blur effect to video player backgrounds.
> *Caution*: Performance intensive filter.
```css
@import url("https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/addons/videoThemeBlur.css");
```

---

# 💻 Screenshots

### Login Page
![Login_Page](https://github.com/luppodev/JellySkin/assets/55829513/9ca0d0c2-9ada-4e41-93b9-e4281be20d1d)

### Home Screen
![Home page](https://github.com/luppodev/JellySkin/assets/55829513/075d844b-ca43-4f61-b54a-cb75110e77ed)

### Library
![Library](https://github.com/luppodev/JellySkin/assets/55829513/c3ef8e48-df17-44f0-9708-e10dfa448237)

### Title Screen
![Title page](https://github.com/luppodev/JellySkin/assets/55829513/270bb0bb-a755-449d-a57d-9da4e31d6082)

### Episodes List
![Episodes](https://github.com/luppodev/JellySkin/assets/55829513/eaded068-5930-47fd-b5d0-03cf89e1da44)

---

# ❓ Common Problem Fixes

### Unable to see blurred background in Firefox
From version 70: this feature is behind the `layout.css.backdrop-filter.enabled` preference (needs to be set to `true`) and the `gfx.webrender.all` preference (needs to be set to `true`). Visit `about:config` to change these.

### Logos not visible even with `logo.css`
1. Install the **Fanart** plugin: Dashboard → Plugins → Catalog
2. Enable Fanart as metadata provider for your libraries: Dashboard → Library → 3 dots → Manage Library → Metadata provider
3. Rescan your drive with **Replace Metadata** enabled

### Background not visible
Go to **Settings → Display** and enable **Backdrops**.

### Fix for Nginx Reverse Proxy
When using the Nginx Reverse proxy config from the [Jellyfin docs](https://jellyfin.org/docs/general/networking/nginx.html), the theme may not load due to CSP (Content Security Policy) restrictions.

Update your nginx config to allow the CDN URLs:

**Before:**
```shell
add_header Content-Security-Policy "default-src https: data: blob: http://image.tmdb.org; style-src 'self' 'unsafe-inline'; script-src 'self' 'unsafe-inline' https://www.gstatic.com/cv/js/sender/v1/cast_sender.js https://www.youtube.com blob:; worker-src 'self' blob:; connect-src 'self'; object-src 'none'; frame-ancestors 'self'";
```

**After (with JellySkin):**
```shell
add_header Content-Security-Policy "default-src https: data: blob: http://image.tmdb.org; style-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/main.css https://cdn.jsdelivr.net/npm/@luppodev/jellyskin@latest/dist/logo.css; script-src 'self' 'unsafe-inline' https://www.gstatic.com/cv/js/sender/v1/cast_sender.js https://www.youtube.com blob:; worker-src 'self' blob:; connect-src 'self'; object-src 'none'; frame-ancestors 'self'";
```

Also add each addon URL you use to `style-src`.

---

# 🔧 Development

```bash
# Install dependencies
npm install

# Build
npm run build

# Watch + Live reload dev server
npm start

# Lint SCSS
npm run lint:style

# Format code
npm run format

# Publish to npm
npm run pub:patch   # 12.5.2 → 12.5.3
npm run pub:minor   # 12.5.3 → 12.6.0
npm run pub:major   # 12.6.0 → 13.0.0
```

# 🚀 Release (GitHub Actions)
Push a tag starting with `v` to trigger automatic build, npm publish, and GitHub release:
```bash
git tag v12.6.0
git push origin v12.6.0
```
