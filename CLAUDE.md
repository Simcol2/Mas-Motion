# Mas Motion — project notes

Single-file app: everything lives in `index.html` (HTML + CSS + one big inline `<script>`).
It's a browser-based carnival reel builder — upload photos/clips, arrange slides, add text
slides, pick music, preview, and export a video (canvas + MediaRecorder, recorded in real time).

## Owner design preferences (honor these unless the user says otherwise for a specific case)

- **No black backgrounds.** Never use a black (or near-black) background anywhere — templates,
  text slides, segments (film strip / shuffle / Brady grid), idle card, etc. — unless the user
  explicitly asks for black in that specific case. Default backgrounds should be light/white or
  the user's chosen backdrop, not black.

## Working notes

- Slides play in the exact arranged order (no shuffling of slide order).
- Projects auto-save to IndexedDB and auto-restore on load. To keep saves within the browser
  storage quota, videos are stored as a compact re-encoded copy of just their trimmed seconds;
  the live session still exports from the untouched originals.
- Verify changes headlessly with Chromium (same engine as the user's Android Chrome) before
  shipping; there's no GPU in the test container, so absolute timing/perf numbers aren't
  representative, but correctness and behavior are.
