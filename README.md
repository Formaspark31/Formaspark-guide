[emails.html](https://github.com/user-attachments/files/26891125/emails.html)
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FormaSpark — Générateur d'emails</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&family=DM+Mono:wght@400;500&display=swap');
:root{
  --or:#E87722;--orl:#FDF0E4;--nv:#1A1A2E;--mid:#2C3E6B;
  --lt:#EEF2FA;--gr:#6B7280;--wh:#FFFFFF;
  --am:#B45309;--aml:#FFFBEB;--pu:#6D28D9;--pul:#F5F3FF;
  --gn:#16A34A;--gnl:#F0FDF4;--bd:#E5E7EB;--bg:#F4F6FB;--tx:#111827;
}
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--tx);min-height:100vh;}

header{background:var(--nv);height:52px;display:flex;align-items:center;padding:0 24px;border-bottom:2px solid var(--or);position:sticky;top:0;z-index:100;gap:12px;}
.logo{font-size:13px;font-weight:700;color:var(--or);letter-spacing:3px;}
.logo em{color:#5A6A90;font-style:normal;font-size:11px;letter-spacing:1px;margin-left:10px;}
.hstats{display:flex;gap:8px;margin-left:auto;}
.hp{background:rgba(255,255,255,.07);border:1px solid rgba(255,255,255,.1);padding:3px 9px;border-radius:20px;font-size:10px;color:#8896B0;font-weight:500;}
.hp b{color:var(--or);}

.app{display:grid;grid-template-columns:280px 1fr;min-height:calc(100vh - 52px);}

.sb{background:white;border-right:1px solid var(--bd);padding:16px 13px;overflow-y:auto;max-height:calc(100vh - 52px);position:sticky;top:52px;}
.sl{font-size:9.5px;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--gr);margin-bottom:7px;padding-left:2px;}
.ss{margin-bottom:16px;}

/* Profil buttons */
.pb{width:100%;text-align:left;padding:10px 12px;border-radius:8px;border:1.5px solid var(--bd);background:white;cursor:pointer;margin-bottom:4px;transition:all .14s;display:flex;align-items:flex-start;gap:10px;}
.pb:hover,.pb.active{border-color:var(--or);background:var(--orl);}
.pc{width:28px;height:28px;background:var(--nv);color:var(--or);border-radius:6px;font-size:11px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;font-family:'DM Mono',monospace;margin-top:1px;}
.pb.active .pc{background:var(--or);color:white;}
.pi{flex:1;}
.pn{font-size:12.5px;font-weight:600;color:var(--nv);line-height:1.3;}
.ps{font-size:10.5px;color:var(--gr);margin-top:2px;line-height:1.4;}

/* Email type */
.eb{width:100%;text-align:left;padding:8px 11px;border-radius:7px;border:1.5px solid transparent;background:white;cursor:pointer;margin-bottom:4px;transition:all .14s;display:flex;align-items:center;gap:7px;font-size:12px;font-weight:500;font-family:'DM Sans',sans-serif;}
.dt{width:7px;height:7px;border-radius:50%;flex-shrink:0;}
.e1{color:var(--or);}.e1:hover,.e1.active{border-color:var(--or);background:var(--orl);}.e1 .dt{background:var(--or);}
.e2{color:var(--am);}.e2:hover,.e2.active{border-color:var(--am);background:var(--aml);}.e2 .dt{background:var(--am);}
.e3{color:var(--pu);}.e3:hover,.e3.active{border-color:var(--pu);background:var(--pul);}.e3 .dt{background:var(--pu);}

/* Fields */
.fi{margin-bottom:10px;}
.fi label{display:block;font-size:11px;font-weight:600;color:var(--mid);margin-bottom:3px;}
.fi input{width:100%;padding:7px 10px;border:1.5px solid var(--bd);border-radius:7px;font-size:12px;font-family:'DM Sans',sans-serif;background:var(--bg);transition:border-color .13s;outline:none;}
.fi input:focus{border-color:var(--or);background:white;}
.fi input::placeholder{color:#B0B8C5;}

/* Main */
.main{padding:22px 26px;overflow-y:auto;max-height:calc(100vh - 52px);}
.wlc{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:400px;text-align:center;color:var(--gr);}
.wic{width:56px;height:56px;background:var(--orl);border-radius:13px;display:flex;align-items:center;justify-content:center;font-size:24px;margin-bottom:16px;}
.wlc h2{font-size:17px;font-weight:600;color:var(--nv);margin-bottom:5px;}
.wlc p{font-size:13px;max-width:280px;line-height:1.6;}

/* Card */
.card{background:white;border-radius:12px;border:1px solid var(--bd);overflow:hidden;box-shadow:0 1px 4px rgba(0,0,0,.06);}
.ctop{padding:12px 16px;border-bottom:1px solid var(--bd);display:flex;align-items:center;gap:9px;flex-wrap:wrap;}
.etag{display:inline-flex;align-items:center;gap:5px;padding:3px 9px;border-radius:20px;font-size:10px;font-weight:700;letter-spacing:.5px;text-transform:uppercase;}
.t1{background:var(--orl);color:var(--or);}
.t2{background:var(--aml);color:var(--am);}
.t3{background:var(--pul);color:var(--pu);}
.sbdg{font-size:10.5px;font-weight:600;padding:3px 9px;border-radius:12px;}
.sok{background:var(--gnl);color:var(--gn);}
.swn{background:var(--aml);color:var(--am);}
.cbtn{margin-left:auto;padding:7px 14px;background:var(--nv);color:white;border:none;border-radius:7px;font-size:12px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;transition:all .13s;display:flex;align-items:center;gap:5px;}
.cbtn:hover{background:var(--mid);}
.cbtn.cp{background:var(--gn);}

.obar{padding:11px 16px;border-bottom:1px solid var(--bd);background:var(--bg);}
.olbl{font-size:9px;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--gr);margin-bottom:3px;}
.oval{font-size:15px;font-weight:700;color:var(--nv);line-height:1.3;}

.cz{padding:16px 18px;}
.ctx{font-size:13.5px;line-height:1.9;color:var(--tx);white-space:pre-wrap;}
.hi{background:#FEF9C3;border-radius:3px;padding:0 3px;color:#92400E;font-weight:600;}

.sz{padding:13px 16px;border-top:1px solid var(--bd);background:var(--bg);font-size:11px;color:var(--gr);line-height:1.8;}
.sz strong{color:var(--mid);font-weight:600;}

.cs{margin-top:12px;padding:13px 15px;background:var(--orl);border-radius:9px;border-left:3px solid var(--or);}
.cst{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:1px;color:var(--or);margin-bottom:4px;}
.csb{font-size:12.5px;color:var(--tx);line-height:1.6;}

.toast{position:fixed;bottom:20px;left:50%;transform:translateX(-50%) translateY(70px);background:var(--nv);color:white;padding:8px 18px;border-radius:20px;font-size:12px;font-weight:600;z-index:999;transition:transform .28s cubic-bezier(.34,1.56,.64,1);pointer-events:none;}
.toast.show{transform:translateX(-50%) translateY(0);}
</style>
</head>
<body>

<header>
  <div class="logo">FORMASPARK <em>Générateur d'emails prospection</em></div>
  <div class="hstats">
    <div class="hp"><b>98%</b> satisfaction</div>
    <div class="hp"><b>94%</b> réussite</div>
    <div class="hp">Qualiopi · OPCO</div>
  </div>
</header>

<div class="app">
  <div class="sb">
    <div class="ss"><div class="sl">Profil du contact</div><div id="pl"></div></div>
    <div class="ss" id="es" style="display:none">
      <div class="sl">Type d'email</div>
      <div id="el"></div>
    </div>
    <div class="ss" id="fs" style="display:none">
      <div class="sl">Personnalisation</div>
      <div class="fi"><label>Prénom</label><input id="fp" type="text" placeholder="ex : Sophie" oninput="render()"></div>
      <div class="fi"><label>Entreprise</label><input id="fe" type="text" placeholder="ex : Acme Industries" oninput="render()"></div>
    </div>
  </div>

  <div class="main" id="main">
    <div class="wlc">
      <div class="wic">✉</div>
      <h2>Choisissez un profil</h2>
      <p>Sélectionnez le profil de votre contact dans le panneau gauche pour générer l'email.</p>
    </div>
  </div>
</div>

<div class="toast" id="toast">✓ Copié dans le presse-papiers</div>

<script>
const SIG = `FormaSpark — Organisme certifié Qualiopi
98% de satisfaction · 94% de réussite
Habilitations élec. · SST · AIPR · Travail en hauteur
formation@formaspark.fr · formaspark.fr · Toulouse — National
──
Pour ne plus recevoir nos emails, répondez STOP.`;

const SIG_FERRO = `FormaSpark — Organisme certifié Qualiopi
Mandaté par Alstom — Sous-systèmes ferroviaires
98% de satisfaction · 94% de réussite
formation@formaspark.fr · formaspark.fr
──
Pour ne plus recevoir nos emails, répondez STOP.`;

const P = [

  // ── PROFIL 1 ──────────────────────────────────────────────────────────────
  {
    code:"01", nom:"Responsable HSE / QSE / QHSE",
    sub:"Préventeur · Animateur sécurité · Ingénieur HSE",
    sig: SIG,
    conseil:"Le HSE est votre interlocuteur idéal : il a le budget, le besoin et le pouvoir de décision. L'email 1 lui parle de son quotidien — pas de vos formations. On lui vend du temps libéré et de la sérénité, pas un catalogue. La question finale est volontairement courte et fermée : oui ou non, il répond en 5 secondes. L'email 3 'Je ferme le dossier' reste le plus puissant — il génère des réponses tardives de contacts qui n'avaient pas répondu aux deux premiers.",
    emails:[
      { tag:"Email 1 — Premier contact", cls:"e1", tcls:"t1",
        objet:"[Entreprise] — une question pour vous, [Prénom]",
        corps:`Bonjour [Prénom],

Votre rôle, c'est de garder vos équipes terrain opérationnelles, conformes et sereines — sans que la gestion administrative de la formation vous prenne un temps précieux.

C'est exactement ce que nous faisons chez FormaSpark.
Nous intervenons directement chez vous, sur vos équipements, avec un seul interlocuteur du premier échange jusqu'au dossier OPCO.
98% de satisfaction · 94% de réussite · Qualiopi.

Est-ce que vous avez des besoins ouverts sur votre plan de formation cette année ?`
      },
      { tag:"Email 2 — Relance J+7", cls:"e2", tcls:"t2",
        objet:"Re : [Entreprise]",
        corps:`Bonjour [Prénom],

Je reviens vers vous en toute simplicité.

Avez-vous des sessions de formation à planifier pour vos équipes terrain dans les prochains mois ?

Oui → on échange 15 minutes, je vous propose quelque chose d'adapté.
Non → je ne vous recontacte pas avant votre prochain cycle.`
      },
      { tag:"Email 3 — Rupture J+14", cls:"e3", tcls:"t3",
        objet:"Je ferme le dossier [Entreprise]",
        corps:`Bonjour [Prénom],

Sans retour de votre part, je ferme le dossier — pas de relance supplémentaire.

Si vos besoins évoluent, nous restons disponibles :
formation@formaspark.fr — réactifs, un seul interlocuteur, 94% de réussite.`
      }
    ]
  },

  // ── PROFIL 2 ──────────────────────────────────────────────────────────────
  {
    code:"02", nom:"Responsable RH / Formation / DRH",
    sub:"Chargé de formation · RRH · Responsable développement RH",
    sig: SIG,
    conseil:"Le RH veut un prestataire qui lui simplifie la vie — pas un de plus à gérer. L'email 1 lui vend du temps libéré et un plan de formation qui tient. L'objet sur le budget OPCO est particulièrement efficace en Q3/Q4 quand les budgets non consommés remontent. Proposez toujours un échange de 15 minutes — jamais une décision directe. Le RH valide, c'est rarement lui qui décide seul.",
    emails:[
      { tag:"Email 1 — Premier contact", cls:"e1", tcls:"t1",
        objet:"[Entreprise] — simplifier votre plan de formation, ça vous parle ?",
        corps:`Bonjour [Prénom],

Un prestataire unique, réactif, qui intervient en intra chez vous et livre le dossier OPCO clé en main — c'est du temps libéré sur votre agenda et un plan de formation qui tient ses engagements.

Chez FormaSpark, c'est exactement notre promesse.
98% de satisfaction · 94% de réussite · Qualiopi · interventions nationales.

Votre budget OPCO est mobilisé pour cette période, ou il reste des créneaux à optimiser ?`
      },
      { tag:"Email 2 — Relance J+7", cls:"e2", tcls:"t2",
        objet:"Re : plan de formation [Entreprise]",
        corps:`Bonjour [Prénom],

Je reviens brièvement.

Votre budget OPCO est-il utilisé cette année ?

Si des créneaux sont encore disponibles, nous pouvons intervenir rapidement — dossier complet, 94% de réussite, zéro déplacement pour vos équipes.`
      },
      { tag:"Email 3 — Rupture J+14", cls:"e3", tcls:"t3",
        objet:"Je ferme le dossier — [Entreprise]",
        corps:`Bonjour [Prénom],

Sans retour de votre part, je ne relancerai plus.

Si votre plan de formation évolue :
formation@formaspark.fr — un seul prestataire, dossier OPCO inclus, 94% de réussite.`
      }
    ]
  },

  // ── PROFIL 3 ──────────────────────────────────────────────────────────────
  {
    code:"03", nom:"Directeur / Gérant / CEO",
    sub:"DG · PDG · Président · Dirigeant · Direction générale",
    sig: SIG,
    conseil:"Le dirigeant scanne — il ne lit pas. 5 lignes maximum. On lui vend une entreprise qui avance sans friction, pas une liste de formations. L'accroche joue sur la performance et la sérénité, pas sur le risque. La relance J+7 est bienveillante et ouvre une porte sans pression. Proposez toujours 15 minutes d'échange — jamais une décision directe dans l'email. Ne jamais faire ça avec un HSE — mais avec un CEO qui délègue ce sujet, c'est redoutable.",
    emails:[
      { tag:"Email 1 — Premier contact", cls:"e1", tcls:"t1",
        objet:"[Entreprise] — vos équipes terrain, notre expertise",
        corps:`Bonjour [Prénom],

Les entreprises qui performent ont un point commun : des équipes terrain formées, certifiées, opérationnelles — sans que ça mobilise leur direction.

Chez FormaSpark, on prend ce sujet en charge de A à Z.
On intervient en intra chez vous, un seul interlocuteur, dossier OPCO clé en main.
98% de satisfaction · 94% de réussite · Qualiopi.

C'est un sujet sur lequel vous souhaitez gagner en sérénité chez [Entreprise] ?`
      },
      { tag:"Email 2 — Relance J+7", cls:"e2", tcls:"t2",
        objet:"Re : [Entreprise]",
        corps:`Bonjour [Prénom],

Je reviens en toute simplicité.

Est-ce que la formation de vos équipes terrain est un sujet que vous souhaitez structurer ou déléguer à un partenaire fiable ?

Si oui, 15 minutes suffisent pour voir si on peut vous apporter quelque chose de concret.`
      },
      { tag:"Email 3 — Rupture J+14", cls:"e3", tcls:"t3",
        objet:"Dernier message — [Entreprise]",
        corps:`Bonjour [Prénom],

Je ne relancerai plus — je respecte votre temps.

Si le sujet de la formation de vos équipes terrain évolue :
formation@formaspark.fr — réactif, fiable, 94% de réussite.`
      }
    ]
  },

  // ── PROFIL 4 ──────────────────────────────────────────────────────────────
  {
    code:"04", nom:"Responsable maintenance / Technique",
    sub:"Directeur technique · Responsable production · Chef d'atelier",
    sig: SIG,
    conseil:"Le responsable maintenance pense efficacité opérationnelle. L'accroche joue sur la performance immédiate : une formation sur les équipements réels = des techniciens opérationnels le lendemain. C'est son langage. Ne parlez jamais de réglementation avec ce profil — parlez de temps gagné, d'efficacité, de techniciens qui montent en compétences sur leur vrai environnement.",
    emails:[
      { tag:"Email 1 — Premier contact", cls:"e1", tcls:"t1",
        objet:"[Entreprise] — des techniciens pleinement opérationnels sur le terrain",
        corps:`Bonjour [Prénom],

Des techniciens formés sur leurs équipements réels, c'est une montée en compétences immédiatement opérationnelle — et des interventions qui gagnent en efficacité dès le lendemain de la formation.

FormaSpark vient en intra chez vous, sur vos installations.
Vos équipes ne se déplacent pas, la formation s'adapte entièrement à votre environnement.
94% de réussite · Qualiopi · OPCO.

Vous avez des formations ou mises à niveau à planifier chez [Entreprise] ?`
      },
      { tag:"Email 2 — Relance J+7", cls:"e2", tcls:"t2",
        objet:"Re : [Entreprise]",
        corps:`Bonjour [Prénom],

Je reviens brièvement.

Avez-vous des formations ou renouvellements à planifier pour vos techniciens dans les prochains mois ?

Si oui, on peut intervenir en intra sous 2 semaines, directement sur vos installations.`
      },
      { tag:"Email 3 — Rupture J+14", cls:"e3", tcls:"t3",
        objet:"Je retire [Entreprise] de mes relances",
        corps:`Bonjour [Prénom],

Aucun retour — je ne relancerai plus.

Si des formations pour vos techniciens se présentent :
formation@formaspark.fr — intra sur vos équipements, 94% de réussite.`
      }
    ]
  },

  // ── PROFIL 5 ──────────────────────────────────────────────────────────────
  {
    code:"05", nom:"Conducteur de travaux / Chef de chantier",
    sub:"Directeur travaux · Gérant PME BTP · Chef de chantier",
    sig: SIG,
    conseil:"Ce profil lit ses emails sur mobile entre deux chantiers. 5 lignes maximum — pas une de plus. L'argument n°1 est le déplacement sur site : on vient chez eux, ils ne bougent pas. Mettez-le en ligne 2. Court, direct, une seule question fermée. La réactivité est clé pour ce profil — mentionnez toujours que vous pouvez intervenir rapidement.",
    emails:[
      { tag:"Email 1 — Premier contact", cls:"e1", tcls:"t1",
        objet:"[Entreprise] — on vient former vos équipes directement sur vos chantiers",
        corps:`Bonjour [Prénom],

Des équipes certifiées et à jour sur vos chantiers, c'est une organisation qui avance sans friction — et des plannings tenus.

FormaSpark se déplace directement sur vos sites ou dans vos locaux.
Tous les niveaux certifiés en une seule journée, zéro déplacement pour vos équipes.
98% de satisfaction · Qualiopi · OPCO.

Vous avez des renouvellements à prévoir chez [Entreprise] dans les prochains mois ?`
      },
      { tag:"Email 2 — Relance J+7", cls:"e2", tcls:"t2",
        objet:"Re : [Entreprise]",
        corps:`Bonjour [Prénom],

Des formations ou certifications à planifier pour vos équipes chantier prochainement ?

On vient sur vos sites, tous les niveaux en une journée, dossier OPCO prêt.
Oui ou non suffit.`
      },
      { tag:"Email 3 — Rupture J+14", cls:"e3", tcls:"t3",
        objet:"Je ferme le dossier — [Entreprise]",
        corps:`Bonjour [Prénom],

Je ne relancerai plus.

Quand des formations arrivent pour vos équipes :
formation@formaspark.fr — déplacement sur vos chantiers, 98% de satisfaction, OPCO.`
      }
    ]
  },

  // ── PROFIL 6 ──────────────────────────────────────────────────────────────
  {
    code:"06", nom:"Secteur ferroviaire",
    sub:"Opérateurs réseau · ETF · Maintenance sous-systèmes · RH ferro",
    sig: SIG_FERRO,
    conseil:"Le mandat Alstom est votre seul vrai différenciateur dans ce secteur — personne ne peut le revendiquer à votre place. Il va dans l'objet et dans le 1er paragraphe. La stratégie ferroviaire est de rentrer par le sous-système (crédibilité Alstom acquise) et d'ouvrir sur les habilitations RFN comme extension naturelle. Ne les présentez jamais comme deux offres séparées. L'email 1A pour les entreprises déjà en contact via Alstom a un taux de réponse bien supérieur — utilisez-le en priorité.",
    emails:[
      { tag:"Email 1 — Premier contact", cls:"e1", tcls:"t1",
        objet:"FormaSpark × Alstom — un partenaire formation pour [Entreprise]",
        corps:`Bonjour [Prénom],

FormaSpark est mandaté par Alstom pour les formations sous-systèmes ferroviaires. Nous intervenons directement auprès de leurs clients et partenaires sur l'ensemble du réseau.

Notre engagement : réactivité, adaptation totale à vos référentiels, zéro déplacement pour vos équipes.
94% de réussite · Qualiopi · OPCO.

Les formations de vos équipes ferroviaires sont planifiées pour cette période, ou c'est un sujet ouvert chez [Entreprise] ?`
      },
      { tag:"Email 2 — Relance J+7", cls:"e2", tcls:"t2",
        objet:"Re : formations ferroviaires [Entreprise]",
        corps:`Bonjour [Prénom],

Vos habilitations RFN et formations sécurité sont planifiées pour les prochains mois ?

Oui → je reviens au moment du renouvellement.
Non → on intervient en intra sous 2 semaines, mandat Alstom, 94% de réussite.`
      },
      { tag:"Email 3 — Rupture J+14", cls:"e3", tcls:"t3",
        objet:"Dernier message — [Entreprise]",
        corps:`Bonjour [Prénom],

Je ferme le dossier — pas de relance supplémentaire.

Quand un renouvellement RFN ou une formation sous-système se présente :
formation@formaspark.fr — mandat Alstom, 94% de réussite, délai 2 semaines.`
      }
    ]
  },

  // ── PROFIL 7 ──────────────────────────────────────────────────────────────
  {
    code:"07", nom:"Email générique — Adresse non nominative",
    sub:"contact@ · rh@ · securite@ · formation@ · info@",
    sig: SIG,
    conseil:"Sur une adresse générique, ne pitchez jamais directement — vous ne savez pas qui va lire. L'objectif unique de cet email est d'être redirigé vers le bon interlocuteur. Restez très court, très neutre, et posez une question de redirection. C'est contre-intuitif mais ça convertit mieux qu'un email complet envoyé dans le vide. Une fois que vous avez le bon contact, passez sur le profil adapté.",
    emails:[
      { tag:"Email 1 — Premier contact", cls:"e1", tcls:"t1",
        objet:"Formations [Entreprise] — à qui m'adresser ?",
        corps:`Bonjour,

FormaSpark accompagne les entreprises dans la formation de leurs équipes terrain — en intra, directement sur vos sites.
98% de satisfaction · 94% de réussite · Qualiopi · OPCO.

Pourriez-vous m'indiquer qui est en charge des formations chez [Entreprise] ?`
      },
      { tag:"Email 2 — Relance J+7", cls:"e2", tcls:"t2",
        objet:"Re : formations [Entreprise]",
        corps:`Bonjour,

Je reviens suite à mon message de la semaine dernière.

Pourriez-vous m'indiquer le bon contact pour les formations réglementaires de vos équipes terrain ?
Je ne prendrai que quelques minutes à la personne concernée.`
      },
      { tag:"Email 3 — Rupture J+14", cls:"e3", tcls:"t3",
        objet:"Dernier message — FormaSpark / [Entreprise]",
        corps:`Bonjour,

Je ne relancerai plus sur cette adresse.

Si un responsable formation ou HSE de [Entreprise] souhaite échanger sur les formations réglementaires de vos équipes :
formation@formaspark.fr`
      }
    ]
  }

];

// ─── STATE ───────────────────────────────────────────────────────────────────
let S={pi:null,ei:null};

function init(){
  document.getElementById('pl').innerHTML=P.map((p,i)=>`
    <button class="pb ${S.pi===i?'active':''}" onclick="selP(${i})">
      <div class="pc">${p.code}</div>
      <div class="pi"><div class="pn">${p.nom}</div><div class="ps">${p.sub}</div></div>
    </button>`).join('');
}

function selP(i){
  S.pi=i; S.ei=null;
  init();
  document.getElementById('es').style.display='block';
  document.getElementById('fs').style.display='block';
  renderE();
  render();
}

function renderE(){
  if(S.pi===null)return;
  const cls=['e1','e2','e3'];
  document.getElementById('el').innerHTML=P[S.pi].emails.map((e,i)=>`
    <button class="eb ${cls[i]} ${S.ei===i?'active':''}" onclick="selE(${i})">
      <span class="dt"></span>${e.tag}
    </button>`).join('');
}

function selE(i){ S.ei=i; renderE(); render(); }

function pers(t){
  const pr=document.getElementById('fp').value.trim();
  const en=document.getElementById('fe').value.trim();
  if(pr) t=t.replace(/\[Prénom\]/g,pr);
  if(en) t=t.replace(/\[Entreprise\]/g,en);
  return t;
}

function hl(t){
  return t
    .replace(/\[Prénom\]/g,'<span class="hi">[Prénom]</span>')
    .replace(/\[Entreprise\]/g,'<span class="hi">[Entreprise]</span>');
}

function render(){
  const m=document.getElementById('main');
  if(S.pi===null){
    m.innerHTML='<div class="wlc"><div class="wic">✉</div><h2>Choisissez un profil</h2><p>Sélectionnez le profil de votre contact dans le panneau gauche.</p></div>';
    return;
  }
  const p=P[S.pi];
  if(S.ei===null){
    m.innerHTML=`<div class="wlc"><div class="wic" style="background:var(--lt)">📧</div><h2>${p.nom}</h2><p>Choisissez le type d'email dans le panneau gauche.</p></div>`;
    return;
  }
  const e=p.emails[S.ei];
  const obj=pers(e.objet);
  const corps=pers(e.corps);
  const hasV=corps.includes('[Prénom]')||corps.includes('[Entreprise]')||obj.includes('[Prénom]')||obj.includes('[Entreprise]');

  m.innerHTML=`
    <div class="card">
      <div class="ctop">
        <span class="etag ${e.tcls}">${e.tag}</span>
        <span class="sbdg ${hasV?'swn':'sok'}">${hasV?'⚠ Variables à remplir':'✓ Prêt à envoyer'}</span>
        <button class="cbtn" id="cb" onclick="doCopy()">
          <svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"/></svg>
          Copier l'email
        </button>
      </div>
      <div class="obar">
        <div class="olbl">Objet</div>
        <div class="oval">${hl(obj)}</div>
      </div>
      <div class="cz">
        <div class="ctx">${hl(corps)}</div>
      </div>
      <div class="sz">
        ${p.sig.split('\n').map((l,i)=>{
          if(i===0) return `<strong>${l}</strong>`;
          if(l==='──') return `<span style="color:var(--bd)">──</span>`;
          if(l.includes('STOP')) return `<span style="color:#C0C8D8;font-size:10px;font-style:italic">${l}</span>`;
          return l;
        }).join('<br>')}
      </div>
    </div>
    <div class="cs">
      <div class="cst">💡 Pourquoi ça marche</div>
      <div class="csb">${p.conseil}</div>
    </div>`;

  window._cp=`OBJET : ${obj}\n\n${corps}\n\n──\n${p.sig}`;
}

function doCopy(){
  if(!window._cp)return;
  navigator.clipboard.writeText(window._cp).then(()=>{
    const b=document.getElementById('cb');
    if(b){b.classList.add('cp');b.innerHTML='✓ Copié !';}
    const t=document.getElementById('toast');
    t.classList.add('show');
    setTimeout(()=>{
      t.classList.remove('show');
      if(b){b.classList.remove('cp');b.innerHTML='<svg width="12" height="12" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 01-2-2V4a2 2 0 012-2h9a2 2 0 012 2v1"/></svg> Copier l\'email';}
    },2200);
  });
}

init();
</script>
</body>
</html>
