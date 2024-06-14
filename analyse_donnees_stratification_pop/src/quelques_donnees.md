# Avant toute chose

```js
const text = view(Inputs.text());
const name = view(
  Inputs.text({
    label: "Name",
    placeholder: "Enter your name",
    value: "Anonymous"
  })
);
const z = view(Inputs.range([0, 10000000], {step: 1, value: 0}));
const m = view(Inputs.number([0, Infinity], {step: 1, label: "Favorite integer", placeholder: ""}));
```


Vous avez choisi de parlé de ${text} en considérant une population de ${z} individus.Vous souhaitez prendre comme variable.
