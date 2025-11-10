<!DOCTYPE html>     
<html lang="de">                                                                                 
<head>
  <meta charset="UTF-8" />
  <title>Heute noch mit Gott in Verbindung treten</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>

/* -------------------------------------------------------------------------------------------------------------  ÜBERSCHRIFT- ----------- */

h1 {
  font-size: 2.8rem;          /* Schriftgröße der Überschrift */
  font-weight: 300;           /* Dünnere Schrift */
  letter-spacing: 0.05em;     /* Etwas mehr Abstand zwischen Buchstaben */
  text-transform: uppercase;  /* Alles in Großbuchstaben */
  margin-bottom: 40px;        /* Abstand nach unten */
}

/* -------------------------------------------------------------------------------------------------------------  VIDEOBEREICH ------------ */

/* ------------------------------------------------------------------Container für das YouTube-Video*/

.video-wrapper {
  position: relative;             /* Ermöglicht absolute Positionierung des iframes */
  padding-bottom: 56.25%;         /* Höhe im Verhältnis 16:9 */
  height: 0;                      /* Höhe wird durch Padding bestimmt */
  overflow: hidden;               /* Schneidet überstehendes Video ab */
  border-radius: 8px;             /* Runde Ecken */
  box-shadow: 0 0 15px rgba(255,255,255,0.2); /* Leichter Schimmer-Effekt */
  margin-bottom: 40px;            /* Abstand nach unten */
}

/* -----------------------------------------------------------------Das YouTube-Video selbst */

.video-wrapper iframe {
  position: absolute;             /* Füllt den Container komplett aus */
  top: 0; left: 0;                /* Startet oben links */
  width: 100%; height: 100%;      /* Passt sich der Containergröße an */
  border: 0;                      /* Entfernt den Rahmen */
}

/* -------------------------------------------------------------------------------------------------------------  ZITATE & ROTATOR ------------ */

/* ----------------------------------------------------------------Grundzustand: Zitat unsichtbar */

.rotator-item {
  display: none;                 /* Nicht anzeigen */
  opacity: 0;                    /* Unsichtbar */
  transition: opacity 1.2s ease; /* Sanfte Einblendung */
  pointer-events: none;          /* Keine Interaktion möglich */
}

/* ----------------------------------------------------------------Aktives Zitat sichtbar */

.rotator-item.active {
  display: block;                /* Anzeigen */
  opacity: 1;                    /* Voll sichtbar */
  pointer-events: auto;          /* Interaktion erlaubt */
}

/* ------------------------------------------------------------------Autorenangabe unter Zitat */

.rotator-item footer {
  margin-top: 10px;              /* Abstand nach oben */
  font-size: 1rem;               /* Schriftgröße */
  font-style: normal;            /* Normale Schrift */
  color: #aaa;                   /* Heller Grauton */
}

/* ------------------------------------------------------------------Bilder im Rotator */

.rotator-image {
  max-width: 100%;               /* Nicht größer als Container */
  height: auto;                  /* Proportional skalieren */
  display: block;                /* Blockelement */
  margin: 0 auto;                /* Zentriert horizontal */
}

/* -------------------------------------------------------------------------------------------------------------  MOND & STERNE ------------ */

/* ------------------------------------------------------------------Gesamter Hintergrund für Mond und Sterne */

#moon-background {
  position: fixed;          /* Bleibt beim Scrollen an Ort und Stelle */
  top: 0; left: 0;          /* Startpunkt oben links */
  width: 100%; height: 100%;/* Füllt das gesamte Fenster */
  overflow: hidden;          /* Überstehende Teile abschneiden */
  z-index: 0;                /* Liegt hinter allem anderen */
  pointer-events: none;      /* Klicks passieren hindurch */
  background: #000;          /* Schwarzer Himmel */
}

/* ------------------------------------------------------------------Der Mond selbst */

.moon {
  position: absolute;
  top: 20px;                 /* Abstand vom oberen Rand */
  left: 50%;                 /* Horizontal zentriert */
  transform: translateX(-50%); /* Genau zentrieren */
  width: 100px;
  height: 100px;
  border-radius: 50%;        /* Kreisform */
  background: #ccc;          /* Helle Mondfarbe */
  overflow: hidden;          /* Überstehende Inhalte abschneiden */
}

/* -----------------------------------------------------------------Schwarzer Schatten für Mondphasen */

.shadow {
  position: absolute;
  top: 0;
  left: -120px;              /* Verschoben für Halbmond-Effekt */
  width: 120px;
  height: 120px;
  border-radius: 50%;
  background: #000;          /* Schwarz für Schatten */
}

