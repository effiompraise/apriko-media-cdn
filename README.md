# apriko-media-cdn
## Digital Apriko media pipeline

The n8n workflow writes each content batch as one Git commit containing:

- `queue/<batch>.manifest.json`
- the batch SVG files listed by the manifest

The manifest is the only file that triggers `.github/workflows/render-media.yml`.
The workflow serialises render jobs, processes only manifests changed by that
push, creates PNG/MP4 output, and writes `rendered/status/<batch>.json` with
`"status": "READY"` when rendering completes.