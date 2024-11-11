# Ansible

## Généralités

### C'est quoi Ansible?

### Problématique d'Ansible

Ansible est conçu pour résoudre des problèes liés à la gestion et à l'automatisation de l'infrastructure informatique, en particulier pour les environnements de grande envergure ou complexes. Les principales problématiques sont les suivantes :

- Difficulté à gérer efficacement les tâches répétitives dans l'administration des serveurs
- Risque d'incohérence dans les configurations des différentes machines d'un environnement
- Manque de documentation et de contrôle de version des configurations de l'infrastructure
- Nécessité d'une gestion centralisée sans ajouter de lourdeur ou de coûts supplémentaires pour installer et gérer des agents sur chaque machine

### Quelle solution Ansible apporte t-il au problème?

Ansible aborde ces problématiques en se basant sur une architecture simple, un langage de configuration accessible (YAML) et une approche sans agent, ce qui facilite son intégration et son utilisation.

- **Gestion des tâches répétitives** : 
Ansible permet d'automatiser les tâches répétitives en utilisant des playbooks, qui sont des fichiers YAML dans lesquels les utilisateurs définissent les étapes précises pour configurer ou gérer les systèmes. Ces playbooks peuvent inclure des instructions pour installer des logiciels, configurer des services, appliquer des correctifs, ou même redémarrer des services. En standardisant et en automatisant ces opérations, Ansible réduit le risque d'erreurs et le temps consacré à l'exécution de tâches manuelles.

- **Consistance et uniformité des configurations** :
Ansible permet de définir des configurations de manière déclarative, en spécifiant l’état final souhaité pour chaque serveur. Cette approche permet à Ansible de vérifier l’état actuel du système et d’appliquer uniquement les changements nécessaires pour atteindre cet état final, assurant ainsi que toutes les machines d’un environnement sont cohérentes. Le système de gestion d’Ansible étant idempotent, réappliquer les mêmes playbooks produit toujours le même résultat, garantissant la consistance.

- **Documentation et contrôle de version de l’infrastructure** :
Les fichiers YAML des playbooks servent aussi de documentation pour l’infrastructure. Ils décrivent en détail les configurations et les étapes nécessaires pour gérer chaque service ou composant. De plus, en utilisant un contrôle de version comme Git pour stocker ces playbooks, les utilisateurs peuvent suivre les modifications dans le temps, comprendre qui a modifié quoi et revenir à une version antérieure si nécessaire. Cette approche facilite également la collaboration entre équipes.

- **Gestion centralisée sans agents** :
Contrairement à certains outils de gestion de configuration qui nécessitent des agents sur chaque machine, Ansible fonctionne en se connectant aux serveurs via SSH, sans nécessiter d’installation supplémentaire. Cela réduit la complexité d’installation et le coût de maintenance. Il suffit d’installer Ansible sur une machine centrale (comme un serveur de gestion ou même un ordinateur personnel) pour déployer des configurations sur plusieurs serveurs, rendant la gestion centralisée.

### Avantages d'Ansible

En plus de résoudre les problématiques d'automatisation, de standardisation, et de gestion d'infrastructure, Ansible présente de nombreux autres avantages qui le rendent interessant pour les administrateurs et les équipes DevOps :
1. **Simplicité et accessibilité**
La syntaxe en YAML est intuitive et lisible, ce qui réduit la barrière d'entrée pour les débutants. Sa structure de playbooks rend l'écriture et la lecture des configurations faciles, permettant aux équipes d’adopter rapidement l’outil sans une courbe d'apprentissage importante.

2. **Sans agent**
Ansible utilise SSH pour se connecter aux serveurs, évitant l'installation d'agents sur les machines cibles. Cela simplifie l'infrastructure en réduisant les dépendances et le besoin de maintenance supplémentaire, et facilite l’utilisation dans des environnements hybrides ou éphémères (comme les instances cloud).

3. **Modularité et extensibilité**
Ansible dispose de milliers de modules prêts à l'emploi pour accomplir une grande variété de tâches : installation de logiciels, gestion des utilisateurs, configuration des réseaux, etc. Il est aussi possible de créer des modules personnalisés pour répondre à des besoins spécifiques, ce qui offre une grande flexibilité.

4. **Communauté active et soutien de Red Hat**
Ansible est soutenu par une large communauté open source et bénéficie du support commercial de Red Hat. Cela signifie que les utilisateurs ont accès à de nombreux modules, extensions, et ressources communautaires, ainsi qu'à des mises à jour régulières et une bonne documentation.

5. **Idempotence**
Ansible garantit l’idempotence, c’est-à-dire qu’exécuter un playbook plusieurs fois produit toujours le même résultat, sans changer l'état d'un système déjà conforme. Cela assure que les configurations sont appliquées sans risque de dégrader le système, offrant une grande fiabilité.

6. **Compatibilité multi-plateforme**
Ansible est compatible avec un large éventail de systèmes d'exploitation, notamment Linux, Windows, et les environnements cloud comme AWS, Azure et Google Cloud. Cette compatibilité permet aux équipes de gérer des environnements hétérogènes avec un seul outil.

7. **Orchestration avancée**
Ansible permet d'orchestrer des tâches complexes impliquant plusieurs services ou machines. Par exemple, il peut déployer une application multi-tiers en orchestrant les serveurs web, les bases de données et les services de mise en cache pour s'assurer que chaque composant est configuré et démarré dans le bon ordre.

8. **Sécurité intégrée**
Ansible gère les connexions via SSH (ou WinRM pour Windows) et peut être configuré pour respecter les normes de sécurité strictes d'une entreprise. Il prend aussi en charge des solutions comme Ansible Vault pour stocker et chiffrer des informations sensibles, telles que les mots de passe ou les clés API, directement dans les fichiers de configuration.

9. **Documentation naturelle de l’infrastructure**
Les playbooks, tout en étant des fichiers de configuration, servent aussi de documentation pour les systèmes et les processus. Ils fournissent une vue complète des étapes nécessaires pour gérer ou configurer une application, facilitant ainsi le transfert de connaissances et la continuité des opérations.

10. **Adapté aux déploiements CI/CD**
Grâce à son intégration avec des outils CI/CD comme Jenkins, GitLab CI, ou même GitHub Actions, Ansible peut être intégré dans des pipelines automatisés de déploiement continu, permettant des mises à jour rapides et sûres.

En somme, Ansible combine simplicité, flexibilité, et puissance pour offrir un outil polyvalent, capable de répondre aux besoins d'infrastructures modernes et complexes tout en restant facile d’accès pour les équipes.

## Mise en place et fonctionnalités

### Installation

Ansible fonctionne sans agent. Cela implique qu'il n'est necessaire de l'installer que sur le serveur de controle (noeud de controle). Le noeud de controle doit être une machine linux (le wsl de Windows peut aussi être utilisé).

- Installation avec `pipx`:
  
```
$ pipx install --include-deps ansible
```
Mise à jour
```
$ pipx upgrade --include-injected ansible
```

- Installation avec `pip`

```
$ python3 -m pip install --user ansible
```
Mise à jour
```
$ python3 -m pip install --upgrade --user ansible
```

### ...

## Démo

## Conclusion