/* -----------------------------------------------------------------Sterne */

.star {
  position: absolute;
  background: white;         /* Weiße Punkte */
  border-radius: 50%;        /* Rund */
  opacity: 0.8;              /* Leicht transparent */
}


/* -------------------------------------------------------------------------------------------------------------MENÜ------------ */

.top-menu {
  position: fixed;
  top: 10px;         /* Abstand oben */
  left: 10px;        /* weiter links */
  z-index: 10;
  display: flex;
  flex-direction: column;
  align-items: flex-start; /* linksbündig */
}

/* ------------------------------------------------------------------Button: kleiner und weiß */

#topMenuBtn {
  background: transparent;  /* Kein Hintergrund */
  border: none;             /* Kein Rahmen */
  color: white;             /* Weißer Text/Pfeil */
  font-size: 1.2rem;        /* Größe des Pfeils */
  cursor: pointer;          /* Mauszeiger zeigt Hand */
  padding: 0;               /* Kein Innenabstand */
  line-height: 1;           /* Zeilenhöhe kompakt */
  transition: transform 0.2s ease; /* sanfte Bewegung beim Hover */
}

#topMenuBtn:hover {
  transform: translateY(-2px); /* Button bewegt sich leicht nach oben */
}

/*-------------------------------------------------------------------Menü-Inhalt (Dropdown) */

.top-menu-content {
  display: flex;           
  flex-direction: column;   /* Untereinander anordnen */
  align-items: flex-start;  /* Links ausrichten */
  margin-top: 2px;          /* Abstand knapp unter Button */
  opacity: 0;               /* Unsichtbar */
  pointer-events: none;     /* Klicks blockiert */
  transition: opacity 0.3s ease; /* sanftes Einblenden */
}

.top-menu-content.active {
  opacity: 1;               /* Sichtbar */
  pointer-events: auto;     /* Klicks erlaubt */
}

/* --------------------------------------------------------------------Links im Menü */

.top-menu-content a {
  margin: 2px 0;            /* Abstand zwischen Links/Logos */
}

/*-------------------------------------------------------------------- Logos im Menü */

.top-menu-content img {
  max-width: 80px;          /* Logos nicht zu groß */
  height: auto;             
  display: block;           /* Blockelement für Zentrierung */
}

/* -------------------------------------------------------------------------------------------------------------FOOTER------------ */

html, body {
  height: 100%;                  /* Seite füllt gesamte Browserhöhe aus */
  margin: 0;                     /* Entfernt Standardabstand außen */
  padding: 0;                    /* Entfernt Standard-Innenabstand */
  display: flex;                 /* Aktiviert Flexbox für vertikale Anordnung */
  flex-direction: column;        /* Elemente (main, footer) untereinander anordnen */
  background-color: #000;        /* Schwarzer Seitenhintergrund */
  color: white;                  /* Standardtextfarbe: weiß */
  font-family: Georgia, serif;   /* Serifenschrift für klassischen Look */
  overflow-x: hidden;            /* Verhindert horizontales Scrollen */
}

main.container {
  flex: 1;                       /* Dehnt sich aus, um Platz zwischen Header & Footer zu füllen */
  position: relative;            /* Erlaubt später absolute Positionierungen innerhalb */
  z-index: 1;                    /* Liegt über dem Hintergrund */
  max-width: 780px;              /* Begrenzt Textbreite für gute Lesbarkeit */
  margin: 0 auto;                /* Zentriert den Inhalt horizontal */
  padding: 120px 20px 60px;      /* Innenabstand: oben, seitlich, unten */
  text-align: center;            /* Zentriert Text und Elemente im Container */
}

.page-footer {
  flex-shrink: 0;                /* Footer schrumpft nicht bei wenig Platz */
  width: 100%;                   /* Nimmt die volle Seitenbreite ein */
  text-align: center;            /* Zentriert den Footer-Text */
  color: #ccc;                   /* Helles Grau für Textfarbe */
  font-size: 0.9rem;             /* Etwas kleinere Schrift */
  padding: 60px 0 40px;          /* Innenabstand: oben, unten */

  /* Hintergrundverlauf: unten schwarz → nach oben leicht transparent */
  background: linear-gradient(to top, rgba(0,0,0,1) 70%, rgba(0,0,0,0.6) 100%);

  /* Dünne, helle Linie über dem Footer */
  border-top: 1px solid rgba(255,255,255,0.15);

  /* Leichter Glas-/Weichzeichner-Effekt für modernen Look */
  backdrop-filter: blur(4px);

  /* Schiebt Footer ans untere Ende, wenn Inhalt kurz ist */
  margin-top: auto;
}

