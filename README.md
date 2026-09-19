<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover, maximum-scale=1.0, user-scalable=no" />
<meta name="theme-color" content="#1f1f2e" />
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
<title>OVER REQUIEMZ 攻略</title>
<style>
  * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
  html, body {
    margin: 0; padding: 0;
    background: #f5f5f7;
    color: #1f1f2e;
    font-family: -apple-system, BlinkMacSystemFont, "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif;
    font-size: 15px;
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
    overscroll-behavior-y: none;
  }
  body {
    padding-top: env(safe-area-inset-top);
    padding-bottom: env(safe-area-inset-bottom);
  }
  a { color: inherit; text-decoration: none; }
  button { font-family: inherit; }

  /* 顶部导航 */
  .nav {
    position: sticky; top: 0; z-index: 10;
    background: #1f1f2e; color: #fff;
    padding: 12px 16px;
    display: flex; align-items: center; gap: 10px;
    min-height: 48px;
    padding-top: calc(12px + env(safe-area-inset-top));
  }
  .nav .back {
    background: none; border: 0; color: #fff;
    font-size: 22px; padding: 4px 10px 4px 0;
    cursor: pointer; display: none;
  }
  .nav .title {
    font-size: 17px; font-weight: 600;
    flex: 1; text-align: center;
  }
  .nav.has-back .title { text-align: left; }
  .nav.has-back .back { display: block; }

  .container { padding: 16px; max-width: 720px; margin: 0 auto; }

  /* 首页头部 */
  .hero {
    text-align: center;
    padding: 20px 0 24px;
  }
  .hero h1 {
    margin: 0; font-size: 26px; letter-spacing: 1px;
    color: #1f1f2e;
  }
  .hero .jp {
    font-size: 14px; color: #666; margin-top: 6px;
  }
  .hero .tip {
    font-size: 12px; color: #999; margin-top: 10px;
    line-height: 1.6;
  }

  /* 角色卡片 */
  .card-list { display: flex; flex-direction: column; gap: 12px; }
  .card {
    display: flex; align-items: stretch;
    background: #fff;
    border-radius: 14px;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    cursor: pointer;
    transition: transform 0.12s ease, box-shadow 0.12s ease;
  }
  .card:active {
    transform: scale(0.985);
    box-shadow: 0 1px 4px rgba(0,0,0,0.08);
  }
  .card .bar {
    width: 6px; flex-shrink: 0;
  }
  .card .body {
    flex: 1; padding: 14px 16px;
    min-width: 0;
  }
  .card .name {
    font-size: 17px; font-weight: 600; color: #1f1f2e;
  }
  .card .jp {
    font-size: 12px; color: #999; margin-top: 2px;
  }
  .card .cv {
    font-size: 12px; color: #888; margin-top: 6px;
  }
  .card .arrow {
    display: flex; align-items: center; padding: 0 16px;
    color: #ccc; font-size: 22px;
  }

  /* 详情页头部 */
  .detail-head {
    background: #fff;
    border-radius: 14px;
    padding: 16px 18px;
    margin-bottom: 14px;
    border-left: 6px solid #1f1f2e;
  }
  .detail-head .name {
    font-size: 20px; font-weight: 700; color: #1f1f2e;
  }
  .detail-head .jp {
    font-size: 12px; color: #888; margin-top: 4px;
  }

  /* 筛选标签 */
  .tabs {
    display: flex; gap: 8px;
    overflow-x: auto;
    padding-bottom: 4px;
    margin-bottom: 14px;
    -webkit-overflow-scrolling: touch;
    scrollbar-width: none;
  }
  .tabs::-webkit-scrollbar { display: none; }
  .tab {
    flex-shrink: 0;
    padding: 8px 18px;
    border-radius: 999px;
    background: #fff;
    color: #666;
    font-size: 13px;
    border: 0;
    cursor: pointer;
    transition: background 0.15s, color 0.15s;
    white-space: nowrap;
  }
  .tab.active {
    background: #1f1f2e;
    color: #fff;
  }

  /* 攻略条目（移动端用卡片式） */
  .list { display: flex; flex-direction: column; gap: 10px; }
  .item {
    background: #fff;
    border-radius: 12px;
    padding: 12px 14px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.04);
    position: relative;
  }
  .item .chapter {
    display: inline-block;
    font-size: 11px;
    color: #888;
    background: #f0f0f3;
    padding: 2px 8px;
    border-radius: 6px;
    margin-bottom: 8px;
  }
  .item .choice {
    font-size: 15px;
    color: #1f1f2e;
    line-height: 1.5;
    word-break: break-word;
  }
  .item.key .choice {
    font-weight: 700;
    color: #c0392b;
  }
  .item.key::before {
    content: "";
    position: absolute;
    top: 14px; right: 14px;
    width: 6px; height: 6px;
    border-radius: 50%;
    background: #c0392b;
  }
  .item .note {
    font-size: 12px;
    color: #999;
    margin-top: 6px;
    line-height: 1.5;
  }

  .footer {
    text-align: center;
    color: #aaa;
    font-size: 12px;
    padding: 24px 0 calc(24px + env(safe-area-inset-bottom));
  }

  /* 桌面端：稍微大一点 */
  @media (min-width: 600px) {
    body { font-size: 16px; }
    .hero h1 { font-size: 32px; }
    .card .name { font-size: 18px; }
    .detail-head .name { font-size: 22px; }
  }

  /* 空状态 */
  .empty {
    text-align: center;
    color: #999;
    padding: 60px 0;
    font-size: 14px;
  }

  /* 加载中 */
  .loading {
    text-align: center;
    padding: 60px 0;
    color: #999;
    font-size: 14px;
  }
