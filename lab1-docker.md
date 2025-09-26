**Section 1.0**



**1. Pensez-vous que cela revient à exécuter une machine virtuelle ?**

**Non, ce n’est pas la même chose. Un conteneur s’appuie directement sur le noyau de l’hôte, tandis qu’une machine virtuelle embarque son propre système d’exploitation complet. Résultat : les conteneurs sont plus légers et démarrent beaucoup plus rapidement. En revanche, les VMs apportent un niveau d’isolation plus fort.**



**2. Un conteneur est une abstraction ?**

**b. d’application.**

**En effet, un conteneur regroupe une application et toutes ses dépendances nécessaires à son exécution, contrairement à une VM qui simule aussi le matériel.**



**3. Est-il possible d’utiliser à la fois des machines virtuelles et des conteneurs dans un même environnement ? Comment ?**

**Oui, tout à fait. C’est même une pratique répandue. Par exemple, on peut exécuter Docker à l’intérieur d’une VM pour renforcer la sécurité, ou encore utiliser les VMs pour héberger certains services critiques et les conteneurs pour déployer des applications légères et facilement scalables. Beaucoup d’architectures modernes combinent les deux approches selon les besoins.**

**Après docker container run alpine echo "hello from alpine"**

**Le texte s’affiche puis le conteneur s’arrête aussitôt. C’est normal : la commande s’exécute puis le conteneur n’a plus rien à faire.**



**Après docker container run alpine /bin/sh**

**Le conteneur se lance puis se ferme immédiatement, car le shell démarre sans terminal interactif et donc se termine aussitôt.**



**Après docker container run -it alpine /bin/sh**

**Cette fois, vous obtenez un shell interactif. Les options -i (mode interactif) et -t (allocation d’un pseudo-terminal) permettent de dialoguer avec le conteneur.**



**Le résultat de docker container ls -a**

**Cette commande liste tous les conteneurs, qu’ils soient en cours d’exécution ou arrêtés. On y voit leur ID, l’image utilisée, la commande lancée et leur état actuel.**



**Pourquoi autant de conteneurs de la même image alpine ?**

**Parce qu’à chaque docker run, Docker crée une nouvelle instance de conteneur, même si c’est toujours à partir de la même image. Chaque conteneur reste isolé, avec son propre système de fichiers.**



**Comment revenir au conteneur avec le fichier hello.txt ?**

**Il faut relancer le conteneur précis où ce fichier avait été créé, avec docker container start <ID>. Ensuite, on peut l’explorer via docker container exec <ID> ls. Le fichier reste uniquement à l’intérieur de ce conteneur-là.**

