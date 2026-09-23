# 🪐 NotiaNote Connexion (Universal School & University Platforms Connector)

[![Version v2.0.0](https://img.shields.io/badge/Version-v2.0.0-8B5CF6?style=for-the-badge)](https://github.com/Shai-Company-Ltd/Notianote-Connexion/tree/v2.0.0)
[![Website](https://img.shields.io/badge/Website-notianote.fr-10B981?style=for-the-badge)](https://notianote.fr)
[![App Store](https://img.shields.io/badge/App_Store-iOS-007AFF?style=for-the-badge&logo=apple)](https://apps.apple.com/fr/app/notianote/id6758548199)
[![Play Store](https://img.shields.io/badge/Play_Store-Android-3DDC84?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=com.dontbyshai.notianote)

Bienvenue sur le dépôt officiel **NotiaNote Connexion** ! 

Ce projet héberge la logique de connexion (Drivers) universelle et publique utilisée par l'application **NotiaNote** pour s'interconnecter de manière transparente avec la quasi-totalité des plateformes scolaires, universitaires et de restauration dans le monde.

---

## 📌 Versions & Historique

* 🚀 **[Version 2.0.0 (Actuelle)](https://github.com/Shai-Company-Ltd/Notianote-Connexion/tree/v2.0.0)** : Ajout des modules Universités & CAS SSO (UCA, Moodle, AppScho), Restauration Scolaire (TurboSelf, Izly, Alise) et mise à jour de Skolengo & Pronote.
* 📜 **[Version 1.0.0 (Archivée)](https://github.com/Shai-Company-Ltd/Notianote-Connexion/tree/v1.0.0)** : Version initiale intégrant EcoleDirecte, Pronote, Smartschool, WebUntis, PowerSchool, Infinite Campus.

---

## 📱 À propos de NotiaNote
**NotiaNote** est l'application mobile de référence pour les élèves, étudiants et parents d'élèves. Conçue avec un design moderne, premium et personnalisable, elle réunit au même endroit toutes les informations académiques indispensables :
* 📊 **Suivi des notes** avec statistiques avancées (évolution, moyennes de classe, répartition).
* 📅 **Emploi du temps interactif** dynamique.
* 📝 **Cahier de textes & Devoirs** pour ne jamais rien oublier.
* 💬 **Messagerie intégrée** avec les enseignants et les établissements.
* 🍽️ **Restauration Scolaire / Cantine** : Suivi des soldes et cartes virtuelles (TurboSelf, Izly, Alise).
* 🎓 **Portails Universitaires (CAS/SSO)** : Intégration UCA (Clermont Auvergne), Sorbonne, Moodle, AppScho.
* 🤖 **NotiaNote IA** : Un assistant intelligent pour vous aider dans vos révisions et devoirs.

🌐 **Découvrez notre site web officiel :** [notianote.fr](https://notianote.fr)

---

## 🛠️ Le Connecteur Universel (`NotiaNote-app-publique.js`)

Le fichier `NotiaNote-app-publique.js` contient la logique d'authentification pure sans dépendance UI.

### 📋 Liste complète des plateformes prises en charge

#### 🏫 1. Secondaire (Collèges & Lycées - France & Europe Francophone)
| Plateforme | Pays / Région | Description & Fonctionnalités |
| :--- | :--- | :--- |
| **EcoleDirecte** | 🇫🇷 France | API v3 officielle, authentification sécurisée, gestion du 2FA |
| **Pronote** | 🇫🇷 France / 🌍 Intl | Intégration chiffrement Pronote API, session token, messagerie & devoirs |
| **Skolengo** | 🇫🇷 France | ENT Régionaux (MonBureauNumerique, LyceeConnecte, etc.) |
| **Smartschool** | 🇧🇪 Belgique / 🇳🇱 NL | Session-based authentication, gestion du module Skore |

#### 🎓 2. Enseignement Supérieur & Universités (CAS / SSO / Moodle)
| Plateforme / Université | Type | Fonctionnalités |
| :--- | :--- | :--- |
| **UCA (Université Clermont Auvergne)** | 🏛️ Université CAS | SSO CAS, iCal ADE Campus, courriels Zimbra, notes Oudin, devoirs & Moodle |
| **Moodle Mobile API** | 🌐 International | API REST officielle Moodle Mobile (Token auth, cours, fichiers) |
| **AppScho** | 🏛️ Universités Fr. | Passerelle pour Sorbonne, SciencesPo, HEC, Sorbonne-Nouvelle, Limoges... |
| **Multi-ENT CAS** | 🇫🇷 Universités | Connecteur CAS générique pour l'authentification SSO universitaire |

#### 🍽️ 3. Restauration Scolaire & Cantines
| Service | Type | Fonctionnalités |
| :--- | :--- | :--- |
| **TurboSelf** | 💳 Cantine Scolaire | Consultation du solde, historique des repas, réapprovisionnement |
| **Izly** | 💳 Crous / Etudiant | Authentification QR Pay Izly & synchronisation solde |
| **Alise & ARD** | 💳 Badge Cantine | Solde et passage carte de restauration numérique |

#### 🌎 4. International (Amérique du Nord & Europe Centrale)
| Plateforme | Pays | Description |
| :--- | :--- | :--- |
| **WebUntis** | 🇩🇪 DE / 🇦🇹 AT / 🇪🇺 Europe | Protocole JSON-RPC API WebUntis |
| **PowerSchool** | 🇺🇸 USA / 🇨🇦 Canada | API REST PowerSchool |
| **Infinite Campus** | 🇺🇸 USA | Connecteur Campus API |
| **Edsby** | 🇺🇸 USA / 🇨🇦 Canada | Gestion de session Edsby |
| **Skyward** | 🇺🇸 USA | Jetons d'accès Skyward API |

---

## 🚀 Exemple d'utilisation (JavaScript)

```javascript
import NotiaNotePlatformsConnector from './NotiaNote-app-publique.js';

async function main() {
    try {
        // --- Exemple 1 : Connexion à EcoleDirecte (v1 & v2) ---
        const resultED = await NotiaNotePlatformsConnector.connectToPlatform('ecoledirecte', {
            username: 'mon_identifiant',
            password: 'mon_mot_de_passe'
        });
        console.log('Connexion EcoleDirecte :', resultED.success);

        // --- Exemple 2 : Connexion UCA (Nouveauté v2.0.0) ---
        const resultUCA = await NotiaNotePlatformsConnector.connectToPlatform('uca', {
            username: 'etudiant_uca',
            password: 'password_cas'
        }, { cookies: { CASTGC: 'mon_cookie_cas' } });
        console.log('Connexion UCA :', resultUCA.success);

        // --- Exemple 3 : Connexion Cantine TurboSelf (Nouveauté v2.0.0) ---
        const resultCantine = await NotiaNotePlatformsConnector.connectToPlatform('turboself', {
            username: 'identifiant_cantine',
            password: 'password_cantine'
        });
        console.log('Connexion Cantine :', resultCantine.success);

    } catch (error) {
        console.error('Erreur :', error);
    }
}
```

---

## 📄 Licence
Ce projet est sous licence **MIT**. Vous êtes libre de l'utiliser, de le modifier et de le distribuer, tant pour des projets open-source que commerciaux.

Propulsé par **Shai's Company**.