.page-footer a {
  color: #fff;                   /* Linkfarbe: weiß */
  text-decoration: none;         /* Kein Unterstrich */
  transition: opacity 0.3s ease; /* Sanfter Übergang bei Hover-Effekt */
}

.page-footer a:hover {
  opacity: 0.8;                  /* Link wird leicht transparenter beim Hover */
}

/*---------------------------------------------LIEBE-FÜR-ALLE-----------CSS----------HASS-FÜR-KEINEN--------------------------------------------*/
/*--------------------------------------------------------------------WAQF-E-RAHALLAH---------------------------------------------------------------------*/

  </style>
</head>

<body>

  <!------------------------------------------------------------------Mond & Sterne--------------------------------------------------------------------->

  <div id="moon-background">
    <div class="moon">
      <div class="shadow" id="shadow"></div>
    </div>
  </div>

  <!-- --------------------------------------------------------------Hauptinhalt------------------------------------------------------------------------->

  <main class="container" role="main">
<p style="font-size: 32px; font-family: 'Scheherazade New', serif; color: #FFFFFF;">
  بِسْمِ اللهِ الرَّحْمٰنِ الرَّحِيمِ
</p>

    <h1 class="fadeInElement delay-2">Heute noch mit Gott in Verbindung treten</h1>

    <div class="video-wrapper fadeInElement delay-0">
      <iframe 
        src="https://www.youtube.com/embed/i6IIwSBtfm4?si=X8zBYMoXr5Ib2TGx"
        title="GOTT"
        frameborder="0"
        allowfullscreen>
      </iframe>
    </div>

    <section id="rotator">
	
	<blockquote class="rotator-item fadeInElement delay-3" data-duration="50000">
  <img src="https://humanityfirst.de/wp-content/uploads/2020/04/hf-logo_r.png"
       alt="Humanity First Logo"
       style="max-width:100%; height:auto; display:block; margin:0 auto;">

  <div class="actions" style="margin-top:1rem; text-align:center;">
    <a href="https://humanityfirst.de/"
       target="_blank"
       rel="noopener noreferrer"
       style="
         display:inline-block;
         padding:0.6rem 1.4rem;
         color:#fff;
         border:1px solid #fff;
         text-decoration:none;
         border-radius:4px;
         background:rgba(255,255,255,0.08);
         transition:background 0.3s ease;
       "
       onmouseover="this.style.background='rgba(255,255,255,0.2)'"
       onmouseout="this.style.background='rgba(255,255,255,0.08)'">
       Meine NGO Hilfsorganisation
    </a>
  </div>
</blockquote>

	<blockquote class="rotator-item fadeInElement delay-3" data-duration="50000">

<!---------------------------------------------------------------------------------------------------------------Klickbares Buchbild -->

<div style="text-align:center; margin:20px 0;">
  <a href="https://www.verlagderislam.de/Zehn-Beweise-fuer-die-Existenz-Gottes" target="_blank" rel="noopener noreferrer">
    <img src="https://verlagderislam.de/media/image/product/6660/lg/zehn-beweise-fuer-die-existenz-gottes.webp"
         alt="Zehn Beweise für die Existenz Gottes"
         style="max-width:20%; height:auto; border-radius:8px; box-shadow:0 0 15px rgba(255,255,255,0.2);">
  </a>
  <div style="margin-top:10px;">
    <a href="https://ahmadiyya.de/wp-content/uploads/site_uploads/library/hadhrat_mirza_bashir_ud-din_mahmud_ahmad-zehn_beweise_fuer_die_existenz_gottes.pdf" 
       target="_blank" 
       style="display:inline-block;
         padding:0.6rem 1.4rem;
         color:#fff;
         border:1px solid #fff;
         text-decoration:none;
         border-radius:4px;
         background:rgba(255,255,255,0.08);
         transition:background 0.3s ease;
       "
       onmouseover="this.style.background='rgba(255,255,255,0.2)'"
       onmouseout="this.style.background='rgba(255,255,255,0.08)'">
       PDF herunterladen
	   
    </a>
  </div>
</div>
     </blockquote>
      <blockquote class="rotator-item fadeInElement delay-3" data-duration="50000">
        „Diejenigen Menschen, die wirklich an den gnädigen Gott 
