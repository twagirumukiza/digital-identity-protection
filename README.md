# Digital Identity Protection V3

V3 ajoute une première couche de surveillance réelle depuis le navigateur :
- génération de variantes et homoglyphes ;
- requêtes RDAP via rdap.org lorsque le service et CORS le permettent ;
- interrogation Certificate Transparency via crt.sh lorsque disponible ;
- scoring et alertes ;
- export JSON ;
- profil sauvegardable localement ;
- emplacement prévu pour un proxy/backend Cloudflare Brand Protection.

## Nouveautés de cette mise à jour

- **Signature** : mention "Conçu et développé par Twagirumukiza" en pied de page.
- **Mentions légales, CGU et Licence** : accessibles depuis le pied de page (fenêtres modales), avec des modèles à personnaliser (statut juridique, SIREN, adresse, contact).
- **Bilingue FR/EN** : bouton FR / EN dans l'en-tête, bascule instantanée de toute l'interface (formulaire, tableau, alertes, pages légales), langue mémorisée d'une visite à l'autre.
- **Thème clair / sombre** : bouton dédié, préférence mémorisée dans le navigateur.
- **Taille du texte réglable** : boutons A- / A / A+ dans l'en-tête, 5 paliers, mémorisés dans le navigateur.
- **Menu burger** : sur mobile et tablette (< 820px), les contrôles (thème, langue, taille du texte) se replient dans un menu ☰ accessible en haut à droite.

## Personnalisation avant publication

Avant de publier, remplir dans les mentions légales et les CGU (fichier `index.html`, objets `I18N.fr` / `I18N.en`) :
- statut juridique et SIREN/SIRET ;
- adresse postale ;
- adresse e-mail de contact.

Choisir également les termes définitifs de la licence (droits réservés par défaut, ou licence open source comme MIT si le code doit être réutilisable).

## Architecture de production recommandée

Navigateur -> API/Worker sécurisé -> sources de veille -> stockage historique -> moteur de scoring -> alerting.

Ne jamais placer un token Cloudflare/API secret dans `index.html`.

Cloudflare Brand Protection fournit aujourd'hui des recherches de domaines et de logos, des matches, une API et des alertes. L'intégration production doit passer par un backend/worker et respecter les droits d'utilisation du service.

RDAP est le protocole standard de données d'enregistrement des gTLD, en remplacement de WHOIS.

Cette V3 reste un prototype : elle ne garantit pas une couverture exhaustive d'Internet et ne constitue pas une preuve juridique.
