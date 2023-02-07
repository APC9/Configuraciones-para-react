

### 1. Posteriormente, instalamos Tailwind CSS como dependencia de desarrollo:


Con Yarn:

```bash
$ yarn add -D tailwindcss postcss autoprefixer
```

### 2. Creamos el archivo de configuración de Tailwind CSS y de PostCSS

```bash
$ npx tailwindcss init -p
```

En el interior del archivo generado agregaremos estas líneas:

```jsx
module.exports = {
 content: ["./index.html", "./src/**/*.{js,jsx,ts,tsx}"],
 theme: {
    extend: {},
  },
  plugins: [],
};
```

### 3. Después agregaremos las directivas en el index.css de nuestro proyecto

```css
/* src/index.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## ¡Y eso es todo!, Disfruta de las bondades que nos ofrece Tailwind CSS!