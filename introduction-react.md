JSX est une extension syntaxique de JavaScript.
JSX décrit l'UI.

`const lilRapper = <h1>Young Mulah, baby</h1>`

React sépare les responsabilités par unités appelées *composants*, chacun possédant la logique.
React n'a pas besoin de JSX mais beaucoup le trouvent pratique.

https://reactjs.org/docs/introducing-jsx.html

We split JSX over multiple lines for readability. While it isn’t required, when doing this, we also recommend wrapping it in parentheses to avoid the pitfalls of automatic semicolon insertion

https://stackoverflow.com/questions/2846283/what-are-the-rules-for-javascripts-automatic-semicolon-insertion-asi

React.createElement() performs a few checks to help you write bug-free code but essentially it creates an object like this:

// Note: this structure is simplified
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};

These objects are called “React elements”. You can think of them as descriptions of what you want to see on the screen. React reads these objects and uses them to construct the DOM and keep it up to date.

