## How to use

1. Clone this repository.

```sh
git clone https://github.com/kais-viz/portfolio
```

2. Go to the cloned directory (e.g. `cd portfolio`).

3. Run `npm install`.

4. Customize your resume

5. Preview resume with `npm run serve`.

6. Build it with `npm run build`.

7. Make sure `/dist` is not ignored by `.gitignore`.

8. Push changes to github.

9) Deploy it to github pages using instructions here: https://cli.vuejs.org/guide/deployment.html#pwa

```sh
#!/usr/bin/env sh

# abort on errors
set -e

# build
npm run build

# navigate into the build output directory
cd dist

git init
git add -A
git commit -m 'deploy'

# if you are deploying to https://<USERNAME>.github.io
# git push -f git@github.com:kais-viz/kais-viz.github.io.git master

# if you are deploying to https://<USERNAME>.github.io/<REPO>
git push -f git@github.com:kais-viz/portfolio.git master:gh-pages

cd -
```

## License

Code is licensed under the [MIT License](LICENSE).
