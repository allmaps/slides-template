# Allmaps Slides template

Create a map slideshow from one configuration file and Markdown slides.
This example explains georeferencing using the Van Berckenrode map of
Amsterdam: draw a mask, add control points and compare two transformations.

Create a repository with GitHub's **Use this template** button, then clone it.
Use Node.js 24 or later and pnpm 10. Before publishing your content,
[review the license you are copying](#license).

## Preview

**Copying or forking this template?** Get your own API key at
[Protomaps](https://protomaps.com/api) and replace `protomaps.key` in
[slides.config.yml](slides.config.yml). The included key is for this template's demo.

Run from your cloned content repository:

```sh
pnpm install --frozen-lockfile
pnpm dev
```

The package version is pinned in `package.json` and `pnpm-lock.yaml`.
See [setup, upgrades and deployment](docs/usage.md) for more commands.

## Make it yours

- Edit [slides.config.yml](slides.config.yml) for the title and project settings.
- Replace the files in [slideshows/main](slideshows/main). Numeric prefixes set their order.
- Put the title and map settings in each slide's YAML frontmatter; write its body in Markdown.
- Replace image and annotation URLs with your own, and update [CREDITS.md](CREDITS.md).

See [writing slides](https://github.com/allmaps/slides/blob/main/docs/authoring.md)
and [images and captions](https://github.com/allmaps/slides/blob/main/docs/images.md)
for examples. [Customization and deployment](docs/usage.md) covers basemaps,
local images and static builds.

## Configuration references

Copy only the settings you need. These files are examples, not extra configuration
loaded by the app; YAML includes and cross-file anchors are not supported.

| File | Contents |
| --- | --- |
| [slides.config.yml](reference/slides.config.yml) | Project, slideshow, basemap and generation options. |
| [slide.yml](reference/slide.yml) | Slide frontmatter and map entries. |
| [warped-map-options.yml](reference/warped-map-options.yml) | Rendering options and dark-mode overrides. |
| [interface.yml](reference/interface.yml) | Interface labels and placeholders. |

Values show defaults; comments explain examples, inheritance and support limits.
Protomaps style overrides are not enumerated.
Check these references when upgrading Slides.

## License

Unless otherwise noted, the original material in this repository, including its
documentation, configuration examples and sample slides, is licensed under
[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE).
Attribution and source references are in [credits.md](credits.md).

**Copying this template also copies its license notice.** If you keep this notice
and publish your own content without a separate rights statement, you are
presenting that content as CC BY 4.0. To choose a different license for material
you own, update your project's license notice, this section and credits before
publishing. CC BY does not require independently authored additions to use the
same license; simply cloning the template does not license your future work.

Any template material you retain, including in adapted form, remains subject to
CC BY 4.0: preserve its attribution and license notice, and indicate your changes.
Changing your project's license does not revoke CC BY rights already granted
for previously published material.

External maps, images and annotations retain their own rights statements.
The separately installed Slides application has its own
[software licenses and content permission](https://github.com/allmaps/slides/blob/main/docs/licensing.md).
