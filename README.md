# HALO Room5 · Epoch 49 benchmark

[Open the public gallery](https://decembered.github.io/halo-room5-epoch49-benchmark/)

A static gallery of 288 single-run benchmark instances: 72 base events, four variants per event, and 48 instances in each of six groups (actions, visual targets, spatial relations, sequential instructions, mid-motion updates, and counterfactual/stability diagnostics).

The model was rerun with upright HOSI first-person images, a 90° pinhole field of view, 512×512 rendering and BICUBIC resize to 224×224. The previous extra clockwise raster rotation was removed, equivalent to correcting the previous sideways image counter-clockwise by 90°.

Every recording combines a third-person view (left) and first-person view (right), with 15 seconds of generated motion plus a 0.5-second known prefix: 465 frames at 30 FPS. There is one retained recording per task instance. The checkpoint is the joint NymeriaPlus + HOSI epoch49 model.

| All 288 instances | Successful | Rate |
| --- | ---: | ---: |
| Semantic | 20 | 6.94% |
| Strict | 10 | 3.47% |
| End-to-end | 8 | 2.78% |

These are frozen engineering task-completion criteria for a known-room diagnostic, not a held-out-scene or physics-control benchmark. There is no unique paired ground-truth motion, so MPJPE is not the main metric. See [score definitions and group results](reports/summary.md), [full summary](reports/summary.json), and [per-task CSV](reports/scores.csv). A–E macro scores and F paired diagnostics are reported separately.

## Public video copies

Web videos are re-encoded as H.264/yuv420p, CRF28, with fast-start playback. Frame count, frame rate, duration and original raster dimensions are preserved. Quantitative scores are computed from the original generated trajectories and are unchanged by web encoding. Source and web video SHA-256 hashes are mapped in [video provenance](data/video_provenance.json).

This repository contains the gallery, public task metadata, score reports, images and web video copies. It does not contain training weights, raw training data, runtime environments or server credentials.

## Hosting

GitHub Pages serves the repository root with Jekyll disabled. All media uses relative URLs and is hosted with the page. Open `index.html` locally with its `videos/` directory, or serve the directory through a static server that supports byte ranges for video seeking.
