---
title: Skills
layout: page
permalink: /skills/
---

# Skills Radar

This chart gives a quick snapshot of my strengths across math, data science, and tools.

<div style="max-width:800px;margin:20px auto;">
  <canvas id="skillsRadar" width="800" height="500" aria-label="Skills radar chart" role="img"></canvas>
</div>

<!-- Chart.js (CDN) -->
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>

<script>
  // ====== EDIT THESE VALUES TO TUNE YOUR RADAR ======
  const axes = [
    "Linear Algebra",
    "Probability/Stats",
    "Optimization",
    "Machine Learning",
    "Data Visualization",
    "Python / NumPy / pandas",
    "PyTorch / ML Tooling",
    "SQL",
    "LaTeX",
    "Linux / Git"
  ];

  // 0–10 scale for each axis (same order as above)
  const scores = [9, 8, 7, 8, 7, 9, 7, 6, 8, 7];

  // Optional: a second dataset (e.g., “in progress”)
  const learningTargets = [10, 9, 9, 9, 8, 10, 9, 8, 9, 8];
  // ====== END EDITS ======

  const ctx = document.getElementById("skillsRadar").getContext("2d");
  new Chart(ctx, {
    type: "radar",
    data: {
      labels: axes,
      datasets: [
        {
          label: "Current",
          data: scores,
          pointRadius: 2,
          borderWidth: 2,
          // Colors intentionally not hard-coded (theme default)
          // but Chart.js needs *some* color; we set modest alpha:
          borderColor: "rgba(59, 130, 246, 0.9)",   // blue-ish
          backgroundColor: "rgba(59, 130, 246, 0.2)"
        },
        {
          label: "Target",
          data: learningTargets,
          pointRadius: 2,
          borderWidth: 2,
          borderColor: "rgba(34, 197, 94, 0.9)",    // green-ish
          backgroundColor: "rgba(34, 197, 94, 0.2)"
        }
      ]
    },
    options: {
      responsive: true,
      scales: {
        r: {
          beginAtZero: true,
          suggestedMin: 0,
          suggestedMax: 10,
          ticks: { stepSize: 2, showLabelBackdrop: false },
          grid: { circular: true }
        }
      },
      plugins: {
        legend: { position: "top" },
        tooltip: { enabled: true }
      },
      elements: {
        line: { tension: 0.25 }
      }
    }
  });
</script>

> Tip: Update the arrays above to reflect your skills. Keep values between **0 and 10**.