</style>
</head>
<body>

<div class="nav" id="nav">
  <button class="back" id="backBtn" aria-label="返回">←</button>
  <div class="title" id="navTitle">OVER REQUIEMZ 攻略</div>
</div>

<div class="container" id="app"></div>

<script>
/* ========== 数据 ========== */
const characters = [
  {
    id: 'kaize',
    name: '凯泽·奥兹玛',
    nameJp: 'カイゼ・オズマ',
    cv: '阿座上洋平',
    color: '#8B0000',
    data: [
      { chapter: '序章', choice: '醒来', note: '', key: false },
      { chapter: '序章', choice: '去废墟探索', note: '解锁奖励语音', key: true },
      { chapter: '任务1', choice: '保持从容', note: '解锁奖励语音', key: true },
      { chapter: '任务2', choice: '待在一起', note: '解锁奖励语音', key: true },
      { chapter: '任务3', choice: '不治之症', note: '解锁奖励语音', key: true },
      { chapter: '任务4', choice: '冲出房间', note: '解锁奖励语音', key: true },
      { chapter: '任务5', choice: '详细告诉我', note: '解锁奖励语音；存档 SAVE 1', key: true },
      { chapter: '任务5（分歧）', choice: '阻止阿克莱', note: '→ 真相路线', key: true },
      { chapter: '任务5（分歧）', choice: '保护凯泽', note: '→ 暗堕路线', key: true },
      { chapter: '真相6', choice: '立刻离开村子', note: '解锁奖励语音', key: true },
      { chapter: '真相7', choice: '有人扭曲了真相', note: '解锁奖励语音', key: true },
      { chapter: '真相8', choice: '凯泽不写字', note: '解锁奖励语音', key: true },
      { chapter: '真相9', choice: '相信凯泽', note: '解锁奖励语音', key: true },
      { chapter: '真相10', choice: '思念凯泽', note: '解锁奖励语音；存档 SAVE 2', key: true },
      { chapter: '真相结局B', choice: '如果是凯泽就不会输', note: '从 SAVE 2 进入', key: false },
      { chapter: '真相结局O', choice: '我在你身边', note: '从 SAVE 2 读取', key: false },
      { chapter: '暗堕6', choice: '多亏身体还没习惯', note: '解锁奖励语音', key: true },
      { chapter: '暗堕7', choice: '离开门边', note: '解锁奖励语音', key: true },
      { chapter: '暗堕8', choice: '什么也不说，保持沉默', note: '解锁奖励语音', key: true },
      { chapter: '暗堕9', choice: '坦率地道歉', note: '', key: false },
      { chapter: '暗堕10', choice: '逃进随便一间房间', note: '存档 SAVE 3', key: true },
      { chapter: '暗堕结局R', choice: '希望你能原谅我', note: '从 SAVE 3 进入', key: false },
      { chapter: '暗堕结局N', choice: '想再谈一次', note: '从 SAVE 3 读取', key: false }
    ]
  },
  {
    id: 'claude',
    name: '克劳德·格雷恩',
    nameJp: 'クロード・グレイン',
    cv: '古川慎',
    color: '#2E8B57',
    data: [
      { chapter: '序章', choice: '醒来', note: '', key: false },
      { chapter: '序章', choice: '去废墟探索', note: '选择克劳德', key: true },
      { chapter: '任务1', choice: '说实话', note: '解锁奖励语音', key: true },
      { chapter: '任务2', choice: '有人在', note: '解锁奖励语音', key: true },
      { chapter: '任务3', choice: '保持沉默', note: '解锁奖励语音', key: true },
      { chapter: '任务4', choice: '告诉克劳德', note: '解锁奖励语音', key: true },
      { chapter: '任务5', choice: '他们死在这里', note: '存档 SAVE 1', key: true },
      { chapter: '任务5（分歧）', choice: '你必须赎罪', note: '→ 真相路线', key: true },
      { chapter: '任务5（分歧）', choice: '你必须死', note: '→ 暗堕路线', key: true },
      { chapter: '真相6', choice: '安静地投降', note: '', key: false },
      { chapter: '真相7', choice: '戒指', note: '', key: false },
      { chapter: '真相8', choice: '使用除草剂', note: '', key: false },
      { chapter: '真相9', choice: '继续他的研究', note: '', key: false },
      { chapter: '真相10', choice: '死者不会回来', note: '存档 SAVE 2', key: true },
      { chapter: '真相结局O', choice: '我在你身边', note: '从 SAVE 2 进入', key: false },
      { chapter: '真相结局R', choice: '别被骗了', note: '从 SAVE 2 读取', key: false },
      { chapter: '暗堕6', choice: '你现在要做什么？', note: '', key: false },
      { chapter: '暗堕7', choice: '……复制生物？', note: '', key: false },
      { chapter: '暗堕8', choice: '帮我忘记他们', note: '', key: false },
      { chapter: '暗堕9', choice: '我会保持沉默', note: '', key: false },
      { chapter: '暗堕10', choice: '刺伤自己', note: '存档 SAVE 3', key: true },
      { chapter: '暗堕结局A', choice: '选择克劳德', note: '从 SAVE 3 进入', key: false },
      { chapter: '暗堕结局M', choice: '说实话', note: '从 SAVE 3 读取', key: false }
    ]
  },
  {
    id: 'molly',
    name: '莫莉·伍德兰德',
    nameJp: 'モリィ・ウッドランド',
    cv: '石川界人',
    color: '#4A4A8A',
    data: [
      { chapter: '序章', choice: '醒来', note: '', key: false },
      { chapter: '序章', choice: '去废墟探索', note: '选择莫莉', key: true },
      { chapter: '任务1', choice: '安静地躲起来', note: '解锁奖励语音', key: true },
      { chapter: '任务2', choice: '见到了老奶奶', note: '解锁奖励语音', key: true },
      { chapter: '任务3', choice: '特意把钥匙给了出去', note: '解锁奖励语音', key: true },
      { chapter: '任务4', choice: '不害怕才奇怪', note: '解锁奖励语音', key: true },
      { chapter: '任务5', choice: '有人触碰了', note: '存档 SAVE 1', key: true },
      { chapter: '任务5（分歧）', choice: '催促回去', note: '→ 真相路线', key: true },
      { chapter: '任务5（分歧）', choice: '仔细调查每个角落', note: '→ 暗堕路线', key: true },
      { chapter: '真相6', choice: '信息的传递', note: '', key: false },
      { chapter: '真相7', choice: '使用乌鸦', note: '', key: false },
      { chapter: '真相8', choice: '使用地铁', note: '', key: false },
      { chapter: '真相9', choice: '伪装死亡', note: '', key: false },
      { chapter: '真相10', choice: '想为他洗清遗憾', note: '存档 SAVE 2', key: true },
      { chapter: '真相结局P', choice: '想留在他身边', note: '从 SAVE 2 进入', key: false },
      { chapter: '真相结局R', choice: '修复心灵', note: '从 SAVE 2 读取', key: false },
      { chapter: '暗堕6', choice: '「亲老鼠」', note: '', key: false },
      { chapter: '暗堕7', choice: '取代了身份', note: '', key: false },
      { chapter: '暗堕8', choice: '是被拐走的孩子', note: '', key: false },
      { chapter: '暗堕9', choice: '多亏了莫莉', note: '', key: false },
      { chapter: '暗堕10', choice: '为了杀害', note: '存档 SAVE 2', key: true },
      { chapter: '暗堕结局A', choice: '不做任何约定', note: '从 SAVE 2 进入', key: false },
      { chapter: '暗堕结局Y', choice: '立下誓言', note: '从 SAVE 2 读取', key: false }
    ]
  },
  {
    id: 'noil',
    name: '诺伊尔·贝斯蒂亚',
    nameJp: 'ノイル・ベスティア',
    cv: '铃木崚汰',
    color: '#B8860B',
    data: [
      { chapter: '序章', choice: '醒来', note: '', key: false },
      { chapter: '序章', choice: '去废墟探索', note: '选择诺伊尔', key: true },
      { chapter: '任务1', choice: '回瞪他', note: '解锁奖励语音', key: true },
      { chapter: '任务2', choice: '游泳？', note: '解锁奖励语音', key: true },
      { chapter: '任务3', choice: '呵斥他', note: '解锁奖励语音', key: true },
      { chapter: '任务4', choice: '尸体是支离破碎的', note: '解锁奖励语音', key: true },
      { chapter: '任务5', choice: '拼命呼唤', note: '存档 SAVE 1', key: true },
      { chapter: '任务5（分歧）', choice: '扔出火把', note: '→ 真相路线', key: true },
      { chapter: '任务5（分歧）', choice: '你是我国的子民？', note: '→ 暗堕路线', key: true },
      { chapter: '真相6', choice: '钻到平台下面', note: '', key: false },
      { chapter: '真相7', choice: '保持警惕', note: '', key: false },
      { chapter: '真相8', choice: '在废墟中', note: '', key: false },
      { chapter: '真相9', choice: '他去了某个地方', note: '', key: false },
      { chapter: '真相10', choice: '拼命忍耐', note: '存档 SAVE 2', key: true },
      { chapter: '真相结局E', choice: '终于找到了真相', note: '从 SAVE 2 进入', key: false },
      { chapter: '真相结局R', choice: '我无法原谅你', note: '从 SAVE 2 读取', key: false },
      { chapter: '暗堕6', choice: '怀疑他的身份', note: '', key: false },
      { chapter: '暗堕7', choice: '让他脱下衣服', note: '', key: false },
      { chapter: '暗堕8', choice: '给他水喝', note: '', key: false },
      { chapter: '暗堕9', choice: '让他无力化', note: '', key: false },
      { chapter: '暗堕10', choice: '别杀我！', note: '存档 SAVE 3', key: true },
      { chapter: '暗堕结局Y', choice: '放下刀', note: '从 SAVE 3 进入', key: false },
      { chapter: '暗堕结局L', choice: '杀死诺伊尔', note: '从 SAVE 3 读取', key: false }
    ]
  },
  {
    id: 'dorothy',
    name: '多萝西',
    nameJp: 'ドロシー',
    cv: '堀江瞬',
    color: '#6A0DAD',
    data: [
      { chapter: '序章', choice: '醒来', note: '', key: false },
      { chapter: '序章', choice: '去废墟探索', note: '选择多萝西', key: true },
      { chapter: '任务1', choice: '蹲下', note: '解锁奖励语音', key: true },
      { chapter: '任务2', choice: '我想得到建议', note: '解锁奖励语音', key: true },
      { chapter: '任务3', choice: '责备他', note: '解锁奖励语音', key: true },
      { chapter: '任务4', choice: '我能读懂奥兹的文字', note: '解锁奖励语音', key: true },
      { chapter: '任务5', choice: '充当诱饵', note: '存档 SAVE 1', key: true },
      { chapter: '任务5（分歧）', choice: '拒绝', note: '→ 真相路线', key: true },
      { chapter: '任务5（分歧）', choice: '交出你的身体', note: '→ 暗堕路线', key: true },
      { chapter: '真相6', choice: '你非常有人性', note: '', key: false },
      { chapter: '真相7', choice: '死者', note: '', key: false },
      { chapter: '真相8', choice: '我可以和你一起住吗？', note: '', key: false },
      { chapter: '真相9', choice: '争取时间', note: '', key: false },
      { chapter: '真相10', choice: '多萝西的牺牲', note: '存档 SAVE 2', key: true },
      { chapter: '真相结局I', choice: '我会做我能做的一切', note: '从 SAVE 2 进入', key: false },
      { chapter: '真相结局W', choice: '我不会离开他', note: '从 SAVE 2 读取', key: false },
      { chapter: '暗堕6', choice: '自然地行动', note: '', key: false },
      { chapter: '暗堕7', choice: '你不是很孤独吗', note: '', key: false },
      { chapter: '暗堕8', choice: '我会留在你身边', note: '', key: false },
      { chapter: '暗堕9', choice: '我开始害怕了', note: '', key: false },
      { chapter: '暗堕10', choice: '道歉', note: '存档 SAVE 3', key: true },
      { chapter: '暗堕结局H', choice: '我想结束这一切', note: '从 SAVE 3 进入', key: false },
      { chapter: '暗堕结局S', choice: '还不要放弃', note: '从 SAVE 3 读取', key: false }
    ]
  }
];

