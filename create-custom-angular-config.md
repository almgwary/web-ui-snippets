## Angular Custom Config

**Create custom angular build config to copy extra files with build process**

 1. `npm i --save-dev @angular-builders/custom-webpack` 
 2. `npm i --save-dev file-loader` 
 3. edit `angular.json`

 
```
        "build": {
          "builder": "@angular-builders/custom-webpack:browser",
          "options": {
            "customWebpackConfig": {
              "path": "./extra-webpack.config.js",
              "replaceDuplicatePlugins": true
             },
            ...
            }
            ...
        }
```

4- create `extra-webpack.config.js` with the following content

```
		module.exports = {
		  module: {
		    rules: [
		      {
		        test: /environment/,
		        use: [
		          {
		            loader: 'file-loader',
		            options: {
		              name: '../../dist/[name].[ext]',
		            },
		          },
		        ],
		      },
		    ],
		  },
		};     
```