glauben und den Umfang Seiner Güte und Liebe erkennen, sind 
mit Dankbarkeit Ihm gegenüber erfüllt. Solche Menschen 
wandeln mit einer unermesslichen Demut auf der Erde und 
verbringen ihr Leben auf gute und gütige Weise. Sie fügen 
niemandem Schaden oder Leid zu, und wenn andere Menschen 
ihnen Zorn entgegenbringen oder unsanft mit ihnen umgehen, 
dann antworten sie auf würdige Art und Weise mit Frieden und 
Zuneigung. Sie beantworten Kränkungen und Schimpfwörter 
nur mit Gebeten und dadurch entwickeln sie solche Qualitäten 
in sich, die einen gnädigen und liebenden Gott widerspiegeln. 
Mit anderen Worten, sie streben danach, allen anderen von 
Nutzen zu sein und ihnen Gutes zu tun.“
        <footer>Hadhrat Mirza Ghulam Ahmad (as)</footer>
      </blockquote>
      <blockquote class="rotator-item fadeInElement delay-3" data-duration="50000">
        „Gott ist der, Der seit ewigen Zeiten Sich immer durch Sein
 klares Wort ‚Ich bin‘ verkündet und die Menschen zu Sich
 eingeladen hat. […] Es steht uns nicht zu, Sein Wort und Seine
 Offenbarung auf eine bestimmte Zeit zu beschränken. Er ist
 heute noch bereit, Seine Sucher an dem Brunnen Seiner
 Offenbarungen reichlich laben zu lassen, wie Er es zuvor tat.
 Die Tore Seiner Gnaden stehen heute noch weit offen, wie
 sie es jederzeit zuvor waren.“
        <footer>Hadhrat Mirza Ghulam Ahmad (as)</footer>
      </blockquote>
      <blockquote class="rotator-item fadeInElement delay-3" data-duration="50000">
        „Die inneren sowie die äußeren Gaben der menschlichen Natur 
zeigen klar, dass der höchste Zweck für deren Erschaffung die 
Liebe und die Erkenntnis Gottes und Seine Verehrung sind. 
Diese Tatsache lässt sich dadurch beweisen, dass der Mensch - 
mag er sich auch noch so vieler Belustigungen erfreuen und an 
vielen Geschäften teilnehmen - die wahre Glückseligkeit ohne 
Gott nicht erfahren kann. Der Mensch als der reichste Millionär, 
als der höchste Beamte, als der erfolgreichste Handelsmann, als 
der mächtigste König oder als der weiseste Philosoph, verlässt 
einst die Verwicklungen dieser Welt mit großem Bedauern. Sein 
Herz hält ihm stets seine Versunkenheit in die weltlichen Sorgen 
vor und sein Gewissen spricht ihn des  Truges und der 
unrechtmäßigen Mittel schuldig, die er für sein weltliches 
Gedeihen anwandte.“
        <footer>Hadhrat Mirza Ghulam Ahmad (as)</footer>
      </blockquote>
	  
    </section>
	
<div style="text-align:center; margin:20px 0;">
  <img src="https://jalsasalana.de/wp-content/uploads/2024/09/4-3.jpg" alt="Beschreibung" style="max-width:50%; height:auto; border-radius:8px;">
</div>

	 <p>„Die inneren sowie die äußeren Gaben der menschlichen Natur 
zeigen klar, dass der höchste Zweck für deren Erschaffung die 
Liebe und die Erkenntnis Gottes und Seine Verehrung sind. 
Diese Tatsache lässt sich dadurch beweisen, dass der Mensch - 
mag er sich auch noch so vieler Belustigungen erfreuen und an 
vielen Geschäften teilnehmen - die wahre Glückseligkeit ohne 
Gott nicht erfahren kann. Der Mensch als der reichste Millionär, 
als der höchste Beamte, als der erfolgreichste Handelsmann, als 
der mächtigste König oder als der weiseste Philosoph, verlässt 
einst die Verwicklungen dieser Welt mit großem Bedauern. Sein 
Herz hält ihm stets seine Versunkenheit in die weltlichen Sorgen 
vor und sein Gewissen spricht ihn des  Truges und der 
unrechtmäßigen Mittel schuldig, die er für sein weltliches 
Gedeihen anwandte.“</p>
	<footer>Hadhrat Mirza Ghulam Ahmad (as)</footer>
  </main>

<!-- --------------------------------------------------------------------------------------------------------------------------------Menü -->

