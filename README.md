# Root Faction Tier List Maker

A web application built with Svelte that allows users to create tier lists for factions from the board game Root by Cole Wehrle.

## Requirements

- Node.js (v16.0.0 or higher)
- npm (v7.0.0 or higher) or pnpm (v8.0.0 or higher)

## Installation

1. Create a new Svelte project:

```bash
npm create vite@latest my-root-tierlist -- --template svelte
# or
pnpm create vite@latest my-root-tierlist -- --template svelte
```

2. Navigate to the project directory:

```bash
cd my-root-tierlist
```

3. Install dependencies:

```bash
npm install
# or
pnpm install
```

4. Create the required directories and files:

```bash
mkdir -p public/factions src/lib
```

5. Add the faction images to `public/factions/`:
   - marquise.png
   - eyrie.png
   - woodland.png
   - vagabond.png
   - riverfolk.png
   - lizard.png
   - corvid.png
   - duchy.png

## Development

To start the development server:

```bash
npm run dev
# or
pnpm dev
```

The site will be available at `http://localhost:5173`

## Building for Production

To create a production build:

```bash
npm run build
# or
pnpm build
```

## Usage

1. The factions appear in a pool at the bottom of the screen
2. Drag any faction and drop it into your desired tier (S through D)
3. Rearrange factions by dragging them between tiers

## Contributing

Feel free to open issues or submit pull requests if you have suggestions for improvements.

## License

[Choose an appropriate license for your project]

## Credits

- Root board game created by Cole Wehrle and Leder Games
- Faction artwork belongs to Leder Games

## Note

This is a fan-made project and is not affiliated with Leder Games or the official Root board game.
