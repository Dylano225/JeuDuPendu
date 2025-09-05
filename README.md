# JeuDuPendu
Just the game of hanged

<!DOCTYPE html>

<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <title>Jeu du pendu</title>
</head>
<body>
  
  <div class="formulaire">
    
  <h2>Bienvenue dans le jeu du pendu en js</h2>
  <p>Ici vous devrez entrez le mot exact</p>
  <p>Mot: <span id="mot">**********</span></p>
  <p>Nombre de vies: <span id="nb_vies">7</span></p>
    
    <form id="form">
  <input type="text" placeholder="Veuiller entrez une lettre" id="letter">
  <input type="submit">
    </form>
    <p id="message"></p>
    
  </div>
  
</body>

<script>

const mot_mystere = "javascript";
const mot_visible = Array(mot_mystere.length).fill("*");
let nb_vies = 7

console.log(mot_visible)

const formulaire = document.querySelector("#form");
const mot = document.querySelector("#mot");
const life = document.querySelector("#nb_vies");
const letter = document.querySelector("#letter");
const mes = document.querySelector("#message");

formulaire.addEventListener("submit",(e)=>{
  e.preventDefault()
  const lettre = letter.value.toLowerCase()
  letter.value = "";
  
  if (mot_mystere.includes(lettre)){
    for (let i = 0; i < mot_mystere.length; i++){
      if (mot_mystere[i] === lettre){
        mot_visible[i] = lettre
      }
    } 
    mes.textContent = "✅Bravo, bien joué"
  } else {
    nb_vies--;
    mes.textContent = "❌ Oups perdu"
  }
  
  if (lettre === "" || lettre.length !== 1 || !/[a-zA-Z]/.test(lettre)){
    e.stopPropagation();
    e.preventDefault();
    mes.textContent = "❌ Veuillez entrer une lettre valide"
  } 
  
  
  mot.textContent = mot_visible.join("");
  life.textContent = nb_vies
  
  if (mot_mystere === mot_visible.join("")){
    mes.textContent = "🎉 Felicitation, vous avez gagné, le mot est " + mot_mystere;
    formulaire.querySelector("input[type='submit']").disabled = true
  }
  
  else if (nb_vies === 0){
    mes.textContent = "💀 Dommage, vous avez perdu, le mot était" + mot_mystere;
    formulaire.querySelector("input[type='submit']").disabled = true
  }
})



</script>

<style>

*{
  font-family: "Poppins"
}

input[type="text"],
input[type="submit"]{
  padding: 8px 12px;
}
 
</style>

</html>

