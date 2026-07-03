/* ============================================
   LE SYSTEME SOLAIRE — script.js
   Toute la scène (orbites, planètes, légende) est
   construite ici à partir du tableau PLANETS.
   ============================================ */

const PLANETS = [
  {
    id: 'soleil', name: 'Le Soleil', type: 'Étoile', color: '#ffb75e',
    desc: "Une naine jaune qui concentre à elle seule 99,8% de la masse du système solaire. Sa fusion nucléaire produit la lumière et la chaleur qui rendent la vie possible sur Terre.",
    distance: '0 UA — centre du système',
    diameter: '1 392 000 km (109× la Terre)',
    day: '≈27 jours (rotation différentielle)',
    year: '—',
    moons: '—',
    temp: '≈5 500 °C en surface',
    fact: "Sa lumière met environ 8 minutes et 20 secondes à atteindre la Terre."
  },
  {
    id: 'mercure', name: 'Mercure', type: 'Planète tellurique', color: '#9c9791',
    orbitPercent: 20, sizeVmin: 2.4, duration: 5,
    desc: "La plus proche du Soleil et la plus rapide sur son orbite. Sans atmosphère pour retenir la chaleur, sa surface passe de plus de 400°C le jour à moins de -180°C la nuit.",
    distance: '0,39 UA (57,9 M km)',
    diameter: '4 879 km',
    day: '59 jours terrestres',
    year: '88 jours',
    moons: '0',
    temp: '≈167 °C en moyenne (écarts extrêmes)',
    fact: "Une journée solaire complète y dure environ 176 jours terrestres, deux fois son année."
  },
  {
    id: 'venus', name: 'Vénus', type: 'Planète tellurique', color: '#e8c9a0',
    orbitPercent: 32, sizeVmin: 3.6, duration: 8,
    desc: "Enveloppée d'une épaisse atmosphère de dioxyde de carbone qui retient la chaleur comme une serre géante. C'est la planète la plus chaude du système solaire.",
    distance: '0,72 UA (108,2 M km)',
    diameter: '12 104 km',
    day: '243 jours (rétrograde)',
    year: '225 jours',
    moons: '0',
    temp: '≈464 °C',
    fact: "Vénus tourne dans le sens inverse des autres planètes, et son jour est plus long que son année."
  },
  {
    id: 'terre', name: 'La Terre', type: 'Planète tellurique', color: '#3f8fb0',
    orbitPercent: 44, sizeVmin: 3.8, duration: 12,
    desc: "La seule planète connue à abriter la vie, grâce à son eau liquide, son atmosphère respirable et son champ magnétique protecteur.",
    distance: '1 UA (149,6 M km)',
    diameter: '12 742 km',
    day: '23 h 56 min',
    year: '365,25 jours',
    moons: '1 (la Lune)',
    temp: '≈15 °C',
    fact: "Près de 70% de sa surface est recouverte d'océans, d'où son surnom de planète bleue."
  },
  {
    id: 'mars', name: 'Mars', type: 'Planète tellurique', color: '#c1622d',
    orbitPercent: 56, sizeVmin: 3.0, duration: 20,
    desc: "La planète rouge doit sa couleur à l'oxyde de fer qui recouvre son sol. Elle abrite Olympus Mons, le plus grand volcan connu du système solaire.",
    distance: '1,52 UA (227,9 M km)',
    diameter: '6 779 km',
    day: '24 h 37 min',
    year: '687 jours',
    moons: '2 (Phobos, Deimos)',
    temp: '≈-65 °C',
    fact: "Une année sur Mars dure près de deux années terrestres."
  },
  {
    id: 'jupiter', name: 'Jupiter', type: 'Géante gazeuse', color: '#d9a878',
    orbitPercent: 68, sizeVmin: 7.5, duration: 45,
    desc: "La plus grande planète du système solaire, composée surtout d'hydrogène et d'hélium. Sa Grande Tache rouge est une tempête plus large que la Terre, active depuis des siècles.",
    distance: '5,20 UA (778,5 M km)',
    diameter: '139 820 km',
    day: '9 h 56 min',
    year: '11,9 années',
    moons: '115+ lunes confirmées',
    temp: '≈-110 °C (sommet des nuages)',
    fact: "Sa masse est plus de deux fois supérieure à celle de toutes les autres planètes réunies."
  },
  {
    id: 'saturne', name: 'Saturne', type: 'Géante gazeuse', color: '#e8d4a0',
    orbitPercent: 80, sizeVmin: 6.6, duration: 65,
    desc: "Reconnaissable à ses anneaux spectaculaires de glace et de roche. C'est la planète la moins dense du système solaire : elle flotterait sur l'eau.",
    distance: '9,58 UA (1,43 Md km)',
    diameter: '116 460 km',
    day: '10 h 34 min',
    year: '29,4 années',
    moons: '290+ lunes recensées',
    temp: '≈-140 °C (sommet des nuages)',
    fact: "Avec le plus grand nombre de lunes connues, Saturne est la championne toutes catégories du système solaire."
  },
  {
    id: 'uranus', name: 'Uranus', type: 'Géante de glace', color: '#a9dee0',
    orbitPercent: 90, sizeVmin: 5.0, duration: 90,
    desc: "Une géante de glace qui tourne presque couchée sur le côté, avec un axe incliné à 98 degrés. Ses fins anneaux sombres sont difficiles à observer depuis la Terre.",
    distance: '19,2 UA (2,87 Md km)',
    diameter: '50 724 km',
    day: '17 h 14 min (rétrograde)',
    year: '84 années',
    moons: '27',
    temp: '≈-195 °C',
    fact: "Elle fut la première planète découverte grâce à un télescope, par William Herschel en 1781."
  },
  {
    id: 'neptune', name: 'Neptune', type: 'Géante de glace', color: '#3d5aa8',
    orbitPercent: 98, sizeVmin: 5.0, duration: 120,
    desc: "La planète la plus éloignée du Soleil, plongée dans un froid extrême. Elle abrite les vents les plus violents du système solaire, jusqu'à 2 100 km/h.",
    distance: '30,1 UA (4,50 Md km)',
    diameter: '49 244 km',
    day: '16 h 06 min',
    year: '165 années',
    moons: '14',
    temp: '≈-200 °C',
    fact: "Elle n'a été observée qu'une seule fois de près, par la sonde Voyager 2 en 1989."
  }
];

