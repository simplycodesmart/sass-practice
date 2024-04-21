- Sass -  Syntactically Awesome Style Sheets
- Sass has features that don’t exist in CSS yet like nesting, mixins, inheritance...
- command used to compilete sass to css => sass --watch input.scss output.css
- command used to compilete sass folder to css folder => sass --watch app/sass:public/stylesheets
- Sass supports two different syntaxes
    - .scss
    - .sass
- Control Flow Directives:
    - conditional logic : @if, @else if, @else
    - looping : @while, @for, @each
    - Imports  : @Imports
    - variables : $variables
    - Built-in Sass Functions : color: lighten($base-color, 20%)
    - @content : content projection
    - @extend : inheritance

- Variables
    - variables as a way to store information that you want to reuse throughout your stylesheet
    - Eg: $font-stack: Helvetica, sans-serif;
          $primary-color: #333;
- Nesting
    - Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML
     ```nav {
            ul {
                margin: 0;
                padding: 0;
                list-style: none;
            }

            li { display: inline-block; }

            a {
                display: block;
                padding: 6px 12px;
                text-decoration: none;
            }
        } 
- Partials
    -  A partial is a Sass file named with a leading underscore. You might name it something like _partial.scss. 
       The underscore lets Sass know that the file is only a partial file and that it should not be generated into a CSS file.
- Modules
    - You don’t have to write all your Sass in a single file. You can split it up however you want with the @use rule.
    - ```_base.scss
        $font-stack: Helvetica, sans-serif;
        $primary-color: #333;
        body {
            font: 100% $font-stack;
            color: $primary-color;
        }
    - ``` // styles.scss
        @use 'base';
        .inverse {
            background-color: base.$primary-color;
            color: white;
        }
    - ``` //CSS
        body {
            font: 100% Helvetica, sans-serif;
            color: #333;
        }
       .inverse {
            background-color: #333;
            color: white;
        }
- Mixins
    - A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. 
        It helps keep your Sass very DRY. You can even pass in values to make your mixin more flexible
    - ``` @mixin theme($theme: DarkGray) {
            background: $theme;
            box-shadow: 0 0 1px rgba($theme, .25);
            color: #fff;
        }
        .info {
             @include theme;
        }
        .alert {
             @include theme($theme: DarkRed);
        }
        .success {
            @include theme($theme: DarkGreen);
        }
    - ``` //CSS
        .info {
            background: DarkGray;
            box-shadow: 0 0 1px rgba(169, 169, 169, 0.25);
            color: #fff;
        }
        .alert {
            background: DarkRed;
            box-shadow: 0 0 1px rgba(139, 0, 0, 0.25);
            color: #fff;
        }
        .success {
            background: DarkGreen;
            box-shadow: 0 0 1px rgba(0, 100, 0, 0.25);
            color: #fff;
       }
- Extend/Inheritance
    - Using @extend lets you share a set of CSS properties from one selector to another
    - ``` /* This CSS will print because %message-shared is extended. */
            %message-shared {
            border: 1px solid #ccc;
            padding: 10px;
            color: #333;
        }
       - .message {
            @extend %message-shared;
         }
- Operators
    - ``` @use "sass:math";
- Install
    - ``` npm install -g sass