<div class="top-menu">

  <!----------------------------------------------------------------------------- Button mit Pfeil nach unten -->

  <button id="topMenuBtn" aria-label="Menü öffnen">
    ٱلْحَمْدُ لِلّٰهِ
  </button>

  <!------------------------------------------------------------------------------ Menüinhalt (die Logos / Links) -->

  <div class="top-menu-content" id="topMenuContent">
    <a href="https://shop.khuddam.de/" target="_blank">
      <img src="https://shop.khuddam.de/cdn/shop/files/MKAD-2_300x@2x.png?v=1672851247" alt="Khuddam Shop">
    </a>
    <a href="https://verlagderislam.de/Deutsche-Buecher" target="_blank">
      <img src="https://verlagderislam.de/bilder/intern/shoplogo/Logo_Neu.jpg" alt="Verlag der Islam">
    </a>
    <a href="https://muhammad.de/" target="_blank">
      <img src="https://muhammad.de/wp-content/uploads/2023/08/Tarikh-Logo-1x500-1-1.png" alt="Muhammad.de">
    </a>
    <a href="https://www.alislam.org/" target="_blank">
      <img src="https://www.ahmadiyya-islam.org/be-nl/wp-content/uploads/sites/7/2015/05/alislam-logo.png" alt="Al Islam">
    </a>
  </div>
</div>

<footer class="page-footer">
  <p>
    © <span id="year"></span> Heute noch mit Gott in Verbindung treten · <br>
    <a href="https://waqf-e-rahallah.my.canva.site" target="_blank" rel="noopener noreferrer">WAQF-E-RAHALLAH | </a><br>E-Mail: gottistlebendig@gmail.com
  </p>
</footer>

/*---------------------------------------------LIEBE-FÜR-ALLE-----------HTML----------HASS-FÜR-KEINEN-------------------------------------------*/
/*----------------------------------------------------------------------WAQF-E-RAHALLAH---------------------------------------------------------------------*/

  <script>

  // ==================================================================== Rotator 

document.addEventListener('DOMContentLoaded', () => {
  const items = document.querySelectorAll('.rotator-item');
  let current = 0;
  let timer = null;

  function showNext() {
    items.forEach(item => item.classList.remove('active')); // alles ausblenden
    items[current].classList.add('active');                // aktuelles einblenden

    const duration = parseInt(items[current].dataset.duration, 10) || 5000;
    current = (current + 1) % items.length;

    timer = setTimeout(showNext, duration);
  }

  showNext();

  const container = document.getElementById('rotator');
  container.addEventListener('mouseenter', () => clearTimeout(timer));
  container.addEventListener('mouseleave', () => showNext());
});

// ===================================================================== Sterne & Mond 

const moon = document.querySelector('.moon');
const shadow = document.getElementById('shadow');
const moonRect = moon.getBoundingClientRect();
const numStars = 100; // Performance

for (let i = 0; i < numStars; i++) {
  const star = document.createElement('div');
  star.classList.add('star');
  const size = Math.random() * 2 + 1;
  star.style.width = `${size}px`;
  star.style.height = `${size}px`;

  let x, y;
  do {
    x = Math.random() * window.innerWidth;
    y = Math.random() * window.innerHeight;
  } while (x > moonRect.left && x < moonRect.right && y > moonRect.top && y < moonRect.bottom);

  star.style.left = `${x}px`;
  star.style.top = `${y}px`;
  document.getElementById('moon-background').appendChild(star);

  const twinkle = () => {
    star.style.opacity = Math.random() * 0.7 + 0.3;
    const duration = Math.random() * 3000 + 1000;
    setTimeout(twinkle, duration);
  };
  twinkle();
}

function startEclipse() {
  let pos = -180;
  const eclipse = setInterval(() => {
    pos += 0.5;
    shadow.style.left = pos + 'px';
    if(pos >= 150){
      clearInterval(eclipse);
      shadow.style.left = '-180px';
      setTimeout(startEclipse, 1000);
    }
  }, 30);
}
startEclipse();

// ======================================================================= menü

// Button & Menü-Content holen
const topMenuBtn = document.getElementById('topMenuBtn');
const topMenuContent = document.getElementById('topMenuContent');

// Toggle Menü öffnen / schließen
topMenuBtn.addEventListener('click', (e) => {
  e.stopPropagation(); // Klick nur auf Button
  topMenuContent.classList.toggle('active');
});

// Klick außerhalb schließt das Menü
document.addEventListener('click', () => {
  topMenuContent.classList.remove('active');
});
</script>

<script>
  // Dynamisches Jahr
  document.getElementById("year").textContent = new Date().getFullYear();
</script>
<script src='https://cdn.jotfor.ms/agent/embedjs/019a697f718c7e76b963a69b46f30917737a/embed.js'>
</script>
/*---------------------------------------------LIEBE-FÜR-ALLE-----------JS----------HASS-FÜR-KEINEN---------------------------------------------*/
/*-------------------------------------------------------------------WAQF-E-RAHALLAH---------------------------------------------------------------------*/

</body>
</html>



