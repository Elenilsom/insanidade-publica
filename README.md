# insanidade-publica

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Insanidade Pública</title>
  <meta name="description" content="Página de zueira – O Professor Aloprado Rogério Pontes apresenta: Show de Insanidade." />
  <style>
    :root{
      --bg:#0f1020; --card:#151734; --ink:#e6e8ff; --muted:#a7abff; --accent:#8b5cf6; --accent2:#22d3ee;
    }
    *{box-sizing:border-box}
    html,body{height:100%; margin:0; font-family:system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell, Noto Sans, Helvetica Neue, Arial; background:linear-gradient(135deg,#1e1f3f,#113361); color:var(--ink);}
    a{color:inherit; text-decoration:none}
    .container{max-width:1100px; margin:0 auto; padding:24px}
    .hero{display:grid; grid-template-columns:1.3fr 1fr; gap:24px; align-items:center}
    @media(max-width:900px){.hero{grid-template-columns:1fr}}
    .title{font-size:clamp(2.5rem,5vw,3.5rem); margin:10px 0}
    .subtitle{color:var(--muted)}
    .card{background:rgba(255,255,255,.05); border-radius:20px; padding:20px; box-shadow:0 10px 30px rgba(0,0,0,.3)}
    .btn{cursor:pointer; border:0; border-radius:14px; padding:14px 18px; font-weight:700; transition:.2s; color:#0b0f1a}
    .btn-primary{background:linear-gradient(135deg,var(--accent),var(--accent2)); box-shadow:0 10px 24px rgba(139,92,246,.35)}
    .btn-ghost{background:transparent; color:var(--ink); border:1px solid rgba(255,255,255,.2)}
    .row{display:flex; gap:12px; flex-wrap:wrap}
    .fake-pic{aspect-ratio:1/1; width:100%; border-radius:22px; background:conic-gradient(from 0deg,#8b5cf6,#22d3ee,#14b8a6,#f59e0b,#ef4444,#8b5cf6); display:grid; place-items:center; position:relative; overflow:hidden}
    .fake-pic::after{content:"Professor Aloprado"; position:absolute; inset:auto 10% 10%; background:rgba(0,0,0,.55); padding:6px 10px; border-radius:10px; font-size:clamp(.75rem,1vw + .4rem,1rem);}
    .fake-emoji{font-size:clamp(4rem,10vw,8rem); filter:drop-shadow(0 10px 20px rgba(0,0,0,.4))}
    .ticker{display:flex; overflow:hidden; gap:24px; border-top:1px dashed rgba(255,255,255,.2); border-bottom:1px dashed rgba(255,255,255,.2); padding:10px 0; margin:20px 0}
    .ticker .item{white-space:nowrap; padding-right:40px; color:var(--muted); opacity:.9}
    .grid{display:grid; grid-template-columns:repeat(3,1fr); gap:16px}
    @media(max-width:900px){.grid{grid-template-columns:1fr}}
    .badge{font-weight:700; font-size:.8rem; background:rgba(34,211,238,.15); color:var(--accent2); padding:6px 10px; border-radius:999px; border:1px solid rgba(34,211,238,.35)}
    .note{font-size:.9rem; color:var(--muted)}
    footer{opacity:.75; font-size:.85rem; margin-top:40px}
    dialog{border:0; border-radius:16px; background:var(--card); color:var(--ink); padding:0; width:min(520px,92vw)}
    dialog::backdrop{background:rgba(0,0,0,.6)}
    .modal-head{padding:18px 20px; border-bottom:1px solid rgba(255,255,255,.15); display:flex; justify-content:space-between; align-items:center}
    .modal-body{padding:18px 20px}
    .switch{display:inline-flex; align-items:center; gap:10px; font-size:.95rem; cursor:pointer}
    .switch input{appearance:none; width:50px; height:28px; background:#2a2f55; border:1px solid rgba(255,255,255,.2); position:relative; border-radius:999px; outline:none; transition:.2s}
    .switch input::after{content:""; position:absolute; width:22px; height:22px; border-radius:50%; background:white; top:2px; left:2px; transition:.2s}
    .switch input:checked{background:linear-gradient(135deg,#10b981,#22d3ee)}
    .switch input:checked::after{left:26px}
    .pulse{animation:pulse 1.6s ease-in-out infinite}@keyframes pulse{0%{transform:scale(1)}50%{transform:scale(1.06)}100%{transform:scale(1)}}
    canvas#confetti{position:fixed; inset:0; pointer-events:none}
  </style>
</head>
<body>
  <canvas id="confetti"></canvas>
  <header class="container">
    <div class="hero">
      <div>
        <h1 class="title">Insanidade Pública</h1>
        <p class="subtitle">Apresentando o <strong>Professor Aloprado Rogério Pontes</strong> no <em>Show de Insanidade</em></p>
        <div class="row" style="margin:14px 0 20px">
          <button class="btn btn-primary" id="btnInscrever">Entrar na Bagunça</button>
          <button class="btn btn-ghost" id="btnCompartilhar">Compartilhar</button>
        </div>
        <label class="switch" title="Liga o Modo Sério">
          <input type="checkbox" id="modoSerio">
          <span>Modo Sério</span>
        </label>
        <p class="note" id="notaSeria" style="display:none; margin-top:8px">Tudo sátira! Ria sem medo 😜</p>
      </div>
      <div class="fake-pic">
        <div class="fake-emoji">🤪</div>
      </div>
    </div>
  </header>

  <section class="container">
    <div class="ticker" id="ticker">
      <div class="item">“Eu ri tanto que esqueci o que ia dizer.” – Aluno Anônimo</div>
      <div class="item">“90% risadas, 10% caos.” – Comitê do Absurdo</div>
      <div class="item">“Show de Insanidade: criatividade liberada.” – Rogério Pontes</div>
      <div class="item">“Certificado imaginário incluso!” – Ministério da Zueira</div>
    </div>

    <div class="grid">
      <article class="card">
        <span class="badge">Treinamento</span>
        <h2>Show de Insanidade</h2>
        <p class="subtitle">3 horas de pura diversão sem sentido, mas com propósito.</p>
        <ul>
          <li>🧪 Laboratório de risadas involuntárias</li>
          <li>📣 Técnicas de alopração pedagógica</li>
          <li>📝 Certificado: “Sobrevivi ao Show de Insanidade”</li>
        </ul>
        <div class="row" style="margin-top:8px">
          <button class="btn btn-primary" id="btnQuero">Quero Participar</button>
          <button class="btn btn-ghost" id="btnProgramacao">Ver Programação</button>
        </div>
      </article>

      <article class="card">
        <span class="badge">Programação</span>
        <h3>Roteiro do Caos</h3>
        <ol>
          <li><strong>Boas-vindas:</strong> confetes e gritos virtuais</li>
          <li><strong>Aula 1:</strong> Como errar com estilo</li>
          <li><strong>Aula 2:</strong> Didática do absurdo</li>
          <li><strong>Intervalo:</strong> água imaginária com gás</li>
          <li><strong>Grand Finale:</strong> Defesa pública da tese “Rindo se Aprende?”</li>
        </ol>
      </article>

      <article class="card">
        <span class="badge">FAQ</span>
        <h3>Perguntas Frequentes</h3>
        <details open>
          <summary>Isso é real?</summary>
          <p>Não. É brincadeira e sátira para se divertir com amigos. 😄</p>
        </details>
        <details>
          <summary>Tem certificado de verdade?</summary>
          <p>Sim, no mundo da imaginação! 🖼️</p>
        </details>
        <details>
          <summary>Posso editar?</summary>
          <p>Claro! Basta alterar este arquivo HTML.</p>
        </details>
      </article>
    </div>

    <footer class="container">
      <p>⚠️ Conteúdo humorístico. Qualquer semelhança com a realidade é pura coincidência (ou zueira autorizada).</p>
    </footer>
  </section>

  <dialog id="modal">
    <div class="modal-head">
      <strong>Inscrição – Show de Insanidade</strong>
      <button class="btn btn-ghost" id="fechar">✕</button>
    </div>
    <div class="modal-body">
      <p>Parabéns! Você ganhou 1 ingresso vitalício para rir de si mesmo. 😜</p>
      <p class="note">Brincadeira! Compartilhe com os amigos para a diversão ser completa.</p>
      <div class="row" style="margin-top:12px">
        <button class="btn btn-primary" id="btnConfete">Soltar Confete</button>
        <button class="btn" style="background:linear-gradient(135deg,#10b981,#34d399)" id="btnOk">Fechar</button>
      </div>
    </div>
  </dialog>

  <script>
    const ticker = document.getElementById('ticker');
    let scrollX = 0;
    function loop(){ scrollX+=0.8; ticker.scrollLeft = scrollX; if(scrollX>=ticker.scrollWidth) scrollX=0; requestAnimationFrame(loop); }
    requestAnimationFrame(loop);

    const modal = document.getElementById('modal');
    const abrir = document.getElementById('btnInscrever');
    const fechar = document.getElementById('fechar');
    const ok = document.getElementById('btnOk');
    for(const el of [abrir, document.getElementById('btnQuero')]) el.addEventListener('click',()=>modal.showModal());
    fechar.addEventListener('click',()=>modal.close()); ok.addEventListener('click',()=>modal.close());

    document.getElementById('btnCompartilhar').addEventListener('click', async()=>{const shareData={title:'Insanidade Pública', text:'Veja o Show de Insanidade do Professor Aloprado!', url:location.href}; try{if(navigator.share){await navigator.share(shareData)}else{await navigator.clipboard.writeText(shareData.url); alert('Link copiado!')}}catch(e){}});

    document.getElementById('btnProgramacao').addEventListener('click',()=>{alert('Programação confirmada: caos às 19h, gargalhadas às 20h.');});

    const modoSerio=document.getElementById('modoSerio'); const notaSeria=document.getElementById('notaSeria');
    modoSerio.addEventListener('change',e=>{document.body.style.filter=e.target.checked?'grayscale(1)':'none'; notaSeria.style.display=e.target.checked?'block':'none';});

    const canvas=document.getElementById('confetti'); const ctx2=canvas.getContext('2d'); let W,H;
    function resize(){W=canvas.width=innerWidth; H=canvas.height=innerHeight} resize(); addEventListener('resize',resize);
    const bits=[]; function spawn(n=100){for(let i=0;i<n;i++){bits.push({x:Math.random()*W,y:Math.random()*-H,r:2+Math.random()*4,vy:1+Math.random()*2,vx:-1+Math.random()*2,a:Math.random()*Math.PI*2})}}
    function draw(){ctx2.clearRect(0,0,W,H); for(const b of bits){b.x+=b.vx; b.y+=b.vy; b.a+=0.05; ctx2.save(); ctx2.translate(b.x,b.y); ctx2.rotate(b.a); ctx2.fillStyle=`hsl(${(b.x+b.y)%360} 90% 70%)`; ctx2.fillRect(-b.r,-b.r,b.r*2,b.r*2); ctx2.restore()} requestAnimationFrame(draw)}
    draw(); document.getElementById('btnConfete').addEventListener('click',()=>{spawn(200)});
    abrir.addEventListener('click',()=>spawn(120));
  </script>
</body>
</html>
