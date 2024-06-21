# Calcul de la précision
```js
import {html} from "@observablehq/stdlib";

// Définition initiale du tableau avec une ligne vide
let data = [
  { nom: "", age: "", ville: "" }
];

// Fonction pour afficher et gérer les entrées utilisateur
function tableauAvecSaisie() {
  const table = html`<table>
    <thead>
      <tr>
        <th>Nom</th>
        <th>Âge</th>
        <th>Ville</th>
      </tr>
    </thead>
    <tbody>
      ${data.map(row => html`
        <tr>
          <td>${inputField(row, 'nom')}</td>
          <td>${inputField(row, 'age')}</td>
          <td>${inputField(row, 'ville')}</td>
        </tr>`)}
    </tbody>
  </table>`;

  const button = html`<button>Ajouter une ligne</button>`;
  button.addEventListener('click', () => {
    data.push({ nom: "", age: "", ville: "" });
    table.value = tableauAvecSaisie();
  });

  return html`${table}${button}`;
}

// Fonction pour créer un champ de saisie
function inputField(row, key) {
  const input = html`<input type="text" value=${row[key]} placeholder=${key.charAt(0).toUpperCase() + key.slice(1)}`;
  input.addEventListener('input', () => {
    row[key] = input.value;
  });
  return input;
}

// Affichage du tableau interactif
tableauAvecSaisie()
```

<table>
    <thead>
        <tr>
            <th>Nom</th>
            <th>Age</th>
            <th>Ville</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Jana</td>
            <td>30</td>
            <td>New York</td>
        </tr>
        <tr>
            <td>Jane Smith</td>
            <td>25</td>
            <td>Los Angeles</td>
        </tr>
        <tr>
            <td>Michael Brown</td>
            <td>35</td>
            <td>Chicago</td>
        </tr>
    </tbody>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid black;
            padding: 8px;
            text-align: center;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</table>

```js
const button = html`<button>Ajouter une ligne</button>`;
  button.addEventListener('click', () => {
    const newRow = document.createElement('tr');
    newRow.innerHTML = `
      <td><input type="text" placeholder="Nom"></td>
      <td><input type="number" placeholder="Âge"></td>
      <td><input type="text" placeholder="Ville"></td>
    `;
    table.querySelector('tbody').appendChild(newRow);
  });
    return html`${table}${button}`;
```

```js
// Exemple de données (remplacez par vos propres données)
let data = [25, 20, 30, 40, 50];

// Calcul de la moyenne
const mean = data.reduce((acc, val) => acc + val, 0) / data.length;

// Calcul de la variance
const variance = data.reduce((acc, val) => acc + Math.pow(val - mean, 2), 0) / data.length;

// Calcul de l'écart-type
const standardDeviation = Math.sqrt(variance);
```

La moyenne est de **${mean}** et la variance de **${variance}**. L'écart-type est de **${standardDeviation}**. 


