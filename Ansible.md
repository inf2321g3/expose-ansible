# Ansible

## Généralités
<div align="justify">
  
### C'est quoi Ansible?
​
Ansible est une plateforme de gestion de la configuration qui automatise le stockage, les serveurs et la mise en réseau. Lorsque vous l'utilisez  pour configurer ces composants, les tâches manuelles complexes deviennent reproductibles et sont moins vulnérables aux erreurs. ​Ansible offre une grande flexibilité et s’adapte à divers scénarios. Ses applications vont de l’automatisation de déploiements à la gestion de configurations, en passant par l’orchestration de tâches et la gestion d’événements.

### Problématique d'Ansible

Ansible est conçu pour résoudre des problèmes liés à la gestion et à l'automatisation de l'infrastructure informatique, en particulier pour les environnements de grande envergure ou complexes. Les principales problématiques sont les suivantes :

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

### FONCTIONNEMENT

Ansible fonctionne en automatisant des tâches via des playbooks, en se connectant aux machines cibles, et en exécutant des instructions pour atteindre l’état souhaité des configurations. Voici un aperçu de son fonctionnement :

#### Architecture sans agent
Ansible est un outil sans agent, ce qui signifie qu’il n’a pas besoin d’installation sur les machines qu’il gère (cibles), contrairement à d'autres outils de gestion de configuration. Il se connecte aux cibles via SSH (ou WinRM pour Windows) depuis une machine de contrôle, généralement un serveur Ansible ou une station de travail où Ansible est installé.

#### Utilisation d'un inventaire
L’inventaire est un fichier texte (par défaut /etc/ansible/hosts) qui répertorie les machines cibles par leurs adresses IP ou noms de domaine. Il peut être structuré en groupes pour appliquer des configurations à un ensemble spécifique de machines.

#### Playbooks : le cœur des configurations
Les configurations Ansible sont écrites dans des playbooks, des fichiers YAML qui contiennent les instructions pour configurer les systèmes. Un playbook est constitué de tâches, chaque tâche étant une action que vous voulez exécuter, comme installer un logiciel ou configurer un fichier. Les tâches appellent des modules intégrés d’Ansible, qui contiennent les actions spécifiques.

#### Modules Ansible
Les modules sont des petits programmes intégrés à Ansible qui effectuent des actions spécifiques sur les cibles, comme la gestion de fichiers, l’installation de logiciels, la gestion de services, la configuration réseau, etc. Ansible dispose de centaines de modules, et il est aussi possible de créer des modules personnalisés pour répondre à des besoins spécifiques.

#### Idempotence : l’état souhaité
Les tâches Ansible sont idempotentes, ce qui signifie que les playbooks peuvent être exécutés plusieurs fois sans modifier l’état final du système s’il est déjà conforme aux configurations. Par exemple, si vous demandez à Ansible de s’assurer qu’un package est installé, il vérifiera d’abord l’état du package avant de tenter de l’installer.

#### Variables et rôles
- Variables : Ansible permet l'utilisation de variables pour personnaliser les configurations en fonction des machines ou des groupes de machines, ce qui améliore la flexibilité.
- Rôles : Un rôle est un ensemble de playbooks et de configurations organisées de manière modulaire. Les rôles facilitent la réutilisation et la maintenance des configurations pour des configurations complexes.

#### Exécution des playbooks
Une fois que tout est prêt (inventaire, playbook, variables, etc.), Ansible exécute le playbook en utilisant la commande suivante :
ansible-playbook nom_du_playbook.yml
Ansible se connecte aux hôtes de l’inventaire et exécute les tâches dans l'ordre spécifié. Il affiche des messages d’état (OK, CHANGED, FAILED) pour chaque tâche, indiquant si elle a été modifiée ou s’il y a eu une erreur.

#### Gestion des secrets avec Ansible Vault
Pour des informations sensibles comme des mots de passe, Ansible propose Ansible Vault pour chiffrer les fichiers de variables. Vous pouvez ainsi inclure des informations sensibles dans vos configurations sans compromettre leur sécurité.

## Démo

## Conclusion

Ansible est un outil puissant qui aide les équipes à automatiser les configurations de systèmes et les déploiements d’applications, en fournissant un cadre cohérent et flexible pour la gestion d'infrastructure à l’échelle. Il est adapté aux environnements cloud, sur site, et hybrides.Grâce à sa simplicité et sa richesse en fonctionnalités, il est largement utilisé pour des tâches d'automatisation, de configuration et d'orchestration, aidant ainsi les équipes à assurer la stabilité et la rapidité de leurs déploiements.
</div>
