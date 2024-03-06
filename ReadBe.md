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