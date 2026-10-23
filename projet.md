## Projet E6 — Casiers connectés

### Contexte
L'ISTP est un établissement d'enseignement supérieur privé sous statut associatif, créé en 1990. Sa mission fondatrice est d'accompagner les entreprises industrielles en développant les compétences individuelles et collectives, notamment via la formation d'ingénieur.

L'institut accueille de nombreux étudiants et alternants, et possède beaucoup de matériel. Ce matériel n'est pas toujours facile d'accès. L'ISTP dispose d'une GMAO, qui recense les moyens techniques de l'ISTP.

Le projet E6 consiste à connecter des casiers physiques à cette GMAO. Chaque casier est piloté par un ESP32 équipé d'un lecteur RFID et de serrures électroniques. Ainsi l'accès au matériel est contrôlé et chaque emprunt et chaque retour sont tracés dans la GMAO.

### Besoin
Un casier connecté basé sur un ESP32 qui doit :
- authentifier un utilisateur grâce à son badge RFID;
- n'ouvrir que les compartiments auxquels cet utilisateur a droit;
- remonter chaque ouverture à la GMAO pour maintenir un historique;
- être administré depuis l'interface web existante.

### Objectifs
1. Sécuriser l'accès physique au matériel : seuls les utilisateurs autorisés ouvrent un compartiment.
2. Suivre précisément les emprunts et les retours dans la GMAO.
3. Assurer la traçabilité complète pour éviter les pertes et les vols et faciliter les audits.

---

### Fonctionnalités

1. **Authentification par badge.** L'ESP32 lit l'UID et l'envoie à la GMAO, retrouve l'utilisateur et vérifie que son compte est actif.
2. **Ouverture contrôlée des serrures.** Le badge ouvre tous les emplacements actifs dont l'utilisateur détient l'acces.
4. **Administration.**
   - Créer, modifier et supprimer des casiers ; les rattacher à un site, une salle et des plateaux techniques.
   - Régénérer la clé API d'un casier.
   - Consulter les emplacements.
   - Associer un UID de badge à chaque utilisateur.
   - Suivre l'occupation et voir si le casier est en ligne.
5. **Historique complet.** Les événements suivants sont horodatés et attribués à leur utilisateur puis stocké en base.