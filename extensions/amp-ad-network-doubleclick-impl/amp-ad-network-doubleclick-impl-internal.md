<!---
Copyright 2016 The AMP HTML Authors. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS-IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# DoubleClick

### <a name="amp-ad-network-doubleclick-impl"></a> `amp-ad-network-doubleclick-impl`

<table>
  <tr>
    <td width="40%"><strong>Description</strong></td>
    <td>DoubleClick implementation of AMP Ad tag which requests early by XHR and
    renders natively within the page if a valid AMP Ad is returned.  Should
    not be directly referenced by pages and instead is dynamically loaded
    via the amp-ad tag.  However, in order to remove an async script load
    of this library, publishers can include its script declaration.</td>
  </tr>
  <tr>
    <td width="40%"><strong>Availability</strong></td>
    <td>In Development</td>
  </tr>
  <tr>
    <td width="40%"><strong>Required Script</strong></td>
    <td><code>&lt;script async custom-element="amp-ad" src="https://cdn.ampproject.org/v0/amp-ad-0.1.js">&lt;/script></code></td>
  </tr>
  <tr>
    <td width="40%"><strong>Examples</strong></td>
    <td><a href="#examples">See Example Section</a></td>
  </tr>
</table>

### Supported Features

<table>
  <tr>
    <td><strong>Feature</strong></td>
    <td><strong>Description</strong></td>
    <td><strong>Status</strong></td>
  </tr>
  <tr>
    <td><a href="multi-size.md">Multi-size</a></td>
    <td>Allows slots to specify multiple sizes.</td>
    <td>Launched</td>
  </tr>
  <tr>
    <td><a href="fluid.md">Fluid</a></td>
    <td>Fluid slots do not require a pre-specified size, but will instead fill up the width of their parent container and adjust their height accordingly.</td>
    <td>Beta</td>
  </tr>
  <tr>
    <td><a href="doubleclick-rtc.md">Real Time Config</a></td>
    <td>Allows Publishers to augment ad requests with targeting information that is retrieved at runtime.</td>
    <td>Launched</td>
  </tr>
  <tr>
    <td><a href="render-on-idle.md">Render on Idle</a></td>
    <td>Allows slots 3-12 viewports down to render while the AMP scheduler is idle.</td>
    <td>Launched</td>
  </tr>
  <tr>
    <td><a href="refresh.md">Refresh</a></td>
    <td>Enabled slots will periodically refetch new creatives.</td>
    <td>Launched</td>
  </tr>
  <tr>
    <td><a href="safeframe.md">Safeframe API</a></td>
    <td>An API-enabled Iframe for facilitating communication between publisher page and creative content.</td>
    <td>Launched</td>
  </tr>
  <tr>
    <td><a href="sra.md">SRA: Single Request Architecture</a></td>
    <td>When enabled, all eligible slots on the page will be serviced by a single ad request.</td>
    <td>Beta</td>
  </tr>
</table>

#### Examples
Example - DoubleClick Ad
```html
<amp-ad width=728 height=90
    type="doubleclick"
    data-slot="/6355419/Travel">
</amp-ad>
```
### Configuration

For semantics of configuration, please see [ad network documentation](https://developers.google.com/doubleclick-gpt/reference).


#### Ad size

By default the ad size is based on the `width` and `height` attributes of the `amp-ad` tag. In order to explicitly request different ad dimensions from those values, pass the attributes `data-override-width` and `data-override-height` to the ad.

Example:

```html
<amp-ad width=320 height=50
    data-override-width=111
    data-override-height=222
    type="doubleclick"
    data-slot="/4119129/mobile_ad_banner">
</amp-ad>
```

#### Attributes
Below the term `primary size` refers to the width and height pair specified by the `width` and `height` attributes of the tag.
- `data-multi-size` A string of comma separated sizes, which if present, forces the tag to request an ad with all of the given sizes, including the primary size. Each individual size must be a number (the width) followed by a lowercase 'x' followed by a number (the height). Each dimension specified this way must not be larger than its counterpart in the primary size. Further, each dimension must be no less than 2/3rds of the corresponding primary dimension, unless `data-mutli-size-validation` is set to false.
- `data-multi-size-validation` If set to false, this will allow secondary sizes (those specified in the `data-multi-size` attribute) to be less than 2/3rds of the corresponding primary size. By default this is assumed to be true.

### Supported parameters

- `data-slot`
- `data-multi-size`
- `data-multi-size-validation`

Supported via `json` attribute:

- `categoryExclusions`
- `cookieOptions`
- `tagForChildDirectedTreatment`
- `targeting`

### Unsupported DFP Formats
- Interstitials
- Expandables. Although expandables on interaction/click is a format that is work in progress.
- Flash
- Anchor Ads / Adhesion Units
- Creatives served over HTTP.
