## ReactJs

### Configurando o ambiente (com Webpack)
- Instalar Webpack

`npm i --save-dev webpack`

- Instalar as dependências do Babel

`npm i --save-dev babel-loader babel-core babel-preset-es2015 babel-preset-react`

- Criar o arquivo webpack.config.js na raiz do projeto

```
const path = require('path')

const inputDirName = 'app'
const outputDirName = 'dist'
const entryFilename = 'index.jsx'

module.exports = {
    entry: path.resolve(__dirname, inputDirName, entryFilename),
    output: {
        filename: 'bundle.js',
        path: path.resolve(__dirname, outputDirName)
    },
    module: {
        loaders: [
            {
                test: /.jsx?$/,
                loader: 'babel-loader',
                exclude: /node_modules/,
                query: {
                    presets: ['es2015', 'react']
                }
            }
        ]
    },
}

```

### Iniciando um novo projeto
- Com NPM:

`npm i --save react react-dom`

- Com Yarn:

`yarn add react react-dom`
