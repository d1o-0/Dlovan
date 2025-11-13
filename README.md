<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Aizen background</title>
  <style>
    /* Replace GIF_URL_HERE with the direct URL to your Aizen Sosuke GIF */
    :root{--overlay-rgba: 0,0,0;--accent: 200,100,255}
    html,body{height:100%;margin:0}
    body{
      min-height:100vh;
      background: black;
      font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      overflow:hidden;
      display:block;
    }

    /* full-bleed animated GIF background */
    .bg{
      position:fixed;inset:0;z-index:0;
      background-image: url('GIF_URL_HERE');
      background-size: cover;
      background-position: center center;
      background-repeat: no-repeat;
      filter: saturate(1.05) contrast(1.02) blur(0.2px);
      transform: translateZ(0);
    }

    /* subtle animated color wash to make the page "kinda cool" without text */
    .wash{
      position:fixed;inset:0;z-index:1;pointer-events:none;
      background: linear-gradient(120deg, rgba(var(--accent),0.06) 0%, rgba(0,0,0,0.04) 30%, rgba(0,0,0,0.18) 100%);
      mix-blend-mode: overlay;
      animation: washMove 12s ease-in-out infinite;
      opacity:0.95;
    }

    @keyframes washMove{
      0%{transform:translateY(-4%)}
      50%{transform:translateY(4%)}
      100%{transform:translateY(-4%)}
    }

    /* vignette + soft flicker for life */
    .vignette{
      position:fixed;inset:0;z-index:2;pointer-events:none;
      background: radial-gradient(ellipse at center, rgba(0,0,0,0) 40%, rgba(0,0,0,0.25) 75%, rgba(0,0,0,0.6) 100%);
      mix-blend-mode: multiply;
      opacity:1;
      animation: pulse 8s ease-in-out infinite;
    }
    @keyframes pulse{
      0%{opacity:0.95}
      50%{opacity:1}
      100%{opacity:0.95}
    }

    /* fine grain noise overlay (CSS-only) */
    .noise{
      position:fixed;inset:0;z-index:3;pointer-events:none;
      background-image: linear-gradient(transparent 50%, rgba(var(--overlay-rgba),0.02) 50%), linear-gradient(90deg, transparent 50%, rgba(var(--overlay-rgba),0.02) 50%);
      background-size: 3px 3px, 3px 3px;
      opacity:0.25;
      mix-blend-mode: overlay;
    }

    /* accessibility: respect reduced motion */
    @media (prefers-reduced-motion: reduce){
      .wash{animation:none}
      .vignette{animation:none}
    }

    /* ensure nothing selectable and no scrollbars */
    *{user-select:none}

  </style>
</head>
<body>
  <div class="bg" aria-hidden="true"></div>
  <div class="wash" aria-hidden="true"></div>
  <div class="vignette" aria-hidden="true"></div>
  <div class="noise" aria-hidden="true"></div>
</body>
</html>

