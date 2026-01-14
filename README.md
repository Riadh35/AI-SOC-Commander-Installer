# AI-SOC-Commander-Installer : Nouvelle Version à Tester 
Installeur MSI d'AI SOC Commander (Windows) 10-11...

********************************************************************************************************************************************************************************************************************************************
🛡️ AI SOC Commander - Version Professionnelle
AI SOC Commander est une solution de surveillance et d'intervention réseau avancée conçue pour les administrateurs système et les analystes SOC.
Alliant une interface fluide à des outils de diagnostic puissants, elle permet une visibilité totale sur l'état de santé et la sécurité de votre infrastructure.
✨ Fonctionnalités Principales
🎯 Dashboard (Surveillance Temps Réel)
Monitoring Critique : Surveillance en direct des processus (CPU/MEM).
Analyse Visuelle : Graphique du trafic réseau animé et interactif.
Navigation Fluide : Tri par colonne, filtres rapides et recherche instantanée.
Intégration Directe : Double-clic ou F8 pour basculer vers l'onglet PORTS filtré sur un PID spécifique.
🌐 Cartographie Réseau Vue Hybride : Basculez entre une table détaillée (IP, MAC, Vendor, Latence) et une vue graphique topologique.
Intelligence Visuelle : Mise en évidence des nœuds critiques (Gateway, Serveurs, IP .1) avec icônes dédiées.
Indicateurs de Performance : Mini-barres de latence colorées et zoom à la molette.
🔌 Gestion des Ports & Connexions Visibilité Totale : Liste TCP/UDP complète avec codes couleurs par statut (LISTEN, ESTABLISHED, etc.).
Action Rapide : Fermeture sécurisée des ports via menu contextuel ou table.
🛠️ Outillage de Diagnostic & Consoles Suite Intégrée : Accès direct aux commandes Windows (CMD/PowerShell) avec historique de commandes.
Automatisation : Export des résultats de diagnostic dans des fichiers textes horodatés.
Feedback Visuel : Indicateurs d'état "En cours / Terminé" pour chaque tâche de fond.
⚠️ Mode console & sécurité : les consoles intégrées (CMD / PowerShell) exécutent les commandes saisies **avec les privilèges de l'utilisateur courant (souvent administrateur)**. Elles sont destinées à un usage par des opérateurs SOC avertis ; évitez d'y coller des commandes dont l'origine n'est pas maîtrisée.
🧭 Raccourcis Clavier & Ergonomie Touche Action F5 Scan complet (Processus, Ports, Cartographie) F8 Focus sur les PORTS du PID sélectionné Ctrl + F Focus sur la recherche contextuelle
🔒 Sécurité et Intégrité (Supply Chain)
Dans un contexte SOC, l'intégrité de l'outil est primordiale. Ce projet utilise GitHub Artifact Attestations.
Build Provenance : Chaque release est signée cryptographiquement via actions/attest-build-provenance.
Auto-élévation : Gestion native des privilèges administrateur pour les commandes système.
Logs : Journalisation complète des actions dans le fichier de log local.
🛡 Sécurité avancée / Réponse à incident
- Colonne d'actions dédiée avec plusieurs blocs :
	- **Contrôles d'intégrité système** : vérification SFC des fichiers système.
	- **Persistance & démarrage** : liste des programmes au démarrage via les clés de registre *Run* (HKLM / HKCU).
	- **Résolution des problèmes Windows** : accès direct aux assistants de maintenance (MaintenanceDiagnostic).
	- **Comptes d'utilisateurs (sécurité)** : centre de gestion des comptes, mots de passe réseau enregistrés, certificats utilisateur et éditeur de stratégie de groupe locale (gpedit.msc).
	- **Réseau & confinement rapide** : consultation de l'état du pare-feu et activation rapide de tous les profils.
	- **Consoles & stratégies de sécurité** : raccourcis vers les consoles avancées (secpol.msc, wf.msc, eventvwr.msc, services.msc).
- Journal des actions de sécurité à droite : commandes lancées, sortie détaillée, export possible des analyses.
- Pensé pour le SOC : vérification rapide de l'intégrité, de la persistance et ouverture en un clic des principales consoles d'administration Windows.

