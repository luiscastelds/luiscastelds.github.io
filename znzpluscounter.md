---
title: Orders in (Z/nZ,+)
layout: page
permalink: /znzpluscounter/
---

<label for="nInput"><strong>n</strong> (size of (ℤ/nℤ, +))</label>
<input id="nInput" type="number" min="1" step="1" placeholder="Enter a positive integer and press Enter" />
<pre id="out" style="white-space:pre-wrap;line-height:1.4;margin-top:1rem"></pre>

<script>
  function gcd(a, b) {
    a = Math.abs(a); b = Math.abs(b);
    while (b !== 0) { const t = b; b = a % b; a = t; }
    return a;
  }
  function computeOrders(n) {
    // sets[d] = elements whose additive order is d
    const sets = Array.from({ length: n + 1 }, () => []);
    sets[1].push(0); // 0 has order 1 in (ℤ/nℤ, +)
    for (let i = 1; i < n; i++) {
      const ord = n / gcd(i, n);   // order(i) = n / gcd(i,n)
      sets[ord].push(i);
    }
    return sets;
  }
  function render(sets) {
    let lines = [];
    let count = 0;
    for (let ord = 1; ord < sets.length; ord++) {
      if (sets[ord].length) {
        count++;
        lines.push(`order ${ord}: [${sets[ord].join(", ")}]`);
      }
    }
    lines.push(`\nNumber of distinct orders (divisors of n): ${count}`);
    return lines.join("\n");
  }
  const nInput = document.getElementById("nInput");
  const out = document.getElementById("out");

  nInput.addEventListener("keydown", (e) => {
    if (e.key !== "Enter") return;
    const n = parseInt(nInput.value, 10);
    if (!Number.isInteger(n) || n < 1) {
      out.textContent = "Please enter a positive integer n ≥ 1.";
      return;
    }
    const sets = computeOrders(n);
    out.textContent = render(sets);
  });
</script>
