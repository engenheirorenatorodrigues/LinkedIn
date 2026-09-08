<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>⚡ Diagnóstico Rápido – Engenharia Solar</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
      background: linear-gradient(145deg, #eef2f7 0%, #d9e2ec 100%);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 30px 20px;
    }
    .container {
      max-width: 8800px;
      width: 100%;
      background: #ffffff;
      border-radius: 40px;
      padding: 40px 45px;
      box-shadow: 0 30px 70px rgba(0, 20, 40, 0.18);
      border: 1px solid rgba(255,255,255,0.5);
    }
    h1 {
      font-size: 1.1rem;
      font-weight: 2000;
      color: #0a1e2f;
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .subhead {
      color: #1d4b6e;
      font-weight: 500;
      margin-bottom: 28px;
      border-left: 6px solid #f39c12;
      padding-left: 20px;
      background: #fef9f0;
      padding: 14px 24px;
      border-radius: 0 16px 16px 0;
      font-size: 1.05rem;
    }
    .question {
      background: #f7faff;
      border-radius: 20px;
      padding: 18px 22px;
      margin-bottom: 14px;
      border: 1px solid #e3ecf5;
      transition: all 0.2s;
    }
    .question:hover {
      border-color: #aac1db;
      background: #f2f8ff;
    }
    .question .pilar {
      display: inline-block;
      background: #1a3652;
      color: white;
      font-size: 0.6rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.6px;
      padding: 2px 14px;
      border-radius: 30px;
      margin-bottom: 6px;
    }
    .question label {
      font-weight: 700;
      font-size: 1rem;
      display: block;
      margin-bottom: 8px;
      color: #0b253b;
    }
    .options {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }
    .options label {
      font-weight: 400;
      background: white;
      padding: 10px 18px;
      border-radius: 40px;
      border: 1px solid #cddcec;
      cursor: pointer;
      font-size: 0.9rem;
      transition: all 0.15s;
      display: flex;
      align-items: center;
      gap: 10px;
      margin: 0;
      width: 100%;
    }
    .options label:hover {
      background: #e3edf8;
      border-color: #7fa3c4;
    }
    .options input[type="radio"] {
      accent-color: #1a6b8f;
      width: 16px;
      height: 16px;
      cursor: pointer;
      flex-shrink: 0;
    }
    .options label:has(input:checked) {
      background: #d2e4f5;
      border-color: #1a6b8f;
      font-weight: 600;
      box-shadow: 0 2px 6px rgba(26, 107, 143, 0.12);
    }

    .btn-primary {
      background: #0b2b44;
      color: white;
      font-weight: 700;
      font-size: 1.1rem;
      border: none;
      padding: 16px 32px;
      border-radius: 60px;
      width: 100%;
      cursor: pointer;
      transition: all 0.25s;
      margin: 18px 0 8px 0;
      letter-spacing: 0.3px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 12px;
    }
    .btn-primary:hover {
      background: #1a4a6e;
      transform: scale(1.01);
      box-shadow: 0 8px 24px rgba(11, 43, 68, 0.25);
    }

    .result-area {
      display: none;
      margin-top: 32px;
      border-top: 2px dashed #c5d8ea;
      padding-top: 30px;
      animation: fadeUp 0.5s ease;
    }
    .result-area.show {
      display: block;
    }

    @keyframes fadeUp {
      0% { opacity: 0; transform: translateY(20px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    .score-header {
      background: linear-gradient(135deg, #0b1e30, #1a3f5c);
      color: white;
      border-radius: 24px;
      padding: 24px 30px;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
    }
    .score-header .big {
      font-size: 2.6rem;
      font-weight: 800;
      letter-spacing: -1px;
    }
    .score-header .label {
      opacity: 0.7;
      font-size: 0.85rem;
    }
    .score-header .status-badge {
      padding: 6px 22px;
      border-radius: 40px;
      font-weight: 700;
      font-size: 1rem;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }
    .status-vermelho { background: #c0392b; color: white; }
    .status-amarelo { background: #f1c40f; color: #1e2a3a; }
    .status-verde { background: #27ae60; color: white; }

    .termometro-wrapper {
      margin: 18px 0 12px 0;
    }
    .termometro-bg {
      width: 100%;
      height: 14px;
      background: #2c4a66;
      border-radius: 30px;
      overflow: hidden;
      box-shadow: inset 0 2px 6px rgba(0,0,0,0.15);
    }
    .termometro-bar {
      height: 100%;
      width: 0%;
      background: linear-gradient(to right, #e74c3c, #f1c40f, #2ecc71);
      border-radius: 30px;
      transition: width 0.9s cubic-bezier(0.22, 1, 0.36, 1);
    }
    .termometro-labels {
      display: flex;
      justify-content: space-between;
      font-size: 0.7rem;
      color: #4d6a86;
      margin-top: 4px;
    }

    .pain-box {
      background: #fff5f0;
      border-left: 8px solid #e67e22;
      padding: 18px 24px;
      border-radius: 16px;
      margin: 20px 0;
    }
    .pain-box strong {
      color: #a04000;
    }

    .solucao-box {
      background: #e3f0fa;
      border-radius: 20px;
      padding: 24px 28px;
      border: 1px solid #b6d0e5;
      margin: 18px 0;
    }
    .solucao-box .titulo-solucao {
      font-size: 1.3rem;
      font-weight: 700;
      color: #0b2b44;
      margin-bottom: 12px;
    }
    .solucao-box ul {
      list-style: none;
      padding-left: 0;
      margin: 12px 0;
    }
    .solucao-box ul li {
      padding: 4px 0 4px 28px;
      background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="%231a6b8f" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>') left center no-repeat;
      background-size: 18px;
      margin-bottom: 2px;
    }

    .solucao-box .experiencia {
      font-weight: 500;
      color: #1a3b52;
      margin: 16px 0 8px 0;
      line-height: 1.6;
      background: #ffffffcc;
      padding: 14px 18px;
      border-radius: 14px;
      border-left: 4px solid #1a6b8f;
      text-align: justify;
    }

    .action-row {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-top: 16px;
    }
    .action-btn {
      flex: 1;
      min-width: 100%;
      padding: 14px 20px;
      border-radius: 60px;
      border: none;
      font-weight: 700;
      font-size: 1rem;
      cursor: pointer;
      transition: all 0.2s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      text-decoration: none;
    }
    .action-btn.whatsapp {
      background: #25D366;
      color: white;
    }
    .action-btn.whatsapp:hover {
      background: #1da85a;
      transform: scale(1.02);
      box-shadow: 0 8px 24px rgba(37, 211, 102, 0.3);
    }

    @media (max-width: 650px) {
      .container { padding: 24px 18px; }
      h1 { font-size: 1.6rem; flex-wrap: wrap; }
      .score-header { flex-direction: column; align-items: flex-start; gap: 12px; }
      .action-btn { min-width: 100%; }
    }
  </style>
</head>
<body>

<div class="container">

  <h1>⚡ Diagnóstico Rápido</h1>
  <div class="subhead">
    Descubra se sua engenharia está travando seu faturamento.
  </div>

  <!-- FORMULÁRIO -->
  <div id="formulario">

    <div class="question">
      <span class="pilar">⏳ Gargalo Operacional</span>
      <label>1. Quem faz a engenharia dos seus projetos hoje?</label>
      <div class="options">
        <label><input type="radio" name="q1" value="0"> Eu mesmo (sócio)</label>
        <label><input type="radio" name="q1" value="1"> Tenho 1 engenheiro interno</label>
        <label><input type="radio" name="q1" value="3"> Terceirizo, mas demora</label>
        <label><input type="radio" name="q1" value="5"> Não tenho estrutura fixa</label>
      </div>
    </div>

    <div class="question">
      <span class="pilar">🔄 Retrabalho</span>
      <label>2. Qual o percentual de projetos devolvidos pela concessionária?</label>
      <div class="options">
        <label><input type="radio" name="q2" value="0"> Menos de 10%</label>
        <label><input type="radio" name="q2" value="2"> De 10% a 30%</label>
        <label><input type="radio" name="q2" value="4"> De 30% a 50%</label>
        <label><input type="radio" name="q2" value="6"> Mais de 50%</label>
      </div>
    </div>

    <div class="question">
      <span class="pilar">📄 Burocracia</span>
      <label>3. Quanto tempo médio gasta com documentação por projeto?</label>
      <div class="options">
        <label><input type="radio" name="q3" value="0"> Até 2h</label>
        <label><input type="radio" name="q3" value="2"> De 2h a 5h</label>
        <label><input type="radio" name="q3" value="4"> De 5h a 10h</label>
        <label><input type="radio" name="q3" value="6"> Mais de 10h</label>
      </div>
    </div>

    <div class="question">
      <span class="pilar">📈 Escalabilidade</span>
      <label>4. Se suas vendas dobrassem, sua engenharia daria conta?</label>
      <div class="options">
        <label><input type="radio" name="q4" value="0"> Sim, tranquilo</label>
        <label><input type="radio" name="q4" value="3"> Talvez, com esforço</label>
        <label><input type="radio" name="q4" value="5"> Não, certamente travaria</label>
        <label><input type="radio" name="q4" value="7"> Já trava hoje</label>
      </div>
    </div>

    <div class="question">
      <span class="pilar">💰 Custo de Oportunidade</span>
      <label>5. Você já deixou de vender ou atrasou cliente por falta de engenharia no último mês?</label>
      <div class="options">
        <label><input type="radio" name="q5" value="0"> Não</label>
        <label><input type="radio" name="q5" value="3"> Aconteceu 1 vez</label>
        <label><input type="radio" name="q5" value="6"> Aconteceu 2+ vezes</label>
      </div>
    </div>

    <div class="question">
      <span class="pilar">⚡ Concessionárias</span>
      <label>6. Você tem dificuldade com alguma distribuidora (CEMIG, ENEL, CPFL, etc.)?</label>
      <div class="options">
        <label><input type="radio" name="q6" value="0"> Nenhuma, tenho domínio em todas</label>
        <label><input type="radio" name="q6" value="2"> Dificuldade com 1</label>
        <label><input type="radio" name="q6" value="4"> Dificuldade com 2+</label>
        <label><input type="radio" name="q6" value="6"> Não conheço algumas regras</label>
      </div>
    </div>

    <div class="question">
      <span class="pilar">📊 Volume</span>
      <label>7. Quantos projetos fotovoltaicos você movimenta por mês?</label>
      <div class="options">
        <label><input type="radio" name="q7" value="0"> Até 2 projetos</label>
        <label><input type="radio" name="q7" value="4"> De 3 a 5 projetos</label>
        <label><input type="radio" name="q7" value="8"> De 6 a 10 projetos</label>
        <label><input type="radio" name="q7" value="12"> Mais de 10 projetos</label>
      </div>
    </div>

    <button class="btn-primary" onclick="calcular()">
      🔎 Ver meu diagnóstico agora
    </button>
  </div>

  <!-- RESULTADO -->
  <div class="result-area" id="resultado">
    <h2 style="font-size:1.5rem; margin-bottom:12px;">📊 Seu termômetro de gargalo</h2>

    <div class="score-header">
      <div>
        <div class="label">Índice de perda</div>
        <div class="big"><span id="scoreNum">0</span> <span style="font-size:1.2rem; opacity:0.6;">/ 100</span></div>
      </div>
      <div>
        <span class="status-badge" id="badgeStatus">🔴 CRÍTICO</span>
      </div>
    </div>

    <div class="termometro-wrapper">
      <div class="termometro-bg">
        <div class="termometro-bar" id="barraProgresso"></div>
      </div>
      <div class="termometro-labels">
        <span>🟢 OK</span>
        <span>🟡 Atenção</span>
        <span>🔴 Crítico</span>
      </div>
    </div>

    <div class="pain-box" id="painBox">
      <strong>⚠️ O que isso significa na prática:</strong><br />
      <span id="mensagemDor">Carregando...</span>
    </div>

    <div class="solucao-box">
      <div class="titulo-solucao">🚀 A solução que resolve</div>

      <ul>
        <li>Projeto + documentação + ART + homologação em fluxo integrado.</li>
        <li>Prazo fixo e rastreabilidade.</li>
        <li>Expertise prática em todas as distribuidoras de energia elétrica.</li>
        <li>Capacidade sob demanda para absorver picos.</li>
        <li>Redução de retrabalho e horas improdutivas.</li>
      </ul>

      <div class="experiencia">
        Conte com a experiência de quem já atuou na engenharia de grandes empresas do setor e hoje exerce a função de Perito do TJPR.
      </div>

      <div class="action-row">
        <a class="action-btn whatsapp" id="whatsappBtn" href="#" target="_blank">
          Quero minha consultoria grátis no WhatsApp 💬
        </a>
      </div>
    </div>

  </div>

</div>

<script>
  function calcular() {
    const radios = document.querySelectorAll('input[type="radio"]:checked');
    if (radios.length < 7) {
      alert('⚠️ Responda todas as 7 perguntas para gerar seu diagnóstico!');
      return;
    }

    let total = 0;
    radios.forEach(r => total += parseInt(r.value));

    const maxTotal = 48;
    let finalScore = Math.round((total / maxTotal) * 100);
    if (finalScore > 100) finalScore = 100;

    document.getElementById('scoreNum').innerText = finalScore;
    document.getElementById('barraProgresso').style.width = finalScore + '%';

    let statusText = '', statusClass = '', msg = '';

    if (finalScore >= 60) {
      statusText = 'CRÍTICO';
      statusClass = 'status-vermelho';
      msg = 'Sua engenharia está destruindo sua margem de lucro. Você perde projetos, atrasa clientes e paga retrabalho. Cada hora gasta com documentação é uma venda que você deixa de fazer. Sem uma solução imediata, seu crescimento vai estagnar.';
    } else if (finalScore >= 35) {
      statusText = 'ATENÇÃO';
      statusClass = 'status-amarelo';
      msg = 'Você já sente os primeiros sinais de gargalo. A burocracia está consumindo seu tempo e os retrabalhos começam a aparecer. Seu negócio está perdendo eficiência e você está perto de travar. Hora de estruturar antes que piore.';
    } else {
      statusText = 'OK';
      statusClass = 'status-verde';
      msg = 'Sua operação atual até funciona, mas você sabe que não é escalável. Se quiser crescer de verdade, vai precisar de um suporte de engenharia que entregue prazo e qualidade. Estou aqui para quando você quiser dar o próximo passo.';
    }

    const badge = document.getElementById('badgeStatus');
    badge.innerText = statusText;
    badge.className = 'status-badge ' + statusClass;

    document.getElementById('mensagemDor').innerHTML = msg;

    const numero = '557791452853';

    const texto = 
`MEU DIAGNÓSTICO RÁPIDO
Pontuacao: ${finalScore}/100
Classificacao: ${statusText}
Diagnostico: ${msg}

---
Quero saber como sua engenharia pode resolver isso?`;

    const url = `https://wa.me/${numero}?text=${encodeURIComponent(texto)}`;
    document.getElementById('whatsappBtn').href = url;

    const resultDiv = document.getElementById('resultado');
    resultDiv.classList.add('show');
    resultDiv.scrollIntoView({ behavior: 'smooth', block: 'start' });
  }
</script>

</body>
</html>
