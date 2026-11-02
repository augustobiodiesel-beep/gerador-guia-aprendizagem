[index.html](https://github.com/user-attachments/files/34288850/index.html)
<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#1E5E4A">
<title>Caderno de Prompts</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Literata:ital,opsz,wght@0,7..72,400;0,7..72,600;0,7..72,700;1,7..72,400&family=Public+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap">
<style>
/* ============================================================
   Caderno de Prompts — sistema de tokens
   ============================================================ */
:root{
  --paper:#F6F7F4; --surface:#FFFFFF; --surface-2:#EDF0EA;
  --ink:#16211D; --ink-2:#42504A; --muted:#6F7C75;
  --line:#DCE2DA; --line-strong:#C6CFC4;
  --accent:#1E5E4A; --accent-hover:#174C3C; --accent-soft:#E3EFE8; --on-accent:#F6F7F4;
  --mark:#9C5D1C; --mark-soft:#F6ECDF;
  --shadow:0 1px 2px rgba(22,33,29,.06), 0 8px 24px -16px rgba(22,33,29,.35);
  --radius:10px; --radius-sm:6px; --sidebar:300px;
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --paper:#101411; --surface:#171D19; --surface-2:#1F2621;
    --ink:#E7EBE5; --ink-2:#B7C1B9; --muted:#8A968E;
    --line:#28302A; --line-strong:#3A443D;
    --accent:#7FC8A6; --accent-hover:#96D6B8; --accent-soft:#1A2721; --on-accent:#0C1310;
    --mark:#D8A263; --mark-soft:#2A2118;
    --shadow:0 1px 2px rgba(0,0,0,.4), 0 8px 24px -16px rgba(0,0,0,.8);
  }
}
:root[data-theme="dark"]{
  --paper:#101411; --surface:#171D19; --surface-2:#1F2621;
  --ink:#E7EBE5; --ink-2:#B7C1B9; --muted:#8A968E;
  --line:#28302A; --line-strong:#3A443D;
  --accent:#7FC8A6; --accent-hover:#96D6B8; --accent-soft:#1A2721; --on-accent:#0C1310;
  --mark:#D8A263; --mark-soft:#2A2118;
  --shadow:0 1px 2px rgba(0,0,0,.4), 0 8px 24px -16px rgba(0,0,0,.8);
}

*,*::before,*::after{box-sizing:border-box}
html{-webkit-text-size-adjust:100%}
body{margin:0;background:var(--paper);color:var(--ink);
  font-family:"Public Sans","Segoe UI",system-ui,-apple-system,sans-serif;font-size:15px;line-height:1.55}
h1,h2,h3{font-family:Literata,Georgia,"Times New Roman",serif;font-weight:600;text-wrap:balance;margin:0}
p{margin:0}
button,input,select,textarea{font:inherit;color:inherit}
a{color:var(--accent);text-underline-offset:3px}
:focus-visible{outline:2px solid var(--accent);outline-offset:2px;border-radius:4px}
@media (prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}

.app{display:grid;grid-template-columns:var(--sidebar) minmax(0,1fr);min-height:100vh}

/* ---------- barra lateral ---------- */
.side{background:var(--surface);border-right:1px solid var(--line);
  display:flex;flex-direction:column;position:sticky;top:0;height:100vh;overflow:hidden}
.brand{display:flex;align-items:center;gap:10px;padding:20px 20px 15px}
.brand-mark{width:34px;height:34px;flex:none;border-radius:8px;background:var(--accent);color:var(--on-accent);
  display:grid;place-items:center;font-family:Literata,serif;font-weight:700;font-size:17px;line-height:1}
.brand-name{font-family:Literata,serif;font-weight:700;font-size:16.5px;letter-spacing:-.01em;line-height:1.15}
.brand-sub{font-size:11.5px;color:var(--muted);letter-spacing:.06em;text-transform:uppercase}
.busca-wrap{padding:0 16px 13px;border-bottom:1px solid var(--line)}
.busca{width:100%;background:var(--paper);border:1px solid var(--line-strong);
  border-radius:var(--radius-sm);padding:7px 10px;font-size:13.5px}
.busca:focus{outline:none;border-color:var(--accent);box-shadow:0 0 0 3px var(--accent-soft)}
.busca::placeholder{color:var(--muted)}
.nav{padding:13px 12px 24px;display:flex;flex-direction:column;gap:15px;flex:1;overflow-y:auto}
.nav-group{display:flex;flex-direction:column;gap:1px}
.nav-label{display:flex;align-items:center;gap:7px;font-size:10.5px;letter-spacing:.13em;text-transform:uppercase;
  color:var(--mark);font-weight:600;padding:0 10px 5px}
.nav-label svg{width:13px;height:13px;flex:none}
.nav-label .n{margin-left:auto;font-family:"IBM Plex Mono",monospace;font-size:10px;color:var(--muted);letter-spacing:0}
.nav-item{display:flex;align-items:center;gap:8px;width:100%;text-align:left;background:none;border:0;cursor:pointer;
  padding:5px 10px;border-radius:var(--radius-sm);color:var(--ink-2);font-size:13.6px;line-height:1.35;
  transition:background .12s ease,color .12s ease}
.nav-item:hover{background:var(--surface-2);color:var(--ink)}
.nav-item[aria-current="true"]{background:var(--accent-soft);color:var(--accent);font-weight:600}
.nav-item .dot{width:5px;height:5px;border-radius:50%;flex:none;background:var(--mark);opacity:.8}
.nav-item .dot.novo{background:transparent;border:1px solid var(--line-strong)}
.nav-item .dot.guia{background:var(--accent);opacity:1}
.vazio{padding:8px 10px;font-size:13px;color:var(--muted)}
.side-foot{border-top:1px solid var(--line);padding:12px 20px 16px;font-size:11.5px;line-height:1.5;color:var(--muted)}
.side-foot a{color:var(--muted);text-decoration:underline}
.side-foot a:hover{color:var(--accent)}
.side-foot strong{color:var(--ink-2);font-weight:600}

/* ---------- topo (celular) ---------- */
.topbar{display:none}
.hamb{display:inline-flex;align-items:center;gap:8px;background:var(--surface);border:1px solid var(--line);
  color:var(--ink);padding:8px 12px;border-radius:var(--radius-sm);cursor:pointer;font-size:14px;font-weight:500}
.scrim{display:none}

/* ---------- área principal ---------- */
.main{padding:36px 40px 64px;min-width:0}
.wrap{max-width:1180px;margin:0 auto}
.page-head{margin-bottom:24px;max-width:64ch}
.eyebrow{display:flex;align-items:center;gap:10px;flex-wrap:wrap;margin-bottom:9px}
.eyebrow .grp{font-size:11px;letter-spacing:.13em;text-transform:uppercase;color:var(--mark);font-weight:600}
.selo{font-size:10.5px;letter-spacing:.04em;padding:2px 7px;border-radius:999px;border:1px solid var(--line-strong);color:var(--muted)}
.selo.modelo{background:var(--mark-soft);border-color:transparent;color:var(--mark);font-weight:600}
.page-head h1{font-size:clamp(25px,3.2vw,32px);letter-spacing:-.015em;line-height:1.18}
.page-head p{color:var(--ink-2);margin-top:9px;font-size:15.5px}

.cols{display:grid;grid-template-columns:minmax(0,1.02fr) minmax(0,1fr);gap:28px;align-items:start}
@media (max-width:1080px){.cols{grid-template-columns:minmax(0,1fr)}}

.card{background:var(--surface);border:1px solid var(--line);border-radius:var(--radius);box-shadow:var(--shadow)}
.card-head{padding:13px 18px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;gap:12px}
.card-title{font-size:11px;letter-spacing:.13em;text-transform:uppercase;color:var(--muted);font-weight:600}
.card-body{padding:18px}

.fields{display:flex;flex-direction:column;gap:15px}
.field{display:flex;flex-direction:column;gap:5px}
.field label{font-size:13px;font-weight:600;color:var(--ink-2)}
.field .hint{font-size:12px;color:var(--muted);font-weight:400;line-height:1.4}
.field input,.field select,.field textarea{width:100%;background:var(--paper);border:1px solid var(--line-strong);
  border-radius:var(--radius-sm);padding:9px 11px;color:var(--ink);transition:border-color .12s ease,box-shadow .12s ease}
.field textarea{min-height:86px;resize:vertical;line-height:1.5}
.field textarea.grande{min-height:170px}
.field input:focus,.field select:focus,.field textarea:focus{outline:none;border-color:var(--accent);box-shadow:0 0 0 3px var(--accent-soft)}
.field input::placeholder,.field textarea::placeholder{color:var(--muted);opacity:.85}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:15px}
@media (max-width:560px){.row2{grid-template-columns:1fr}}

.out-card{position:sticky;top:24px}
.out{font-family:"IBM Plex Mono",ui-monospace,SFMono-Regular,Menlo,monospace;font-size:12.8px;line-height:1.62;
  white-space:pre-wrap;word-break:break-word;margin:0;padding:18px;max-height:min(52vh,560px);overflow:auto;color:var(--ink)}
.btn{display:inline-flex;align-items:center;gap:7px;border-radius:var(--radius-sm);cursor:pointer;padding:7px 13px;
  font-size:13px;font-weight:600;border:1px solid var(--line-strong);background:var(--surface-2);color:var(--ink);
  transition:background .12s ease,border-color .12s ease,color .12s ease}
