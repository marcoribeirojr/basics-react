### Configuração inicial

### Iniciando um novo projeto

`npm init`

`npm i --save react react-dom`

### Configurando o ambiente (com Webpack)
- Instalar Webpack

`npm i --save-dev webpack`

- Instalar as dependências do Babel

`npm i --save-dev babel-loader babel-core babel-preset-es2015 babel-preset-react`

- Criar o arquivo webpack.config.js na raiz do projeto

```
const path = require('path')

const inputDirName = '[NOME DA PASTA DO APP]'
const outputDirName = '[NOME DA PASTA DE ACESSO EXTERNO]'
const entryFilename = '[NOME DO ARQUIVO PRINCIPAL DO PROJETO]'

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
