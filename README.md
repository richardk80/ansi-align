This is a fix for using Astro JS and for installing an Astro JS project on Vercel.

This will most likely work for other frameworks too.

Since this package hasn't been updated in 3 years, I decided to update it myself.

Inside the index.js file, it used to say this: const stringWidth = require('string-width')

This would break a lot of projects built with modern frameworks that work with NodeJS since you can't have a .js file with require in it.

I changed this to const stringWidth = import('string-width') and now any of my projects that use it will work as before.

I know people might ask questions and come up with a better solution, and my answer to those questions and such will be Occam's Razor. Just changing require to import is the most simple solution and it works.

To make this work in your project you just have to add something to your package.json file depending on your package manager (npm, yarn, pnpm, bun)

NPM:
```
"overrides": {
    "ansi-align": "git+https://github.com/richardk80/ansi-align.git"
}
```
YARN:
```
"resolutions": {
    "ansi-align": "git+https://github.com/richardk80/ansi-align.git"
}
```
PNPM:
```
"pnpm": {
    "overrides": {
      "ansi-align": "git+https://github.com/richardk80/ansi-align.git"
    }
}
```
BUN:

There's no native solution at the moment, but you can add this to your "dependencies" list in package.json and it should work: 

```"ansi-align": "git+https://github.com/richardk80/ansi-align.git"```

After doing this, delete any .lock files you have in the root of your project that pertain to your package manager of choice, delete your node_modules folder and run whatever command you need to reinstall your node modules.

Everything should be working once again.
