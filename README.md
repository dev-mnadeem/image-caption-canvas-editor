# Image Text Editor

A browser-based editor for putting text on images. Upload a PNG, add text layers on a canvas, style them, and export the result at the original image resolution. Everything runs client-side, there is no backend.

![Editor screenshot](docs/screenshots/editor.png)

## Features

- PNG upload, with the canvas sized to the image
- Multiple text layers, each with its own font, size, weight, color, opacity and alignment
- Layer panel and properties panel
- Undo and redo
- Export to PNG at the original dimensions
- A curated list of Google Fonts that works without an API key

Built with Next.js 15, React 18, TypeScript, Fabric.js, Tailwind CSS and Radix UI components.

## Running it

For development:

```bash
npm install
npm run dev
```

Then open http://localhost:3000.

Or build and serve the static export with Docker (nginx in the container):

```bash
docker compose up -d --build
```

and open http://localhost:3900.

## Fonts

By default the font picker uses the curated families in `src/lib/curated-fonts.ts`, loaded from the public Google Fonts CSS endpoint. No key is needed for that. If you set `NEXT_PUBLIC_GOOGLE_FONTS_API_KEY`, the app fetches the full Google Fonts catalogue instead.

## Project structure

- `src/app/page.tsx` is the main page
- `src/components/editor/` has the toolbar, canvas, layer panel and properties panel
- `src/hooks/use-editor.ts` holds the editor state and history
- `src/lib/` contains the Fabric helpers and font loading

## Limitations

- Only PNG uploads are accepted.
- Nothing is saved, a page reload clears the design.
- There are no tests yet. The undo/redo history would be the first thing worth covering.
