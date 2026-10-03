# Preview, customize and build

## Install and preview

Create a repository from this template, clone it, and run with Node.js 24 and pnpm 10:

```sh
pnpm install --frozen-lockfile
pnpm dev
```

Open the URL printed by the server. Markdown and configuration changes reload
automatically. The repository pins its Slides dependency and all transitive
versions. To upgrade, run `pnpm add -D -E @allmaps/slides@<version>` and commit the
manifest and lockfile after testing.

For software development in a Slides checkout, run
`pnpm exec slides dev ./content/slides-template` from the Slides root instead.

## Edit the example

The filename `01-original-map.md` becomes the `original-map` anchor.
Each slide declares its own maps; repeat a map to retain it on the next slide.
The example slides use the same versioned Van Berckenrode annotation.
Their frontmatter changes the mask, control points, transformation and opacity;
the later slides explore central Amsterdam.

The first three slides keep the full image visible with `applyMask: false`,
preserve its orientation with `useBearing: true` and use a `helmert`
transformation. Later slides apply the mask and compare `polynomial` with
`thinPlateSpline` over a Protomaps basemap.

The last two slides demonstrate GeoJSON overlays. `sources` in `slides.config.yml`
declares the datasets; `layers` sets their default visibility and defines a
custom symbol layer whose `text-field: [get, Naam]` reads building names.
Each slide enables the layers it needs with `layers: [{layer: ..., visibility: visible}]`.
Omitted settings return to the global defaults, including when navigating backward.
Use the IDs in the configuration without adding a `user-` prefix.
See [layer configuration](https://github.com/allmaps/slides/blob/main/docs/configuration.md#shared-geojson-overlays)
for local files, styling and additional layer types. These examples require the
Slides version that introduces global layers; in this checkout, use the local CLI.

For local images, create `assets/images/` and use ordinary Markdown:

```md
![Description of the image](assets/images/photo.jpg)
```

Run `pnpm exec slides iiif .` before viewing local images and after
changing them. For rich captions and crops, see
[images and captions](https://github.com/allmaps/slides/blob/main/docs/images.md).

## Basemap and API key

The template uses Protomaps. When copying or forking it, get your own API key at
[protomaps.com/api](https://protomaps.com/api) and replace the demo key in
`slides.config.yml`:

```yaml
protomaps:
  key: your-own-key
```

This setting is used for local previews, builds and thumbnail generation,
including the GitHub Pages workflow. The key is included in the generated
website. To supply it through `PUBLIC_PROTOMAPS_KEY` instead, remove the configured
`protomaps.key` first; a key in the configuration takes precedence.

Use `http://localhost:<port>` for local previews. If the server prints
`127.0.0.1`, replace it with `localhost` in your browser: Protomaps allows
localhost, while other origins depend on your key's allowed-site settings.
Add your published website's origin to those settings before deploying.

For a different basemap, set `map.styles.light` and `map.styles.dark` to your own
MapLibre style URLs or files under `assets/map-styles/`.

## Validate and build

From this content repository:

```sh
pnpm exec slides validate
pnpm exec slides build
pnpm exec slides preview
```

Builds generate map previews and local IIIF images, then export
the site to the content repository's `dist/`. The native thumbnail renderer has
additional [Linux dependencies](https://github.com/allmaps/slides/blob/main/docs/static-render.md#linux-setup).

For deployment, set `site.publicUrl` to the full public URL and `site.basePath`
to its path prefix (for example `/my-slideshow` on GitHub Pages). Serve the
generated `dist/` directory with a static host.

For GitHub Pages, select **GitHub Actions** under **Settings → Pages**. The included
workflow deploys on pushes to `main` and can also run manually. It reads the Pages
URL and base path automatically, installs the locked npm package and native Linux
libraries, and builds with Xvfb. Configure any custom domain in Pages settings.
Manual runs offer separate reset switches for IIIF, annotations and thumbnails.

To refresh map previews while developing, run `pnpm exec slides thumbnails`
with the content directory.
