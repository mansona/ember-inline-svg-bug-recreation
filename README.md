# ember-inline-svg bug recreation

This repo is a reproduction of a bug that we noticed in [Embroider](https://github.com/embroider-build/embroider) relating to symbolic links.

## Steps to reproduce

If you run `pnpm install` and `pnpm start` in this repo without doing any symbolic links you should see something that looks like this: 

(image)

which is an inlined svg using [ember-inline-svg](https://github.com/minutebase/ember-inline-svg)

to reproduce the issue follow these steps: 

- `rm -rf node_modules` (if you have run `pnpm i` already)
- `mkdir /tmp/some-strange-place`
- `ln -s /tmp/some-strange-place node_modules`
- `pnpm i`
- `pnpm start`
- 💥 Error!

The error is 

```
Module not found: Error: Can't resolve '../svgs' in '/path-to-repo/node_modules/.embroider/rewritten-app/helpers'
```
