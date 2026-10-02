---
title: A better fit?
location:
  center: [4.897004, 52.3691733]
  zoom: 15
  duration: 5000
warpedMaps:
  - url: https://annotations.allmaps.org/maps/e9aa6ec10276bf65@d2d0044d129ea2d5
    caption: Van Berckenrode map of Amsterdam
    provenance: Allard Pierson
    homepage: https://hdl.handle.net/11245/3.39844
    options:
      applyMask: true
      renderGcps: true
      renderTransformedGcps: true
      renderVectors: true
      transformationType: thinPlateSpline
      opacity: 0.8
---

A **thin-plate-spline transformation** removes the vectors between the control points on the image and the underlying map, and distorts the image locally in between those points to create a better fit.

Compare this view with the previous slide: a closer fit at these points also changes the shapes between them.
