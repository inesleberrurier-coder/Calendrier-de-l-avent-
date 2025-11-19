<img width="463" height="514" alt="Capture d&#39;écran 2025-11-13 140157" src="https://github.com/user-attachments/assets/071766b7-58df-4e2e-a69d-f0a2a7ef001e" />
<img width="463" height="514" alt="Capture d&#39;écran 2025-11-13 140157" src="https://github.com/user-attachments/assets/83170fd2-e655-4d0e-aec0-039236d747db" />
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>🎄 Calendrier de l'Avent 🎄</title>
<style>
  body { font-family: Arial, sans-serif; background: #064E3B; color: #fff; text-align: center; margin:0; padding:20px; overflow: hidden; }
  h1 { margin-top: 0; font-size: 44px; color: #FFD700; text-shadow: 3px 3px 6px #000; }
  .calendar { display: grid; grid-template-columns: repeat(6, 150px); gap: 15px; justify-content: center; margin: 20px auto; max-width: 960px; z-index: 2; position: relative; }
  .day { background: #e63946; width:150px; height:150px; cursor: pointer; font-weight: bold; color: #fff; text-shadow: 1px 1px 2px #000; box-shadow: 0 6px 12px rgba(0,0,0,0.5); display:flex; align-items:center; justify-content:center; position: relative; font-size:28px; }
  .day::before { content:'🎀'; position:absolute; top:5px; left:5px; font-size:20px; }
  .popup { display:none; position: fixed; z-index: 9999; left:50%; top:50%; transform: translate(-50%,-50%); background:#fff4d9; color:#000; padding:22px; border-radius:12px; width:420px; max-height:80vh; overflow:auto; box-shadow: 0 12px 30px rgba(0,0,0,0.5); }
  .close { margin-top:12px; background:#e63946; color:#fff; border:none; padding:8px 12px; border-radius:6px; cursor:pointer; }
  input[type='text']{padding:6px; width:70%;}
  a{ color:#064E3B; font-weight:bold; }
  .popupSnowflake{position:absolute; top:-10px; color:white; user-select:none; pointer-events:none; font-size:14px; animation:fallPopup 6s linear infinite;}
  @keyframes fallPopup{0%{transform:translateY(-10px)}100%{transform:translateY(300px)}}
  .snowflake{position:fixed; top:-10px; color:white; user-select:none; pointer-events:none; z-index:1; font-size:16px; animation:fallBackground 8s linear infinite;}
  @keyframes fallBackground{0%{transform:translateY(-10px)}100%{transform:translateY(110vh)}}
</style>
</head>
<body>

<h1>🎄 Calendrier de l'Avent 🎄</h1>

<div class="calendar" id="calendar">
  <div class="day" onclick="openPopup(1)">1</div>
  <div class="day" onclick="openPopup(2)">2</div>
  <div class="day" onclick="openPopup(3)">3</div>
  <div class="day" onclick="openPopup(4)">4</div>
  <div class="day" onclick="openPopup(5)">5</div>
  <div class="day" onclick="openPopup(6)">6</div>
  <div class="day" onclick="openPopup(7)">7</div>
  <div class="day" onclick="openPopup(8)">8</div>
  <div class="day" onclick="openPopup(9)">9</div>
  <div class="day" onclick="openPopup(10)">10</div>
  <div class="day" onclick="openPopup(11)">11</div>
  <div class="day" onclick="openPopup(12)">12</div>
  <div class="day" onclick="openPopup(13)">13</div>
  <div class="day" onclick="openPopup(14)">14</div>
  <div class="day" onclick="openPopup(15)">15</div>
  <div class="day" onclick="openPopup(16)">16</div>
  <div class="day" onclick="openPopup(17)">17</div>
  <div class="day" onclick="openPopup(18)">18</div>
  <div class="day" onclick="openPopup(19)">19</div>
  <div class="day" onclick="openPopup(20)">20</div>
  <div class="day" onclick="openPopup(21)">21</div>
  <div class="day" onclick="openPopup(22)">22</div>
  <div class="day" onclick="openPopup(23)">23</div>
  <div class="day" onclick="openPopup(24)">24</div>
</div>

<div id="popup" class="popup" aria-hidden="true">
  <div id="popupContent"></div>
  <button class="close" onclick="closePopup()">Fermer</button>
</div>

<script>
// Snow in background
(function(){
  const count=80;
  for(let i=0;i<count;i++){
    const el=document.createElement('div');
    el.className='snowflake';
    el.textContent='❄';
    el.style.left=Math.random()*100+'vw';
    el.style.opacity=0.4+Math.random()*0.6;
    el.style.fontSize=(8+Math.random()*18)+'px';
    el.style.animationDuration=(6+Math.random()*8)+'s';
    document.body.appendChild(el);
  }
})();

function openPopup(day){
  const box=document.getElementById('popupContent');
  box.innerHTML='';
  for(let i=0;i<30;i++){
    const f=document.createElement('div');
    f.className='popupSnowflake';
    f.textContent='❄';
    f.style.left=Math.random()*380+'px';
    f.style.animationDuration=4+Math.random()*4+'s';
    box.appendChild(f);
  }
  switch(day){
    case 1: box.innerHTML+=`<h2>Jour 1</h2><p><strong style='color:red;'>Info du Jour🗞️<p></strong>La DiSI CO a été <strong>parmi les premiers</strong> établissements à mettre en place l'intranet ULLO.</p>`; break;
    case 2: box.innerHTML+=`<h2>Jour 2</h2><p><strong style='color:red;'>Quiz du jour :<p></strong> Savez-vous par qui a été développé l'outil TaToo météo ?☀️</p><form id='quiz2'><label><input type='radio' name='ans2' value='Nantes'> Nantes</label><br><label><input type='radio' name='ans2' value='Angers'> Angers</label><br><label><input type='radio' name='ans2' value='Rennes'> Rennes</label><br><button type='button' onclick='checkQuiz("quiz2","Angers","res2","info2")'>Valider</button></form><p id='res2'></p><p id='info2' style='display:none;'>TaToo météo a été déployé à l'échelle nationale sur environ 120 000 postes entre mars et mai 2025.</p>`; break;
    case 3: box.innerHTML+=`<h2>Jour 3</h2>
<p><strong style='color:red;'>Info du Jour☀️<p></strong>
Tous les ans l'ESI d'Orléans participe au Cross de Bercy. Cette année :<br>
🏆 Nicolas 5km 322ème<br>
🏆 Eric 10km 630ème<br>
🏆 Charles-Etienne 10km 127ème<br>
👏 Bravo à eux et aux 2000 coureurs !</p>
<img src="https://raw.githubusercontent.com/TON_UTILISATEUR/NOM_DEPOT/main/images/jour3.jpg" alt="Photo Jour 3" width="250">
`; break;
    case 4: box.innerHTML+=`<h2>Jour 4</h2><p>Le site des Marsauderies acceuil chaque année des nouveaux moutons🐑<strong style='color:red;'><Quiz:</p></strongstyle='color:red;'><p> Savez-vous combien d'agneaux la DiSI CO a eu ce printemps ?</p><form id='quiz4'><label><input type='radio' name='ans4' value='1'> 1</label><br><label><input type='radio' name='ans4' value='2'> 2</label><br><label><input type='radio' name='ans4' value='3'> 3</label><br><button type='button' onclick='checkQuiz("quiz4","3","res4","info4")'>Valider</button></form><p id='res4'></p>`; break;
    case 5: box.innerHTML+=`<h2>Jour 5</h2><p>Le mois de l'innovation publique s'est déroulé le mois dernier avec comme thème l'IA.</p><p><strong style='color:red;'>Quiz :<p></strong> En quelle année l'IA a été créée ?</p><form id='quiz5'><label><input type='radio' name='ans5' value='1956'> 1956</label><br><label><input type='radio' name='ans5' value='1962'> 1962</label><br><label><input type='radio' name='ans5' value='1970'> 1970</label><br><button type='button' onclick='checkQuiz("quiz5","1956","res5","info5")'>Valider</button></form><p id='res5'></p>`; break;
    case 6: box.innerHTML+=`<h2>Jour 6</h2><p><p>Bon weekend à tous, n'oubliez pas c'est bientôt Noël ! Pour vous aider à confectionner vos plats de Noël, voici une délicieuse recette pour un apéro réussi 🍽️:</p>
<p><a href='https://www.marmiton.org/recettes/recette_sapin-feuillete-au-pesto_383379.aspx' target='_blank'>Recette de sapin feuilleté au pesto</a></p>
`;
break;
    case 7: box.innerHTML+=`<h2>Jour 7</h2><p>Suite à la recette d'hier, en voici une autre pour un super apéro :</p><p><a href='https://www.marmiton.org/recettes/recette_gougeres-au-fromage_20095.aspx' target='_blank'>Recette des gougères au fromage</a></p>`; break;
    case 8: box.innerHTML+=`<h2>Jour 8</h2><p>Contenu à ajouter pour le jour 8.</p>`; break;
    case 9: box.innerHTML+=`<h2>Jour 9</h2><p>Contenu à ajouter pour le jour 9.</p>`; break;
    case 10: box.innerHTML+=`<h2>Jour 10</h2><p>Contenu à ajouter pour le jour 10.</p>`; break;
    case 11: box.innerHTML+=`<h2>Jour 11</h2><p>Contenu à ajouter pour le jour 11.</p>`; break;
    case 12: box.innerHTML+=`<h2>Jour 12</h2><p><strong style='color:red;'> En lumière : <p></strong> Nous avons 2 ruches aux Marsauderies pour la biodiversité 🍯🐝 et nous avons reçu des pots de miel.<p>Quiz : à votre avis, combien une abeille produit-elle de miel au cours de sa vie ? (g)</p>
        <input type="text" id="quiz12Input" placeholder="Votre réponse (ex : 1g)">
        <button type="button" onclick="checkOpenAnswer12()">Valider</button>
        <p id="quiz12Result"></p>
        <hr>`;
        break;
    case 13: box.innerHTML+=`<h2>Jour 13</h2><p>Bon week-end ! N'hésitez pas à tester des plats de Noël avant l'heure :</p><p><a href='https://www.marmiton.org/recettes/recette_huitres-gratinees-au-parmesan_56242.aspx' target='_blank'>Huîtres gratinées au parmesan</a></p>`; break;
    case 14: box.innerHTML+=`<h2>Jour 14</h2><p>Pour occuper votre dimanche, voici la liste des marchés de Noël en Loire-Atlantique :</p><p><a href='https://44.kidiklik.fr/articles/335276-les-marches-de-noel-nantes-et-en-loire-atlantique.html' target='_blank'>Marchés de Noël de Loire-Atlantique</a></p>`; break;
    case 15: box.innerHTML+=`<h2>Jour 15<p><strong style='color:red;'>Info du Jour<p></strong></h2><p>Relamping du couloir du rez-de-chaussée :<p></strong> les néons ont été remplacés par des panneaux LED💡 Cette démarche s'inscrit dans la politique <strong>ÉcoFiP</strong> de la direction<p>une vraie action écologique : réduction de la consommation électrique et moins de déchets.</p>`; break;
    case 16: box.innerHTML+=`<h2>Jour 16</h2><p>Contenu à ajouter pour le jour 16.</p>`; break;
    case 17: box.innerHTML+=`<h2>Jour 17</h2><p><strong>Info :</strong> Concours des pulls de Noël le 15 décembre 🎅 ! Venez avec vos plus beaux pulls et gagnez vos chocolats 🍫 ! Nous prendrons une photo pour le vote final 📸.</p>`; break;
    case 18: box.innerHTML+=`<h2>Jour 18</h2><p>Contenu à ajouter pour le jour 18.</p>`; break;
    case 19: box.innerHTML+=`<h2>Jour 19</h2><p>🎉 Aujourd'hui, c'est la Journée mondiale du pull de Noël 🎄</p><p><strong style='color:red;'>Quiz :</strong> Savez-vous d'où vient la tradition du jour des pulls de Noël ?</p><form id='quiz19'><label><input type='radio' name='ans19' value='France'> France</label><br><label><input type='radio' name='ans19' value='Suisse'> Suisse</label><br><label><input type='radio' name='ans19' value='Angleterre'> Angleterre</label><br><button type='button' onclick='checkQuiz("quiz19","Angleterre","res19","info19")'>Valider</button></form><p id='res19'></p><p id='info19' style='display:none;'>La tradition trouve ses origines en Angleterre en 1980. Mais ce n’est que dans les années 2000 que le pull trouvera son succès grâce au film “Bridget Jones“.</p> <p>Rappel : Une photo peut être proposée dans les établissements, a la DiSI CO rendez-vous à 11h30 dans le hall des Marsauderies pour participer au concours des pulls de Noël 🎁 !</p> <hr>`;
      `;
  `;
    break;
    case 20: box.innerHTML+=`<h2>Jour 20</h2><p>Ce week-end, n'oubliez pas de vous réchauffer ☕</p><p><a href='https://www.marmiton.org/recettes/recette_vin-chaud-aux-epices_25224.aspx' target='_blank'>Recette du vin chaud aux épices</a></p>`; break;
    case 21: box.innerHTML+=`<h2>Jour 21</h2><p>En ce dimanche, n'oubliez pas de vous nourrir de bons repas chauds 🍲 :</p><p><a href='https://www.marmiton.org/recettes/recette_gratin-dauphinois_13809.aspx' target='_blank'>Recette du gratin dauphinois</a></p>`; break;
    case 22: box.innerHTML+=`<h2>Jour 22</h2><p>Contenu à ajouter pour le jour 22.</p>`; break;
    case 23: box.innerHTML+=`<h2>Jour 23</h2><p>Contenu à ajouter pour le jour 23.</p>`; break;
    case 24: box.innerHTML+=`<h2>Jour 24</h2><p>Contenu à ajouter pour le jour 24.</p>`; break;
  }
  document.getElementById('popup').style.display='block';
}
function closePopup(){ document.getElementById('popup').style.display='none'; }
function checkQuiz(formId, correct, resId, infoId){ const form=document.getElementById(formId); const selected=form?form.querySelector('input[type=radio]:checked'):null; const res=document.getElementById(resId); if(!res) return; if(!selected){ res.textContent='Sélectionnez une réponse !'; return; } if(selected.value===correct) res.textContent='Bonne réponse ! 👏'; else res.textContent=`Loupé ! La bonne réponse est ${correct}.`; if(infoId){ const el=document.getElementById(infoId); if(el) el.style.display='block'; }}
function checkOpenAnswer12(){ const v=document.getElementById('quiz12Input').value.trim(); const r=document.getElementById('quiz12Result'); if(!r) return; if(!v) { r.textContent='Veuillez entrer une réponse.'; return; } r.innerHTML='Réponse : une abeille ne produit qu\'1/12 de cuillère à café de miel, soit environ 7 grammes.';}
</script>

</body>
</html>
