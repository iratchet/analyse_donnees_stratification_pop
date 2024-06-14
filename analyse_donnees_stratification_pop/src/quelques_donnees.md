# Avant toute chose
---
Quelle est le sujet que vous voulez traiter ?
---

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Zone de Texte Simple en JavaScript</title>
</head>
<body>

<!-- Zone de texte simple -->
<input type="text" id="zoneTexte" placeholder="Saisissez du texte ici">

<script>
// Exemple de manipulation de la zone de texte en JavaScript
const zoneTexte = document.getElementById('zoneTexte');

// Écouter les événements de saisie dans la zone de texte
zoneTexte.addEventListener('input', function() {
    console.log("Texte saisi :", zoneTexte.value);
});
</script>

</body>
</html>

---
Quel est la taille de la population considérée ?
---
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Zone de Texte Numérique en JavaScript</title>
</head>
<body>

<!-- Zone de texte numérique -->
<label for="zoneTexteNumerique"></label>
<input type="number" id="zoneTexteNumerique" min="0" max="100" step="1" placeholder="0">

<script>
// Sélectionner la zone de texte numérique
const zoneTexteNumerique = document.getElementById('zoneTexteNumerique');

// Écouter les événements de saisie dans la zone de texte numérique
zoneTexteNumerique.addEventListener('input', function() {
    const valeur = zoneTexteNumerique.value;
    console.log("Valeur numérique saisie :", valeur);

    // Optionnel : Validation supplémentaire ou actions en fonction de la valeur saisie
    if (valeur < 0 || valeur > 100) {
        console.log("Valeur hors des limites autorisées (0-100).");
    }
// Ajouter un écouteur d'événement sur le formulaire pour capter la soumission
formulaire.addEventListener('submit', function(event) {
    // Empêcher le comportement par défaut du formulaire (rechargement de la page)
    event.preventDefault();

    // Récupérer la valeur saisie par l'utilisateur
    const valeur = zoneTexte.value.trim();

    // Vérifier si la valeur est vide
    if (valeur === '') {
        resultat.textContent = 'Veuillez saisir une valeur.';
    } else {
        // Exemple d'opération : convertir la valeur en majuscules
        const valeurEnMajuscules = valeur.toUpperCase();

        // Afficher le résultat dans le paragraphe
        resultat.textContent = `Vous avez saisi : ${valeurEnMajuscules}`;
    }
});
});
</script>

</body>
</html>

---
Quelle est la variable que vous souhaitez prendre en compte ?
---

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Zone de Texte Simple en JavaScript</title>
</head>
<body>

<!-- Zone de texte simple -->
<input type="text" id="zoneTexte" placeholder="Saisissez du texte ici">

<script>
// Exemple de manipulation de la zone de texte en JavaScript
const zoneTexte = document.getElementById('zoneTexte');

// Écouter les événements de saisie dans la zone de texte
zoneTexte.addEventListener('input', function() {
    console.log("Texte saisi :", zoneTexte.value);
});
// Ajouter un écouteur d'événement sur le formulaire pour capter la soumission
formulaire.addEventListener('submit', function(event) {
    // Empêcher le comportement par défaut du formulaire (rechargement de la page)
    event.preventDefault();

    // Récupérer la valeur saisie par l'utilisateur
    const valeur = zoneTexte.value.trim();

    // Vérifier si la valeur est vide
    if (valeur === '') {
        resultat.textContent = 'Veuillez saisir une valeur.';
    } else {
        // Exemple d'opération : convertir la valeur en majuscules
        const valeurEnMajuscules = valeur.toUpperCase();

        // Afficher le résultat dans le paragraphe
        resultat.textContent = `Vous avez saisi : ${valeurEnMajuscules}`;
    }
});
</script>
</body>
</html>

---
Vous avez choisi de parler du en considérant une population de . Prenons en compte la varaible de ${valeurEnMajuscules}. 

```js
// Options pour le formatage de la date
const options = { year: 'numeric', month: '2-digit', day: '2-digit' };
const nom_poste_recherche = "ARBAS";
const date_recherche = new Date("2023-05-21");

// Conversion de l'objet Date en chaîne de caractères au format souhaité
const dateString = date_recherche.toLocaleDateString('fr-FR', options).split('/').join('-');

const objetTrouve = meteo_31_2023_2024_extrait.find(
  obj => obj.nom_poste === nom_poste_recherche && obj.date.getTime() === date_recherche.getTime()
);
display(objetTrouve)
```