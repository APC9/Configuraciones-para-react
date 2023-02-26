# Instalación y configuracion de Storybook
## En proyectos de React + Vite

1. Eliminar los archivos como lo muestra el profesor (vite-env.d, App.css, main.css, public, etc)

NO ELIMINAR: tsconfig.json, tsconfig.node.json

2. para eliminar el script del package.json se deben forzar con el comando :

```
npm --force uninstall @types/react
```

3. Se instala storybook con el comando
```
npx storybook init

```

4. Se reemplazan los scripts de react en el package.json
```
"scripts": {
    "dev": "start-storybook -p 6006",
    "build": "build-storybook"
  },

```

5. Una vez eliminados los scripts se configura el main.js en la carpeta " .storybook ", como lo recomiendan las personas de storybook en esta pagina: https://storybook.js.org/docs/react/configure/overview,  adicionan el path de las historias para que los módulos puedan ser reconocidos en la introducción, es decir; el main quedaría así:

```
// .storybook/main.js
 
module.exports = {
  addons: ['@storybook/addon-essentials'],
  babel: async (options) => ({
    // Update your babel configuration here
    ...options,
  }),
  framework: '@storybook/react',
  stories: [
    '../src/**/*.stories.@(js|mdx)', 
    '../src/**/*.stories.@(js|jsx|ts|tsx)'<=LÍNEA ADICIONADA PARA LAS HISTORIAS
  ],
  webpackFinal: async (config, { configType }) => {
    // Make whatever fine-grained changes you need
    // Return the altered config
    return config;
  },
};

```


6. Posible error debido a la versión de node.

Tiene dos soluciones:

1. Instalar la versión 16 de node.

2. Ejecutar la siguiente configuración en la terminal:


_Linux and macOS (Windows Git Bash)_
```
export NODE_OPTIONS=--openssl-legacy-provider

```

_Windows command prompt_
```
set NODE_OPTIONS=--openssl-legacy-provider

```
   
_Windows PowerShell_
```
$env:NODE_OPTIONS = "--openssl-legacy-provider"

```