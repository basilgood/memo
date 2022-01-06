title: to-be-visible
==========
date: 2022-01-03 23:34
tags: []
categories: []
- - -
I'd recommend to use web-first assertions with frame locators instead of all the custom waitForSelector logic, this should simplify your tests and probably get rid of some potential races, see here:

```js
const iframe = page.frameLocator(PDFTronSelectors.PDFTronAppFrame);
const progress = iframe.locator(PDFTronSelectors.progress);
await expect(progress).toBeVisible();
await expect(progress).toBeHidden();
```
