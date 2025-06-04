<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Menu Hamburger Exemple</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }
    .navbar {
      background: #333;
      color: white;
      padding: 1rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .brand {
      font-weight: bold;
      font-size: 1.2em;
    }
    .menu {
      display: none;
      flex-direction: column;
      background: #222;
      position: absolute;
      top: 60px;
      right: 16px;
      min-width: 150px;
      border-radius: 4px;
      overflow: hidden;
    }
    .menu a {
      color: white;
      text-decoration: none;
      padding: 1rem;
      display: block;
      transition: background 0.2s;
    }
    .menu a:hover {
      background: #444;
    }
    .hamburger {
      width: 30px;
      height: 22px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      cursor: pointer;
    }
    .bar {
      height: 4px;
      width: 100%;
      background: white;
      border-radius: 2px;
    }
    @media (min-width: 600px) {
      .menu {
        display: flex !important;
        position: static;
        flex-direction: row;
        background: none;
        min-width: unset;
        border-radius: 0;
        overflow: visible;
      }
      .menu a {
        padding: 0 1rem;
      }
      .hamburger {
        display: none;
      }
    }
  </style>
</head>
<body>
  <nav class="navbar">
    <div class="brand">MonSite</div>
    <div class="hamburger" id="hamburger" aria-label="Menu" tabindex="0">
      <div class="bar"></div>
      <div class="bar"></div>
      <div class="bar"></div>
    </div>
    <div class="menu" id="menu">
      <a href="#">Accueil</a>
      <a href="#">À propos</a>
      <a href="#">Contact</a>
    </div>
  </nav>
  <script>
    const hamburger = document.getElementById('hamburger');
    const menu = document.getElementById('menu');
    hamburger.addEventListener('click', () => {
      menu.style.display = menu.style.display === 'flex' ? 'none' : 'flex';
    });
    // Accessibilité: permet d'ouvrir/fermer le menu avec Enter ou Espace
    hamburger.addEventListener('keydown', (e) => {
      if (e.key === "Enter" || e.key === " ") {
        menu.style.display = menu.style.display === 'flex' ? 'none' : 'flex';
      }
    });
    // Ferme le menu si on clique ailleurs (mobile)
    document.addEventListener('click', (e) => {
      if (!hamburger.contains(e.target) && !menu.contains(e.target)) {
        if(window.innerWidth < 600) menu.style.display = 'none';
      }
    });
    // Réinitialise le menu en cas de redimensionnement
    window.addEventListener('resize', () => {
      if(window.innerWidth >= 600) {
        menu.style.display = 'flex';
      } else {
        menu.style.display = 'none';
      }
    });
  </script>
</body>
</html>
