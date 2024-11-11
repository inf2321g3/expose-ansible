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

## Mise en place et fonctionnalités

### Installation

### ...

## Démo

## Conclusion
