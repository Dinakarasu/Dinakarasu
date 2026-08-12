<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dinakarasu S — Full-Stack Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#060818;
    --bg-2:#0a0e27;
    --cyan:#22d3ee;
    --violet:#a78bfa;
    --pink:#f472b6;
    --text:#e2e8f0;
    --text-dim:#8b93b0;
    --card:#0e1330;
    --border:rgba(167,139,250,0.15);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--text);
    font-family:'Inter',sans-serif;
    overflow-x:hidden;
  }
  #bg-canvas{
    position:fixed;
    top:0;left:0;
    width:100%;height:100%;
    z-index:0;
  }
  .content{position:relative;z-index:1;}

  /* ---- Hero ---- */
  .hero{
    min-height:100vh;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    text-align:center;
    padding:2rem;
  }
  .eyebrow{
    font-family:'JetBrains Mono',monospace;
    font-size:0.8rem;
    letter-spacing:0.15em;
    color:var(--cyan);
    text-transform:uppercase;
    margin-bottom:1.25rem;
    opacity:0;
    animation:fadeUp 0.8s ease forwards 0.1s;
  }
  h1{
    font-family:'Space Grotesk',sans-serif;
    font-weight:700;
    font-size:clamp(2.5rem,8vw,5.5rem);
    line-height:1.05;
    background:linear-gradient(135deg,#ffffff 30%,var(--cyan) 70%,var(--violet) 100%);
    -webkit-background-clip:text;
    background-clip:text;
    color:transparent;
    opacity:0;
    animation:fadeUp 0.8s ease forwards 0.25s;
  }
  .tagline{
    font-family:'JetBrains Mono',monospace;
    font-size:clamp(0.95rem,2vw,1.15rem);
    color:var(--text-dim);
    margin-top:1.5rem;
    height:1.5em;
    opacity:0;
    animation:fadeUp 0.8s ease forwards 0.4s;
  }
  .tagline .cursor{
    display:inline-block;
    width:2px;
    background:var(--cyan);
    margin-left:2px;
    animation:blink 0.9s step-end infinite;
  }
  .cta-row{
    display:flex;
    gap:1rem;
    margin-top:2.5rem;
    flex-wrap:wrap;
    justify-content:center;
    opacity:0;
    animation:fadeUp 0.8s ease forwards 0.55s;
  }
  .btn{
    font-family:'Space Grotesk',sans-serif;
    font-weight:600;
    font-size:0.95rem;
    padding:0.85rem 1.75rem;
    border-radius:999px;
    text-decoration:none;
    transition:transform 0.2s ease, box-shadow 0.2s ease;
    display:inline-flex;
    align-items:center;
    gap:0.5rem;
  }
  .btn-primary{
    background:linear-gradient(135deg,var(--cyan),var(--violet));
    color:#060818;
  }
  .btn-outline{
    border:1px solid var(--border);
    color:var(--text);
    background:rgba(255,255,255,0.02);
  }
  .btn:hover{transform:translateY(-2px);box-shadow:0 8px 24px rgba(34,211,238,0.25);}

  .scroll-hint{
    position:absolute;
    bottom:2.5rem;
    font-family:'JetBrains Mono',monospace;
    font-size:0.75rem;
    color:var(--text-dim);
    letter-spacing:0.1em;
    opacity:0;
    animation:fadeUp 0.8s ease forwards 0.75s, bob 2.4s ease-in-out infinite 1.5s;
  }

  @keyframes fadeUp{
    from{opacity:0;transform:translateY(16px);}
    to{opacity:1;transform:translateY(0);}
  }
  @keyframes blink{50%{opacity:0;}}
  @keyframes bob{
    0%,100%{transform:translateY(0);}
    50%{transform:translateY(6px);}
  }

  /* ---- Sections ---- */
  section{
    max-width:920px;
    margin:0 auto;
    padding:7rem 2rem;
  }
  .section-label{
    font-family:'JetBrains Mono',monospace;
    font-size:0.75rem;
    letter-spacing:0.15em;
    text-transform:uppercase;
    color:var(--violet);
    margin-bottom:0.75rem;
  }
  h2{
    font-family:'Space Grotesk',sans-serif;
    font-size:clamp(1.8rem,4vw,2.6rem);
    font-weight:600;
    margin-bottom:2.5rem;
  }

  .stack-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(140px,1fr));
    gap:1rem;
  }
  .stack-chip{
    font-family:'JetBrains Mono',monospace;
    font-size:0.9rem;
    padding:1rem 1.2rem;
    background:var(--card);
    border:1px solid var(--border);
    border-radius:12px;
    text-align:center;
    transition:border-color 0.2s ease, transform 0.2s ease;
  }
  .stack-chip:hover{border-color:var(--cyan);transform:translateY(-3px);}
  .stack-chip.learning{
    border-style:dashed;
    color:var(--text-dim);
  }

  .project-card{
    background:var(--card);
    border:1px solid var(--border);
    border-radius:16px;
    padding:2.25rem;
  }
  .project-card h3{
    font-family:'Space Grotesk',sans-serif;
    font-size:1.4rem;
    margin-bottom:0.5rem;
  }
  .project-meta{
    font-family:'JetBrains Mono',monospace;
    font-size:0.8rem;
    color:var(--cyan);
    margin-bottom:1.25rem;
  }
  .project-card ul{
    list-style:none;
    display:grid;
    gap:0.6rem;
  }
  .project-card li{
    color:var(--text-dim);
    font-size:0.95rem;
    padding-left:1.4rem;
    position:relative;
  }
  .project-card li::before{
    content:"▹";
    position:absolute;
    left:0;
    color:var(--violet);
  }
  .project-link{
    display:inline-block;
    margin-top:1.75rem;
    font-family:'JetBrains Mono',monospace;
    font-size:0.85rem;
    color:var(--cyan);
    text-decoration:none;
    border-bottom:1px solid transparent;
  }
  .project-link:hover{border-bottom-color:var(--cyan);}

  footer{
    text-align:center;
    padding:5rem 2rem 4rem;
  }
  footer .section-label{text-align:center;}
  .contact-links{
    display:flex;
    gap:1.5rem;
    justify-content:center;
    margin-top:1.5rem;
  }
  .contact-links a{
    color:var(--text-dim);
    text-decoration:none;
    font-family:'JetBrains Mono',monospace;
    font-size:0.9rem;
    transition:color 0.2s ease;
  }
  .contact-links a:hover{color:var(--cyan);}

  @media (prefers-reduced-motion:reduce){
    *{animation:none !important;}
  }
