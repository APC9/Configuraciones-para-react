

### 1. intallar eslint:


Con Yarn y npm:

```bash
$ yarn add -D eslint
$ npm install --save-dev eslint
```

### 2. instalar el plugin para typescript

```bash
$ yarn add -D @typescript-eslint/eslint-plugin
$ npm i --save-dev @typescript-eslint/eslint-plugin
```

### 3. instalar el plugin para prettier

```bash
$ yarn add -D eslint-plugin-prettier
$ npm i --save-dev eslint-plugin-prettier
```

### 4. instalar eslit-config-prettier

```bash
$ yarn add -D eslint-config-prettier
$ npm i --save-dev eslint-config-prettier
```

### 5. instalar typescript-eslint/parser

```bash
$ yarn add -D @typescript-eslint/parser
$ npm i --save-dev @typescript-eslint/parser
```

### 6. instalar prettier

```bash
$yarn add -D prettier
$ npm i --save-dev prettier
```

### 7. crear un archivo llamado .eslintrc.json con la siguiente configuracion:

```json
{
  "parser": "@typescript-eslint/parser",
  "extends": [
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ],
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "rules": {
    "eqeqeq": ["error", "always"],
    "no-empty-function": "error",
    "no-implicit-coercion": "warn",
    "@typescript-eslint/no-explicit-any": "warn",
    "@typescript-eslint/no-duplicate-enum-values": "warn",
    "@typescript-eslint/no-inferrable-types": "off"
  }
}

```

### 8. en packages.json agregar el siguiente scripts

```
"lint": "eslint \"*/**/*.{js,ts,tsx}\" --quiet --fix"
```

### 9. crear un archivo llamado .eslintignore

```
package.json
package.lock.json
node_modules
dist
```

### 10. crear un archivo .prettierrc.json

```json
{
    "tabWidth": 4,
    "singleQuote": true
}
```

### 11. Por ultimo installar husky: esto evitar que se realice el commit en git si aun hay errores

```bash
npx husky-init $$ yarn add
npx husky-init $$ npm install add
```

### 12. en la carpet .husky - pre-commit hacer la siguiente configuracion

```
yarn lint      "NOTA: si estas en yarn"
npm run dev 

```

### y eso es todoo....