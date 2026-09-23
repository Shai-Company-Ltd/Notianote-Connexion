# 🪐 NotiaNote Connexion (Universal School Platforms Connector)

[![Website](https://img.shields.io/badge/Website-notianote.fr-8B5CF6?style=for-the-badge)](https://notianote.fr)
[![App Store](https://img.shields.io/badge/App_Store-iOS-007AFF?style=for-the-badge&logo=apple)](https://apps.apple.com/fr/app/notianote/id6758548199)
[![Play Store](https://img.shields.io/badge/Play_Store-Android-3DDC84?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=com.dontbyshai.notianote)

Bienvenue sur le dépôt officiel **NotiaNote Connexion** ! 

Ce projet héberge la logique de connexion (Drivers) universelle et publique utilisée par l'application **NotiaNote** pour s'interconnecter de manière transparente avec la quasi-totalité des plateformes scolaires, universitaires et de restauration dans le monde.

---

## 📱 À propos de NotiaNote
**NotiaNote** est l'application mobile de référence pour les élèves, étudiants et parents d'élèves. Conçue avec un design moderne, premium et personnalisable, elle réunit au même endroit toutes les informations académiques indispensables :
* 📊 **Suivi des notes** avec statistiques avancées (évolution, moyennes de classe, répartition).
* 📅 **Emploi du temps interactif** dynamique.
* 📝 **Cahier de textes & Devoirs** pour ne jamais rien oublier.
* 💬 **Messagerie intégrée** avec les enseignants et les établissements.
* 🍽️ **Restauration Scolaire / Cantine** : Suivi des soldes et badges virtuels (TurboSelf, Izly, Alise).
* 🎓 **Portails Universitaires (CAS/SSO)** : Intégration UCA (Clermont Auvergne), Sorbonne, Moodle, AppScho.
* 🤖 **NotiaNote IA** : Un assistant intelligent pour vous aider dans vos révisions et devoirs.

🌐 **Découvrez notre site web officiel :** [notianote.fr](https://notianote.fr)

---

## 🛠️ Le Connecteur Universel (`NotiaNote-app-publique.js`)
Ce fichier contient la logique de connexion pure, **sans aucune interface graphique**, pour vous connecter à tous les services scolaires et universitaires mondiaux :

### 🇫🇷 France & Europe Francophone
* **EcoleDirecte** — Authentification sécurisée API v3 avec gestion du Double Facteur (2FA).
* **Pronote** — Chiffrement et intégration avec les serveurs Pronote (France / International).
* **Skolengo & ENT** — Passerelle multi-ENT régionales (MonBureauNumerique, LyceeConnecte, CAS, etc.).
* **Smartschool** (Belgique / Pays-Bas) — Session-based authentification et module Skore.

### 🍽️ Restauration Scolaire & Cantines
* **TurboSelf** — Consultation du solde et réapprovisionnement de cantine.
* **Izly** — Synchronisation avec la solution de paiement étudiante Crous / Izly.
* **Alise & ARD** — Cartes et badge cantine numériques.

### 🎓 Enseignement Supérieur & Universités
* **UCA (Université Clermont Auvergne)** — Connecteur CAS SSO, emploi du temps ADE Campus (iCal), courriels Zimbra, notes Oudin, devoirs et Moodle.
* **Moodle** — Connexion via l'API officielle mobile Moodle.
* **AppScho** — Intégration pour les Universités françaises et internationales (Sorbonne, SciencesPo, HEC, Sorbonne-Nouvelle, Université de Limoges, etc.).

### 🇩🇪 Allemagne / Autriche / Europe Centrale
* **WebUntis** — Intégration via protocole Web Untis JSON-RPC API.

### 🇺🇸 USA & Canada (Amérique du Nord)
* **PowerSchool** — Connexion API REST officielle PowerSchool.
* **Infinite Campus** — Connecteur d'authentification Campus.
* **Edsby** — Gestion de session Edsby.
* **Skyward** — Jeton d'accès API Skyward.

---

## 🚀 Exemple d'intégration rapide (JavaScript)

```javascript
import NotiaNotePlatformsConnector from './NotiaNote-app-publique.js';

async function main() {
    try {
        // Connexion à EcoleDirecte
        const resultED = await NotiaNotePlatformsConnector.connectToPlatform('ecoledirecte', {
            username: 'mon_identifiant',
            password: 'mon_mot_de_passe'
        });
        console.log('Connexion EcoleDirecte réussie :', resultED.success);

        // Connexion à UCA (Université Clermont Auvergne)
        const resultUCA = await NotiaNotePlatformsConnector.connectToPlatform('uca', {
            username: 'etudiant_uca',
            password: 'password_cas'
        }, { cookies: { CASTGC: 'ticket_value' } });
        console.log('Connexion UCA réussie :', resultUCA.success);

        // Connexion à TurboSelf (Cantine)
        const resultCantine = await NotiaNotePlatformsConnector.connectToPlatform('turboself', {
            username: 'mon_login_cantine',
            password: 'mon_password_cantine'
        });
        console.log('Connexion Cantine réussie :', resultCantine.success);
    } catch (error) {
        console.error('Erreur :', error);
    }
}
```

---

## 📄 Licence
Ce projet est sous licence **MIT**. Vous êtes libre de l'utiliser, de le modifier et de le distribuer, tant pour des projets open-source que commerciaux.

Propulsé par **Shai's Company**.
