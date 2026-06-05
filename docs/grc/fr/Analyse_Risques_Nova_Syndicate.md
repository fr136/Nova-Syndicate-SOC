# Analyse des risques et mesures de sécurité

## Infrastructure Nova Syndicate

### Présentation

Nova Syndicate est un laboratoire cybersécurité reproduisant une infrastructure d'entreprise composée d'un Active Directory, d'un pare-feu OPNsense, d'un SIEM Wazuh, d'un serveur PostgreSQL, d'un serveur applicatif Flask/Nginx et de postes clients supervisés.

L'objectif de ce document est d'identifier les principaux risques de sécurité et les mesures de protection associées.

---

## Actifs critiques

| Actif | Fonction | Criticité |
|---------|---------|---------|
| DC01 | Authentification Active Directory et DNS | Critique |
| OPNsense | Contrôle des flux réseau | Critique |
| WAZUH01 | Supervision et détection des incidents | Élevée |
| DB01 | Hébergement des données applicatives | Critique |
| APP01 | Service web Flask/Nginx | Élevée |
| FS01 | Partage de fichiers | Élevée |

---

## Politique de sécurité des utilisateurs

### Gestion des accès

- Les utilisateurs disposent uniquement des droits nécessaires à leurs missions.
- Les privilèges administrateurs sont limités aux comptes dédiés.
- Une revue périodique des droits d'accès doit être réalisée.

### Verrouillage des sessions

- Toute session doit être verrouillée lorsqu'un poste est laissé sans surveillance.
- Un verrouillage automatique doit être appliqué après une période d'inactivité.
- Les utilisateurs sont responsables des actions réalisées sous leur compte.

### Gestion des mots de passe

- Les mots de passe doivent respecter les exigences de complexité définies par l'organisation.
- Les mots de passe ne doivent jamais être partagés.
- Les comptes privilégiés doivent disposer de mots de passe distincts.
- Les mots de passe compromis doivent être changés immédiatement.

### Utilisation des périphériques amovibles

- Les clés USB personnelles sont interdites.
- Les supports amovibles autorisés doivent être validés et analysés avant utilisation.

### Installation de logiciels

- Les utilisateurs ne disposent pas de droits d'installation.
- Toute installation doit être validée par l'administration système.

### Utilisation d'Internet

- L'accès aux sites sans lien avec l'activité professionnelle peut être restreint.
- Les sites identifiés comme malveillants ou à risque doivent être bloqués.

### Messagerie

- L'utilisation de messageries personnelles pour transmettre des données professionnelles est interdite.
- Les échanges doivent être réalisés via les outils approuvés par l'organisation.

### Outils d'administration

- L'accès aux consoles d'administration, terminaux système et outils de sécurité est réservé aux personnels habilités.
- Les activités d'administration font l'objet d'une journalisation centralisée.

---

## Principaux risques identifiés

### Compromission d'un compte administrateur
Impact : Critique

Mesures existantes :
- Active Directory
- RBAC
- Journalisation Wazuh

Recommandations :
- MFA
- Revue des privilèges
- Comptes d'administration dédiés

### Mouvement latéral
Impact : Élevé

Mesures existantes :
- Segmentation OPNsense
- Supervision Wazuh

Recommandations :
- Renforcement de la segmentation
- Restriction des flux internes

### Ransomware
Impact : Critique

Mesures existantes :
- SIEM Wazuh
- Collecte centralisée des journaux

Recommandations :
- Sauvegardes hors ligne
- Procédure de réponse à incident
- Tests de restauration

---

## Conclusion

L'infrastructure Nova Syndicate met déjà en œuvre plusieurs contrôles de sécurité présents dans les environnements professionnels : gestion des identités, segmentation réseau, supervision centralisée, journalisation et détection des menaces.

Les axes d'amélioration concernent principalement la formalisation de la gouvernance SSI, la gestion des risques et les procédures de réponse à incident.