# snowpack-css-proxy-bug

example repo to demonstrate snowpack bug with css proxy files

## steps to reproduce

- set up project with snowpack and @snowpack/plugin-sass
- import sass file in js
- run build with watch flag (`snowpack build --watch`)
- change contents of sass file
- check build output

- css output receives update
- css proxy output does not receive update
