---
title: "Intégrer React dans AstroJS : Guide complet"
description: "Apprenez à intégrer efficacement des composants React dans vos projets AstroJS pour créer des interfaces interactives performantes."
pubDate: "2024-12-10"
author: "Thomas Dubois"
image: "/public/images/astro.webp"
tags: ['React', 'AstroJS', 'Integration']
slug: "react-astro"
---


Astro n’est pas un simple framework statique : il permet aussi d’intégrer des composants issus d'autres frameworks tels que React, Vue, Svelte ou Solid. Ce guide se concentre sur l’intégration de React dans un projet Astro pour tirer profit de l’interactivité tout en maintenant des performances élevées.

## Pourquoi utiliser React dans Astro ?

React est populaire pour sa modularité et sa communauté. Dans un projet Astro, on peut continuer à tirer profit des bibliothèques React (formulaires, UI, logique complexe) tout en évitant le coût d’un rendu côté client complet.

## Mise en place

1. **Installation du plugin React**

```bash
npm install @astrojs/react
```

2. **Configuration dans astro.config.mjs**

```js
import react from '@astrojs/react';
export default {
  integrations: [react()],
};
```

3. **Utilisation dans une page Astro**

```astro
---
import MonComposant from '../components/MonComposant.jsx';
---

<MonComposant client:load />
```

## Astuces pour un rendu optimal

- Utilisez `client:idle` ou `client:visible` pour charger les composants React uniquement quand c’est nécessaire.
- Minimisez la taille des bundles React en utilisant des composants légers.
- Evitez d’utiliser React pour la totalité de la page, préférez Astro pour la structure principale.

## Comparaison des directives

| Directive         | Description                          |
|-------------------|--------------------------------------|
| `client:load`     | Charge au chargement de la page      |
| `client:idle`     | Charge après l’inactivité            |
| `client:visible`  | Charge à l’apparition dans le viewport |
| `client:only`     | Ne s’exécute que côté client         |

## Exemple d'utilisation

```jsx
export default function Compteur() {
  const [compte, setCompte] = useState(0);
  return (
    <button onClick={() => setCompte(compte + 1)}>
      Compte : {compte}
    </button>
  );
}
```

## Conclusion

React dans Astro permet d’allier le meilleur des deux mondes : la performance du statique et la souplesse du dynamique. En suivant ces bonnes pratiques, vos interfaces resteront réactives sans sacrifier la rapidité.