const state = {
  isPlaying: true,
  selected: null,
  wasPlayingBeforeSelect: true
};

/* ---------- Construction de la scène ---------- */

function buildStage() {
  const stage = document.getElementById('stage');
  const legend = document.getElementById('legend');
  const sunData = PLANETS.find(p => p.id === 'soleil');

  // Le Soleil
  const sun = document.createElement('button');
  sun.type = 'button';
  sun.className = 'sun';
  sun.dataset.planet = 'soleil';
  sun.setAttribute('aria-label', 'Explorer le Soleil');
  stage.appendChild(sun);

  // Puce du Soleil dans la légende
  legend.appendChild(makeChip(sunData));

  // Une orbite + une planète pour chaque astre (sauf le Soleil)
  PLANETS.filter(p => p.id !== 'soleil').forEach(p => {
    const ring = document.createElement('div');
    ring.className = 'orbit-ring';
    ring.dataset.planet = p.id;
    ring.style.width = p.orbitPercent + '%';
    ring.style.height = p.orbitPercent + '%';
    ring.setAttribute('aria-hidden', 'true');

    const auLabel = document.createElement('span');
    auLabel.className = 'au-label';
    auLabel.textContent = p.distance.split(' ')[0] + ' UA';
    ring.appendChild(auLabel);

    const rotator = document.createElement('div');
    rotator.className = 'orbit-rotator';
    rotator.dataset.planet = p.id;
    rotator.style.width = p.orbitPercent + '%';
    rotator.style.height = p.orbitPercent + '%';
    rotator.style.setProperty('--dur', p.duration + 's');

    const planetBtn = document.createElement('button');
    planetBtn.type = 'button';
    planetBtn.className = 'planet planet--' + p.id;
    planetBtn.dataset.planet = p.id;
    planetBtn.style.setProperty('--planet-color', p.color);
    planetBtn.style.width = p.sizeVmin + 'vmin';
    planetBtn.style.height = p.sizeVmin + 'vmin';
    planetBtn.setAttribute('aria-label', 'Explorer ' + p.name);

    rotator.appendChild(planetBtn);
    stage.appendChild(ring);
    stage.appendChild(rotator);

    legend.appendChild(makeChip(p));
  });
}

function makeChip(p) {
  const chip = document.createElement('button');
  chip.type = 'button';
  chip.className = 'chip';
  chip.dataset.planet = p.id;
  chip.style.setProperty('--planet-color', p.color);
  const swatch = document.createElement('span');
  swatch.className = 'swatch';
  chip.appendChild(swatch);
  chip.appendChild(document.createTextNode(p.name));
  return chip;
}

function buildStars() {
  const container = document.getElementById('stars');
  const frag = document.createDocumentFragment();
  const count = 140;

  for (let i = 0; i < count; i++) {
    const star = document.createElement('span');
    star.className = 'star';
    const size = (Math.random() * 1.6 + 0.6).toFixed(2);
    star.style.width = size + 'px';
    star.style.height = size + 'px';
    star.style.top = (Math.random() * 100).toFixed(2) + '%';
    star.style.left = (Math.random() * 100).toFixed(2) + '%';
    star.style.setProperty('--min-o', (Math.random() * 0.25 + 0.1).toFixed(2));
    star.style.setProperty('--max-o', (Math.random() * 0.4 + 0.6).toFixed(2));
    star.style.animationDuration = (Math.random() * 3 + 2).toFixed(2) + 's';
    star.style.animationDelay = (Math.random() * 3).toFixed(2) + 's';
    frag.appendChild(star);
  }
  container.appendChild(frag);
}

