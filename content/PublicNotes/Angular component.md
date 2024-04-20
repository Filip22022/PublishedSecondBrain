---
title: Angular component
Date created: 2024-04-16 13:42
Aliases:
tags: 
  - Public
---

Component is a basic UI building blocs in Angular applications. They consist of html templates, TypeScript logic and CSS styling. 

Components are responsible for the presentation and data binding

To be available to another component or application, component must belong to an `NgModule` - listed in the `declarations` field of `NgModule` metadata

## Generating a New Component

`ng generate component <name>` / `ng generate c <name>`

- `<name>`: `String` value


This command will by default create the following:
- `<component name>` directory
	- `<component name>.component.ts` component file
	- `<component name>.component.html` template file
	- `<component name>.component.css` css file
	- `<component name>.component.spec.ts` testing specification file

### Options


## Component Structure

```typescript
@Component({
  selector: 'some-componenet',
  templatUrl: `./some-component.component.html`
  inputs: ['someinput', 'id: some-id'],
  template: ` Name: {{ someName }}  Id: {{ id }} `,
})
export class SomeComponent {
```

### CSS Selector
A selector is the name of the corresponding html tag, for example the component above would be instantiated by `<some-component>`

### Template
A template is the html code used to render the component. It can be defined by providing an url to a html file with `templateUrl` property, or directly by putting the html code in a `template` property. These properties are mutually exclusive

For multiline direct template use backticks

### Style
Similarly to templates styles can be declared by referencing an external file or directly within the component.

`styleUrls` property will link a css file to the component, while `styles` property will accept an array of strings that contain css rules

## Style Guidelines

- Give components an _element_ selector instead of _attribute_ or _class_ selectors
	- element selector:  `'some-button'` - html: `<some-button></some-button>`
	- attribute selector: `'[some-button]'` - html: `<div some-button></div>`
- Extracts styles and templates to separate files if over 3 lines
- Use `@Input` and `@Output` decorators
- Order members with properties -> methods, and public -> private, alphabetized
- Limit logic in components to that required for the view and delegate the rest to [[Angular service|services]]
- Provide initial value for inputs or mark as optional with `?`