.btn:hover{border-color:var(--accent);color:var(--accent)}
.btn-primary{background:var(--accent);border-color:var(--accent);color:var(--on-accent)}
.btn-primary:hover{background:var(--accent-hover);border-color:var(--accent-hover);color:var(--on-accent)}
.btn svg{width:14px;height:14px;flex:none}
.actions{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.counter{font-size:11.5px;color:var(--muted);font-variant-numeric:tabular-nums}

/* ---------- botões de IA ---------- */
.ias{border-top:1px solid var(--line);padding:15px 18px 17px}
.ias-tit{font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:var(--mark);font-weight:600;margin-bottom:10px}
.ias-lista{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:8px}
.ia{display:flex;align-items:center;justify-content:center;gap:8px;cursor:pointer;text-decoration:none;
  background:var(--surface-2);border:1px solid var(--line-strong);border-radius:var(--radius-sm);
  padding:11px 12px;font-size:13.5px;font-weight:600;color:var(--ink);
  transition:border-color .12s ease,background .12s ease,transform .1s ease}
.ia:hover,.ia:focus-visible{border-color:var(--accent);background:var(--accent-soft);color:var(--accent);transform:translateY(-1px)}
.ia .mk{display:inline-flex;flex:none;color:var(--ia,var(--muted))}
.ia .mk svg{width:18px;height:18px;display:block}
.ia .ext{width:11px;height:11px;opacity:.4}
.ia:hover .ext{opacity:.9}
.ias-nota{font-size:11.5px;color:var(--muted);margin-top:10px;line-height:1.45}
.vazio-out{padding:26px 18px;color:var(--muted);font-size:13.8px;line-height:1.55;text-align:center}
.vazio-out b{display:block;color:var(--ink-2);font-weight:600;margin-bottom:3px}
.form-foot{padding:14px 18px;border-top:1px solid var(--line);display:flex;gap:8px;flex-wrap:wrap;align-items:center}
.btn-lg{padding:10px 18px;font-size:13.5px}

/* ---------- início ---------- */
.home{display:grid;grid-template-columns:minmax(0,1.35fr) minmax(0,1fr);gap:28px;align-items:start}
@media (max-width:1080px){.home{grid-template-columns:minmax(0,1fr)}}
.lede{font-size:17px;line-height:1.6;color:var(--ink-2);max-width:60ch}
.steps{list-style:none;margin:24px 0 0;padding:0;display:flex;flex-direction:column;gap:14px;counter-reset:s}
.steps li{display:flex;gap:14px;align-items:flex-start;counter-increment:s}
.steps li::before{content:counter(s,decimal-leading-zero);font-family:"IBM Plex Mono",monospace;font-size:12px;font-weight:500;
  color:var(--accent);background:var(--accent-soft);border-radius:var(--radius-sm);padding:4px 7px;line-height:1;flex:none;margin-top:2px}
.steps b{display:block;font-weight:600;color:var(--ink)}
.steps span{color:var(--ink-2);font-size:14px}
.catalogo{margin-top:28px;display:flex;flex-direction:column;gap:20px}
.cat-grupo h2{font-size:12.5px;letter-spacing:.11em;text-transform:uppercase;color:var(--mark);margin-bottom:9px;
  font-family:"Public Sans",sans-serif;font-weight:600}
.tiles{display:grid;grid-template-columns:1fr 1fr;gap:8px}
@media (max-width:620px){.tiles{grid-template-columns:1fr}}
.tile{text-align:left;cursor:pointer;background:var(--surface);border:1px solid var(--line);border-radius:var(--radius);
  padding:10px 13px;transition:border-color .12s ease,transform .12s ease}
.tile:hover{border-color:var(--accent);transform:translateY(-1px)}
.tile .t{display:flex;align-items:center;gap:7px;margin-bottom:2px}
.tile b{font-family:Literata,serif;font-size:14.3px;font-weight:600}
.tile .dot{width:5px;height:5px;border-radius:50%;flex:none;background:var(--mark)}
.tile .dot.novo{background:transparent;border:1px solid var(--line-strong)}
.tile .dot.guia{background:var(--accent)}
.tile span{font-size:12.3px;color:var(--muted);line-height:1.45;display:block}
.legenda{display:flex;gap:16px;flex-wrap:wrap;font-size:12px;color:var(--muted);margin-top:6px}
.legenda i{display:inline-block;width:6px;height:6px;border-radius:50%;background:var(--mark);margin-right:6px;vertical-align:middle;font-style:normal}
.legenda i.novo{background:transparent;border:1px solid var(--line-strong)}
.aside-note{font-size:13.5px;line-height:1.6;color:var(--ink-2)}
.aside-note p+p{margin-top:11px}
.aside-note .lic{display:inline-block;margin-top:4px;font-family:"IBM Plex Mono",monospace;font-size:11.5px;
  color:var(--mark);border:1px solid var(--line-strong);border-radius:var(--radius-sm);padding:3px 7px}

/* ---------- guias ---------- */
.guia{max-width:74ch;font-size:15px;line-height:1.65;color:var(--ink-2)}
.guia h2{font-size:19px;margin:30px 0 10px;color:var(--ink)}
.guia h2:first-child{margin-top:0}
.guia h3{font-size:15.5px;margin:20px 0 6px;color:var(--ink);font-family:"Public Sans",sans-serif;font-weight:600}
.guia p{margin:0 0 11px}
.guia ul,.guia ol{margin:0 0 14px;padding-left:22px}
.guia li{margin-bottom:6px}
.guia li::marker{color:var(--mark)}
.guia strong{color:var(--ink);font-weight:600}
.guia code{font-family:"IBM Plex Mono",monospace;font-size:12.6px;background:var(--surface-2);
  border-radius:4px;padding:1px 4px;word-break:break-word}
.guia .aviso{background:var(--mark-soft);border-left:3px solid var(--mark);border-radius:0 var(--radius-sm) var(--radius-sm) 0;
  padding:11px 14px;margin:0 0 16px;font-size:13.7px;color:var(--ink-2)}
.tab-wrap{overflow-x:auto;margin:0 0 18px;border:1px solid var(--line);border-radius:var(--radius);background:var(--surface)}
.guia table{border-collapse:collapse;width:100%;font-size:13.5px;min-width:520px}
.guia th{text-align:left;font-weight:600;color:var(--ink);background:var(--surface-2);padding:9px 13px;
  border-bottom:1px solid var(--line);font-size:12px;letter-spacing:.05em;text-transform:uppercase}
.guia td{padding:9px 13px;border-bottom:1px solid var(--line);vertical-align:top}
.guia tr:last-child td{border-bottom:0}
.passos{list-style:none;padding:0;margin:0 0 18px;counter-reset:pp;display:flex;flex-direction:column;gap:12px}
.passos li{counter-increment:pp;display:flex;gap:13px;align-items:flex-start}
.passos li::before{content:counter(pp);font-family:"IBM Plex Mono",monospace;font-size:12px;color:var(--on-accent);
  background:var(--accent);border-radius:50%;width:21px;height:21px;display:grid;place-items:center;flex:none;margin-top:2px}

.foot{margin-top:44px;padding-top:18px;border-top:1px solid var(--line);font-size:12.5px;color:var(--muted);line-height:1.6;max-width:82ch}
.foot a{color:var(--muted);text-decoration:underline}
.foot a:hover{color:var(--accent)}

/* ---------- BNCC de Computação ---------- */
.bncc{border-top:1px solid var(--line);padding:15px 18px 16px;background:var(--surface)}
.bncc-head{display:flex;align-items:center;justify-content:space-between;gap:10px;margin-bottom:10px}
.bncc-head .card-title{color:var(--mark)}
.bncc-cont{font-size:11.5px;color:var(--muted);font-variant-numeric:tabular-nums}
.bncc-ctrl{display:grid;grid-template-columns:minmax(0,1fr) minmax(0,1fr);gap:8px;margin-bottom:10px}
@media (max-width:560px){.bncc-ctrl{grid-template-columns:1fr}}
.bncc-ctrl select,.bncc-ctrl input{width:100%;background:var(--paper);border:1px solid var(--line-strong);
  border-radius:var(--radius-sm);padding:8px 10px;font-size:13px;color:var(--ink)}
.bncc-ctrl select:focus,.bncc-ctrl input:focus{outline:none;border-color:var(--accent);box-shadow:0 0 0 3px var(--accent-soft)}
.bncc-lista{max-height:260px;overflow-y:auto;border:1px solid var(--line);border-radius:var(--radius-sm);background:var(--paper)}
.bncc-eixo{font-size:10.5px;letter-spacing:.12em;text-transform:uppercase;color:var(--mark);font-weight:600;
  padding:9px 11px 5px;position:sticky;top:0;background:var(--paper)}
.bncc-item{display:flex;gap:9px;align-items:flex-start;padding:6px 11px;cursor:pointer;font-size:12.8px;line-height:1.45;color:var(--ink-2)}
.bncc-item:hover{background:var(--surface-2)}
.bncc-item input{margin:3px 0 0;flex:none;accent-color:var(--accent)}
.bncc-item code{font-family:"IBM Plex Mono",monospace;font-size:11.5px;color:var(--accent);font-weight:500}
.bncc-item.on{background:var(--accent-soft)}
.bncc-vazio{padding:16px 12px;font-size:12.8px;color:var(--muted);text-align:center}
.bncc-nota{font-size:11.5px;color:var(--muted);margin-top:9px;line-height:1.45}
.gb-item{border-bottom:1px solid var(--line);padding:10px 0}
.gb-item:last-child{border-bottom:0}
.gb-cod{font-family:"IBM Plex Mono",monospace;font-size:12px;color:var(--accent);font-weight:500}
.gb-eixo{font-size:11px;color:var(--mark);margin-left:8px}
.gb-item p{margin:3px 0 0;font-size:13.6px}
.gb-etapa{margin:26px 0 4px!important;color:var(--ink)}
.gb-eixo-tit{margin:12px 0 2px!important;font-size:12px;letter-spacing:.08em;text-transform:uppercase;color:var(--mark)}

@media (max-width:900px){
  .app{grid-template-columns:minmax(0,1fr)}
  .topbar{display:flex;align-items:center;gap:12px;padding:12px 16px;border-bottom:1px solid var(--line);
    background:var(--surface);position:sticky;top:0;z-index:30}
  .topbar .brand-name{font-size:15px}
  .side{position:fixed;z-index:50;top:0;left:0;width:min(88vw,var(--sidebar));transform:translateX(-102%);transition:transform .22s ease}
  .side.open{transform:translateX(0)}
  .scrim{display:block;position:fixed;inset:0;z-index:40;background:rgba(10,16,13,.45);opacity:0;pointer-events:none;transition:opacity .22s ease}
  .scrim.on{opacity:1;pointer-events:auto}
  .main{padding:24px 18px 56px}
  .out-card{position:static}
}
</style>
</head>
<body>
<div class="app">
  <aside class="side" id="side" aria-label="Geradores">
    <div class="brand">
      <div class="brand-mark" aria-hidden="true">CP</div>
      <div>
        <div class="brand-name">Caderno de Prompts</div>
        <div class="brand-sub">IA na sala de aula</div>
      </div>
    </div>
    <div class="busca-wrap">
      <input class="busca" id="busca" type="search" placeholder="Buscar gerador…" aria-label="Buscar gerador">
    </div>
    <nav class="nav" id="nav"></nav>
    <div class="side-foot">
      <strong>Baseado no modelo de Sérgio Araújo</strong><br>
      “Geradores de Prompts de IA para Professores”.<br>
      <a href="https://educ.nekoweb.org/geradores/home.html" target="_blank" rel="noopener">educ.nekoweb.org</a> ·
      <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt-br" target="_blank" rel="noopener">CC BY-NC-SA 4.0</a>
    </div>
  </aside>

  <div>
    <div class="topbar">
      <button class="hamb" id="hamb" aria-expanded="false" aria-controls="side">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" width="16" height="16"><path d="M3 6h18M3 12h18M3 18h18"/></svg>
        Geradores
      </button>
      <div class="brand-name">Caderno de Prompts</div>
    </div>
    <main class="main"><div class="wrap" id="view"></div></main>
  </div>
</div>
<div class="scrim" id="scrim"></div>

<datalist id="disciplinas">
  <option value="Língua Portuguesa"></option><option value="Literatura"></option><option value="Redação"></option>
  <option value="Matemática"></option><option value="História"></option><option value="Geografia"></option>
  <option value="Ciências"></option><option value="Biologia"></option><option value="Física"></option>
  <option value="Química"></option><option value="Artes"></option><option value="Educação Física"></option>
  <option value="Inglês"></option><option value="Espanhol"></option><option value="Filosofia"></option>
  <option value="Sociologia"></option><option value="Ensino Religioso"></option><option value="Projeto de Vida"></option>
  <option value="Informática"></option><option value="Ensino Técnico"></option><option value="Polivalente"></option>
</datalist>

<script>
/* ============================================================
   Caderno de Prompts
   Adaptação do modelo "Geradores de Prompts de IA para
   Professores", de Sérgio Araújo (educ.nekoweb.org),
   licenciado em CC BY-NC-SA 4.0. Esta versão mantém a licença.
   ============================================================ */

const L = (rot, v) => (v && String(v).trim()) ? `\n- ${rot}: ${String(v).trim()}` : "";
const P = (titulo, corpo) => (corpo && String(corpo).trim()) ? `\n\n${titulo}\n${String(corpo).trim()}` : "";
const REGRAS_BASE =
`- Escreva em português do Brasil, com linguagem clara e acessível.
- Garanta correção conceitual e adequação à faixa etária.
- Se faltar alguma informação essencial, faça no máximo 3 perguntas antes de começar.`;

const ANOS = ["",
"Berçário / Maternal","G4 (4 anos)","G5 (5 anos)",
"1º ano — Fundamental I","2º ano — Fundamental I","3º ano — Fundamental I","4º ano — Fundamental I","5º ano — Fundamental I",
"6º ano — Fundamental II","7º ano — Fundamental II","8º ano — Fundamental II","9º ano — Fundamental II",
"1ª série — Ensino Médio","2ª série — Ensino Médio","3ª série — Ensino Médio",
"EJA I","EJA II","Curso técnico","Ensino superior"];

/* ---------- IAs recomendadas ----------
   Os ícones são desenhos próprios, feitos para lembrar cada
   ferramenta. Não são as marcas oficiais.                     */
const SVG_T = 'viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"';
const SVG_F = 'viewBox="0 0 24 24" fill="currentColor"';

const IAS = {
  chatgpt:{nome:"ChatGPT", url:"https://chatgpt.com/", cor:"#10A37F",
    icone:`<svg ${SVG_T}><path d="M12 2.7l8 4.6v9.4l-8 4.6-8-4.6V7.3z"/><path d="M12 7.4l3.9 2.3v4.6L12 16.6l-3.9-2.3V9.7z"/></svg>`},
  claude:{nome:"Claude", url:"https://claude.ai/new", cor:"#D97757",
    icone:`<svg ${SVG_T} stroke-width="2"><path d="M12 3.2v17.6M3.2 12h17.6M5.8 5.8l12.4 12.4M18.2 5.8L5.8 18.2"/></svg>`},
  gemini:{nome:"Gemini", url:"https://gemini.google.com/app", cor:"#4285F4",
    icone:`<svg ${SVG_F}><path d="M12 2.2c.55 4.95 4.28 8.68 9.23 9.23-4.95.55-8.68 4.28-9.23 9.23-.55-4.95-4.28-8.68-9.23-9.23C7.72 10.88 11.45 7.15 12 2.2z"/></svg>`},
  copilot:{nome:"Copilot", url:"https://copilot.microsoft.com/", cor:"#2A8AC8",
    icone:`<svg ${SVG_T} stroke-width="2"><path d="M4.6 15.6c0-5.1 2.6-8.7 6.2-8.7 2.7 0 3.9 2.1 4.5 4.5"/><path d="M19.4 8.4c0 5.1-2.6 8.7-6.2 8.7-2.7 0-3.9-2.1-4.5-4.5"/></svg>`},
  deepseek:{nome:"DeepSeek", url:"https://chat.deepseek.com/", cor:"#4D6BFE",
    icone:`<svg ${SVG_F}><path d="M3 12.6c3 .6 4.3-1.5 7.3-1.3 2.8.2 3.9 2.7 7.5 3 1.1.1 2.2-.1 3.2-.6-.7 3.3-4 5.7-8.2 5.7C7.2 19.4 3.6 16.5 3 12.6z"/><path d="M17.5 5.3L21 4l-1 3.6c-.6-1-1.4-1.8-2.5-2.3z"/></svg>`},
  perplexity:{nome:"Perplexity", url:"https://www.perplexity.ai/", cor:"#20A0AE",
    icone:`<svg ${SVG_T}><path d="M12 4.4v15.2"/><path d="M12 8.6L6.6 4.7v6.5H4.3v5.1h2.3v3.9L12 16.3"/><path d="M12 8.6l5.4-3.9v6.5h2.3v5.1h-2.3v3.9L12 16.3"/></svg>`},
  notebooklm:{nome:"NotebookLM", url:"https://notebooklm.google.com/", cor:"#7B61FF",
    icone:`<svg ${SVG_T}><rect x="4.4" y="3.2" width="15.2" height="17.6" rx="2.2"/><path d="M9 3.2v17.6"/><path d="M14.6 9.1l.85 2.05 2.05.85-2.05.85-.85 2.05-.85-2.05-2.05-.85 2.05-.85z"/></svg>`},
  aistudio:{nome:"AI Studio", url:"https://aistudio.google.com/", cor:"#34A853",
    icone:`<svg ${SVG_T}><rect x="3.2" y="3.2" width="17.6" height="17.6" rx="4.6"/><path d="M12 7.3c.34 2.55 2.15 4.36 4.7 4.7-2.55.34-4.36 2.15-4.7 4.7-.34-2.55-2.15-4.36-4.7-4.7 2.55-.34 4.36-2.15 4.7-4.7z" fill="currentColor" stroke="none"/></svg>`},
  gamma:{nome:"Gamma", url:"https://gamma.app/", cor:"#8B5CF6",
    icone:`<svg ${SVG_F}><text x="12" y="18" text-anchor="middle" font-size="16" font-weight="700" font-family="Georgia,serif">&#947;</text></svg>`},
  canva:{nome:"Canva", url:"https://www.canva.com/", cor:"#00A9B0",
    icone:`<svg ${SVG_T}><circle cx="12" cy="12" r="9"/><path d="M15.4 9.3a4.4 4.4 0 0 0-6.3 6 4.4 4.4 0 0 0 6.5-.7" stroke-width="2"/></svg>`},
  ideogram:{nome:"Ideogram", url:"https://ideogram.ai/", cor:"#E2556B",
    icone:`<svg ${SVG_T}><rect x="3.4" y="3.4" width="17.2" height="17.2" rx="5"/><path d="M12 7.8v8.4" stroke-width="2.6"/></svg>`},
  leonardo:{nome:"Leonardo", url:"https://leonardo.ai/", cor:"#C08A2E",
    icone:`<svg ${SVG_F}><path d="M7.4 3h9.2l4 6-8.6 12L3.4 9z"/></svg>`},
  bingimg:{nome:"Bing Imagens", url:"https://www.bing.com/images/create", cor:"#2A8AC8",
    icone:`<svg ${SVG_T}><rect x="3.2" y="4.6" width="17.6" height="14.8" rx="2.4"/><circle cx="8.6" cy="10" r="1.6"/><path d="M3.8 17.4l5-4.9 3.4 3.3 3-2.5 5 4.2"/></svg>`},
  napkin:{nome:"Napkin", url:"https://www.napkin.ai/", cor:"#8A948F",
    icone:`<svg ${SVG_T}><circle cx="6" cy="6.6" r="2.5"/><circle cx="18" cy="12" r="2.5"/><circle cx="6" cy="17.4" r="2.5"/><path d="M8.4 7.7l7.2 3.1M8.4 16.3l7.2-3.1"/></svg>`},
  v0:{nome:"v0", url:"https://v0.app/", cor:"#8A948F",
    icone:`<svg ${SVG_F}><text x="12" y="16.8" text-anchor="middle" font-size="12" font-weight="700" font-family="Helvetica,Arial,sans-serif">v0</text></svg>`},
  bolt:{nome:"Bolt", url:"https://bolt.new/", cor:"#3B82F6",
    icone:`<svg ${SVG_F}><path d="M13.5 2L4.4 13.7h5.6L9.1 22l9.5-12.5h-6.1z"/></svg>`},
  lovable:{nome:"Lovable", url:"https://lovable.dev/", cor:"#E8446C",
    icone:`<svg ${SVG_F}><path d="M12 20.6l-1.4-1.3C5.5 14.7 2.4 11.9 2.4 8.4 2.4 5.6 4.6 3.4 7.4 3.4c1.6 0 3.1.7 4.1 1.9 1-1.2 2.5-1.9 4.1-1.9 2.8 0 5 2.2 5 5 0 3.5-3.1 6.3-8.2 10.9z"/></svg>`},
  replit:{nome:"Replit", url:"https://replit.com/", cor:"#F26207",
    icone:`<svg ${SVG_F}><rect x="4.2" y="3.6" width="6.6" height="6.2" rx="1.6"/><rect x="13.2" y="9.9" width="6.6" height="6.2" rx="1.6"/><rect x="4.2" y="14.2" width="6.6" height="6.2" rx="1.6"/></svg>`}
};

/* ============================================================
   BNCC de Computação — Complemento à BNCC (CNE/CEB, 2022)
   141 habilidades e as competências de cada etapa, transcritas
   do documento oficial. Os textos são citação literal.
   ============================================================ */
const BNCC_ETAPAS = ["Educação Infantil", "1º ano", "2º ano", "3º ano", "4º ano", "5º ano", "1º ao 5º ano (por etapa)", "6º ano", "7º ano", "8º ano", "9º ano", "6º ao 9º ano (por etapa)", "Ensino Médio"];
const BNCC_COMPETENCIAS = {
  ei:{rotulo:"Educação Infantil — premissas da Computação", itens:[
    "Desenvolver o reconhecimento e a identificação de padrões, construindo conjuntos de objetos com base em diferentes critérios como: quantidade, forma, tamanho, cor e comportamento.",
    "Vivenciar e identificar diferentes formas de interação mediadas por artefatos computacionais.",
    "Criar e testar algoritmos brincando com objetos do ambiente e com movimentos do corpo de maneira individual ou em grupo.",
    "Solucionar problemas decompondo-os em partes menores identificando passos, etapas ou ciclos que se repetem e que podem ser generalizadas ou reutilizadas para outros problemas."
  ]},
  ef:{rotulo:"Ensino Fundamental — competências de Computação", itens:[
    "Compreender a Computação como uma área de conhecimento que contribui para explicar o mundo atual e ser um agente ativo e consciente de transformação capaz de analisar criticamente seus impactos sociais, ambientais, culturais, econômicos, científicos, tecnológicos, legais e éticos.",
    "Reconhecer o impacto dos artefatos computacionais e os respectivos desafios para os indivíduos na sociedade, discutindo questões socioambientais, culturais, científicas, políticas e econômicas.",
    "Expressar e partilhar informações, ideias, sentimentos e soluções computacionais utilizando diferentes linguagens e tecnologias da Computação de forma criativa, crítica, significativa, reflexiva e ética.",
    "Aplicar os princípios e técnicas da Computação e suas tecnologias para identificar problemas e criar soluções computacionais, preferencialmente de forma cooperativa, bem como alicerçar descobertas em diversas áreas do conhecimento seguindo uma abordagem científica e inovadora, considerando os impactos sob diferentes contextos.",
    "Avaliar as soluções e os processos envolvidos na resolução computacional de problemas de diversas áreas do conhecimento, sendo capaz de construir argumentações coerentes e consistentes, utilizando conhecimentos da Computação para argumentar em diferentes contextos com base em fatos e informações confiáveis com respeito à diversidade de opiniões, saberes, identidades e culturas.",
    "Desenvolver projetos, baseados em problemas, desafios e oportunidades que façam sentido ao contexto ou interesse do estudante, de maneira individual e/ou cooperativa, fazendo uso da Computação e suas tecnologias, utilizando conceitos, técnicas e ferramentas computacionais que possibilitem automatizar processos em diversas áreas do conhecimento com base em princípios éticos, democráticos, sustentáveis e solidários, valorizando a diversidade de indivíduos e de grupos sociais, de maneira inclusiva.",
    "Agir pessoal e coletivamente com respeito, autonomia, responsabilidade, flexibilidade, resiliência e determinação, identificando e reconhecendo seus direitos e deveres, recorrendo aos conhecimentos da Computação e suas tecnologias para tomar decisões frente às questões de diferentes naturezas."
  ]},
  em:{rotulo:"Ensino Médio — competências de Computação", itens:[
    "Compreender as possibilidades e os limites da Computação para resolver problemas, tanto em termos de viabilidade quanto de eficiência, propondo e analisando soluções computacionais para diversos domínios do conhecimento, considerando diferentes aspectos.",
    "Analisar criticamente artefatos computacionais, sendo capaz de identificar as vulnerabilidades dos ambientes e das soluções computacionais buscando garantir a integridade, privacidade, sigilo e segurança das informações.",
    "Analisar situações do mundo contemporâneo, selecionando técnicas computacionais apropriadas para a solução de problemas.",
    "Construir conhecimento usando técnicas e tecnologias computacionais, produzindo conteúdos e artefatos de forma criativa, com respeito às questões éticas e legais, que proporcionem experiências para si e os demais.",
    "Desenvolver projetos para investigar desafios do mundo contemporâneo, construir soluções e tomar decisões éticas, democráticas e socialmente responsáveis, articulando conceitos, procedimentos e linguagens próprias da Computação preferencialmente de maneira colaborativa.",
    "Expressar e partilhar informações, ideias, sentimentos e soluções computacionais utilizando diferentes plataformas, ferramentas, linguagens e tecnologias da Computação de forma fluente, criativa, crítica, significativa, reflexiva e ética.",
    "Agir pessoal e coletivamente com respeito, autonomia, responsabilidade, flexibilidade, resiliência e determinação, identificando e reconhecendo seus direitos e deveres, recorrendo aos conhecimentos da Computação e suas tecnologias frente às questões de diferentes naturezas."
  ]},
};
const BNCC_HAB = [
  {c:"EI03CO01",e:"Educação Infantil",x:"Pensamento Computacional",t:"Reconhecer padrão de repetição em sequência de sons, movimentos, desenhos."},
  {c:"EI03CO02",e:"Educação Infantil",x:"Pensamento Computacional",t:"Expressar as etapas para a realização de uma tarefa de forma clara e ordenada."},
  {c:"EI03CO03",e:"Educação Infantil",x:"Pensamento Computacional",t:"Experienciar a execução de algoritmos brincando com objetos (des)plugados."},
  {c:"EI03CO04",e:"Educação Infantil",x:"Pensamento Computacional",t:"Criar e representar algoritmos para resolver problemas."},
  {c:"EI03CO05",e:"Educação Infantil",x:"Pensamento Computacional",t:"Comparar soluções algorítmicas para resolver um mesmo problema."},
  {c:"EI03CO06",e:"Educação Infantil",x:"Pensamento Computacional",t:"Compreender decisões em dois estados (verdadeiro ou falso)."},
  {c:"EI03CO07",e:"Educação Infantil",x:"Mundo Digital",t:"Reconhecer dispositivos eletrônicos (e não-eletrônicos), identificando quando estão ligados ou desligados (abertos ou fechados)."},
  {c:"EI03CO08",e:"Educação Infantil",x:"Mundo Digital",t:"Compreender o conceito de interfaces para comunicação com objetos (des)plugados."},
  {c:"EI03CO09",e:"Educação Infantil",x:"Mundo Digital",t:"Identificar dispositivos computacionais e as diferentes formas de interação."},
  {c:"EI03CO10",e:"Educação Infantil",x:"Cultura Digital",t:"Utilizar tecnologia digital de maneira segura, consciente e respeitosa."},
  {c:"EI03CO11",e:"Educação Infantil",x:"Cultura Digital",t:"Adotar hábitos saudáveis de uso de artefatos computacionais, seguindo recomendações de órgãos de saúde competentes."},
  {c:"EF01CO01",e:"1º ano",x:"Pensamento Computacional",t:"Organizar objetos físicos ou digitais considerando diferentes características para esta organização, explicitando semelhanças (padrões) e diferenças."},
  {c:"EF01CO02",e:"1º ano",x:"Mundo Digital",t:"Identificar e seguir sequências de passos aplicados no dia a dia para resolver problemas."},
  {c:"EF01CO03",e:"1º ano",x:"Mundo Digital",t:"Reorganizar e criar sequências de passos em meios físicos ou digitais, relacionando essas sequências à palavra “Algoritmos”."},
  {c:"EF01CO04",e:"1º ano",x:"Mundo Digital",t:"Reconhecer o que é a informação, que ela pode ser armazenada, transmitida como mensagem por diversos meios e descrita em várias linguagens."},
  {c:"EF01CO05",e:"1º ano",x:"Mundo Digital",t:"Representar informação usando diferentes codificações."},
  {c:"EF01CO06",e:"1º ano",x:"Cultura Digital",t:"Reconhecer e explorar artefatos computacionais voltados a atender necessidades pessoais ou coletivas."},
  {c:"EF01CO07",e:"1º ano",x:"Cultura Digital",t:"Conhecer as possibilidades de uso seguro das tecnologias computacionais para proteção dos dados pessoais e para garantir a própria segurança."},
  {c:"EF02CO01",e:"2º ano",x:"Pensamento Computacional",t:"Criar e comparar modelos (representações) de objetos, identificando padrões e atributos essenciais."},
  {c:"EF02CO02",e:"2º ano",x:"Mundo Digital",t:"Criar e simular algoritmos representados em linguagem oral, escrita ou pictográfica, construídos como sequências com repetições simples (iterações definidas) com base em instruções preestabelecidas ou criadas, analisando como a precisão da instrução impacta na execução do algoritmo."},
  {c:"EF02CO03",e:"2º ano",x:"Mundo Digital",t:"Identificar que máquinas diferentes executam conjuntos próprios de instruções e que podem ser usadas para definir algoritmos."},
  {c:"EF02CO04",e:"2º ano",x:"Cultura Digital",t:"Diferenciar componentes físicos (hardware) e programas que fornecem as instruções (software) para o hardware."},
  {c:"EF02CO05",e:"2º ano",x:"Cultura Digital",t:"Reconhecer as características e usos das tecnologias computacionais no cotidiano dentro e fora da escola."},
  {c:"EF02CO06",e:"2º ano",x:"Cultura Digital",t:"Reconhecer os cuidados com a segurança no uso de dispositivos computacionais."},
  {c:"EF03CO01",e:"3º ano",x:"Pensamento Computacional",t:"Associar os valores 'verdadeiro' e 'falso' a sentenças lógicas que dizem respeito a situações do dia a dia, fazendo uso de termos que indicam negação."},
  {c:"EF03CO02",e:"3º ano",x:"Pensamento Computacional",t:"Criar e simular algoritmos representados em linguagem oral, escrita ou pictográfica, que incluam sequências e repetições simples com condição (iterações indefinidas), para resolver problemas de forma independente e em colaboração."},
  {c:"EF03CO03",e:"3º ano",x:"Pensamento Computacional",t:"Aplicar a estratégia de decomposição para resolver problemas complexos, dividindo esse problema em partes menores, resolvendo-as e combinando suas soluções."},
  {c:"EF03CO04",e:"3º ano",x:"Mundo Digital",t:"Relacionar o conceito de informação com o de dado."},
  {c:"EF03CO05",e:"3º ano",x:"Mundo Digital",t:"Compreender que dados são estruturados em formatos específicos dependendo da informação armazenada."},
  {c:"EF03CO06",e:"3º ano",x:"Mundo Digital",t:"Reconhecer que, para um computador realizar tarefas, ele se comunica com o mundo exterior com o uso de interfaces físicas (dispositivos de entrada e saída)."},
  {c:"EF03CO07",e:"3º ano",x:"Cultura Digital",t:"Utilizar diferentes navegadores e ferramentas de busca para pesquisar e acessar informações."},
  {c:"EF03CO08",e:"3º ano",x:"Cultura Digital",t:"Usar ferramentas computacionais em situações didáticas para se expressar em diferentes formatos digitais."},
  {c:"EF03CO09",e:"3º ano",x:"Cultura Digital",t:"Reconhecer o potencial impacto do compartilhamento de informações pessoais ou de seus pares em meio digital."},
  {c:"EF04CO01",e:"4º ano",x:"Pensamento Computacional",t:"Reconhecer objetos do mundo real e/ou digital que podem ser representados através de matrizes que estabelecem uma organização na qual cada componente está em uma posição definida por coordenadas, fazendo manipulações simples sobre estas representações."},
  {c:"EF04CO02",e:"4º ano",x:"Pensamento Computacional",t:"Reconhecer objetos do mundo real e/ou digital que podem ser representados através de registros que estabelecem uma organização na qual cada componente é identificado por um nome, fazendo manipulações sobre estas representações."},
  {c:"EF04CO03",e:"4º ano",x:"Pensamento Computacional",t:"Criar e simular algoritmos representados em linguagem oral, escrita ou pictográfica, que incluam sequências e repetições simples e aninhadas (iterações definidas e indefinidas), para resolver problemas de forma independente e em colaboração."},
  {c:"EF04CO04",e:"4º ano",x:"Mundo Digital",t:"Entender que para guardar, manipular e transmitir dados deve-se codificá-los de alguma forma que seja compreendida pela máquina (formato digital)."},
  {c:"EF04CO05",e:"4º ano",x:"Cultura Digital",t:"Codificar diferentes informações para representação em computador (binária, ASCII, atributos de pixel, como RGB etc.)."},
  {c:"EF04CO06",e:"4º ano",x:"Cultura Digital",t:"Usar diferentes ferramentas computacionais para criação de conteúdo (textos, apresentações, vídeos etc.)."},
  {c:"EF04CO07",e:"4º ano",x:"Cultura Digital",t:"Demonstrar postura ética nas atividades de coleta, transferência, guarda e uso de dados."},
  {c:"EF04CO08",e:"4º ano",x:"Cultura Digital",t:"Reconhecer a importância de verificar a confiabilidade das fontes de informações obtidas na Internet."},
  {c:"EF05CO01",e:"5º ano",x:"Pensamento Computacional",t:"Reconhecer objetos do mundo real e/ou digital que podem ser representados através de listas que estabelecem uma organização na qual há um número variável de itens dispostos em sequência, fazendo manipulações simples sobre estas representações."},
  {c:"EF05CO02",e:"5º ano",x:"Pensamento Computacional",t:"Reconhecer objetos do mundo real e digital que podem ser representados através de grafos que estabelecem uma organização com uma quantidade variável de vértices conectados por arestas, fazendo manipulações simples sobre estas representações."},
  {c:"EF05CO03",e:"5º ano",x:"Pensamento Computacional",t:"Realizar operações de negação, conjunção e disjunção sobre sentenças lógicas e valores 'verdadeiro' e 'falso'."},
  {c:"EF05CO04",e:"5º ano",x:"Mundo Digital",t:"Criar e simular algoritmos representados em linguagem oral, escrita ou pictográfica, que incluam sequências, repetições e seleções condicionais para resolver problemas de forma independente e em colaboração."},
  {c:"EF05CO05",e:"5º ano",x:"Mundo Digital",t:"Identificar os componentes principais de um computador (dispositivos de entrada/saída, processadores e armazenamento)."},
  {c:"EF05CO06",e:"5º ano",x:"Mundo Digital",t:"Reconhecer que os dados podem ser armazenados em um dispositivo local ou remoto."},
  {c:"EF05CO07",e:"5º ano",x:"Mundo Digital",t:"Reconhecer a necessidade de um sistema operacional para a execução de programas e gerenciamento do hardware."},
  {c:"EF05CO08",e:"5º ano",x:"Cultura Digital",t:"Acessar as informações na Internet de forma crítica para distinguir os conteúdos confiáveis de não confiáveis."},
  {c:"EF05CO09",e:"5º ano",x:"Cultura Digital",t:"Usar informações considerando aplicações e limites dos direitos autorais em diferentes mídias digitais."},
  {c:"EF05CO10",e:"5º ano",x:"Cultura Digital",t:"Expressar-se crítica e criativamente na compreensão das mudanças tecnológicas no mundo do trabalho e sobre a evolução da sociedade."},
  {c:"EF05CO11",e:"5º ano",x:"Cultura Digital",t:"Identificar a adequação de diferentes tecnologias computacionais na resolução de problemas."},
  {c:"EF15CO01",e:"1º ao 5º ano (por etapa)",x:"Pensamento Computacional",t:"Identificar as principais formas de organizar e representar a informação de maneira estruturada (matrizes, registros, listas e grafos) ou não estruturada (números, palavras, valores verdade)."},
  {c:"EF15CO02",e:"1º ao 5º ano (por etapa)",x:"Pensamento Computacional",t:"Construir e simular algoritmos, de forma independente ou em colaboração, que resolvam problemas simples e do cotidiano com uso de sequências, seleções condicionais e repetições de instruções."},
  {c:"EF15CO03",e:"1º ao 5º ano (por etapa)",x:"Pensamento Computacional",t:"Realizar operações de negação, conjunção e disjunção sobre sentenças lógicas e valores 'verdadeiro' e 'falso'."},
  {c:"EF15CO04",e:"1º ao 5º ano (por etapa)",x:"Pensamento Computacional",t:"Aplicar a estratégia de decomposição para resolver problemas complexos, dividindo esse problema em partes menores, resolvendo-as e combinando suas soluções."},
  {c:"EF15CO05",e:"1º ao 5º ano (por etapa)",x:"Mundo Digital",t:"Codificar a informação de diferentes formas, entendendo a importância desta codificação para o armazenamento, manipulação e transmissão em dispositivos computacionais."},
  {c:"EF15CO06",e:"1º ao 5º ano (por etapa)",x:"Cultura Digital",t:"Conhecer os componentes básicos de dispositivos computacionais, entendendo os princípios de seu funcionamento."},
  {c:"EF15CO07",e:"1º ao 5º ano (por etapa)",x:"Cultura Digital",t:"Conhecer o conceito de Sistema Operacional e sua importância na integração entre software e hardware."},
  {c:"EF15CO08",e:"1º ao 5º ano (por etapa)",x:"Cultura Digital",t:"Reconhecer e utilizar tecnologias computacionais para pesquisar e acessar informações, expressar-se crítica e criativamente e resolver problemas."},
  {c:"EF15CO09",e:"1º ao 5º ano (por etapa)",x:"Cultura Digital",t:"Entender que as tecnologias devem ser utilizadas de maneira segura, ética e responsável, respeitando direitos autorais, de imagem e as leis vigentes."},
  {c:"EF06CO01",e:"6º ano",x:"Pensamento Computacional",t:"Classificar informações, agrupando-as em coleções (conjuntos) e associando cada coleção a um “tipo de dados”."},
  {c:"EF06CO02",e:"6º ano",x:"Pensamento Computacional",t:"Elaborar algoritmos que envolvam instruções sequenciais, de repetição e de seleção usando uma linguagem de programação."},
  {c:"EF06CO03",e:"6º ano",x:"Pensamento Computacional",t:"Descrever com precisão a solução de um problema, construindo o programa que implementa a solução descrita."},
  {c:"EF06CO04",e:"6º ano",x:"Pensamento Computacional",t:"Construir soluções de problemas usando a técnica de decomposição e automatizar tais soluções usando uma linguagem de programação."},
  {c:"EF06CO05",e:"6º ano",x:"Pensamento Computacional",t:"Identificar os recursos ou insumos necessários (entradas) para a resolução de problemas, bem como os resultados esperados (saídas), determinando os respectivos tipos de dados, e estabelecendo a definição de problema como uma relação entre entrada e saída."},
  {c:"EF06CO06",e:"6º ano",x:"Pensamento Computacional",t:"Comparar diferentes casos particulares (instâncias) de um mesmo problema, identificando as semelhanças e diferenças entre eles, e criar um algoritmo para resolver todos, fazendo uso de variáveis (parâmetros) para permitir o tratamento de todos os casos de forma genérica."},
  {c:"EF06CO07",e:"6º ano",x:"Cultura Digital",t:"Entender o processo de transmissão de dados, como a informação é quebrada em pedaços, transmitida em pacotes através de múltiplos equipamentos, e reconstruída no destino."},
  {c:"EF06CO08",e:"6º ano",x:"Cultura Digital",t:"Compreender e utilizar diferentes formas de armazenar, manipular, compactar e recuperar arquivos, documentos e metadados."},
  {c:"EF06CO09",e:"6º ano",x:"Cultura Digital",t:"Apresentar conduta e linguagem apropriadas ao se comunicar em ambiente digital, considerando a ética e o respeito."},
  {c:"EF06CO10",e:"6º ano",x:"Cultura Digital",t:"Analisar o consumo de tecnologia na sociedade, compreendendo criticamente o caminho da produção dos recursos bem como aspectos ligados à obsolescência e a sustentabilidade."},
  {c:"EF07CO01",e:"7º ano",x:"Pensamento Computacional",t:"Criar soluções de problemas para os quais seja adequado o uso de registros e matrizes unidimensionais para descrever suas informações e automatizá-las usando uma linguagem de programação."},
  {c:"EF07CO02",e:"7º ano",x:"Pensamento Computacional",t:"Analisar programas para detectar e remover erros, ampliando a confiança na sua correção."},
  {c:"EF07CO03",e:"7º ano",x:"Pensamento Computacional",t:"Construir soluções computacionais de problemas de diferentes áreas do conhecimento, de forma individual e colaborativa, selecionando as estruturas de dados e técnicas adequadas, aperfeiçoando e articulando saberes escolares."},
  {c:"EF07CO04",e:"7º ano",x:"Pensamento Computacional",t:"Explorar propriedades básicas de grafos."},
  {c:"EF07CO05",e:"7º ano",x:"Mundo Digital",t:"Criar algoritmos fazendo uso da decomposição e do reúso no processo de solução de forma colaborativa e cooperativa e automatizá-los usando uma linguagem de programação."},
  {c:"EF07CO06",e:"7º ano",x:"Mundo Digital",t:"Compreender o papel de protocolos para a transmissão de dados."},
  {c:"EF07CO07",e:"7º ano",x:"Mundo Digital",t:"Identificar problemas de segurança cibernética e experimentar formas de proteção."},
  {c:"EF07CO08",e:"7º ano",x:"Cultura Digital",t:"Demonstrar empatia sobre opiniões divergentes na web."},
  {c:"EF07CO09",e:"7º ano",x:"Cultura Digital",t:"Reconhecer e debater sobre cyberbullying."},
  {c:"EF07CO10",e:"7º ano",x:"Cultura Digital",t:"Identificar os impactos ambientais do descarte de peças de computadores e eletrônicos, bem como sua relação com a sustentabilidade."},
  {c:"EF07CO11",e:"7º ano",x:"Cultura Digital",t:"Criar, documentar e publicar, de forma individual ou colaborativa, produtos (vídeos, podcasts, web sites) usando recursos de tecnologia."},
  {c:"EF08CO01",e:"8º ano",x:"Pensamento Computacional",t:"Construir soluções de problemas usando a técnica de recursão e automatizar tais soluções usando uma linguagem de programação."},
  {c:"EF08CO02",e:"8º ano",x:"Mundo Digital",t:"Criar soluções de problemas para os quais seja adequado o uso de listas para descrever suas informações e automatizá-las usando uma linguagem de programação, empregando ou não a recursão como uma técnica de resolver o problema."},
  {c:"EF08CO03",e:"8º ano",x:"Mundo Digital",t:"Utilizar algoritmos clássicos de manipulação sobre listas."},
  {c:"EF08CO04",e:"8º ano",x:"Mundo Digital",t:"Construir soluções computacionais de problemas de diferentes áreas do conhecimento, de forma individual e colaborativa, selecionando as estruturas de dados e técnicas adequadas, aperfeiçoando e articulando saberes escolares."},
  {c:"EF08CO05",e:"8º ano",x:"Mundo Digital",t:"Compreender os conceitos de paralelismo, concorrência e armazenamento/ processamento distribuídos."},
  {c:"EF08CO06",e:"8º ano",x:"Mundo Digital",t:"Entender como é a estrutura e funcionamento da internet."},
  {c:"EF08CO07",e:"8º ano",x:"Cultura Digital",t:"Compartilhar informações por meio de redes sociais, compreendendo a sua dinâmica de funcionamento, de forma responsável e avaliando sua confiabilidade, considerando o respeito e a ética."},
  {c:"EF08CO08",e:"8º ano",x:"Cultura Digital",t:"Distinguir os tipos de dados pessoais que são solicitados em espaços digitais e os riscos associados."},
  {c:"EF08CO09",e:"8º ano",x:"Cultura Digital",t:"Analisar criticamente as políticas de termos de uso das redes sociais e demais plataformas."},
  {c:"EF08CO10",e:"8º ano",x:"Cultura Digital",t:"Discutir questões sobre segurança e privacidade relacionadas ao uso dos ambientes virtuais."},
  {c:"EF08CO11",e:"8º ano",x:"Cultura Digital",t:"Avaliar a precisão, relevância, adequação, abrangência e vieses que ocorrem em fontes de informação eletrônica."},
  {c:"EF09CO01",e:"9º ano",x:"Pensamento Computacional",t:"Criar soluções de problemas para os quais seja adequado o uso de árvores e grafos para descrever suas informações e automatizá-las usando uma linguagem de programação."},
  {c:"EF09CO02",e:"9º ano",x:"Mundo Digital",t:"Construir soluções computacionais de problemas de diferentes áreas do conhecimento, de forma individual e colaborativa, selecionando as estruturas de dados e técnicas adequadas, aperfeiçoando e articulando saberes escolares."},
  {c:"EF09CO03",e:"9º ano",x:"Mundo Digital",t:"Usar autômatos para descrever comportamentos de forma abstrata automatizando-os através de uma linguagem de programação baseada em eventos."},
  {c:"EF09CO04",e:"9º ano",x:"Mundo Digital",t:"Compreender o funcionamento de malwares e outros ataques cibernéticos."},
  {c:"EF09CO05",e:"9º ano",x:"Cultura Digital",t:"Analisar técnicas de criptografia para armazenamento e transmissão de dados."},
  {c:"EF09CO06",e:"9º ano",x:"Cultura Digital",t:"Analisar problemas sociais de sua cidade e estado a partir de ambientes digitais, propondo soluções."},
  {c:"EF09CO07",e:"9º ano",x:"Cultura Digital",t:"Avaliar aplicações e implicações políticas, socioambientais e culturais das tecnologias digitais para propor alternativas aos desafios do mundo contemporâneo, incluindo aqueles relativos ao mundo do trabalho."},
  {c:"EF09CO08",e:"9º ano",x:"Cultura Digital",t:"Discutir como a distribuição desigual de recursos de computação em uma economia global levanta questões de equidade, acesso e poder."},
  {c:"EF09CO09",e:"9º ano",x:"Cultura Digital",t:"Criar ou utilizar conteúdo em meio digital, compreendendo questões éticas relacionadas a direitos autorais e de uso de imagem."},
  {c:"EF09CO10",e:"9º ano",x:"Cultura Digital",t:"Avaliar a veracidade, credibilidade e relevância da informação em seus diferentes formatos, sendo capaz de identificar o propósito pelo qual foi disseminada."},
  {c:"EF69CO01",e:"6º ao 9º ano (por etapa)",x:"Pensamento Computacional",t:"Classificar informações, agrupando-as em coleções (conjuntos) e associando cada coleção a um “tipo de dado”."},
  {c:"EF69CO02",e:"6º ao 9º ano (por etapa)",x:"Pensamento Computacional",t:"Elaborar algoritmos que envolvam instruções sequenciais, de repetição e de seleção usando uma linguagem de programação."},
  {c:"EF69CO03",e:"6º ao 9º ano (por etapa)",x:"Pensamento Computacional",t:"Descrever com precisão a solução de um problema, construindo o programa que implementa a solução descrita."},
  {c:"EF69CO04",e:"6º ao 9º ano (por etapa)",x:"Pensamento Computacional",t:"Construir soluções de problemas usando a técnica de decomposição e automatizar tais soluções usando uma linguagem de programação."},
  {c:"EF69CO05",e:"6º ao 9º ano (por etapa)",x:"Pensamento Computacional",t:"Identificar os recursos ou insumos necessários (entradas) para a resolução de problemas, bem como os resultados esperados (saídas), determinando os respectivos tipos de dados, e estabelecendo a definição de problema como uma relação entre entrada e saída."},
  {c:"EF69CO06",e:"6º ao 9º ano (por etapa)",x:"Pensamento Computacional",t:"Comparar diferentes casos particulares (instâncias) de um mesmo problema, identificando as semelhanças e diferenças entre eles, e criar um algoritmo para resolver todos, fazendo uso de variáveis (parâmetros) para permitir o tratamento de todos os casos de forma genérica."},
  {c:"EF69CO07",e:"6º ao 9º ano (por etapa)",x:"Mundo Digital",t:"Entender o processo de transmissão de dados, como a informação é quebrada em pedaços, transmitida em pacotes através de múltiplos equipamentos, e reconstruída no destino."},
  {c:"EF69CO08",e:"6º ao 9º ano (por etapa)",x:"Cultura Digital",t:"Compreender e utilizar diferentes formas de armazenar, manipular, compactar e recuperar arquivos, documentos e metadados. Sistemas distribuídos e internet Fundamentos de sistemas distribuídos Entender os fundamentos de sistemas distribuídos e da internet."},
  {c:"EF69CO09",e:"6º ao 9º ano (por etapa)",x:"Cultura Digital",t:"Compreender os conceitos de paralelismo, concorrência e armazenamento/ processamento distribuídos."},
  {c:"EF69CO10",e:"6º ao 9º ano (por etapa)",x:"Cultura Digital",t:"Entender como é a estrutura e funcionamento da internet."},
  {c:"EF69CO11",e:"6º ao 9º ano (por etapa)",x:"Cultura Digital",t:"Apresentar conduta e linguagem apropriadas ao se comunicar em ambiente digital, considerando a ética e o respeito."},
  {c:"EF69CO12",e:"6º ao 9º ano (por etapa)",x:"Cultura Digital",t:"Analisar o consumo de tecnologia na sociedade, compreendendo criticamente o caminho da produção dos recursos bem como aspectos ligados à obsolescência e a sustentabilidade."},
  {c:"EM13CO01",e:"Ensino Médio",x:null,t:"Explorar e construir a solução de problemas por meio da reutilização de partes de soluções existentes."},
  {c:"EM13CO02",e:"Ensino Médio",x:null,t:"Explorar e construir a solução de problemas por meio de refinamentos, utilizando diversos níveis de abstração desde a especificação até a implementação."},
  {c:"EM13CO03",e:"Ensino Médio",x:null,t:"Identificar o comportamento dos algoritmos no que diz respeito ao consumo de recursos como tempo de execução, espaço de memória e energia, entre outros."},
  {c:"EM13CO04",e:"Ensino Médio",x:null,t:"Reconhecer o conceito de metaprogramação como uma forma de generalização na construção de programas, permitindo que algoritmos sejam entrada ou saída para outros algoritmos."},
  {c:"EM13CO05",e:"Ensino Médio",x:null,t:"Identificar os limites da Computação para diferenciar o que pode ou não ser automatizado, buscando uma compreensão mais ampla dos limites dos processos mentais envolvidos na resolução de problemas."},
  {c:"EM13CO06",e:"Ensino Médio",x:null,t:"Avaliar software levando em consideração diferentes características e métricas associadas."},
  {c:"EM13CO07",e:"Ensino Médio",x:null,t:"Compreender as diferentes tecnologias, bem como equipamentos, protocolos e serviços envolvidos no funcionamento de redes de computadores, identificando suas possibilidades de escala e confiabilidade."},
  {c:"EM13CO08",e:"Ensino Médio",x:null,t:"Entender como mudanças na tecnologia afetam a segurança, incluindo novas maneiras de preservar sua privacidade e dados pessoais on-line, reportando suspeitas e buscando ajuda em situações de risco. Analisar situações do mundo contemporâneo, selecionando técnicas computacionais apropriadas para a solução de problemas."},
  {c:"EM13CO09",e:"Ensino Médio",x:null,t:"Identificar tecnologias digitais, sua presença e formas de uso, nas diferentes atividades no mundo do trabalho."},
  {c:"EM13CO10",e:"Ensino Médio",x:null,t:"Conhecer os fundamentos da Inteligência Artificial, comparando-a com a inteligência humana, analisando suas potencialidades, riscos e limites."},
  {c:"EM13CO11",e:"Ensino Médio",x:null,t:"Criar e explorar modelos computacionais simples para simular e fazer previsões, identificando sua importância no desenvolvimento científico."},
  {c:"EM13CO12",e:"Ensino Médio",x:null,t:"Produzir, analisar, gerir e compartilhar informações a partir de dados, utilizando princípios de ciência de dados."},
  {c:"EM13CO13",e:"Ensino Médio",x:null,t:"Analisar e utilizar as diferentes formas de representação e consulta a dados em formato digital para pesquisas científicas."},
  {c:"EM13CO14",e:"Ensino Médio",x:null,t:"Avaliar a confiabilidade das informações encontradas em meio digital, investigando seus modos de construção e considerando a autoria, a estrutura e o propósito da mensagem."},
  {c:"EM13CO15",e:"Ensino Médio",x:null,t:"Analisar a interação entre usuários e artefatos computacionais, abordando aspectos da experiência do usuário e promovendo reflexão sobre a qualidade do uso dos artefatos nas esferas do trabalho, do lazer e do estudo."},
  {c:"EM13CO16",e:"Ensino Médio",x:null,t:"Desenvolver projetos com robótica, utilizando artefatos físicos ou simuladores."},
  {c:"EM13CO17",e:"Ensino Médio",x:null,t:"Construir redes virtuais de interação e colaboração, favorecendo o desenvolvimento de projetos de forma segura, legal e ética."},
  {c:"EM13CO18",e:"Ensino Médio",x:null,t:"Planejar e gerenciar projetos integrados às áreas de conhecimento de forma colaborativa, solucionando problemas, usando diversos artefatos computacionais."},
  {c:"EM13CO19",e:"Ensino Médio",x:null,t:"Expor, argumentar e negociar propostas, produtos e serviços, utilizando diferentes mídias e ferramentas digitais."},
  {c:"EM13CO20",e:"Ensino Médio",x:null,t:"Criar conteúdos, disponibilizando-os em ambientes virtuais para publicação e compartilhamento, avaliando a confiabilidade e as consequências da disseminação dessas informações."},
  {c:"EM13CO21",e:"Ensino Médio",x:null,t:"Comunicar ideias complexas de forma clara por meio de objetos digitais como mapas conceituais, infográficos, hipertextos e outros."},
  {c:"EM13CO22",e:"Ensino Médio",x:null,t:"Produzir e publicar conteúdo como textos, imagens, áudios, vídeos e suas associações, bem como ferramentas para sua integração, organização e apresentação, utilizando diferentes mídias digitais."},
  {c:"EM13CO23",e:"Ensino Médio",x:null,t:"Analisar criticamente as experiências em comunidades virtuais e as relações advindas da interação e comunicação com outras pessoas, bem como seus impactos na sociedade."},
  {c:"EM13CO24",e:"Ensino Médio",x:null,t:"Identificar e reconhecer como as redes sociais e artefatos computacionais em geral interferem na saúde física e mental de seus usuários."},
  {c:"EM13CO25",e:"Ensino Médio",x:null,t:"Dialogar em ambientes virtuais com segurança e respeito às diferenças culturais e pessoais, reconhecendo e denunciando atitudes abusivas."},
  {c:"EM13CO26",e:"Ensino Médio",x:null,t:"Aplicar os conceitos e pressupostos do direito digital em sua conduta e experiências com o cotidiano da cultura digital, bem como na produção e uso de artefatos computacionais."},
];


/* ---------- BNCC de Computação: do formulário para o prompt ---------- */
const MAPA_ANO_BNCC = {
  "Berçário / Maternal":"Educação Infantil","G4 (4 anos)":"Educação Infantil","G5 (5 anos)":"Educação Infantil",
  "1º ano — Fundamental I":"1º ano","2º ano — Fundamental I":"2º ano","3º ano — Fundamental I":"3º ano",
  "4º ano — Fundamental I":"4º ano","5º ano — Fundamental I":"5º ano",
  "6º ano — Fundamental II":"6º ano","7º ano — Fundamental II":"7º ano",
  "8º ano — Fundamental II":"8º ano","9º ano — Fundamental II":"9º ano",
  "1ª série — Ensino Médio":"Ensino Médio","2ª série — Ensino Médio":"Ensino Médio","3ª série — Ensino Médio":"Ensino Médio",
  "EJA I":"1º ao 5º ano (por etapa)","EJA II":"6º ao 9º ano (por etapa)",
  "Curso técnico":"Ensino Médio","Ensino superior":"Ensino Médio"
};
const BNCC_PAR = {
  "1º ano":"1º ao 5º ano (por etapa)","2º ano":"1º ao 5º ano (por etapa)","3º ano":"1º ao 5º ano (por etapa)",
  "4º ano":"1º ao 5º ano (por etapa)","5º ano":"1º ao 5º ano (por etapa)",
  "6º ano":"6º ao 9º ano (por etapa)","7º ano":"6º ao 9º ano (por etapa)",
  "8º ano":"6º ao 9º ano (por etapa)","9º ano":"6º ao 9º ano (por etapa)"
};
const bnccManual = {};

function etapaDoFormulario(g){
  const v = valores[g.id] || {};
  for(const c of g.campos){ if(c.op === ANOS && v[c.id]) return MAPA_ANO_BNCC[v[c.id]] || ""; }
  for(const c of g.campos){
    const val = v[c.id] || "";
    if(/G4|G5|Berçário|Maternal/i.test(val)) return "Educação Infantil";
    if(/Ensino Médio/i.test(val)) return "Ensino Médio";
    if(/^(\d)º ano/.test(val)) return RegExp.$1 + "º ano";
  }
  return "";
}
function etapaEfetiva(g){
  return bnccManual[g.id] ? (bnccEtapa[g.id] || "") : etapaDoFormulario(g);
}
function habsDaEtapa(etapa){
  if(!etapa) return [];
  const par = BNCC_PAR[etapa];
  return BNCC_HAB.filter(h => h.e === etapa || (par && h.e === par));
}
function competenciasDaEtapa(etapa){
  if(etapa === "Educação Infantil") return BNCC_COMPETENCIAS.ei;
  if(etapa === "Ensino Médio") return BNCC_COMPETENCIAS.em;
  return BNCC_COMPETENCIAS.ef;
}

function bnccUI(){
  return `<div class="bncc">
    <div class="bncc-head">
      <span class="card-title">BNCC de Computação</span>
      <span class="bncc-cont" id="bncc-cont"></span>
    </div>
    <div class="bncc-ctrl">
      <select id="bncc-etapa" aria-label="Etapa da BNCC de Computação"></select>
      <input id="bncc-busca" type="search" placeholder="Filtrar por palavra ou código…" aria-label="Filtrar habilidades">
    </div>
    <div class="bncc-lista" id="bncc-lista"></div>
    <p class="bncc-nota" id="bncc-nota"></p>
  </div>`;
}

function listaBNCC(g){
  const caixa = document.getElementById("bncc-lista");
  if(!caixa) return;
  const etapa = etapaEfetiva(g);
  const q = (document.getElementById("bncc-busca").value || "").trim().toLowerCase();
  const sel = bnccSel[g.id] || (bnccSel[g.id] = []);
  const itens = habsDaEtapa(etapa).filter(h => !q || (h.c + " " + h.t + " " + (h.x||"")).toLowerCase().includes(q));

  if(!etapa){
    caixa.innerHTML = '<div class="bncc-vazio">Escolha o ano/série no formulário ou a etapa aqui em cima para ver as habilidades.</div>';
  } else if(!itens.length){
    caixa.innerHTML = '<div class="bncc-vazio">Nenhuma habilidade encontrada com esse filtro.</div>';
  } else {
    let html = "", eixoAtual = null;
    itens.forEach(h=>{
      const eixo = h.x || "Competências específicas do Ensino Médio";
      if(eixo !== eixoAtual){ html += `<div class="bncc-eixo">${esc(eixo)}</div>`; eixoAtual = eixo; }
      const on = sel.includes(h.c);
      html += `<label class="bncc-item ${on?"on":""}">
        <input type="checkbox" value="${h.c}" ${on?"checked":""}>
        <span><code>${h.c}</code> ${esc(h.t)}</span></label>`;
    });
    caixa.innerHTML = html;
    caixa.querySelectorAll('input[type="checkbox"]').forEach(cb=>{
      cb.addEventListener("change", ()=>{
        const lista = bnccSel[g.id];
        const i = lista.indexOf(cb.value);
        if(cb.checked && i < 0) lista.push(cb.value);
        if(!cb.checked && i >= 0) lista.splice(i,1);
        cb.closest(".bncc-item").classList.toggle("on", cb.checked);
        atualizaContadorBNCC(g);
        if(gerado[g.id]) render();
      });
    });
  }
  atualizaContadorBNCC(g);
}

function atualizaContadorBNCC(g){
  const etapa = etapaEfetiva(g);
  const n = (bnccSel[g.id]||[]).length;
  const cont = document.getElementById("bncc-cont");
  const nota = document.getElementById("bncc-nota");
  if(cont) cont.textContent = n ? n + (n===1 ? " habilidade marcada" : " habilidades marcadas") : "nenhuma marcada";
  if(nota){
    nota.textContent = !etapa
      ? "Sem a etapa, o prompt pede que a IA pergunte o ano antes de produzir — para não inventar códigos."
      : (n ? "O prompt vai exigir que a produção contemple essas habilidades, com o código marcado em cada parte."
           : "Sem marcar nada, o prompt leva todas as " + habsDaEtapa(etapa).length + " habilidades da etapa e pede que a IA escolha de 2 a 4 e justifique.");
  }
}

function ligarBNCC(g){
  const selEtapa = document.getElementById("bncc-etapa");
  if(!selEtapa) return;
  const auto = etapaDoFormulario(g);
  selEtapa.innerHTML = `<option value="">${auto ? "Etapa do formulário: " + auto : "— escolha a etapa —"}</option>`
    + BNCC_ETAPAS.map(e=>`<option value="${esc(e)}">${esc(e)}</option>`).join("");
  selEtapa.value = bnccManual[g.id] ? (bnccEtapa[g.id] || "") : "";
  selEtapa.addEventListener("change", ()=>{
    bnccEtapa[g.id] = selEtapa.value;
    bnccManual[g.id] = !!selEtapa.value;
    bnccSel[g.id] = [];
    listaBNCC(g);
    if(gerado[g.id]) render();
  });
  document.getElementById("bncc-busca").addEventListener("input", ()=>listaBNCC(g));
  listaBNCC(g);
}

function sincronizarBNCC(){
  if(!atual || !atual.campos) return;
  if(bnccManual[atual.id]) return;
  const selEtapa = document.getElementById("bncc-etapa");
  if(!selEtapa) return;
  const auto = etapaDoFormulario(atual);
  selEtapa.options[0].textContent = auto ? "Etapa do formulário: " + auto : "— escolha a etapa —";
  listaBNCC(atual);
}

function blocoBNCC(id){
  const g = GERADORES.find(x=>x.id===id);
  if(!g) return "";
  const etapa = etapaEfetiva(g);
  const marcadas = (bnccSel[id]||[]).map(c=>BNCC_HAB.find(h=>h.c===c)).filter(Boolean);

  let b = "\n\n==================================================\nBNCC DE COMPUTAÇÃO — ALINHAMENTO OBRIGATÓRIO\n"
        + "Esta produção deve estar alinhada ao Complemento à BNCC — Computação (Resolução CNE/CEB nº 1/2022).";

  if(!etapa){
    return b + "\n\nO professor ainda não indicou a etapa de ensino. Antes de produzir qualquer coisa, pergunte qual é a etapa "
      + "(Educação Infantil, qual ano do Ensino Fundamental ou Ensino Médio) e quais habilidades de Computação devem ser contempladas. "
      + "Não cite nenhum código da BNCC de Computação sem ter em mãos o texto oficial correspondente — nunca invente códigos.";
  }

  const comp = competenciasDaEtapa(etapa);
  const lista = marcadas.length ? marcadas : habsDaEtapa(etapa);
  b += "\n\nETAPA: " + etapa;
  b += "\n\n" + comp.rotulo.toUpperCase() + "\n" + comp.itens.map((x,i)=>(i+1) + ". " + x).join("\n");
  b += "\n\nHABILIDADES QUE A PRODUÇÃO DEVE CONTEMPLAR\n"
     + lista.map(h=>"- (" + h.c + ")" + (h.x ? " [" + h.x + "]" : "") + " " + h.t).join("\n");
  if(!marcadas.length){
    b += "\n\nO professor não marcou habilidades específicas. Escolha de 2 a 4 habilidades da lista acima que façam sentido para esta produção e justifique a escolha logo no início.";
  }
  b += "\n\nCOMO INCORPORAR"
     + "\n1. Comece a resposta com um quadro “BNCC de Computação”, com uma linha por habilidade contemplada: código, eixo e a descrição completa, copiados exatamente como estão acima."
     + "\n2. Dentro da produção, marque entre colchetes o código da habilidade mobilizada em cada parte — etapa da aula, questão, atividade, critério de avaliação. Exemplo: [EF06CO04]."
     + "\n3. Para cada habilidade, escreva a evidência observável de que o estudante a desenvolveu."
     + "\n4. Feche relacionando as habilidades contempladas às competências da etapa listadas acima."
     + "\n\nREGRAS DESTE BLOCO"
     + "\n- Use somente os códigos e os textos fornecidos acima, sem alterar uma palavra. Não invente, não adapte e não arredonde códigos."
     + "\n- Se alguma habilidade não puder ser contemplada com honestidade nesta produção, diga isso em vez de forçar o encaixe."
     + "\n- A Computação entra integrada ao conteúdo do componente curricular: não transforme a produção em aula de informática.";
  return b;
}

const ICONES = {
  Planejar:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="17" rx="2"/><path d="M8 2v4M16 2v4M3 10h18"/></svg>',
  Atividades:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 3h11l5 5v13H4z"/><path d="M15 3v5h5M8 13h8M8 17h5"/></svg>',
  Avaliar:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 11l3 3 6-6"/><rect x="3" y="3" width="18" height="18" rx="2"/></svg>',
  Engajar:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 3l2.4 5.2 5.6.7-4.1 3.9 1.1 5.6L12 15.8 6.999 18.4 8.1 12.8 4 8.9l5.6-.7z"/></svg>',
  Pesquisar:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="7"/><path d="M20 20l-4.3-4.3"/></svg>',
  Materiais:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h7a3 3 0 0 1 3 3v13a2.5 2.5 0 0 0-2.5-2.5H4z"/><path d="M20 4h-3a3 3 0 0 0-3 3v13a2.5 2.5 0 0 1 2.5-2.5H20z"/></svg>',
  Comunicar:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H8l-5 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>',
  Tecnologia:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M8 8l-4 4 4 4M16 8l4 4-4 4M14 4l-4 16"/></svg>',
  Guias:'<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="9"/><path d="M12 17v-5M12 8h.01"/></svg>'
};

const GERADORES = [
{
  id:"plano-aula", grupo:"Planejar", origem:"modelo", nome:"Plano de aula",
  resumo:"Plano completo, com objetivos, etapas cronometradas e avaliação.",
  ias:["chatgpt","claude","gemini","deepseek"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Química", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema da aula", ph:"Reações de esterificação e produção de biodiesel"},
    {id:"dur",  rot:"Duração", tipo:"select", op:["","45 minutos","50 minutos","1 hora","2 aulas de 50 min","90 minutos"], meia:true},
    {id:"obj",  rot:"Objetivo principal", ph:"Ex.: relacionar a reação química ao uso do biodiesel", meia:true},
    {id:"rec",  rot:"Recursos disponíveis", ph:"Quadro, projetor, laboratório, celulares"},
    {id:"turma",rot:"Perfil da turma", tipo:"textarea", ph:"32 alunos, boa parte com dificuldade em cálculo; turma participativa quando há atividade prática.", dica:"Quanto mais específico, melhor o resultado."}
  ],
  prompt:v=>
`Aja como um professor experiente e especialista em planejamento didático, com domínio da BNCC.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema",v.tema)}${L("Duração",v.dur)}${L("Objetivo principal",v.obj)}${L("Recursos disponíveis",v.rec)}${P("PERFIL DA TURMA",v.turma)}

TAREFA
Elabore um plano de aula completo e pronto para aplicar.

FORMATO DA RESPOSTA
1. Objetivo geral (1 frase) e 3 objetivos específicos observáveis (verbo no infinitivo).
2. Conhecimentos prévios necessários.
3. Sequência da aula em etapas, cada uma com tempo estimado: acolhida/problematização, desenvolvimento, sistematização e fechamento.
4. Atividade principal passo a passo, com o que o professor faz e o que os alunos fazem.
5. Recursos e materiais necessários.
6. Avaliação: o que observar e 3 perguntas de verificação de aprendizagem.
7. Adaptação para quem tem mais dificuldade e proposta de aprofundamento.

REGRAS
${REGRAS_BASE}
- A soma dos tempos das etapas deve bater exatamente com a duração informada.
- Não deixe nenhuma etapa sem tempo estimado.`
},
{
  id:"plano-unidade", grupo:"Planejar", origem:"modelo", nome:"Plano de unidade",
  resumo:"Bloco de várias aulas em torno de uma unidade temática do bimestre.",
  ias:["chatgpt","claude","gemini","deepseek"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"História", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Unidade temática", ph:"Brasil República: da Proclamação à Era Vargas"},
    {id:"n",    rot:"Número de aulas", tipo:"number", ph:"10", meia:true},
    {id:"obj",  rot:"Objetos de conhecimento", tipo:"textarea", ph:"Proclamação da República, política do café-com-leite, Revolução de 1930, Estado Novo", dica:"opcional — a IA pode sugerir se deixar em branco"},
    {id:"aval", rot:"Avaliação prevista para a unidade", ph:"Prova bimestral + trabalho em grupo"}
  ],
  prompt:v=>
`Aja como um coordenador pedagógico especialista em planejamento de unidades didáticas alinhadas à BNCC.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Unidade temática",v.tema)}${L("Número de aulas",v.n)}${L("Avaliação prevista",v.aval)}${P("OBJETOS DE CONHECIMENTO",v.obj)}

TAREFA
Estruture um plano de unidade que organize o número de aulas indicado em torno da unidade temática, com progressão clara.

FORMATO DA RESPOSTA
1. Objetivo geral da unidade e habilidades da BNCC mobilizadas.
2. Objetos de conhecimento organizados em blocos, do mais simples ao mais complexo.
3. Distribuição aula a aula: número, foco do dia e objeto de conhecimento trabalhado.
4. Estratégias de ensino previstas para a unidade (ao menos 3, variadas).
5. Momentos de avaliação formativa ao longo da unidade, antes da avaliação final.
6. Descrição da avaliação prevista, com critérios de correção.
7. Recuperação: como retomar o que não foi consolidado.

REGRAS
${REGRAS_BASE}
- O número de aulas do quadro precisa bater exatamente com o número informado.
- Distribua os objetos de conhecimento de forma equilibrada entre as aulas, sem amontoar tudo no fim.`
},
{
  id:"plano-curso", grupo:"Planejar", origem:"novo", nome:"Plano de curso anual",
  resumo:"Planejamento do ano inteiro dividido em bimestres, com objetos de conhecimento e habilidades.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Geografia", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"ch",   rot:"Carga horária semanal", ph:"2 aulas por semana", meia:true},
    {id:"foco", rot:"Eixo ou foco do ano", ph:"Ex.: geografia do Brasil e globalização", meia:true},
    {id:"livro",rot:"Material ou livro didático adotado", ph:"Nome da coleção (opcional)"}
  ],
  prompt:v=>
