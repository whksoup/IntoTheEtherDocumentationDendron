---
id: 4854a8a2-d71a-466f-993d-3b34cc46cfc6
title: Herbarium specimen imaging — scale and colour calibration
desc: "The standardized scale-bar and colour-reference convention herbaria use so specimen photographs can be measured and compared across institutions."
updated: 1788443317297
created: 1788419688518
tags: [meta, photography, scientific-plate, scale]
vendor_approved: false
vendor: ""
approved_on: ""
---

## The problem

A specimen photograph is only useful to someone who wasn't in the room if
its size and true colour can be recovered from the image itself. Two
photographs of the same plant, shot on different days by different people
with different cameras, need to be comparable — for identification, for
measurement, for later computer-vision work — without anyone having to
trust the photographer's word for scale or lighting.

## What they did

Herbaria have converged on a shared frame layout rather than a shared
camera setup: every specimen image carries a colour-calibration scale (a
patch series with known reference values) and a separate measurement scale
bar, both physically placed on the copy stand rather than added digitally
after the fact. A commonly cited design for the ruler itself is a black
background with white centimetre markings, alternating black and white
blocks per centimetre, with the first centimetre further subdivided into
millimetres so sub-centimetre detail can be read directly off the image
without a separate reference table. The point isn't the elegance of the
ruler — it's that the same physical object appears, unchanged, in every
frame, so it functions as a bridge between arbitrary photographs and real
units.

## What we take

Directly usable for our "scale is always declared" rule: rather than
inventing our own scale device, we should adopt one fixed, physically
present reference object — the same one, every shot — the way herbaria use
one ruler design across institutions. It also suggests going a step
further than we'd planned: a colour-calibration patch alongside the
measurement scale, so board and die colours (which vary a lot under
different fab processes and lighting) stay comparable across the exhibition
rather than just their size. Cheap to adopt, and it reads as method rather
than decoration, which fits the datasheet-plain aesthetic we're going for.

What doesn't transfer: herbarium sheets are flat, rigid, and shot on a
fixed copy stand; most of our subjects (racks, installed hardware) aren't,
so the scale convention transfers more cleanly than the flat-copy-stand
setup does.

Source: (https://www.edwardburtynsky.com/projects/films/manufactured-landscapes)
Further reading: <https://arxiv.org/pdf/2505.17317>
