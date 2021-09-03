## A Component in a Render Function

Here is a .render() method that returns an HTML-like JSX element:

```
class Example extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
}
```

You’ve seen render methods return <div></div>s, <p></p>s, and <h1></h1>s, just like in the above example.

Render methods can also return another kind of JSX: component instances.

```
class OMG extends React.Component {
  render() {
    return <h1>Whooaa!</h1>;
  }
}
 
class Crazy extends React.Component {
  render() {
    return <OMG />;
  }
}
```

## Require A File

When you use React.js, every JavaScript file in your application is invisible to every other JavaScript file by default. ProfilePage.js and NavBar.js can’t see each other.

If you want to use a variable that’s declared in a different file, such as NavBar, then you have to import the variable that you want. To import a variable, you can use an import statement:

```
import { NavBar } from './NavBar.js';
```

If you use an import statement, and the string at the end begins with either a dot or a slash, then import will treat that string as a filepath. import will follow that filepath, and import the file that it finds.

If your filepath doesn’t have a file extension, then “.js” is assumed. So the above example could be shortened:

```
import { NavBar } from './NavBar';
```

## export
When you import a variable from a file that is not the current file, then an import statement isn’t quite enough. You also need an export statement, written in the other file, exporting the variable that you hope to grab.

export comes from ES6’s module system, just like import does. export and import are meant to be used together, and you rarely see one without the other.

There are a few different ways to use export. In this course, we will be using a style called “named exports.” Here’s how named exports works:

In one file, place the keyword export immediately before something that you want to export. That something can be any top-level var, let, const, function, or class:

```
// Manifestos.js:
 
export const faveManifestos = {
  futurist: 'http://www.artype.de/Sammlung/pdf/russolo_noise.pdf',
  agile: 'https://agilemanifesto.org/iso/en/manifesto.html',
  cyborg:   'http://faculty.georgetown.edu/irvinem/theory/Haraway-CyborgManifesto-1.pdf'
};
```
You can export multiple things from the same file:

```
// Manifestos.js:
 
export const faveManifestos = {
  futurist: 'http://www.artype.de/Sammlung/pdf/russolo_noise.pdf',
  agile:  'https://agilemanifesto.org/iso/en/manifesto.html',
  cyborg:   'http://faculty.georgetown.edu/irvinem/theory/Haraway-CyborgManifesto-1.pdf'
};
 
export const alsoRan = 'TimeCube';
```
In a different file, import the name of the var, let, const, function, or class from the first file:

```
// App.js:
 
// Import faveManifestos and alsoRan from ./Manifestos.js:
import { faveManifestos, alsoRan } from './Manifestos';
 
// Use faveManifestos:
console.log(`A Cyborg Manifesto:  ${faveManifestos.cyborg}`); 
```
