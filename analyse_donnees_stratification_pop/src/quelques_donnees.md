# Avant toute chose

<div class="grid grid-cols-1">
  <div class="card">

```js
const population = view(
  Inputs.text({
    label: "Quelle est la population d'étude ?",
    placeholder: "Entrer la population d'étude",
    width: 600
  })
);
const taille = view(Inputs.number([0, Infinity], {step: 1, label : "Taille de la popultation", placeholder: "400000",
    width: 600}));
const catégorie = view(
  Inputs.text({
    label: "Quelle est la variable à l'étude ?",
    placeholder: "Entrer la variable à l'étude",
    width: 600
  })
);
const part = view(Inputs.number([0, 100], {step: 1, label: "Part de la population ayant cette caractéristique en %", placeholder: "12",
    width: 600}));

const order = view(Inputs.toggle({label: "Ordonner la population", value: false}));
```
  </div>
</div>


<div class="grid grid-cols-2">
  <div class="card">

# Visualiation de la population

Vous avez choisi de parler de **${population}** en considérant une population de **${taille}** individus. Vous souhaitez prendre comme variable d'étude **${catégorie}** avec une part de la population estimée à **${part}**%.   

```js
// Dimensions du rectangle
const width = 285;
const height = 300;

let nb_max_rond = taille > 100000? 100000 : taille;
// Taille des cercles
let radius = Math.min(width, height) / Math.sqrt(2 * Number(nb_max_rond));
let width_ok = 0;
if(order === true){
 width_ok = width * part / 100;
}

// Création d'un tableau de données avec les positions et couleurs aléatoires
console.log(nb_max_rond)
let data = Array.from({ length: nb_max_rond }, () => {
  const color = Math.random() < part/100 ? 'blue' : 'lightblue'; // Utilisation de 'blue' pour n% et 'lightblue' pour les autres
  let x=0;
  if(order === true){
    if(color==="blue"){
       x = Math.random() * (width_ok - 2 * radius) + radius;
    }else{
       x = width_ok + Math.random() * ((width - width_ok) - 2 * radius) + radius;
    }

  }else{
     x = Math.random() * (width - 2 * radius) + radius;
  }
  const y = Math.random() * (height - 2 * radius) + radius;
  return { x, y, radius, color };
});

// Sélection du SVG
const svg = d3.select('body')
  .append('svg')
  .attr('width', width)
  .attr('height', height);

// Ajout des cercles
let rond = svg.selectAll('circle')
  .data(data)
  .enter()
  .append('circle')
  .attr('cx', d => d.x)
  .attr('cy', d => d.y)
  .attr('r', d => d.radius)  
  .style('fill', d => d.color);

display(svg.node());

```
  </div>
<div class="card">
    
# Tirage d'un échantillon

```js
const taille_echantillon = view(Inputs.range([0, taille], {step: 1, label: "Taille de l'échantillon", placeholder: "1000"}));
```

```js
// Dimensions du rectangle
const width = 500;
const height = 300;
let data_select = [];
if (taille_echantillon > 0 && taille_echantillon <= data.length) {
   // Générez n indices aléatoires uniques
  const indicesAleatoires = new Set();
  while (indicesAleatoires.size < taille_echantillon) {
    const randomIndex = Math.floor(Math.random() * data.length);
    indicesAleatoires.add(randomIndex);
  }
  data_select = Array.from(indicesAleatoires).map(index => data[index]);

}
const blueElements = data_select.filter(item => item.color === 'blue').length;
const proportionBlue = (blueElements / taille_echantillon) * 100;

let nb_max_rond_echantillon = taille_echantillon > 100000? 100000 : taille_echantillon;
// Taille des cercles
let radius = Math.min(width, height) / Math.sqrt(2 * Number(nb_max_rond));
let width_ok = 0;
if(order === true){
 width_ok = 500 * part / 100;
}

// Sélection du SVG
const svg = d3.select('body')
  .append('svg')
  .attr('width', width)
  .attr('height', height);

// Ajout des cercles
let rond = svg.selectAll('circle')
  .data(data_select)
  .enter()
  .append('circle')
  .attr('cx', d => d.x)
  .attr('cy', d => d.y)
  .attr('r', d => d.radius)  
  .style('fill', d => d.color);

display(svg.node());

```
Le tirage de **${taille_echantillon}** individus dans la population totale a choisi **${blueElements}** individus ayant la propriété à l'étude soit **${proportionBlue.toFixed(2)}**% de l'échantillon.

  </div>
</dv>
