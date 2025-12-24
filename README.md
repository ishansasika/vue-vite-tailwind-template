# VueVite Template

A modern, lightning-fast Vue 3 template built with Vite, TypeScript, and Tailwind CSS. Perfect for building your next web application with a beautiful blue-purple gradient design theme.

## Features

- ⚡ **Vue 3** - Progressive JavaScript framework
- 🚀 **Vite 6** - Next generation frontend tooling
- 📘 **TypeScript** - Type safety and enhanced developer experience
- 🎨 **Tailwind CSS** - Utility-first CSS framework
- 🛣️ **Vue Router** - Official router for Vue.js
- 🌙 **Dark Mode** - Built-in dark mode support
- 📱 **Responsive** - Mobile-first responsive design
- 🎯 **Production Ready** - Optimized build configuration

## Project Structure

```
vue-vite-tailwind-template/
├── src/
│   ├── components/     # Reusable components (Header, Footer)
│   ├── pages/          # Page components (Home, About, Services, Contact)
│   ├── router/         # Vue Router configuration
│   ├── App.vue         # Root component
│   ├── main.ts         # Application entry point
│   └── style.css       # Global styles with Tailwind directives
├── public/             # Static assets
├── index.html          # HTML entry point
└── vite.config.ts      # Vite configuration
```

## Getting Started

### Prerequisites

- Node.js 18+ and npm

### Installation

1. Clone the repository:
```bash
git clone https://github.com/ishansasika/vue-vite-tailwind-template.git
cd vue-vite-tailwind-template
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run type-check` - Run TypeScript type checking

## Pages

- **Home** - Landing page with hero, features, stats, and CTA sections
- **About** - Mission, tech stack, values, and team information
- **Services** - Service offerings with color-coded cards
- **Contact** - Contact form and information

## Customization

### Colors

The template uses a blue-purple gradient theme. To customize the colors, modify the Tailwind classes in the components:

- Primary gradient: `from-blue-600 to-purple-600`
- Background gradients: `from-blue-50 to-purple-50`

### Logo

Update the logo letter in `Header.vue` and `Footer.vue`:
```vue
<span class="text-white font-bold text-xl">V</span>
```

### Branding

Replace "VueVite" with your brand name in:
- `Header.vue`
- `Footer.vue`
- `index.html` (title tag)

## Technologies

- [Vue 3](https://vuejs.org/) - Progressive JavaScript framework
- [Vite](https://vitejs.dev/) - Next generation frontend tooling
- [TypeScript](https://www.typescriptlang.org/) - Typed superset of JavaScript
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework
- [Vue Router](https://router.vuejs.org/) - Official router for Vue.js

## License

MIT License - feel free to use this template for your projects!

## Author

Created with ❤️ by [Ishan Sasika](https://github.com/ishansasika)
