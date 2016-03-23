# tw-ng1-seed-module
A seed project to create Angular 1 modules

## Installation

Ensure `jspm` is installed
 
```
npm install -g jspm
```

Then simply clone `tw-ng1-seed-module` and install:

```
git clone https://github.com/kazuo/tw-ng1-seed-module.git my-module 
cd my-module
npm install
```

Finally, modify `package.json` to your liking (e.g. name, version, description, main, etc)

## Structure

The following is an example folder structure

```
| - /src
| --- /directives
| --- /templates
| --- /styles
|      | --- my-module.less
|      | --- styles.css
| --- module.js
| - test
```

By default, the `grunt:less` tasks will look for any `*.less` files within the `styles` folder then compiles it to
`styles.css`. Ensure that `styles.css` is added to git. You can simply import the style with any module you're
writing

```
import './../styles/styles.css!';
```

This goes for the same for importing templates for your Angular directives

```
import template from './../templates/my-module-directive.html!text';

export default function myModuleDirective()
{
    return {
        restrict: 'E',
        scope: {},
        template: template,
        link: function (scope, elem, attrs, ctrl) {
            // ...
        }
    };
}
```

And finally define your module in `src/module.js`:

```
import 'angular'
import myModuleDirective from './directives/myModuleDirective'

// Define your module and register any Angular components with it
angular.module('myModule', [])
    .directive('myModuleDirective', myModuleDirective);
```

SystemJS (ala `jspm`) will take care of the rest