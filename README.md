<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BTP Hélicoptère — Boîte de Transmission Principale</title>
<style>
@import url(' https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@300;500;700&display=swap' );

:racine {
--bg: #080c10;
--panneau : #0d1520 ;
--bordure : #1e3a50 ;
--accent: #00c8ff;
--accent2: #ff6b00;
--vert : #00ff88 ;
--jaune : #ffe033 ;
--texte: #b0cce0;
--dim: #3a5a6a;
}

* { margin:0; padding:0; box-sizing:border-box; }

corps {
arrière-plan : var(--bg);
couleur : var(--texte);
famille de polices : 'Rajdhani', sans empattement ;
police-weight: 300;
hauteur minimale : 100vh ;
débordement-x : caché ;
}

corps::avant {
contenu:'';
position:fixe;
incrustation : 0 ;
arrière-plan : dégradé linéaire répétitif (0deg, transparent, transparent 2px, rgba(0,200,255,0.012) 2px, rgba(0,200,255,0.012) 4px);
événements de pointeur : aucun ;
z-index:999;
}

en-tête {
affichage : flexible ;
aligner-éléments:centre;
justifier-contenu:espace-entre;
marge intérieure : 1rem 2rem ;
border-bottom : 1px solid var(--border);
arrière-plan : var(--panel);
}
.logo-tag {
police-family:'Share Tech Mono', monospace;
taille de police : 0,6rem ;
couleur : var(--accent);
arrière-plan : rgba(0,200,255,0.08);
bordure : 1px solide rgba(0,200,255,0,25);
marge intérieure : 4px 10px ;
espacement des lettres : 0,12 em ;
bordure-radius:3px;
marge droite : 1rem ;
}
en-tête h1 {
famille de polices : 'Rajdhani', sans empattement ;
police-weight:700;
taille de police : clamp(1rem, 3vw, 1,6rem);
espacement des lettres : 0,08 em ;
couleur : var(--accent);
text-shadow: 0 0 20px rgba(0,200,255,0.4);
}
titre h1 span { couleur: var(--texte); épaisseur de police: 300; }
.status-bar { display:flex; gap:0.8rem; align-items:center; }
.status-dot {
largeur : 8 px ; hauteur : 8 px ; rayon de bordure : 50 % ;
arrière-plan : var(--vert);
box-shadow: 0 0 8px var(--green);
animation : clignotement de 1,8 s avec transition infinie ;
}
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.3} }
.status-txt { font-family:'Share Tech Mono', monospace; font-size:0.62rem; color: var(--green); letter-spacing:0.1em; }

.principal {
affichage : grille ;
grid-template-columns: 1fr 320px;
largeur maximale : 1200px ;
marge : 0 automatique ;
}

.viz-panel {
bordure droite : 1px solide var(--border);
border-bottom : 1px solid var(--border);
marge intérieure : 1,2 rem ;
position : relative ;
arrière-plan : dégradé radial (ellipse à 40 % 40 %, rgba(0,80,120,0.08) 0 %, transparent 70 %) ;
}
.viz-title {
police-family:'Share Tech Mono', monospace;
taille de police : 0,58 rem ;
couleur : var(--dim);
espacement des lettres : 0,15 em ;
marge inférieure : 0,8rem ;
}

svg#btp { largeur:100%; affichage:bloc; débordement:visible; }

.info-panel {
arrière-plan : var(--panel);
border-bottom : 1px solid var(--border);
affichage : flexible ;
direction flexible : colonne ;
hauteur maximale : 520 px ;
}
.info-header {
marge intérieure : 0,8rem 1,2rem 0,5rem ;
border-bottom : 1px solid var(--border);
police-family:'Share Tech Mono', monospace;
taille de police : 0,58 rem ;
couleur : var(--dim);
espacement des lettres : 0,15 em ;
}
.component-list { flex:1; overflow-y:auto; }
.comp-item {
marge intérieure : 0,65 rem 1,2 rem ;
bordure inférieure : 1px solide rgba(30,58,80,0.5);
curseur : pointeur ;
transition : arrière-plan 0,2 s, bordure gauche 0,2 s ;
affichage : flexible ;
aligner-éléments:début-flexible;
écart : 0,7 rem ;
bordure gauche : 3px solide transparent ;
}
.comp-item:hover, .comp-item.active {
arrière-plan : rgba(0,200,255,0.05);
couleur de bordure gauche : var(--accent);
}
.comp-item.active .comp-name { color: var(--accent); }
.comp-icon { font-size:1.1rem; margin-top:1px; flex-shrink:0; }
.comp-name { font-weight:700; font-size:0.82rem; letter-spacing:0.04em; margin-bottom:2px; color: var(--text); transition:color 0.2s; }
.comp-desc { font-size:0.72rem; opacity:0.6; line-height:1.5; }
.comp-badge {
marge gauche : automatique ;
police-family:'Share Tech Mono', monospace;
taille de police : 0,55rem ;
couleur : var(--accent2);
bordure : 1px solide rgba(255,107,0,0.3);
marge intérieure : 2px 5px ;
bordure-radius:2px;
espace blanc : pas de retour à la ligne ;
rétrécissement flexible : 0 ;
}