</style>
</head>
<body>

<canvas id="bg-canvas"></canvas>

<div class="content">

  <section class="hero">
    <div class="eyebrow">// full-stack engineer</div>
    <h1>Dinakarasu S</h1>
    <div class="tagline" id="typed-tagline"><span id="typed-text"></span><span class="cursor">&nbsp;</span></div>
    <div class="cta-row">
      <a class="btn btn-primary" href="https://github.com/Dinakarasu" target="_blank" rel="noopener">View GitHub</a>
      <a class="btn btn-outline" href="https://www.linkedin.com/in/dinakarasu-s" target="_blank" rel="noopener">Connect on LinkedIn</a>
    </div>
    <div class="scroll-hint">scroll ↓</div>
  </section>

  <section id="stack">
    <div class="section-label">01 / the stack</div>
    <h2>Tools I build with</h2>
    <div class="stack-grid">
      <div class="stack-chip">Java</div>
      <div class="stack-chip">JSP</div>
      <div class="stack-chip">Servlets</div>
      <div class="stack-chip">MySQL</div>
      <div class="stack-chip">JavaScript</div>
      <div class="stack-chip">HTML / CSS</div>
      <div class="stack-chip learning">Spring Boot →</div>
      <div class="stack-chip learning">React →</div>
    </div>
  </section>

  <section id="work">
    <div class="section-label">02 / featured build</div>
    <h2>Featured Project</h2>
    <div class="project-card">
      <h3>E-Commerce Website</h3>
      <div class="project-meta">Java · JSP · Servlets · MySQL</div>
      <ul>
        <li>User registration, login, and session handling</li>
        <li>Shopping cart and checkout flow</li>
        <li>Product catalog and management</li>
        <li>Admin dashboard for inventory and orders</li>
      </ul>
      <a class="project-link" href="https://github.com/Dinakarasu/E_commerce_website2" target="_blank" rel="noopener">View source →</a>
    </div>
  </section>

  <footer>
    <div class="section-label">03 / say hello</div>
    <h2>Let's build something</h2>
    <div class="contact-links">
      <a href="https://github.com/Dinakarasu" target="_blank" rel="noopener">GitHub</a>
      <a href="https://www.linkedin.com/in/dinakarasu-s" target="_blank" rel="noopener">LinkedIn</a>
    </div>
  </footer>

