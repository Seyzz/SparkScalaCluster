# Setup a Spark-Scala Multi-Node Standalone Cluster

## 1. Introduction

Pour un cluster, on pense tout d'abord aux deux entités qui auront un rôle majeur dans celui-ci : Le maître (master) et les esclaves (slaves). Il nous faut donc une machine pour 'contrôler' ce cluster, et des esclaves pour lui obéir.

Plusieurs solutions s'offrent à vous pour ces 'nodes' :

  - Plusieurs ordinateurs (rpi, pc ...)
  - Amazon AWS
  - Installation d'une plateforme virtuelle avec plusieurs machines virtuelles pour simuler ce cluster

## 2. Configuration des slaves

Quelque soit le moyen utilisé pour les nodes il faut s'assurer qu'elles aient bien des ip différentes.

Pour le choix de l'OS, Linux est le plus facile à setup, il me semble néanmoins que cela soit soit aussi facile avec MacOS, à tester ! Je vais donc détailler l'installation pour Ubuntu 16.04, assez commun et très stable :

#### A. Installation de Java

**TODO**

#### B. Installation de Scala

Scala est dans les repositories xenial, il suffit donc d'exécuter la commande (dans le terminal) : 

```bash
sudo apt-get install scala
```

#### C. Installation de Spark

Vous pouvez vous même vous rendre sur le site de Spark pour télécharger la dernière version directement, ou bien utilisez cette commande pour la version 2.1.0 (28 Décembre 2016) :

```bash
wget http://d3kbcqa49mib13.cloudfront.net/spark-2.1.0-bin-hadoop2.7.tgz
```

Il faut decompresser ce tgz pour ensuite placer cette librairie quelque part (/usr/share/ pour ma part, mais je ne sais pas si c'est le mieux ...) :

```bash
tar -xvzf spark-2.1.0-bin-hadoop2.7.tgz
sudo mv spark-2.1.0-bin-hadoop2.7 /usr/share/
```

#### D. Ajout des variables d'environnements

La meilleure méthode pour modifier des variables d'environement est de les ajouter dans le *~/.bashrc* (ou zsh, fish ...)
Pour ouvrir votre fichier de configuration :

```bash
nano ~/.bashrc
```

Ensuite à la fin de votre fichier ajoutez : 

```bash
export SCALA_HOME=/usr/share/scala-2.11
export SPARK_HOME=/usr/share/spark-2.1.0-bin-hadoop2.7
export PATH=$PATH:$SPARK_HOME/bin
```

Pour rendre les changements effectifs :

```bash
source ~/.bashrc
```

## 3. Configuration du maître

#### A. Installation de Java

**[ Même chose que en 2.A ]**

**TODO**

#### B. Installation de Scala

**[ Même chose que en 2.B ]**

Scala est dans les repositories xenial, il suffit donc d'exécuter la commande (dans le terminal) : 

```bash
sudo apt-get install scala
```

#### C. Installation de Spark

**[ Même chose que en 2.C ]**

Vous pouvez vous même vous rendre sur le site de Spark pour télécharger la dernière version directement, ou bien utilisez cette commande pour la version 2.1.0 (28 Décembre 2016) :

```bash
wget http://d3kbcqa49mib13.cloudfront.net/spark-2.1.0-bin-hadoop2.7.tgz
```

Il faut decompresser ce tgz pour ensuite placer cette librairie quelque part (/usr/share/ pour ma part, mais je ne sais pas si c'est le mieux ...) :

```bash
tar -xvzf spark-2.1.0-bin-hadoop2.7.tgz
sudo mv spark-2.1.0-bin-hadoop2.7 /usr/share/
```

#### D. Ajout des variables d'environnements

**[ Même chose que en 2.D ]**

La meilleure méthode pour modifier des variables d'environement est de les ajouter dans le *~/.bashrc* (ou zsh, fish ...)
Pour ouvrir votre fichier de configuration :

```bash
nano ~/.bashrc
```

Ensuite à la fin de votre fichier ajoutez : 

```bash
export SCALA_HOME=/usr/share/scala-2.11
export SPARK_HOME=/usr/share/spark-2.1.0-bin-hadoop2.7
export PATH=$PATH:$SPARK_HOME/bin
```

Pour rendre les changements effectifs :

```bash
source ~/.bashrc
```

#### E. Configuation de /etc/hosts

**TODO**

#### F. Configuration des scripts pour lancer les slaves

- slaves.template -> slaves
  - TODO

- spark-env.sh.template -> spark-env.sh
  - TODO

## 4. Configuration de OpenSSH entre chaque slave / master

Pour chaque slave il faut faire l'action suivante :

Sur le MAÎTRE :

Générer une clé public : 

```bash
ssh-keygen -t rsa
```

Il faut ensuite ajouter cette clé public dans le fichier authorized_keys du slave, on peut le faire directement depuis le MAÎTRE

```bash
ssh-copy-id user@<ip-address or hostname>
```
*Il faudra entrer le mot de passe de la session slave pour se connecter :)*

Sur l'ESCLAVE :

Générer une clé public :

```bash
ssh-keygen -t rsa
```

Il faut ensuite ajouter cette clé public dans le fichier authorized_keys du maître, on peut le faire directement depuis l'ESCLAVE avec :

```bash
ssh-copy-id user@<ip-address or hostname>
```
*Il faudra entrer le mot de passe de la session maître pour se connecter :)*

## 5. Lancement d'un programme Spark sur le cluster

**TODO**

_________________________________________________________________________________________________________________________________

#### Sources : 

- Spark GraphX in Action - *Michael S. Malak* and *Robin East* 
