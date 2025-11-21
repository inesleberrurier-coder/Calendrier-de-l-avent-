<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Calendrier de l'Avent</title>
<style>
    body {
        margin: 0;
        background: #0b2e1f;
        font-family: Arial, sans-serif;
        color: white;
        overflow-x: hidden;
    }

    /* Titre animé */
    h1 {
        text-align: center;
        font-size: 3rem;
        margin-top: 20px;
        color: #ff0000;
        text-shadow: 0 0 10px #ff6b6b;
        animation: glow 2s infinite alternate;
    }
    @keyframes glow {
        from { text-shadow: 0 0 5px #ff6b6b; }
        to { text-shadow: 0 0 20px #ff0000; }
    }

    /* Grille des cases */
    .grid {
        display: grid;
        grid-template-columns: repeat(6, 1fr);
        gap: 15px;
        padding: 30px;
        max-width: 1200px;
        margin: auto;
    }

    /* Case */
    .day {
        background: #b30000;
        height: 120px;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 2rem;
        font-weight: bold;
        cursor: pointer;
        position: relative;
        transition: transform 0.2s;
    }

    .day:hover {
        transform: scale(1.1);
    }

    /* Petit nœud */
    .day::before {
        content: "🎀";
        position: absolute;
        top: -10px;
        font-size: 22px;
    }

    /* Fenêtre popup */
    .popup {
        display: none;
        position: fixed;
        top: 0; left: 0; right: 0; bottom: 0;
        background: rgba(0, 0, 0, 0.8);
        align-items: center;
        justify-content: center;
        padding: 20px;
    }

    .popup-content {
        background: white;
        color: black;
        padding: 20px;
        border-radius: 10px;
        width: 80%;
        max-width: 500px;
        text-align: center;
        position: relative;
    }

    .close {
        position: absolute;
        top: 10px;
        right: 15px;
        cursor: pointer;
        font-size: 20px;
        font-weight: bold;
    }

    /* Neige permanente */
    .snow {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        z-index: 5;
        background-image: url("https://i.imgur.com/8yZ8FfP.png");
        animation: snowfall 12s linear infinite;
        opacity: 0.6;
    }

    @keyframes snowfall {
        from { background-position: 0 0; }
        to { background-position: 0 1000px; }
    }

    /* Neige dans case ouverte */
    .snow-inside {
        width: 100%;
        height: 150px;
        background-image: url("https://i.imgur.com/8yZ8FfP.png");
        animation: snowfall 6s linear infinite;
        opacity: 0.7;
        margin-bottom: 15px;
    }

    /* Quiz */
    .quiz-question {
        font-weight: bold;
        color: #b30000;
    }
</style>
</head>

<body>

<div class="snow"></div>

<h1>✨ Calendrier de l’Avent ✨</h1>

<div class="grid">

    <!-- CASES 1 À 24 -->
    <div class="day" onclick="openCase(1)">1</div>
    <div class="day" onclick="openCase(2)">2</div>
    <div class="day" onclick="openCase(3)">3</div>
    <div class="day" onclick="openCase(4)">4</div>
    <div class="day" onclick="openCase(5)">5</div>
    <div class="day" onclick="openCase(6)">6</div>
    <div class="day" onclick="openCase(7)">7</div>
    <div class="day" onclick="openCase(8)">8</div>
    <div class="day" onclick="openCase(9)">9</div>
    <div class="day" onclick="openCase(10)">10</div>
    <div class="day" onclick="openCase(11)">11</div>
    <div class="day" onclick="openCase(12)">12</div>
    <div class="day" onclick="openCase(13)">13</div>
    <div class="day" onclick="openCase(14)">14</div>
    <div class="day" onclick="openCase(15)">15</div>
    <div class="day" onclick="openCase(16)">16</div>
    <div class="day" onclick="openCase(17)">17</div>
    <div class="day" onclick="openCase(18)">18</div>
    <div class="day" onclick="openCase(19)">19</div>
    <div class="day" onclick="openCase(20)">20</div>
    <div class="day" onclick="openCase(21)">21</div>
    <div class="day" onclick="openCase(22)">22</div>
    <div class="day" onclick="openCase(23)">23</div>
    <div class="day" onclick="openCase(24)">24</div>

</div>

<!-- POPUP -->
<div class="popup" id="popup">
    <div class="popup-content">
        <span class="close" onclick="closePopup()">X</span>
        <div id="snowInside" class="snow-inside"></div>
        <div id="popupText"></div>
    </div>
</div>

<script>
function openCase(num) {
    const popup = document.getElementById("popup");
    const text = document.getElementById("popupText");

    text.innerHTML = "";

    const messages = {
        1: "<strong>Info :</strong> La DiSI CO a été parmi les premiers établissements à mettre en place l'intranet ULLO.",
        2: "<strong class='quiz-question'>Quiz :</strong> Savez-vous par qui a été développé l'outil TaToo météo ?<br>Réponse correcte : Angers.",
        3: "Tous les ans l'ESI d'Orléans participe au Cross de Bercy. Bravo aux participants !",
        4: "<strong class='quiz-question'>Quiz :</strong> Combien d’agneaux la DiSI CO a eu ce printemps ? Réponse correcte : 3.",
        5: "<strong class='quiz-question'>Quiz :</strong> Date de création de l'IA ? Réponse correcte : 1956.",
        6: "Recette pour un apéro réussi : <a href='https://www.marmiton.org/recettes/recette_sapin-feuillete-au-pesto_383379.aspx' target='_blank'>Sapin feuilleté au pesto</a>",
        7: "Suite à la recette d’hier, une deuxième pour un super apéro : <a href='https://www.marmiton.org/recettes/recette_gougeres-au-fromage_20095.aspx' target='_blank'>Gougères au fromage</a>",
        8: "Contenu à ajouter pour le jour 8.",
        9: "Contenu à ajouter pour le jour 9.",
        10: "Contenu à ajouter pour le jour 10.",
        11: "Contenu à ajouter pour le jour 11.",
        12: "En lumière : Nous avons 2 ruches pour la biodiversité.",
        13: "Recette : <a href='https://www.marmiton.org/recettes/recette_huitres-gratinees-au-parmesan_56242.aspx' target='_blank'>Huîtres gratinées</a>",
        14: "Marchés de Noël en Loire-Atlantique : <a href='https://44.kidiklik.fr/articles/335276-les-marches-de-noel-nantes-et-en-loire-atlantique.html' target='_blank'>Voir la liste</a>",
        15: "Relamping des néons remplacés par LED.",
        16: "Contenu à ajouter pour le jour 16.",
        17: "Concours des pulls de Noël 🎅 Prenez vos plus beaux pulls et gagnez des chocolats !",
        18: "Contenu à ajouter pour le jour 18.",
        19: "<strong class='quiz-question'>Journée mondiale du pull de Noël</strong><br>Quiz : D'où vient la tradition ? Réponse correcte : Angleterre.",
        20: "Vin chaud : <a href='https://www.marmiton.org/recettes/recette_vin-chaud-aux-epices_25224.aspx' target='_blank'>Vin chaud aux épices</a>",
        21: "Gratin dauphinois : <a href='https://www.marmiton.org/recettes/recette_gratin-dauphinois_13809.aspx' target='_blank'>Gratin dauphinois</a>",
        22: "Contenu à ajouter pour le jour 22.",
        23: "Contenu à ajouter pour le jour 23.",
        24: "Contenu à ajouter pour le jour 24."
    };

    text.innerHTML = messages[num];
    popup.style.display = "flex";
}

function closePopup() {
    document.getElementById("popup").style.display = "none";
}
</script>

</body>
</html>
