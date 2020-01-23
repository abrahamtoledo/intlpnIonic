# intlpnIonic
Simple version of intl-phone number input for Ionic

Heavily based on https://github.com/Bluefieldscom/intl-tel-input

Using https://github.com/Bluefieldscom/intl-tel-input inside Ionic framework creates incompatibilities, as by default, Ionic will handle scroll event which makes the phone number plugin not working, as the popup to choose a country is not scrollable.

There is as well a filter to format a number in either international or national mode.

#### Note from the [original author](https://github.com/pierre-vigier/) 
Implemenation is dirty for now, as i need that as soon as possible.


## Getting Started
1. Install the package
 ```bash
 npm install "git+https://github.com/abrahamtoledo/intlpnIonic.git#v0.4.0" --save
 ```
 or include it in your project dependencies.

2. Link the stylesheet in index.html
  ```html
  <link rel="stylesheet" href="path/to/intlpn.css">
  ```

3. Import the library into the module where it is going to be used
  ```ts
  import "path/to/intlpnIonic.js";
  ```

4. load the directive
  ```js
  export default angular
      .module('myApp', [
          'ionic',
          'intlpnIonic', 
          ...
          ]
      )...
  ```

5. Usit in your template
  ```html
  <intlpn 
      ng-model="phone.number" 
      placeholder="placeholder" 
      only-country="['us','fr']">
  </intlpn>
  ```

6. for formatting a number, use filter `intlpnFormat`, default international mode
  ```html
  <span>{{ model.phoneNUmber | intlpnFormat }}</span><!-- number will be in internaional mode -->
  <span>{{ model.phoneNUmber | intlpnFormat:'national' }}</span><!-- number will be in national mode -->
  ```


## Configurations

A set of options can be passed to the component:
* _ng-model_: model to store the phone number in, will be set only on valid number (verified by google phonenumber utils)
* _placeholder_: Placeholder of the input
* _default-country_: Country selected by default
* _only-country_: to restrain the list of available countries, if not given full list, format : ['fr','cn']
* _national-node_: true: allow user to input phone number in national mode (without + and the international code)
* _box-header-class_: Class of the header bar of the modal to select countries
* _box-header-title_: Title of the modal to select countries
* _search-placeholder_: placeholder text of the search box in the header to select countries
* _country-iso-code_: you can bind a scope variable here, that will be updated with the current iso code of the selected country, read-only
* _country-dial-code_: you can bind a scope variable here, that will be updated with the current dial code of the selected country, read-only
* _close-icon-spec_: Specification for the close icon to use in search country modal . Some icons can contain multiple
  layers. An example inconspec is `{cls: 'icon icon-close', paths: ['path1', 'path2', ...]}`, for multilayer icons. For single layer icons leave it as `paths: []`
* _search-icon-spec_: Icon spec for search button. See __*close-icon-spec*__.


Sample code:
```html
<intlpn 
    ng-model="model.field" 
    placeholder="Placeholder" 
    default-country="fr" 
    only-country="['fr','cn','us','it']" 
    national-mode="true" 
    box-header-class="bar-energized" 
    box-header-title="Search country" 
    search-placeholder="search"
    country-iso-code="model.isocode" 
    country-dial-code="model.dialcode"
    close-icon-spec="{cls: 'icon icon-close', paths: ['path1', 'path2']}"
    search-icon-spec="{cls: 'icon icon-search', paths: ['path1', 'path2', 'path2']}"
    >
</intlpn>
```

## Attributions
* Original repo [pierre-vigier/intlpnIonic](https://github.com/pierre-vigier/intlpnIonic.git).
* All the logic in managing flag and dialCode from [intl-tel-input](https://github.com/Bluefieldscom/intl-tel-input).
* Formatting/validation/example number code from [libphonenumber](http://libphonenumber.googlecode.com).
