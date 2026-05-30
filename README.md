<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>金璟宇 — 简历 · COMIC EDITION</title>
<style>
  :root {
    --red:       #E63946;
    --blue:      #1D3557;
    --yellow:    #FFD60A;
    --cyan:      #00B4D8;
    --white:     #FEFAE0;
    --black:     #111111;
    --orange:    #FB8500;
    --purple:    #8338EC;
    --green:     #2DC653;
    --gray:      #6C757D;
    --pink:      #FF477E;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  @font-face {
    font-family: 'ComicTitle';
    src: local('Impact'), local('Arial Black'), local('Bebas Neue');
  }

  body {
    font-family: 'Gochi Hand', 'Comic Sans MS', 'KaiTi', 'STKaiti', cursive, sans-serif;
    background: var(--white);
    color: var(--black);
    min-height: 100vh;
    position: relative;
    overflow-x: hidden;
  }

  /* ── Ben-Day Dots Background ── */
  .bg-dots {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    opacity: 0.06;
    --dot-size: 3px;
    --gap: 14px;
    background:
      radial-gradient(circle, #1D3557 var(--dot-size), transparent var(--dot-size)) 0 0 / var(--gap) var(--gap),
      radial-gradient(circle, #E63946 var(--dot-size), transparent var(--dot-size)) calc(var(--gap)/2) calc(var(--gap)/2) / var(--gap) var(--gap);
  }

  /* ── Action Lines Strips ── */
  .page {
    position: relative;
    z-index: 1;
    max-width: 1100px;
    margin: 0 auto;
    padding: 1.5rem;
  }

  /* ── TOP HERO BANNER ── */
  .hero-banner {
    background: var(--red);
    border: 5px solid var(--black);
    padding: 2.5rem 2rem 2rem;
    position: relative;
    box-shadow: 12px 12px 0 var(--black);
    margin-bottom: 2rem;
    overflow: hidden;
  }

  .hero-banner::after {
    content: '';
    position: absolute;
    top: -30px; right: -30px;
    width: 120px; height: 120px;
    background: var(--yellow);
    border: 5px solid var(--black);
    border-radius: 50%;
    box-shadow: 5px 5px 0 var(--black);
  }

  .hero-starburst {
    position: absolute;
    top: 15px; left: 20px;
    font-size: 2.5rem;
    color: var(--yellow);
    text-shadow: 2px 2px 0 var(--black);
    animation: pulse 1.2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { transform: scale(1) rotate(0deg); }
    50% { transform: scale(1.15) rotate(5deg); }
  }

  .hero-speech {
    display: inline-block;
    background: var(--yellow);
    color: var(--black);
    padding: 0.2rem 1rem;
    font-size: 0.75rem;
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    border: 3px solid var(--black);
    margin-bottom: 1rem;
    transform: rotate(-2deg);
    box-shadow: 3px 3px 0 var(--black);
  }

  .hero-name {
    font-family: 'ComicTitle', 'Impact', sans-serif;
    font-size: clamp(4rem, 10vw, 7rem);
    font-weight: 900;
    color: var(--yellow);
    line-height: 0.9;
    text-shadow:
      4px 4px 0 var(--black),
      -1px -1px 0 var(--black),
      1px -1px 0 var(--black),
      -1px 1px 0 var(--black);
    letter-spacing: 0.02em;
    margin-bottom: 0.5rem;
  }

  .hero-subtitle {
    font-size: 1.3rem;
    font-weight: 900;
    color: var(--white);
    text-transform: uppercase;
    letter-spacing: 0.15em;
  }

  .hero-badges {
    display: flex;
    gap: 0.6rem;
    margin-top: 1rem;
    flex-wrap: wrap;
  }

  .hero-badge {
    background: var(--white);
    color: var(--black);
    border: 3px solid var(--black);
    padding: 0.4rem 0.8rem;
    font-size: 0.8rem;
    font-weight: 900;
    display: flex;
    align-items: center;
    gap: 0.4rem;
    box-shadow: 3px 3px 0 var(--black);
    text-transform: uppercase;
  }

  .hero-badge .icon { font-size: 1.1rem; }

  /* ── ACTION DIVIDER ── */
  .action-divider {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin: 1.5rem 0;
    position: relative;
  }

  .action-divider::before {
    content: '';
    flex: 1;
    height: 5px;
    background: var(--black);
    border-radius: 3px;
  }

  .action-burst {
    font-family: 'ComicTitle', 'Impact', sans-serif;
    background: var(--orange);
    color: var(--white);
    border: 4px solid var(--black);
    padding: 0.5rem 1.5rem;
    font-size: 1.1rem;
    font-weight: 900;
    transform: rotate(-1deg);
    box-shadow: 5px 5px 0 var(--black);
    white-space: nowrap;
    letter-spacing: 0.08em;
  }

  .action-divider::after {
    content: '';
    flex: 1;
    height: 5px;
    background: var(--black);
    border-radius: 3px;
  }

  /* ── GRID ── */
  .comic-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }

  /* ── COMIC PANEL ── */
  .comic-panel {
    background: var(--white);
    border: 5px solid var(--black);
    padding: 0;
    box-shadow: 8px 8px 0 var(--black);
    position: relative;
    overflow: hidden;
  }

  .comic-panel.full {
    grid-column: 1 / -1;
  }

  .panel-header {
    padding: 0.8rem 1.2rem;
    border-bottom: 4px solid var(--black);
    display: flex;
    align-items: center;
    gap: 0.6rem;
  }

  .panel-header.red    { background: var(--red); }
  .panel-header.blue   { background: var(--blue); }
  .panel-header.yellow { background: var(--yellow); }
  .panel-header.green  { background: var(--green); }
  .panel-header.orange { background: var(--orange); }
  .panel-header.purple { background: var(--purple); }
  .panel-header.cyan   { background: var(--cyan); }

  .panel-header-icon {
    width: 42px; height: 42px;
    background: var(--white);
    border: 3px solid var(--black);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.3rem;
    box-shadow: 3px 3px 0 var(--black);
    flex-shrink: 0;
  }

  .panel-header h3 {
    font-family: 'ComicTitle', 'Impact', sans-serif;
    font-size: 1.3rem;
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: var(--white);
    text-shadow: 2px 2px 0 rgba(0,0,0,0.4);
  }

  .panel-header.yellow h3,
  .panel-header.yellow .panel-header-icon { color: var(--black); text-shadow: none; }

  .panel-body {
    padding: 1.2rem;
  }

  /* ── Education Item ── */
  .edu-item {
    padding: 1rem;
    margin-bottom: 1rem;
    border: 3px solid var(--black);
    background: #FFF9E6;
    position: relative;
    box-shadow: 4px 4px 0 var(--black);
  }

  .edu-item:last-child { margin-bottom: 0; }

  .edu-school {
    font-family: 'ComicTitle', 'Impact', sans-serif;
    font-size: 1.05rem;
    font-weight: 900;
    color: var(--black);
    margin-bottom: 0.3rem;
  }

  .edu-meta {
    font-size: 0.78rem;
    font-weight: 700;
    color: var(--gray);
    margin-bottom: 0.3rem;
  }

  .gpa-badge {
    display: inline-block;
    background: var(--green);
    color: var(--white);
    border: 2px solid var(--black);
    padding: 0.2rem 0.5rem;
    font-size: 0.72rem;
    font-weight: 900;
    box-shadow: 2px 2px 0 var(--black);
    margin-top: 0.3rem;
  }

  .edu-courses {
    font-size: 0.72rem;
    color: var(--gray);
    margin-top: 0.5rem;
    line-height: 1.5;
    font-style: italic;
  }

  /* ── Skill Tags ── */
  .skill-section { margin-bottom: 0.8rem; }
  .skill-section:last-child { margin-bottom: 0; }

  .skill-label {
    font-weight: 900;
    font-size: 0.75rem;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
    display: flex;
    align-items: center;
    gap: 0.3rem;
    color: var(--black);
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }

  .skill-tag {
    background: var(--white);
    border: 2.5px solid var(--black);
    padding: 0.3rem 0.6rem;
    font-size: 0.7rem;
    font-weight: 700;
    text-transform: uppercase;
    box-shadow: 2px 2px 0 var(--black);
    letter-spacing: 0.03em;
  }

  .skill-tag.star {
    background: var(--yellow);
  }

  .skill-tag.hot {
    background: var(--red);
    color: var(--white);
  }

  /* ── Experience ── */
  .exp-item {
    margin-bottom: 1.5rem;
    position: relative;
    padding-left: 1.8rem;
  }

  .exp-item:last-child { margin-bottom: 0; }

  .exp-item::before {
    content: '';
    position: absolute;
    left: 0; top: 8px; bottom: 8px;
    width: 5px;
    background: var(--red);
    border-radius: 3px;
  }

  .exp-item::after {
    content: '★';
    position: absolute;
    left: -5px; top: 0;
    font-size: 0.9rem;
    color: var(--yellow);
    text-shadow: 1px 1px 0 var(--black);
  }

  .exp-co-row {
    display: flex;
    flex-wrap: wrap;
    align-items: baseline;
    gap: 0.5rem;
    margin-bottom: 0.2rem;
  }

  .exp-company {
    font-family: 'ComicTitle', 'Impact', sans-serif;
    font-size: 1.05rem;
    font-weight: 900;
    color: var(--black);
  }

  .exp-role {
    display: inline-block;
    background: var(--purple);
    color: var(--white);
    padding: 0.15rem 0.5rem;
    font-size: 0.7rem;
    font-weight: 900;
    border: 2px solid var(--black);
    box-shadow: 2px 2px 0 var(--black);
  }

  .exp-meta {
    font-size: 0.72rem;
    font-weight: 700;
    color: var(--gray);
    margin-bottom: 0.5rem;
  }

  .exp-desc {
    font-size: 0.78rem;
    line-height: 1.65;
    list-style: none;
  }

  .exp-desc li {
    margin-bottom: 0.4rem;
    position: relative;
    padding-left: 1.1rem;
  }

  .exp-desc li::before {
    content: '▶';
    position: absolute;
    left: 0;
    color: var(--orange);
    font-size: 0.5rem;
    top: 0.3rem;
  }

  .kpi-badge {
    display: inline-block;
    background: var(--yellow);
    color: var(--black);
    padding: 0.05rem 0.4rem;
    font-weight: 900;
    font-size: 0.78rem;
    border: 1.5px solid var(--black);
  }

  /* ── Project Cards ── */
  .project-card {
    background: #F0F7FF;
    border: 3px solid var(--black);
    padding: 1rem;
    margin-bottom: 1rem;
    box-shadow: 4px 4px 0 var(--black);
    position: relative;
  }

  .project-card:last-child { margin-bottom: 0; }

  .project-card::before {
    content: '';
    position: absolute;
    top: -8px; right: -8px;
    width: 28px; height: 28px;
    background: var(--orange);
    border: 3px solid var(--black);
    border-radius: 50%;
    transform: rotate(15deg);
  }

  .proj-title {
    font-family: 'ComicTitle', 'Impact', sans-serif;
    font-size: 1rem;
    font-weight: 900;
    color: var(--black);
    display: flex;
    align-items: center;
    gap: 0.4rem;
    margin-bottom: 0.2rem;
  }

  .proj-role {
    font-size: 0.72rem;
    font-weight: 700;
    color: var(--blue);
    margin-bottom: 0.5rem;
  }

  .proj-desc {
    font-size: 0.76rem;
    line-height: 1.6;
    list-style: none;
  }

  .proj-desc li {
    margin-bottom: 0.3rem;
    padding-left: 1rem;
    position: relative;
  }

  .proj-desc li::before {
    content: '⚡';
    position: absolute;
    left: 0;
    font-size: 0.55rem;
    top: 0.15rem;
  }

  /* ── SOUND EFFECTS ── */
  .sfx {
    font-family: 'ComicTitle', 'Impact', sans-serif;
    font-size: 2rem;
    font-weight: 900;
    color: var(--red);
    text-shadow: 2px 2px 0 var(--black);
    transform: rotate(-8deg);
    position: absolute;
    opacity: 0.7;
    pointer-events: none;
    z-index: 2;
  }

  .sfx.panel-tl { top: -15px; left: 10px; }
  .sfx.panel-br { bottom: -10px; right: 10px; transform: rotate(6deg); color: var(--orange); }

  /* ── CONTACT STRIP ── */
  .contact-strip {
    display: flex;
    flex-wrap: wrap;
    gap: 0.8rem;
    background: var(--black);
    border: 5px solid var(--black);
    padding: 1rem 1.5rem;
    margin-top: 1.5rem;
    justify-content: center;
    box-shadow: 8px 8px 0 var(--yellow);
  }

  .contact-item {
    color: var(--yellow);
    font-weight: 900;
    font-size: 0.85rem;
    display: flex;
    align-items: center;
    gap: 0.4rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .contact-item .icon {
    font-size: 1.1rem;
    filter: none;
  }

  /* ── FOOTER COMIC BOX ── */
  .comic-footer {
    text-align: center;
    margin-top: 2rem;
    font-family: 'ComicTitle', 'Impact', sans-serif;
    font-size: 1.3rem;
    font-weight: 900;
    color: var(--red);
    text-shadow: 2px 2px 0 var(--black);
    letter-spacing: 0.1em;
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    .comic-grid { grid-template-columns: 1fr; }
    .hero-name { font-size: clamp(2.8rem, 12vw, 4rem); }
    .hero-banner { padding: 1.5rem; }
    .panel-header h3 { font-size: 1.1rem; }
    .contact-strip { flex-direction: column; align-items: center; }
  }

  @media print {
    .bg-dots { display: none; }
    .hero-banner, .comic-panel { box-shadow: none; }
    body { background: white; }
  }
</style>
</head>
<body>

<div class="bg-dots"></div>

<div class="page">

  <!-- ════════════ HERO BANNER ════════════ -->
  <div class="hero-banner">
    <div class="hero-starburst">💥</div>
    <div class="hero-speech">📋 RESUME UNLEASHED!</div>
    <div class="hero-name">金璟宇</div>
    <div class="hero-subtitle">Product · Analytics · Supply Chain</div>
    <div class="hero-badges">
      <span class="hero-badge"><span class="icon">🎓</span> 哥伦比亚大学 硕士</span>
      <span class="hero-badge"><span class="icon">💼</span> 德勤咨询</span>
      <span class="hero-badge"><span class="icon">🌐</span> 中 / EN / KO</span>
    </div>
  </div>

  <!-- ════════════ ACTION DIVIDER ════════════ -->
  <div class="action-divider">
    <span class="action-burst">EDUCATION</span>
    <span class="action-burst" style="background:var(--blue);">EXPERIENCE</span>
    <span class="action-burst" style="background:var(--green);">SKILLS</span>
  </div>

  <!-- ════════════ COMIC GRID ════════════ -->
  <div class="comic-grid">

    <!-- PANEL: Education -->
    <div class="comic-panel">
      <div class="panel-header blue">
        <div class="panel-header-icon">🎓</div>
        <h3>教育背景</h3>
      </div>
      <div class="panel-body">
        <div class="edu-item">
          <div class="edu-school">哥伦比亚大学</div>
          <div class="edu-meta">硕士 · 应用分析 · 纽约 &nbsp;|&nbsp; 2023.08 – 2024.12</div>
          <span class="gpa-badge">GPA 3.7 / 4.0</span>
          <div class="edu-courses">研究设计 · 数据叙事与可视化 · 策略与分析 · 应用分析框架 I&II · 数据管理 · 企业组织分析</div>
        </div>
        <div class="edu-item">
          <div class="edu-school">新泽西州立大学</div>
          <div class="edu-meta">本科 · 供应链管理 · 新泽西 &nbsp;|&nbsp; 2019.08 – 2023.05</div>
          <span class="gpa-badge">GPA 3.79 / 4.0</span>
          <div class="edu-courses">🏅 连续四年院长荣誉名单 · 优秀毕业生 · 管理会计 · 市场营销 · 财务管理 · 供应链管理 · 全球采购 · 商业政策与战略</div>
        </div>
      </div>
    </div>

    <!-- PANEL: Skills -->
    <div class="comic-panel">
      <div class="panel-header orange">
        <div class="panel-header-icon">🛠️</div>
        <h3>专业技能</h3>
      </div>
      <div class="panel-body">
        <div class="skill-section">
          <div class="skill-label">💻 技术武器库</div>
          <div class="skill-tags">
            <span class="skill-tag star">Python</span>
            <span class="skill-tag">SQL</span>
            <span class="skill-tag">R</span>
            <span class="skill-tag star">Tableau</span>
            <span class="skill-tag">SAP</span>
            <span class="skill-tag">JavaScript</span>
            <span class="skill-tag">HTML</span>
            <span class="skill-tag">Excel</span>
          </div>
        </div>
        <div class="skill-section">
          <div class="skill-label">🔬 分析必杀技</div>
          <div class="skill-tags">
            <span class="skill-tag hot">ANOVA</span>
            <span class="skill-tag">随机森林</span>
            <span class="skill-tag">聚类分析</span>
            <span class="skill-tag">逻辑回归</span>
            <span class="skill-tag star">NLP</span>
            <span class="skill-tag">数据可视化</span>
            <span class="skill-tag">关联规则</span>
            <span class="skill-tag hot">神经网络</span>
          </div>
        </div>
        <div class="skill-section">
          <div class="skill-label">🎨 创意工坊</div>
          <div class="skill-tags">
            <span class="skill-tag">Photoshop</span>
            <span class="skill-tag">Premiere</span>
            <span class="skill-tag">Procreate</span>
            <span class="skill-tag">PowerPoint</span>
            <span class="skill-tag star">平面设计</span>
            <span class="skill-tag">视频剪辑</span>
          </div>
        </div>
      </div>
    </div>

    <!-- PANEL: Work Experience (FULL WIDTH) -->
    <div class="comic-panel full">
      <div class="panel-header red">
        <div class="panel-header-icon">💼</div>
        <h3>工作 & 实习经历</h3>
      </div>
      <div class="panel-body">

        <div class="exp-item">
          <div class="exp-co-row">
            <span class="exp-company">德勤咨询</span>
            <span class="exp-role">咨询顾问</span>
          </div>
          <div class="exp-meta">📍 北京 · 2025.04 – 现在</div>
          <ul class="exp-desc">
            <li>驻场联想客户，围绕供应链数字化与智能化参与 <span class="kpi-badge">11+</span> 个系统功能设计与业务流程增强项目</li>
            <li>推动供应链可视化平台搭建，生产订单创建时间 <span class="kpi-badge">22天 → 9.5天</span>，发货文件故障率 <span class="kpi-badge">&lt;6%</span></li>
            <li>参与大疆、领充、路特创新等客户前期访谈及需求沟通，制作行业研究与竞品分析文档</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-co-row">
            <span class="exp-company">Ehomie</span>
            <span class="exp-role">房地产分析 & 销售实习生</span>
          </div>
          <div class="exp-meta">📍 纽约 · 2024.05 – 2024.09</div>
          <ul class="exp-desc">
            <li>用 Python + Tableau 做数据分析与可视化，公司营业额同比增长 <span class="kpi-badge">11%</span></li>
            <li>打造小红书专业账号，浏览量 <span class="kpi-badge">5万+</span>，点赞收藏 <span class="kpi-badge">2000+</span></li>
            <li>个人房产申请额 <span class="kpi-badge">$12,000</span>（同部门排名第4）</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-co-row">
            <span class="exp-company">Phalanx Analysis Group</span>
            <span class="exp-role">商业分析实习生</span>
          </div>
          <div class="exp-meta">📍 纽约 · 2022.06 – 2022.08</div>
          <ul class="exp-desc">
            <li>为 AGODA、BUMBLE、Spotify 等公司收集市场及财务数据，用 R 做时间序列与线性回归</li>
            <li>撰写《企业发展战略报告》，输出前瞻性战略建议</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-co-row">
            <span class="exp-company">小米</span>
            <span class="exp-role">市场营销实习生</span>
          </div>
          <div class="exp-meta">📍 北京 · 2021.06 – 2021.08</div>
          <ul class="exp-desc">
            <li>为欧莱雅、沃尔沃、阿里巴巴等定制广告计划，平均用户触达率提高 <span class="kpi-badge">25%</span></li>
            <li>分析爱优腾综艺广告植入，提供小米综艺招商策略；制作 <span class="kpi-badge">6+</span> 个营销链路图，营销效率提升 <span class="kpi-badge">17%+</span></li>
          </ul>
        </div>

      </div>
    </div>

    <!-- PANEL: Projects (FULL WIDTH) -->
    <div class="comic-panel full">
      <div class="panel-header purple">
        <div class="panel-header-icon">🚀</div>
        <h3>项目经历</h3>
      </div>
      <div class="panel-body" style="display:grid; grid-template-columns: 1fr 1fr; gap:1rem;">

        <div class="project-card">
          <div class="proj-title">🥞 煎饼创业项目</div>
          <div class="proj-role">创始人 · 新泽西 · 2023.02 – 2023.05</div>
          <ul class="proj-desc">
            <li>识别校园餐饮空缺，单份成本控制至 <span class="kpi-badge">$1.1</span></li>
            <li>火腿肠采购价降低 <span class="kpi-badge">33%</span>，分层定价策略</li>
            <li>三个月累计收入 <span class="kpi-badge">$1,500</span></li>
          </ul>
        </div>

        <div class="project-card">
          <div class="proj-title">🏭 MAERSK 仓库可持续发展</div>
          <div class="proj-role">供应链管理组员 · 新泽西 · 2022.09 – 2022.12</div>
          <ul class="proj-desc">
            <li>助力 2060 碳中和目标，实地考察 5 个仓库</li>
            <li>采购成本控制在 <span class="kpi-badge">$100K 内</span></li>
            <li>项目演讲获高分评价</li>
          </ul>
        </div>

      </div>
    </div>

  </div>

  <!-- ════════════ CONTACT ════════════ -->
  <div class="contact-strip">
    <span class="contact-item"><span class="icon">📧</span> jingyu2001@aliyun.com</span>
    <span class="contact-item"><span class="icon">📱</span> 18201121438</span>
    <span class="contact-item"><span class="icon">🌍</span> 英语专业 · 韩语初级</span>
    <span class="contact-item"><span class="icon">🎯</span> 产品 × 供应链 × 分析</span>
  </div>

  <div class="comic-footer">💥 JIN JINGYU · RESUME 2025 · TO BE CONTINUED... 💥</div>

</div>

</body>
</html>