.panneau-télémétrie {
colonne de grille : 1 / -1 ;
border-top : 1px solid var(--border);
arrière-plan : var(--panel);
marge intérieure : 0,8 rem 1,5 rem ;
affichage : grille ;
grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
écart : 1rem ;
}
.telem-label { font-family:'Share Tech Mono', monospace; font-size:0.54rem; letter-spacing:0.1em; color: var(--dim); text-transform:uppercase; margin-bottom:3px; }
.telem-value { font-family:'Share Tech Mono', monospace; font-size:1.3rem; font-weight:bold; color: var(--accent); text-shadow: 0 0 12px rgba(0,200,255,0.5); }
.telem-value.warn { color: var(--yellow); text-shadow: 0 0 12px rgba(255,224,51,0.5); }
.telem-bar { hauteur:3px; arrière-plan: rgba(255,255,255,0.07); bordure-radius:3px; débordement:masqué; marge-haut:4px; }
.telem-fill { hauteur:100%; bordure-radius:3px; arrière-plan: dégradé-linéaire(90deg, var(--accent), #00ffcc); transition: largeur 0.4s ease; }

.controls-row {
colonne de grille : 1 / -1 ;
marge intérieure : 0,7 rem 1,5 rem ;
arrière-plan : rgba(0,0,0,0.3);
border-top : 1px solid var(--border);
affichage : flexible ;
aligner-éléments:centre;
écart : 1,2 rem ;
flex-wrap:wrap;
}
.ctrl-label { font-family:'Share Tech Mono', monospace; font-size:0.6rem; color: var(--dim); letter-spacing:0.1em; white-space:nowrap; }
entrée[type=range] {
-webkit-appearance:none;
hauteur : 4px ;
arrière-plan : rgba(0,200,255,0.15);
bordure-radius:4px;
contour : aucun ;
flex:1; min-width:100px; max-width:200px; cursor:pointer;
}
input[type=range]::-webkit-slider-thumb {
-webkit-appearance:none;
largeur : 14 px ; hauteur : 14 px ; rayon de bordure : 50 % ;
arrière-plan : var(--accent);
box-shadow: 0 0 8px rgba(0,200,255,0.7);
curseur : pointeur ;
}
.ctrl-value { font-family:'Share Tech Mono', monospace; font-size:0.88rem; color: var(--accent); min-width:50px; }
.btn-pause {
police de caractères : « Rajdhani », sans empattement ; graisse : 700 ; taille : 0,78 rem ; espacement des lettres : 0,1 em ;
padding:5px 16px; background: transparent; border: 1px solid var(--accent);
couleur : var(--accent); bordure arrondie : 4 px; curseur : pointeur; transition : arrière-plan 0,2 s;
}
.btn-pause:hover { background: rgba(0,200,255,0.12); }
.btn-pause.paused { border-color: var(--accent2); color: var(--accent2); }

.detail-box {
position:absolute; bottom:1.2rem; left:1.2rem;
arrière-plan : rgba(8,12,16,0.94);
bordure : 1px solide var(--accent); rayon de bordure : 6px;
marge intérieure : 0,8 rem 1 rem ; largeur maximale : 250 px ;
taille de police : 0,75 rem ; hauteur de ligne : 1,6 ;
box-shadow: 0 0 20px rgba(0,200,255,0.12);
opacité : 0 ; transformation : translateY(6px) ;
transition : opacité 0,3 s, transformation 0,3 s ;
événements de pointeur : aucun ;
}
.detail-box.show { opacité:1; transform: translateY(0); }
.detail-box h4 { font-weight:700; font-size:0.85rem; color: var(--accent); margin-bottom:0.4rem; letter-spacing:0.06em; }
.detail-box p { opacité:0.75; }
</style>
</head>
<corps>

<header>
<div style="display:flex;align-items:center">
<div class="logo-tag">AIRBUS HELICOPTERS</div>
<h1>BTP <span>— Boîte de Transmission Principale</span></h1>
</div>
<div class="status-bar">
<div class="status-dot"></div>
<div class="status-txt">NOM DU SYSTÈME</div>
</div>
</header>

<div class="main">

<div class="viz-panel">
<div class="viz-title">// SCHÉMA CINÉMATIQUE BTP — NH90 / H225 SUPER PUMA</div>
<svg id="btp" viewBox="0 0 640 430" xmlns=" http://www.w3.org/2000/svg ">
<defs>
<filter id="glow"><feGaussianBlur stdDeviation="3" result="b"/><feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
<filter id="glowS"><feGaussianBlur stdDeviation="5" result="b"/><feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
<linearGradient id="sG" x1="0" y1="0" x2="1" y2="0">
<stop offset="0%" stop-color="#5080a0"/>
<stop offset="50%" stop-color="#c0d8e8"/>
<stop offset="100%" stop-color="#5080a0"/>
</linearGradient>
<linearGradient id="gG1" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#1e4a70"/>
<stop offset="100%" stop-color="#0d2030"/>
</linearGradient>
<linearGradient id="gG2" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#1a3a55"/>
<stop offset="100%" stop-color="#0a1825"/>
</linearGradient>
<radialGradient id="hubG" cx="40%" cy="35%">
<stop offset="0%" stop-color="#4090c0"/>
<stop offset="100%" stop-color="#0d2030"/>
</radialGradient>
<marker id="arrB" MarkerWidth="7" MarkerHeight="7" refX="5" refY="3" orient="auto">
<path d="M0,0 L0,6 L7,3 z" fill="#00c8ff" opacity="0.8"/>
</marker>
<marker id="arrO" MarkerWidth="7" MarkerHeight="7" refX="5" refY="3" orient="auto">
<path d="M0,0 L0,6 L7,3 z" fill="#ff6b00" opacity="0.8"/>
</marker>
<marker id="arrY" MarkerWidth="7" MarkerHeight="7" refX="5" refY="3" orient="auto">
<path d="M0,0 L0,6 L7,3 z" fill="#ffe033" opacity="0.8"/>
</marker>
</defs>

<g opacité="0.05" trait="00c8ff" largeur-trait="0.5">
<line x1="0" y1="0" x2="0" y2="430"/><line x1="80" y1="0" x2="80" y2="430"/><line x1="160" y1="0" x2="160" y2="430"/>
<line x1="240" y1="0" x2="240" y2="430"/><line x1="320" y1="0" x2="320" y2="430"/><line x1="400" y1="0" x2="400" y2="430"/>
<line x1="480" y1="0" x2="480" y2="430"/><line x1="560" y1="0" x2="560" y2="430"/>
<line x1="0" y1="0" x2="640" y2="0"/><line x1="0" y1="80" x2="640" y2="80"/>
<line x1="0" y1="160" x2="640" y2="160"/><line x1="0" y1="240" x2="640" y2="240"/>
<line x1="0" y1="320" x2="640" y2="320"/><line x1="0" y1="400" x2="640" y2="400"/>
</g>

<g>
<rect x="15" y="148" width="82" height="48" rx="6" fill="url(#gG2)" stroke="#2a5a80" stroke-width="1.5"/>
<text x="56" y="167" text-anchor="middle" font-family="Share Tech Mono" font-size="8" fill="#00c8ff">MOTEUR 1</text>
<text x="56" y="180" text-anchor="middle" font-family="Share Tech Mono" font-size="6.5" fill="#3a6a8a">Turbomeca</text>
<circle cx="97" cy="172" r="4" fill="#ff6b00" filter="url(#glow)">
<animate attributeName="r" values="3;5;3" dur="0.8s" repeatCount="indefinite"/>
<animate attributeName="opacity" values="0.5;1;0.5" dur="0.8s" repeatCount="indefinite"/>
</cercle>
</g>

<g>
<rect x="543" y="148" width="82" height="48" rx="6" fill="url(#gG2)" stroke="2a5a80" stroke-width="1.5"/>
<text x="584" y="167" text-anchor="middle" font-family="Share Tech Mono" font-size="8" fill="#00c8ff">MOTEUR 2</text>
<text x="584" y="180" text-anchor="middle" font-family="Share Tech Mono" font-size="6.5" fill="#3a6a8a">Turbomeca</text>
<circle cx="543" cy="172" r="4" fill="#ff6b00" filter="url(#glow)">
<animate attributeName="r" values="3;5;3" dur="0.9s" repeatCount="indefinite"/>
<animate attributeName="opacity" values="0.5;1;0.5" dur="0.9s" repeatCount="indefinite"/>
</cercle>
</g>

<rect x="97" y="168" width="96" height="8" rx="3" fill="url(#sG)" opacity="0.9"/>
<rect x="447" y="168" width="96" height="8" rx="3" fill="url(#sG)" opacity="0.9"/>
<line x1="108" y1="160" x2="148" y2="160" stroke="#ff6b00" stroke-width="1.2" marker-end="url(#arrO)" opacity="0.7"/>
<line x1="532" y1="160" x2="492" y2="160" stroke="#ff6b00" stroke-width="1.2" marker-end="url(#arrO)" opacity="0.7"/>
<text x="125" y="155" text-anchor="middle" font-family="Share Tech Mono" font-size="6" fill="#ff6b00" opacity="0.7">N1 22k tr/min</text>
<text x="515" y="155" text-anchor="middle" font-family="Share Tech Mono" font-size="6" fill="#ff6b00" opacity="0.7">N1 22k tr/min</text>

<rect x="190" y="88" width="260" height="230" rx="14" fill="url(#gG1)" stroke="#2a6a90" stroke-width="2"/>
<rect x="190" y="88" width="260" height="230" rx="14" fill="none" stroke="00c8ff" stroke-width="0.5" opacity="0.25"/>
<text x="320" y="108" text-anchor="middle" font-family="Share Tech Mono" font-size="7.5" fill="#00c8ff" opacity="0.75" letter-spacing="2.5">BOÎTE DE TRANSMISSION PRINCIPALE</text>

<circle cx="212" cy="172" r="7" fill="none" stroke="ffe033" stroke-width="1.5" stroke-dasharray="3 2" opacity="0.85"/>
<text x="212" y="158" text-anchor="middle" font-family="Share Tech Mono" font-size="6" fill="#ffe033" opacity="0.85">FW</text>
<circle cx="428" cy="172" r="7" fill="none" stroke="ffe033" stroke-width="1.5" stroke-dasharray="3 2" opacity="0.85"/>
<text x="428" y="158" text-anchor="middle" font-family="Share Tech Mono" font-size="6" fill="#ffe033" opacity="0.85">FW</text>

<g id="pinion1" style="transform-origin:244px 172px">
<circle cx="244" cy="172" r="26" fill="url(#gG2)" stroke="#2a8ab0" stroke-width="1.5"/>
<circle cx="244" cy="172" r="22" fill="none" stroke="3090b0" stroke-width="3" stroke-dasharray="6 4"/>
<circle cx="244" cy="172" r="10" fill="#0d2030" stroke="#1e4a70" stroke-width="1"/>
<line x1="244" y1="162" x2="244" y2="182" stroke="#2a6a90" stroke-width="1.5" opacity="0.5"/>
<line x1="234" y1="172" x2="254" y2="172" stroke="2a6a90" stroke-width="1.5" opacity="0.5"/>
<text x="244" y="176" text-anchor="middle" font-family="Share Tech Mono" font-size="6" fill="#5090a0">P1</text>
</g>

<g id="pinion2" style="transform-origin:396px 172px">
<circle cx="396" cy="172" r="26" fill="url(#gG2)" stroke="#2a8ab0" stroke-width="1.5"/>
<circle cx="396" cy="172" r="22" fill="none" stroke="3090b0" stroke-width="3" stroke-dasharray="6 4"/>
<circle cx="396" cy="172" r="10" fill="#0d2030" stroke="#1e4a70" stroke-width="1"/>
<line x1="396" y1="162" x2="396" y2="182" stroke="2a6a90" stroke-width="1.5" opacity="0.5"/>
<line x1="386" y1="172" x2="406" y2="172" stroke="2a6a90" stroke-width="1.5" opacity="0.5"/>
<text x="396" y="176" text-anchor="middle" font-family="Share Tech Mono" font-size="6" fill="#5090a0">P2</text>
</g>

<g id="intgear1" style="transform-origin:278px 206px">
<circle cx="278" cy="206" r="32" fill="url(#gG2)" stroke="#2a7a9a" stroke-width="1.5"/>
<circle cx="278" cy="206" r="27" fill="none" stroke="3090b0" stroke-width="3" stroke-dasharray="7 4"/>
<circle cx="278" cy="206" r="12" fill="#0d2030" stroke="#1e4a70" stroke-width="1"/>
<line x1="278" y1="194" x2="278" y2="218" stroke="2a6a90" stroke-width="1.5" opacity="0.4"/>
<line x1="266" y1="206" x2="290" y2="206" stroke="#2a6a90" stroke-width="1.5" opacity="0.4"/>
<text x="278" y="210" text-anchor="middle" font-family="Share Tech Mono" font-size="6" fill="#5090a0">IG1</text>
</g>
<g id="intgear2" style="transform-origin:362px 206px">
<circle cx="362" cy="206" r="32" fill="url(#gG2)" stroke="#2a7a9a" stroke-width="1.5"/>
<circle cx="362" cy="206" r="27" fill="none" stroke="3090b0" stroke-width="3" stroke-dasharray="7 4"/>
<circle cx="362" cy="206" r="12" fill="#0d2030" stroke="#1e4a70" stroke-width="1"/>
<line x1="362" y1="194" x2="362" y2="218" stroke="#2a6a90" stroke-width="1.5" opacity="0.4"/>
<line x1="350" y1="206" x2="374" y2="206" stroke="2a6a90" stroke-width="1.5" opacity="0.4"/>
<text x="362" y="210" text-anchor="middle" font-family="Share Tech Mono" font-size="6" fill="#5090a0">IG2</text>
</g>

<circle cx="320" cy="206" r="60" fill="none" stroke="1e4a70" stroke-width="4"/>
<circle cx="320" cy="206" r="60" fill="none" stroke="#2a6a90" stroke-width="2" stroke-dasharray="12 5"/>
<text x="395" y="290" font-family="Share Tech Mono" font-size="6" fill="#3a6a80">COURONNE FIXE</text>

<g id="carrier" style="transform-origin:320px 206px">
<g id="pl1">
<circle cx="320" cy="158" r="14" fill="url(#gG2)" stroke="3090b0" stroke-width="1.5"/>
<circle cx="320" cy="158" r="10" fill="none" stroke="#2a8ab0" stroke-width="2" stroke-dasharray="4 3"/>
<circle cx="320" cy="158" r="4" fill="#0d2030"/>
</g>
<g id="pl2">
<circle cx="283" cy="228" r="14" fill="url(#gG2)" stroke="3090b0" stroke-width="1.5"/>
<circle cx="283" cy="228" r="10" fill="none" stroke="#2a8ab0" stroke-width="2" stroke-dasharray="4 3"/>
<circle cx="283" cy="228" r="4" fill="#0d2030"/>
</g>
<g id="pl3">
<circle cx="357" cy="228" r="14" fill="url(#gG2)" stroke="3090b0" stroke-width="1.5"/>
<circle cx="357" cy="228" r="10" fill="none" stroke="#2a8ab0" stroke-width="2" stroke-dasharray="4 3"/>
<circle cx="357" cy="228" r="4" fill="#0d2030"/>
</g>
<line x1="320" y1="206" x2="320" y2="172" stroke="1e4a70" stroke-width="2" opacity="0.5"/>
<line x1="320" y1="206" x2="290" y2="220" stroke="1e4a70" stroke-width="2" opacity="0.5"/>
<line x1="320" y1="206" x2="350" y2="220" stroke="1e4a70" stroke-width="2" opacity="0.5"/>
</g>

<g id="sungear" style="transform-origin:320px 206px">
<circle cx="320" cy="206" r="20" fill="url(#hubG)" stroke="#3ab0d0" stroke-width="2" filter="url(#glow)"/>
<circle cx="320" cy="206" r="14" fill="none" stroke="#00c8ff" stroke-width="1.5" stroke-dasharray="4 3" opacity="0.6"/>
<circle cx="320" cy="206" r="5" fill="#0d2030" stroke="#00c8ff" stroke-width="1"/>
</g>

<rect x="314" y="24" width="12" height="66" rx="4" fill="url(#sG)" filter="url(#glow)"/>
<line x1="320" y1="18" x2="320" y2="26" stroke="#00c8ff" stroke-width="2" marker-end="url(#arrB)" opacity="0.9"/>
<text x="338" y="56" font-family="Share Tech Mono" font-size="6" fill="#00c8ff" opacity="0.7">Nr ~265 tr/min</text>

<circle cx="320" cy="26" r="20" fill="url(#gG1)" stroke="#3ab0d0" stroke-width="2" filter="url(#glow)"/>
<circle cx="320" cy="26" r="9" fill="url(#hubG)" stroke="#00c8ff" stroke-width="1.5"/>

<g id="rotorBlades" style="transform-origin:320px 26px">
<rect x="322" y="-32" width="9" height="58" rx="4" fill="url(#gG2)" stroke="3090b0" stroke-width="1" transform="rotate(0 320 26)"/>
<rect x="322" y="-32" width="9" height="58" rx="4" fill="url(#gG2)" stroke="3090b0" stroke-width="1" transform="rotate(60 320 26)"/>
<rect x="322" y="-32" width="9" height="58" rx="4" fill="url(#gG2)" stroke="3090b0" stroke-width="1" transform="rotate(120 320 26)"/>
<rect x="322" y="-32" width="9" height="58" rx="4" fill="url(#gG2)" stroke="3090b0" stroke-width="1" transform="rotate(180 320 26)"/>
<rect x="322" y="-32" width="9" height="58" rx="4" fill="url(#gG2)" stroke="3090b0" stroke-width="1" transform="rotate(240 320 26)"/>
</g>
<text x="258" y="22" font-family="Share Tech Mono" font-size="6.5" fill="#00c8ff" opacity="0.6">PRINCIPAL DU ROTOR</text>

<rect x="450" ​​y="234" width="88" height="7" rx="3" fill="url(#sG)" opacity="0.75"/>
<line x1="500" y1="226" x2="530" y2="226" stroke="#ffe033" stroke-width="1.2" marker-end="url(#arrY)" opacity="0.7"/>
<text x="460" y="224" font-family="Share Tech Mono" font-size="6" fill="#ffe033" opacity="0.8">ROTOR ANTI-COUPLE</text>
<rect x="538" y="226" width="38" height="22" rx="4" fill="url(#gG2)" stroke="4a6a40" stroke-width="1"/>
<text x="557" y="238" text-anchor="middle" font-family="Share Tech Mono" font-size="5.5" fill="#80a070">TGB</text>

<rect x="208" y="284" width="52" height="22" rx="4" fill="url(#gG2)" stroke="#2a5a70" stroke-width="1"/>
<text x="234" y="294" text-anchor="middle" font-family="Share Tech Mono" font-size="5.5" fill="#5090a0">HYDRO.</text>
<text x="234" y="302" text-anchor="middle" font-family="Share Tech Mono" font-size="5.5" fill="#5090a0">POMPE</text>
<rect x="380" y="284" width="52" height="22" rx="4" fill="url(#gG2)" stroke="#2a5a70" stroke-width="1"/>
<text x="406" y="294" text-anchor="middle" font-family="Share Tech Mono" font-size="5.5" fill="#5090a0">MODIFIER.</text>
<text x="406" y="302" text-anchor="middle" font-family="Share Tech Mono" font-size="5.5" fill="#5090a0">28 V CC</text>
<rect x="248" y="289" width="72" height="5" rx="2" fill="#1e4a60" opacity="0.5"/>
<rect x="320" y="289" width="60" height="5" rx="2" fill="#1e4a60" opacity="0.5"/>
<text x="208" y="326" font-family="Share Tech Mono" font-size="6.5" fill="#00ff88" opacity="0.55">CIRCUIT HUILE SYNTHÉTIQUE</text>
<text x="320" y="378" text-anchor="middle" font-family="Share Tech Mono" font-size="7" fill="#2a5a70">RÉDUCTION GLOBALE ~1/65 · N1 : 22 000 tr/min → Nr : 265 tr/min</text>
</svg>

<div class="detail-box" id="detailBox">
<h4 id="detailTitle">—</h4>
<p id="detailText">—</p>
</div>
</div>

<div class="info-panel">
<div class="info-header">// SYSTÈME DE COMPOSANTS</div>
<div class="component-list">
<div class="comp-item active" data-id="moteurs"><div class="comp-icon">🔥</div><div><div class="comp-name">Turbomoteurs</div><div class="comp-desc">2× Turbomeca Makila / RTM322. Sortie N1 ≈ 22 000 tr/min.</div></div><div class="comp-badge">×2</div></div>
<div class="comp-item" data-id="freewheel"><div class="comp-icon">🔓</div><div><div class="comp-name">Roue libre (Freewheel)</div><div class="comp-desc">Découpler un moteur en panne pour permettre l'autorotation.</div></div><div class="comp-badge">FW</div></div>
<div class="comp-item" data-id="pinions"><div class="comp-icon">⚙️</div><div><div class="comp-name">Pignons d'entrée</div><div class="comp-desc">Pignons coniques hélicoïdaux. Premier étage de réduction.</div></div><div class="comp-badge">BEVEL</div></div>
<div class="comp-item" data-id="planetary"><div class="comp-icon">🌍</div><div><div class="comp-name">Train épicycloïdal</div><div class="comp-desc">3 satellites, planétaire central, couronne fixe. Ratio ~1/65.</div></div><div class="comp-badge">ÉPICYCL.</div></div>
<div class="comp-item" data-id="arbre"><div class="comp-icon">🔩</div><div><div class="comp-name">Arbre rotor principal</div><div class="comp-desc">Sortie ≈ 265 tr/min. Acier forgé haute résistance.</div></div><div class="comp-badge">Nr ~265</div></div>
<div class="comp-item" data-id="tailshaft"><div class="comp-icon">↗️</div><div><div class="comp-name">Quai de transmission (TGB)</div><div class="comp-desc">Renvoi d'angle vers le rotor anti-couple.</div></div><div class="comp-badge">TGB</div></div>
<div class="comp-item" data-id="accessories"><div class="comp-icon">⚡</div><div><div class="comp-name">Accessoires (PTO)</div><div class="comp-desc">Pompes hydrauliques, alternateurs 28V DC.</div></div><div class="comp-badge">PTO</div></div>
<div class="comp-item" data-id="lubrication"><div class="comp-icon">🛢️</div><div><div class="comp-name">Lubrification HUMS</div><div class="comp-desc">Huile synthétique surveillée en continu par le HUMS.</div></div><div class="comp-badge">HUMS</div></div>
</div>
</div>

<div class="panneau de télémétrie">
<div class="telem"><div class="telem-label">// N1 Mot.1 (tr/min)</div><div class="telem-value" id="t-n1">22 142</div><div class="telem-bar"><div class="telem-fill" id="b-n1" style="width:88%"></div></div></div>
<div class="telem"><div class="telem-label">// Nombre de rotors (tr/min)</div><div class="telem-value" id="t-nr">265</div><div class="telem-bar"><div class="telem-fill" id="b-nr" style="width:92%;background:linear-gradient(90deg,#00ff88,#00c8ff)"></div></div></div>
<div class="telem"><div class="telem-label">// Couple BTP (kNm)</div><div class="telem-value" id="t-torque">18,4</div><div class="telem-bar"><div class="telem-fill" id="b-torque" style="width:72%"></div></div></div>
<div class="telem"><div class="telem-label">// Temp. Huile (°C)</div><div class="telem-value warn" id="t-oil">87</div><div class="telem-bar"><div class="telem-fill" id="b-oil" style="width:65%;background:linear-gradient(90deg,#ffe033,#ff6b00)"></div></div></div>
<div class="telem"><div class="telem-label">// Pression Huile (bar)</div><div class="telem-value" id="t-press">3.8</div><div class="telem-bar"><div class="telem-fill" id="b-press" style="width:76%"></div></div># index.htlm
