<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Luis Castellanos — Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
  <style>
    body { margin:0; font-family:Inter, sans-serif; background:#0f172a; color:#e5e7eb; }
    a { color:#3b82f6; text-decoration:none; }
    a:hover { text-decoration:underline; }
    .container { max-width:1100px; margin:0 auto; padding:32px 20px 64px; }
    header { display:grid; gap:10px; align-items:center; grid-template-columns:80px 1fr; }
    .avatar { width:80px; height:80px; border-radius:50%; background:linear-gradient(135deg,#3b82f6,#22c55e); display:grid; place-items:center; color:white; font-weight:800; }
    .title h1 { margin:0; font-size:28px; }
    .title p { margin:4px 0 0; color:#94a3b8; }
    .badges { display:flex; gap:10px; margin-top:10px; }
    .badge { padding:8px 12px; background:#111827; border-radius:999px; }
    .grid { display:grid; gap:18px; margin-top:28px; }
    @media(min-width:900px){ .grid { grid-template-columns:1fr 1fr; } }
    .card { background:#111827; border-radius:18px; padding:18px; }
    h2 { margin:0 0 8px; font-size:20px; }
    .sub { color:#94a3b8; margin:0 0 14px; }
    footer { margin-top:28px; color:#94a3b8; font-size:14px; text-align:center; }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="avatar">LC</div>
      <div class="title">
        <h1>Luis Castellanos — Data Science & Mathematics</h1>
        <p>Turning data into insight with math, code, and curiosity.</p>
        <div class="badges">
          <a class="badge" href="/assets/CV.pdf">📄 CV</a>
          <a class="badge" href="https://github.com/luiscastelds" target="_blank">🐙 GitHub</a>
          <a class="badge" href="/notes/">📝 Notes</a>
        </div>
      </div>
    </header>

    <!-- Degree Progress -->
    <div class="card" style="margin-top:24px;">
      <h2>Degree Progress</h2>
      <div style="display:flex; gap:20px; flex-wrap:wrap; align-items:center;">
        <div>
          <canvas id="degreeChart" width="220" height="220"></canvas>
          <div id="centerLabel" style="text-align:center; font-weight:800; font-size:24px; margin-top:-140px;"></div>
        </div>
        <div>
          <div id="courseProgress"></div>
          <p id="creditSummary" style="color:#94a3b8; font-size:14px;"></p>
        </div>
      </div>
    </div>

    <!-- Skills Radar -->
    <div class="card" style="margin-top:24px;">
      <h2>Skills Snapshot</h2>
      <p class="sub">A quick visual overview of my math and data science skills.</p>
      <canvas id="skillsRadar" width="800" height="500"></canvas>
    </div>

    <!-- Projects -->
    <div class="card" style="margin-top:24px;">
      <h2>Featured Projects</h2>
      <ul>
        <li><strong>Carcassonne Markov Chain</strong> — Modeling tile draws and game progression with probability.</li>
        <li><strong>Hot Hand in Soccer</strong> — Markov chains applied to streaks and scoring momentum.</li>
        <li><strong>Recipe Virality Predictor</strong> — ML project analyzing why recipes go viral.</li>
        <li><strong>Display Tech Analysis</strong> — CRT vs OLED vs IPS, data-driven comparison.</li>
      </ul>
    </div>

    <!-- About + Q&A -->
    <div class="card" style="margin-top:24px;">
      <h2>About Me</h2>
      <p>
        Born and raised in <strong>El Salvador</strong>, I'm currently a <strong>Purdue University student</strong> with a passion for <strong>mathematics, data science, and technology</strong>.
        My focus is on developing models that explore the complexities of statistics and uncover patterns behind numbers.
      </p>
      <h3>Favorite Q&A</h3>
      <p><strong>Q: Favorite programming language?</strong><br>A: Python — flexible, intuitive, and powerful for data science.</p>
      <p><strong>Q: Favorite math concept?</strong><br>A: Orthogonal diagonalization — clean geometry, efficient computation, and useful in PCA.</p>
      <p><strong>Q: Favorite project?</strong><br>A: Modeling Carcassonne with a Markov chain — capturing the probabilistic structure of tile draws and game progression.</p>
      <p><strong>Q: Favorite way to relax?</strong><br>A: Classical guitar — my favorite composer is Bach.</p>
      <p><strong>Q: Favorite problem to solve?</strong><br>A: Anything that mixes statistics with real-world uncertainty — finding structure in randomness.</p>
      <p><strong>Q: Coffee or tea?</strong><br>A: Tea, always.</p>
      <p><strong>Q: Favorite game?</strong><br>A: The Legend of Zelda: The Wind Waker.</p>
      <p><strong>Q: Favorite food?</strong><br>A: Medium rare steak — ribeye if possible!</p>
      <p><strong>Q: What area of data science excites you the most?</strong><br>A: Applying linear algebra and probability to uncover structure in data — especially PCA and clustering.</p>
    </div>

    <footer>
      © <span id="year"></span> Luis Castellanos. Built with GitHub Pages.
    </footer>
  </div>

  <script>
    // ===== DEGREE DONUT =====
    const totalCredits = 120, completedCredits = 78;
    const ctx1 = document.getElementById("degreeChart").getContext("2d");
    new Chart(ctx1, {
      type: "doughnut",
      data: { labels: ["Completed","Remaining"], datasets:[{ data:[completedCredits, totalCredits-completedCredits], backgroundColor:["#22c55e","#1e293b"], borderWidth:0 }]},
      options:{ cutout:"68%", plugins:{ legend:{ display:false }}}
    });
    document.getElementById("centerLabel").textContent = Math.round((completedCredits/totalCredits)*100)+"%";
    document.getElementById("creditSummary").textContent = `${completedCredits}/${totalCredits} credits completed`;

    // ===== SKILLS RADAR =====
    const axes = ["Linear Algebra","Probability/Stats","Optimization","Machine Learning","Data Visualization","Python/NumPy/pandas","PyTorch","SQL","LaTeX","Linux/Git"];
    const scores = [9,8,7,8,7,9,7,6,8,7];
    const ctx2 = document.getElementById("skillsRadar").getContext("2d");
    new Chart(ctx2,{
      type:"radar",
      data:{ labels:axes, datasets:[{ label:"Current", data:scores, backgroundColor:"rgba(59,130,246,0.2)", borderColor:"rgba(59,130,246,0.9)", borderWidth:2 }]},
      options:{ scales:{ r:{ beginAtZero:true, suggestedMax:10 }}, plugins:{ legend:{ display:false }}}
    });

    // Footer year
    document.getElementById("year").textContent = new Date().getFullYear();
  </script>
</body>
</html>
