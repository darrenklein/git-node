# git-to-json
> Read your project's latest git commit info and write it to JSON

> Upgrading from v1.X.X to v2.X.X? See the [upgrade guide]

[git-to-json] is a simple NPM module designed to retrieve the info for your project's most recent git commit and write it to a file in JSON format as an exportable module.

## Installation

#### NPM

``` SH
npm install --save git-to-json
```

## Usage

The default behavior of git-to-json is to read the info from your most recent git commit and write it to the file `git-commit-info.js`, adjacent to your `package.json` file.

Example of a `git-commit-info.js` file:

``` JS
module.exports = {"commit":"5aqfaa6741871zz5e67683a012a0062bdbd46a8z","author":"Foo Bar <foo@bar.com>","date":"Sun Feb 11 13:37:29 2018 -0500","message":"My cool git commit"}
```

To run git-to-json, simply include the following command in the NPM script of your choice:

``` JSON
git-to-json
```

for example, in your project's `package.json` file:

``` JSON
"scripts": {
  "start": "git-to-json && node index.js"
}
```

It probably goes without saying, but this app requires that it is run in a directory that has been established as a git repository.

### Options

As noted, the default behavior is to create a file named `git-commit-info.js` adjacent to your `package.json` file. You can also provide an optional directory and customize the file's name and content with the following options:

``` JSON
--dir <path/to/dir>     specify the relative file path
--name <filename.js>    specify the name of the file
--upcasekeys            set the keys of the exported JSON as uppercase
```

For example:

``` JSON
git-to-json --dir gitignore --name commit-info
```

will result in `gitignore/commit-info.js`.

As of v2.X.X, you can provide a file path of any depth:

``` JSON
git-to-json --dir gitignore/git-info/latest --upcasekeys
```

will result in `gitignore/git-info/latest/git-commit-info.js` with uppercased keys - "COMMIT", etc...

If the directory provided does not exist, git-to-json will create it. If it does exist, git-to-json will output the file to the existing directory.

## Notes

This module has been formatted according to ESLint's [eslint-config-airbnb-base] rules.

[upgrade guide]: upgrade_guides/v1-to-v2-upgrade-guide.md
[git-to-json]: https://www.npmjs.com/package/git-to-json
[eslint-config-airbnb-base]: https://www.npmjs.com/package/eslint-config-airbnb-base