/* ========== 工具函数 ========== */
function escapeHtml(s) {
  if (s == null) return '';
  return String(s)
    .replace(/&/g, '&amp;')
    .replace(/</g, '&lt;')
    .replace(/>/g, '&gt;')
    .replace(/"/g, '&quot;')
    .replace(/'/g, '&#39;');
}

function filterData(data, filter) {
  if (filter === 'all') return data;
  if (filter === 'common') {
    return data.filter(item =>
      !item.chapter.includes('真相') &&
      !item.chapter.includes('暗堕') &&
      !item.chapter.includes('结局')
    );
  }
  if (filter === 'fact') {
    return data.filter(item =>
      item.chapter.includes('真相') || item.chapter.includes('分歧')
    );
  }
  if (filter === 'dark') {
    return data.filter(item =>
      item.chapter.includes('暗堕') || item.chapter.includes('分歧')
    );
  }
  return data;
}

/* ========== 视图渲染 ========== */
const app = document.getElementById('app');
const nav = document.getElementById('nav');
const navTitle = document.getElementById('navTitle');
const backBtn = document.getElementById('backBtn');

let currentFilter = 'all';

function renderHome() {
  currentFilter = 'all';
  nav.classList.remove('has-back');
  navTitle.textContent = 'OVER REQUIEMZ 攻略';
  document.title = 'OVER REQUIEMZ 攻略';

  const cards = characters.map(c => `
    <a class="card" href="#/${c.id}">
      <div class="bar" style="background:${c.color}"></div>
      <div class="body">
        <div class="name">${escapeHtml(c.name)}</div>
        <div class="jp">${escapeHtml(c.nameJp)}</div>
        <div class="cv">CV：${escapeHtml(c.cv)}</div>
      </div>
      <div class="arrow">›</div>
    </a>
  `).join('');

  app.innerHTML = `
    <div class="hero">
      <h1>OVER REQUIEMZ</h1>
      <div class="jp">オーバーレクイエムズ 攻略</div>
      <div class="tip">点击角色查看详细攻略 · 红点为关键选择</div>
    </div>
    <div class="card-list">${cards}</div>
    <div class="footer">本攻略仅供参考 · 内容为文字信息</div>
  `;
  window.scrollTo(0, 0);
}

function renderDetail(charId) {
  const character = characters.find(c => c.id === charId);
  if (!character) {
    renderHome();
    return;
  }
  currentFilter = 'all';
  nav.classList.add('has-back');
  navTitle.textContent = character.name + ' 攻略';
  document.title = character.name + ' 攻略';

  const tabs = `
    <div class="tabs" id="tabs">
      <button class="tab active" data-filter="all">全部</button>
      <button class="tab" data-filter="common">共通</button>
      <button class="tab" data-filter="fact">真相</button>
      <button class="tab" data-filter="dark">暗堕</button>
    </div>
  `;

  const list = `
    <div class="list" id="list"></div>
    <div class="footer" id="count"></div>
  `;

  app.innerHTML = `
    <div class="detail-head" style="border-left-color:${character.color}">
      <div class="name">${escapeHtml(character.name)}</div>
      <div class="jp">${escapeHtml(character.nameJp)} · CV：${escapeHtml(character.cv)}</div>
    </div>
    ${tabs}
    ${list}
  `;

  // 绑定 tab 事件
  document.getElementById('tabs').addEventListener('click', e => {
    const btn = e.target.closest('.tab');
    if (!btn) return;
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    btn.classList.add('active');
    currentFilter = btn.dataset.filter;
    renderList(character);
  });

  renderList(character);
  window.scrollTo(0, 0);
}

function renderList(character) {
  const listEl = document.getElementById('list');
  const countEl = document.getElementById('count');
  const items = filterData(character.data, currentFilter);

  if (!items.length) {
    listEl.innerHTML = '<div class="empty">暂无内容</div>';
    countEl.textContent = '';
    return;
  }

  listEl.innerHTML = items.map(item => `
    <div class="item${item.key ? ' key' : ''}">
      <div class="chapter">${escapeHtml(item.chapter)}</div>
      <div class="choice">${escapeHtml(item.choice)}</div>
      ${item.note ? `<div class="note">${escapeHtml(item.note)}</div>` : ''}
    </div>
  `).join('');

  countEl.textContent = `共 ${items.length} 条记录`;
}

/* ========== 路由 ========== */
function route() {
  const hash = location.hash.replace(/^#\/?/, '');
  if (!hash) {
    renderHome();
  } else {
    renderDetail(hash);
  }
}

backBtn.addEventListener('click', () => {
  location.hash = '';
  history.replaceState(null, '', location.pathname + location.search);
  renderHome();
});

window.addEventListener('hashchange', route);
window.addEventListener('DOMContentLoaded', route);
if (document.readyState !== 'loading') route();

/* 兼容直接打开 #/kaize 的情况 */
if (!location.hash && document.readyState === 'complete') {
  // 已渲染
}
</script>
</body>
</html>
