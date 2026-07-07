<!DOCTYPE html>
<html>
<head>
<style>
@keyframes glitch {
  0% { text-shadow: 0.05em 0 0 #00D4FF, -0.05em -0.025em 0 #9D00FF; }
  14% { text-shadow: 0.05em 0 0 #00D4FF, -0.05em -0.025em 0 #9D00FF; }
  15% { text-shadow: -0.05em -0.025em 0 #00D4FF, 0.025em 0.025em 0 #9D00FF; }
  49% { text-shadow: -0.05em -0.025em 0 #00D4FF, 0.025em 0.025em 0 #9D00FF; }
  50% { text-shadow: 0.025em 0.05em 0 #00D4FF, 0.05em 0 0 #9D00FF; }
  99% { text-shadow: 0.025em 0.05em 0 #00D4FF, 0.05em 0 0 #9D00FF; }
  100% { text-shadow: -0.025em 0 0 #00D4FF, -0.025em -0.025em 0 #9D00FF; }
}

@keyframes scanline {
  0% { background-position: 0 0; }
  100% { background-position: 0 100%; }
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

@keyframes flicker {
  0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% { opacity: 1; }
  20%, 24%, 55% { opacity: 0.4; }
}

@keyframes matrixRain {
  0% { transform: translateY(-100%); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateY(100%); opacity: 0; }
}

.cyber-container {
  background: #0A0A0F;
  padding: 20px;
  position: relative;
  overflow: hidden;
}

.cyber-container::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: repeating-linear-gradient(
    0deg,
    rgba(0, 212, 255, 0.03) 0px,
    rgba(0, 212, 255, 0.03) 2px,
    transparent 2px,
    transparent 4px
  );
  pointer-events: none;
  animation: scanline 20s linear infinite;
  z-index: 999;
}

.matrix-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  opacity: 0.05;
  z-index: 0;
  font-family: 'Courier New', monospace;
  color: #00D4FF;
  overflow: hidden;
}

.matrix-column {
  position: absolute;
  animation: matrixRain 10s linear infinite;
  font-size: 14px;
  line-height: 1.2;
}

.cyber-card {
  background: linear-gradient(135deg, rgba(10, 10, 15, 0.95), rgba(20, 20, 30, 0.95));
  border: 1px solid #00D4FF;
  border-radius: 8px;
  padding: 20px;
  margin: 10px 0;
  position: relative;
  backdrop-filter: blur(10px);
  box-shadow: 0 0 30px rgba(0, 212, 255, 0.1), inset 0 0 30px rgba(0, 212, 255, 0.05);
  transition: all 0.3s ease;
  z-index: 1;
}

.cyber-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 0 50px rgba(0, 212, 255, 0.2), inset 0 0 50px rgba(0, 212, 255, 0.1);
}

.cyber-card.purple {
  border-color: #9D00FF;
  box-shadow: 0 0 30px rgba(157, 0, 255, 0.1), inset 0 0 30px rgba(157, 0, 255, 0.05);
}

.cyber-card.purple:hover {
  box-shadow: 0 0 50px rgba(157, 0, 255, 0.2), inset 0 0 50px rgba(157, 0, 255, 0.1);
}

.cyber-title {
  font-family: 'Courier New', monospace;
  font-size: 24px;
  font-weight: bold;
  color: #00D4FF;
  text-shadow: 0 0 20px rgba(0, 212, 255, 0.3);
  position: relative;
  display: inline-block;
}

.cyber-title.glitch {
  animation: glitch 3s infinite;
}

.cyber-title.purple {
  color: #9D00FF;
  text-shadow: 0 0 20px rgba(157, 0, 255, 0.3);
}

.cyber-title::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #00D4FF, transparent);
  animation: pulse 2s infinite;
}

.cyber-title.purple::after {
  background: linear-gradient(90deg, transparent, #9D00FF, transparent);
}

.cyber-text {
  color: #7AC7FF;
  font-family: 'Courier New', monospace;
  line-height: 1.8;
}

.cyber-text.purple {
  color: #D4A0FF;
}

.cyber-badge {
  display: inline-block;
  padding: 4px 12px;
  margin: 2px;
  background: rgba(0, 212, 255, 0.1);
  border: 1px solid #00D4FF;
  border-radius: 3px;
  color: #00D4FF;
  font-family: 'Courier New', monospace;
  font-size: 11px;
  transition: all 0.3s ease;
}

.cyber-badge:hover {
  background: rgba(0, 212, 255, 0.2);
  box-shadow: 0 0 20px rgba(0, 212, 255, 0.2);
}

.cyber-badge.purple {
  border-color: #9D00FF;
  color: #9D00FF;
  background: rgba(157, 0, 255, 0.1);
}

.cyber-badge.purple:hover {
  background: rgba(157, 0, 255, 0.2);
  box-shadow: 0 0 20px rgba(157, 0, 255, 0.2);
}

.cyber-table {
  background: rgba(10, 10, 15, 0.8);
  border-collapse: collapse;
  width: 100%;
  font-family: 'Courier New', monospace;
}

.cyber-table th {
  background: rgba(0, 212, 255, 0.1);
  color: #00D4FF;
  padding: 12px;
  text-align: left;
  border-bottom: 2px solid #00D4FF;
}

.cyber-table td {
  padding: 10px 12px;
  border-bottom: 1px solid rgba(0, 212, 255, 0.1);
  color: #c9d1d9;
}

.cyber-table tr:hover td {
  background: rgba(0, 212, 255, 0.05);
}

.hud-border {
  border-left: 3px solid #00D4FF;
  padding-left: 15px;
  position: relative;
}

.hud-border::before {
  content: '>';
  position: absolute;
  left: -10px;
  color: #00D4FF;
  animation: pulse 1.5s infinite;
}

.hud-border.purple {
  border-left-color: #9D00FF;
}

.hud-border.purple::before {
  color: #9D00FF;
}

.metric-box {
  background: rgba(0, 212, 255, 0.05);
  border: 1px solid rgba(0, 212, 255, 0.2);
  border-radius: 5px;
  padding: 15px;
  margin: 5px;
  transition: all 0.3s ease;
}

.metric-box:hover {
  background: rgba(0, 212, 255, 0.1);
  border-color: #00D4FF;
  box-shadow: 0 0 20px rgba(0, 212, 255, 0.1);
}

.terminal-line {
  font-family: 'Courier New', monospace;
  color: #00D4FF;
  padding: 2px 0;
}

.terminal-line .prompt {
  color: #9D00FF;
}

.terminal-line .cmd {
  color: #00D4FF;
}

.terminal-line .output {
  color: #7AC7FF;
}

.glowing-border {
  position: relative;
}

.glowing-border::before {
  content: '';
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, #00D4FF, #9D00FF, #00D4FF);
  background-size: 400% 400%;
  border-radius: 10px;
  z-index: -1;
  animation: pulse 3s ease-in-out infinite;
  opacity: 0.3;
}

.footer-glow {
  border-top: 2px solid #9D00FF;
  box-shadow: 0 -5px 30px rgba(157, 0, 255, 0.2);
  padding: 20px;
  margin-top: 20px;
  text-align: center;
}

@media (max-width: 768px) {
  .cyber-title { font-size: 18px; }
  .cyber-card { padding: 15px; }
}
</style>
</head>
<body>

<div class="cyber-container">

<!-- Matrix Rain Background -->
<div class="matrix-bg" id="matrixRain"></div>

<!-- Header -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0A0A0F&height=220&section=header&text=%E2%9A%A1%20VIVEK%20R%20NAIR%20%E2%9A%A1&fontSize=45&animation=twinkling&fontColor=00D4FF&desc=%5B%20CYBERPUNK%20ARCHITECT%20%7C%20FULL%20STACK%20DEVELOPER%20%7C%20AI%20ENGINEER%20%5D&descAlignY=65&descAlign=50&descSize=15" width="100%"/>
  
  <div style="margin: 15px 0;">
    <span class="cyber-badge" style="animation: flicker 2s infinite;">⟐ GRID_STATUS: ONLINE</span>
    <span class="cyber-badge purple" style="animation: flicker 2.5s infinite;">⟐ SECTOR: NEO_KERALA</span>
    <span class="cyber-badge" style="animation: flicker 3s infinite;">⟐ ACADEMIC_NODE: MCA @ AMRITA</span>
  </div>

  <!-- Boot Sequence -->
  <div class="cyber-card" style="text-align: left; max-width: 800px; margin: 0 auto;">
    <div class="terminal-line">
      <span class="prompt">[▲]</span> <span class="cmd">BOOT SEQUENCE:</span> <span class="output">vivek.exe...</span>
    </div>
    <div class="terminal-line">
      <span class="prompt">[▲]</span> <span class="cmd">LOADING FULL-STACK INJECTORS...</span> <span class="output">[ SUCCESS ]</span>
    </div>
    <div class="terminal-line">
      <span class="prompt">[▲]</span> <span class="cmd">INITIALIZING NEURAL AI CORES...</span> <span class="output">[ ACTIVE ]</span>
    </div>
    <div class="terminal-line" style="color: #00D4FF;">
      <span class="prompt">[▲]</span> <span class="cmd">UPLINK SECURE.</span> <span class="output">WELCOME TO THE CYBERGRID.</span>
    </div>
  </div>
</div>

<br/>

<!-- Identity Matrix -->
<h2 class="cyber-title glitch">🌐 [// USER_IDENTITY_MATRIX]</h2>
<div class="cyber-card hud-border">
  <div class="cyber-text">
    <b style="color: #9D00FF;">identity:</b><br/>
    &nbsp;&nbsp;alias: <span style="color: #00D4FF;">"MrGhost007"</span><br/>
    &nbsp;&nbsp;subroutines: <span style="color: #00D4FF;">"Full Stack Developer Intern @ Upto Skills"</span><br/>
    &nbsp;&nbsp;neural_network: <span style="color: #00D4FF;">"MCA Node, Amrita Vishwa Vidyapeetham (2025 - Present)"</span><br/>
    &nbsp;&nbsp;core_directives: [<span style="color: #00D4FF;">"Cyberpunk Architecture"</span>, <span style="color: #00D4FF;">"Neural Networks"</span>, <span style="color: #00D4FF;">"Data Synthesizers"</span>]<br/>
    &nbsp;&nbsp;current_operation: <span style="color: #00D4FF;">"Constructing AI-Driven Medical Decision Support System"</span><br/>
    &nbsp;&nbsp;comms_channel:<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;secure_line: <span style="color: #00D4FF;">"vivekrnair22@gmail.com"</span><br/>
    &nbsp;&nbsp;&nbsp;&nbsp;signal_wave: <span style="color: #00D4FF;">"+91 8943558239"</span>
  </div>
</div>

<br/>

<!-- Network Uplinks -->
<h2 class="cyber-title purple glitch">📡 [// NETWORK_UPLINKS]</h2>
<div align="center" style="margin: 10px 0;">
  <a href="https://linkedin.com/in/vivek-r-nair-24544734a" target="_blank">
    <img src="https://img.shields.io/badge/LINKED_IN-0A0A0F?style=for-the-badge&logo=linkedin&logoColor=9D00FF&color=0A0A0F&labelColor=0A0A0F&borderColor=9D00FF"/>
  </a>
  <a href="https://github.com/MrGhost007" target="_blank">
    <img src="https://img.shields.io/badge/GIT_HUB-0A0A0F?style=for-the-badge&logo=github&logoColor=00D4FF&color=0A0A0F&labelColor=0A0A0F&borderColor=00D4FF"/>
  </a>
  <a href="mailto:vivekrnair22@gmail.com">
    <img src="https://img.shields.io/badge/COMMS_NODE-0A0A0F?style=for-the-badge&logo=gmail&logoColor=9D00FF&color=0A0A0F&labelColor=0A0A0F&borderColor=9D00FF"/>
  </a>
</div>

<br/>

<!-- Hardware Arsenal -->
<h2 class="cyber-title">🛠️ [// HARDWARE_ARSENAL]</h2>
<div align="center" class="cyber-card" style="display: flex; flex-wrap: wrap; justify-content: center; gap: 5px;">
  <span class="cyber-badge">Java</span>
  <span class="cyber-badge purple">Python</span>
  <span class="cyber-badge">React</span>
  <span class="cyber-badge purple">Node.js</span>
  <span class="cyber-badge">Express</span>
  <span class="cyber-badge purple">Django</span>
  <span class="cyber-badge">Angular</span>
  <span class="cyber-badge purple">HTML5</span>
  <span class="cyber-badge">CSS3</span>
  <span class="cyber-badge purple">MySQL</span>
  <span class="cyber-badge">Git</span>
  <span class="cyber-badge purple">GitHub</span>
  <span class="cyber-badge">VS Code</span>
</div>

<br/>

<!-- Cognitive Protocols -->
<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
  <div class="cyber-card">
    <h3 style="color: #00D4FF; margin-top: 0;">💾 COGNITIVE PROTOCOLS</h3>
    <ul style="color: #7AC7FF; list-style-type: none; padding: 0;">
      <li style="padding: 5px 0;">▸ Java · Python · Angular · SQL</li>
      <li style="padding: 5px 0;">▸ OOP · SDLC · DSA · DBMS</li>
    </ul>
  </div>
  
  <div class="cyber-card purple">
    <h3 style="color: #9D00FF; margin-top: 0;">⚡ INTERPERSONAL SYNAPSES</h3>
    <ul style="color: #D4A0FF; list-style-type: none; padding: 0;">
      <li style="padding: 5px 0;">▸ Communication</li>
      <li style="padding: 5px 0;">▸ Teamwork</li>
      <li style="padding: 5px 0;">▸ Problem-Solving</li>
    </ul>
  </div>
</div>

<br/>

<!-- Experience -->
<h2 class="cyber-title purple glitch">🏢 [// RUNTIME_LOGS & EXPERIENCE]</h2>
<div class="cyber-card hud-border purple">
  <h3 style="color: #00D4FF; margin: 0;">Full Stack Developer — Upto Skills <span style="font-size: 12px; color: #7AC7FF; float: right;">Jun 2026 – Present</span></h3>
  <p style="color: #c9d1d9; line-height: 1.8;">
    • Engineered adaptive web architectures utilizing CSS, React, Node.js, and Express.js framework injectors.<br/>
    • Formulated high-throughput RESTful data pipelines and fused terminal interfaces with core backend servers.<br/>
    • Deployed distributed version control nodes via Git/GitHub for seamless code deployment.
  </p>
</div>

<br/>

<!-- Projects -->
<h2 class="cyber-title">🚀 [// DEPLOYED_PROJECTS]</h2>
<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
  <div class="cyber-card">
    <h3 style="color: #00D4FF; margin-top: 0;">🩺 AI-Medical Support Care</h3>
    <p style="font-size: 12px; color: #7AC7FF;">Jan 2026 – Present</p>
    <p style="color: #c9d1d9; font-size: 13px; line-height: 1.6;">A real-time predictive matrix analyzing critical biometric symptoms via NLP and multi-variant probabilistic algorithms to isolate anomalies and streamline emergency diagnostic workflows.</p>
    <div style="margin: 10px 0;">
      <span class="cyber-badge purple">React</span>
      <span class="cyber-badge purple">Node.js</span>
      <span class="cyber-badge purple">NLP</span>
      <span class="cyber-badge purple">Python</span>
    </div>
    <p style="color: #c9d1d9; font-size: 13px; margin-bottom: 0;">• Built deterministic backend frameworks to safely handle critical inputs.<br/>• Managed telemetry components for processing asynchronous system outputs.</p>
  </div>
  
  <div class="cyber-card purple">
    <h3 style="color: #9D00FF; margin-top: 0;">🦁 Zoo Visitors & Management</h3>
    <p style="font-size: 12px; color: #D4A0FF;">Nov 2023 – Mar 2024</p>
    <p style="color: #c9d1d9; font-size: 13px; line-height: 1.6;">Enterprise resource routing interface optimizing facility actions—personnel tracking, access authorization, and dynamic diagnostic monitoring telemetry.</p>
    <div style="margin: 10px 0;">
      <span class="cyber-badge">HTML/CSS</span>
      <span class="cyber-badge">Django</span>
    </div>
    <p style="color: #c9d1d9; font-size: 13px; margin-bottom: 0;">• Generated access-token booking configurations.<br/>• Integrated high-level diagnostic analytics dashboards.<br/>• Enabled continuous system visualization streams.</p>
  </div>
</div>

<br/>

<!-- Education -->
<h2 class="cyber-title purple glitch">🎓 [// DATA_ARCHIVE: EDUCATION]</h2>
<table class="cyber-table">
  <thead>
    <tr>
      <th>Node Level</th>
      <th>Institution Hub</th>
      <th>Data Window</th>
      <th>Processing Metric</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Master of Computer Applications</b></td>
      <td>Amrita Vishwa Vidyapeetham</td>
      <td>Jul 2025 – Present</td>
      <td style="color: #00D4FF;"><code>SYSTEM_ACTIVE</code></td>
    </tr>
    <tr>
      <td>Bachelor of Computer Applications</td>
      <td>Paramekkavu College of Arts & Science</td>
      <td>Sep 2021 – May 2024</td>
      <td><b>CGPA 8.09</b></td>
    </tr>
    <tr>
      <td>Higher Secondary Node</td>
      <td>Kendriya Vidyalaya Thrissur</td>
      <td>Jun 2019 – May 2021</td>
      <td><b>CGPA 8.48</b></td>
    </tr>
    <tr>
      <td>Secondary Node</td>
      <td>Kendriya Vidyalaya Thrissur</td>
      <td>Apr 2018 – Mar 2019</td>
      <td><b>CGPA 8.92</b></td>
    </tr>
  </tbody>
</table>

<br/>

<!-- Certificates -->
<h2 class="cyber-title">🏅 [// ACCREDITED_CERTIFICATES]</h2>
<div align="center" style="display: flex; flex-wrap: wrap; justify-content: center; gap: 8px;">
  <span class="cyber-badge">IIT Guwahati - Data Analytics & GenAI</span>
  <span class="cyber-badge purple">IBM - Data Analysis with Python</span>
  <span class="cyber-badge">Let's Upgrade - Data Science with Python</span>
  <span class="cyber-badge purple">Infosys - Computational Problem Solving</span>
</div>

<br/>

<!-- Achievements -->
<h2 class="cyber-title purple glitch">🏆 [// NETRUNS & SECTOR_WINS]</h2>
<div class="cyber-card" style="font-family: 'Courier New', monospace; line-height: 2;">
  • 🤖 <span style="color: #00D4FF;"><b>AI Without Code Interface</b></span> — Mastered zero-code structural AI logic <span style="color: #9D00FF;">[Feb 2026]</span><br/>
  • 🎮 <span style="color: #00D4FF;"><b>DEVMODE:ON Matrix</b></span> — Real-time rendering architecture in Unreal Engine <span style="color: #9D00FF;">[Jan 2026]</span><br/>
  • 🏆 Processed <span style="color: #7AC7FF;">Deloitte Corporate Simulation Suite</span><br/>
  • 🏆 Successfully executed <span style="color: #7AC7FF;">McKinsey Forward Protocols</span>
</div>

<br/>

<!-- Metrics -->
<h2 class="cyber-title">📊 [// CORE_METRICS]</h2>
<div align="center">
  <div style="display: inline-block; margin: 5px;">
    <img src="https://github-readme-stats.vercel.app/api?username=MrGhost007&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0A0A0F&title_color=00D4FF&icon_color=9D00FF&text_color=c9d1d9" height="165"/>
  </div>
  <div style="display: inline-block; margin: 5px;">
    <img src="https://streak-stats.demolab.com?user=MrGhost007&theme=tokyonight&hide_border=true&background=0A0A0F&ring=00D4FF&fire=9D00FF&currStreakLabel=00D4FF" height="165"/>
  </div>
  <br/>
  <div style="display: inline-block; margin: 5px;">
    <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=MrGhost007&layout=compact&theme=tokyonight&hide_border=true&bg_color=0A0A0F&title_color=00D4FF&text_color=c9d1d9" height="165"/>
  </div>
</div>

<br/>

<!-- Footer -->
<div class="footer-glow">
  <p style="color: #ffffff; margin-bottom: 10px;">
    <b>🌍 Dialects:</b> Malayalam · Hindi · English &nbsp;|&nbsp; <b>🎯 Capture Vectors:</b> Photography · Music Audio-Feeds
  </p>
  <img src="https://komarev.com/ghpvc/?username=MrGhost007&color=9D00FF&style=for-the-badge&label=LOGGED+VISITORS"/>
  <p style="color: #00D4FF; font-family: 'Courier New', monospace; margin-top: 15px; font-size: 14px; text-shadow: 0 0 20px rgba(0, 212, 255, 0.3);">
    <b>Uplink completed. Let's rewrite the matrix together.</b>
  </p>
</div>

</div>

<script>
// Matrix Rain Effect
function createMatrixRain() {
  const container = document.getElementById('matrixRain');
  const columns = Math.floor(window.innerWidth / 20);
  
  for (let i = 0; i < columns; i++) {
    const column = document.createElement('div');
    column.className = 'matrix-column';
    column.style.left = (i * 20) + 'px';
    column.style.animationDelay = (Math.random() * 10) + 's';
    column.style.animationDuration = (8 + Math.random() * 4) + 's';
    
    let chars = '';
    for (let j = 0; j < 20; j++) {
      const char = String.fromCharCode(0x30A0 + Math.random() * 96);
      chars += char + '<br>';
    }
    column.innerHTML = chars;
    container.appendChild(column);
  }
}

createMatrixRain();

// Glitch effect on hover for cards
document.querySelectorAll('.cyber-card').forEach(card => {
  card.addEventListener('mouseenter', function() {
    this.style.transform = 'translateX(2px)';
    setTimeout(() => {
      this.style.transform = 'translateX(-2px)';
    }, 50);
    setTimeout(() => {
      this.style.transform = 'translateX(0)';
    }, 100);
  });
});
</script>

</body>
</html>
