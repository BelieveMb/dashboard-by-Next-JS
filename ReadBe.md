Lorsque vous utilisez create-next-apppour démarrer un nouveau projet, Next.js vous demandera si vous souhaitez utiliser Tailwind. Si vous sélectionnez yes, Next.js installera automatiquement les packages nécessaires et configurera Tailwind dans votre application.
# ipour installer les packages du projet. -> npm i, npm run dev

## Style global
** pour le style global de l'application ./app/ui/global.css
Si vous regardez à l'intérieur du /app/uidossier, vous verrez un fichier appelé global.css.
il est généralement recommandé de l'ajouter à votre composant de niveau
supérieur. Dans Next.js,
**pour importer -> import '@/app/ui/global.css';

## Module CSS
créer dans ./app/ui/monfichier.module.css -> mettre un style natif css
* pour l'utiliser 
import styles from '@/app/ui/home.module.css';
<div className={styles.shape} />;

Les modules Tailwind et CSS sont les deux manières les plus courantes de styliser les applications Next.js. 
* Tailwind vient par défaut.

## Librarie clsx
pour mettre une condition dans la className
 <span
      className={clsx('inline-flex items-center rounded-full px-2 py-1 text-xs',
      {'bg-gray-100 text-gray-500': status === 'pending',  'bg-green-500 text-white': status === 'paid',        },
      )}    >

## Optimiser la police
* le module next/font  : en dev, il télécharge et stock de police et en prod,il ne fera plus de req pour récup de polices
* dans app/ui/ crée un font.ts, importer les polices comme suit :
import { Inter } from 'next/font/google';

export const inter = Inter({ subsets: ['latin'] });

utiliser comme suit : 
      <body className={`${inter.className} antialiased`}>{children}</body>

## optimiser les images
Pour optimiser automatiquement les images, on utilise le composant next/image ou
utiliser la méthode de HTML src='/monImg.jpg'
* le composant <Image>
-> import Image from 'next/image';
->  <Image
        src="/hero-desktop.png" ... />

## Système de routage ( Routes )
* Route imbriqué -> acme.com/dashboard/invoices/
Vous pouvez créer des interfaces utilisateur distinctes pour chaque itinéraire à
l'aide de fichiers layout.tsxet page.tsx.
* page.tsxest un fichier Next.js spécial qui exporte un composant React, 
* Pour créer un itinéraire imbriqué, vous pouvez imbriquer des dossiers les uns
  dans les autres et page.tsx y ajouter des fichiers.
Par exemple:
app/page.tsx -> /
app/dashboard/page.tsx -> /dashboard

/app/dashboard/page.tsx est associé au chemin /dashboard . Créons la page pour
voir comment elle fonctionne !
* # avec NExT, les routes sont définies dans de dossiers, par exemple si je veux avoir la route /voiture, je dois crée un dossier voiture et après j'ajoute un fichier page.tsx,
* lorsque j'appelle /voiture, il appelera le fichier page.tsx qui est dans le
  dossier voiture

## mise en page -> Layout
* layout.tsx fichier spécial pour créer une interface utilisateur partagée entre
  plusieurs pages.
* L'un des avantages de l'utilisation des mises en page dans Next.js est que
  lors de la navigation, seuls les composants de la page sont mis à jour tandis
  que la mise en page ne sera pas restituée. C'est ce qu'on appelle le rendu
  partiel :

## Navigation entre les pages
*  le composant <Link /> pour créer des liens entre les pages de votre
   application. <Link>vous permet d'effectuer une navigation côté client avec
   JavaScript.
-> import Link from 'next/link';
-> <Link href={link.href} ... >....</Link>

Comme vous pouvez le voir, le Linkcomposant est similaire à l'utilisation <a>de balises, mais au lieu de <a href="…">, vous utilisez <Link href="…">.

## Division automatique du code et prélecture
* Diviser le code par itinéraires signifie que les pages sont isolées. Si une
  certaine page génère une erreur, le reste de l'application fonctionnera
  toujours.
* De plus, en production, chaque fois que <Link>des composants apparaissent dans
  la fenêtre d'affichage du navigateur, Next.js pré-extrait automatiquement le
  code de l'itinéraire lié en arrière-plan. Au moment où l'utilisateur clique
  sur le lien, le code de la page de destination sera déjà chargé en
  arrière-plan, et c'est ce qui rend la transition de page quasi instantanée !

## Affichage des liens actifs
Un modèle d'interface utilisateur courant consiste à afficher un lien actif pour indiquer à l'utilisateur sur quelle page il se trouve actuellement. Pour ce faire, vous devez obtenir le chemin actuel de l'utilisateur à partir de l'URL. Next.js fournit un hook appelé usePathname()que vous pouvez utiliser pour vérifier le chemin et implémenter ce modèle.

DepuisusePathname()est un hook, vous devrez le transformer nav-links.tsxen
composant client. Ajoutez la directive de React "use client"en haut du fichier,
puis importez usePathname()depuisnext/navigation :
