<!doctype html>
<html lang="tr">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Benimle barışır mısın?</title>
<style>
  :root{--bg:#f8eef6;--card:#fff;--accent:#ff6b81;--muted:#666;}
  html,body{height:100%;margin:0;font-family:Segoe UI,Roboto,Helvetica,Arial,sans-serif;background:linear-gradient(135deg,#fffafa 0%, #f6f0ff 100%);}
  .container{min-height:100%;display:flex;flex-direction:column;align-items:center;}
  header{width:100%;background:var(--card);box-shadow:0 6px 20px rgba(0,0,0,0.06);padding:18px 16px;text-align:center;font-size:20px;font-weight:600;color:var(--accent);position:sticky;top:0;z-index:10;}
  .stage{flex:1;display:flex;align-items:center;justify-content:center;padding:40px 20px;}
  .card{width:100%;max-width:720px;background:linear-gradient(180deg,#ffffffcc,#fff);border-radius:16px;box-shadow:0 12px 40px rgba(0,0,0,0.08);padding:36px;text-align:center;}
  .question{font-size:26px;margin-bottom:22px;color:#333;}
  .sub{color:var(--muted);margin-bottom:28px;}
  .buttons{display:flex;gap:18px;align-items:center;justify-content:center;position:relative;min-height:80px;}
  button{border:0;padding:14px 28px;font-size:18px;border-radius:999px;cursor:pointer;user-select:none;transition:transform 160ms ease, box-shadow 160ms ease;box-shadow:0 8px 18px rgba(0,0,0,0.08);}
  .yes{background:linear-gradient(90deg,#ff8aa0,#ff557a);color:#fff;}
  .no{background:#fff;color:#ff557a;border:2px solid #ffd4dd;}
  .no:active, .yes:active{transform:translateY(2px);}
  .big-yes{display:none;font-size:42px;padding:28px 48px;border-radius:24px;box-shadow:0 20px 40px rgba(0,0,0,0.12);}
  .final-message{margin-top:22px;font-size:20px;color:#333;display:none;animation:fadeIn .6s ease both;}
  @keyframes fadeIn{from{opacity:0; transform:translateY(10px)}to{opacity:1; transform:translateY(0)}}
  .counter{margin-top:12px;color:var(--muted);font-size:14px;}
</style>
</head>
<body>
<div class="container">
  <header id="topMessage">Benimle barışır mısın? Özür dilerim ❤️</header>
  <main class="stage">
    <div class="card" role="main">
      <div class="question">Seni kırdım, çok üzgünüm. Lütfen beni affeder misin?</div>
      <div class="sub">Sevgilim şu an trip atıyor, seni tekrar güldürmek istiyorum.</div>
      <div class="buttons" id="buttonsArea">
        <button class="yes" id="yesBtn">Evet</button>
        <button class="no" id="noBtn">Hayır</button>
      </div>
      <div class="counter" id="counterText">Hayır butonuna basılma sayısı: 0</div>
      <div style="margin-top:18px;">
        <button class="big-yes" id="bigYes">EVET!!</button>
      </div>
      <div class="final-message" id="finalMsg"></div>
    </div>
  </main>
</div>
<script>
  const yesBtn=document.getElementById('yesBtn');
  const noBtn=document.getElementById('noBtn');
  const counterText=document.getElementById('counterText');
  const bigYes=document.getElementById('bigYes');
  const finalMsg=document.getElementById('finalMsg');
  const buttonsArea=document.getElementById('buttonsArea');
  let noCount=0;
  const REQUIRED_NO=7;
  yesBtn.addEventListener('click',()=>{showThanks();});
  noBtn.addEventListener('click',()=>{noCount++;counterText.textContent='Hayır butonuna basılma sayısı: '+noCount;avoidNoButton();if(noCount>=REQUIRED_NO){yesBtn.style.display='none';noBtn.style.display='none';bigYes.style.display='inline-block';bigYes.classList.add('yes');bigYes.focus();}});
  bigYes.addEventListener('click',()=>{showThanks();});
  noBtn.addEventListener('mouseover',()=>{avoidNoButton();});
  function avoidNoButton(){const area=buttonsArea.getBoundingClientRect();const btn=noBtn.getBoundingClientRect();const maxX=Math.max(10,area.width-btn.width-10);const maxY=Math.max(0,area.height-btn.height);if(window.innerWidth<480){noBtn.style.transform='translateY(-8px) rotate(-6deg)';setTimeout(()=>noBtn.style.transform='translateY(0) rotate(0deg)',180);return;}const newLeft=Math.floor(Math.random()*maxX);const newTop=Math.floor(Math.random()*(maxY+30))-10;noBtn.style.position='relative';noBtn.style.left=newLeft+'px';noBtn.style.top=newTop+'px';}
  function showThanks(){finalMsg.style.display='block';finalMsg.innerHTML='<strong>tesekur ederm balim beni affetigin icin.</strong><br>hadi gorim seni kocum 💋';bigYes.style.display='none';yesBtn.style.display='none';noBtn.style.display='none';counterText.style.display='none';}
</script>
</body>
</html>
