<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)
const toggleMenu = () => { menuOpen.value = !menuOpen.value }
const closeMenu = () => { menuOpen.value = false }

const dishes = [
  { name: '春笋 · 青豆 · 橄榄油', price: '¥ 68', description: '临安春笋 / 当日采摘青豆 / 柚子醋', image: 'https://images.unsplash.com/photo-1547592180-85f173990554?auto=format&fit=crop&w=900&q=85', alt: '春笋与青豆时蔬沙拉' },
  { name: '海鲈 · 青酱 · 炭火', price: '¥ 128', description: '东海当日鲜鱼 / 自制青酱 / 炭火慢烤', image: 'https://images.unsplash.com/photo-1476224203421-9ac39bcb3327?auto=format&fit=crop&w=900&q=85', alt: '香煎时令鱼配绿色香草' },
  { name: '谷物 · 山野菜 · 温泉蛋', price: '¥ 88', description: '本地小农谷物 / 山野嫩芽 / 有机鸡蛋', image: 'https://images.unsplash.com/photo-1512621776951-a57141f2eefd?auto=format&fit=crop&w=900&q=85', alt: '谷物与时令蔬菜组成的分享盘' },
]
</script>

<template>

  <div class="topline">本季新菜单 <span>✳</span> 山野春鲜 · 已上新，欢迎预约席位</div>
  <header>
    <a class="brand" href="#home" aria-label="禾间首页"><span class="brand-mark">禾</span><span class="brand-name">禾间<small>HÉJIAN · SEASONAL TABLE</small></span></a>
    <button class="menu-toggle" aria-label="打开菜单" :aria-expanded="menuOpen" @click="toggleMenu">{{ menuOpen ? '×' : '☰' }}</button>
    <nav class="nav" :class="{ open: menuOpen }" aria-label="主导航" @click="closeMenu"><a href="#menu">当季菜单</a><a href="#story">关于禾间</a><a href="#visit">到店信息</a><a class="book" href="#visit">预约席位　↗</a></nav>
  </header>
  <main>
    <section class="hero" id="home">
      <div class="hero-copy">
        <div class="eyebrow">A TABLE IN NATURE · SINCE 2018</div>
        <h1>一席山野<br><em>四时有味</em></h1>
        <p class="hero-desc">从山野、田间与海岸，拾取当季的鲜味。<br>以一餐饭的时间，感受土地的呼吸。</p>
        <div class="hero-actions"><a class="button" href="#menu">探索当季菜单 <span>↗</span></a><a class="text-link" href="#story">认识禾间</a></div>
        <div class="hero-note"><span class="note-line"></span>杭州 · 西湖区 · 每日 11:30—21:30</div>
      </div>
      <div class="hero-visual"><img class="hero-photo" src="https://images.unsplash.com/photo-1512621776951-a57141f2eefd?auto=format&fit=crop&w=1400&q=88" alt="以时令蔬菜和鲜花呈现的山野料理"/><div class="season-tag">春日<br>鲜味<small>SPRING 2026</small></div></div>
    </section>
    <div class="ticker" aria-label="餐厅理念"><div class="ticker-track">山野寻味 <span class="star">✳</span> 四时而食 <span class="star">✳</span> 本地风土 <span class="star">✳</span> 慢一点，好好吃饭 <span class="star">✳</span> 山野寻味 <span class="star">✳</span> 四时而食 <span class="star">✳</span> 本地风土 <span class="star">✳</span> 慢一点，好好吃饭 <span class="star">✳</span></div></div>
    <section class="section" id="menu">
      <div class="section-head"><div><div class="section-index">01 / FROM THE SEASON</div><h2>此时此地，<br>正好入味</h2></div><p>菜单跟着季节走，也跟着土地走。<br>每一道菜，都从今天的新鲜开始。</p></div>
      <div class="dishes">
        <article v-for="(dish, index) in dishes" :key="dish.name" class="dish"><div class="dish-image"><img :src="dish.image" :alt="dish.alt"/><span class="dish-no">{{ String(index + 1).padStart(2, '0') }}</span></div><div class="dish-meta"><h3>{{ dish.name }}</h3><span class="price">{{ dish.price }}</span></div><p>{{ dish.description }}</p></article>
      </div>
    </section>
    <section class="story" id="story">
      <div class="story-image"><img src="https://images.unsplash.com/photo-1414235077428-338989a2e8c0?auto=format&fit=crop&w=1200&q=85" alt="禾间餐桌上的季节料理与餐具"/></div>
      <div class="story-copy"><div class="section-index">02 / OUR PHILOSOPHY</div><h2>让土地的味道，<br/>留在餐桌上</h2><p>禾间相信，好好吃饭是一件很具体的事。清晨去菜场挑选当季食材，和熟悉的农人一起等候土地的馈赠，再用简单的方式，呈现食物本来的样子。</p><p>我们不追赶远方的流行，只认真对待今天的鲜、眼前的人，和这一餐饭。</p><a href="#visit" class="text-link">走进禾间　↗</a></div>
    </section>
    <section class="visit" id="visit">
      <div><div class="section-index">03 / COME FIND US</div><h2>留一张桌，<br/>等你来吃饭</h2><p>无论是一个人的午餐，还是一桌人的相聚，<br/>禾间都为你留着当季的好味道。</p><div class="visit-details"><div class="detail"><b>地址</b><span>杭州市西湖区青芝坞 18 号<br/>近植物园南门，步行约 5 分钟</span></div><div class="detail"><b>营业时间</b><span>周一至周日　11:30—14:00<br/>晚市　17:30—21:30（最后点单 20:45）</span></div><div class="detail"><b>预约电话</b><span>0571 — 8790 2018</span></div></div><a class="button" href="tel:057187902018">电话预约 <span>↗</span></a></div>
      <div class="map-card" role="img" aria-label="禾间餐厅空间"><div class="map-pin">禾间 HÉJIAN<span>杭州市 · 西湖区 · 青芝坞 18 号</span></div></div>
    </section>
  </main>
  <footer><div class="footer-top"><a class="brand footer-brand" href="#home"><span class="brand-mark">禾</span><span class="brand-name">禾间<small>HÉJIAN · SEASONAL TABLE</small></span></a><div class="footer-message">一餐一饭，<br>都是与土地的相遇。</div></div><div class="footer-bottom"><span>© 2026 HÉJIAN RESTAURANT · 杭州</span><div class="social"><a href="#visit">小红书　↗</a><a href="#visit">微信公众号　↗</a><a href="#home">回到顶部　↑</a></div></div></footer>

