# ChatbotAI-test

Step per creare la libreria:
- Creare un repository
- Lanciare il comando npm init e inserire i dati richiesti. Questo processo andrà a creare il file package.json
- Installare le dipendenze necessarie:
    - React: npm install react react-dom
    - Babel/webpack: npm install --save-dev babel-loader @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli webpack-dev-server
    - Typescript (opzionale ma consigliato): npm install --save-dev typescript @types/react @types/react-dom
- Configurazione Babel:
    - Crea un file di configurazione Babel babel.config.js:
    ```javascript
    module.exports = {
        presets: ["@babel/preset-env", "@babel/preset-react"]
    };
    ```
- Configurazione webpack:
    - Crea un file di configurazione Webpack webpack.config.js:
    ```javascript
    const path = require('path');
    module.exports = {
        entry: './src/index.js',
        output: {
            path: path.resolve(__dirname, 'dist'),
            filename: 'index.js',
            library: 'MyReactComponents',
            libraryTarget: 'umd',
            umdNamedDefine: true
        },
        module: {
            rules: [
            {
             test: /\.js$/,
                exclude: /node_modules/,
                use: {
                    loader: 'babel-loader'
                }
            }
            ]
        },
        resolve: {
            extensions: ['.js', '.jsx']
        },
        externals: {
         react: {
                commonjs: 'react',
                commonjs2: 'react',
                amd: 'react',
                root: 'React'
            }
        }
    };
    ```