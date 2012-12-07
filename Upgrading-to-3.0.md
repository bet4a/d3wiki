Most changes to D3 are carefully designed to be backwards-compatible, which makes it easier to upgrade. If you’ve been linking to the official [d3.v2.js](http://d3js.org/d3.v2.js), you’ve been getting bug fixes, performance improvements, and new features automatically. Unfortunately, not all changes can be made backwards-compatible; periodically, these potentially disruptive changes are needed to keep the API and the code lean, by removing deprecated, broken or confusing functionality.

D3 3.0 is the first major release since 2.0 was released last August. Since 2.0.0, there have been 10 minor releases and 37 patch releases. 3.0 includes significant new features and improvements, but in accordance with [semantic versioning](http://semver.org/), this major release also includes several backwards-incompatibilities. This document will guide you on how to upgrade from 2.x to 3.0.

## Requests

One of the first things you are likely to notice is that the d3.xhr callback interface has changed.

