# Mojular GOV.UK Elements

This is the implementation of [GOV.UK elements](http://govuk-elements.herokuapp.com/) for use with Mojular.

## Installation

Install via NPM:

```js
npm install https://github.com/mojular/govuk-elements/tarball/master --save
```

To use in your project with Gulp add the following to your `gulpfile.js`:

```js
var gulp = require('gulp');
var sass = require('gulp-sass');
var sourcemaps = require('gulp-sourcemaps');

var importPaths = [];
importPaths.push(require('mojular-govuk-elements').getPaths('sass'));

gulp.task('sass', function() {
  var result = gulp.src('path/to/your/local/styles/**/*.scss')
    .pipe(sourcemaps.init())
    .pipe(sass({ includePaths: [].concat.apply([], importPaths) }).on('error', sass.logError))
    .pipe(sourcemaps.write('./'))
    .pipe(gulp.dest(paths.dest + 'css/'));
```

Each Mojular module containing Sass files exposes its paths in `package.json` file.
These then can be passed to Sass compiler via `includePaths` and allows to import them
directly by file names as if they were local. Each module which includes Sass files has
`getPaths()` method which gets the list of paths to Sass files. Additional modules can
be `push`ed as required.

## Usage

The whole module can be imported in your Sass file:

```scss
@import 'govuk';
```

Or individual modules can be imported:

```scss
@import 'govuk/fonts';
@import 'govuk/base';
@import 'govuk/typography';
@import 'govuk/layout';

@import 'govuk/elements/global-header';
@import 'govuk/elements/global-subheader';
@import 'govuk/elements/global-footer';
@import 'govuk/elements/phase-banner';
```

See the list of modules in [`assets/sass/govuk`](/mojular/govuk-elements/tree/master/assets/sass/govuk/elements).

HTML Examples can be found on [GOV.UK generated styleguide](http://ministryofjustice.github.io/bower-playground/GOV.UK/).