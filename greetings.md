---
title: Greetings
layout: page
permalink: /greetings/
---



<pre id="greetings-banner" style="font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, 'Liberation Mono', 'Courier New', monospace; line-height: 1.05; white-space: pre; margin: 0;">
</pre>

<script>
(() => {
  const banner = String.raw`
  _____                _   _                 
 / ____|              | | (_)                
| |  __ _ __ ___  ___ | |_ _ _ __   __ _ ___ 
| | |_ | '__/ _ \/ _ \| __| | '_ \ / _\` / __|
| |__| | | |  __/  __/| |_| | | | | (_| \__ \
 \_____|_|  \___|\___| \__|_|_| |_|\__, |___/
                                    __/ |    
                                   |___/     

  _____ _                           _           
 / ____| |                         | |          
| (___ | |_ _ __ _   _  __ _  __ _ | | ___  _ __
 \___ \| __| '__| | | |/ _\`|/ _\`|| |/ _ \| '__/
 ____) | |_| |  | |_| | (_| | (_| || |  __/| |
|_____/ \__|_|   \__,_|\__, |\__, ||_|\___||_|
                        __/ | __/ |                       
                       |___/ |___/                        
`;
  const el = document.getElementById("greetings-banner");
  if (el) el.textContent = banner.trimEnd() + "\n";
})();
</script>
