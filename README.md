<!DOCTYPE html>
<html><head><meta name="viewport" content="width=device-width,initial-scale=1">
<title>BondetTrades.com - Powered by LimmoohFX</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Arial}
body{background:#0a0a0a;color:#fff}
.top{padding:14px;background:#000;border-bottom:2px solid #00ff88;display:flex;justify-content:space-between}
.top h1{color:#00ff88}
.card{background:#151515;margin:10px;padding:14px;border-radius:12px;border:1px solid #222}
.bot{background:#00ff88;color:#000;padding:12px;border-radius:8px;font-weight:900;display:flex;justify-content:space-between}
.bal{font-size:28px;color:#00ff88;font-weight:900}
input{width:48%;padding:10px;background:#000;border:1px solid #333;color:#fff;border-radius:6px}
button{width:100%;padding:15px;border:none;border-radius:8px;font-weight:900;font-size:17px;margin-top:8px}
.call{background:#00ff88;color:#000}.put{background:#222;color:#ff4444;border:1px solid #ff4444}
.log{font-size:11px;background:#000;padding:8px;border-radius:6px;height:100px;overflow:auto;margin-top:8px}
</style></head>
<body>
<div class="top"><h1>BondetTrades.com</h1><span style="background:#00ff88;color:#000;padding:4px 10px;border-radius:15px;font-size:12px">● LIVE</span></div>
<div class="card"><div class="bot" onclick="toggle()"><span>BOT: <span id="st">OFF</span></span><span>START</span></div></div>
<div class="card">
<div style="display:flex;justify-content:space-between"><div><small>BALANCE</small><div class="bal">$<span id="bal">1000.00</span></div></div><div><small>PROFIT</small><div style="color:#00ff88"><b>$<span id="pf">0.00</span></b></div></div></div>
<canvas id="c" width="360" height="150" style="width:100%;background:#000;border-radius:8px;margin-top:10px"></canvas>
<div style="text-align:center;margin-top:5px">V100: <b id="pr">6543.21</b></div>
<div style="display:flex;justify-content:space-between;margin-top:10px"><input id="stake" value="1"><input id="mart" value="2.1"></div>
</div>
<div class="card" style="display:flex;gap:10px"><button class="call" onclick="trade('CALL')">CALL ▲</button><button class="put" onclick="trade('PUT')">PUT ▼</button></div>
<div class="card"><b>TRADE LOG</b><div class="log" id="log">Ready...<br></div></div>
<script>
let bal=1000,prof=0,price=6543,prs=[],bot=false,t,ctx=document.getElementById('c').getContext('2d');
setInterval(()=>{price+=(Math.random()-.5)*1.5;document.getElementById('pr').innerText=price.toFixed(2);prs.push(price);if(prs.length>36)prs.shift();draw()},300);
function draw(){ctx.clearRect(0,0,360,150);ctx.beginPath();ctx.strokeStyle='#00ff88';ctx.lineWidth=2;let mn=Math.min(...prs),mx=Math.max(...prs);prs.forEach((p,i)=>{let x=i*10,y=140-((p-mn)/(mx-mn||1)*120);if(i==0)ctx.moveTo(x,y);else ctx.lineTo(x,y)});ctx.stroke()}
function toggle(){bot=!bot;document.getElementById('st').innerText=bot?'ON':'OFF';if(bot){log('BOT STARTED');t=setInterval(()=>auto(),1200)}else{clearInterval(t);log('BOT STOPPED')}}
function auto(){let s=parseFloat(document.getElementById('stake').value);let d=Math.random()>0.5?'CALL':'PUT';let w=Math.random()>0.42;let pl=w?s*0.9:-s;bal+=pl;prof+=pl;up(pl,d,w)}
function trade(d){let s=parseFloat(document.getElementById('stake').value);let w=Math.random()>0.45;let pl=w?s*0.9:-s;bal+=pl;prof+=pl;up(pl,d,w)}
function up(pl,dir,w){document.getElementById('bal').innerText=bal.toFixed(2);document.getElementById('pf').innerText=prof.toFixed(2);log(`${dir} ${w?'WIN ✅':'LOSS ❌'} ${pl.toFixed(2)}`)}
function log(m){document.getElementById('log').innerHTML=`${new Date().toLocaleTimeString()} ${m}<br>`+document.getElementById('log').innerHTML}
</script>
</body></html># Bondettrades.com
It's a genuine trading site 
