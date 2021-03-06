# Ember-multiselect-checkboxes [![](https://travis-ci.org/RSSchermer/ember-multiselect-checkboxes.svg?branch=master)](https://travis-ci.org/RSSchermer/ember-multiselect-checkboxes)

Simple Ember component for allowing multiple selection using checkboxes from a certain collection (a hasMany property
for example).

## Demo
Demo available [here](https://rsschermer.github.io/ember-multiselect-checkboxes/).

## Installation

`ember install ember-multiselect-checkboxes`

## Usage

Example:

``` handlebars
{{multiselect-checkboxes options=users labelProperty='name' selection=selectedUsers}}
```

This component can be used with an array of primitives as the options, an array of plain javascript objects as the
options, or an array of Ember objects as the options. The following properties are available and should always be set:

* `options`: a collection of Ember objects that can be selected.
* `selection`: the subset of the options that is currently selected. The selection will automatically be updated when
  the user checks or unchecks options through Ember's two-way bindings.

When using this component with an array of javascript objects or an array of Ember objects you should also set the
`labelProperty` attribute:

* `labelProperty`: the property on the plain javascript object or the Ember object that will be used as a label for the
  checkbox.

When using this component with an array of javascript objects or an array of Ember objects you may optionally specify
the `valueProperty` attribute:

* `valueProperty`: the property on the plain javascript object or the Ember object that will be used to represent this
  object in the selection. Example: when using an array of car objects as the options, if you set the `valueProperty`
  as their "color" property, the selection will be an array of color strings (not an array of cars).

It's also possible to pass a custom template block should you want to customize the option list in some way (requires
Ember 1.13 or higher). The above example without a custom template block is essentially equivalent to the following
example with a custom template block:

```handlebars
{{#multiselect-checkboxes options=users labelProperty='name' selection=selectedUsers as |label isSelected|}}
  <li>
    <label>
      {{input type="checkbox" checked=isSelected}}
      {{label}}
    </label>
  </li>
{{/multiselect-checkboxes}}
```
