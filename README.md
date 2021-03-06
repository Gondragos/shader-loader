# Glsl loader for webpack

Glsl loader for webpack2 & webpack3. It support chunks & inspire by [ShaderLoader](https://github.com/cabbibo/ShaderLoader)

## Getting started

Install:
``` shell
npm install shader-loader --save-dev
```

Config webpack:
``` javascript
module: {
	rules: [
      {
        test: /\.(glsl|vs|fs)$/,
        loader: 'shader-loader',
        options: {
          glsl: {
            chunkPath: resolve("/glsl/chunks")
          }
        }
      }
	]
}
```

You can now require your glsl files:
``` javascript
var vertexShader = require("shader.vs");
var fragmentShader = require("shader.fs");
```

if you use $xxx in your shader its replace by the content of xxx.glsl, for example:

``` glsl
void main(void) {
	$snoise //replace by chunks/snoise.glsl
}
```

Learn more about loaders & webpack:
http://webpack.github.io/docs/loaders.html

## Options
### chunkPath
Path, where chunks are located
``` javascript
options: {
    glsl: {
        chunkPath: path.resolve(__dirname, "src/glsl/chunks")
    }
}
```
### chunkPrefix
Customize, how import will be look like

``` javascript
options: {
    glsl: {
        chunkPrefix: '#include '
    }
}
```

``` glsl
void main(void) {
	#include snoise //replace by <path>/snoise.glsl
}
```


## License
MIT (http://www.opensource.org/licenses/mit-license.php)