🖥️ Sécurité Système (Hardening & Forensics)
- **Durcissement Windows (Hardening)** :
	- Contrôle des services critiques (Spooler, RemoteRegistry) en lecture seule.
	- Audit des tâches planifiées (schTasks) pour détecter des mécanismes de persistance.
	- Préparation à une future analyse des DLL non signées (intégration possible d’outils Sysinternals).
- **Sécurité Réseau / HIDS local** :
	- Détection simplifiée de scans de ports via l’analyse des connexions locales.
	- Surveillance du fichier `C:\Windows\System32\drivers\etc\hosts` pour repérer des redirections suspectes (banques, SOC, etc.).
	- Analyse basique de la table ARP pour mettre en évidence des patterns d’ARP spoofing.
- **Interface & BIOS / Intégrité matérielle** :
	- Vérification de l’état du Secure Boot via PowerShell.
	- Récupération de la version BIOS/UEFI et de la date via WMIC.
	- Inventaire des périphériques USB (historique simple) pour traquer des branchements non autorisés.
- **Forensics post-incident** :
	- Liste des fichiers Prefetch récents (programmes exécutés récemment).
	- Placeholder documenté pour l’analyse Shimcache (prévue via outils forensics dédiés).
	- Analyse rapide du journal Security (wevtutil) pour filtrer les événements critiques LSASS (ID 4656/4663).

🤖 Assistant IA Locale (Ollama)
- Onglet dédié à l'analyse IA hors ligne des journaux (Windows, firewall, proxy, EDR, scripts PowerShell…).
- Synthèse structurée en français générée par un modèle local Ollama (aucune donnée envoyée vers le cloud).
- Rapport exportable (copie ou fichier texte) pour intégration dans les tickets SOC ou rapports d'incident.
- Version conseillée : utiliser la dernière version stable d'Ollama disponible sur le site officiel.
- Téléchargement Ollama : https://ollama.com
- **Rappel aux utilisateurs : Ollama doit être installé séparément sur le système pour que cette fonctionnalité s'active.**
🚀 Installation & Performances
Optimisation : Threading optimisé pour une interface sans latence, même lors de scans lourds.
Dépendances principales : psutil, scapy, tkinter/customtkinter.

Lancez l'application (Droits Admin recommandés)

🔑 Licence, mode démo et activation
- Mode démo : par défaut, AI SOC Commander démarre en **version d'essai de 7 jours** liée à la machine (fingerprint matériel).
- Empreinte machine : lors du premier lancement sans licence, un code machine est affiché et enregistré dans :
	- `C:\\ProgramData\\AI_SOC_Commander\\fingerprint.txt`
- Fin de démo : au-delà de 7 jours sans licence valide, l'application se bloque et demande une activation.
- Activation définitive :
	1. Le client transmet son fingerprint à l'éditeur.
	2. L'éditeur génère un fichier de licence `machine.lic` (simple fichier texte UTF-8 contenant le fingerprint autorisé).
	3. Le client copie ce fichier dans : `C:\\ProgramData\\AI_SOC_Commander\\machine.lic`.
	4. Au prochain lancement, si le fingerprint correspond, le logiciel est **débloqué en mode complet** (sans limitation de durée).

📊 Performances
✓ Interface fluide (60 FPS)

✓ Gestion mémoire efficace

✓ Notifications non bloquantes

⚖️ Clause de Non-Responsabilité (Disclaimer)

> **Usage à vos propres risques** : l'utilisation de AI SOC Commander est fournie sans aucune garantie d'aucune sorte.  						Ni le développeur Ni le logiciel ne sauraient être tenus responsables de tout dommage direct ou indirect résultant de son utilisation.

**Limitation de responsabilité** : le développeur décline toute responsabilité en cas de :
- Erreur de diagnostic ou faux positifs/négatifs lors de l'analyse de sécurité.
- Fuite de données, perte d'informations ou corruption de fichiers.
- Faille de sécurité ou vulnérabilité non détectée par l'outil.
- Interruption de service ou erreur système consécutive à l'exécution du logiciel.

**Responsabilité de l'utilisateur** : il appartient à l'utilisateur final de valider les résultats fournis par le logiciel et de s'assurer que l'usage de cet outil est conforme aux politiques de sécurité et aux réglementations en vigueur au sein de son organisation.

<span style="color: blue;">© 2026 - AI SOC Commander ©</span> | Dédié à la résilience des infrastructures.
Développeur : © Riadh Ben Khaled ©

