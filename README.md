# 🚀 Demo Jenkins Pipeline

## 🧩 Objectif du projet

Mettre en place une **chaîne d’intégration continue (CI)** complète avec **Jenkins**, à partir d’un projet hébergé sur **GitHub**.
Le pipeline est défini dans un fichier **`Jenkinsfile`** et s’exécute automatiquement à chaque changement sur le dépôt.

---

## 🧱 Technologies utilisées

* **Java 17**
* **Maven 3.x**
* **JUnit 5**
* **Jenkins** (avec plugin *Pipeline* et *JUnit*)
* **Docker** (image Maven officielle utilisée pour le build)

---

## 📂 Structure du projet

```
demo-jenkins-pipeline/
├── Jenkinsfile
├── pom.xml
└── src/
    ├── main/java/
    │   └── App.java
    └── test/java/
        └── AppTest.java
```

---

## 🛠️ Configuration Jenkins

### 1️⃣ Pré-requis

* Jenkins fonctionnel (via Docker ou machine locale)
* Plugins installés :

  * **Pipeline**
  * **JUnit**
  * **Docker Pipeline**
* Docker disponible sur la machine Jenkins

### 2️⃣ Créer le job Jenkins

1. Dans Jenkins → **New Item → Pipeline**
2. Nom : `exo2`
3. **GitHub Project** : 
4. * Project URL : `https://github.com/<votre-utilisateur>/demo-jenkins-pipeline`
5. **Pipeline definition** : *Pipeline script from SCM*
6. SCM : `Git`

   * Repository URL : `https://github.com/<votre-utilisateur>/demo-jenkins-pipeline.git`
   * Branch : `*/main`
   * Script Path : `Jenkinsfile`
7. **Branch Specifier** : */main
8. **Script Path** : Jenkinsfile
9. **Save** → **Build Now**

---

## 📈 Résultat attendu

### ✅ En cas de succès :

* Jenkins clone le dépôt
* Compile le projet
* Exécute les tests
* Publie les rapports JUnit
* Affiche un message “✅ Build réussi !”

### ❌ En cas d’échec :

* Jenkins arrête le pipeline à l’étape fautive
* Le build passe en **rouge**
* Les logs indiquent les erreurs Maven ou JUnit

---

## 🧾 Exemple de sortie Jenkins

```
[INFO] --- maven-surefire-plugin:3.0.0-M7:test (default-test) @ demo ---
[INFO] BUILD SUCCESS
✅ Build réussi !
Finished: SUCCESS
```