`Aja como um coordenador pedagógico especialista em planejamento curricular anual alinhado à BNCC.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Carga horária semanal",v.ch)}${L("Eixo do ano",v.foco)}${L("Material adotado",v.livro)}

TAREFA
Construa um plano de curso anual dividido nos 4 bimestres, coerente e com progressão de complexidade.

FORMATO DA RESPOSTA
1. Objetivo geral do ano e competências gerais da BNCC mobilizadas.
2. Quadro por bimestre (1º ao 4º): tema central, objetos de conhecimento e habilidades da BNCC (com código).
3. Justificativa da ordem escolhida entre os bimestres.
4. Marcos de avaliação previstos em cada bimestre.
5. Pontos de possível articulação interdisciplinar em cada bimestre.
6. Datas ou eventos do calendário escolar que pedem atenção (feiras, provas externas, recesso).
7. Sugestão de ajuste caso o ano tenha menos aulas do que o previsto (calendário reduzido).

REGRAS
${REGRAS_BASE}
- Distribua os objetos de conhecimento nos 4 bimestres sem sobrecarregar nenhum deles.
- Avise quando não tiver certeza do código exato de uma habilidade da BNCC; não invente códigos.`
},
{
  id:"sequencia", grupo:"Planejar", origem:"modelo", nome:"Sequência didática",
  resumo:"Aulas encadeadas em torno de um produto final.",
  ias:["chatgpt","claude","gemini","deepseek"],
  campos:[
    {id:"comp",rot:"Componente curricular", tipo:"lista", ph:"Biologia", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema",rot:"Tema central", ph:"Sustentabilidade e combustíveis renováveis"},
    {id:"n",   rot:"Número de aulas", tipo:"number", ph:"6", meia:true},
    {id:"prod",rot:"Produto final", ph:"Feira de ciências, podcast, relatório...", meia:true},
    {id:"aval",rot:"Como pretende avaliar", ph:"Processual, com rubrica e autoavaliação"}
  ],
  prompt:v=>
`Aja como um coordenador pedagógico especialista em sequências didáticas por competências.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema central",v.tema)}${L("Número de aulas",v.n)}${L("Produto final",v.prod)}${L("Avaliação pretendida",v.aval)}

TAREFA
Construa uma sequência didática que leve a turma do primeiro contato com o tema até a entrega do produto final.

FORMATO DA RESPOSTA
1. Justificativa da sequência em 3 a 5 linhas.
2. Competências e habilidades mobilizadas.
3. Quadro aula a aula: número, título, objetivo, atividade central e evidência de aprendizagem.
4. Descrição detalhada da aula de abertura e da aula de fechamento.
5. Orientações para o produto final: critérios, formato de entrega e cronograma.
6. Instrumentos de avaliação processual.

REGRAS
${REGRAS_BASE}
- Garanta progressão real de complexidade entre as aulas.
- O número de aulas do quadro deve bater exatamente com o número informado.`
},
{
  id:"projeto", grupo:"Planejar", origem:"modelo", nome:"Projeto didático",
  resumo:"Projeto (interdisciplinar ou não) a partir de um problema real, com cronograma e produto.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"tema",rot:"Problema ou pergunta do projeto", ph:"Como reduzir o desperdício de óleo de cozinha no nosso bairro?"},
    {id:"comps",rot:"Componentes envolvidos", ph:"Química, Biologia, Matemática (ou só um componente)", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"sem", rot:"Duração", tipo:"select", op:["","2 semanas","1 mês","1 bimestre","1 semestre"], meia:true},
    {id:"prod",rot:"Entrega final", ph:"Protótipo, campanha, feira, artigo, exposição", meia:true}
  ],
  prompt:v=>
`Aja como um coordenador de projetos didáticos em escola de educação básica, especialista em metodologias ativas.

CONTEXTO${L("Componentes envolvidos",v.comps)}${L("Ano/série",v.ano)}${L("Duração",v.sem)}${L("Entrega final",v.prod)}${P("PROBLEMA OU PERGUNTA DO PROJETO",v.tema)}

TAREFA
Desenhe um projeto didático completo, partindo do problema real informado até a entrega final.

FORMATO DA RESPOSTA
1. Pergunta motriz reformulada de forma clara e pergunta desdobrada por componente (se houver mais de um).
2. Objetivos de aprendizagem e habilidades da BNCC mobilizadas.
3. Cronograma semana a semana até a entrega, com marcos de checagem.
4. Papel de cada componente envolvido no desenvolvimento do projeto.
5. Critérios de avaliação do produto final e do processo.
6. Como envolver a comunidade escolar ou externa, se fizer sentido.
7. Riscos comuns do projeto (desmotivação, atraso, grupos desequilibrados) e como preveni-los.

REGRAS
${REGRAS_BASE}
- O cronograma deve caber dentro da duração informada.
- Garanta que o produto final responda de fato à pergunta motriz, não apenas ilustre o tema.`
},
{
  id:"trilha", grupo:"Planejar", origem:"modelo", nome:"Trilha de aprendizagem",
  resumo:"Percurso personalizado por nível do aluno, com etapas, checkpoints e materiais.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Habilidade ou conteúdo alvo", ph:"Resolução de equações do 1º grau"},
    {id:"niveis",rot:"Níveis de partida da turma", ph:"Iniciante (não domina o pré-requisito), intermediário, avançado", dica:"descreva os níveis que existem na turma"},
    {id:"n",    rot:"Número de etapas por nível", tipo:"number", ph:"4", meia:true},
    {id:"rec",  rot:"Recursos disponíveis", ph:"Plataforma adaptativa, fichas impressas, monitoria entre pares", meia:true}
  ],
  prompt:v=>
`Aja como um especialista em personalização do ensino e trilhas de aprendizagem por nível de proficiência.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Habilidade/conteúdo alvo",v.tema)}${L("Etapas por nível",v.n)}${L("Recursos disponíveis",v.rec)}${P("NÍVEIS DE PARTIDA DA TURMA",v.niveis)}

TAREFA
Monte uma trilha de aprendizagem com percursos diferentes para cada nível de partida, convergindo para a mesma habilidade alvo.

FORMATO DA RESPOSTA
1. Diagnóstico rápido: como identificar em qual nível cada aluno está (atividade ou pergunta de sondagem).
2. Trilha para cada nível, com as etapas na ordem, cada uma com objetivo e atividade.
3. Checkpoint ao final de cada etapa: como o aluno mostra que pode avançar.
4. Material ou recurso indicado em cada etapa.
5. Ponto de convergência: atividade final comum a todos os níveis.
6. Como o professor acompanha várias trilhas rodando ao mesmo tempo na sala.

REGRAS
${REGRAS_BASE}
- Cada nível precisa de um ponto de partida realista, não apenas “mais difícil” ou “mais fácil”.
- Os checkpoints devem ser rápidos de aplicar, sem virar uma nova prova.`
},
{
  id:"conteudos", grupo:"Planejar", origem:"modelo", nome:"Conteúdos de aula",
  resumo:"Lista e sequencia os conteúdos de um tema, do pré-requisito ao aprofundamento.",
  ias:["chatgpt","claude","gemini","perplexity"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Física", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema ou assunto", ph:"Leis de Newton"},
    {id:"n",    rot:"Número de aulas disponíveis", tipo:"number", ph:"5", meia:true},
    {id:"base", rot:"O que a turma já sabe", ph:"Já viu conceito de força e vetores, mas nunca aplicou fórmulas", meia:true}
  ],
  prompt:v=>
`Aja como um especialista em currículo e progressão de conteúdos, com domínio profundo desta área do conhecimento.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema",v.tema)}${L("Número de aulas disponíveis",v.n)}${L("O que a turma já sabe",v.base)}

TAREFA
Liste e sequencie os conteúdos necessários para ensinar este tema, do pré-requisito ao aprofundamento.

FORMATO DA RESPOSTA
1. Pré-requisitos indispensáveis — o que precisa estar consolidado antes de começar.
2. Lista de conteúdos em ordem lógica de ensino, numerada.
3. Para cada conteúdo: por que ele vem nessa posição na sequência (o que ele exige do anterior).
4. Erros conceituais comuns dos alunos em cada conteúdo, e como preveni-los.
5. Distribuição sugerida dos conteúdos dentro do número de aulas informado.
6. Conteúdo de aprofundamento opcional, para quem terminar antes.

REGRAS
${REGRAS_BASE}
- A ordem precisa respeitar dependência real entre os conteúdos, não apenas a ordem do livro didático.
- Se o número de aulas for insuficiente para tudo, avise e proponha o que cortar.`
},
{
  id:"bncc", grupo:"Planejar", origem:"modelo", nome:"Habilidades da BNCC",
  resumo:"A partir de um tema e ano, indica habilidades e competências da BNCC relacionadas e como avaliá-las.",
  ias:["chatgpt","claude","gemini","perplexity"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Língua Portuguesa", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema ou atividade planejada", ph:"Produção de texto argumentativo sobre redes sociais"},
    {id:"etapa",rot:"Etapa da educação básica", tipo:"select", op:["","Educação Infantil","Ensino Fundamental","Ensino Médio"], meia:true}
  ],
  prompt:v=>
`Aja como um especialista em currículo com domínio profundo da BNCC (Base Nacional Comum Curricular).

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Etapa",v.etapa)}${P("TEMA OU ATIVIDADE PLANEJADA",v.tema)}

TAREFA
Indique as habilidades e competências da BNCC relacionadas a este tema e ano, e como cada uma pode ser avaliada.

FORMATO DA RESPOSTA
1. Competências gerais da BNCC mobilizadas (liste apenas as realmente pertinentes).
2. Competências específicas da área.
3. Habilidades diretamente relacionadas, cada uma com código e descrição na íntegra.
4. Para cada habilidade: um indicador observável de que o aluno a desenvolveu.
5. Sugestão de instrumento de avaliação para verificar cada habilidade (não precisa ser prova).
6. Habilidades de anos anteriores que servem de pré-requisito, se relevante.

REGRAS
${REGRAS_BASE}
- Avise explicitamente sempre que não tiver certeza do código exato de uma habilidade; nunca invente ou arredonde um código da BNCC.
- Cite o código apenas quando a descrição correspondente também for apresentada, para permitir a conferência.`
},
{
  id:"desc-port", grupo:"Planejar", origem:"modelo", nome:"Descritores SAEB — Português",
  resumo:"Atividades alinhadas a descritores de Língua Portuguesa do SAEB.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"desc",rot:"Descritor do SAEB", ph:"D3 — Inferir o sentido de uma palavra ou expressão", meia:true},
    {id:"tema",rot:"Tema ou gênero textual", ph:"Notícia sobre meio ambiente", meia:true},
    {id:"qtd", rot:"Quantidade de itens", tipo:"number", ph:"5", meia:true},
    {id:"form",rot:"Formato dos itens", tipo:"select", op:["","Múltipla escolha (estilo SAEB)","Resposta curta","Misto"]}
  ],
  prompt:v=>
`Aja como um especialista em avaliação em larga escala, com domínio da matriz de referência de Língua Portuguesa do SAEB.

CONTEXTO${L("Ano/série",v.ano)}${L("Descritor do SAEB",v.desc)}${L("Tema/gênero textual",v.tema)}${L("Quantidade de itens",v.qtd)}${L("Formato dos itens",v.form)}

TAREFA
Elabore itens de Língua Portuguesa alinhados exatamente ao descritor informado, no formato indicado.

FORMATO DA RESPOSTA
1. O que o descritor exige do aluno, em linguagem simples (para o professor conferir o alinhamento).
2. Texto-base apropriado ao tema e ao ano/série, com extensão adequada.
3. Os itens numerados, cada um mobilizando de fato o descritor (nada de itens de outro descritor disfarçado).
4. Em cada item de múltipla escolha: gabarito e uma justificativa curta do porquê cada distrator é plausível, mas incorreto.
5. Nível de dificuldade estimado de cada item (fácil, médio, difícil).
6. Sugestão de como agrupar os itens em uma atividade ou simulado.

REGRAS
${REGRAS_BASE}
- Todos os itens devem ser autocontidos no texto-base fornecido, sem exigir conhecimento externo.
- Não misture mais de um descritor por item.`
},
{
  id:"desc-mat", grupo:"Planejar", origem:"modelo", nome:"Descritores SAEB — Matemática",
  resumo:"Atividades alinhadas a descritores de Matemática do SAEB.",
  ias:["chatgpt","claude","deepseek","gemini"],
  campos:[
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"desc",rot:"Descritor do SAEB", ph:"D20 — Resolver problema com números racionais", meia:true},
    {id:"tema",rot:"Contexto do problema", ph:"Compras, receitas culinárias, orçamento familiar", meia:true},
    {id:"qtd", rot:"Quantidade de itens", tipo:"number", ph:"5", meia:true},
    {id:"form",rot:"Formato dos itens", tipo:"select", op:["","Múltipla escolha (estilo SAEB)","Resposta curta","Misto"]}
  ],
  prompt:v=>
`Aja como um especialista em avaliação em larga escala, com domínio da matriz de referência de Matemática do SAEB.

CONTEXTO${L("Ano/série",v.ano)}${L("Descritor do SAEB",v.desc)}${L("Contexto do problema",v.tema)}${L("Quantidade de itens",v.qtd)}${L("Formato dos itens",v.form)}

TAREFA
Elabore itens de Matemática alinhados exatamente ao descritor informado, contextualizados no cenário indicado.

FORMATO DA RESPOSTA
1. O que o descritor exige do aluno, em linguagem simples (para o professor conferir o alinhamento).
2. Os itens numerados, cada um contextualizado no cenário informado.
3. Em cada item de múltipla escolha: gabarito e a lógica de cálculo de cada distrator (que erro comum ele representa).
4. Resolução passo a passo de cada item, para conferência do professor.
5. Nível de dificuldade estimado de cada item (fácil, médio, difícil).
6. Sugestão de como agrupar os itens em uma atividade ou simulado.

REGRAS
${REGRAS_BASE}
- Confira todos os cálculos e resultados antes de responder; nenhum gabarito pode estar errado.
- Não misture mais de um descritor por item.`
},
{
  id:"quatro-pilares", grupo:"Planejar", origem:"modelo", nome:"Plano dos 4 pilares da educação",
  resumo:"Plano de aula estruturado nos quatro pilares de Delors.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema da aula", ph:"Ecossistemas e cadeia alimentar"},
    {id:"dur",  rot:"Duração", tipo:"select", op:["","45 minutos","50 minutos","90 minutos","2 aulas"], meia:true},
    {id:"foco", rot:"Pilar que merece mais destaque", tipo:"select", op:["","Equilíbrio entre os quatro","Aprender a conhecer","Aprender a fazer","Aprender a conviver","Aprender a ser"], meia:true}
  ],
  prompt:v=>
`Aja como um professor especialista em educação integral, com domínio dos quatro pilares da educação propostos por Jacques Delors.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema",v.tema)}${L("Duração",v.dur)}${L("Pilar em destaque",v.foco)}

TAREFA
Elabore um plano de aula em que cada momento seja claramente associado a um dos quatro pilares: aprender a conhecer, aprender a fazer, aprender a conviver e aprender a ser.

FORMATO DA RESPOSTA
1. Objetivo geral da aula, situando os quatro pilares no contexto do tema.
2. Aprender a conhecer: atividade e conteúdo conceitual trabalhado.
3. Aprender a fazer: atividade prática ou aplicada, com o que o aluno produz.
4. Aprender a conviver: momento de trabalho coletivo ou discussão, com papel de cada aluno.
5. Aprender a ser: momento de reflexão pessoal ou autoavaliação.
6. Distribuição do tempo entre os quatro momentos, batendo com a duração informada.
7. Avaliação que capture indícios dos quatro pilares, não apenas o conteúdo conceitual.

REGRAS
${REGRAS_BASE}
- Cada um dos quatro pilares precisa aparecer em pelo menos um momento explícito da aula.
- A soma dos tempos deve bater exatamente com a duração informada.`
},
{
  id:"plano-fi", grupo:"Planejar", origem:"modelo", nome:"Plano específico para o Fundamental I",
  resumo:"Plano pensado para os anos iniciais: professor polivalente, rotina, alfabetização e ludicidade.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"ano",  rot:"Ano", tipo:"select", op:["","1º ano — Fundamental I","2º ano — Fundamental I","3º ano — Fundamental I","4º ano — Fundamental I","5º ano — Fundamental I"], meia:true},
    {id:"tema", rot:"Tema do dia", ph:"Os animais e seus habitats", meia:true},
    {id:"comps",rot:"Componentes integrados", ph:"Língua Portuguesa, Ciências e Artes", dica:"o professor polivalente costuma integrar mais de um componente no mesmo dia"},
    {id:"alfab",rot:"Fase de alfabetização da turma", tipo:"select", op:["","Não se aplica (turma já alfabetizada)","Pré-silábica","Silábica","Silábico-alfabética","Alfabética","Turma heterogênea"], meia:true},
    {id:"rotina",rot:"Rotina do dia já fixada", tipo:"textarea", ph:"Roda de conversa (15min) + atividade dirigida (40min) + intervalo + leitura deleite (20min)", dica:"opcional — descreva se a escola já tem uma rotina fixa"}
  ],
  prompt:v=>
`Aja como um professor polivalente experiente dos anos iniciais do Ensino Fundamental, especialista em alfabetização e ludicidade.

CONTEXTO${L("Ano",v.ano)}${L("Tema do dia",v.tema)}${L("Componentes integrados",v.comps)}${L("Fase de alfabetização da turma",v.alfab)}${P("ROTINA DO DIA JÁ FIXADA",v.rotina)}

TAREFA
Monte um plano do dia para os anos iniciais, integrando os componentes indicados em torno do tema, respeitando a rotina informada (ou propondo uma, se não houver).

FORMATO DA RESPOSTA
1. Rotina do dia com horários e nome de cada momento (acolhida, roda, atividade dirigida, lúdico, fechamento).
2. Atividade central do dia, passo a passo, com linguagem para o professor usar com a turma.
3. Como cada componente integrado entra dentro do mesmo tema (não como aulas separadas).
4. Pelo menos uma atividade lúdica (jogo, música, movimento) conectada ao tema.
5. Apoio à alfabetização adequado à fase informada da turma, mesmo em componentes fora de Português.
6. Materiais concretos e simples de providenciar (nada que exija recursos caros).
7. Como observar e registrar o desenvolvimento das crianças ao longo do dia.

REGRAS
${REGRAS_BASE}
- Use linguagem lúdica e concreta, adequada à faixa etária informada.
- Nunca peça nome completo de criança; use apenas iniciais nos exemplos de registro.`
},
{
  id:"cultura-paz", grupo:"Planejar", origem:"modelo", nome:"Plano de aula: cultura de paz",
  resumo:"Aula sobre convivência, mediação de conflitos e não violência, partindo de uma situação real da escola.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"tema", rot:"Tema da aula", ph:"Resolução de conflitos na hora do intervalo"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Ensino Religioso, Tutoria, qualquer componente", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"situacao", rot:"Situação real que motivou a aula", tipo:"textarea", ph:"Descreva o que aconteceu, sem citar nomes completos, apenas iniciais", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em cultura de paz, mediação de conflitos e convivência escolar, alinhado às competências socioemocionais da BNCC.

CONTEXTO${L("Tema",v.tema)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${P("SITUAÇÃO QUE MOTIVOU A AULA",v.situacao)}

TAREFA
Crie um plano de aula completo sobre o tema informado, trabalhando cultura de paz e, quando houver, a situação real descrita, sem expor identidades.

FORMATO DA RESPOSTA
1. Objetivo socioemocional da aula
2. Acolhida inicial (roda de conversa ou dinâmica de abertura)
3. Atividade principal de mediação de conflito ou reflexão sobre convivência
4. Momento de escuta e reflexão coletiva
5. Construção de combinados e compromissos da turma
6. Fechamento e forma de avaliar a aprendizagem socioemocional
7. Encaminhamento sugerido para casos que precisem de acompanhamento individual

REGRAS
${REGRAS_BASE}
- Nunca cite nomes completos ou identifique alunos envolvidos na situação; use apenas iniciais ou descrições genéricas.
- Trate qualquer conflito relatado com neutralidade, sem apontar culpados.`
},
{
  id:"primeiro-dia", grupo:"Planejar", origem:"modelo", nome:"1º dia de aula",
  resumo:"Roteiro da primeira aula do ano: acolhida, dinâmica de apresentação, combinados e diagnóstico leve.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"dur", rot:"Duração", tipo:"select", op:["","45 minutos","50 minutos","Aula dupla (90-100 minutos)"], meia:true},
    {id:"obs", rot:"Algo específico da turma ou escola", tipo:"textarea", ph:"Turma nova, turma que já se conhece, escola com pouca estrutura...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor experiente em acolhimento escolar e planejamento do início do ano letivo.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Duração",v.dur)}${P("OBSERVAÇÕES SOBRE A TURMA OU ESCOLA",v.obs)}

TAREFA
Monte um roteiro minuto a minuto para a primeira aula do ano com esse componente curricular e essa turma.

FORMATO DA RESPOSTA
1. Objetivo do primeiro encontro
2. Dinâmica de acolhida e apresentação (com tempo estimado)
3. Apresentação do componente e do que será estudado ao longo do ano
4. Construção coletiva dos combinados de convivência
5. Atividade diagnóstica leve para conhecer a turma, sem caráter de nota
6. Fechamento e expectativas para a próxima aula
7. Lista de materiais necessários

REGRAS
${REGRAS_BASE}
- A atividade diagnóstica deve ser leve e informal, apenas para o professor conhecer o grupo, nunca uma avaliação formal.
- Considere que os alunos podem não se conhecer ainda ou estar se reencontrando após as férias.`
},
{
  id:"invertida", grupo:"Planejar", origem:"modelo", nome:"Sala de aula invertida",
  resumo:"Define o que o aluno estuda antes, o que se faz na aula e um plano B impresso para quem não tem internet.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"tema", rot:"Tema da aula", ph:"Revolução Industrial"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"História", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"turma", rot:"Perfil da turma", tipo:"textarea", ph:"Acesso a internet e dispositivos em casa, hábito de estudo autônomo...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em metodologias ativas, em especial sala de aula invertida.

CONTEXTO${L("Tema",v.tema)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${P("PERFIL DA TURMA",v.turma)}

TAREFA
Crie um plano de sala de aula invertida completo sobre o tema, incluindo uma alternativa impressa para quem não tem acesso à internet em casa.

FORMATO DA RESPOSTA
1. Material de estudo prévio sugerido (vídeo, texto ou podcast) com roteiro de estudo
2. Perguntas-guia para o aluno responder antes da aula
3. Atividade principal em sala aplicando o conteúdo estudado
4. Dinâmica para verificar quem não fez o estudo prévio, sem constranger ninguém
5. Plano B impresso, equivalente ao material digital, para quem não tem internet em casa
6. Fechamento e consolidação do conteúdo
7. Forma de avaliar o que foi aprendido

REGRAS
${REGRAS_BASE}
- Sempre ofereça uma versão impressa equivalente ao material de estudo prévio, pensando em alunos sem internet ou dispositivo em casa.
- A atividade em sala não pode ser mera repetição da exposição do conteúdo; precisa ser aplicação prática.`
},
{
  id:"design-thinking", grupo:"Planejar", origem:"modelo", nome:"Design thinking",
  resumo:"Projeto pelas etapas empatia, definição, ideação, prototipagem e teste, a partir de um desafio real da escola.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"desafio", rot:"Desafio real da escola ou comunidade", ph:"Desperdício de merenda no refeitório"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Projeto de vida, Ciências", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"n", rot:"Número de aulas", tipo:"number", ph:"4", meia:true},
    {id:"dur", rot:"Duração", tipo:"select", op:["","45 minutos","50 minutos"], meia:true}
  ],
  prompt:v=>
`Aja como um professor especialista em design thinking aplicado à educação básica.

CONTEXTO${L("Desafio",v.desafio)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Número de aulas",v.n)}${L("Duração",v.dur)}

TAREFA
Estruture um projeto de design thinking em torno do desafio informado, percorrendo as etapas empatia, definição, ideação, prototipagem e teste.

FORMATO DA RESPOSTA
1. Etapa 1 – Empatia: atividades para os alunos entenderem o problema e ouvirem os afetados
2. Etapa 2 – Definição: como a turma vai formular o problema central a resolver
3. Etapa 3 – Ideação: dinâmica de geração de ideias
4. Etapa 4 – Prototipagem: o que os alunos vão construir ou representar
5. Etapa 5 – Teste: como testar o protótipo e coletar feedback de quem vive o problema
6. Distribuição das etapas ao longo do número de aulas informado
7. Critérios para avaliar o projeto final

REGRAS
${REGRAS_BASE}
- Ligue cada etapa a um desafio real e concreto da escola ou comunidade, evitando exemplos genéricos e distantes da vivência dos alunos.
- Preveja apenas materiais de baixo custo e fáceis de conseguir na escola.`
},
{
  id:"integral", grupo:"Planejar", origem:"modelo", nome:"Educação integral",
  resumo:"Planeja atividade ou oficina para tempo integral/contraturno, articulando as dimensões cognitiva, física, social e emocional.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"atividade", rot:"Nome/tema da oficina ou atividade", ph:"Horta escolar"},
    {id:"eixo", rot:"Eixo temático", tipo:"lista", ph:"Esporte, cultura, tecnologia, meio ambiente", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"dur", rot:"Duração", tipo:"select", op:["","45 minutos","50 minutos","1h30"], meia:true},
    {id:"turma", rot:"Perfil dos alunos no contraturno/tempo integral", tipo:"textarea", ph:"Idades, se já se conhecem, nível de cansaço após o turno regular...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em educação integral e atividades de tempo integral e contraturno escolar.

CONTEXTO${L("Atividade/oficina",v.atividade)}${L("Eixo temático",v.eixo)}${L("Ano/série",v.ano)}${L("Duração",v.dur)}${P("PERFIL DA TURMA",v.turma)}

TAREFA
Planeje a oficina ou atividade de tempo integral articulando as dimensões cognitiva, física, social e emocional dos alunos.

FORMATO DA RESPOSTA
1. Objetivo integrado, cobrindo as quatro dimensões (cognitiva, física, social, emocional)
2. Acolhida e ativação inicial do grupo
3. Atividade principal com a dimensão física/corporal envolvida
4. Momento de trabalho cognitivo ligado ao tema da oficina
5. Dinâmica de interação social entre os alunos
6. Espaço para expressão emocional ou autoconhecimento
7. Fechamento e registro do que foi vivido na oficina

REGRAS
${REGRAS_BASE}
- Garanta que a atividade articule de fato as quatro dimensões, e não apenas uma delas disfarçada de “educação integral”.
- Considere que os alunos já tiveram um turno inteiro de aula e podem estar cansados.`
},
{
  id:"estrategias", grupo:"Planejar", origem:"modelo", nome:"Estratégias de aprendizagem",
  resumo:"Sugere estratégias e metodologias para um conteúdo e uma dificuldade específica da turma, com quando usar cada uma.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"conteudo", rot:"Conteúdo / habilidade", ph:"Interpretação de gráficos e tabelas"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"dificuldade", rot:"Dificuldade específica da turma", tipo:"textarea", ph:"A maioria não relaciona os dados do gráfico com o enunciado do problema"}
  ],
  prompt:v=>
`Aja como um especialista em metodologias e estratégias de aprendizagem para a educação básica brasileira.

CONTEXTO${L("Conteúdo/habilidade",v.conteudo)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${P("DIFICULDADE ESPECÍFICA DA TURMA",v.dificuldade)}

TAREFA
Sugira estratégias de aprendizagem adequadas a esse conteúdo e a essa dificuldade específica, explicando quando usar cada uma.

FORMATO DA RESPOSTA
1. Diagnóstico rápido da provável causa da dificuldade
2. Estratégia 1: passo a passo e quando aplicá-la
3. Estratégia 2: passo a passo e quando aplicá-la
4. Estratégia 3: passo a passo e quando aplicá-la
5. Como adaptar cada estratégia para diferentes ritmos de aprendizagem
6. Sinais de que a estratégia está funcionando
7. Como avaliar se a dificuldade foi superada

REGRAS
${REGRAS_BASE}
- Explique claramente em que situação cada estratégia funciona melhor, não apenas o que ela é.
- Priorize estratégias viáveis com os recursos comuns de uma escola pública brasileira.`
},
{
  id:"temagerador", grupo:"Planejar", origem:"modelo", nome:"Tema gerador (Freire)",
  resumo:"Desenvolve um tema gerador dentro da pedagogia freiriana, partindo da realidade da comunidade dos alunos.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"tema", rot:"Tema gerador", ph:"Água e saneamento no bairro"},
    {id:"etapa", rot:"Etapa a desenvolver", tipo:"select", op:["","Investigação temática","Codificação do tema","Descodificação e diálogo","Problematização e aprofundamento","Ação transformadora","Avaliação do processo","Sequência completa (todas as etapas)"]},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Educação de Jovens e Adultos (EJA)", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"comunidade", rot:"Realidade da comunidade", tipo:"textarea", ph:"Contexto do bairro, do trabalho, das famílias, dos problemas locais ligados ao tema"}
  ],
  prompt:v=>
`Aja como um professor especialista em pedagogia freiriana e no trabalho com temas geradores.

CONTEXTO${L("Tema gerador",v.tema)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${P("REALIDADE DA COMUNIDADE",v.comunidade)}

TAREFA
Desenvolva o tema gerador para a etapa “${v.etapa || "Sequência completa (todas as etapas)"}” da pedagogia freiriana, partindo da realidade da comunidade descrita.

FORMATO DA RESPOSTA
1. Contextualização do tema gerador a partir da realidade da comunidade
2. Investigação temática: como levantar as falas e vivências dos alunos sobre o tema
3. Codificação do tema em uma situação, imagem ou texto que represente essa realidade
4. Descodificação e diálogo: perguntas problematizadoras para a roda de conversa
5. Problematização e aprofundamento do conteúdo formal ligado ao tema
6. Proposta de ação transformadora que a turma pode realizar a partir do que discutiu
7. Forma de avaliar o processo, não apenas o produto final

REGRAS
${REGRAS_BASE}
- Parta do saber que os alunos já trazem sobre o tema antes de apresentar o conteúdo formal.
- Não abra mão do rigor do conteúdo curricular só porque o ponto de partida é a vivência dos alunos.`
},
{
  id:"atividade-mes", grupo:"Planejar", origem:"modelo", nome:"Atividade do mês",
  resumo:"Atividade ligada à data comemorativa ou campanha do mês, com objetivo de aprendizagem real e não decorativo.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"data", rot:"Data comemorativa ou campanha", ph:"Setembro Amarelo, Consciência Negra, Semana da Água..."},
    {id:"mes", rot:"Mês", tipo:"select", op:["","Fevereiro","Março","Abril","Maio","Junho","Julho","Agosto","Setembro","Outubro","Novembro","Dezembro"], meia:true},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Qualquer componente", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"dur", rot:"Duração", tipo:"select", op:["","45 minutos","50 minutos"], meia:true}
  ],
  prompt:v=>
`Aja como um professor especialista em datas comemorativas e campanhas escolares com intencionalidade pedagógica.

CONTEXTO${L("Data/campanha",v.data)}${L("Mês",v.mes)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Duração",v.dur)}

TAREFA
Crie uma atividade ligada a essa data ou campanha com objetivo de aprendizagem claro dentro do componente curricular, evitando atividade meramente decorativa.

FORMATO DA RESPOSTA
1. Objetivo de aprendizagem ligado ao componente curricular, além de “comemorar a data”
2. Conexão entre a data/campanha e o conteúdo curricular do momento
3. Atividade principal com os alunos
4. Produto ou registro que a turma vai gerar
5. Forma de avaliar se o objetivo de aprendizagem foi atingido
6. Sugestão de divulgação ou exposição do resultado na escola
7. Cuidados a ter ao abordar o tema, considerando sua sensibilidade

REGRAS
${REGRAS_BASE}
- A atividade precisa ter objetivo de aprendizagem claro dentro do componente curricular: nada de cartaz ou atividade só decorativa sem propósito pedagógico.
- Trate o tema com sensibilidade, especialmente se envolver saúde mental, racismo ou outros assuntos delicados.`
},
{
  id:"livro-didatico", grupo:"Planejar", origem:"modelo", nome:"Apoio ao livro didático",
  resumo:"A partir do capítulo do livro adotado, gera complemento: o que falta, atividades extras e adaptação à realidade local.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"capitulo", rot:"Capítulo / páginas do livro", ph:"Capítulo 5 – Frações, páginas 80 a 95"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"conteudo", rot:"Texto base", tipo:"textarea", grande:true, ph:"Cole aqui o conteúdo, o índice ou um resumo do capítulo do livro didático"}
  ],
  prompt:v=>
