<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Premier 848 - Interactive GitHub Resume</title>

<!-- Google Font Neon -->
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&display=swap" rel="stylesheet">

<!-- Chart.js -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<!-- Particles.js for background animation -->
<script src="https://cdn.jsdelivr.net/npm/tsparticles@2.11.1/tsparticles.min.js"></script>

<style>
  body {
    margin: 0;
    font-family: 'Orbitron', sans-serif;
    background: radial-gradient(circle at top, #0f0c29, #302b63, #24243e);
    color: #00ffea;
    overflow-x: hidden;
  }

  #tsparticles {
    position: fixed;
    width: 100%;
    height: 100%;
    z-index: -1;
  }

  .container {
    max-width: 1000px;
    margin: 50px auto;
    padding: 20px;
    background: rgba(0,0,0,0.6);
    border-radius: 20px;
    box-shadow: 0 0 30px #00ffe1;
    animation: glow 2s infinite alternate;
  }

  @keyframes glow {
    from { box-shadow: 0 0 30px #00ffe1; }
    to { box-shadow: 0 0 60px #00ffe1; }
  }

  h1, h2, h3 {
    text-align: center;
    text-shadow: 0 0 10px #00ffe1, 0 0 20px #00ffe1, 0 0 30px #00ffe1;
  }

  .glow-text {
    color: #00ffe1;
    font-size: 1.2rem;
    text-align: center;
    text-shadow: 0 0 5px #00ffe1, 0 0 10px #00ffe1, 0 0 20px #00ffe1;
    animation: pulse 2s infinite alternate;
  }

  @keyframes pulse {
    from { text-shadow: 0 0 5px #00ffe1, 0 0 10px #00ffe1, 0 0 20px #00ffe1; }
    to { text-shadow: 0 0 10px #00ffe1, 0 0 20px #00ffe1, 0 0 40px #00ffe1; }
  }

  canvas {
    background: rgba(0,0,0,0.4);
    border-radius: 15px;
    box-shadow: 0 0 20px #00ffe1;
    margin: 20px 0;
  }
</style>
</head>
<body>

<div id="tsparticles"></div>

<div class="container">
  <h1>👋 Hi, I'm Premier 848</h1>
  <h2>Aspiring Python Developer | Beginner Level 🐍</h2>
  <p class="glow-text">Passionate about Python, open-source contributions, and interactive projects.</p>

  <h2>📊 GitHub Contributions</h2>
  <canvas id="contributionsChart" height="250"></canvas>

  <h2>📈 Language Usage</h2>
  <canvas id="languageChart" height="250"></canvas>

  <h2>🛠 Repositories</h2>
  <canvas id="reposChart" height="250"></canvas>
</div>

<script>
  // Particles.js background
  tsParticles.load("tsparticles", {
    fpsLimit: 60,
    particles: {
      number: { value: 80 },
      color: { value: "#00ffe1" },
      shape: { type: "circle" },
      opacity: { value: 0.5 },
      size: { value: { min: 1, max: 3 } },
      move: { enable: true, speed: 1, direction: "none", outModes: "out" }
    },
    interactivity: {
      events: { onHover: { enable: true, mode: "repulse" }, onClick: { enable: true, mode: "push" } },
      modes: { repulse: { distance: 100 }, push: { quantity: 4 } }
    },
    detectRetina: true
  });

  // Contributions chart
  const ctx1 = document.getElementById('contributionsChart').getContext('2d');
  const contributionsChart = new Chart(ctx1, {
    type: 'line',
    data: {
      labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
      datasets: [{
        label: 'Contributions',
        data: [120, 140, 130, 160, 180, 200, 190, 210, 180, 170, 160, 180],
        borderColor: '#00ffe1',
        backgroundColor: 'rgba(0,255,225,0.2)',
        tension: 0.4,
        fill: true,
        pointHoverRadius: 10,
        pointHoverBackgroundColor: '#ff00f7'
      }]
    },
    options: {
      responsive: true,
      plugins: { legend: { labels: { color: '#00ffe1' } } },
      scales: {
        x: { ticks: { color: '#00ffe1' }, grid: { color: '#00ffe133' } },
        y: { ticks: { color: '#00ffe1' }, grid: { color: '#00ffe1' } }
      }
    }
  });

  // Language usage chart
  const ctx2 = document.getElementById('languageChart').getContext('2d');
  const languageChart = new Chart(ctx2, {
    type: 'doughnut',
    data: {
      labels: ['Python', 'HTML', 'CSS', 'JavaScript', 'Others'],
      datasets: [{
        label: 'Languages',
        data: [70, 10, 5, 10, 5],
        backgroundColor: ['#00ffe1', '#ff00f7', '#00ff3c', '#ffec00', '#ff4f00'],
        hoverOffset: 15
      }]
    },
    options: {
      responsive: true,
      plugins: { legend: { labels: { color: '#00ffe1' } } }
    }
  });

  // Repositories chart
  const ctx3 = document.getElementById('reposChart').getContext('2d');
  const reposChart = new Chart(ctx3, {
    type: 'bar',
    data: {
      labels: ['Repo A', 'Repo B', 'Repo C', 'Repo D', 'Repo E'],
      datasets: [{
        label: 'Stars',
        data: [25, 40, 15, 30, 20],
        backgroundColor: '#00ffe1',
        borderRadius: 10,
        hoverBackgroundColor: '#ff00f7'
      }]
    },
    options: {
      responsive: true,
      plugins: { legend: { labels: { color: '#00ffe1' } } },
      scales: {
        x: { ticks: { color: '#00ffe1' }, grid: { color: '#00ffe133' } },
        y: { ticks: { color: '#00ffe1' }, grid: { color: '#00ffe133' } }
      }
    }
  });
</script>

</body>
</html>
