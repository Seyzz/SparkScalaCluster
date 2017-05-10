# Setup a Spark-Scala Multi-Node Standalone Cluster

## 1. Introduction

Pour un cluster, on pense tout d'abord aux deux entités qui auront un rôle dans celui-ci : Le maître (master) et les esclaves (slaves). Il nous faut donc une machine pour 'contrôler' ce cluster, et des esclaves pour lui obéir.

Plusieurs solutions s'offrent à vous pour ces 'nodes' :

  - Plusieurs ordinateurs (rpi, pc ...)
  - Amazon AWS
  - Installation d'une plateforme virtuelle avec plusieurs machines virtuelles pour simuler ce cluster

## 2. Configuration des slaves

Quelque soit le moyen utilisé pour les nodes il faut s'assurer qu'elles aient bien des ip différentes.

Pour le choix de l'OS, Linux est le plus facile à setup, il me semble néanmoins que cela soit soit aussi facile avec MacOS, à tester ! Je vais donc détailler l'installation pour Ubuntu 16.04, assez commun et très stable :

#### A. Installation de Java

TODO

#### B. Installation de Scala

Scala est dans les repositories xenial, il suffit donc d'exécuter la commande (dans le terminal) : 

```
sudo apt-get install scala
```

#### C. Installation de Spark

Vous pouvez vous même vous rendre sur le site de Spark pour télécharger la dernière version directement, ou bien utilisez cette commande pour la version <version_number> :

```
wget < URL : TODO >
```

#### D. Ajout des variables d'environnements

La meilleure méthode pour modifier des variables d'environement est de les ajouter dans le *~/.bashrc* (ou zsh, fish ...)
Pour ouvrir votre fichier de configuration :

```
nano ~/.bashrc
```

Ensuite à la fin de votre fichier ajoutez : 

```
export SCALA_HOME=/usr/share/scala-2.11
export SPARK_HOME=TODO
export PATH=$PATH:$SPARK_HOME/bin
```

Pour rendre les changements effectifs :

```
source ~/.bashrc
```

## 3. Configuration du maître

TODO

## 4. Lancement d'un programme Spark avec le cluster

TODO