/* ---------- Sélection d'un astre ---------- */

function selectPlanet(id) {
  const data = PLANETS.find(p => p.id === id);
  if (!data) return;

  state.selected = id;
  state.wasPlayingBeforeSelect = state.isPlaying;
  if (state.isPlaying) setPlaying(false);

  document.querySelectorAll('.orbit-ring').forEach(r => {
    r.classList.toggle('is-active', r.dataset.planet === id);
    r.classList.toggle('is-dim', r.dataset.planet !== id);
  });
  document.querySelectorAll('.orbit-rotator').forEach(r => {
    r.classList.toggle('is-dim', r.dataset.planet !== id);
  });
  document.querySelectorAll('.planet').forEach(el => {
    el.classList.toggle('is-active', el.dataset.planet === id);
  });
  document.getElementById('stage').querySelector('.sun')
    .classList.toggle('is-active', id === 'soleil');
  document.querySelectorAll('.chip').forEach(c => {
    c.classList.toggle('is-active', c.dataset.planet === id);
  });

  fillInfoPanel(data);
  openInfoPanel();
}

function fillInfoPanel(data) {
  document.getElementById('infoType').textContent = data.type;
  document.getElementById('infoName').textContent = data.name;
  document.getElementById('infoDesc').textContent = data.desc;

  const grid = document.getElementById('infoGrid');
  grid.innerHTML = '';
  const stats = [
    ['Distance du Soleil', data.distance],
    ['Diamètre', data.diameter],
    ['Durée du jour', data.day],
    ["Durée de l'année", data.year],
    ['Lunes connues', data.moons],
    ['Température', data.temp]
  ];
  stats.forEach(([label, value]) => {
    const row = document.createElement('div');
    const dt = document.createElement('dt');
    dt.textContent = label;
    const dd = document.createElement('dd');
    dd.textContent = value;
    row.appendChild(dt);
    row.appendChild(dd);
    grid.appendChild(row);
  });

  const fact = document.getElementById('infoFact');
  fact.innerHTML = '';
  const strong = document.createElement('strong');
  strong.textContent = 'Le saviez-vous ? ';
  fact.appendChild(strong);
  fact.appendChild(document.createTextNode(data.fact));
}

function openInfoPanel() {
  const panel = document.getElementById('infoPanel');
  panel.classList.add('is-open');
  panel.setAttribute('aria-hidden', 'false');
  document.getElementById('scrim').classList.add('is-visible');
  document.getElementById('closeInfo').focus();
}

function closeInfoPanel() {
  const panel = document.getElementById('infoPanel');
  panel.classList.remove('is-open');
  panel.setAttribute('aria-hidden', 'true');
  document.getElementById('scrim').classList.remove('is-visible');

  document.querySelectorAll('.orbit-ring, .orbit-rotator').forEach(el => {
    el.classList.remove('is-active', 'is-dim');
  });
  document.querySelectorAll('.planet, .chip, .sun').forEach(el => {
    el.classList.remove('is-active');
  });

  const previous = state.selected;
  state.selected = null;
  if (state.wasPlayingBeforeSelect) setPlaying(true);

  const trigger = previous && document.querySelector('.chip[data-planet="' + previous + '"]');
  if (trigger) trigger.focus();
}

/* ---------- Lecture / pause / vitesse ---------- */

function setPlaying(playing) {
  state.isPlaying = playing;
  document.getElementById('stage').classList.toggle('is-paused', !playing);
  document.getElementById('playPauseIcon').textContent = playing ? '⏸' : '▶';
  document.getElementById('playPause').setAttribute(
    'aria-label', playing ? 'Mettre en pause' : 'Reprendre'
  );
}

/* ---------- Écouteurs d'événements ---------- */

function initEvents() {
  document.getElementById('stage').addEventListener('click', e => {
    const btn = e.target.closest('[data-planet]');
    if (btn) selectPlanet(btn.dataset.planet);
  });

  document.getElementById('legend').addEventListener('click', e => {
    const btn = e.target.closest('[data-planet]');
    if (btn) selectPlanet(btn.dataset.planet);
  });

  document.getElementById('closeInfo').addEventListener('click', closeInfoPanel);
  document.getElementById('scrim').addEventListener('click', closeInfoPanel);

  document.getElementById('playPause').addEventListener('click', () => {
    setPlaying(!state.isPlaying);
    if (state.selected) state.wasPlayingBeforeSelect = state.isPlaying;
  });

  document.getElementById('speed').addEventListener('input', e => {
    const v = parseFloat(e.target.value);
    document.documentElement.style.setProperty('--speed', v);
    document.getElementById('speedValue').textContent = v + '×';
  });

  document.addEventListener('keydown', e => {
    if (e.key === 'Escape' && state.selected) closeInfoPanel();
  });
}

/* ---------- Démarrage ---------- */

buildStage();
buildStars();
initEvents();
