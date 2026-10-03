---
title: Put the map in place
warpedMaps:
  - url: https://annotations.allmaps.org/maps/e9aa6ec10276bf65@c8c1e1934bc93e0f
    caption: Van Berckenrode map of Amsterdam
    provenance: Allard Pierson
    homepage: https://hdl.handle.net/11245/3.39844
    options:
      applyMask: true
      renderTransformedGcps: true
      transformationType: polynomial
---

Allmaps uses the control points to position the image in geographic coordinates.
This first fit uses a **polynomial transformation**. This means that the image is translated, scaled, rotated and skewed to fit on top of a modern map, all in the browser! The mask now hides the surrounding paper.
