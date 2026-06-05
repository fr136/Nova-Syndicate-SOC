# Cartographie des Actifs - Nova Syndicate

## Actifs critiques

| Actif | Fonction | Criticité |
|---------|---------|---------|
| DC01 | Contrôleur de domaine Active Directory | Critique |
| OPNsense | Pare-feu et filtrage réseau | Critique |
| WAZUH01 | SIEM et supervision sécurité | Élevée |
| CLIENT01 | Poste utilisateur Windows | Moyenne |
| CLIENT02 | Poste utilisateur Windows | Moyenne |
| KALI01 | Tests de sécurité et validation | Moyenne |

## Flux principaux
Internet -> OPNsense -> Réseau interne -> Active Directory -> Postes utilisateurs -> Wazuh

## Objectif
Identifier les composants essentiels à la sécurité et à la continuité de service.