</template>

<style>

    :root{--paper:#f5f1e8;--ink:#25291f;--muted:#74776a;--green:#344a37;--lime:#c9d56a;--line:rgba(37,41,31,.18);--serif:'Noto Serif SC',serif;--sans:'DM Sans','Noto Sans SC',sans-serif}
    *{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;background:var(--paper);color:var(--ink);font-family:var(--sans);-webkit-font-smoothing:antialiased}a{color:inherit;text-decoration:none}button{font:inherit}
    .topline{height:34px;background:var(--green);color:#f5f1e8;display:flex;align-items:center;justify-content:center;font-size:10px;letter-spacing:.18em}.topline span{color:var(--lime);padding:0 7px}
    header{height:84px;padding:0 6.2%;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid var(--line);position:relative;z-index:5}.brand{display:flex;align-items:center;gap:12px}.brand-mark{width:36px;height:36px;border:1px solid var(--green);border-radius:50%;display:grid;place-items:center;color:var(--green);font-family:var(--serif);font-size:18px}.brand-name{font-family:var(--serif);font-size:18px;font-weight:600;letter-spacing:.12em}.brand-name small{display:block;font-family:var(--sans);font-size:8px;letter-spacing:.22em;color:var(--muted);margin-top:2px}.nav{display:flex;gap:36px;align-items:center;font-size:12px;letter-spacing:.08em}.nav a{transition:color .2s}.nav a:hover{color:#82904b}.nav .book{border:1px solid var(--ink);padding:12px 18px}.menu-toggle{display:none;background:none;border:0;font-size:22px}
    .hero{min-height:660px;padding:62px 6.2% 68px;display:grid;grid-template-columns:1fr 1.04fr;gap:6%;align-items:center;overflow:hidden}.hero-copy{padding-left:5%;position:relative;z-index:1}.eyebrow{font-size:10px;letter-spacing:.25em;text-transform:uppercase;color:var(--green);display:flex;align-items:center;gap:12px}.eyebrow:before{content:'';width:29px;height:1px;background:currentColor}.hero h1{font-family:var(--serif);font-size:clamp(50px,6.1vw,88px);line-height:1.22;letter-spacing:.08em;font-weight:500;margin:27px 0 20px}.hero h1 em{font-style:normal;color:#879351}.hero-desc{font-family:var(--serif);font-size:14px;line-height:2.1;letter-spacing:.06em;color:#626658;max-width:370px}.hero-actions{display:flex;align-items:center;gap:22px;margin-top:35px}.button{display:inline-flex;align-items:center;justify-content:center;gap:22px;padding:15px 20px;background:var(--green);color:white;font-size:11px;letter-spacing:.12em;transition:transform .2s,background .2s}.button:hover{transform:translateY(-2px);background:#26382a}.text-link{font-size:11px;letter-spacing:.1em;border-bottom:1px solid var(--ink);padding:0 0 6px}.hero-note{display:flex;align-items:center;gap:12px;color:var(--muted);font-size:10px;letter-spacing:.08em;margin-top:55px}.note-line{width:38px;height:1px;background:var(--line)}
    .hero-visual{height:535px;position:relative}.hero-photo{height:100%;width:100%;object-fit:cover;display:block;border-radius:48% 48% 4px 4px;filter:saturate(.82)}.hero-visual:after{content:'';position:absolute;inset:12px -12px -12px 12px;border:1px solid rgba(52,74,55,.5);border-radius:48% 48% 4px 4px;pointer-events:none}.season-tag{position:absolute;bottom:29px;left:-31px;background:var(--lime);width:103px;height:103px;border-radius:50%;display:grid;place-content:center;text-align:center;color:var(--green);font-family:var(--serif);font-size:15px;line-height:1.6;transform:rotate(-9deg)}.season-tag small{font-family:var(--sans);font-size:8px;letter-spacing:.12em}
    .ticker{background:var(--green);color:var(--paper);height:51px;display:flex;align-items:center;overflow:hidden;white-space:nowrap}.ticker-track{display:flex;gap:29px;animation:marquee 34s linear infinite;font-size:10px;letter-spacing:.22em}.ticker .star{color:var(--lime);font-size:15px}@keyframes marquee{to{transform:translateX(-50%)}}
    .section{padding:116px 8.5%}.section-head{display:flex;justify-content:space-between;align-items:end;margin-bottom:47px}.section-index{font-size:10px;letter-spacing:.2em;color:var(--muted)}h2{font-family:var(--serif);font-weight:500;font-size:clamp(33px,4vw,51px);letter-spacing:.08em;line-height:1.35;margin:13px 0 0}.section-head p{font-family:var(--serif);font-size:13px;line-height:1.9;color:var(--muted);max-width:290px;margin:0 0 3px}
    .dishes{display:grid;grid-template-columns:repeat(3,1fr);gap:22px}.dish{min-width:0}.dish-image{height:340px;overflow:hidden;position:relative;background:#d9d4c7}.dish-image img{width:100%;height:100%;object-fit:cover;transition:transform .6s;display:block}.dish:hover .dish-image img{transform:scale(1.045)}.dish-no{position:absolute;top:13px;left:14px;background:var(--paper);width:35px;height:35px;border-radius:50%;display:grid;place-items:center;font-size:10px}.dish-meta{display:flex;justify-content:space-between;align-items:baseline;margin-top:18px}.dish h3{font-family:var(--serif);font-size:19px;font-weight:500;letter-spacing:.08em;margin:0}.price{font-size:11px;color:var(--green);letter-spacing:.08em}.dish p{font-size:11px;color:var(--muted);letter-spacing:.04em;margin:8px 0 0}
    .story{background:#e9e5d9;padding:0 8.5%;display:grid;grid-template-columns:1fr 1fr;min-height:590px;align-items:center;gap:9%}.story-image{height:470px;position:relative}.story-image img{width:100%;height:100%;object-fit:cover;display:block}.story-image:before{content:'H';font-family:var(--serif);font-size:150px;color:var(--lime);position:absolute;right:-28px;top:-70px;line-height:1;z-index:1;opacity:.9}.story-copy{padding:55px 0}.story-copy h2{margin:19px 0 23px}.story-copy p{font-family:var(--serif);font-size:13px;line-height:2.3;color:#66695e;max-width:420px}.story-copy .text-link{display:inline-block;margin-top:20px}
    .visit{padding:105px 8.5%;display:grid;grid-template-columns:1.2fr .8fr;gap:10%;align-items:center}.visit h2{margin-bottom:20px}.visit p{font-family:var(--serif);font-size:13px;line-height:2.2;color:var(--muted)}.visit-details{border-top:1px solid var(--line)}.detail{display:grid;grid-template-columns:95px 1fr;padding:18px 0;border-bottom:1px solid var(--line);font-size:11px;line-height:1.8}.detail b{font-weight:500;color:var(--green);letter-spacing:.1em}.detail span{color:#626658}.visit .button{margin-top:25px}.map-card{height:330px;background:linear-gradient(135deg,rgba(52,74,55,.82),rgba(52,74,55,.34)),url('https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?auto=format&fit=crop&w=1000&q=80') center/cover;display:grid;place-items:center;color:white;position:relative}.map-pin{text-align:center;font-family:var(--serif);font-size:18px;letter-spacing:.15em}.map-pin span{display:block;font-family:var(--sans);font-size:9px;letter-spacing:.22em;margin-top:8px}.map-card:after{content:'VIEW LOCATION ↗';position:absolute;bottom:18px;right:18px;font-size:9px;letter-spacing:.15em}
    footer{background:var(--green);color:#f5f1e8;padding:49px 6.2% 23px}.footer-top{display:flex;justify-content:space-between;align-items:flex-start;padding-bottom:42px}.footer-brand .brand-mark{border-color:var(--lime);color:var(--lime)}.footer-brand .brand-name small{color:#c1c6b5}.footer-message{font-family:var(--serif);font-size:20px;letter-spacing:.12em;line-height:1.8;text-align:right;color:#e0e4d4}.footer-bottom{border-top:1px solid rgba(245,241,232,.25);padding-top:17px;display:flex;justify-content:space-between;font-size:9px;letter-spacing:.1em;color:#c1c6b5}.social{display:flex;gap:20px}
    @media(max-width:850px){header{padding:0 5%;height:72px}.nav{gap:18px}.hero{padding:52px 6% 58px;gap:4%;min-height:560px}.hero-copy{padding-left:0}.hero-visual{height:440px}.section{padding:85px 6%}.dish-image{height:260px}.story{padding:0 6%;gap:6%}.story-image{height:390px}.visit{padding:85px 6%;gap:6%}}
    @media(max-width:620px){.topline{font-size:8px;letter-spacing:.1em}.menu-toggle{display:block}.nav{display:none;position:absolute;left:0;right:0;top:72px;background:var(--paper);padding:24px 6%;border-bottom:1px solid var(--line);flex-direction:column;align-items:flex-start;gap:20px}.nav.open{display:flex}.hero{display:flex;flex-direction:column;padding:44px 7% 58px;gap:45px;align-items:stretch}.hero-copy{padding:0}.hero h1{font-size:57px;margin:22px 0 14px}.hero-desc{font-size:13px}.hero-note{margin-top:33px}.hero-visual{height:390px;margin:0 10px 0 18px}.season-tag{width:83px;height:83px;left:-23px;font-size:12px}.ticker{height:43px}.section{padding:77px 7%}.section-head{display:block;margin-bottom:30px}.section-head p{margin-top:15px}.dishes{grid-template-columns:1fr;gap:32px}.dish-image{height:330px}.story{display:flex;flex-direction:column;padding:58px 7%;gap:31px;align-items:stretch}.story-image{height:330px;margin-right:12px}.story-image:before{font-size:110px;right:-14px;top:-52px}.story-copy{padding:0}.story-copy h2{font-size:36px}.visit{display:flex;flex-direction:column;align-items:stretch;padding:76px 7%;gap:35px}.map-card{height:270px}.footer-top{display:block}.footer-message{text-align:left;margin-top:28px;font-size:17px}.footer-bottom{gap:13px;flex-direction:column}.social{gap:14px}}
  
</style>
