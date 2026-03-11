------------------------------------------------------------------------------------------------------
🎯Comprendre les bases du réseau (OSI, DHCP, NAT)
------------------------------------------------------------------------------------------------------
Cet atelier propose une exploration pratique des fondamentaux des réseaux informatiques à travers trois mécanismes essentiels : le modèle OSI, le protocole DHCP et la traduction d’adresses NAT.  
  
L’objectif est de visualiser concrètement le fonctionnement du réseau, depuis la structure des communications jusqu’à l’attribution des adresses IP et la communication avec Internet. Dans un premier temps, nous allons découvrir le modèle OSI (Open Systems Interconnection) et son rôle comme cadre conceptuel pour organiser les communications réseau en 7 couches. Ensuite, notre atelier reviendra sur le protocole DHCP, qui permet d’attribuer automatiquement une configuration réseau (adresse IP, passerelle, DNS). Et enfin, l’atelier abordera le NAT (Network Address Translation), un mécanisme clé permettant à plusieurs machines d’un réseau privé de partager une même adresse IP publique pour accéder à Internet.  
  
**Notre atelier**  

![Screenshot Actions](Architecture_cible_Reseau.png)  

-------------------------------------------------------------------------------------------------------
🧩 Séquence 1 : GitHUB
-------------------------------------------------------------------------------------------------------
Objectif : Création d'un Repository GitHUB pour travailler avec son projet  
Difficulté : Très facile (~10 minutes)
-------------------------------------------------------------------------------------------------------
**Faites un Fork de ce projet**. Si besoin, voici une vidéo d'accompagnement pour vous aider à "Forker" un Repository Github : [Forker ce projet](https://youtu.be/p33-7XQ29zQ)  

---------------------------------------------------
🧩 Séquence 2 : Création d'un site chez Pythonanywhere
---------------------------------------------------
Objectif : Créer un hébergement sur Pythonanywhere  
Difficulté : Faible (~10 minutes)
---------------------------------------------------

Rendez-vous sur **https://www.pythonanywhere.com/** et créez vous un compte. Puis créez un serveur Web **Flask 3.13**.  
  