`Aja como um especialista em currículo que ajuda professores a complementar o livro didático adotado pela escola.

CONTEXTO${L("Capítulo/páginas",v.capitulo)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${P("CONTEÚDO DO CAPÍTULO",v.conteudo)}

TAREFA
A partir do conteúdo do capítulo colado, identifique lacunas e proponha um complemento de ensino adaptado à realidade local dos alunos.

FORMATO DA RESPOSTA
1. O que o livro cobre bem nesse capítulo
2. O que o livro não cobre ou trata de forma rasa ou desatualizada
3. Sugestões de atividades extras para preencher essas lacunas
4. Ideias para adaptar os exemplos do livro à realidade local dos alunos
5. Conexões possíveis com outros componentes curriculares ou temas atuais
6. Sugestão de uma atividade avaliativa complementar
7. Materiais de apoio adicionais recomendados

REGRAS
${REGRAS_BASE}
- Baseie-se estritamente no conteúdo colado; não invente que o livro traz algo que não foi informado no texto base.
- Priorize adaptações de baixo custo e fáceis de aplicar em sala.`
},
{
  id:"recursos", grupo:"Planejar", origem:"modelo", nome:"Recursos didáticos",
  resumo:"Sugere vídeos, simuladores, jogos e materiais concretos para um conteúdo, considerando o que a escola tem.",
  ias:["chatgpt","claude","gemini","perplexity"],
  campos:[
    {id:"conteudo", rot:"Conteúdo / tema", ph:"Ciclo da água"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"recursos", rot:"O que a escola tem disponível", tipo:"textarea", ph:"Projetor, poucos computadores, sem internet na sala, laboratório simples...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um curador de recursos didáticos (vídeos, simuladores, jogos e materiais concretos) para a educação básica brasileira.

CONTEXTO${L("Conteúdo/tema",v.conteudo)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${P("O QUE A ESCOLA TEM DISPONÍVEL",v.recursos)}

TAREFA
Sugira recursos didáticos concretos para ensinar esse conteúdo, considerando a infraestrutura disponível na escola.

FORMATO DA RESPOSTA
1. Vídeos ou documentários sugeridos, com tema e duração aproximada
2. Simuladores ou ferramentas interativas
3. Jogos ou dinâmicas com materiais de baixo custo
4. Recursos que funcionam sem internet ou sem projetor
5. Materiais concretos ou manipuláveis para montar em sala
6. Como usar cada recurso dentro da aula, não apenas a lista de nomes
7. Links e endereços citados marcados claramente como “a conferir”

REGRAS
${REGRAS_BASE}
- Marque claramente todo link ou endereço sugerido como “a conferir”, porque endereços podem ser inventados ou estar desatualizados.
- Priorize recursos compatíveis com a infraestrutura informada pelo professor.`
},
{
  id:"recuperacao", grupo:"Planejar", origem:"novo", nome:"Plano de recuperação",
  resumo:"Retomada focada no que não foi aprendido, com diagnóstico rápido, priorização de pré-requisitos e nova avaliação.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"conteudo", rot:"Conteúdo(s) não aprendidos", ph:"Equações do 1º grau"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"n", rot:"Número de aulas de recuperação", tipo:"number", ph:"3", meia:true},
    {id:"dur", rot:"Duração", tipo:"select", op:["","45 minutos","50 minutos"], meia:true},
    {id:"diagnostico", rot:"O que os alunos não conseguem fazer", tipo:"textarea", ph:"Descreva o erro típico ou a habilidade que ainda falta"}
  ],
  prompt:v=>
`Aja como um professor especialista em recuperação da aprendizagem e ensino por priorização de pré-requisitos.

CONTEXTO${L("Conteúdo(s)",v.conteudo)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Número de aulas",v.n)}${L("Duração",v.dur)}${P("DIAGNÓSTICO",v.diagnostico)}

TAREFA
Monte um plano de recuperação focado apenas no que não foi aprendido, priorizando pré-requisitos antes de reavaliar a turma.

FORMATO DA RESPOSTA
1. Diagnóstico rápido para confirmar exatamente o que falta, com atividade ou pergunta-chave
2. Lista de pré-requisitos a retomar, em ordem de prioridade
3. Sequência de atividades de retomada para cada aula
4. Estratégias diferentes das já usadas na aula regular, para não repetir o que não funcionou
5. Critério para saber quando o aluno está pronto para a nova avaliação
6. Modelo e formato da nova avaliação
7. Encaminhamento para quem ainda não atingir o objetivo após a recuperação

REGRAS
${REGRAS_BASE}
- Não repita a mesma explicação e os mesmos exercícios da aula regular; use uma abordagem diferente.
- Priorize os pré-requisitos antes de qualquer conteúdo novo.`
},
{
  id:"atividade", grupo:"Atividades", origem:"modelo", nome:"Atividade",
  resumo:"Atividade pronta para imprimir, no formato e no nível que você pedir.",
  ias:["chatgpt","claude","gemini","deepseek"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema", ph:"Frações"},
    {id:"n",    rot:"Quantidade de questões", tipo:"number", ph:"10", meia:true},
    {id:"fmt",  rot:"Formato das questões", tipo:"select", op:["","Múltipla escolha","Verdadeiro ou falso","Complete as lacunas","Dissertativa curta","Misto"], meia:true},
    {id:"dif",  rot:"Nível de dificuldade", tipo:"select", op:["","Fácil","Médio","Difícil","Progressivo (fácil ao difícil)"]},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Ex.: evitar números negativos, focar em interpretação de enunciado...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor experiente da educação básica brasileira, especialista em elaborar atividades pedagógicas.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Tema",v.tema)}${L("Nível de dificuldade",v.dif)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade completa sobre o tema informado, pronta para ser impressa e aplicada em sala de aula.

FORMATO DA RESPOSTA
1. Um cabeçalho com espaço para data e turma (sem pedir nome completo)
2. Um enunciado breve explicando o que o aluno deve fazer
3. ${v.n||"10"} questões no formato ${v.fmt||"escolhido"}, numeradas e organizadas em ordem crescente de dificuldade
4. Espaço em branco suficiente para o aluno responder cada questão
5. Um gabarito completo ao final, separado por uma linha divisória, com a resposta de cada questão
6. Quando aplicável, uma breve justificativa da resposta correta no gabarito

REGRAS
${REGRAS_BASE}
- Adapte a linguagem e a complexidade ao ano/série informado
- Não repita o mesmo tipo de pergunta em todas as questões, varie a abordagem
- Se “Formato” não for definido, use múltipla escolha com 4 alternativas`
},
{
  id:"alfabetizacao", grupo:"Atividades", origem:"modelo", nome:"Atividade de alfabetização",
  resumo:"Atividade sob medida para a hipótese de escrita da turma, com palavras do universo da criança.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"fase", rot:"Hipótese de escrita da turma", tipo:"select", op:["","Pré-silábica","Silábica sem valor sonoro","Silábica com valor sonoro","Silábico-alfabética","Alfabética"], meia:true},
    {id:"foco", rot:"Foco da atividade", tipo:"select", op:["","Consciência fonológica","Reconhecimento de sílabas","Escrita de palavras","Leitura de frases"], meia:true},
    {id:"tema", rot:"Tema", ph:"Animais da fazenda"},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"n",    rot:"Quantidade de atividades", tipo:"number", ph:"6", meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Ex.: turma gosta de bichos, evitar letras cursivas...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor alfabetizador especialista em psicogênese da língua escrita.

CONTEXTO${L("Ano/série",v.ano)}${L("Hipótese de escrita da turma",v.fase)}${L("Foco da atividade",v.foco)}${L("Tema",v.tema)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade de alfabetização adequada à hipótese de escrita informada, pronta para imprimir.

FORMATO DA RESPOSTA
1. Um cabeçalho simples com espaço para data e turma (sem pedir nome completo)
2. Uma instrução curta e objetiva, com linguagem que a própria criança ou o professor consiga ler em voz alta
3. ${v.n||"6"} atividades práticas relacionadas ao foco escolhido, com espaço para escrever, circular, ligar ou desenhar
4. Descrição em texto das imagens necessárias (para o professor desenhar ou substituir por figuras)
5. Um critério de observação para o professor avaliar se a criança conseguiu realizar a tarefa
6. Uma sugestão de variação mais fácil e outra mais desafiadora, para os dois extremos da turma

REGRAS
${REGRAS_BASE}
- Use apenas palavras do universo da criança (nomes de bichos, brincadeiras, comidas, família), nunca palavras artificiais ou sem sentido
- Respeite exatamente a hipótese de escrita informada, sem pular etapas
- Use letras de forma maiúscula, salvo indicação contrária`
},
{
  id:"matematica", grupo:"Atividades", origem:"modelo", nome:"Atividade de matemática",
  resumo:"Questões de matemática já resolvidas e conferidas antes de chegar até você.",
  ias:["chatgpt","claude","deepseek","gemini"],
  campos:[
    {id:"ano",      rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"conteudo", rot:"Conteúdo", ph:"Frações"},
    {id:"tipo",     rot:"Tipo de item", tipo:"select", op:["","Cálculo direto","Problema contextualizado","Múltipla escolha","Verdadeiro ou falso","Misto"], meia:true},
    {id:"n",        rot:"Quantidade de questões", tipo:"number", ph:"10", meia:true},
    {id:"dif",      rot:"Nível de dificuldade", tipo:"select", op:["","Fácil","Médio","Difícil","Progressivo (fácil ao difícil)"], meia:true},
    {id:"obs",      rot:"Observações", tipo:"textarea", ph:"Ex.: usar apenas números naturais, evitar frações mistas...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor de Matemática da educação básica brasileira, com domínio profundo de resolução de problemas.

CONTEXTO${L("Ano/série",v.ano)}${L("Conteúdo",v.conteudo)}${L("Tipo de item",v.tipo)}${L("Nível de dificuldade",v.dif)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade de matemática sobre o conteúdo informado, pronta para imprimir, com todas as questões já resolvidas e conferidas por você.

FORMATO DA RESPOSTA
1. Um cabeçalho com espaço para data e turma (sem pedir nome completo)
2. Uma breve instrução de como resolver a atividade
3. ${v.n||"10"} questões do tipo ${v.tipo||"escolhido"}, com espaço para o cálculo do aluno
4. Questões organizadas em ordem crescente de dificuldade
5. Um gabarito completo, com o resultado final de cada questão
6. A resolução passo a passo de cada questão, mostrando as contas
7. Uma observação final confirmando que todas as respostas foram conferidas

REGRAS
${REGRAS_BASE}
- Antes de entregar a atividade, resolva cada questão internamente e confira se o resultado bate; corrija qualquer questão cujo resultado não feche
- Use apenas números e operações compatíveis com o ano/série informado
- Na resolução passo a passo, mostre as contas de forma que o professor consiga acompanhar o raciocínio`
},
{
  id:"geometria", grupo:"Atividades", origem:"modelo", nome:"Atividades de geometria",
  resumo:"Questões de geometria com as figuras descritas em texto para o professor desenhar.",
  ias:["chatgpt","claude","deepseek","gemini"],
  campos:[
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tipo", rot:"Conteúdo de geometria", tipo:"select", op:["","Figuras planas","Figuras espaciais","Área","Perímetro","Volume","Ângulos","Misto"], meia:true},
    {id:"n",    rot:"Quantidade de questões", tipo:"number", ph:"8", meia:true},
    {id:"dif",  rot:"Nível de dificuldade", tipo:"select", op:["","Fácil","Médio","Difícil","Progressivo (fácil ao difícil)"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Ex.: usar apenas medidas em centímetros...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor de Matemática especialista em geometria na educação básica brasileira.

CONTEXTO${L("Ano/série",v.ano)}${L("Conteúdo de geometria",v.tipo)}${L("Nível de dificuldade",v.dif)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade de geometria sobre o conteúdo informado, pronta para imprimir, descrevendo cada figura em texto para que o professor consiga desenhá-la à mão ou na lousa.

FORMATO DA RESPOSTA
1. Um cabeçalho com espaço para data e turma (sem pedir nome completo)
2. Uma instrução clara de como resolver a atividade
3. ${v.n||"8"} questões, cada uma com a figura descrita em texto (tipo de figura, medidas dos lados, ângulos ou raio, conforme o caso) para o professor desenhar
4. Espaço para o aluno fazer os cálculos
5. Um gabarito com o resultado numérico de cada questão
6. A fórmula usada e a resolução passo a passo de cada questão

REGRAS
${REGRAS_BASE}
- Descreva cada figura em texto de forma que o professor consiga reproduzi-la sem precisar de imagem, informando todas as medidas necessárias
- Use unidades de medida coerentes com o ano/série (cm, m, cm², m², cm³, graus)
- Varie os tipos de figura ao longo da atividade, sem repetir a mesma forma em todas as questões`
},
{
  id:"problemas-mat", grupo:"Atividades", origem:"modelo", nome:"Problemas de matemática",
  resumo:"Situações-problema do cotidiano do aluno, com raciocínio explicado passo a passo.",
  ias:["chatgpt","claude","deepseek","gemini"],
  campos:[
    {id:"ano",      rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"conteudo", rot:"Conteúdo", tipo:"lista", ph:"Regra de três", meia:true},
    {id:"contexto", rot:"Contexto do problema", tipo:"select", op:["","Feira","Transporte","Roça / lavoura","Mercado","Outro"], meia:true},
    {id:"n",        rot:"Quantidade de problemas", tipo:"number", ph:"6", meia:true},
    {id:"dif",      rot:"Nível de dificuldade", tipo:"select", op:["","Fácil","Médio","Difícil","Progressivo (fácil ao difícil)"]},
    {id:"obs",      rot:"Observações", tipo:"textarea", ph:"Ex.: usar nomes de frutas da região, valores em reais...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor de Matemática especialista em resolução de problemas contextualizados na realidade brasileira.

CONTEXTO${L("Ano/série",v.ano)}${L("Conteúdo",v.conteudo)}${L("Contexto do problema",v.contexto)}${L("Nível de dificuldade",v.dif)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie problemas matemáticos contextualizados no cotidiano do aluno, com o raciocínio de resolução explicado passo a passo.

FORMATO DA RESPOSTA
1. Um cabeçalho com espaço para data e turma (sem pedir nome completo)
2. ${v.n||"6"} situações-problema ambientadas no contexto informado, com nomes fictícios simples
3. Cada problema com espaço para o aluno registrar seu raciocínio e o cálculo
4. Um gabarito com a resposta final de cada problema
5. A resolução comentada de cada problema, explicando cada etapa do raciocínio em linguagem simples
6. Uma dica de estratégia (desenho, tabela, esquema) para os alunos que têm dificuldade em interpretar o enunciado

REGRAS
${REGRAS_BASE}
- Ambiente os problemas em situações realistas e próximas da vida do aluno, evitando contextos distantes da sua realidade
- Na resolução comentada, explique o porquê de cada etapa, não apenas o cálculo
- Use valores numéricos plausíveis (preços, distâncias, quantidades) para o contexto escolhido`
},
{
  id:"ingles", grupo:"Atividades", origem:"modelo", nome:"Atividade de inglês",
  resumo:"Atividade de inglês com enunciados em português, conteúdo em inglês e glossário.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"habilidade", rot:"Habilidade trabalhada", tipo:"select", op:["","Reading","Listening","Speaking","Writing","Vocabulary","Grammar"], meia:true},
    {id:"nivel",       rot:"Nível (CEFR)", tipo:"select", op:["","A1","A2","B1","B2"], meia:true},
    {id:"ano",         rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"n",           rot:"Quantidade de palavras/itens", tipo:"number", ph:"8", meia:true},
    {id:"tema",        rot:"Tema", ph:"Family and daily routine"},
    {id:"obs",         rot:"Observações", tipo:"textarea", ph:"Ex.: turma iniciante, evitar phrasal verbs...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor de Língua Inglesa da educação básica brasileira, especialista em ensino comunicativo de idiomas.

CONTEXTO${L("Ano/série",v.ano)}${L("Habilidade trabalhada",v.habilidade)}${L("Nível (CEFR)",v.nivel)}${L("Tema",v.tema)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade de inglês pronta para imprimir, com os enunciados em português e o conteúdo (textos, frases, exercícios) em inglês.

FORMATO DA RESPOSTA
1. Um cabeçalho com espaço para data e turma (sem pedir nome completo)
2. Um pequeno glossário inicial com ${v.n||"8"} palavras-chave do tema, em inglês, com tradução e um exemplo de frase
3. Um texto, diálogo ou conjunto de frases em inglês, no nível ${v.nivel||"informado"}, trabalhando a habilidade de ${v.habilidade||"escolhida"}
4. Exercícios em português orientando o que fazer com o conteúdo em inglês (responder, completar, ligar, marcar)
5. Espaço para o aluno responder
6. Um gabarito completo ao final

REGRAS
${REGRAS_BASE}
- Escreva os enunciados e instruções em português; mantenha o conteúdo a ser trabalhado (textos, frases, vocabulário) em inglês
- Sempre inclua a tradução das palavras novas no glossário
- Ajuste o vocabulário e a complexidade das frases ao nível CEFR informado`
},
{
  id:"vocabulario", grupo:"Atividades", origem:"modelo", nome:"Vocabulário",
  resumo:"Lista de palavras de um tema com significado, exemplo em frase e atividades de fixação.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"lingua", rot:"Língua", tipo:"select", op:["","Português","Inglês","Espanhol","Outra"], meia:true},
    {id:"tema",   rot:"Tema", ph:"Meios de transporte", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"n",      rot:"Quantidade de palavras", tipo:"number", ph:"10", meia:true},
    {id:"obs",    rot:"Observações", tipo:"textarea", ph:"Ex.: incluir palavras usadas na região...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor de Língua Portuguesa (ou de idiomas, conforme indicado) especialista em ensino de vocabulário.

CONTEXTO${L("Ano/série",v.ano)}${L("Língua",v.lingua)}${L("Tema",v.tema)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade de vocabulário sobre o tema informado, pronta para imprimir, com lista de palavras e exercícios de fixação.

FORMATO DA RESPOSTA
1. Um cabeçalho com espaço para data e turma (sem pedir nome completo)
2. Uma lista com ${v.n||"10"} palavras relacionadas ao tema, cada uma com significado simples e um exemplo de uso em frase
3. Uma breve instrução de como usar a lista nas atividades seguintes
4. Três atividades de fixação variadas (por exemplo: completar frases, relacionar palavra e significado, escrever frases próprias) usando as palavras da lista
5. Espaço para o aluno responder cada atividade
6. Um gabarito completo ao final

REGRAS
${REGRAS_BASE}
- Escolha palavras adequadas ao ano/série e ao tema informados, na língua indicada
- Os significados devem ser explicados em linguagem simples e os exemplos devem ser frases completas e claras
- Varie os tipos de exercício de fixação, sem repetir o mesmo formato em todos eles`
},
{
  id:"compreensao", grupo:"Atividades", origem:"modelo", nome:"Compreensão de texto",
  resumo:"Perguntas de compreensão em níveis a partir de um texto colado, com gabarito comentado.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"ano", rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"n",   rot:"Quantidade de perguntas", tipo:"number", ph:"8", meia:true},
    {id:"txt", rot:"Texto base", tipo:"textarea", grande:true, ph:"Cole aqui o texto que os alunos vão ler..."},
    {id:"obs", rot:"Observações", tipo:"textarea", ph:"Ex.: incluir uma pergunta sobre o vocabulário do texto...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor de Língua Portuguesa especialista em compreensão e interpretação de texto.

CONTEXTO${L("Ano/série",v.ano)}${P("TEXTO BASE",v.txt)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
A partir do texto colado, crie perguntas de compreensão em diferentes níveis de leitura, prontas para imprimir.

FORMATO DA RESPOSTA
1. Um cabeçalho com espaço para data e turma (sem pedir nome completo)
2. Uma breve instrução pedindo para o aluno ler o texto com atenção antes de responder
3. ${v.n||"8"} perguntas organizadas em quatro blocos: localizar informação explícita, inferir informação implícita, relacionar partes do texto (ou o texto com outros conhecimentos) e opinar/posicionar-se sobre o texto
4. Espaço para o aluno responder cada pergunta
5. Um gabarito comentado, indicando o trecho do texto que sustenta cada resposta (exceto nas perguntas de opinião)

REGRAS
${REGRAS_BASE}
- Toda pergunta, exceto as de opinião, precisa ser respondível apenas com base no texto fornecido, sem exigir conhecimento externo
- Não invente informações que não estejam no texto
- Distribua as perguntas de forma equilibrada entre os quatro níveis de leitura`
},
{
  id:"texto-literario", grupo:"Atividades", origem:"modelo", nome:"Texto literário",
  resumo:"Texto literário para leitura em sala, com roteiro de análise e proposta de produção.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"genero", rot:"Gênero literário", tipo:"select", op:["","Conto","Poema","Cordel","Crônica","Fábula","Outro"], meia:true},
    {id:"tema",   rot:"Tema", ph:"Amizade e diferenças", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"ext",    rot:"Extensão", tipo:"select", op:["","Curto","Médio","Longo"], meia:true},
    {id:"obs",    rot:"Observações", tipo:"textarea", ph:"Ex.: ambientar a história em uma cidade do interior...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor de Língua Portuguesa e Literatura, especialista em leitura literária na educação básica brasileira.

CONTEXTO${L("Ano/série",v.ano)}${L("Gênero literário",v.genero)}${L("Tema",v.tema)}${L("Extensão",v.ext)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Produza um texto literário original no gênero indicado para leitura em sala, junto com um roteiro de análise e uma proposta de produção textual.

FORMATO DA RESPOSTA
1. O texto literário completo (${v.genero||"gênero escolhido"}), com título, adequado ao ano/série e ao tema informados
2. Um pequeno glossário com palavras que possam ser difíceis para a turma
3. Um roteiro de análise com 5 a 6 perguntas sobre elementos do texto (personagens, cenário, conflito, linguagem, sentimentos, mensagem)
4. Espaço para o aluno responder ao roteiro de análise
5. Uma proposta de produção textual inspirada no texto lido, com instrução clara do que o aluno deve escrever
6. Um critério simples de avaliação da produção textual, em 3 a 4 itens

REGRAS
${REGRAS_BASE}
- O texto literário deve ser original, coerente com o gênero pedido e apropriado para a faixa etária da turma
- Evite temas sensíveis sem contextualização pedagógica adequada
- O roteiro de análise deve explorar tanto o conteúdo quanto a linguagem do texto`
},
{
  id:"texto-apoio", grupo:"Atividades", origem:"modelo", nome:"Texto de apoio",
  resumo:"Texto explicativo no nível de leitura da turma, com box de curiosidade e glossário.",
  ias:["claude","chatgpt","gemini","perplexity"],
  campos:[
    {id:"tema", rot:"Tema", ph:"O ciclo da água", meia:true},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"ext",  rot:"Extensão", tipo:"select", op:["","Curto","Médio","Longo"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Ex.: relacionar o tema com a realidade local...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em produzir materiais didáticos de apoio para a educação básica brasileira.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Tema",v.tema)}${L("Extensão",v.ext)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Produza um texto de apoio explicativo sobre o tema informado, no nível de leitura da turma, pronto para ser entregue impresso.

FORMATO DA RESPOSTA
1. Um título chamativo e um pequeno subtítulo
2. O texto explicativo principal, dividido em parágrafos curtos e com linguagem adequada ao ano/série
3. Um box de “Você sabia?” com uma curiosidade relacionada ao tema
4. Um glossário ao final com as palavras mais difíceis do texto, explicadas de forma simples
5. Duas ou três perguntas de verificação de leitura ao final do texto

REGRAS
${REGRAS_BASE}
- Use linguagem clara e frases curtas, compatíveis com o nível de leitura do ano/série informado
- Baseie o conteúdo em informações corretas e atualizadas sobre o tema
- O box de curiosidade deve trazer uma informação realmente interessante, não uma repetição do texto principal`
},
{
  id:"resumos", grupo:"Atividades", origem:"modelo", nome:"Resumos",
  resumo:"Resumo de um conteúdo ou de um texto colado, no formato que você escolher.",
  ias:["claude","chatgpt","gemini","notebooklm"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"História", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"fmt",  rot:"Formato do resumo", tipo:"select", op:["","Tópicos","Esquema","Quadro","Resumo corrido","Fichamento"], meia:true},
    {id:"ext",  rot:"Tamanho", tipo:"select", op:["","Curto","Médio","Longo"], meia:true},
    {id:"tema", rot:"Tema ou conteúdo", ph:"Segunda Guerra Mundial"},
    {id:"txt",  rot:"Texto a resumir", tipo:"textarea", grande:true, ph:"Cole aqui o texto a resumir (deixe em branco para resumir o tema informado acima)..."}
  ],
  prompt:v=>
`Aja como um professor especialista em organizar e sintetizar conteúdos para estudo.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Tema ou conteúdo",v.tema)}${L("Formato do resumo",v.fmt)}${L("Tamanho",v.ext)}${P("TEXTO A RESUMIR",v.txt)}

TAREFA
Produza um resumo do conteúdo ou do texto informado, no formato escolhido, pronto para o aluno estudar.

FORMATO DA RESPOSTA
1. Um título indicando o conteúdo resumido
2. O resumo em si, organizado no formato ${v.fmt||"escolhido"} (tópicos, esquema, quadro, resumo corrido ou fichamento)
3. Destaque (em negrito ou marcadores) para os termos e conceitos mais importantes
4. Uma lista final com 3 a 5 pontos-chave que o aluno não pode esquecer
5. Quando fizer sentido para o formato, use subtítulos para separar as partes do conteúdo

REGRAS
${REGRAS_BASE}
- Se um texto for colado, baseie o resumo apenas nele; se não houver texto colado, resuma o tema/conteúdo informado com base no currículo do ano/série
- Mantenha o resumo fiel ao conteúdo original, sem adicionar informações que não fazem parte dele
- Ajuste o nível de detalhe ao tamanho escolhido (curto, médio ou longo)`
},
{
  id:"quadro-comp", grupo:"Atividades", origem:"modelo", nome:"Quadro comparativo",
  resumo:"Compara dois ou mais conceitos, autores, períodos ou processos em uma tabela.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp",      rot:"Componente curricular", tipo:"lista", ph:"Geografia", meia:true},
    {id:"ano",       rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"itens",     rot:"Itens a comparar", ph:"Clima equatorial, clima tropical, clima temperado"},
    {id:"criterios", rot:"Critérios de comparação", tipo:"textarea", ph:"Ex.: localização, temperatura, chuvas, vegetação...", dica:"opcional — a IA define os critérios se deixar em branco"}
  ],
  prompt:v=>
`Aja como um professor especialista em organizar conteúdos comparativos para estudo.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Itens a comparar",v.itens)}${P("CRITÉRIOS DE COMPARAÇÃO",v.criterios)}

TAREFA
Crie um quadro comparativo entre os itens informados, pronto para o aluno estudar ou completar.

FORMATO DA RESPOSTA
1. Um título indicando o que está sendo comparado
2. Uma tabela em formato de texto, com os itens comparados nas colunas e os critérios de comparação nas linhas
3. Se nenhum critério for informado, defina de 4 a 6 critérios relevantes para a comparação
4. Cada célula da tabela preenchida com uma explicação breve e objetiva
5. Um parágrafo final de síntese, destacando a principal diferença e a principal semelhança entre os itens
6. Uma versão da tabela em branco (só com os critérios preenchidos), para o aluno completar como exercício

REGRAS
${REGRAS_BASE}
- Use critérios de comparação claros e aplicáveis a todos os itens comparados
- Mantenha as explicações de cada célula curtas e objetivas, evitando parágrafos longos dentro da tabela
- Garanta que a tabela fique legível mesmo em formato de texto simples (use | ou alinhamento por linhas)`
},
{
  id:"linha-tempo", grupo:"Atividades", origem:"modelo", nome:"Linha do tempo",
  resumo:"Linha do tempo de um processo histórico ou científico, com marcos e datas.",
  ias:["chatgpt","claude","gemini","perplexity"],
  campos:[
    {id:"tema",   rot:"Tema ou processo", ph:"Revolução Industrial"},
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"História", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"n",      rot:"Quantidade de marcos", tipo:"number", ph:"8", meia:true},
    {id:"formato",rot:"Formato da linha do tempo", tipo:"select", op:["","Lista cronológica","Tabela","Código Mermaid (diagrama)","Instruções para montar no mural"], meia:true},
    {id:"obs",    rot:"Observações", tipo:"textarea", ph:"Focar no período pós-1870; incluir personagens locais.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em construir linhas do tempo didáticas para a sala de aula.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Quantidade de marcos",v.n)}${L("Formato de saída",v.formato)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Monte uma linha do tempo sobre “${v.tema||"o tema informado"}”, com os marcos mais importantes do processo.

FORMATO DA RESPOSTA
1. Lista dos marcos, em ordem cronológica, cada um com data (ou período) e uma frase curta do que aconteceu.
2. Para cada marco, uma frase explicando por que ele importa para entender o processo como um todo.
3. As datas que são consenso e as que variam entre fontes ou são aproximadas, marcadas explicitamente como “[conferir]”.
4. A linha do tempo no formato pedido (lista cronológica, tabela, código Mermaid ou instruções de montagem no mural).
5. Uma sugestão de como os alunos podem interagir com a linha do tempo (registrar, comparar, completar).
6. Duas perguntas para os alunos pensarem sobre a relação entre os marcos, não só decorá-los.

REGRAS
${REGRAS_BASE}
- Marque com “[conferir]” toda data que possa estar imprecisa ou que varie entre fontes — o professor precisa validar antes de usar.
- Não invente marco que não seja amplamente reconhecido pelas fontes históricas ou científicas do tema.`
},
{
  id:"bibliografia", grupo:"Atividades", origem:"modelo", nome:"Bibliografia",
  resumo:"Referências e sugestões de leitura sobre um tema, formatadas em ABNT.",
  ias:["perplexity","gemini","chatgpt","claude"],
  campos:[
    {id:"tema",  rot:"Tema da pesquisa", ph:"Letramento racial na escola"},
    {id:"comp",  rot:"Componente curricular", tipo:"lista", ph:"Língua Portuguesa", meia:true},
    {id:"nivel", rot:"Nível / público", tipo:"select", op:ANOS, meia:true},
    {id:"n",     rot:"Quantidade de referências", tipo:"number", ph:"6", meia:true},
    {id:"tipo",  rot:"Tipo de fonte", tipo:"select", op:["","Livros","Artigos acadêmicos","Livros e artigos","Vídeos e livros","Qualquer fonte confiável"], meia:true},
    {id:"obs",   rot:"Observações", tipo:"textarea", ph:"Priorizar autores brasileiros; incluir pelo menos uma fonte de acesso gratuito.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um bibliotecário e pesquisador especialista em levantamento bibliográfico para professores da educação básica.

CONTEXTO${L("Componente curricular",v.comp)}${L("Nível/público",v.nivel)}${L("Quantidade de referências",v.n)}${L("Tipo de fonte",v.tipo)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Monte uma lista de referências e sugestões de leitura sobre “${v.tema||"o tema informado"}”, formatadas em ABNT.

FORMATO DA RESPOSTA
1. Cada referência completa, em formato ABNT (autor, título, editora, ano etc.).
2. Um resumo de 1 a 2 linhas do que cada obra traz sobre o tema.
3. Para cada referência, um grau de certeza — “Confirmo que existe”, “Provavelmente existe, mas não tenho certeza dos detalhes” ou “Posso estar confundindo com outra obra”.
4. Uma sugestão de por onde começar, caso o professor só possa ler uma delas.
5. Um aviso claro de que toda referência precisa ser conferida pelo professor antes de ser usada.

REGRAS
${REGRAS_BASE}
- Nunca invente uma referência: indique apenas obras que você tem razoável confiança de que existem.
- Marque o grau de certeza de cada referência, item por item — não generalize apenas no final.
- Avise explicitamente que modelos de IA podem inventar referências (“alucinação”) e que cada uma precisa ser conferida antes de ir para um plano de aula ou material entregue aos alunos.`
},
{
  id:"edinfantil", grupo:"Atividades", origem:"modelo", nome:"Atividade de Educação Infantil",
  resumo:"Atividade lúdica organizada pelos campos de experiência da BNCC.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"nivel",   rot:"Nível", tipo:"select", op:["","Berçário","Maternal","G4 (4 anos)","G5 (5 anos)"], meia:true},
    {id:"campo",   rot:"Campo de experiência", tipo:"select", op:["","O eu, o outro e o nós","Corpo, gestos e movimentos","Traços, sons, cores e formas","Escuta, fala, pensamento e imaginação","Espaços, tempos, quantidades, relações e transformações"], meia:true},
    {id:"tema",    rot:"Tema", ph:"Os bichos do quintal"},
    {id:"objetivo",rot:"Objetivo da atividade", ph:"Explorar texturas e nomear animais"},
    {id:"materiais",rot:"Materiais disponíveis", ph:"Caixa de papelão, tinta, potes", meia:true},
    {id:"duracao", rot:"Duração", tipo:"select", op:["","15 minutos","30 minutos","45 minutos","1 hora","Ao longo da semana"], meia:true}
  ],
  prompt:v=>
`Aja como um professor de Educação Infantil especialista na Base Nacional Comum Curricular (BNCC) e em aprendizagem pelo brincar.

CONTEXTO${L("Nível",v.nivel)}${L("Campo de experiência",v.campo)}${L("Objetivo",v.objetivo)}${L("Materiais disponíveis",v.materiais)}${L("Duração",v.duracao)}

TAREFA
Crie uma atividade sobre “${v.tema||"o tema informado"}” para essa turma.

FORMATO DA RESPOSTA
1. Nome da atividade e o campo de experiência da BNCC trabalhado.
2. Objetivo de aprendizagem, em termos observáveis para essa faixa etária.
3. Lista de materiais, com alternativas caso a escola não tenha algum deles.
4. Passo a passo da atividade, com o que o professor faz e diz em cada etapa.
5. Como organizar o espaço e o tempo (roda, cantos, pátio, mesa).
6. O que observar em cada criança durante a atividade (um registro de observação, não uma prova).
7. Uma variação para o dia em que algo não sair como o planejado.

REGRAS
${REGRAS_BASE}
- Segurança em primeiro lugar: para Berçário e Maternal, não sugira peça pequena, solta ou que caiba na boca.
- A atividade principal precisa ser a criança fazendo, tocando, experimentando — não assistindo passivamente.
- Não proponha folha para colorir como atividade principal; se usar desenho, ele vem depois de uma experiência concreta.`
},
{
  id:"creche", grupo:"Atividades", origem:"modelo", nome:"Atividades de creche",
  resumo:"Experiências sensoriais e de vínculo para bebês e crianças bem pequenas.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"faixa",   rot:"Faixa etária", tipo:"select", op:["","0 a 6 meses","6 a 12 meses","1 a 2 anos","2 a 3 anos"], meia:true},
    {id:"tipo",    rot:"Tipo de experiência", tipo:"select", op:["","Sensorial (texturas, sons, cheiros)","Vínculo e acolhimento","Movimento e exploração do corpo","Rotina e cuidado (troca, sono, alimentação)","Música e sons","Faz de conta inicial"], meia:true},
    {id:"n",       rot:"Quantidade de bebês/crianças", tipo:"number", ph:"6", meia:true},
    {id:"duracao", rot:"Duração", tipo:"select", op:["","10 minutos","20 minutos","30 minutos","Ao longo da rotina do dia"], meia:true},
    {id:"materiais",rot:"Materiais disponíveis", ph:"Panos, potes, bolas sensoriais, caixa de papelão"},
    {id:"obs",     rot:"Observações", tipo:"textarea", ph:"Uma criança tem restrição alimentar; berçário com 6 bebês e 1 professora.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor de creche especialista em educação infantil para bebês e crianças bem pequenas (0 a 3 anos).

CONTEXTO${L("Faixa etária",v.faixa)}${L("Tipo de experiência",v.tipo)}${L("Quantidade de bebês/crianças",v.n)}${L("Duração",v.duracao)}${L("Materiais disponíveis",v.materiais)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Proponha uma experiência para essa turma de creche.

FORMATO DA RESPOSTA
1. Nome da experiência e o que ela desenvolve (vínculo, sentidos, corpo, linguagem).
2. Materiais, com o cuidado de higienização de cada um antes e depois do uso.
3. Como organizar o espaço, incluindo onde o professor se posiciona para acompanhar de perto.
4. Passo a passo, respeitando o ritmo de cada bebê — não é preciso que todos façam ao mesmo tempo.
5. O que o professor fala e como sustenta o vínculo durante a experiência.
6. Sinais de desconforto, sono ou saturação e o que fazer quando aparecerem.
7. Como essa experiência pode se repetir ao longo da semana, com pequenas variações.

REGRAS
${REGRAS_BASE}
- Segurança e higiene em primeiro lugar: nada de peça pequena, pontiaguda ou tóxica; oriente a higienização dos materiais.
- Respeite o tempo de cada bebê — ninguém é obrigado a participar no mesmo momento ou do mesmo jeito.
- Não proponha atividade de alfabetização, números abstratos ou tarefa de papel e caneta: nessa faixa etária, o corpo, os sentidos e o vínculo são o currículo.`
},
{
  id:"eja", grupo:"Atividades", origem:"modelo", nome:"Atividades de EJA",
  resumo:"Atividade para jovens e adultos, partindo da experiência de vida deles.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"tema",     rot:"Tema", ph:"Leitura de contrato de trabalho"},
    {id:"comp",     rot:"Componente curricular", tipo:"lista", ph:"Língua Portuguesa", meia:true},
    {id:"ano",      rot:"Etapa", tipo:"select", op:ANOS, meia:true},
    {id:"formato",  rot:"Formato", tipo:"select", op:["","Individual","Em dupla","Em grupo"], meia:true},
    {id:"tempo",    rot:"Tempo disponível", tipo:"select", op:["","1 aula (50 min)","2 aulas","1 semana"], meia:true},
    {id:"realidade",rot:"Realidade e experiência dos alunos", tipo:"textarea", ph:"Maioria trabalha durante o dia; vários lidam com leitura de boletos e escalas de trabalho; alguns pouco alfabetizados."}
  ],
  prompt:v=>
`Aja como um professor de Educação de Jovens e Adultos (EJA), especialista em ensino que parte da experiência de vida e de trabalho dos alunos.

CONTEXTO${L("Componente curricular",v.comp)}${L("Etapa",v.ano)}${L("Formato",v.formato)}${L("Tempo disponível",v.tempo)}${P("REALIDADE E EXPERIÊNCIA DOS ALUNOS",v.realidade)}

TAREFA
Crie uma atividade sobre “${v.tema||"o tema informado"}” para essa turma de EJA.

FORMATO DA RESPOSTA
1. Objetivo da atividade, ligado a uma situação real que esses alunos enfrentam.
2. Ponto de partida: uma pergunta ou situação que ativa o que eles já sabem pela experiência de vida ou de trabalho.
3. Passo a passo da atividade, com o enunciado pronto para usar.
4. Como o conteúdo aprendido pode ser usado imediatamente fora da sala de aula.
5. Adaptações para quem está pouco alfabetizado, sem separar a turma em “grupo fraco”.
6. Uma forma de fechar a aula em que os próprios alunos digam o que aprenderam e para que serve.

REGRAS
${REGRAS_BASE}
- Parta sempre da experiência de trabalho e de vida da turma — nunca de um exemplo genérico de livro didático infantil.
- A atividade precisa ter uso imediato e reconhecível na vida do aluno adulto.
- Não infantilize: nada de personagens, enunciados ou ilustrações voltados para criança.`
},
{
  id:"pcd", grupo:"Atividades", origem:"modelo", nome:"Atividade para PCD",
  resumo:"Atividade adaptada para um estudante público-alvo da educação especial, sem isolá-lo da turma.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"nec",     rot:"Necessidade específica", tipo:"select", op:["","Deficiência física / motora","Deficiência visual","Baixa visão","Deficiência auditiva","Surdez","Deficiência intelectual","Transtorno do Espectro Autista (TEA)","Síndrome de Down","TDAH","Dislexia","Discalculia","Altas habilidades / superdotação","Dificuldades de aprendizagem","Outro"], meia:true},
    {id:"ano",     rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"alfa",    rot:"Está alfabetizado?", tipo:"select", op:["","Sim","Não","Em processo"], meia:true},
    {id:"area",    rot:"Área de conhecimento", ph:"Matemática", meia:true},
    {id:"objetivo",rot:"Objetivo da atividade", ph:"Reconhecer figuras geométricas", meia:true},
    {id:"recursos",rot:"Recursos disponíveis", ph:"Material tátil, tablet com leitor de tela", meia:true},
    {id:"conteudo",rot:"Conteúdo que a turma está estudando", ph:"Figuras planas e seus nomes"}
  ],
  prompt:v=>
`Aja como um professor de sala de recursos multifuncionais, especialista em educação inclusiva e em desenho universal para a aprendizagem (DUA).

CONTEXTO${L("Necessidade específica",v.nec)}${L("Ano/série",v.ano)}${L("Alfabetizado",v.alfa)}${L("Área de conhecimento",v.area)}${L("Objetivo",v.objetivo)}${L("Recursos disponíveis",v.recursos)}${L("Conteúdo que a turma está estudando",v.conteudo)}

TAREFA
Crie uma atividade para este estudante participar junto com a turma, dentro do mesmo conteúdo.

FORMATO DA RESPOSTA
1. Nome e objetivo da atividade, em termos observáveis.
2. Como essa atividade se conecta com o que a turma está estudando.
3. Materiais necessários e como adaptá-los com recursos simples da escola.
4. Passo a passo, com a mediação do professor descrita em cada etapa.
5. Como organizar o aluno dentro do grupo — a atividade precisa incluir, não isolar.
6. Sinais de sobrecarga ou desconforto e o que fazer quando aparecerem.
7. Como avaliar o que ele aprendeu, sem reduzir a expectativa de aprendizagem.

REGRAS
${REGRAS_BASE}
- Adaptar não é simplificar o objetivo: é mudar o caminho até ele.
- A atividade não pode isolar o estudante do restante da turma nem parecer “a versão fácil” aos olhos dos colegas.
- Não faça diagnóstico nem recomendação clínica; fale apenas do plano pedagógico.`
},
{
  id:"adaptada", grupo:"Atividades", origem:"novo", nome:"Adaptar uma atividade existente",
  resumo:"Cole a atividade pronta e receba uma versão acessível, com o mesmo objetivo.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"txt",     rot:"Atividade original", tipo:"textarea", grande:true, ph:"Cole aqui o enunciado ou a descrição da atividade que a turma vai fazer."},
    {id:"nec",     rot:"Necessidade do estudante", tipo:"select", op:["","Transtorno do Espectro Autista (TEA)","TDAH","Deficiência intelectual","Dislexia","Discalculia","Deficiência física / motora","Deficiência visual ou baixa visão","Surdez ou deficiência auditiva","Altas habilidades / superdotação","Estudante em defasagem de aprendizagem","Outro"], meia:true},
    {id:"ano",     rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"comp",    rot:"Componente curricular", tipo:"lista", ph:"Geografia", meia:true},
    {id:"objetivo",rot:"Objetivo que deve ser preservado", ph:"Identificar as regiões do Brasil", meia:true}
  ],
  prompt:v=>
`Aja como um professor de sala de recursos multifuncionais, especialista em educação inclusiva e em desenho universal para a aprendizagem (DUA).

CONTEXTO${L("Necessidade do estudante",v.nec)}${L("Ano/série",v.ano)}${L("Componente curricular",v.comp)}${L("Objetivo a preservar",v.objetivo)}${P("ATIVIDADE ORIGINAL",v.txt)}

TAREFA
Adapte a atividade original para este estudante, mantendo o mesmo objetivo de aprendizagem da turma.

FORMATO DA RESPOSTA
1. O que exatamente dificulta o acesso deste estudante à atividade original.
2. Versão adaptada, pronta para uso, com o enunciado já reescrito.
3. Apoios necessários: materiais, tempo adicional, mediação, tecnologia assistiva.
4. Como o professor deve apresentar a atividade (o que dizer, onde posicionar o aluno, como acompanhar).
5. Como avaliar sem reduzir a exigência de aprendizagem.
6. Sinais de que a adaptação está funcionando — e o que fazer se não estiver.

REGRAS
${REGRAS_BASE}
- Adaptar não é simplificar o objetivo: é mudar o caminho até ele.
- A versão adaptada precisa manter a mesma expectativa de aprendizagem da atividade original, só muda a forma de chegar lá.
- Não faça diagnóstico nem recomendação clínica; fale apenas do plano pedagógico.`
},
{
  id:"socioemocional", grupo:"Atividades", origem:"modelo", nome:"Atividades socioemocionais",
  resumo:"Dinâmica para trabalhar uma competência socioemocional da turma.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"competencia",rot:"Competência", tipo:"select", op:["","Autoconhecimento","Autorregulação","Empatia","Colaboração","Resiliência","Responsabilidade","Comunicação"], meia:true},
    {id:"ano",        rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"formato",    rot:"Formato", tipo:"select", op:["","Roda de conversa","Dinâmica em grupo","Atividade individual escrita","Jogo cooperativo","Vivência prática"], meia:true},
    {id:"tempo",      rot:"Tempo disponível", tipo:"select", op:["","15 minutos","30 minutos","1 aula completa"], meia:true},
    {id:"obs",        rot:"Contexto da turma", tipo:"textarea", ph:"Turma com conflitos frequentes no recreio; pouco à vontade para falar em público.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em educação socioemocional, com base em competências como as da BNCC e do CASEL.

CONTEXTO${L("Competência",v.competencia)}${L("Ano/série",v.ano)}${L("Formato",v.formato)}${L("Tempo disponível",v.tempo)}${P("CONTEXTO DA TURMA",v.obs)}

TAREFA
Crie uma dinâmica para trabalhar essa competência com a turma.

FORMATO DA RESPOSTA
1. Objetivo da dinâmica, em termos observáveis.
2. Como abrir a atividade (o que o professor diz para engajar a turma).
3. Passo a passo da dinâmica, com o tempo de cada etapa.
4. Perguntas de reflexão para usar durante ou depois da atividade.
5. Como fechar a dinâmica de forma segura, sem deixar ninguém exposto.
6. O que fazer se algum aluno ficar visivelmente incomodado durante a atividade.

REGRAS
${REGRAS_BASE}
- Não transforme a aula em sessão de terapia: a dinâmica é pedagógica, não clínica.
- Nunca peça que o aluno exponha um trauma pessoal ou uma situação familiar delicada para o grupo.
- Toda dinâmica precisa terminar com um fechamento seguro, que devolva a turma ao clima normal da aula.`
},
{
  id:"ambiental", grupo:"Atividades", origem:"modelo", nome:"Educação ambiental",
  resumo:"Atividade de educação ambiental com recorte local e ação prática.",
  ias:["chatgpt","claude","gemini","perplexity"],
  campos:[
    {id:"tema",   rot:"Tema ambiental com recorte local", ph:"Poluição do rio que passa perto da escola"},
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"acao",   rot:"Ação prática", tipo:"select", op:["","Mutirão de limpeza","Horta ou jardim escolar","Coleta seletiva na escola","Campanha de conscientização","Visita técnica ou de campo","Projeto de pesquisa e monitoramento"], meia:true},
    {id:"duracao",rot:"Duração", tipo:"select", op:["","1 aula","Projeto de 1 semana","Projeto do bimestre"], meia:true},
    {id:"obs",    rot:"Observações", tipo:"textarea", ph:"A escola já tem horta iniciada; existe coleta seletiva no bairro.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em educação ambiental, com foco em ações práticas e no contexto local dos alunos.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Ação prática",v.acao)}${L("Duração",v.duracao)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade sobre “${v.tema||"o tema ambiental informado"}”, conectada ao componente curricular e com uma ação prática.

FORMATO DA RESPOSTA
1. Como o tema se conecta com o conteúdo do componente curricular.
2. Levantamento inicial: o que os alunos já sabem ou observam sobre esse problema no dia a dia deles.
3. Passo a passo da ação prática proposta, com materiais e organização da turma.
4. Como a atividade mostra que o problema tem causas coletivas e estruturais, não só escolhas individuais.
5. Um produto final que os alunos podem apresentar para a escola ou a comunidade.
6. Como avaliar a participação e a aprendizagem, sem exigir apenas texto escrito.

REGRAS
${REGRAS_BASE}
- Evite culpabilizar o aluno ou a família pelo problema ambiental (por exemplo, por gerar lixo ou consumir água).
- Mostre a dimensão coletiva e política da questão: quem decide, quem é afetado, o que pode mudar em nível de política pública.
- Conecte a ação prática com o conteúdo do componente curricular; não deixe a atividade só no campo da conscientização.`
},
{
  id:"consumo", grupo:"Atividades", origem:"modelo", nome:"Consumo consciente",
  resumo:"Atividade prática sobre consumo, publicidade e desperdício, com dados coletados pelos alunos.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"foco",   rot:"Recorte", tipo:"select", op:["","Publicidade e persuasão","Desperdício de alimentos","Orçamento doméstico","Descarte e reciclagem","Consumismo e redes sociais"], meia:true},
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"formato",rot:"Formato", tipo:"select", op:["","Individual","Em dupla","Em grupo"], meia:true},
    {id:"coleta", rot:"O que os alunos vão observar ou coletar", ph:"Quantidade de comida jogada fora na cantina em uma semana"},
    {id:"obs",    rot:"Observações", tipo:"textarea", ph:"Evitar perguntas sobre renda familiar; usar dados da própria escola.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em educação financeira e consumo consciente para a educação básica.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Formato",v.formato)}${L("O que os alunos vão observar ou coletar",v.coleta)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade prática sobre “${v.foco||"consumo consciente"}”.

FORMATO DA RESPOSTA
1. Objetivo da atividade, ligado ao componente curricular informado.
2. Como os alunos vão coletar os dados propostos (roteiro simples de observação ou registro).
3. Como organizar e analisar os dados coletados em sala (tabela, gráfico ou lista).
4. Perguntas para discutir o que os dados revelam, sem apontar culpados individuais.
5. Uma ação concreta que a turma pode propor a partir do que descobriu.
6. Como avaliar a participação de cada aluno na atividade.

REGRAS
${REGRAS_BASE}
- Nunca peça informações sobre a renda, o emprego ou os bens da família do aluno.
- Não use exemplos que exponham ou constranjam um aluno pela condição financeira da família.
- Trabalhe com dados que os próprios alunos possam coletar na escola ou no bairro, não em casa de forma invasiva.`
},
{
  id:"valores", grupo:"Atividades", origem:"modelo", nome:"Aula sobre valores",
  resumo:"Aula sobre ética, respeito e convivência, em que a turma constrói a própria conclusão.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"tema",     rot:"Valor ou tema a trabalhar", ph:"Respeito às diferenças"},
    {id:"comp",     rot:"Componente curricular", tipo:"lista", ph:"Língua Portuguesa", meia:true},
    {id:"ano",      rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"aval",     rot:"Tipo de avaliação", tipo:"select", op:["","Formativa","Formativa + somativa","Autoavaliação","Avaliação por pares","Portfólio","Rubrica"], meia:true},
    {id:"formato",  rot:"Formato da aula", tipo:"select", op:["","Roda de conversa","Debate","Estudo de caso","Dinâmica em grupo"], meia:true},
    {id:"situacao", rot:"Situação real da turma", tipo:"textarea", ph:"Houve um caso de exclusão no grupo de mensagens da turma na semana passada."}
  ],
  prompt:v=>
`Aja como um professor especialista em formação ética e cidadã, que conduz discussões sem impor conclusões prontas.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Tipo de avaliação",v.aval)}${L("Formato da aula",v.formato)}${P("SITUAÇÃO REAL DA TURMA",v.situacao)}

TAREFA
Crie uma aula sobre “${v.tema||"o valor informado"}” para essa turma.

FORMATO DA RESPOSTA
1. Pergunta ou situação de abertura, que provoca a turma a pensar sem dar a resposta.
2. Passo a passo da aula, com o papel do professor como mediador, não como quem dá a lição.
3. Perguntas que levam a turma a construir a própria conclusão, em vez de recebê-la pronta.
4. Como lidar com opiniões divergentes dentro da turma, sem silenciar nenhuma delas.
5. Instrumento de avaliação, coerente com o tipo escolhido.
6. Como fechar a aula sem parecer um sermão ou uma lição de moral.

REGRAS
${REGRAS_BASE}
- Não dê sermão nem imponha conclusão moral pronta: a turma discute e chega às próprias conclusões, mediada pelo professor.
- Respeite a pluralidade de crenças da turma — não inclua doutrinação religiosa nem posicionamento político-partidário.
- Use a situação real da turma com cuidado, sem expor ou identificar quem esteve envolvido.`
},
{
  id:"explicar", grupo:"Atividades", origem:"novo", nome:"Explicação acessível",
  resumo:"Um conceito difícil traduzido para a linguagem da turma, com analogia e verificação.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"conceito",rot:"Conceito a explicar", ph:"Ligação de hidrogênio"},
    {id:"comp",    rot:"Componente curricular", tipo:"lista", ph:"Química", meia:true},
    {id:"ano",     rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"analogia",rot:"Usar analogia", tipo:"select", op:["","Sim, do cotidiano do aluno","Sim, ligada ao contexto local/regional","Não, explicação direta"], meia:true},
    {id:"tamanho", rot:"Tamanho", tipo:"select", op:["","Curta (até 150 palavras)","Média (até 400 palavras)","Completa, com exemplos e exercício"], meia:true},
    {id:"erro",    rot:"Erro comum que quer desfazer", ph:"Os alunos acham que é uma ligação química de verdade"}
  ],
  prompt:v=>
`Aja como um professor famoso por explicar bem — daqueles que a turma entende de primeira.

CONTEXTO${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Usar analogia",v.analogia)}${L("Tamanho",v.tamanho)}${L("Erro comum a desfazer",v.erro)}

TAREFA
Explique “${v.conceito||"o conceito informado"}” para essa turma.

FORMATO DA RESPOSTA
1. Uma frase que resume a ideia central, sem jargão.
2. A explicação, construída do concreto para o abstrato.
3. Uma analogia do cotidiano do aluno (se pedida) ou uma explicação direta.
4. O erro comum, nomeado e desfeito explicitamente.
5. Onde a analogia deixa de funcionar, para não criar um novo erro.
6. Três perguntas de verificação, da mais simples à mais difícil, com as respostas.

REGRAS
${REGRAS_BASE}
- Use frases curtas; não empilhe termos técnicos sem defini-los.
- Se precisar de um termo técnico, apresente-o depois da ideia, nunca antes.
- Diga explicitamente onde a analogia deixa de valer, para o aluno não levar a comparação longe demais.`
},
{
  id:"ativ-avaliativa", grupo:"Avaliar", origem:"modelo", nome:"Atividade avaliativa",
  resumo:"Atividade que vale nota, com pontuação por item e critérios de correção.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Química", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"cont", rot:"Conteúdo cobrado", ph:"Ésteres e biodiesel"},
    {id:"n",    rot:"Quantidade de questões", tipo:"number", ph:"8", meia:true},
    {id:"tipo", rot:"Tipo de questão", tipo:"select", op:["","Objetiva","Discursiva","Mista"], meia:true},
    {id:"pts",  rot:"Pontuação total", ph:"10 pontos", meia:true},
    {id:"tempo",rot:"Tempo para realizar", tipo:"select", op:["","30 minutos","45 minutos","50 minutos","90 minutos","1 aula dupla"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Pode ser aplicada em dupla; um aluno usa cadeira de rodas e precisa de espaço extra na carteira.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor experiente, especialista em elaborar atividades avaliativas que valem nota, com critérios de correção claros.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Conteúdo cobrado",v.cont)}${L("Quantidade de questões",v.n)}${L("Tipo de questão",v.tipo)}${L("Pontuação total",v.pts)}${L("Tempo para realizar",v.tempo)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Elabore uma atividade avaliativa completa, pronta para aplicar e que valha nota.

FORMATO DA RESPOSTA
1. Cabeçalho da atividade (componente, ano, valor total em pontos e instruções para o aluno).
2. As questões numeradas, com a pontuação de cada uma indicada ao lado.
3. Em questões objetivas, alternativas plausíveis e apenas uma correta.
4. Gabarito comentado ao final, explicando por que a alternativa certa está certa.
5. Critérios de correção para as questões discursivas, com o que precisa aparecer na resposta em cada faixa de pontuação.
6. Estimativa de tempo necessário para a turma resolver.

REGRAS
${REGRAS_BASE}
- A soma dos pontos de todas as questões deve bater exatamente com a pontuação total informada.
- Em questões discursivas, o critério de correção deve permitir pontuação parcial, não apenas certo ou errado.`
},
{
  id:"questoes", grupo:"Avaliar", origem:"novo", nome:"Questões de prova",
  resumo:"Itens no nível cognitivo escolhido (taxonomia de Bloom), com distratores plausíveis e gabarito comentado.",
  ias:["chatgpt","claude","gemini","deepseek"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Física", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"cont", rot:"Conteúdo cobrado", ph:"Leis de Newton aplicadas a planos inclinados"},
    {id:"n",    rot:"Quantidade de questões", tipo:"number", ph:"8", meia:true},
    {id:"tipo", rot:"Tipo", tipo:"select", op:["","Objetiva","Discursiva"], meia:true},
    {id:"bloom",rot:"Nível cognitivo (Bloom)", tipo:"select", op:["","Lembrar","Compreender","Aplicar","Analisar","Avaliar","Criar","Progressivo: do mais simples ao mais complexo"], meia:true},
    {id:"dific",rot:"Grau de dificuldade", tipo:"select", op:["","Fácil","Médio","Difícil","Misto"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Evitar contas com fração; a turma ainda está insegura com decimais.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em elaboração de itens de avaliação, com domínio da taxonomia de Bloom.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Conteúdo cobrado",v.cont)}${L("Quantidade de questões",v.n)}${L("Tipo",v.tipo)}${L("Nível cognitivo (Bloom)",v.bloom)}${L("Grau de dificuldade",v.dific)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Elabore questões de prova no nível cognitivo indicado, com distratores plausíveis (quando objetivas) e gabarito comentado.

FORMATO DA RESPOSTA
1. As questões numeradas, cada uma mobilizando de fato o nível cognitivo escolhido.
2. Em questões objetivas, alternativas plausíveis: cada distrator representa um erro de raciocínio real, não um erro absurdo.
3. Gabarito comentado ao final, com a resposta correta e por que cada distrator está errado.
4. Em questões discursivas, o que uma resposta completa precisa conter para pontuar integralmente.
5. Classificação de cada questão pelo nível cognitivo de Bloom mobilizado.
6. Grau de dificuldade estimado de cada questão.

REGRAS
${REGRAS_BASE}
- Todas as questões devem mobilizar de fato o nível cognitivo escolhido, não apenas memorização disfarçada.
- Nenhum distrator pode estar obviamente errado; todos precisam ser plausíveis para quem não domina o conteúdo.`
},
{
  id:"simulado", grupo:"Avaliar", origem:"modelo", nome:"Teste simulado: ENEM, SAEB…",
  resumo:"Prova completa no estilo de uma avaliação em larga escala, pronta para aplicar.",
  ias:["chatgpt","claude","gemini","deepseek"],
  campos:[
    {id:"estilo",rot:"Estilo do simulado", tipo:"select", op:["","ENEM — Ciências da Natureza","ENEM — Matemática","ENEM — Ciências Humanas","ENEM — Linguagens","SAEB","Avaliação externa da rede","Vestibular tradicional","Concurso","Outro"], meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"n",    rot:"Número de questões", tipo:"number", ph:"20", meia:true},
    {id:"tempo",rot:"Tempo de prova", tipo:"select", op:["","45 minutos","1 hora","2 horas","3 horas","4 horas"], meia:true},
    {id:"dific",rot:"Grau de dificuldade", tipo:"select", op:["","Fácil","Médio","Difícil","Progressivo (fácil → difícil)"], meia:true},
    {id:"cont", rot:"Conteúdos que devem cair", tipo:"textarea", ph:"Funções, progressões, geometria plana. Deixe em branco para cobrir a matriz completa.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um especialista em avaliação em larga escala, com domínio profundo da estrutura e do estilo de provas como o ENEM e o SAEB.

CONTEXTO${L("Estilo do simulado",v.estilo)}${L("Ano/série",v.ano)}${L("Componente",v.comp)}${L("Número de questões",v.n)}${L("Tempo de prova",v.tempo)}${L("Grau de dificuldade",v.dific)}${P("CONTEÚDOS QUE DEVEM CAIR",v.cont)}

TAREFA
Elabore uma prova simulada completa, no estilo e no nível de exigência indicados, pronta para aplicar dentro do tempo informado.

FORMATO DA RESPOSTA
1. Cabeçalho da prova (estilo, componente, tempo de duração e instruções ao aluno).
2. As questões numeradas, no estilo indicado, com texto-base, comando e alternativas quando for múltipla escolha.
3. Quando uma questão exigir gráfico, tabela, imagem ou mapa, descreva em texto exatamente o que deve aparecer, com todos os valores e rótulos, para o professor reproduzir ou desenhar.
4. Gabarito comentado ao final, com a lógica de cada distrator.
5. Grau de dificuldade de cada questão, coerente com o grau geral informado.
6. Estimativa de tempo médio por questão, batendo com o tempo total de prova.
7. Sugestão de como distribuir as questões por nível de dificuldade ao longo da prova.

REGRAS
${REGRAS_BASE}
- Sempre que uma questão precisar de gráfico, imagem ou mapa, descreva-o em texto com todos os dados necessários para o professor reproduzir — nunca deixe a questão incompleta por depender de uma imagem que você não pode gerar.
- O número de questões deve bater exatamente com o informado.`
},
{
  id:"saeb", grupo:"Avaliar", origem:"modelo", nome:"Atividade baseada no SAEB",
  resumo:"Itens no formato SAEB alinhados a um descritor, com a matriz de referência explicitada.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Língua Portuguesa", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"desc", rot:"Descritor do SAEB", ph:"D3 — Inferir o sentido de uma palavra ou expressão"},
    {id:"tema", rot:"Tema ou contexto sugerido", ph:"Notícia sobre meio ambiente", meia:true},
    {id:"n",    rot:"Quantidade de itens", tipo:"number", ph:"5", meia:true},
    {id:"form", rot:"Formato dos itens", tipo:"select", op:["","Múltipla escolha (estilo SAEB)","Resposta curta","Misto"]}
  ],
  prompt:v=>
`Aja como um especialista em avaliação em larga escala, com domínio da matriz de referência do SAEB.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Descritor do SAEB",v.desc)}${L("Tema/contexto sugerido",v.tema)}${L("Quantidade de itens",v.n)}${L("Formato dos itens",v.form)}

TAREFA
Elabore itens alinhados exatamente ao descritor do SAEB informado, com a matriz de referência explicitada.

FORMATO DA RESPOSTA
1. A matriz de referência do descritor: código, competência da área e o que ele exige do aluno, em linguagem simples.
2. Texto-base (quando o descritor pedir), adequado ao tema/contexto e ao ano/série.
3. Os itens numerados, cada um mobilizando de fato o descritor informado.
4. Em itens de múltipla escolha, gabarito e uma justificativa curta de por que cada distrator é plausível.
5. Nível de dificuldade estimado de cada item.
6. Sugestão de como registrar o desempenho da turma em relação a esse descritor.

REGRAS
${REGRAS_BASE}
- Não misture mais de um descritor no mesmo item.
- Se o descritor informado não existir ou estiver incompleto, avise antes de inventar um código.`
},
{
  id:"diagnostica", grupo:"Avaliar", origem:"modelo", nome:"Avaliação diagnóstica",
  resumo:"Sondagem de início de ano ou bimestre para descobrir o que a turma já sabe, com mapa de pré-requisitos e ficha de registro por aluno.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"cont", rot:"Conteúdo/habilidade que vem em seguida", ph:"Equações do 2º grau"},
    {id:"momento",rot:"Momento da sondagem", tipo:"select", op:["","Início de ano","Início de bimestre","Antes de iniciar um novo conteúdo"], meia:true},
    {id:"n",    rot:"Quantidade de questões/itens", tipo:"number", ph:"6", meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Turma nova para mim; não conheço o histórico dos alunos.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um especialista em avaliação diagnóstica e sondagem de aprendizagens.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Conteúdo/habilidade em seguida",v.cont)}${L("Momento da sondagem",v.momento)}${L("Quantidade de questões/itens",v.n)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Elabore uma avaliação diagnóstica para descobrir o que a turma já sabe antes de iniciar o conteúdo indicado.

FORMATO DA RESPOSTA
1. Mapa de pré-requisitos: o que o aluno precisa já saber para acompanhar o conteúdo seguinte, do mais básico ao mais avançado.
2. Os itens da sondagem numerados, cada um ligado a um pré-requisito do mapa.
3. Para cada item, o que uma resposta certa e uma resposta errada revelam sobre o que o aluno já sabe.
4. Ficha de registro por aluno (usando iniciais), com uma linha por pré-requisito e espaço para marcar “domina”, “domina parcialmente” ou “não domina”.
5. Como agrupar a turma a partir dos resultados, para planejar os próximos passos.
6. Orientação de aplicação: tempo estimado e como comunicar à turma que a atividade não vale nota.

REGRAS
${REGRAS_BASE}
- Deixe claro, na própria avaliação, que ela não vale nota e serve apenas para planejamento do professor.
- Use apenas iniciais nos exemplos de ficha de registro, nunca nome completo.`
},
{
  id:"rubrica", grupo:"Avaliar", origem:"modelo", nome:"Rubrica avaliativa",
  resumo:"Critérios e níveis descritos com clareza, prontos para virar tabela.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp",  rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",   rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"ativ",  rot:"Atividade ou tarefa avaliada", ph:"Relatório de prática laboratorial"},
    {id:"niveis",rot:"Número de níveis", tipo:"select", op:["","3 níveis","4 níveis","5 níveis"], meia:true},
    {id:"esc",   rot:"Escala", tipo:"select", op:["","Nota de 0 a 10","Pontos por critério","Conceitos (A, B, C, D)","Apenas descritivo, sem nota"], meia:true},
    {id:"crit",  rot:"Critérios que você quer avaliar", tipo:"textarea", ph:"Clareza, precisão conceitual, análise dos dados, trabalho em equipe", dica:"opcional — deixe em branco para a IA sugerir os critérios"}
  ],
  prompt:v=>
`Aja como um especialista em avaliação por critérios, com domínio de construção de rubricas avaliativas.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Atividade avaliada",v.ativ)}${L("Número de níveis",v.niveis)}${L("Escala",v.esc)}${P("CRITÉRIOS QUE VOCÊ QUER AVALIAR",v.crit)}

TAREFA
Construa uma rubrica avaliativa para a atividade indicada, pronta para virar uma tabela de critérios × níveis.

FORMATO DA RESPOSTA
1. Lista de critérios de avaliação (use os informados; se não houver, proponha de 4 a 6 critérios pertinentes à atividade).
2. Tabela de critérios × níveis, com uma descrição observável e específica em cada célula.
3. Nome de cada nível de desempenho, na quantidade informada.
4. Pontuação ou conceito correspondente a cada nível, coerente com a escala escolhida.
5. Versão da mesma rubrica reescrita em linguagem simples, para entregar ao aluno junto com a atividade.
6. Um exemplo de trabalho hipotético e em qual nível ele se encaixaria em cada critério, para o professor calibrar o próprio olhar.

REGRAS
${REGRAS_BASE}
- Os níveis devem ser mutuamente excludentes: a diferença entre um nível e o seguinte precisa estar na qualidade descrita do que o aluno fez, nunca apenas em um advérbio como “muito” ou “pouco”.
- Cada célula da tabela deve ser observável — algo que o professor consiga checar no trabalho do aluno, não uma impressão subjetiva.`
},
{
  id:"corrigir-provas", grupo:"Avaliar", origem:"modelo", nome:"Corrigir provas",
  resumo:"Corrige as respostas coladas a partir do gabarito e aponta os erros mais comuns da turma.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"comp",     rot:"Componente curricular", tipo:"lista", ph:"Geografia", meia:true},
    {id:"ano",      rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"gabarito", rot:"Gabarito", tipo:"textarea", ph:"1-C, 2-A, 3-B. Questão 4 (discursiva): precisa citar causa e consequência do processo."},
    {id:"respostas",rot:"Respostas dos alunos", tipo:"textarea", grande:true, ph:"Cole aqui as respostas, uma linha por aluno, usando iniciais. Ex.: J.S. — 1-C, 2-A, 3-C, 4: (texto da resposta)"},
    {id:"obs",      rot:"Observações", tipo:"textarea", ph:"Aceitar variações de nomenclatura na questão 3.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor experiente e meticuloso na correção de provas, atento a erros de conteúdo e a padrões de erro da turma.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${P("GABARITO",v.gabarito)}${P("RESPOSTAS DOS ALUNOS",v.respostas)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Corrija as respostas coladas usando o gabarito fornecido e aponte os erros mais comuns da turma.

FORMATO DA RESPOSTA
1. Tabela por aluno (usando as iniciais informadas): questão, resposta dada, certo/errado/parcial e pontuação.
2. Total de pontos de cada aluno, e a nota correspondente, se aplicável.
3. Para questões discursivas, um comentário curto sobre o que faltou ou o que foi bem feito no trabalho.
4. Ranking das questões com mais erros na turma, da mais errada para a menos errada.
5. Para cada questão muito errada, uma hipótese do porquê (erro de conteúdo, de leitura do enunciado ou de cálculo).
6. Sugestão do que retomar na próxima aula com base nos erros mais comuns.

REGRAS
${REGRAS_BASE}
- Comente sempre o trabalho entregue, nunca a pessoa do aluno.
- Se o gabarito e as respostas não tiverem o mesmo número de questões, avise antes de corrigir.`
},
{
  id:"redacao", grupo:"Avaliar", origem:"modelo", nome:"Corrigir redação",
  resumo:"Correção por competências do ENEM (ou outro gênero), com trechos citados, nota por competência e versão reescrita opcional.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"tipo", rot:"Gênero ou modelo", tipo:"select", op:["","Redação do ENEM (5 competências)","Dissertativo-argumentativo","Artigo de opinião","Carta argumentativa","Resenha","Outro gênero"], meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"prop", rot:"Tema ou proposta dada", ph:"Desafios para o descarte de resíduos no Brasil", meia:true},
    {id:"reescrever",rot:"Reescrever?", tipo:"select", op:["","Não, só corrigir","Sim, sugerir versão reescrita"], meia:true},
    {id:"txt",  rot:"Texto do aluno", tipo:"textarea", grande:true, ph:"Cole aqui o texto da redação."}
  ],
  prompt:v=>
`Aja como um corretor de redações experiente, com domínio dos critérios de avaliação do gênero indicado.

CONTEXTO${L("Gênero/modelo",v.tipo)}${L("Ano/série",v.ano)}${L("Tema/proposta dada",v.prop)}${L("Reescrever",v.reescrever)}${P("TEXTO DO ALUNO",v.txt)}

TAREFA
Corrija o texto por competências (ou pelos critérios do gênero indicado), citando trechos exatos do aluno.

FORMATO DA RESPOSTA
1. Nota ou avaliação por competência (ou por critério do gênero), cada uma com um trecho citado do texto que justifica a nota.
2. Pontos fortes do texto, com trecho citado para cada um.
3. Pontos a melhorar, com trecho citado e uma sugestão concreta de como reescrever aquele trecho.
4. Nota final (ou avaliação global), somando ou combinando as competências.
5. Se “reescrever” estiver marcado como sim, uma versão reescrita do texto corrigindo os problemas apontados.
6. Um comentário final direcionado ao aluno, em tom construtivo.

REGRAS
${REGRAS_BASE}
- Comente sempre o texto entregue, nunca a pessoa do aluno.
- Ao reescrever, preserve a tese e a voz do aluno — não escreva um texto novo, apenas corrija o que está lá.`
},
{
  id:"corrigir-texto", grupo:"Avaliar", origem:"modelo", nome:"Corrigir texto",
  resumo:"Revisão de um texto qualquer — gramática, coesão, clareza — em tabela trecho, correção e por quê.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"tipo", rot:"Tipo de texto", ph:"E-mail para os pais sobre a reunião", meia:true},
    {id:"autor",rot:"Autor do texto", tipo:"select", op:["","Texto de um aluno","Meu texto (professor)"], meia:true},
    {id:"foco", rot:"Foco da revisão", tipo:"select", op:["","Gramática e ortografia","Coesão e coerência","Clareza e objetividade","Tudo"], meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"txt",  rot:"Texto para revisar", tipo:"textarea", grande:true, ph:"Cole aqui o texto."}
  ],
  prompt:v=>
`Aja como um revisor de texto experiente, atento à gramática, à coesão e à clareza.

CONTEXTO${L("Tipo de texto",v.tipo)}${L("Autor do texto",v.autor)}${L("Foco da revisão",v.foco)}${L("Ano/série",v.ano)}${P("TEXTO PARA REVISAR",v.txt)}

TAREFA
Revise o texto colado e devolva as correções organizadas em tabela.

FORMATO DA RESPOSTA
1. Tabela com três colunas: trecho original, correção sugerida e por que a mudança é necessária.
2. Ordene a tabela na ordem em que os trechos aparecem no texto.
3. Ao final, uma versão completa do texto já corrigido.
4. Um resumo dos 2 ou 3 tipos de erro mais frequentes encontrados.
5. Se o autor for um aluno, uma observação de aprendizagem: o que esse padrão de erro sugere que ele ainda precisa praticar.

REGRAS
${REGRAS_BASE}
- Corrija apenas o que de fato está incorreto ou pouco claro; não reescreva por preferência de estilo.
- Se o autor for um aluno, comente sempre o texto, nunca a pessoa.`
},
{
  id:"autocorrecao", grupo:"Avaliar", origem:"modelo", nome:"Autocorreção de textos",
  resumo:"Gera um roteiro que o próprio aluno usa para revisar o texto antes de entregar.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp",  rot:"Componente curricular", tipo:"lista", ph:"Língua Portuguesa", meia:true},
    {id:"ano",   rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"genero",rot:"Tipo de texto/gênero", ph:"Redação dissertativo-argumentativa"},
    {id:"crit",  rot:"Critérios que o roteiro deve cobrir", tipo:"textarea", ph:"Coesão entre parágrafos, ortografia, se a tese aparece na introdução", dica:"opcional — deixe em branco para a IA sugerir com base no gênero"}
  ],
  prompt:v=>
`Aja como um tutor de escrita paciente, que vai me ajudar a revisar meu próprio texto antes de entregar.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tipo de texto/gênero",v.genero)}${P("CRITÉRIOS QUE O ROTEIRO DEVE COBRIR",v.crit)}

TAREFA
Monte um roteiro de autocorreção, em forma de checklist, para eu seguir sozinho antes de entregar o texto — sem que você veja o texto ainda.

FORMATO DA RESPOSTA
1. De 6 a 10 perguntas de checklist, em ordem, da estrutura geral do texto até o detalhe, que eu possa responder “sim” ou “não” olhando para o meu próprio texto.
2. Para cada pergunta do checklist, um exemplo do que procurar no texto.
3. Uma pergunta específica sobre se o texto responde de fato à proposta ou ao tema pedido.
4. Uma pergunta sobre a coesão entre os parágrafos.
5. Uma pergunta sobre ortografia e pontuação, com uma dica de como revisar sozinho (por exemplo, ler em voz alta).
6. Uma instrução final do que fazer quando alguma resposta do checklist for “não”.

REGRAS
${REGRAS_BASE}
- Use linguagem simples, direta e encorajadora, adequada para eu ler sozinho.
- O roteiro deve me ajudar a encontrar meus próprios problemas no texto, não corrigir o texto por mim.`
},
{
  id:"questoes-pdf", grupo:"Avaliar", origem:"modelo", nome:"Questões de PDF",
  resumo:"Gera questões a partir de um PDF anexado, citando a página de origem de cada uma.",
  ias:["claude","chatgpt","gemini","notebooklm"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"História", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"cont", rot:"Conteúdo ou capítulo do PDF", ph:"Capítulo 3 — Revolução Industrial (opcional, deixe em branco para usar o arquivo todo)"},
    {id:"n",    rot:"Quantidade de questões", tipo:"number", ph:"6", meia:true},
    {id:"tipo", rot:"Tipo de questão", tipo:"select", op:["","Objetiva","Discursiva","Mista"], meia:true}
  ],
  prompt:v=>
`Aja como um professor especialista em elaborar questões a partir de um material de apoio específico.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Conteúdo ou capítulo do PDF",v.cont)}${L("Quantidade de questões",v.n)}${L("Tipo de questão",v.tipo)}

TAREFA
Anexei um arquivo em PDF nesta conversa. Elabore questões usando exclusivamente o conteúdo desse arquivo.

FORMATO DA RESPOSTA
1. As questões numeradas, cada uma citando a página (ou seção) do PDF de onde foi retirada.
2. Em questões objetivas, alternativas plausíveis, todas baseadas em informações do próprio arquivo.
3. Gabarito comentado ao final, com a página onde está a resposta correta.
4. Se algum trecho pedido não existir no arquivo, diga isso explicitamente em vez de inventar.
5. Um resumo, em poucas linhas, do que o arquivo cobre e que ainda poderia virar questão.

REGRAS
${REGRAS_BASE}
- Use apenas o conteúdo do arquivo anexado; nunca complemente com conhecimento externo sem avisar.
- Cite a página de origem de cada questão; se não conseguir identificar a página exata, indique a seção ou o trecho.`
},
{
  id:"questoes-video", grupo:"Avaliar", origem:"modelo", nome:"Questões de vídeos",
  resumo:"A partir do link ou da transcrição de um vídeo, gera perguntas com marcação de minutagem.",
  ias:["gemini","notebooklm","chatgpt"],
  campos:[
    {id:"comp",  rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",   rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"link",  rot:"Link do vídeo", ph:"https://..."},
    {id:"n",     rot:"Quantidade de perguntas", tipo:"number", ph:"6", meia:true},
    {id:"tipo",  rot:"Tipo de pergunta", tipo:"select", op:["","Objetiva","Discursiva","Mista"], meia:true},
    {id:"transc",rot:"Transcrição do vídeo", tipo:"textarea", grande:true, ph:"Cole aqui a transcrição, se tiver.", dica:"opcional se o link já for acessível pela IA"}
  ],
  prompt:v=>
`Aja como um professor especialista em transformar conteúdo audiovisual em questões de verificação de aprendizagem.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Link do vídeo",v.link)}${L("Quantidade de perguntas",v.n)}${L("Tipo de pergunta",v.tipo)}${P("TRANSCRIÇÃO DO VÍDEO",v.transc)}

TAREFA
A partir do vídeo indicado (pelo link ou pela transcrição colada), elabore perguntas com a marcação do minuto de onde cada uma vem.

FORMATO DA RESPOSTA
1. As perguntas numeradas, cada uma com a minutagem aproximada (mm:ss) do trecho do vídeo de onde foi retirada.
2. Em perguntas objetivas, alternativas plausíveis baseadas apenas no que o vídeo mostra ou diz.
3. Gabarito comentado ao final, com a minutagem da resposta.
4. Se não for possível acessar o vídeo pelo link e não houver transcrição, diga isso claramente em vez de inventar o conteúdo.
5. Uma sugestão de pausa estratégica no vídeo (minutagem) para checar a compreensão da turma ao vivo.

REGRAS
${REGRAS_BASE}
- Baseie-se apenas no que está no vídeo ou na transcrição fornecida; não invente falas ou cenas.
- Sempre indique a minutagem de cada pergunta, mesmo que aproximada.`
},
{
  id:"boletim", grupo:"Avaliar", origem:"modelo", nome:"Boletim de aprendizagem",
  resumo:"Relatório de desempenho da turma ou de um aluno, por habilidade, com o que já domina e os encaminhamentos.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"alvo",   rot:"Relatório para", tipo:"select", op:["","Turma inteira","Um aluno (iniciais)"], meia:true},
    {id:"periodo",rot:"Período", tipo:"select", op:["","Bimestre","Trimestre","Semestre","Ano letivo"], meia:true},
    {id:"dados",  rot:"Dados de desempenho", tipo:"textarea", grande:true, ph:"Cole notas, resultados de avaliações e observações de sala, por habilidade ou por questão."}
  ],
  prompt:v=>
`Aja como um coordenador pedagógico especialista em análise de desempenho por habilidade.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Relatório para",v.alvo)}${L("Período",v.periodo)}${P("DADOS DE DESEMPENHO",v.dados)}

TAREFA
Transforme os dados em um boletim de aprendizagem organizado por habilidade, com o que já foi consolidado, o que ainda falta e o encaminhamento sugerido.

FORMATO DA RESPOSTA
1. Lista das habilidades avaliadas no período, identificadas a partir dos dados fornecidos.
2. Para cada habilidade, o nível de domínio: consolidado, em desenvolvimento ou não consolidado.
3. Se for relatório de turma, o percentual de alunos em cada nível por habilidade.
4. Se for de um aluno (iniciais), o desempenho dele em cada habilidade, com um exemplo extraído dos dados.
5. Encaminhamento concreto para cada habilidade não consolidada, além de “retomar o conteúdo”.
6. Um resumo de 3 a 5 linhas para constar no boletim ou no relatório à coordenação.

REGRAS
${REGRAS_BASE}
- Use apenas iniciais para identificar qualquer aluno, nunca o nome completo.
- Baseie cada conclusão nos dados fornecidos; não presuma desempenho em habilidades sem dado correspondente.`
},
{
  id:"feedback", grupo:"Avaliar", origem:"novo", nome:"Devolutiva para o aluno",
  resumo:"Feedback formativo, na segunda pessoa, com dois passos concretos para o aluno avançar.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"ativ", rot:"Atividade avaliada", ph:"Relatório de laboratório", meia:true},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Química", meia:true},
    {id:"forte",rot:"O que o aluno fez bem", tipo:"textarea", ph:"Coletou os dados com cuidado e montou a tabela corretamente."},
    {id:"melh", rot:"O que precisa melhorar", tipo:"textarea", ph:"Confundiu causa e correlação; a conclusão não retoma o objetivo."},
    {id:"tom",  rot:"Tom", tipo:"select", op:["","Acolhedor e encorajador","Direto e objetivo","Formal, para registro"], meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true}
  ],
  prompt:v=>
`Aja como um professor experiente em avaliação formativa, especialista em dar devolutivas que ajudam o aluno a avançar.

CONTEXTO${L("Atividade avaliada",v.ativ)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tom",v.tom)}${P("O QUE O ALUNO FEZ BEM",v.forte)}${P("O QUE PRECISA MELHORAR",v.melh)}

TAREFA
Escreva uma devolutiva formativa para o aluno, na segunda pessoa, terminando com dois passos concretos para ele avançar.

FORMATO DA RESPOSTA
1. Abertura reconhecendo algo específico que o aluno fez bem, citado a partir do que foi informado.
2. Um ou dois pontos de melhoria, descritos com clareza e sem rodeios.
3. Dois passos concretos e realizáveis que o aluno pode dar na próxima atividade.
4. Uma frase final de encorajamento, coerente com o tom escolhido.
5. Uma versão curta da mesma devolutiva (2 a 3 frases), para registrar rápido no caderno ou no sistema da escola.

REGRAS
${REGRAS_BASE}
- Escreva na segunda pessoa (“você fez”, “você pode”), diretamente para o aluno.
- Descreva sempre o trabalho e as atitudes observáveis, nunca o caráter ou a personalidade do aluno.`
},
{
  id:"parecer", grupo:"Avaliar", origem:"novo", nome:"Parecer descritivo",
  resumo:"Relatório individual por período, com avanços, desafios e encaminhamentos.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"periodo",rot:"Período", tipo:"select", op:["","Bimestre","Trimestre","Semestre","Ano letivo"], meia:true},
    {id:"inic",   rot:"Iniciais do aluno", ph:"J.S.", meia:true},
    {id:"obs",    rot:"Observações sobre o aluno no período", tipo:"textarea", grande:true, ph:"Notas, participação, comportamento em sala, avanços percebidos, dificuldades..."}
  ],
  prompt:v=>
`Aja como um professor experiente na elaboração de pareceres descritivos individuais.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Período",v.periodo)}${L("Iniciais do aluno",v.inic)}${P("OBSERVAÇÕES SOBRE O ALUNO NO PERÍODO",v.obs)}

TAREFA
Escreva um parecer descritivo individual para o período informado, com avanços, desafios e encaminhamentos.

FORMATO DA RESPOSTA
1. Parágrafo de abertura descrevendo o percurso geral do aluno no período, usando as iniciais informadas.
2. Avanços observados, com exemplo concreto extraído das observações.
3. Desafios observados, cada um descrito de forma objetiva e comportamental.
4. Para cada desafio listado, um encaminhamento correspondente — o que a escola ou a família pode fazer.
5. Parágrafo de fechamento com uma expectativa realista para o próximo período.

REGRAS
${REGRAS_BASE}
- Use apenas as iniciais do aluno, nunca o nome completo.
- Nunca use rótulos de personalidade, como “preguiçoso”, “desatento” ou “imaturo”; descreva sempre comportamentos e fatos observáveis.
- Nunca sugira diagnóstico clínico ou linguagem médica ou psicológica; se algo parecer exigir avaliação especializada, recomende encaminhar à equipe pedagógica ou à família, sem nomear uma condição.
- Todo desafio listado precisa vir acompanhado de um encaminhamento concreto.`
},
{
  id:"diagnostico-turma", grupo:"Avaliar", origem:"novo", nome:"Análise de resultados da turma",
  resumo:"Transforma os acertos por questão em decisão pedagógica, separando erro de conceito, de procedimento e de leitura.",
  ias:["chatgpt","claude","gemini","deepseek"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"aval", rot:"Avaliação aplicada", ph:"Prova bimestral, 10 questões objetivas", meia:true},
    {id:"n",    rot:"Número de alunos", tipo:"number", ph:"32", meia:true},
    {id:"dados",rot:"Resultados observados", tipo:"textarea", grande:true, ph:"Q1: 28 acertos. Q2: 9 acertos. Q3: 14 acertos...\nOu descreva: metade da turma errou as questões de fração; quase todos acertaram interpretação de gráfico.", dica:"pode colar a tabela de acertos por questão ou descrever com suas palavras"},
    {id:"tempo",rot:"Tempo disponível para agir", tipo:"select", op:["","1 aula","2 a 3 aulas","1 semana","O bimestre inteiro"], meia:true},
    {id:"dec",  rot:"Decisão que você precisa tomar", tipo:"select", op:["","Replanejar as próximas aulas","Montar grupos de reforço","Decidir se retomo o conteúdo ou sigo em frente","Preparar relatório para a coordenação","Planejar a recuperação"], meia:true}
  ],
  prompt:v=>
`Aja como um especialista em análise pedagógica de resultados de avaliação, focado em transformar dados em decisão de sala de aula.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Avaliação aplicada",v.aval)}${L("Número de alunos",v.n)}${L("Tempo disponível para agir",v.tempo)}${L("Decisão que você precisa tomar",v.dec)}${P("RESULTADOS OBSERVADOS",v.dados)}

TAREFA
Analise os resultados por questão e transforme-os em uma decisão pedagógica concreta para o tempo disponível.

FORMATO DA RESPOSTA
1. Leitura geral do desempenho da turma, com o percentual de acerto por questão.
2. Para cada questão com desempenho baixo, uma hipótese do tipo de erro: de conceito, de procedimento (sabia o conceito, errou o processo) ou de leitura do enunciado.
3. Agrupamento das questões problemáticas por causa provável — as que compartilham o mesmo tipo de erro.
4. Plano de ação cabendo no tempo disponível informado, priorizando as causas mais frequentes.
5. Sugestão de atividade ou estratégia específica para cada causa de erro identificada.
6. Indicação do que ainda precisa ser investigado com mais dados antes de qualquer conclusão, quando os dados não forem suficientes.

REGRAS
${REGRAS_BASE}
- Não conclua além do que os dados permitem: quando a causa do erro não estiver clara pelos números, diga que é uma hipótese e sugira como confirmar.
- Separe claramente erro de conceito, de procedimento e de leitura do enunciado; não trate todos como “o aluno não sabe”.`
},
/* ===================== ENGAJAR ===================== */
{
  id:"games", grupo:"Engajar", origem:"modelo", nome:"Games",
  resumo:"Jogo educacional digital, pronto para jogar em sala ou em casa.",
  ias:["claude","chatgpt","v0","bolt","aistudio"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema ou conteúdo do jogo", ph:"Tabuada e operações básicas"},
    {id:"plat", rot:"Plataforma", tipo:"select", op:["","Página HTML em arquivo único","Apresentação (PowerPoint / Google Slides)","Formulário (Google Forms)","Projetor com a turma toda","Sem preferência"], meia:true},
    {id:"tipo", rot:"Tipo de jogo", tipo:"select", op:["","Quiz com pontuação","Corrida contra o tempo","Jogo de memória","Caça ao tesouro por fases","Desafio em duplas ou equipes","Livre — sugira o melhor formato"], meia:true},
    {id:"obj",  rot:"Objetivo de aprendizagem", ph:"Ex.: praticar a tabuada do 7 com agilidade"},
    {id:"rec",  rot:"Recursos ou elementos que não podem faltar", tipo:"textarea", ph:"Ranking de pontuação, som de acerto/erro, níveis de dificuldade crescente", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um designer instrucional especialista em gamificação e prototipagem rápida de jogos educacionais digitais.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema/conteúdo",v.tema)}${L("Plataforma",v.plat)}${L("Tipo de jogo",v.tipo)}${L("Objetivo de aprendizagem",v.obj)}${P("RECURSOS QUE NÃO PODEM FALTAR",v.rec)}

TAREFA
Crie um jogo educacional digital completo sobre o tema informado, pronto para ser jogado pela turma.

FORMATO DA RESPOSTA
1. Nome do jogo e uma frase de pitch.
2. Objetivo pedagógico explícito e conteúdo trabalhado.
3. Regras do jogo, explicadas passo a passo.
4. Estrutura de pontuação, fases ou níveis.
5. Todo o conteúdo usado no jogo (perguntas, desafios, cartas), com a resposta correta de cada item indicada.
6. Instruções de uso para o professor, incluindo como aplicar em sala.
7. Se a plataforma escolhida for “Página HTML em arquivo único”, o código completo (HTML, CSS e JavaScript no mesmo arquivo).
8. Alternativa para o caso de a turma não ter acesso a computador ou internet no momento.

REGRAS
${REGRAS_BASE}
- Se a plataforma escolhida for “Página HTML em arquivo único”, entregue um único arquivo autocontido, sem frameworks nem bibliotecas externas, sem CDN, funcionando totalmente offline.
- Nenhum aluno pode ficar eliminado e sem participar logo no início do jogo; garanta que todos joguem desde o começo.
- Confira que todo o conteúdo usado no jogo (perguntas, fatos, respostas) está correto antes de responder.`
},
{
  id:"quizzes", grupo:"Engajar", origem:"modelo", nome:"Quizzes",
  resumo:"Quiz com perguntas, alternativas e feedback imediato.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema do quiz", ph:"Sistema solar e movimentos da Terra"},
    {id:"n",    rot:"Quantidade de perguntas", tipo:"number", ph:"10", meia:true},
    {id:"form", rot:"Formato de aplicação", tipo:"select", op:["","Papel","Google Forms","Estilo Kahoot (projetado, em grupos)","Oral, em rodada"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Turma gosta de perguntas com imagem/situação; evitar decoreba pura.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em avaliação formativa e elaboração de quizzes educacionais.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema do quiz",v.tema)}${L("Quantidade de perguntas",v.n)}${L("Formato de aplicação",v.form)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Elabore um quiz completo sobre o tema informado, com feedback pedagógico para cada resposta.

FORMATO DA RESPOSTA
1. Título do quiz e uma instrução curta de aplicação, adequada ao formato escolhido.
2. As perguntas numeradas, cada uma com 4 alternativas (A a D).
3. Gabarito de cada pergunta.
4. Para cada alternativa incorreta, um feedback curto que corrige o conceito, não apenas aponta o erro.
5. Nível de dificuldade de cada pergunta (fácil, médio, difícil), variando ao longo do quiz.
6. Passo a passo de como aplicar no formato escolhido.
7. Uma pergunta bônus mais desafiadora, opcional.

REGRAS
${REGRAS_BASE}
- Confira que cada gabarito está correto antes de responder.
- O feedback de cada erro precisa corrigir o conceito, nunca apenas dizer que a resposta está errada.`
},
{
  id:"escape", grupo:"Engajar", origem:"modelo", nome:"Escape room",
  resumo:"Sala de fuga pedagógica com enigmas encadeados sobre o conteúdo.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"História", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema ou conteúdo trabalhado", ph:"Revolução Industrial"},
    {id:"dur",  rot:"Tempo disponível", tipo:"select", op:["","20 minutos","1 aula (50 min)","2 aulas"], meia:true},
    {id:"mat",  rot:"Materiais disponíveis", ph:"Cadeados com senha, envelopes, folhas impressas", meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Missão precisa envolver toda a turma dividida em equipes fixas.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um designer de jogos educacionais especialista em salas de fuga pedagógicas (breakout educacional).

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema/conteúdo",v.tema)}${L("Tempo disponível",v.dur)}${L("Materiais disponíveis",v.mat)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma sala de fuga pedagógica sobre o tema informado, com 4 a 6 enigmas encadeados que só se resolvem aplicando o conteúdo.

FORMATO DA RESPOSTA
1. Narrativa/missão que dá sentido à fuga (2 a 4 linhas).
2. Os enigmas em ordem (de 4 a 6), cada um com: o desafio apresentado, o conteúdo que ele mobiliza, a solução esperada e como ela libera o próximo passo (cadeado, código, envelope).
3. Uma dica de resgate para cada enigma, a ser usada só se a equipe travar.
4. Folha de pistas para entregar às equipes, sem as soluções.
5. Gabarito completo do professor, com todas as soluções e a lógica de cada uma.
6. Lista de materiais necessários, coerente com o que foi informado como disponível.
7. Tempo estimado por enigma, somando o tempo disponível informado.

REGRAS
${REGRAS_BASE}
- Cada enigma precisa ter uma solução verificável e inequívoca, sem depender de sorte ou de conhecimento fora do conteúdo indicado.
- Toda equipe deve poder participar do início ao fim; nenhuma equipe pode “travar” sem ter uma dica de resgate disponível.`
},
{
  id:"caca", grupo:"Engajar", origem:"modelo", nome:"Caça-palavras",
  resumo:"Grade de caça-palavras em texto, com lista de palavras e gabarito.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Língua Portuguesa", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"pal",  rot:"Lista de palavras", tipo:"textarea", ph:"separadas por vírgula (ou deixe em branco e informe o tema abaixo para a IA sugerir as palavras)"},
    {id:"tam",  rot:"Tamanho da grade", tipo:"select", op:["","10x10","12x12","15x15","20x20"], meia:true},
    {id:"dir",  rot:"Direções permitidas", tipo:"select", op:["","Só horizontal e vertical","Horizontal, vertical e diagonal","Todas as direções, inclusive de trás para frente"], meia:true}
  ],
  prompt:v=>
`Aja como um professor especialista em criação de jogos de palavras e materiais lúdicos impressos.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tamanho da grade",v.tam)}${L("Direções permitidas",v.dir)}${P("LISTA DE PALAVRAS",v.pal)}

TAREFA
Crie um caça-palavras completo sobre o tema ou a lista de palavras informada, pronto para imprimir.

FORMATO DA RESPOSTA
1. Lista final de palavras usadas (em maiúsculas, sem acento nem cedilha), com uma dica de cada uma quando a lista não tiver sido fornecida pelo professor.
2. A grade completa, em texto monoespaçado (dentro de um bloco de código), do tamanho informado, com o alfabeto preenchendo os espaços vazios.
3. Confirmação de que todas as palavras couberam na grade, respeitando as direções permitidas.
4. Instruções de aplicação para os alunos.
5. Gabarito: para cada palavra, a posição inicial (linha, coluna) e a direção usada.
6. Versão da grade com as palavras marcadas, para conferência rápida do professor.

REGRAS
${REGRAS_BASE}
- Escreva a grade em fonte monoespaçada, dentro de um bloco de código, sem acento nem cedilha dentro da grade.
- Confira que todas as palavras cabem no tamanho de grade informado antes de responder; se alguma não couber, avise e ajuste a palavra ou o tamanho da grade.`
},
{
  id:"cruzadas", grupo:"Engajar", origem:"modelo", nome:"Palavras cruzadas",
  resumo:"Cruzadinha com definições numeradas, grade em texto e gabarito.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Geografia", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema ou conteúdo", ph:"Relevo e hidrografia do Brasil"},
    {id:"n",    rot:"Quantidade de palavras", tipo:"number", ph:"10", meia:true},
    {id:"tam",  rot:"Tamanho aproximado da grade", tipo:"select", op:["","Pequena (8x8)","Média (12x12)","Grande (15x15)"], meia:true}
  ],
  prompt:v=>
`Aja como um professor especialista em criação de palavras cruzadas educativas.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema/conteúdo",v.tema)}${L("Quantidade de palavras",v.n)}${L("Tamanho aproximado da grade",v.tam)}

TAREFA
Crie uma cruzadinha completa sobre o tema informado, com definições resolvíveis pelo nível do ano/série indicado.

FORMATO DA RESPOSTA
1. Lista das palavras escolhidas (sem acento, em maiúsculas) e por que cada uma é relevante para o tema.
2. Definições numeradas, separadas em “Horizontais” e “Verticais”.
3. A grade vazia, em texto monoespaçado (bloco de código), com a numeração de início de cada palavra.
4. Confirmação de que as letras compartilhadas entre palavras que se cruzam realmente coincidem.
5. Grade preenchida com o gabarito, em texto monoespaçado.
6. Sugestão de como aplicar a atividade (individual, em dupla, impressa).

REGRAS
${REGRAS_BASE}
- As definições precisam ser resolvíveis por um aluno do ano/série informado, sem exigir conhecimento externo ao componente.
- Confira que as letras compartilhadas entre as palavras que se cruzam coincidem antes de responder.`
},
{
  id:"gamificada", grupo:"Engajar", origem:"novo", nome:"Atividade gamificada presencial",
  resumo:"Jogo de sala de aula com materiais simples, roteiro minuto a minuto e roda de conversa.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Conteúdo a trabalhar", ph:"Ciclo da água"},
    {id:"dur",  rot:"Tempo disponível", tipo:"select", op:["","20 minutos","1 aula (50 min)","2 aulas"], meia:true},
    {id:"mat",  rot:"Materiais que a escola já tem", ph:"Bola, giz, cartolina, fichas de papel", meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Turma agitada depois do intervalo; espaço da sala é pequeno.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em gamificação de sala de aula usando apenas materiais simples que a escola já tem.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Conteúdo a trabalhar",v.tema)}${L("Tempo disponível",v.dur)}${L("Materiais disponíveis",v.mat)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Crie uma atividade gamificada presencial sobre o conteúdo informado, usando apenas os materiais indicados.

FORMATO DA RESPOSTA
1. Nome do jogo e objetivo pedagógico.
2. Regras do jogo em poucas frases, fáceis de explicar em até 2 minutos.
3. Lista de materiais necessários, coerente com o que foi informado como disponível.
4. Roteiro minuto a minuto da atividade, do início ao fechamento.
5. Pelo menos 10 itens de conteúdo (perguntas, desafios ou cartas) usados no jogo, todos corretos.
6. Como formar grupos ou duplas sem deixar ninguém de fora no início.
7. Sistema de pontuação ou de progressão do jogo.
8. Roteiro de perguntas para a roda de conversa final, retomando o conteúdo.

REGRAS
${REGRAS_BASE}
- Ninguém pode ficar eliminado logo no início do jogo e sem participar; garanta que todos joguem desde o começo.
- O roteiro minuto a minuto deve somar exatamente o tempo disponível informado.
- Confira que os itens de conteúdo usados no jogo estão corretos.`
},
{
  id:"estudo-caso", grupo:"Engajar", origem:"modelo", nome:"Estudo de caso",
  resumo:"Caso real ou verossímil com dados de apoio, pergunta central e roteiro de discussão.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Biologia", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema ou conceito a ser trabalhado pelo caso", ph:"Uso indiscriminado de antibióticos e resistência bacteriana"},
    {id:"ctx",  rot:"Contexto ou cenário do caso", ph:"Posto de saúde de bairro, hospital, comunidade rural", meia:true},
    {id:"n",    rot:"Número de personagens", tipo:"number", ph:"3", meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Incluir um gráfico simples ou uma tabela de dados no caso.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em metodologia de estudo de caso (case-based learning).

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema/conceito",v.tema)}${L("Contexto/cenário",v.ctx)}${L("Número de personagens",v.n)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Elabore um estudo de caso completo, real ou verossímil, que só possa ser resolvido aplicando o conteúdo informado.

FORMATO DA RESPOSTA
1. Título do caso e uma linha de contexto.
2. Narrativa do caso, com personagens nomeados e o dilema central.
3. Dados de apoio (números, trechos, tabela simples), marcados claramente como fictícios quando forem inventados.
4. Pergunta central que os alunos devem responder.
5. Roteiro de discussão com 5 a 8 perguntas guiadas, da compreensão à análise crítica.
6. Conceitos do componente curricular que precisam ser mobilizados para responder à pergunta central.
7. Critérios para avaliar a resposta dos alunos.
8. Um possível encaminhamento ou desfecho do caso, para fechar a discussão.

REGRAS
${REGRAS_BASE}
- Deixe claro, dentro do texto, quando um dado é fictício, para não ser confundido com informação real.
- A pergunta central só deve ser respondível aplicando de fato o conteúdo do componente informado.`
},
{
  id:"debate", grupo:"Engajar", origem:"modelo", nome:"Debate regrado",
  resumo:"Papéis, tempos de fala e argumentos para os dois lados, com ficha de observação.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Sociologia", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema do debate", ph:"Redes sociais devem ter limite de idade mais rígido?"},
    {id:"n",    rot:"Número de alunos", tipo:"number", ph:"30", meia:true},
    {id:"dur",  rot:"Tempo disponível", tipo:"select", op:["","20 minutos","1 aula (50 min)","2 aulas"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Turma tende a interromper; reforçar regras de conduta.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em debate regrado e argumentação em sala de aula.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema do debate",v.tema)}${L("Número de alunos",v.n)}${L("Tempo disponível",v.dur)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Estruture um debate regrado sobre o tema informado, apresentando os dois lados com a mesma força.

FORMATO DA RESPOSTA
1. Reformulação do tema como uma moção de debate, clara e equilibrada.
2. Divisão de papéis entre os alunos informados (a favor, contra, plateia com função ativa de observação).
3. Pelo menos 3 argumentos principais de cada lado, com força equivalente entre os dois lados.
4. Para cada argumento, um possível contra-argumento do lado oposto.
5. Tempos de fala de cada etapa (abertura, réplica, tréplica, considerações finais), somando o tempo disponível.
6. Ficha de observação para quem não está debatendo, com critérios objetivos (clareza, uso de dados, respeito às regras).
7. Regras de conduta do debate (ordem de fala, interrupção, tempo).
8. Roteiro de fechamento para sistematizar o aprendizado depois do debate.

REGRAS
${REGRAS_BASE}
- Apresente os argumentos dos dois lados com a mesma qualidade e força; não favoreça um lado com argumentos melhores que o outro.
- Se o tema envolver os direitos ou a dignidade de algum grupo de pessoas, isso não deve virar um dos lados do debate — avise o professor e sugira reformular a moção para uma questão controversa, porém pedagogicamente segura.`
},
{
  id:"juri", grupo:"Engajar", origem:"modelo", nome:"Júri simulado",
  resumo:"Julgamento simulado com acusação, defesa, testemunhas, jurados e roteiro cronometrado.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"História", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Caso ou tema a ser julgado", ph:"Julgamento simbólico de uma decisão histórica controversa"},
    {id:"n",    rot:"Número de alunos disponíveis", tipo:"number", ph:"28", meia:true},
    {id:"dur",  rot:"Tempo disponível", tipo:"select", op:["","20 minutos","1 aula (50 min)","2 aulas"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Sala com espaço para separar acusação, defesa e jurados.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em júri simulado como estratégia pedagógica.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Caso/tema a julgar",v.tema)}${L("Número de alunos disponíveis",v.n)}${L("Tempo disponível",v.dur)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Monte um júri simulado completo sobre o caso ou tema informado, distribuindo papéis entre os alunos disponíveis.

FORMATO DA RESPOSTA
1. Descrição do caso a ser julgado, com os fatos e a “acusação” claramente definida (fictícia ou histórica).
2. Lista de papéis (juiz, acusação, defesa, réu quando fizer sentido, testemunhas, jurados) e quantos alunos cada papel ocupa, distribuindo todos os alunos informados.
3. Roteiro de argumentos possíveis para a acusação e para a defesa.
4. Perguntas sugeridas para cada testemunha, e um resumo do que cada testemunha “sabe”.
5. Roteiro cronometrado da sessão (abertura, depoimentos, alegações finais, deliberação), somando o tempo disponível.
6. Critérios de avaliação do veredito para os jurados.
7. Ficha de deliberação para os jurados preencherem.
8. Roteiro de fechamento retomando o conteúdo pedagógico por trás do caso.

REGRAS
${REGRAS_BASE}
- O veredito avalia a qualidade e a coerência da argumentação apresentada em sessão, nunca a opinião pessoal do jurado sobre o tema.
- Distribua papéis para todos os alunos informados, sem deixar ninguém de fora da atividade.`
},
{
  id:"historias", grupo:"Engajar", origem:"modelo", nome:"Histórias infantis",
  resumo:"Narrativa sob medida com personagens, glossário e proposta de atividade.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema ou conteúdo a ensinar", ph:"Cuidado com a água e desperdício"},
    {id:"pers", rot:"Personagens", ph:"Uma formiga curiosa e um sapo desconfiado (opcional)", meia:true},
    {id:"cen",  rot:"Cenário", ph:"Um jardim depois da chuva (opcional)", meia:true},
    {id:"estilo",rot:"Estilo da narrativa", tipo:"select", op:["","Conto de fadas","Aventura","Ficção científica","Fábula com moral","Rima/poema infantil","Livre — sugira o melhor"], meia:true},
    {id:"ext",  rot:"Tamanho da história", tipo:"select", op:["","Curta (1 página)","Média (2 a 3 páginas)","Em capítulos (série)"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Turma adora animais falantes; evitar histórias assustadoras.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um escritor especialista em literatura infantil e histórias com propósito pedagógico.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema/conteúdo",v.tema)}${L("Personagens",v.pers)}${L("Cenário",v.cen)}${L("Estilo",v.estilo)}${L("Tamanho",v.ext)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Escreva uma história infantil completa que ensine o conteúdo informado através da própria trama, no estilo e tamanho escolhidos.

FORMATO DA RESPOSTA
1. Título da história.
2. A história completa, do início ao fim, com o conteúdo pedagógico aparecendo dentro da trama e das falas dos personagens.
3. Glossário com 3 a 6 palavras ou conceitos que os alunos podem não conhecer, com explicação simples.
4. De 4 a 6 perguntas de compreensão sobre a história e sobre o conteúdo trabalhado.
5. Uma proposta de atividade (desenho, dramatização, produção de texto, experimento) para depois da leitura.
6. Sugestão de como contar ou ler a história em sala, com pausas e participação da turma.

REGRAS
${REGRAS_BASE}
- O conteúdo pedagógico deve nascer da trama e dos personagens, nunca aparecer como uma explicação separada colada ao final da história.
- Evite estereótipos de gênero, raça, classe social ou aparência física nos personagens e situações.`
},
{
  id:"filmes", grupo:"Engajar", origem:"modelo", nome:"Filmes nacionais",
  resumo:"Sugestão de filmes brasileiros para um tema, com sinopse, classificação e roteiro de debate.",
  ias:["perplexity","gemini","chatgpt","claude"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Sociologia", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema ou conteúdo a explorar", ph:"Desigualdade social nas grandes cidades brasileiras"},
    {id:"n",    rot:"Quantidade de filmes sugeridos", tipo:"number", ph:"3", meia:true},
    {id:"disp", rot:"Onde o filme deve estar disponível", tipo:"select", op:["","Streaming (qualquer)","Netflix","Prime Video","Globoplay","YouTube gratuito","Não importa, o professor confere depois"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Evitar filmes com cenas de violência explícita.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um curador de cinema brasileiro especialista em uso pedagógico de filmes em sala de aula.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema/conteúdo",v.tema)}${L("Quantidade de filmes",v.n)}${L("Onde deve estar disponível",v.disp)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Sugira filmes nacionais (brasileiros) reais, apropriados para o tema e a faixa etária informados, com material de apoio para uso em sala.

FORMATO DA RESPOSTA
1. Lista de filmes brasileiros reais relacionados ao tema, na quantidade solicitada, cada um com título, ano de lançamento, diretor e classificação indicativa oficial.
2. Sinopse curta de cada filme, destacando a relação com o tema.
3. Para cada filme, um aviso claro de que o professor deve conferir a classificação indicativa e o conteúdo antes de exibir para a turma.
4. Um trecho ou cena de cada filme (com tempo aproximado, quando souber) que mais se conecta ao conteúdo, para exibição parcial quando não houver tempo para o filme inteiro.
5. Roteiro de debate após a exibição, com 5 a 8 perguntas.
6. Proposta de atividade pós-filme conectada ao componente curricular.
7. Onde o filme costuma estar disponível, considerando a preferência informada.

REGRAS
${REGRAS_BASE}
- Indique apenas filmes brasileiros que realmente existem; se não tiver certeza da existência, do diretor, do ano ou de algum detalhe, diga isso claramente em vez de inventar.
- Sempre informe a classificação indicativa oficial e avise que o professor deve conferir o conteúdo do filme antes de exibi-lo para a turma.`
},
{
  id:"documentario", grupo:"Engajar", origem:"modelo", nome:"Roteiro de documentário",
  resumo:"Documentário produzido pelos alunos: pauta, entrevistas, gravação e edição.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Geografia", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema do documentário", ph:"Como a comunidade do entorno da escola lida com o lixo"},
    {id:"n",    rot:"Duração estimada (minutos)", tipo:"number", ph:"5", meia:true},
    {id:"pub",  rot:"Pessoas disponíveis para entrevistar", ph:"Colegas, funcionários da escola, comerciantes do bairro", meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Só temos celular para gravar, sem microfone externo.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um produtor de vídeo especialista em documentários escolares feitos por alunos.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema do documentário",v.tema)}${L("Duração estimada",v.n)}${L("Pessoas disponíveis para entrevistar",v.pub)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Estruture um roteiro de documentário produzido pelos alunos sobre o tema informado, da pauta à edição.

FORMATO DA RESPOSTA
1. Pauta do documentário: pergunta central e ângulo da reportagem.
2. Lista de personagens/pessoas a entrevistar, com o motivo de cada escolha.
3. Roteiro de perguntas para cada entrevistado.
4. Plano de gravação: cenas, locações e ordem de captação, com tempo estimado de cada uma.
5. Roteiro de edição, com a ordem final de cenas, entrevistas e narração, somando a duração estimada.
6. Sugestão de texto de narração, se houver.
7. Cronograma de produção, da pré-produção à entrega final.
8. Orientação sobre autorização de uso de imagem de quem for filmado.

REGRAS
${REGRAS_BASE}
- Sempre oriente que é preciso obter autorização de uso de imagem de toda pessoa filmada ou entrevistada, com autorização do responsável quando for menor de idade.
- O roteiro de edição deve caber dentro da duração estimada informada.`
},
{
  id:"podcast", grupo:"Engajar", origem:"novo", nome:"Roteiro de podcast ou vídeo",
  resumo:"Script com marcação de tempo e fala por extenso, pronto para gravar.",
  ias:["notebooklm","chatgpt","claude","gemini"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Filosofia", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Tema do episódio", ph:"O que é uma fake news e por que caímos nelas"},
    {id:"dur",  rot:"Duração do episódio", tipo:"select", op:["","3 minutos","5 minutos","10 minutos","15 minutos","20 minutos"], meia:true},
    {id:"form", rot:"Formato", tipo:"select", op:["","Podcast (áudio)","Vídeo curto","Vídeo-aula"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Dois locutores conversando, tom leve e bem-humorado.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um roteirista especialista em podcasts e vídeos educacionais.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tema do episódio",v.tema)}${L("Duração",v.dur)}${L("Formato",v.form)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Escreva um roteiro completo de podcast ou vídeo sobre o tema informado, com marcação de tempo e fala por extenso.

FORMATO DA RESPOSTA
1. Título do episódio e uma frase de chamada.
2. Estrutura em blocos (abertura, desenvolvimento, encerramento), com o tempo de cada bloco.
3. Roteiro com marcação de tempo (ex.: 00:00–00:30) e a fala por extenso de cada trecho, pronta para ser lida ou gravada.
4. Indicação de trocas de locutor, se houver mais de um.
5. Sugestão de efeitos sonoros, pausas ou trilha, quando fizer sentido.
6. Pergunta ou chamada de encerramento para engajar quem está ouvindo ou assistindo.
7. Contagem aproximada de palavras faladas em cada bloco.

REGRAS
${REGRAS_BASE}
- Calcule a fala a partir de cerca de 130 palavras faladas por minuto e ajuste o roteiro para caber exatamente na duração informada.
- Escreva a fala por extenso, pronta para ser lida em voz alta, não em tópicos.`
},
{
  id:"situacao", grupo:"Engajar", origem:"novo", nome:"Situação-problema",
  resumo:"Problema autêntico e contextualizado que só se resolve com o conteúdo da aula.",
  ias:["claude","chatgpt","gemini","deepseek"],
  campos:[
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tema", rot:"Conteúdo da aula a ser mobilizado", ph:"Regra de três e porcentagem"},
    {id:"local",rot:"Contexto local", ph:"Feira do bairro, mercadinho da esquina, transporte escolar", meia:true},
    {id:"n",    rot:"Número de perguntas intermediárias", tipo:"number", ph:"4", meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Turma trabalha em grupos de 4; incluir uma tabela simples de dados.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um professor especialista em ensino por situações-problema e contextualização.

CONTEXTO${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Conteúdo a mobilizar",v.tema)}${L("Contexto local",v.local)}${L("Número de perguntas intermediárias",v.n)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Elabore uma situação-problema autêntica, ambientada no contexto local informado, que só possa ser resolvida aplicando o conteúdo da aula.

FORMATO DA RESPOSTA
1. Situação-problema narrada em um contexto real e próximo da vida dos alunos, usando o contexto local informado.
2. Pergunta central que os alunos precisam responder.
3. Perguntas intermediárias, na quantidade informada, que guiam o raciocínio até a pergunta central.
4. Dados ou informações necessárias para resolver o problema, incluídos no próprio enunciado.
5. Conceitos do componente curricular que precisam ser mobilizados em cada etapa.
6. Critérios de avaliação da resposta, do básico ao aprofundado.
7. Uma possível resolução esperada, para conferência do professor.

REGRAS
${REGRAS_BASE}
- A situação só deve ser resolvível de fato aplicando o conteúdo do componente informado, não apenas senso comum.
- Use um contexto local plausível e respeitoso com a realidade informada, sem estereótipos.`
},
/* ===================== PESQUISAR ===================== */
{
  id:"videos", grupo:"Pesquisar", origem:"novo", nome:"Encontrar vídeos para a aula",
  resumo:"Vídeos separados por duração, com minutagem dos trechos que valem a pena.",
  ias:["perplexity","gemini","chatgpt","claude"],
  campos:[
    {id:"tema", rot:"Tema", ph:"Ciclo do carbono e efeito estufa"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Biologia", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"faixa",rot:"Duração desejada", tipo:"select", op:["","Curtos — até 8 minutos","Média duração — de 8 a 20 minutos","Longos — de 20 a 45 minutos","Muito longos — acima de 45 minutos","Qualquer duração, classificando por faixa"], meia:true},
    {id:"uso",  rot:"Para que vai usar", tipo:"select", op:["","Disparar a aula (gancho inicial)","Explicar o conteúdo","Aprofundar depois da aula","Passar inteiro em sala","Estudo em casa","Formação do professor"], meia:true},
    {id:"idioma",rot:"Idioma", tipo:"select", op:["","Português do Brasil","Português (Brasil ou Portugal)","Inglês com legenda em português","Espanhol","Qualquer idioma"], meia:true},
    {id:"plat", rot:"Onde procurar", tipo:"select", op:["","YouTube","Canais de universidades e institutos","TV Escola, Canal Futura e afins","Khan Academy","Qualquer plataforma gratuita"], meia:true},
    {id:"n",    rot:"Quantos vídeos", tipo:"number", ph:"8", meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"A turma tem pouca base em química; evitar vídeo com muita fórmula. A escola só tem projetor sem som bom.", dica:"Opcional, mas melhora bastante a seleção."}
  ],
  prompt:v=>
`Aja como um professor curador de recursos audiovisuais para a educação básica, com acesso a busca na internet. Use a busca antes de responder.

CONTEXTO${L("Tema",v.tema)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Duração desejada",v.faixa)}${L("Uso pretendido",v.uso)}${L("Idioma",v.idioma)}${L("Onde procurar",v.plat)}${L("Quantidade de vídeos",v.n)}${P("OBSERVAÇÕES",v.obs)}

TAREFA
Encontre vídeos que realmente existam sobre este tema e organize-os por faixa de duração.

FAIXAS DE DURAÇÃO (use exatamente estas)
- CURTO: até 8 minutos
- MÉDIA DURAÇÃO: mais de 8 até 20 minutos
- LONGO: mais de 20 até 45 minutos
- MUITO LONGO: acima de 45 minutos

FORMATO DA RESPOSTA
1. Agrupe os vídeos por faixa de duração, com a faixa como subtítulo. Se eu pedi uma faixa específica, priorize-a, mas indique no final se encontrou algo muito bom em outra faixa.
2. Para cada vídeo, informe: título exato, canal ou instituição responsável, link completo, duração real, faixa em que se encaixa, ano de publicação.
3. Resumo do vídeo em 2 linhas e o que ele explica bem.
4. Trecho aproveitável com minutagem (de 04:12 a 07:30, por exemplo) e o que acontece nesse trecho — especialmente importante nos vídeos longos, para eu não passar o vídeo inteiro.
5. Como usar em aula: antes, durante ou depois do conteúdo, e 3 perguntas para fazer à turma depois de assistir.
6. Alertas: publicidade, linguagem inadequada, erro conceitual conhecido, conteúdo desatualizado ou vídeo que exige conhecimento prévio.
7. Ao final, uma tabela-resumo com título, duração, faixa e link.
8. Cinco termos de busca prontos para eu procurar mais vídeos por conta própria.

REGRAS
${REGRAS_BASE}
- Indique apenas vídeos que você tem motivo para acreditar que existem e estão públicos. NUNCA invente título, canal, duração ou endereço.
- Para cada vídeo, diga o grau de certeza: confirmado, provável ou não confirmado. Se for “não confirmado”, entregue o termo de busca em vez do link.
- Duração e minutagem aproximadas devem vir marcadas como aproximadas.
- Avise, no início, que os links precisam ser abertos e assistidos pelo professor antes de irem para a sala.`
},
{
  id:"sites", grupo:"Pesquisar", origem:"novo", nome:"Sites de referência para a aula",
  resumo:"Fontes confiáveis para preparar o conteúdo, classificadas por tipo e confiabilidade.",
  ias:["perplexity","gemini","chatgpt","claude"],
  campos:[
    {id:"tema", rot:"Tema ou conteúdo", ph:"Energias renováveis e biocombustíveis"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Química", meia:true},
    {id:"ano",  rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tipo", rot:"Tipo de recurso", tipo:"select", op:["","Textos e materiais de aprofundamento","Planos de aula e sequências prontas","Simuladores e laboratórios virtuais","Bancos de imagens, mapas e infográficos","Exercícios e bancos de questões","Vídeos e podcasts","Dados e estatísticas oficiais","Um pouco de cada tipo"], meia:true},
    {id:"acesso",rot:"Condição de acesso", tipo:"select", op:["","Só gratuito e sem cadastro","Gratuito, cadastro tudo bem","Pode incluir opções pagas, sinalizando o preço"], meia:true},
    {id:"idioma",rot:"Idioma", tipo:"select", op:["","Português do Brasil","Português ou espanhol","Qualquer idioma, com aviso"], meia:true},
    {id:"n",    rot:"Quantos sites", tipo:"number", ph:"10", meia:true},
    {id:"obs",  rot:"O que você já usa ou quer evitar", tipo:"textarea", ph:"Já uso o PhET e a Nova Escola. Procuro coisa com dado brasileiro e que abra em celular.", dica:"Opcional."}
  ],
  prompt:v=>
`Aja como um bibliotecário escolar especializado em curadoria de fontes digitais para professores, com acesso a busca na internet. Use a busca antes de responder.

CONTEXTO${L("Tema",v.tema)}${L("Componente",v.comp)}${L("Ano/série",v.ano)}${L("Tipo de recurso",v.tipo)}${L("Condição de acesso",v.acesso)}${L("Idioma",v.idioma)}${L("Quantidade",v.n)}${P("O QUE JÁ USO OU QUERO EVITAR",v.obs)}

TAREFA
Monte uma curadoria de sites confiáveis que me ajudem a preparar aulas sobre este tema.

FORMATO DA RESPOSTA
1. Tabela principal com: nome do site, endereço completo, o que é, quem mantém (universidade, órgão público, instituto, ONG, editora, empresa ou pessoa física), tipo de recurso e se exige cadastro.
2. Para cada site, um parágrafo curto dizendo exatamente o que aproveitar ali para este tema — a página, a seção ou o material específico, não só a home.
3. Classificação de confiabilidade de cada fonte, em três níveis, com justificativa de uma linha:
   ALTA — órgão oficial, universidade, periódico científico ou instituto reconhecido;
   MÉDIA — portal educacional consolidado, com autoria identificada;
   USAR COM CUIDADO — blog, conteúdo sem autoria ou com viés comercial.
4. Separe explicitamente as fontes primárias (dados oficiais, documentos, pesquisa) das fontes de divulgação (resumos, matérias, portais).
5. Três sites que servem para o aluno pesquisar sozinho, com o nível de leitura indicado.
6. O que NÃO usar neste tema e por quê (páginas com desinformação frequente, conteúdo desatualizado, sites de trabalho pronto).
7. Cinco buscas prontas para eu continuar a curadoria sozinho, incluindo buscas com filtro de domínio, como termo seguido de site:gov.br ou site:edu.br.

REGRAS
${REGRAS_BASE}
- Indique apenas sites que você tem motivo para acreditar que existem e estão no ar. NUNCA invente endereço.
- Marque cada indicação como confirmada, provável ou não confirmada. Endereço não confirmado deve virar sugestão de busca, não link.
- Priorize domínios .gov.br, .edu.br, universidades, institutos de pesquisa e periódicos, antes de portais comerciais.
- Avise que todo link precisa ser aberto e conferido pelo professor antes de ir para os alunos.`
},
{
  id:"artigos", grupo:"Pesquisar", origem:"novo", nome:"Buscar artigos acadêmicos",
  resumo:"Referências de bases gratuitas para fundamentar projetos, com strings de busca prontas.",
  ias:["perplexity","gemini","chatgpt","claude"],
  campos:[
    {id:"tema", rot:"Pergunta ou tema da pesquisa", ph:"Como a gamificação afeta o engajamento em aulas de matemática no Ensino Fundamental II?", dica:"Quanto mais parecido com uma pergunta, melhor o resultado."},
    {id:"area", rot:"Área", tipo:"lista", ph:"Educação matemática", meia:true},
    {id:"ano",  rot:"Etapa de ensino estudada", tipo:"select", op:ANOS, meia:true},
    {id:"per",  rot:"Recorte temporal", tipo:"select", op:["","Últimos 3 anos","Últimos 5 anos","Últimos 10 anos","Sem limite de data"], meia:true},
    {id:"tipo", rot:"Tipo de produção", tipo:"select", op:["","Artigos de periódico","Anais de congresso","Dissertações e teses","Revisões de literatura","Relatos de experiência","Todos os tipos"], meia:true},
    {id:"idioma",rot:"Idioma", tipo:"select", op:["","Português","Português e inglês","Português, inglês e espanhol"], meia:true},
    {id:"n",    rot:"Quantas referências", tipo:"number", ph:"10", meia:true},
    {id:"fim",  rot:"Para que serve", tipo:"select", op:["","Fundamentar um projeto da escola","Escrever a justificativa de um TCC ou artigo","Embasar uma prática de sala de aula","Conhecer o estado da arte do tema","Preparar formação para colegas"], meia:true},
    {id:"obs",  rot:"Observações", tipo:"textarea", ph:"Preciso de trabalhos com escola pública brasileira. Já tenho o artigo do Fardo (2013).", dica:"Opcional."}
  ],
  prompt:v=>
`Aja como um pesquisador em educação, experiente em revisão de literatura, com acesso a busca na internet. Use a busca antes de responder.

CONTEXTO${L("Área",v.area)}${L("Etapa de ensino estudada",v.ano)}${L("Recorte temporal",v.per)}${L("Tipo de produção",v.tipo)}${L("Idioma",v.idioma)}${L("Quantidade de referências",v.n)}${L("Finalidade",v.fim)}${P("PERGUNTA OU TEMA DA PESQUISA",v.tema)}${P("OBSERVAÇÕES",v.obs)}

BASES GRATUITAS PARA CONSULTAR
- Google Acadêmico — scholar.google.com.br
- SciELO Brasil — scielo.br
- Portal de Periódicos CAPES, seção de acesso aberto — periodicos.capes.gov.br
- BDTD, teses e dissertações brasileiras — bdtd.ibict.br
- SOL, biblioteca digital da Sociedade Brasileira de Computação — sol.sbc.org.br
- RENOTE, Revista Novas Tecnologias na Educação, UFRGS — seer.ufrgs.br/renote
- DOAJ, periódicos de acesso aberto — doaj.org
- ERIC, base internacional de educação — eric.ed.gov
- Redalyc — redalyc.org
- LA Referencia, repositórios da América Latina — lareferencia.redclara.net
- Repositórios institucionais das universidades federais e estaduais
- Periódicos brasileiros de educação: Revista Brasileira de Educação (ANPEd), Educação e Pesquisa (USP), Educação & Realidade (UFRGS), Educação em Revista (UFMG), Ensaio: Avaliação e Políticas Públicas em Educação, Revista Brasileira de Estudos Pedagógicos (INEP)
- Anais de eventos: SBIE, WIE, CBIE, ENPEC, ENEM (Encontro Nacional de Educação Matemática), ANPEd

TAREFA
Levante referências que sustentem essa pesquisa, usando apenas material de acesso gratuito.

FORMATO DA RESPOSTA
1. Reescreva minha pergunta em uma pergunta de pesquisa bem delimitada e liste os descritores (palavras-chave) em português e em inglês.
2. Tabela de referências, uma por linha: autores, ano, título, periódico ou evento, base onde está, link direto, se o texto completo é aberto, e o grau de certeza de que a referência existe (confirmada, provável, não confirmada).
3. Para cada referência: resumo em até 3 linhas e uma frase dizendo como ela se conecta à minha pergunta.
4. Agrupe as referências por eixo temático, mostrando quais concordam e quais divergem entre si.
5. Lista das referências em formato ABNT, pronta para copiar.
6. Strings de busca prontas para colar em cada base, com operadores (aspas, AND, OR, filtros de data). Uma string por base.
7. Lacunas: o que a literatura ainda não responde sobre o tema, e como o projeto do professor pode se posicionar nessa lacuna.
8. Três autores ou grupos de pesquisa brasileiros que são referência no assunto.

REGRAS
${REGRAS_BASE}
- Esta é a regra mais importante: NUNCA invente uma referência. Modelos de linguagem costumam criar artigos, DOIs e nomes de autores que não existem.
- Se não conseguir confirmar que um trabalho existe, classifique como “não confirmada” e entregue no lugar a string de busca para eu procurar. É melhor devolver 6 referências reais do que 10 com 4 inventadas.
- Não escreva o resumo de um artigo que você não leu: se estiver descrevendo pelo título, diga isso explicitamente.
- Priorize produção brasileira e latino-americana quando o tema envolver a escola brasileira.
- Ao final, deixe claro que cada link precisa ser aberto e conferido antes de entrar no projeto.`
},
{
  id:"trechos", grupo:"Pesquisar", origem:"novo", nome:"Trechos para citar no projeto",
  resumo:"Extrai citações literais dos artigos e monta a amarração com o seu texto.",
  ias:["claude","chatgpt","gemini","notebooklm"],
  campos:[
    {id:"texto",rot:"Texto dos artigos", tipo:"textarea", grande:true, ph:"Cole aqui o texto do artigo, o capítulo ou os trechos que você já separou. Se forem vários, separe com uma linha contendo três hifens (---) e escreva antes o autor e o ano.", dica:"É daqui que as citações vão sair. Sem o texto colado, a IA não tem de onde citar."},
    {id:"refs", rot:"Referências dos textos colados", tipo:"textarea", ph:"FARDO, M. L. A gamificação aplicada em ambientes de aprendizagem. RENOTE, v. 11, n. 1, 2013.", dica:"Uma por linha, do jeito que você tiver. A IA formata depois."},
    {id:"proj", rot:"Tema do seu projeto", ph:"Gamificação para reduzir a evasão nas aulas de matemática do 8º ano"},
    {id:"secao",rot:"Seção que você está escrevendo", tipo:"select", op:["","Introdução","Justificativa","Referencial teórico","Metodologia","Resultados esperados","Considerações finais","Todas as seções"], meia:true},
    {id:"n",    rot:"Quantos trechos", tipo:"number", ph:"12", meia:true},
    {id:"norma",rot:"Norma de citação", tipo:"select", op:["","ABNT (NBR 10520)","APA","Vancouver"], meia:true},
    {id:"tom",  rot:"Tipo de texto", tipo:"select", op:["","Projeto escolar","Artigo ou TCC acadêmico","Relatório para a secretaria de educação","Projeto para edital ou financiamento"], meia:true}
  ],
  prompt:v=>
`Aja como um orientador acadêmico ajudando um professor a fundamentar um projeto.

CONTEXTO${L("Tema do projeto",v.proj)}${L("Seção em construção",v.secao)}${L("Quantidade de trechos",v.n)}${L("Norma de citação",v.norma)}${L("Tipo de texto",v.tom)}${P("REFERÊNCIAS DOS TEXTOS",v.refs)}${P("TEXTO DOS ARTIGOS",v.texto)}

TAREFA
Extraia dos textos acima os trechos que servem para fundamentar este projeto e mostre como usá-los.

FORMATO DA RESPOSTA
1. Tabela de trechos, uma linha por trecho, com as colunas:
   - CITAÇÃO LITERAL, entre aspas, copiada exatamente do texto, sem alterar nenhuma palavra
   - LOCALIZAÇÃO (página, seção ou o número do texto colado)
   - AUTOR E ANO, no formato da norma escolhida
   - SEÇÃO DO PROJETO em que o trecho cabe melhor
   - O QUE O TRECHO SUSTENTA, em uma frase
2. Para cada trecho, entregue também:
   - a versão parafraseada, com minhas palavras, mantendo o sentido e a citação indireta correta;
   - uma frase de amarração ligando o trecho ao meu projeto — o texto que vem logo depois da citação.
3. Separe os trechos em citações curtas (até 3 linhas, entre aspas no corpo do texto) e citações longas (com recuo), já formatadas na norma escolhida.
4. Um parágrafo-modelo pronto para a seção que estou escrevendo, encadeando três dos trechos com as amarrações — para eu ver como fica o texto final.
5. Lista das referências completas, na norma escolhida, na ordem correta.
6. O que ainda falta: quais afirmações do meu projeto continuam sem apoio nos textos colados e que tipo de fonte eu preciso procurar para elas.

REGRAS
${REGRAS_BASE}
- Regra absoluta: só é permitido citar o que está literalmente escrito no texto que eu colei. Não invente frases, não complete citações, não atribua ao autor nada que ele não escreveu.
- Se eu não colei o texto, ou colei só referências e links, não invente citações: diga que precisa do texto integral e liste o que devo colar.
- Se o texto colado não sustentar o número de trechos pedido, entregue menos e explique por quê.
- Nunca mude palavras dentro das aspas. Corte só é permitido com reticências entre colchetes.
- Ao parafrasear, mude a estrutura da frase, não apenas os sinônimos — e mantenha a indicação de autoria.`
},
/* ===================== MATERIAIS ===================== */
{
  id:"slides", grupo:"Materiais", origem:"modelo", nome:"Slides",
  resumo:"Roteiro slide a slide, com fala do professor e imagem sugerida.",
  ias:["gamma","canva","chatgpt","claude"],
  campos:[
    {id:"tit",  rot:"Título da apresentação", ph:"Fotossíntese: como as plantas produzem energia"},
    {id:"txt",  rot:"Texto base (opcional)", tipo:"textarea", grande:true, ph:"Cole aqui um texto, resumo ou conteúdo que os slides devem seguir...", dica:"opcional — se não colar nada, a IA monta o conteúdo a partir do tema"},
    {id:"comp", rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"pub",  rot:"Ano / série (público-alvo)", tipo:"select", op:ANOS, meia:true},
    {id:"n",    rot:"Número de slides", tipo:"number", ph:"12", meia:true},
    {id:"est",  rot:"Estilo", tipo:"select", op:["","Profissional","Criativo","Minimalista","Educacional","Narrativo"], meia:true},
    {id:"instr",rot:"Instruções adicionais", tipo:"textarea", ph:"Ex.: terminar com um slide de atividade prática.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um designer instrucional especialista em criar apresentações educacionais claras e objetivas.

CONTEXTO${L("Título",v.tit)}${L("Componente curricular",v.comp)}${L("Ano/série",v.pub)}${L("Número de slides",v.n)}${L("Estilo",v.est)}${P("TEXTO BASE",v.txt)}${P("INSTRUÇÕES ADICIONAIS",v.instr)}

TAREFA
Crie o roteiro completo da apresentação, slide a slide, pronto para eu colar em uma ferramenta de slides.

FORMATO DA RESPOSTA
1. Slide 1: título da apresentação e subtítulo.
2. Para cada slide seguinte, no formato:
   - Título do slide
   - Conteúdo do slide (máximo 25 palavras, em tópicos curtos)
   - Fala do professor (o que dizer enquanto o slide está na tela)
   - Imagem sugerida (descrição curta do que ilustrar)
   - Pergunta de engajamento para a turma (quando fizer sentido)
3. Último slide: fechamento com síntese ou chamada para a próxima etapa.
4. Ao final, uma sugestão de tempo total de apresentação.

REGRAS
${REGRAS_BASE}
- Nunca coloque parágrafo longo dentro do slide: o texto do slide é sempre em tópicos curtos, a explicação completa vai na fala do professor.
- Respeite rigorosamente o número de slides pedido.`
},
{
  id:"imagens", grupo:"Materiais", origem:"modelo", nome:"Gerar imagens",
  resumo:"Comando pronto para gerar uma imagem educacional em ferramentas de IA.",
  ias:["chatgpt","gemini","ideogram","leonardo","bingimg","canva"],
  campos:[
    {id:"cena",   rot:"Descrição da cena", tipo:"textarea", grande:true, ph:"Uma sala de aula colorida com crianças plantando mudas em um jardim escolar, sob luz natural, estilo ilustração."},
    {id:"uso",    rot:"Uso pretendido", tipo:"select", op:["","Capa de slide","Ilustração de atividade","Cartaz","Material impresso","Post para redes sociais","Fundo decorativo"], meia:true},
    {id:"estilo", rot:"Estilo artístico", tipo:"select", op:["","Fotorrealista","Ilustração plana (flat design)","Aquarela","Desenho infantil","Cartum","3D renderizado","Minimalista"], meia:true},
    {id:"tema",   rot:"Tema", ph:"Sustentabilidade e meio ambiente", meia:true},
    {id:"ilum",   rot:"Iluminação", tipo:"select", op:["","Luz natural diurna","Pôr do sol","Ambiente interno neutro","Dramática","Suave e difusa"], meia:true},
    {id:"cores",  rot:"Cores predominantes", ph:"Tons de verde e azul", meia:true},
    {id:"detalhe",rot:"Nível de detalhe", tipo:"select", op:["","Simples","Médio","Alto detalhamento"], meia:true},
    {id:"prop",   rot:"Proporção", tipo:"select", op:["","Quadrada (1:1)","Paisagem (16:9)","Retrato (9:16)","Widescreen (4:3)"], meia:true},
    {id:"evitar", rot:"O que evitar", ph:"Textos, rostos de pessoas reais, marcas", meia:true}
  ],
  prompt:v=>
`Gere uma imagem com as seguintes especificações.

CENA
${(v.cena&&v.cena.trim())||"—"}

ESPECIFICAÇÕES${L("Uso pretendido",v.uso)}${L("Estilo artístico",v.estilo)}${L("Tema",v.tema)}${L("Iluminação",v.ilum)}${L("Cores predominantes",v.cores)}${L("Nível de detalhe",v.detalhe)}${L("Proporção",v.prop)}${L("O que evitar",v.evitar)}

DIRETRIZES
- Composição limpa, com espaço livre para adicionar texto por cima depois, se for o caso.
- Conteúdo apropriado para ambiente escolar: sem violência, sem conteúdo sexual, sem estereótipos ofensivos.
- Não escrever nenhum texto dentro da imagem, a menos que isso tenha sido pedido explicitamente.
- Não reproduzir pessoas reais, marcas registradas ou personagens protegidos por direitos autorais.`
},
{
  id:"mapas", grupo:"Materiais", origem:"modelo", nome:"Mapas mentais",
  resumo:"Conceito central, ramos, subtópicos e conexões, no formato que você precisar.",
  ias:["claude","chatgpt","napkin","gemini"],
  campos:[
    {id:"central",rot:"Conceito central", ph:"Sistema Solar"},
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"Ciências", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"ramos",  rot:"Ramos principais (se já tiver ideia)", ph:"Planetas, Sol, satélites naturais, cometas...", dica:"opcional", meia:true},
    {id:"sub",    rot:"Nível de detalhe", tipo:"select", op:["","Só os ramos principais","Ramos + 2 níveis de subtópicos","Bem detalhado, com exemplos em cada ramo"], meia:true},
    {id:"conex",  rot:"Conexões cruzadas a destacar", tipo:"textarea", ph:"Ex.: relação entre gravidade e formato da órbita.", dica:"opcional"},
    {id:"saida",  rot:"Formato de saída", tipo:"select", op:["","Lista hierárquica em texto","Código Mermaid (para renderizar)","Tabela de tópicos e subtópicos","Instruções para desenhar no quadro"]}
  ],
  prompt:v=>
`Aja como um especialista em organização visual do conhecimento e mapas mentais para uso educacional.

CONTEXTO${L("Conceito central",v.central)}${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Ramos principais sugeridos",v.ramos)}${L("Nível de detalhe",v.sub)}${P("CONEXÕES CRUZADAS A DESTACAR",v.conex)}${L("Formato de saída",v.saida)}

TAREFA
Crie um mapa mental completo sobre o conceito central, organizado em ramos e subtópicos.

FORMATO DA RESPOSTA
1. Conceito central destacado no topo.
2. Ramos principais numerados.
3. Subtópicos de cada ramo, no nível de detalhe pedido.
4. Conexões cruzadas entre ramos diferentes, quando fizer sentido.
5. Entrega no formato de saída solicitado.
6. Se for texto hierárquico, use indentação clara com marcadores.
7. Uma sugestão de como usar esse mapa em sala de aula.

REGRAS
${REGRAS_BASE}
- Se o formato escolhido for código Mermaid, entregue o código dentro de um bloco de código (\`\`\`mermaid), usando sintaxe válida de mindmap ou flowchart.
- Não invente subtópicos sem relação real com o conceito central.`
},
{
  id:"infografico", grupo:"Materiais", origem:"novo", nome:"Infográfico",
  resumo:"Roteiro pronto de infográfico: blocos, hierarquia visual, textos e paleta.",
  ias:["canva","chatgpt","claude","gemini"],
  campos:[
    {id:"tema",   rot:"Tema do infográfico", ph:"Impactos do desmatamento na Amazônia"},
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"Geografia", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"dado",   rot:"Dado ou mensagem principal", ph:"Área desmatada equivale a X campos de futebol por minuto", meia:true},
    {id:"nblocos",rot:"Número de blocos de informação", tipo:"number", ph:"5", meia:true},
    {id:"est",    rot:"Estilo visual", tipo:"select", op:["","Profissional","Colorido e lúdico","Minimalista","Científico"], meia:true},
    {id:"paleta", rot:"Paleta de cores preferida", ph:"Tons de verde e terra", dica:"opcional", meia:true},
    {id:"txt",    rot:"Texto base / fonte dos dados", tipo:"textarea", grande:true, ph:"Cole aqui dados, trechos de texto ou a referência que embasa o infográfico..."}
  ],
  prompt:v=>
`Aja como um designer de informação especialista em infográficos educacionais.

CONTEXTO${L("Tema",v.tema)}${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Dado ou mensagem principal",v.dado)}${L("Número de blocos",v.nblocos)}${L("Estilo visual",v.est)}${L("Paleta de cores",v.paleta)}${P("TEXTO BASE / FONTE DOS DADOS",v.txt)}

TAREFA
Crie o roteiro completo de um infográfico, pronto para ser montado em uma ferramenta de design.

FORMATO DA RESPOSTA
1. Título de impacto (máximo 8 palavras).
2. Dado ou mensagem principal em destaque.
3. Lista de blocos de informação, cada um com: título curto, texto já pronto (máximo 30 palavras) e ícone sugerido.
4. Hierarquia visual sugerida — o que deve ser maior, o que vem primeiro, o que vem por último.
5. Paleta de cores sugerida, com nomes ou códigos aproximados.
6. Fonte/rodapé sugerido.
7. Observações de diagramação para quem for montar a peça.

REGRAS
${REGRAS_BASE}
- Todo número ou estatística apresentada deve vir acompanhado da marcação “[fonte a conferir]”, a menos que a fonte já tenha sido informada no texto base.
- Os textos de cada bloco devem ser curtos e já prontos para copiar, sem enrolação.`
},
{
  id:"planilha", grupo:"Materiais", origem:"novo", nome:"Planilha do professor",
  resumo:"Estrutura de planilha com colunas, fórmulas prontas e formatação condicional.",
  ias:["chatgpt","claude","gemini","copilot"],
  campos:[
    {id:"tipo",     rot:"Tipo de planilha", tipo:"select", op:["","Controle de notas","Frequência","Acompanhamento de habilidades/competências","Controle de entregas de atividades","Diário de classe simplificado"]},
    {id:"comp",     rot:"Componente curricular", tipo:"lista", ph:"Matemática", meia:true},
    {id:"ano",      rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"ferramenta",rot:"Ferramenta", tipo:"select", op:["","Google Sheets","Excel"], meia:true},
    {id:"nalunos",  rot:"Número de alunos", tipo:"number", ph:"32", meia:true},
    {id:"crit",     rot:"Critérios ou colunas específicas que precisa", tipo:"textarea", ph:"Ex.: nota de prova, nota de trabalho, participação, recuperação...", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um especialista em planilhas para gestão escolar, com domínio de fórmulas do Excel e do Google Sheets.

CONTEXTO${L("Tipo de planilha",v.tipo)}${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Ferramenta",v.ferramenta)}${L("Número de alunos",v.nalunos)}${P("CRITÉRIOS OU COLUNAS ESPECÍFICAS",v.crit)}

TAREFA
Monte a estrutura completa de uma planilha pronta para eu criar e usar.

FORMATO DA RESPOSTA
1. Lista de colunas na ordem exata em que devem aparecer, com a letra da coluna (A, B, C...).
2. Linha de cabeçalho sugerida, pronta para colar.
3. Fórmulas necessárias (médias, totais, situação do aluno, alertas), cada uma indicando exatamente em qual célula ela vai e qual é a fórmula completa.
4. Regras de formatação condicional sugeridas (o que destacar e com qual condição/cor).
5. Uma linha de exemplo já preenchida, mostrando como usar.
6. Dicas de proteção de células e organização em abas, se fizer sentido.

REGRAS
${REGRAS_BASE}
- Entregue as fórmulas exatas, prontas para colar, sempre indicando em qual célula cada uma deve ser inserida.
- Use a sintaxe compatível com a ferramenta informada; se não for informada, ofereça as duas versões quando forem diferentes.
- Nunca use nome completo de aluno nos exemplos — use apenas iniciais.`
},

/* ===================== COMUNICAR ===================== */
{
  id:"comunicado", grupo:"Comunicar", origem:"novo", nome:"Comunicado aos responsáveis",
  resumo:"Bilhete, e-mail ou mensagem de WhatsApp pronta, no tom certo.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"assunto",rot:"Assunto do comunicado", ph:"Mudança de horário da reunião de pais"},
    {id:"canal",  rot:"Canal", tipo:"select", op:["","Bilhete impresso","E-mail","WhatsApp","Mural / agenda escolar"], meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"tom",    rot:"Tom", tipo:"select", op:["","Formal","Cordial e direto","Acolhedor","Urgente"], meia:true},
    {id:"prazo",  rot:"Prazo ou data-limite (se houver)", ph:"Até sexta-feira, dia 28", meia:true},
    {id:"pontos", rot:"Pontos que precisam entrar no texto", tipo:"textarea", ph:"O que aconteceu, o que muda, o que os responsáveis precisam fazer, até quando."}
  ],
  prompt:v=>
`Aja como um coordenador escolar especialista em comunicação clara com famílias.

CONTEXTO${L("Assunto",v.assunto)}${L("Canal",v.canal)}${L("Ano/série",v.ano)}${L("Tom desejado",v.tom)}${L("Prazo/data-limite",v.prazo)}${P("PONTOS QUE PRECISAM ENTRAR NO TEXTO",v.pontos)}

TAREFA
Escreva o comunicado pronto para eu enviar aos responsáveis, no canal indicado.

FORMATO DA RESPOSTA
1. Título ou assunto da mensagem.
2. Texto do comunicado, já formatado para o canal escolhido (com saudação e despedida quando fizer sentido).
3. Se houver prazo ou ação esperada dos responsáveis, destaque isso em frase separada.
4. Uma versão resumida, para o caso de precisar enviar por WhatsApp/mural mesmo que o canal escolhido seja outro.

REGRAS
${REGRAS_BASE}
- Sem jargão pedagógico: escreva como quem fala com uma família, não como quem fala com outro professor.
- Nunca exponha informação de nenhum aluno específico em um comunicado coletivo — trate a turma como grupo.`
},
{
  id:"reuniao", grupo:"Comunicar", origem:"novo", nome:"Reunião de pais",
  resumo:"Roteiro cronometrado, do que dizer sobre desempenho até a ata final.",
  ias:["chatgpt","claude","gemini"],
  campos:[
    {id:"comp",  rot:"Componente curricular / papel na turma", tipo:"lista", ph:"Professor(a) regente", meia:true},
    {id:"ano",   rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"dur",   rot:"Duração da reunião", tipo:"select", op:["","30 minutos","45 minutos","1 hora","1h30"], meia:true},
    {id:"foco",  rot:"Foco principal da reunião", tipo:"select", op:["","Fechamento de bimestre/trimestre","Início do ano letivo","Encaminhamento de um problema da turma","Reunião de rotina"], meia:true},
    {id:"pontos",rot:"Pontos específicos a tratar", tipo:"textarea", ph:"Resultado geral da turma, projeto em andamento, combinados de convivência, datas importantes.", dica:"opcional"}
  ],
  prompt:v=>
`Aja como um coordenador pedagógico especialista em conduzir reuniões de pais produtivas.

CONTEXTO${L("Papel na turma",v.comp)}${L("Ano/série",v.ano)}${L("Duração",v.dur)}${L("Foco principal",v.foco)}${P("PONTOS ESPECÍFICOS A TRATAR",v.pontos)}

TAREFA
Monte um roteiro cronometrado completo para essa reunião de pais.

FORMATO DA RESPOSTA
1. Abertura: o que dizer nos primeiros minutos, com tempo estimado.
2. Apresentação de dados da turma (desempenho geral, frequência, clima), com tempo estimado.
3. Como comunicar pontos de atenção sem citar casos individuais na parte coletiva.
4. Orientação para o momento de atendimento individual, se houver.
5. Como conduzir perguntas difíceis ou reclamações dos responsáveis, com 3 frases prontas de manejo.
6. Encaminhamentos e combinados finais.
7. Modelo de ata da reunião, pronto para preencher.

REGRAS
${REGRAS_BASE}
- Não cite nenhum aluno pelo nome na parte coletiva da reunião — assuntos individuais ficam só para o atendimento individual.
- Separe claramente o que é comunicado geral do que é conversa individual.`
},
{
  id:"tutor", grupo:"Comunicar", origem:"novo", nome:"Tutor de estudos para o aluno",
  resumo:"Prompt na voz do aluno, para ele colar na IA e estudar sozinho, sem receber a resposta pronta.",
  ias:["chatgpt","claude","gemini","deepseek"],
  campos:[
    {id:"materia",rot:"Matéria ou tema", ph:"Equações do 1º grau"},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"dific",  rot:"Onde costuma travar", ph:"Isolar a incógnita quando tem número negativo", meia:true},
    {id:"nivel",  rot:"Nível de exigência", tipo:"select", op:["","Bem básico, do zero","Nível da turma","Quero ser desafiado"], meia:true},
    {id:"tempo",  rot:"Tempo disponível para estudar hoje", ph:"30 minutos", meia:true},
    {id:"obs",    rot:"Alguma outra informação para o tutor", tipo:"textarea", ph:"Ex.: prova é semana que vem; já tentei sozinho e não consegui.", dica:"opcional"}
  ],
  prompt:v=>
`Você é meu tutor de estudos.

MEU CONTEXTO${L("Matéria/tema",v.materia)}${L("Ano/série",v.ano)}${L("Onde costumo travar",v.dific)}${L("Nível de exigência",v.nivel)}${L("Tempo disponível hoje",v.tempo)}${P("OUTRAS INFORMAÇÕES",v.obs)}

COMO VOCÊ DEVE ME ENSINAR
1. Comece perguntando o que eu já sei sobre o assunto, em vez de explicar tudo de uma vez.
2. Nunca me dê a resposta pronta de um exercício: me dê uma pista, espere eu tentar, e só então me diga se acertei ou onde errei.
3. Faça uma pergunta de cada vez — nunca uma lista de perguntas juntas.
4. Quando eu errar, não corrija direto: pergunte como eu cheguei naquela resposta, para descobrirmos juntos onde está o erro.
5. Vá aumentando a dificuldade aos poucos, só depois que eu mostrar que entendi o passo anterior.
6. De tempos em tempos, resuma comigo o que já aprendemos até aqui.
7. Ao final do tempo que eu tenho disponível, feche com um resumo do que avançamos e o que ainda preciso praticar.

REGRAS
- Nunca entregue a resposta final de um exercício antes de eu tentar pelo menos uma vez.
- Use linguagem simples, do jeito que se explica para alguém da minha idade/série.
- Se eu pedir a resposta pronta direto, não entregue — me ajude a chegar nela.
- Seja paciente e encorajador, mesmo se eu errar várias vezes.`
},
{
  id:"justificativa", grupo:"Comunicar", origem:"novo", nome:"Justificativa pedagógica",
  resumo:"Texto formal para a coordenação, com fundamentação em documentos oficiais.",
  ias:["claude","chatgpt","gemini"],
  campos:[
    {id:"objeto",rot:"O que precisa ser justificado", tipo:"select", op:["","Escolha metodológica","Pedido de material ou recurso","Saída de campo / passeio pedagógico","Adaptação de atividade ou avaliação","Outro"]},
    {id:"comp",  rot:"Componente curricular", tipo:"lista", ph:"Artes", meia:true},
    {id:"ano",   rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"destino",rot:"Destinado a", tipo:"select", op:["","Coordenação pedagógica","Direção","Secretaria de educação","Conselho de classe"], meia:true},
    {id:"prazo", rot:"Quando isso vai acontecer", ph:"Na semana do dia 15", meia:true},
    {id:"detalhe",rot:"Detalhe da proposta", tipo:"textarea", ph:"O que exatamente você quer fazer, por que e o que precisa em troca (material, autorização, orçamento, tempo de aula)."}
  ],
  prompt:v=>
`Aja como um coordenador pedagógico especialista em elaborar justificativas formais para a gestão escolar.

CONTEXTO${L("O que precisa ser justificado",v.objeto)}${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Destinado a",v.destino)}${L("Quando vai acontecer",v.prazo)}${P("DETALHE DA PROPOSTA",v.detalhe)}

TAREFA
Escreva um texto formal e objetivo justificando essa decisão para a gestão da escola.

FORMATO DA RESPOSTA
1. Assunto/título do documento.
2. Parágrafo de contextualização: o que está sendo proposto e por quê.
3. Fundamentação pedagógica, com objetivos de aprendizagem esperados.
4. Base em documentos oficiais (BNCC, LDB, DCN ou o currículo da rede), citando o trecho ou a habilidade pertinente.
5. Recursos, tempo ou autorizações necessários.
6. Riscos previstos e como serão administrados, se for o caso (ex.: saída de campo).
7. Fechamento com pedido claro de aprovação.

REGRAS
${REGRAS_BASE}
- Cite apenas documentos que realmente existem (BNCC, LDB, DCN, currículo da rede) e marque com “[conferir referência exata]” qualquer citação específica que precise ser checada antes de enviar.
- Mantenha tom formal, mas sem exagero de burocratês.
- Não prometa resultados que não podem ser garantidos.`
},

/* ===================== TECNOLOGIA ===================== */
{
  id:"app", grupo:"Tecnologia", origem:"novo", nome:"Criar um app educacional",
  resumo:"Código completo de um app ou ferramenta simples, em um único arquivo HTML.",
  ias:["claude","v0","bolt","lovable","replit","aistudio"],
  campos:[
    {id:"func",   rot:"O que o app deve fazer", tipo:"textarea", grande:true, ph:"Um sorteador de grupos de trabalho que evita repetir a mesma dupla de aulas anteriores."},
    {id:"quem",   rot:"Quem vai usar", tipo:"select", op:["","Professor(a)","Alunos","Famílias","Turma toda, junto, na lousa"], meia:true},
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"Qualquer disciplina", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"onde",   rot:"Onde vai rodar", tipo:"select", op:["","Página HTML em arquivo único","Site com várias páginas","App instalável no celular (PWA)","Planilha ou formulário"], meia:true},
    {id:"salvar", rot:"Precisa salvar dados?", tipo:"select", op:["","Não, só usa e fecha","Sim, no próprio navegador do usuário","Sim, compartilhado entre usuários"], meia:true},
    {id:"visual", rot:"Visual desejado", tipo:"select", op:["","Simples e neutro","Colorido e lúdico (infantil)","Sério e profissional","Divertido tipo jogo"], meia:true},
    {id:"funcs",  rot:"Funcionalidades principais", tipo:"textarea", ph:"Ex.: colar lista de nomes, escolher tamanho dos grupos, botão sortear, botão para excluir combinações já usadas."}
  ],
  prompt:v=>
`Aja como um desenvolvedor front-end sênior especialista em criar ferramentas web simples para uso escolar.

CONTEXTO${L("Quem vai usar",v.quem)}${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Onde vai rodar",v.onde)}${L("Precisa salvar dados?",v.salvar)}${L("Visual desejado",v.visual)}${P("O QUE O APP DEVE FAZER",v.func)}${P("FUNCIONALIDADES PRINCIPAIS",v.funcs)}

TAREFA
Projete e implemente esse app do zero, entregando o código completo e funcional.

FORMATO DA RESPOSTA
1. Análise rápida do pedido: o que realmente precisa existir para resolver o problema.
2. Escopo mínimo viável: o que entra nesta primeira versão e o que fica de fora.
3. Lista de telas ou estados da interface.
4. Código completo em um único arquivo HTML, com CSS e JavaScript embutidos no mesmo arquivo, sem nenhuma dependência externa, funcionando totalmente offline.
5. Explicação de como garantir acessibilidade (contraste, tamanho de fonte, navegação por teclado) e responsividade (celular e computador).
6. Passo a passo de como testar o app localmente.
7. O que fazer depois, se eu quiser publicar o app na internet.

REGRAS
${REGRAS_BASE}
- Nada de biblioteca externa via CDN, fonte externa ou qualquer recurso que dependa de internet: o arquivo tem que abrir e funcionar sozinho.
- Se precisar guardar dados, use apenas localStorage, sempre dentro de try/catch, prevendo que ele pode falhar ou estar vazio.
- O app não pode pedir nenhum dado pessoal de aluno (nome completo, foto, contato) — se precisar identificar alguém, use apenas iniciais ou apelido.`
},
{
  id:"site-turma", grupo:"Tecnologia", origem:"novo", nome:"Site ou blog da turma",
  resumo:"Site simples da turma ou disciplina, em um único arquivo, pronto para publicar.",
  ias:["claude","v0","bolt","lovable"],
  campos:[
    {id:"proposito",rot:"Propósito do site", tipo:"select", op:["","Mural de avisos da turma","Portfólio dos trabalhos da turma","Blog da disciplina","Site de um projeto específico"]},
    {id:"comp",   rot:"Componente curricular", tipo:"lista", ph:"Língua Portuguesa", meia:true},
    {id:"ano",    rot:"Ano / série", tipo:"select", op:ANOS, meia:true},
    {id:"paginas",rot:"Páginas ou seções desejadas", ph:"Início, Sobre a turma, Trabalhos, Contato", meia:true},
    {id:"visual", rot:"Visual desejado", tipo:"select", op:["","Simples e neutro","Colorido e lúdico (infantil)","Sério e profissional","Divertido tipo jogo"], meia:true},
    {id:"conteudo",rot:"Conteúdo de cada seção", tipo:"textarea", grande:true, ph:"Descreva o que deve entrar em cada página: textos, listas de trabalhos, imagens (com legenda do que seria), links."}
  ],
  prompt:v=>
`Aja como um desenvolvedor front-end sênior especialista em criar sites simples para uso escolar.

CONTEXTO${L("Propósito do site",v.proposito)}${L("Componente curricular",v.comp)}${L("Ano/série",v.ano)}${L("Páginas ou seções desejadas",v.paginas)}${L("Visual desejado",v.visual)}${P("CONTEÚDO DE CADA SEÇÃO",v.conteudo)}

TAREFA
Projete e implemente esse site do zero, entregando o código completo e funcional.

FORMATO DA RESPOSTA
1. Estrutura do site: lista das páginas ou seções e o que cada uma contém.
2. Código completo em um único arquivo HTML, com CSS e JavaScript embutidos no mesmo arquivo, sem nenhuma dependência externa, funcionando totalmente offline.
3. Onde entram imagens (com um espaço reservado e a legenda do que deveria aparecer ali).
4. Como o texto e o visual ficam responsivos em celular e computador.
5. Passo a passo de como abrir e conferir o site antes de publicar.
6. Como manter o site atualizado depois (o que editar no arquivo para trocar um texto ou adicionar um novo trabalho).
7. Sugestão simples de onde publicar gratuitamente.

REGRAS
${REGRAS_BASE}
- Nada de biblioteca externa via CDN ou fonte externa: o arquivo tem que abrir e funcionar sozinho.
- Nunca publique foto ou nome completo de nenhum aluno sem autorização — use apenas iniciais, apelidos combinados com a turma, ou espaços reservados com a legenda “[foto mediante autorização]”.`
},
];

/* ============================================================
   GUIAS — páginas de conteúdo, sem formulário
   ============================================================ */
function guiaBNCCHtml(){
  const comp = ["ei","ef","em"].map(k=>{
    const c = BNCC_COMPETENCIAS[k];
    return `<h3>${esc(c.rotulo)}</h3><ol>` + c.itens.map(x=>`<li>${esc(x)}</li>`).join("") + `</ol>`;
  }).join("");

  let hab = "", etapaAtual = null, eixoAtual = null;
  BNCC_HAB.forEach(h=>{
    if(h.e !== etapaAtual){ hab += `<h3 class="gb-etapa">${esc(h.e)}</h3>`; etapaAtual = h.e; eixoAtual = null; }
    const eixo = h.x || "Competências específicas do Ensino Médio";
    if(eixo !== eixoAtual){ hab += `<p class="gb-eixo-tit"><strong>${esc(eixo)}</strong></p>`; eixoAtual = eixo; }
    hab += `<div class="gb-item" data-busca="${esc((h.c+" "+h.t+" "+h.e+" "+eixo).toLowerCase())}">
      <span class="gb-cod">${h.c}</span><p>${esc(h.t)}</p></div>`;
  });

  return `
  <div class="aviso">Texto transcrito do <strong>Complemento à BNCC — Computação</strong> (Resolução CNE/CEB nº 1, de 2022),
  a partir do documento enviado pelo professor. São ${BNCC_HAB.length} habilidades, organizadas nos eixos
  <strong>Pensamento Computacional</strong>, <strong>Mundo Digital</strong> e <strong>Cultura Digital</strong> —
  no Ensino Médio, a organização é por competência específica.</div>

  <p>Todo gerador deste app tem um bloco <strong>BNCC de Computação</strong> no formulário. Escolha ali as habilidades
  e elas entram no prompt com o código e o texto na íntegra, junto com a exigência de que a IA marque, em cada parte
  da produção, qual habilidade está sendo mobilizada.</p>

  <p><input id="guia-filtro" type="search" placeholder="Filtrar por código, palavra ou etapa…"
     style="width:100%;background:var(--paper);border:1px solid var(--line-strong);border-radius:6px;padding:9px 11px;font-size:14px"></p>

  <h2>Competências e premissas por etapa</h2>
  ${comp}

  <h2>Habilidades</h2>
  <div id="guia-habs">${hab}</div>`;
}

const GUIAS = [
{
  id:"guia-bncc", grupo:"Guias", nome:"BNCC de Computação",
  resumo:"As 141 habilidades e as competências de cada etapa, na íntegra.",
  html: guiaBNCCHtml
},
{
  id:"guia-ias", grupo:"Guias", nome:"IAs testadas e recomendadas",
  resumo:"Qual assistente usar para cada tipo de tarefa, e o que dá para fazer de graça.",
  html:`
  <div class="aviso">Planos gratuitos, limites diários e nomes de produto mudam o tempo todo.
  Trate esta página como um ponto de partida e confira as condições no site de cada ferramenta antes de contar com ela.</div>

  <h2>Assistentes de conversa</h2>
  <p>São os que você vai usar na maior parte dos geradores deste app. Todos têm versão gratuita e todos aceitam
  o prompt colado direto na caixa de mensagem.</p>
  <div class="tab-wrap"><table>
    <thead><tr><th>Ferramenta</th><th>Vai bem em</th><th>Observação</th></tr></thead>
    <tbody>
      <tr><td><a href="https://chatgpt.com/" target="_blank" rel="noopener">ChatGPT</a></td>
        <td>Uso geral, atividades, provas, imagens</td><td>Gera imagem e lê arquivos na versão gratuita, com limite.</td></tr>
      <tr><td><a href="https://claude.ai/new" target="_blank" rel="noopener">Claude</a></td>
        <td>Textos longos, correção, análise de PDF, código</td><td>Costuma escrever melhor em português corrido e seguir formato pedido.</td></tr>
      <tr><td><a href="https://gemini.google.com/app" target="_blank" rel="noopener">Gemini</a></td>
        <td>Vídeos do YouTube, imagens, integração com Google</td><td>Único que analisa vídeo direto pelo link com facilidade.</td></tr>
      <tr><td><a href="https://copilot.microsoft.com/" target="_blank" rel="noopener">Microsoft Copilot</a></td>
        <td>Word, Excel e PowerPoint</td><td>Útil se a escola já usa o pacote da Microsoft.</td></tr>
      <tr><td><a href="https://chat.deepseek.com/" target="_blank" rel="noopener">DeepSeek</a></td>
        <td>Matemática e raciocínio passo a passo</td><td>Bom para conferir contas e resolver questões.</td></tr>
      <tr><td><a href="https://www.perplexity.ai/" target="_blank" rel="noopener">Perplexity</a></td>
        <td>Pesquisa com fonte</td><td>Responde citando links — melhor escolha quando você precisa de referência.</td></tr>
    </tbody>
  </table></div>

  <h2>Para materiais específicos</h2>
  <div class="tab-wrap"><table>
    <thead><tr><th>Tarefa</th><th>Onde fazer</th></tr></thead>
    <tbody>
      <tr><td>Slides prontos</td><td><a href="https://gamma.app/" target="_blank" rel="noopener">Gamma</a>, <a href="https://www.canva.com/" target="_blank" rel="noopener">Canva</a></td></tr>
      <tr><td>Imagens e ilustrações</td><td>ChatGPT, Gemini, <a href="https://ideogram.ai/" target="_blank" rel="noopener">Ideogram</a>, <a href="https://leonardo.ai/" target="_blank" rel="noopener">Leonardo</a>, <a href="https://www.bing.com/images/create" target="_blank" rel="noopener">Bing Imagens</a></td></tr>
      <tr><td>Estudar um PDF ou montar podcast</td><td><a href="https://notebooklm.google.com/" target="_blank" rel="noopener">NotebookLM</a></td></tr>
      <tr><td>Diagramas e esquemas</td><td><a href="https://www.napkin.ai/" target="_blank" rel="noopener">Napkin</a>, Claude (código Mermaid)</td></tr>
      <tr><td>Criar um app ou site</td><td>Claude, <a href="https://v0.app/" target="_blank" rel="noopener">v0</a>, <a href="https://bolt.new/" target="_blank" rel="noopener">Bolt</a>, <a href="https://lovable.dev/" target="_blank" rel="noopener">Lovable</a>, <a href="https://replit.com/" target="_blank" rel="noopener">Replit</a>, <a href="https://aistudio.google.com/" target="_blank" rel="noopener">Google AI Studio</a></td></tr>
    </tbody>
  </table></div>

  <h2>Três hábitos que mudam o resultado</h2>
  <ol>
    <li><strong>Confira tudo que for fato.</strong> Data, código da BNCC, referência bibliográfica, link, classificação
    de filme, resultado de conta: a IA erra com toda a confiança do mundo. Os prompts deste app já pedem que ela
    sinalize o que precisa de conferência, mas a checagem é sua.</li>
    <li><strong>Não coloque dado pessoal de aluno.</strong> Nome completo, laudo, endereço, foto, nota nominal.
    Use iniciais. Isso vale para qualquer ferramenta, paga ou gratuita.</li>
    <li><strong>Peça ajuste em vez de recomeçar.</strong> Recebeu algo perto do que queria? Responda na mesma conversa:
    “reduza para 45 minutos”, “troque o contexto para a zona rural”, “deixe a linguagem mais simples”.</li>
  </ol>`
},
{
  id:"guia-celular", grupo:"Guias", nome:"Instalar no celular",
  resumo:"Deixe o Caderno de Prompts como um ícone na tela do seu celular.",
  html:`
  <p>Este app é uma página só. Dá para deixar um atalho dele na tela inicial do celular e abrir como se fosse
  um aplicativo, sem passar pela loja e sem ocupar espaço.</p>

  <h2>Android (Chrome)</h2>
  <ol class="passos">
    <li>Abra o endereço do app no Chrome.</li>
    <li>Toque nos três pontinhos, no canto superior direito.</li>
    <li>Escolha <strong>Adicionar à tela inicial</strong> (ou “Instalar aplicativo”, se aparecer).</li>
    <li>Confirme o nome e toque em <strong>Adicionar</strong>. O ícone aparece junto com os outros apps.</li>
  </ol>

  <h2>iPhone e iPad (Safari)</h2>
  <ol class="passos">
    <li>Abra o endereço do app no Safari — precisa ser o Safari, não funciona no Chrome do iPhone.</li>
    <li>Toque no botão de compartilhar (o quadrado com a seta para cima).</li>
    <li>Role a lista e escolha <strong>Adicionar à Tela de Início</strong>.</li>
    <li>Toque em <strong>Adicionar</strong>.</li>
  </ol>

  <h2>Computador</h2>
  <p>No Chrome ou no Edge, um ícone de instalação costuma aparecer na barra de endereço. Se não aparecer,
  use o menu do navegador e procure por <strong>Instalar</strong> ou <strong>Criar atalho</strong>.</p>

  <h2>Funciona sem internet?</h2>
  <p>O app em si é um arquivo só e roda offline depois de carregado — se você baixar o arquivo
  <code>.html</code> e abrir direto do celular, ele funciona sem rede. O que precisa de internet é a IA:
  a hora de colar o prompt no ChatGPT, no Claude ou no Gemini.</p>
  <div class="aviso">Sem conexão, as fontes bonitas não carregam e o app aparece com a fonte padrão do sistema.
  Nada mais muda.</div>`
},
{
  id:"guia-publicar", grupo:"Guias", nome:"Publicar seu app na internet",
  resumo:"Passo a passo para colocar no ar, de graça, na Netlify ou na Vercel.",
  html:`
  <p>Você gerou um app com a IA e recebeu um arquivo <code>.html</code>. Agora falta colocá-lo em um endereço
  que qualquer pessoa consiga abrir. As duas opções mais usadas são a <strong>Netlify</strong> e a
  <strong>Vercel</strong>, as duas com plano gratuito que dá e sobra para um projeto de escola.</p>

  <div class="aviso"><strong>Antes de tudo:</strong> renomeie o arquivo principal para <code>index.html</code>.
  É o nome que os servidores procuram quando alguém abre o endereço. Se o app tiver mais de um arquivo,
  coloque todos dentro de uma pasta e mantenha o <code>index.html</code> na raiz dessa pasta.</div>

  <h2>Caminho mais fácil: Netlify Drop</h2>
  <p>Não precisa instalar nada nem saber Git. É literalmente arrastar a pasta.</p>
  <ol class="passos">
    <li>Coloque o <code>index.html</code> dentro de uma pasta (por exemplo, <code>meu-app</code>).</li>
    <li>Acesse <a href="https://app.netlify.com/drop" target="_blank" rel="noopener">app.netlify.com/drop</a>.</li>
    <li>Arraste a pasta inteira para a área indicada na página.</li>
    <li>Em alguns segundos o site sobe e você recebe um endereço parecido com
    <code>nome-aleatorio.netlify.app</code>. Já está no ar.</li>
    <li>Crie uma conta gratuita quando ela pedir — é o que garante que o site continue existindo e que você
    possa alterá-lo depois.</li>
    <li>Em <strong>Site configuration → Change site name</strong>, troque o nome aleatório por algo como
    <code>quimica-prof-augusto</code>.</li>
  </ol>
  <p>Para atualizar depois: entre no painel do site, vá em <strong>Deploys</strong> e arraste a pasta nova.
  A versão anterior fica guardada no histórico, então dá para voltar atrás.</p>

  <h2>Vercel</h2>
  <p>A Vercel não tem o arrastar-e-soltar do navegador. São dois caminhos:</p>

  <h3>Pelo GitHub (recomendado se você pretende mexer no app com frequência)</h3>
  <ol class="passos">
    <li>Crie uma conta no <a href="https://github.com/" target="_blank" rel="noopener">GitHub</a>.</li>
    <li>Crie um repositório novo, público, e envie o <code>index.html</code> pelo botão
    <strong>Add file → Upload files</strong>.</li>
    <li>Entre na <a href="https://vercel.com/" target="_blank" rel="noopener">Vercel</a> e faça login com a conta do GitHub.</li>
    <li>Clique em <strong>Add New… → Project</strong> e escolha o repositório que você acabou de criar.</li>
    <li>Deixe as configurações como estão (é um site estático, não precisa de comando de build) e clique em
    <strong>Deploy</strong>.</li>
    <li>Pronto: o endereço fica parecido com <code>seu-projeto.vercel.app</code>. A partir daí, toda vez que você
    alterar o arquivo no GitHub, a Vercel republica sozinha.</li>
  </ol>

  <h3>Pelo terminal</h3>
  <p>Se você tem o Node.js instalado, entre na pasta do projeto e rode:</p>
  <p><code>npx vercel</code></p>
  <p>Responda às perguntas e o site sobe. Para a versão definitiva, rode <code>npx vercel --prod</code>.</p>

  <h2>Qual escolher</h2>
  <div class="tab-wrap"><table>
    <thead><tr><th></th><th>Netlify</th><th>Vercel</th></tr></thead>
    <tbody>
      <tr><td>Subir sem instalar nada</td><td>Sim, arrastando a pasta</td><td>Não, precisa de GitHub ou terminal</td></tr>
      <tr><td>Atualizar o site</td><td>Arrastar a pasta de novo</td><td>Automático, ao salvar no GitHub</td></tr>
      <tr><td>Endereço grátis</td><td><code>.netlify.app</code></td><td><code>.vercel.app</code></td></tr>
      <tr><td>HTTPS (cadeado)</td><td>Já vem</td><td>Já vem</td></tr>
      <tr><td>Melhor para</td><td>Publicar rápido, uma vez</td><td>Projeto que você vai mexer sempre</td></tr>
    </tbody>
  </table></div>

  <h2>Outras opções gratuitas</h2>
  <ul>
    <li><strong><a href="https://pages.github.com/" target="_blank" rel="noopener">GitHub Pages</a></strong> —
    se o arquivo já está no GitHub, é só ativar em <em>Settings → Pages</em>.</li>
    <li><strong><a href="https://pages.cloudflare.com/" target="_blank" rel="noopener">Cloudflare Pages</a></strong> —
    parecido com a Vercel, muito rápido.</li>
    <li><strong><a href="https://nekoweb.org/" target="_blank" rel="noopener">Nekoweb</a></strong> —
    hospedagem simples, com editor de arquivos no próprio navegador. É onde está o site que inspirou este app.</li>
  </ul>

  <h2>Antes de divulgar o endereço</h2>
  <ul>
    <li>Abra o site no celular e no computador e teste tudo.</li>
    <li>Um site publicado é público: qualquer pessoa com o endereço entra. Não coloque nome completo,
    foto ou nota de aluno sem autorização por escrito da família.</li>
    <li>Se o app guarda informação, entenda onde: o que fica no navegador do usuário não é visto por mais ninguém —
    mas também some se ele limpar os dados do navegador.</li>
    <li>Coloque no rodapé quem fez e a data. Daqui a um ano você vai agradecer.</li>
  </ul>`
}
];

/* ============================================================
   Aplicação
   ============================================================ */
const view  = document.getElementById("view");
const nav   = document.getElementById("nav");
const side  = document.getElementById("side");
const scrim = document.getElementById("scrim");
const hamb  = document.getElementById("hamb");
const busca = document.getElementById("busca");
let atual = null;
const valores = {};
const gerado = {};
const bnccSel = {};
const bnccEtapa = {};

const esc = s => String(s==null?"":s)
  .replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;");

const TUDO = GERADORES.concat(GUIAS.map(g=>({...g, origem:"guia"})));
const GRUPOS = [];
TUDO.forEach(g=>{ if(!GRUPOS.includes(g.grupo)) GRUPOS.push(g.grupo); });

const N_MODELO = GERADORES.filter(g=>g.origem==="modelo").length;
const N_NOVO   = GERADORES.length - N_MODELO;

/* ---------- barra lateral ---------- */
function montarNav(filtro){
  const q = (filtro||"").trim().toLowerCase();
  const casa = g => !q || (g.nome+" "+g.resumo+" "+g.grupo).toLowerCase().includes(q);
  nav.innerHTML = "";

  if(!q){
    const inicio = document.createElement("div");
    inicio.className = "nav-group";
    inicio.innerHTML = '<button class="nav-item" data-id="home">Início</button>';
    nav.appendChild(inicio);
  }

  let achou = 0;
  GRUPOS.forEach(gr=>{
    const itens = TUDO.filter(g=>g.grupo===gr && casa(g));
    if(!itens.length) return;
    achou += itens.length;
    const bloco = document.createElement("div");
    bloco.className = "nav-group";
    const lbl = document.createElement("div");
    lbl.className = "nav-label";
    lbl.innerHTML = (ICONES[gr]||"") + "<span>"+gr+"</span><span class='n'>"+itens.length+"</span>";
    bloco.appendChild(lbl);
    itens.forEach(g=>{
      const b = document.createElement("button");
      b.className = "nav-item";
      b.dataset.id = g.id;
      b.innerHTML = "<span class='dot "+(g.origem==="novo"?"novo":(g.origem==="guia"?"guia":""))+"'></span><span>"+esc(g.nome)+"</span>";
      bloco.appendChild(b);
    });
    nav.appendChild(bloco);
  });

  if(!achou){
    const vazio = document.createElement("div");
    vazio.className = "vazio";
    vazio.textContent = "Nenhum gerador com esse nome.";
    nav.appendChild(vazio);
  }
  marcarNav(atual ? atual.id : "home");
}

function marcarNav(id){
  nav.querySelectorAll(".nav-item").forEach(b=>{
    b.setAttribute("aria-current", b.dataset.id===id ? "true" : "false");
  });
}

nav.addEventListener("click", e=>{
  const b = e.target.closest(".nav-item");
  if(!b) return;
  abrir(b.dataset.id);
  fecharMenu();
});
busca.addEventListener("input", ()=>montarNav(busca.value));

const RODAPE = `
  <div class="foot">
    © 2026 · Caderno de Prompts. Adaptação de “Geradores de Prompts de IA para Professores”,
    de Sérgio Araújo (© 2025), publicado em
    <a href="https://educ.nekoweb.org/geradores/home.html" target="_blank" rel="noopener">educ.nekoweb.org</a>
    sob licença
    <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt-br" target="_blank" rel="noopener">CC BY-NC-SA 4.0</a>.
    Esta versão é distribuída sob a mesma licença.
  </div>`;

/* ---------- tela inicial ---------- */
function telaInicial(){
  atual = null;
  marcarNav("home");

  const catalogo = GRUPOS.map(gr=>{
    const itens = TUDO.filter(g=>g.grupo===gr);
    return `<div class="cat-grupo">
      <h2>${esc(gr)}</h2>
      <div class="tiles">${itens.map(g=>`
        <button class="tile" data-go="${g.id}">
          <span class="t"><span class="dot ${g.origem==="novo"?"novo":(g.origem==="guia"?"guia":"")}"></span><b>${esc(g.nome)}</b></span>
          <span>${esc(g.resumo)}</span>
        </button>`).join("")}</div>
    </div>`;
  }).join("");

  view.innerHTML = `
    <div class="page-head">
      <div class="eyebrow"><span class="grp">${GERADORES.length} geradores de prompts</span></div>
      <h1>Você conhece a sua turma. A IA só precisa saber disso.</h1>
    </div>
    <div class="home">
      <div>
        <p class="lede">Um prompt genérico devolve um plano de aula genérico. Aqui você preenche
        o que só o professor sabe — a série, o tema, os recursos que a escola tem, o jeito da turma —
        e leva um comando pronto, com um clique para abrir direto na IA mais indicada para aquela tarefa.</p>

        <ol class="steps">
          <li><span><b>Escolha um gerador</b>${GERADORES.length} ferramentas, organizadas por aquilo que você precisa fazer.</span></li>
          <li><span><b>Preencha e clique em Gerar Prompt</b>Escolha também as habilidades da BNCC de Computação que a produção deve contemplar.</span></li>
          <li><span><b>Clique na IA recomendada</b>O prompt é copiado e a ferramenta abre numa nova aba. É só colar com Ctrl+V.</span></li>
        </ol>

        <div class="legenda">
          <span><i></i>${N_MODELO} vêm do modelo original</span>
          <span><i class="novo"></i>${N_NOVO} foram acrescentados nesta versão</span>
        </div>

        <div class="catalogo">${catalogo}</div>
      </div>

      <div class="card">
        <div class="card-head"><span class="card-title">Sobre esta versão</span></div>
        <div class="card-body aside-note">
          <p>Este app é uma adaptação do modelo <strong>“Geradores de Prompts de IA para Professores”</strong>,
          criado por <strong>Sérgio Araújo</strong> e publicado em
          <a href="https://educ.nekoweb.org/geradores/home.html" target="_blank" rel="noopener">educ.nekoweb.org</a>.</p>
          <p>Os ${N_MODELO} geradores marcados com o ponto cheio correspondem às ferramentas que existem no site dele.
          Os outros ${N_NOVO} foram acrescentados aqui, junto com os botões de IA e os guias. O código foi escrito
          do zero, mas a ideia e a organização vêm do trabalho dele — o crédito é dele.</p>
          <p><strong>BNCC de Computação:</strong> todo gerador traz um bloco para escolher as habilidades do
          Complemento à BNCC — Computação (CNE/CEB, 2022). O prompt sai com o código e o texto oficial de cada uma,
          e exige que a IA marque onde cada habilidade é mobilizada. O guia lista as ${BNCC_HAB.length} habilidades.</p>
          <p>A obra original está licenciada em CC BY-NC-SA 4.0 e esta adaptação mantém a mesma licença:
          uso não comercial, com atribuição e compartilhamento pela mesma licença.</p>
          <span class="lic">CC BY-NC-SA 4.0</span>
        </div>
      </div>
    </div>
    ${RODAPE}`;

  view.querySelectorAll("[data-go]").forEach(b=>{
    b.addEventListener("click", ()=>abrir(b.dataset.go));
  });
  window.scrollTo(0,0);
}

/* ---------- página de guia ---------- */
function abrirGuia(g){
  atual = g;
  marcarNav(g.id);
  view.innerHTML = `
    <div class="page-head">
      <div class="eyebrow"><span class="grp">Guia</span></div>
      <h1>${esc(g.nome)}</h1>
      <p>${esc(g.resumo)}</p>
    </div>
    <div class="card"><div class="card-body"><div class="guia">${typeof g.html === "function" ? g.html() : g.html}</div></div></div>
    ${RODAPE}`;
  const filtro = document.getElementById("guia-filtro");
  if(filtro){
    filtro.addEventListener("input", ()=>{
      const q = filtro.value.trim().toLowerCase();
      document.querySelectorAll("#guia-habs .gb-item").forEach(el=>{
        el.style.display = (!q || el.dataset.busca.includes(q)) ? "" : "none";
      });
      document.querySelectorAll("#guia-habs h3, #guia-habs .gb-eixo-tit").forEach(t=>{
        let n = t.nextElementSibling, visivel = false;
        while(n && !/^(H3)$/.test(n.tagName) && !(n.classList && n.classList.contains("gb-eixo-tit"))){
          if(n.classList && n.classList.contains("gb-item") && n.style.display !== "none"){ visivel = true; break; }
          n = n.nextElementSibling;
        }
        t.style.display = visivel ? "" : "none";
      });
    });
  }
  window.scrollTo(0,0);
}

/* ---------- página de um gerador ---------- */
function abrir(id){
  if(id==="home"){ telaInicial(); return; }
  const guia = GUIAS.find(x=>x.id===id);
  if(guia) return abrirGuia(guia);
  const g = GERADORES.find(x=>x.id===id);
  if(!g) return telaInicial();
  atual = g;
  marcarNav(id);
  if(!valores[id]) valores[id] = {};
  const v = valores[id];

  const campoHTML = c=>{
    const val = v[c.id] || "";
    const dica = c.dica ? `<span class="hint">${esc(c.dica)}</span>` : "";
    let ctrl;
    if(c.tipo==="textarea"){
      ctrl = `<textarea id="f-${c.id}" class="${c.grande?"grande":""}" placeholder="${esc(c.ph||"")}">${esc(val)}</textarea>`;
    } else if(c.tipo==="select"){
      ctrl = `<select id="f-${c.id}">` + (c.op||[]).map(o=>
        `<option value="${esc(o)}"${o===val?" selected":""}>${o===""?"— selecione —":esc(o)}</option>`).join("") + `</select>`;
    } else if(c.tipo==="lista"){
      ctrl = `<input type="text" id="f-${c.id}" list="disciplinas" value="${esc(val)}" placeholder="${esc(c.ph||"")}">`;
    } else {
      const t = c.tipo==="number" ? "number" : "text";
      ctrl = `<input type="${t}" id="f-${c.id}" value="${esc(val)}" placeholder="${esc(c.ph||"")}">`;
    }
    return `<div class="field"><label for="f-${c.id}">${esc(c.rot)}</label>${dica}${ctrl}</div>`;
  };

  let corpo = "", fila = [];
  const flush = ()=>{ if(fila.length){ corpo += `<div class="row2">${fila.join("")}</div>`; fila=[]; } };
  g.campos.forEach(c=>{
    if(c.meia && c.tipo!=="textarea"){ fila.push(campoHTML(c)); if(fila.length===2) flush(); }
    else { flush(); corpo += campoHTML(c); }
  });
  flush();

  const selo = g.origem==="modelo"
    ? '<span class="selo modelo">do modelo original</span>'
    : '<span class="selo">novo nesta versão</span>';

  const SETA = '<svg class="ext" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="M8 16L16 8M9 8h7v7"/></svg>';
  const chips = (g.ias||["chatgpt","claude","gemini"]).filter(k=>IAS[k]).map(k=>{
    const ia = IAS[k];
    return `<a class="ia" href="${ia.url}" target="_blank" rel="noopener noreferrer" data-ia="${k}"
      style="--ia:${ia.cor}" title="Copia o prompt e abre o ${esc(ia.nome)} em outra aba">
      <span class="mk">${ia.icone}</span>${esc(ia.nome)}${SETA}</a>`;
  }).join("");

  view.innerHTML = `
    <div class="page-head">
      <div class="eyebrow"><span class="grp">${esc(g.grupo)}</span>${selo}</div>
      <h1>${esc(g.nome)}</h1>
      <p>${esc(g.resumo)}</p>
    </div>

    <div class="cols">
      <section class="card">
        <div class="card-head"><span class="card-title">Preencha</span></div>
        <div class="card-body"><div class="fields">${corpo}</div></div>
        ${bnccUI()}
        <div class="form-foot">
          <button class="btn btn-primary btn-lg" id="gerar">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 3l1.9 4.1L18 9l-4.1 1.9L12 15l-1.9-4.1L6 9l4.1-1.9z"/><path d="M18 15l.9 2.1L21 18l-2.1.9L18 21l-.9-2.1L15 18l2.1-.9z"/></svg>
            Gerar Prompt
          </button>
          <button class="btn" id="limpar">Apagar todos os campos</button>
        </div>
      </section>

      <section class="card out-card">
        <div class="card-head">
          <span class="card-title">Prompt gerado</span>
          <div class="actions">
            <span class="counter" id="cont"></span>
            <button class="btn btn-primary" id="copiar">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="9" y="9" width="12" height="12" rx="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg>
              Copiar Texto
            </button>
          </div>
        </div>
        <div id="area-saida"></div>
        <div class="ias">
          <div class="ias-tit">Gerar com as IAs</div>
          <div class="ias-lista" id="ias">${chips}</div>
          <p class="ias-nota" id="ias-nota">Ao clicar, o prompt é copiado e a ferramenta abre em outra aba — é só colar com Ctrl+V.</p>
        </div>
      </section>
    </div>
    ${RODAPE}`;

  g.campos.forEach(c=>{
    const el = document.getElementById("f-"+c.id);
    if(!el) return;
    el.addEventListener("input", ()=>{ v[c.id]=el.value; if(gerado[id]) render(); sincronizarBNCC(); });
    el.addEventListener("change", ()=>{ v[c.id]=el.value; if(gerado[id]) render(); sincronizarBNCC(); });
  });

  ligarBNCC(g);

  document.getElementById("gerar").addEventListener("click", ()=>{
    gerado[id] = true;
    render();
    const cx = document.querySelector(".out-card");
    if(window.innerWidth < 1080 && cx) cx.scrollIntoView({behavior:"smooth", block:"start"});
  });
  document.getElementById("limpar").addEventListener("click", ()=>{
    valores[id] = {}; gerado[id] = false; bnccSel[id] = []; bnccEtapa[id] = ""; abrir(id);
  });
  document.getElementById("copiar").addEventListener("click", copiar);

  // Os botões de IA são links de verdade (<a target="_blank">): quem abre a aba é o
  // navegador. Aqui só geramos e copiamos o prompt, tudo de forma síncrona, para não
  // perder o gesto do clique e cair no bloqueador de pop-up.
  document.getElementById("ias").addEventListener("click", e=>{
    const b = e.target.closest(".ia");
    if(!b) return;
    const ia = IAS[b.dataset.ia];
    if(!gerado[id]){ gerado[id] = true; render(); }
    const ok = copiarSync(textoAtual());
    const nota = document.getElementById("ias-nota");
    nota.textContent = ok
      ? "Prompt copiado. Cole com Ctrl+V (ou Cmd+V) na janela do " + ia.nome + " que acabou de abrir."
      : "Não consegui copiar sozinho — selecione o prompt acima, copie à mão e cole no " + ia.nome + ".";
  });

  render();
  window.scrollTo(0,0);
}

function textoAtual(){
  const el = document.getElementById("saida");
  return el ? el.textContent : "";
}

function render(){
  if(!atual || !atual.prompt) return;
  const area = document.getElementById("area-saida");
  const cont = document.getElementById("cont");
  if(!area) return;

  if(!gerado[atual.id]){
    area.innerHTML = `<div class="vazio-out"><b>Nada gerado ainda</b>
      Preencha o que souber, escolha as habilidades da BNCC de Computação e clique em
      <strong>Gerar Prompt</strong>. Nenhum campo é obrigatório.</div>`;
    cont.textContent = "";
    return;
  }

  let texto;
  try{ texto = atual.prompt(valores[atual.id] || {}).trim(); }
  catch(e){ texto = "Não foi possível montar o prompt: " + e.message; }
  texto = texto + blocoBNCC(atual.id);
  if(!document.getElementById("saida")) area.innerHTML = '<pre class="out" id="saida"></pre>';
  document.getElementById("saida").textContent = texto;
  cont.textContent = texto.length.toLocaleString("pt-BR") + " caracteres";
}

/* Cópia síncrona: precisa acontecer dentro do próprio clique, senão o navegador
   cancela a navegação do link e/ou nega acesso à área de transferência. */
function copiarSync(texto){
  let ok = false;
  try{
    const ta = document.createElement("textarea");
    ta.value = texto;
    ta.setAttribute("readonly","");
    ta.style.position="fixed"; ta.style.top="0"; ta.style.left="0";
    ta.style.width="1px"; ta.style.height="1px"; ta.style.opacity="0";
    document.body.appendChild(ta);
    ta.select();
    ta.setSelectionRange(0, texto.length);
    ok = document.execCommand("copy");
    document.body.removeChild(ta);
  }catch(e){ ok = false; }
  try{
    if(navigator.clipboard && navigator.clipboard.writeText){
      navigator.clipboard.writeText(texto).then(()=>{}, ()=>{});
      ok = true;
    }
  }catch(e){}
  return ok;
}

function copiar(){
  const btn = document.getElementById("copiar");
  if(atual && !gerado[atual.id]){ gerado[atual.id] = true; render(); }
  const ok = copiarSync(textoAtual());
  const antes = btn.innerHTML;
  btn.innerHTML = ok
    ? '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6L9 17l-5-5"/></svg> Texto Copiado!'
    : 'Selecione e copie à mão';
  setTimeout(()=>{ btn.innerHTML = antes; }, 2000);
}

/* ---------- menu no celular ---------- */
function abrirMenu(){ side.classList.add("open"); scrim.classList.add("on"); hamb.setAttribute("aria-expanded","true"); }
function fecharMenu(){ side.classList.remove("open"); scrim.classList.remove("on"); hamb.setAttribute("aria-expanded","false"); }
hamb.addEventListener("click", ()=> side.classList.contains("open") ? fecharMenu() : abrirMenu());
scrim.addEventListener("click", fecharMenu);
document.addEventListener("keydown", e=>{ if(e.key==="Escape") fecharMenu(); });

/* ---------- início ---------- */
montarNav("");
telaInicial();
</script>
</body>
</html>
