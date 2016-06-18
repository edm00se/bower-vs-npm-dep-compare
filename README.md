# Comparing Front-End Dependency Management

This repository is a basic comparison between a simple "hello world" style web site, complete with jQuery and Bootstrap 3, for a basic use case.

## Bower vs NPM

This isn't my main discussion regarding the approach of  bower vs npm, for package management. For that, you can [go check it out on my blog]().

This project makes use of a single, simple `index.html` with jQuery and Bootstrap 3, with a sass file, for demonstrative purposes.

### Why Not Grunt/Gulp/Other?

I like grunt and love gulp and I use both frequently, but seeing how I neither wanted to distract from the task at hand nor make anything more confusing with different configs for a task runner, I decited to use a more purist ["npm build pipeline"](https://css-tricks.com/why-npm-scripts/), in which the build steps are all defined as `npm run ...` scripts, with superceding main scripts to do the joint operations. I mostly adapted my `npm run` scripts [from this nice article on "npm for everything"](http://beletsky.net/2015/04/npm-for-everything.html); which, coincidentally, is good reading material for the subject of this project.

### To Use

- `git clone https://github.com/edm00se/bower-vs-npm-dep-compare.git` (clone this repository)
- `cd bower-test` (change directory into one of the two tests)
- run `npm install` (for the `bower-test` project, a post-install script will run the `bower install` so you don't have to)
- `npm run serve` to build, watch, and serve (via [`lite-server`](https://github.com/johnpapa/lite-server), [which is worth checking out](https://scotch.io/tutorials/develop-quickly-and-painlessly-with-lite-server) for a default `browser-sync` configuration for front-end dev)

### File Tree

```bash
├── README.md
├── bower-test
│   ├── bower.json
│   ├── bs-config.json
│   ├── js
│   │   ├── app.js
│   │   └── vendor.js
│   ├── package.json
│   ├── public
│   │   ├── css
│   │   │   └── main.min.css
│   │   ├── index.html
│   │   └── js
│   │       ├── app.min.js
│   │       └── vendor.min.js
│   └── sass
│       └── main.scss
└── npm-test
    ├── bs-config.json
    ├── js
    │   └── app.js
    ├── package.json
    ├── public
    │   ├── css
    │   │   └── main.min.css
    │   ├── index.html
    │   └── js
    │       ├── app.js
    │       └── app.min.js
    └── sass
        └── main.scss
```

### Notable Differences

Despite my best efforts,  you can note the following differences between the two implementations:
- the `npm-test` project actually builds both app and vendor JS into a single file
- the `npm-test` project _must_ have the jquery dependency explicitly defined (peer dependency) \*
- the `bower-test` project builds a separate vendor JS file (could easily concatenate them)
- the `bower-test` incorporates the jquery dependency based on its listed requirement in the bower registry (sub dependency) \*

\* Note: these differences appear to be based on their respective registry's definition, not directly reflecting the capabilities of the respective package manager.

## License

MIT