---------------------------------------------------------------------------------------------
🧩 Séquence 3 : Les Actions GitHUB (Industrialisation Continue)
---------------------------------------------------------------------------------------------
Objectif : Automatiser la mise à jour de votre hébergement Pythonanywhere  
Difficulté : Moyenne (~15 minutes)
---------------------------------------------------------------------------------------------
Dans le Repository GitHUB que vous venez de créer précédemment lors de la séquence 1, vous avez un fichier intitulé deploy-pythonanywhere.yml et qui est déposé dans le répertoire .github/workflows. Ce fichier a pour objectif d'automatiser le déploiement de votre code sur votre site Pythonanywhere. Pour information, c'est ce que l'on appel des Actions GitHUB. Ce sont des scripts qui s'exécutent automatiquement lors de chaque Commit dans votre projet (C'est à dire à chaque modification de votre code). Ces scripts (appelés actions) sont au format yml qui est un format structuré proche de celui d'XML.  

Pour utiliser cette Action (deploy-pythonanywhere.yml), **vous avez besoin de créer des secrets dans GitHUB** afin de ne pas divulguer des informations sensibles aux internautes de passage dans votre Repository comme vos login et password par exemple.  

Pour cet atelier, **vous avez 4 secrets à créer** dans votre Repository GitHUB : **Settings → Secrets and variables → Actions → New repository secret**  
  
**PA_USERNAME** = votre username PythonAnywhere.  
**PA_TOKEN** = votre API token. Token à créer dans pythonanywhere (Acount → API Token).  
**PA_TARGET_DIR** = Web → Source code (ex: /home/monuser/myapp).  
**PA_WEBAPP_DOMAIN** = votre site (ex: monuser.pythonanywhere.com).  
  
**Dernière étape :** Pour engager l'automatisation de votre première Action, vous devez cliquer sur le gros boutton vert dans l'onglet supérieur [Actions] dans votre Repository Github. Le boutton s'intitule "I understand my workflows, go ahead and enable them"   

Notions acquises de cette séquence :  
Vous avez vu dans cette séquence comment créer des secrets GiHUB afin de mettre en place de l'industrialisation continue.   

---------------------------------------------------
🗺️ Séquence 4 : OSI (Open Systems Interconnection)
---------------------------------------------------
Vous pouvez observez les différentes couches OSI sur votre site **{site}.pythonanywhere.com/osi**  
  
**Exercice 1 : Définissez les termes suivants (Répondre directement dans GitHub)**    
### Un protocole,
Un protocole est un ensemble de règles et de conventions qui régissent la communication entre deux entités de même niveau (même couche) dans un système en réseau. Il définit le format des messages échangés, l'ordre dans lequel ils sont envoyés, ainsi que les actions à entreprendre lors de leur émission ou réception.

### Une entité protocolaire,
Une entité protocolaire est un élément actif (logiciel ou matériel) qui implémente un protocole au sein d'une couche donnée. Elle est capable d'envoyer et de recevoir des PDU (Protocol Data Units) en respectant les règles du protocole. Deux entités homologues (dans deux machines différentes) communiquent via le même protocole.

### Un service,
Un service est l'ensemble des fonctionnalités qu'une couche (N) offre à la couche supérieure (N+1). Il représente ce que la couche sait faire, sans exposer comment elle le fait. La relation est verticale : une couche rend service à celle qui est au-dessus d'elle.
  
### Une primitive de service,
Une primitive de service est une opération élémentaire permettant d'interagir avec un service. Elle matérialise les échanges entre deux couches adjacentes. On distingue quatre types canoniques : Request (demande d'un service), Indication (notification à l'entité distante), Response (réponse à une indication) et Confirm (confirmation de la requête initiale).

### Une Service Data Unit (SDU) par rapport à une PDU
Une SDU (Service Data Unit) est le bloc de données transmis par la couche (N+1) à la couche (N) pour être acheminé. C'est la donnée utile du point de vue de la couche inférieure.

Une PDU (Protocol Data Unit) est le bloc de données que la couche (N) construit en ajoutant son propre en-tête (et éventuellement un trailer) à la SDU reçue. La PDU de la couche (N) devient la SDU de la couche (N−1).

### Un point d'accès à un service SAP (Service Access Point)  
Un SAP est l'interface abstraite entre deux couches adjacentes, le point précis où la couche (N) met son service à disposition de la couche (N+1). Il est identifié par une adresse unique (ex. : numéro de port TCP, SAP LLC…) qui permet de démultiplexer les données vers la bonne entité de la couche supérieure.

---------------------------------------------------
🗺️ Séquence 5 : Retour sur le protocole DHCP
---------------------------------------------------
Vous pouvez observez le protocole DHCP sur votre site **{site}.pythonanywhere.com/dhcp**  
  
**Exercice 2 : Créer une image montrant l’encapsulation des couches suivantes**    
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Encapsulation DHCP</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;600;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
* { margin:0; padding:0; box-sizing:border-box; }

body {
  background: #f0ede8;
  font-family: 'Syne', sans-serif;
  color: #1a1410;
  min-height: 100vh;
  padding: 40px 24px 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-image:
    repeating-linear-gradient(0deg, transparent, transparent 39px, rgba(0,0,0,0.04) 39px, rgba(0,0,0,0.04) 40px),
    repeating-linear-gradient(90deg, transparent, transparent 39px, rgba(0,0,0,0.04) 39px, rgba(0,0,0,0.04) 40px);
}

/* ── Header ── */
.page-header {
  text-align: center;
  margin-bottom: 44px;
}
.proto-badge {
  display: inline-block;
  background: #1a1410;
  color: #f0ede8;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.7rem;
  letter-spacing: 0.3em;
  padding: 6px 16px;
  border-radius: 2px;
  margin-bottom: 12px;
  text-transform: uppercase;
}
h1 {
  font-size: 2.6rem;
  font-weight: 800;
  line-height: 1;
  letter-spacing: -0.02em;
  margin-bottom: 4px;
}
h1 span { color: #c0392b; }
.tagline {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.72rem;
  color: #7a6f65;
  letter-spacing: 0.15em;
}

/* ── Layout ── */
.canvas {
  width: 100%;
  max-width: 980px;
  display: grid;
  grid-template-columns: 200px 1fr 200px;
  gap: 0 20px;
  align-items: start;
}

/* ── DORA Steps ── */
.dora-col {
  display: flex;
  flex-direction: column;
  gap: 0;
  padding-top: 60px;
}
.dora-step {
  position: relative;
  padding: 14px 16px;
  margin-bottom: 4px;
  border-radius: 6px;
  border-left: 4px solid;
  background: #fff;
  box-shadow: 2px 2px 0 rgba(0,0,0,0.08);
  opacity: 0;
  transform: translateX(-20px);
  animation: slideIn 0.5s forwards;
}
.dora-step:nth-child(1) { animation-delay: 0.1s; border-color: #e67e22; }
.dora-step:nth-child(2) { animation-delay: 0.25s; border-color: #27ae60; }
.dora-step:nth-child(3) { animation-delay: 0.4s; border-color: #2980b9; }
.dora-step:nth-child(4) { animation-delay: 0.55s; border-color: #8e44ad; }

.dora-letter {
  font-size: 1.5rem;
  font-weight: 800;
  line-height: 1;
}
.dora-step:nth-child(1) .dora-letter { color: #e67e22; }
.dora-step:nth-child(2) .dora-letter { color: #27ae60; }
.dora-step:nth-child(3) .dora-letter { color: #2980b9; }
.dora-step:nth-child(4) .dora-letter { color: #8e44ad; }

.dora-name {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.7rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: #3d3530;
  margin-top: 2px;
}
.dora-desc {
  font-size: 0.65rem;
  color: #7a6f65;
  margin-top: 4px;
  line-height: 1.4;
}

/* ── Info col ── */
.info-col {
  padding-top: 60px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.info-card {
  background: #fff;
  border-radius: 6px;
  padding: 14px 16px;
  box-shadow: 2px 2px 0 rgba(0,0,0,0.08);
  border-top: 3px solid #1a1410;
  opacity: 0;
  animation: slideIn2 0.5s forwards;
}
.info-card:nth-child(1) { animation-delay: 0.7s; }
.info-card:nth-child(2) { animation-delay: 0.85s; }
.info-card:nth-child(3) { animation-delay: 1.0s; }
.info-title {
  font-size: 0.6rem;
  font-family: 'IBM Plex Mono', monospace;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #7a6f65;
  margin-bottom: 6px;
}
.port-row {
  display: flex;
  gap: 10px;
}
.port-badge {
  flex: 1;
  background: #1a1410;
  color: #f0ede8;
  border-radius: 4px;
  padding: 8px;
  text-align: center;
}
.port-badge .num {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 1.2rem;
  font-weight: 700;
  display: block;
}
.port-badge .lbl {
  font-size: 0.6rem;
  opacity: 0.6;
  letter-spacing: 0.1em;
}
.bail-text {
  font-size: 0.72rem;
  color: #3d3530;
  line-height: 1.5;
}
.risk-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.risk-list li {
  font-size: 0.68rem;
  color: #c0392b;
  padding-left: 14px;
  position: relative;
  line-height: 1.4;
}
.risk-list li::before {
  content: '⚠';
  position: absolute;
  left: 0;
  font-size: 0.6rem;
}

/* ── Centre: Encapsulation stack ── */
.encap-col {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  gap: 0;
}
.encap-title {
  text-align: center;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.65rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: #7a6f65;
  margin-bottom: 14px;
}

.layer-block {
  position: relative;
  border-radius: 8px;
  margin-bottom: 5px;
  overflow: hidden;
  opacity: 0;
  animation: fadeUp 0.5s forwards;
  box-shadow: 3px 3px 0 rgba(0,0,0,0.1);
}
.layer-block:nth-child(2) { animation-delay: 0.05s; }
.layer-block:nth-child(3) { animation-delay: 0.15s; }
.layer-block:nth-child(4) { animation-delay: 0.25s; }
.layer-block:nth-child(5) { animation-delay: 0.35s; }
.layer-block:nth-child(6) { animation-delay: 0.45s; }

.layer-header {
  display: flex;
  align-items: center;
  padding: 8px 14px;
  gap: 10px;
}
.layer-num-badge {
  font-family: 'IBM Plex Mono', monospace;
  font-weight: 700;
  font-size: 1rem;
  width: 28px;
  height: 28px;
  border-radius: 50%;
  display: flex; align-items:center; justify-content:center;
  flex-shrink: 0;
  color: #fff;
}
.layer-title-group { flex: 1; }
.layer-name-main {
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.layer-name-fr {
  font-size: 0.6rem;
  opacity: 0.6;
  font-family: 'IBM Plex Mono', monospace;
}
.pdu-name-badge {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.65rem;
  font-weight: 600;
  background: rgba(0,0,0,0.15);
  padding: 3px 9px;
  border-radius: 20px;
}

/* PDU visual row */
.pdu-visual {
  display: flex;
  margin: 0 10px 10px;
  border-radius: 5px;
  overflow: hidden;
  height: 30px;
  border: 1px solid rgba(0,0,0,0.1);
}
.pv-hdr {
  display:flex; align-items:center; justify-content:center;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.58rem;
  font-weight: 700;
  color: #fff;
  padding: 0 8px;
  white-space: nowrap;
  border-right: 1px solid rgba(255,255,255,0.2);
  letter-spacing: 0.03em;
}
.pv-data {
  flex:1;
  display:flex; align-items:center; justify-content:center;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.6rem;
  color: rgba(0,0,0,0.3);
  background: rgba(255,255,255,0.5);
  font-style: italic;
}
.pv-trl {
  display:flex; align-items:center; justify-content:center;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.58rem;
  font-weight: 700;
  color: #fff;
  padding: 0 8px;
  border-left: 1px solid rgba(255,255,255,0.2);
}

/* Layer colors */
.app   { background: #fef3e2; border: 2px solid #e67e22; }
.app   .layer-num-badge { background: #e67e22; }
.app   .layer-name-main { color: #a04000; }
.app   .pv-hdr, .app .pv-trl { background: #e67e22; }

.trans { background: #eafaf1; border: 2px solid #27ae60; }
.trans .layer-num-badge { background: #27ae60; }
.trans .layer-name-main { color: #1a5c30; }
.trans .pv-hdr, .trans .pv-trl { background: #27ae60; }

.net   { background: #eaf4fb; border: 2px solid #2980b9; }
.net   .layer-num-badge { background: #2980b9; }
.net   .layer-name-main { color: #1a4d73; }
.net   .pv-hdr, .net .pv-trl { background: #2980b9; }

.link  { background: #f5eef8; border: 2px solid #8e44ad; }
.link  .layer-num-badge { background: #8e44ad; }
.link  .layer-name-main { color: #5b2c6f; }
.link  .pv-hdr, .link .pv-trl { background: #8e44ad; }

.phys  { background: #fdfefe; border: 2px solid #717d7e; }
.phys  .layer-num-badge { background: #717d7e; }
.phys  .layer-name-main { color: #2c3e50; }

/* Arrow */
.arrow-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2px 0;
}
.arrow-svg { width: 16px; opacity: 0.3; }

/* Medium bar */
.medium-bar {
  margin: 6px 10px 0;
  height: 28px;
  background: repeating-linear-gradient(
    45deg,
    #717d7e,
    #717d7e 4px,
    #9eaaab 4px,
    #9eaaab 8px
  );
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.medium-bar span {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #fff;
  letter-spacing: 0.1em;
  text-shadow: 0 1px 3px rgba(0,0,0,0.5);
}

/* Connector lines between stack and DORA */
.conn-line {
  position: absolute;
  right: -20px;
  top: 50%;
  width: 20px;
  height: 2px;
  background: rgba(0,0,0,0.15);
}

/* Footer */
.footer {
  margin-top: 36px;
  width: 100%;
  max-width: 980px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px 20px;
  background: #1a1410;
  border-radius: 8px;
  color: #f0ede8;
  opacity: 0;
  animation: fadeUp 0.5s 1.2s forwards;
}
.footer-left {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.65rem;
  letter-spacing: 0.15em;
  color: #7a6f65;
}
.mnemonic {
  font-size: 1rem;
  font-weight: 800;
  letter-spacing: 0.1em;
}
.mnemonic span:nth-child(1) { color: #e67e22; }
.mnemonic span:nth-child(2) { color: #27ae60; }
.mnemonic span:nth-child(3) { color: #2980b9; }
.mnemonic span:nth-child(4) { color: #8e44ad; }
.footer-right {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.65rem;
  color: #7a6f65;
  text-align: right;
}

@keyframes fadeUp {
  to { opacity:1; transform: translateY(0); }
  from { opacity:0; transform: translateY(12px); }
}
@keyframes slideIn {
  to { opacity:1; transform: translateX(0); }
}
@keyframes slideIn2 {
  to { opacity:1; transform: translateX(0); }
  from { opacity:0; transform: translateX(20px); }
}
</style>
</head>
<body>

<!-- Header -->
<div class="page-header">
  <div class="proto-badge">Protocole réseau · RFC 2131</div>
  <h1>Encapsulation <span>DHCP</span></h1>
  <div class="tagline">Dynamic Host Configuration Protocol · Traversée des couches OSI</div>
</div>

<div class="canvas">

  <!-- DORA Steps (left) -->
  <div class="dora-col">
    <div class="dora-step">
      <div class="dora-letter">D</div>
      <div class="dora-name">Discover</div>
      <div class="dora-desc">Le client diffuse un message broadcast pour trouver un serveur DHCP.</div>
    </div>
    <div class="dora-step">
      <div class="dora-letter">O</div>
      <div class="dora-name">Offer</div>
      <div class="dora-desc">Le serveur répond en proposant une adresse IP et une configuration.</div>
    </div>
    <div class="dora-step">
      <div class="dora-letter">R</div>
      <div class="dora-name">Request</div>
      <div class="dora-desc">Le client accepte l'offre et demande officiellement la configuration.</div>
    </div>
    <div class="dora-step">
      <div class="dora-letter">A</div>
      <div class="dora-name">Acknowledge</div>
      <div class="dora-desc">Le serveur confirme et attribue définitivement la configuration réseau.</div>
    </div>
  </div>

  <!-- Encapsulation Stack (centre) -->
  <div class="encap-col">
    <div class="encap-title">↓ Encapsulation à l'émission &nbsp;·&nbsp; ↑ Décapsulation à la réception</div>

    <!-- Layer 7 — Application -->
    <div class="layer-block app">
      <div class="layer-header">
        <div class="layer-num-badge">7</div>
        <div class="layer-title-group">
          <div class="layer-name-main">Application</div>
          <div class="layer-name-fr">DHCP service</div>
        </div>
        <div class="pdu-name-badge">Message DHCP</div>
      </div>
      <div class="pdu-visual">
        <div class="pv-hdr" style="min-width:90px">DHCP Header</div>
        <div class="pv-data">DISCOVER / OFFER / REQUEST / ACK</div>
      </div>
    </div>

    <div class="arrow-wrap">
      <svg class="arrow-svg" viewBox="0 0 16 20" fill="none">
        <path d="M8 0 L8 14 M2 8 L8 16 L14 8" stroke="#1a1410" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <!-- Layer 4 — Transport -->
    <div class="layer-block trans">
      <div class="layer-header">
        <div class="layer-num-badge">4</div>
        <div class="layer-title-group">
          <div class="layer-name-main">Transport</div>
          <div class="layer-name-fr">UDP — sans connexion</div>
        </div>
        <div class="pdu-name-badge">Datagramme UDP</div>
      </div>
      <div class="pdu-visual">
        <div class="pv-hdr" style="min-width:80px;background:#1a5c30">UDP Hdr<br><span style="font-size:0.5rem;opacity:0.8">67/68</span></div>
        <div class="pv-hdr">DHCP Hdr</div>
        <div class="pv-data">Données DHCP</div>
      </div>
    </div>

    <div class="arrow-wrap">
      <svg class="arrow-svg" viewBox="0 0 16 20" fill="none">
        <path d="M8 0 L8 14 M2 8 L8 16 L14 8" stroke="#1a1410" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <!-- Layer 3 — Network -->
    <div class="layer-block net">
      <div class="layer-header">
        <div class="layer-num-badge">3</div>
        <div class="layer-title-group">
          <div class="layer-name-main">Réseau</div>
          <div class="layer-name-fr">IP — 0.0.0.0 → 255.255.255.255</div>
        </div>
        <div class="pdu-name-badge">Paquet IP</div>
      </div>
      <div class="pdu-visual">
        <div class="pv-hdr" style="min-width:70px;background:#1a4d73">IP Hdr</div>
        <div class="pv-hdr" style="background:#1a5c30">UDP</div>
        <div class="pv-hdr">DHCP</div>
        <div class="pv-data">Données</div>
      </div>
    </div>

    <div class="arrow-wrap">
      <svg class="arrow-svg" viewBox="0 0 16 20" fill="none">
        <path d="M8 0 L8 14 M2 8 L8 16 L14 8" stroke="#1a1410" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <!-- Layer 2 — Data Link -->
    <div class="layer-block link">
      <div class="layer-header">
        <div class="layer-num-badge">2</div>
        <div class="layer-title-group">
          <div class="layer-name-main">Liaison</div>
          <div class="layer-name-fr">Ethernet — broadcast MAC</div>
        </div>
        <div class="pdu-name-badge">Trame Ethernet</div>
      </div>
      <div class="pdu-visual">
        <div class="pv-hdr" style="min-width:66px;background:#5b2c6f">ETH Hdr</div>
        <div class="pv-hdr" style="background:#1a4d73">IP</div>
        <div class="pv-hdr" style="background:#1a5c30">UDP</div>
        <div class="pv-hdr" style="font-size:0.5rem">DHCP</div>
        <div class="pv-data">…</div>
        <div class="pv-trl" style="background:#5b2c6f">FCS</div>
      </div>
    </div>

    <div class="arrow-wrap">
      <svg class="arrow-svg" viewBox="0 0 16 20" fill="none">
        <path d="M8 0 L8 14 M2 8 L8 16 L14 8" stroke="#1a1410" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <!-- Layer 1 — Physical -->
    <div class="layer-block phys">
      <div class="layer-header">
        <div class="layer-num-badge">1</div>
        <div class="layer-title-group">
          <div class="layer-name-main">Physique</div>
          <div class="layer-name-fr">Bits sur le médium</div>
        </div>
        <div class="pdu-name-badge">Bits / Signal</div>
      </div>
      <div class="medium-bar">
        <span>01001101 01001000 01000011 01010000 · · · · signal électrique / radio</span>
      </div>
      <div style="height:10px"></div>
    </div>

  </div>

  <!-- Info col (right) -->
  <div class="info-col">

    <div class="info-card">
      <div class="info-title">Ports UDP</div>
      <div class="port-row">
        <div class="port-badge">
          <span class="num">67</span>
          <span class="lbl">SERVEUR</span>
        </div>
        <div class="port-badge" style="background:#3d3530">
          <span class="num">68</span>
          <span class="lbl">CLIENT</span>
        </div>
      </div>
    </div>

    <div class="info-card">
      <div class="info-title">Bail (Lease)</div>
      <div class="bail-text">L'adresse IP est attribuée pour une <strong>durée limitée</strong>. Le client renouvelle son bail avant expiration pour conserver sa configuration.</div>
    </div>

    <div class="info-card" style="border-top-color: #c0392b;">
      <div class="info-title" style="color:#c0392b">Points de vigilance</div>
      <ul class="risk-list">
        <li>Faux serveur DHCP (Rogue DHCP)</li>
        <li>Conflits d'adresses IP</li>
        <li>Point critique de l'infrastructure</li>
      </ul>
    </div>

  </div>
</div>

<!-- Footer mnemonic -->
<div class="footer">
  <div class="footer-left">MNÉMONIQUE</div>
  <div class="mnemonic">
    <span>D</span>iscover &nbsp;·&nbsp;
    <span>O</span>ffer &nbsp;·&nbsp;
    <span>R</span>equest &nbsp;·&nbsp;
    <span>A</span>cknowledge
  </div>
  <div class="footer-right">UDP · Broadcast<br>Sans connexion préalable</div>
</div>

</body>
</html> 
  
--------------------------------------------------------------------
🧠 Troubleshooting :
---------------------------------------------------
Objectif : Visualiser ses logs et découvrir ses erreurs
---------------------------------------------------
Lors de vos développements, vous serez peut-être confronté à des erreurs systèmes car vous avez faits des erreurs de syntaxes dans votre code, faits de mauvaises déclarations de fonctions, appelez des modules inexistants, mal renseigner vos secrets, etc…  
Les causes d'erreurs sont quasi illimitées. **Vous devez donc vous tourner vers les logs de votre système pour comprendre d'où vient le problème** :  

Vos log sont accéssible via les URL suivantes :  
* Access log : {site}.pythonanywhere.com.access.log
* Error log : {site}.pythonanywhere.com.error.log
* Server log: {site}.pythonanywhere.com.server.log
