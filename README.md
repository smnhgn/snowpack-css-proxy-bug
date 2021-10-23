# snowpack-css-proxy-bug

example repo to demonstrate snowpack bug with css proxy files

## steps to reproduce

1. set up project with snowpack and @snowpack/plugin-sass
2. import sass file in js (or ts)

   `import "./index.scss"`

3. run build with watch flag

   `snowpack build --watch`

4. change contents of sass file (index.scss)

   `body { background: blue; }` -> `body { background: red; }`

5. check build output

6. css output (index.css) received update

   `body { background: red; }`

7. css proxy output (index.css.proxy.js) did not receive update

```
if (typeof document !== 'undefined') {
  const code = "body {\n  background: blue;\n}";

  const styleEl = document.createElement("style");
  const codeEl = document.createTextNode(code);
  styleEl.type = 'text/css';
  styleEl.appendChild(codeEl);
  document.head.appendChild(styleEl);
}
```