</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
  // ---------- Typing tagline ----------
  const lines = [
    "engineering scalable digital experiences",
    "java · jsp · servlets · mysql",
    "next up: spring boot & react",
    "based in chennai, india"
  ];
  const typedEl = document.getElementById('typed-text');
  let lineIndex = 0, charIndex = 0, deleting = false;

  function typeLoop(){
    const current = lines[lineIndex];
    if(!deleting){
      typedEl.textContent = current.slice(0, charIndex + 1);
      charIndex++;
      if(charIndex === current.length){
        deleting = true;
        setTimeout(typeLoop, 1400);
        return;
      }
    } else {
      typedEl.textContent = current.slice(0, charIndex - 1);
      charIndex--;
      if(charIndex === 0){
        deleting = false;
        lineIndex = (lineIndex + 1) % lines.length;
      }
    }
    setTimeout(typeLoop, deleting ? 30 : 55);
  }
  typeLoop();

  // ---------- Three.js scene ----------
  const canvas = document.getElementById('bg-canvas');
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(55, window.innerWidth / window.innerHeight, 0.1, 100);
  camera.position.z = 9;

  const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, alpha: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

  // Starfield
  const starGeo = new THREE.BufferGeometry();
  const starCount = 900;
  const starPositions = new Float32Array(starCount * 3);
  for(let i = 0; i < starCount; i++){
    starPositions[i*3] = (Math.random() - 0.5) * 60;
    starPositions[i*3+1] = (Math.random() - 0.5) * 60;
    starPositions[i*3+2] = (Math.random() - 0.5) * 60;
  }
  starGeo.setAttribute('position', new THREE.BufferAttribute(starPositions, 3));
  const starMat = new THREE.PointsMaterial({ color: 0x8b93b0, size: 0.045, transparent: true, opacity: 0.55 });
  const stars = new THREE.Points(starGeo, starMat);
  scene.add(stars);

  // The Stack: three orbiting wireframe solids — db / backend / frontend
  const group = new THREE.Group();
  scene.add(group);

  function makeSolid(geometry, color, radius, speed, phase){
    const wire = new THREE.WireframeGeometry(geometry);
    const mat = new THREE.LineBasicMaterial({ color, transparent: true, opacity: 0.85 });
    const mesh = new THREE.LineSegments(wire, mat);
    const pivot = new THREE.Group();
    pivot.add(mesh);
    mesh.position.x = radius;
    pivot.userData = { speed, phase, selfSpin: 0.01 + Math.random()*0.01 };
    return { pivot, mesh };
  }

  const dbSolid = makeSolid(new THREE.BoxGeometry(1.1,1.1,1.1), 0x22d3ee, 3.4, 0.35, 0);
  const apiSolid = makeSolid(new THREE.OctahedronGeometry(1.15), 0xa78bfa, 2.5, -0.5, 2.1);
  const uiSolid = makeSolid(new THREE.TetrahedronGeometry(1.3), 0xf472b6, 1.7, 0.65, 4.2);

  [dbSolid, apiSolid, uiSolid].forEach(s => group.add(s.pivot));

  // faint connecting core
  const core = new THREE.Mesh(
    new THREE.IcosahedronGeometry(0.35, 0),
    new THREE.MeshBasicMaterial({ color: 0xffffff, wireframe: true, transparent: true, opacity: 0.3 })
  );
  group.add(core);

  group.position.set(0, 0, 0);
  group.rotation.x = 0.4;

  // Mouse parallax
  let mouseX = 0, mouseY = 0;
  window.addEventListener('mousemove', (e) => {
    mouseX = (e.clientX / window.innerWidth - 0.5) * 2;
    mouseY = (e.clientY / window.innerHeight - 0.5) * 2;
  });

  const clock = new THREE.Clock();
  function animate(){
    requestAnimationFrame(animate);
    const t = clock.getElapsedTime();

    [dbSolid, apiSolid, uiSolid].forEach(s => {
      s.pivot.rotation.y = t * s.pivot.userData.speed + s.pivot.userData.phase;
      s.mesh.rotation.x += s.pivot.userData.selfSpin;
      s.mesh.rotation.y += s.pivot.userData.selfSpin * 0.7;
    });
    core.rotation.y += 0.004;
    core.rotation.x += 0.003;

    group.rotation.y += (mouseX * 0.4 - group.rotation.y) * 0.02;
    group.rotation.x = 0.4 + (mouseY * 0.2 - 0.4) * 0.3;

    stars.rotation.y = t * 0.01;

    renderer.render(scene, camera);
  }
  animate();

  window.addEventListener('resize', () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  });
</script>

</body>
</html>
