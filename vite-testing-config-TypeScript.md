# Instalación y configuracion de Jest + React Testing Library
## En proyectos de React + Vite + TypeScript

1. Instalaciones:
```
yarn add --dev jest babel-jest @babel/preset-env @babel/preset-react

yarn add --dev @testing-library/react @testing-library/dom @testing-library/user-event @types/jest jest-environment-jsdom

yarn add --dev jest-svg-transformer

npm i --save-dev @babel/core @babel/preset-typescript

npm i --save-dev identity-obj-proxy

```

2. Opcional: Si usamos Fetch API en el proyecto:
```
yarn add --dev whatwg-fetch
```

3. Actualizar los scripts del __package.json__
```
"scripts: {
  ...
  "test": "jest --watchAll"
```

4. Crear la configuración de babel __babel.config.js__
```
module.exports = {
    presets: [
        [ '@babel/preset-env', { targets: { esmodules: true } } ],
        [ '@babel/preset-react', { runtime: 'automatic' } ],
        '@babel/preset-typescript',
    ],
};
```

5. Opcional, pero eventualmente necesario, crear Jest config y setup:

__jest.config.js__
```
module.exports = {
    testEnvironment: 'jest-environment-jsdom',
    setupFiles: ['./jest.setup.js'],
    moduleNameMapper: {
        "^.+\\.svg$": "jest-svg-transformer",
	"\\.(css|less|scss)$": "identity-obj-proxy",
  }
}
```

__jest.setup.js__
```
// En caso de necesitar la implementación del FetchAPI
import 'whatwg-fetch'; // <-- yarn add whatwg-fetch
```


6. Eliminar "type": "module", del __package.json__ para evitar problemas, Ó Cambiar la extencion 
   de los archivos babel.config.cjs y jest.config.cjs para forzar que los archivos sean de 
   tipo COMMON JS .
