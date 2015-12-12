# sass starter

This is a repo to help you get started with sass.

To build your sass files, navigate to the directory of your project and run:

```bash
sass --watch scss:css
```

If you haven't already installed the `sass` utility, do so by running

```bash
gem install sass
```

You may need to prefix that command with `sudo` so it reads
`sudo gem install sass`, and then enter in your password, depending on how
you've set up your dev machine file permissions.

# Things to know

You should only ever have one `main.css` file. It exists in the `css/`
directory. Don't *ever* edit this file directly. **EVER**.

The style changes you should need to make will be in the `.scss` files in the
`scss/` directory.

For example:

If you wanted to change the background color of the `#header` element, you would
open up `scss/partials/_header.scss` and add `background-color: blue;` to your
`#header` styles, so that the file reads something like this:

```scss
#header {
    background-color: blue; // This is the line we added

    nav {
        float: right;

        li {
            float: left;
        }
    }
}// #header
```

If your sass watcher command is running, your `main.css` file should have been
updated with your new style.

In this example, the header doesn't have any content in it, so you would either
have to add a `height:` property to your `#header` styles, or add some more
content in the `<div id="header"></div>` tag in your `index.html` file.

# Adding your own custom file

If you wish to add a new sass file to your project to help your stylesheet
organization, you need to do two things:

1. You need to add the file in your `scss/` directory. Following the convention
  of this repo, you should add it to a sub-directory, like to the already
  created `scss/partials/` directory or `scss/pages/` directory. So if I wanted
  to create generalized styles for the main content, I would create a new file
  called `_content.scss` and put it in the `scss/partials/` directory. So it
  would read `scss/partials/_content.scss`.

  Note: The reason you prefix those extra sass files with an underscore (`_`) is
  because the sass watcher won't compile those files directly. It will watch
  them for changes, but it won't create a file for each of those sass files.
  Your `main.scss` file is the one we want to compile over to css. If you add
  another file like `custom.scss`, to your `scss/` directory, it will create a
  new file in `css/custom.css`. You probably only want/need one css file as it
  will load faster than trying to load two separate css files.

1. In order to include it in your styles, you need to add the `@import` line
  to your `scss/main.scss` file:

  ```scss
  // Main SCSS, there should be no CSS in this page!


  // Global Specificity
  @import 'partials/variables.scss';

  // Site Specificity
  @import 'partials/header.scss';

  // Page Specificity
  @import 'pages/home-page.scss';

  // This is the one we're adding
  @import 'partials/content.scss';
  ```

  Note that we left out the underscore when we included it here. This is just
  the way we do it in sass.

After you do you that, any css/scss you add/change/remove to any of your scss
files, it will be reflected in your `css/main.css` file, and in turn, your html
page. s
