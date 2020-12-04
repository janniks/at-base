<h1 align="center" style="font-weight: bold !important">basetag ⚾️</h1>

<p align="center">
  <strong>basetag</strong> lets you require local modules relative to your Node.js project base path
</p>

<p align="center">
  <a href="https://github.com/janniks/basetag/actions">
    <img src="https://github.com/janniks/basetag/workflows/build/badge.svg" alt="Build status" />
  </a>
  <a href="https://www.npmjs.org/package/basetag">
    <img src="https://img.shields.io/npm/v/basetag.svg" alt="Package version" />
  </a>
  <a href="https://npmcharts.com/compare/basetag?minimal=true">
    <img src="https://img.shields.io/npm/dm/basetag.svg" alt="Downloads per month" />
  </a>
  <a href="https://npmcharts.com/compare/basetag?minimal=true">
    <img src="https://img.shields.io/npm/dt/basetag.svg" alt="Total downloads" />
  </a>
  <a href="https://github.com/janniks/basetag/blob/master/LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT license" />
  </a>
  <a href="https://twitter.com/intent/follow?screen_name=jnnksbrt">
    <img src="https://img.shields.io/twitter/follow/jnnksbrt.svg?label=Follow%20@jnnksbrt" alt="Follow @jnnksbrt on Twitter" />
  </a>
</p>

<h3 align="center">
  <a href="#installation-">Installation</a>
  <span> · </span>
  <a href="#why-%EF%B8%8F">Why?</a>
  <span> · </span>
  <a href="#how-">How?</a>
  <span> · </span>
  <a href="#license-%EF%B8%8F">License</a>
</h3>

## Installation 🛠

`npm i -S basetag`

☝️ and that's it!
You can now use the `$` basetag prefix.
No need to require basetag itself anywhere.

## Why? ⚡️

**What does `basetag` solve?**

In Node.js applications we sometimes want to import local modules that are in different far away subdirectories.
This can lead to very messy looking `require` statements.
Using basetag you can import modules with `$/` as the project base path.
If you're not convinced, check out the example below...

🤯 _The modern **basetag** way:_

```js
const balls = require('$/baseball/balls')           // ✅
```

😓 _The traditional (often messy) way:_

```js
const balls = require('../../../../baseball/balls') // ❌
```

## How? 💭

### How do I use `basetag`?

It's really all described above and there's not much to it.
Look at the code in [`test/example/`](test/example/) for an executable example.
A larger project can have many nested subfolders as shown in the directory structure below.
Of course a _real_ project would have more files in those subdirectories but for simplicity we'll leave those out.
Using basetag you can reference modules from the base `example/` path, rather than using relative directories (i.e. `../../..`).

```
example/
├── its/
│   └── baseballs/
│       └── all/
│           └── the/
│               └── way/
│                   └── down.js
├── somewhere/
│   └── deep/
│       └── and/
│           └── random.js
└── index.js
```

### How does `basetag` work?

It's rather simple.
After installing basetag as a dependency a `postinstall` script creates a symlink that points from `node_modules/$` to your project base path.
Everytime you use a `require` with `$/…` Node.js will look inside the `$` package (i.e. our new symlink).
The lookup is routed natively to your project files.

To Node.js, both methods of requiring look the same, because the files are literally the same files.
Both methods can be used in the same project and Node.js will cache imports correctly.

## Compatibility

`basetag` supports macOS, Linux, and Windows as of version `1.1.0`.

## License ⚖️

[MIT](LICENSE)
