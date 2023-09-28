<template>
    <v-container>
      <div class="container">
        <div class="left-content">
          <h2>Sobre mí</h2>
          <img class="fotoMi" src="Foto.jpeg">
          <br>
          <br>
          <p>Mi nombre es Paulina Muñoz Saldarriaga, tengo 19 años, soy estudiante de ingenieria de sistemas
            con muchas ganas de aprender sobre el desarrollo de aplicaciones web.
  
            A lo largo del desarrollo del proyecto, he trabajado arduamente en su diseño y construcción. Mi ética de 
            trabajo y actitud positiva son cualidades que me definen y me han ayudado a destacar tanto en el aula como 
            en el equipo de desarrollo.
            
            Estoy emocionada por lo que el futuro tiene reservado para mí en el campo de la ingeniería de sistemas y el desarrollo 
            de aplicaciones web.
          </p>
          <br>
          <h4>Creadora del proyecto</h4>
        </div>
      <div class="right-content">
        <h2>Marvel</h2>
        <br>
        <p>El API de Marvel Comics, desarrollado por Marvel Entertainment, es una interfaz de programación de aplicaciones
           (API) que proporciona acceso a una vasta cantidad de datos relacionados con los personajes, cómics, series y 
           eventos del universo de Marvel Comics. Esta API permite a desarrolladores y entusiastas acceder y utilizar
            información detallada sobre el extenso mundo de Marvel para crear aplicaciones, sitios web y servicios 
            relacionados con estos populares personajes y sus historias.</p>
        <br>
        <p>Esta pagina es una entrega para desarrollo web que consiste en consumir esta API de marvel comics
          para mostrar detalles sobre 
          
        </p>
        <br>
        <br>
        <v-btn color="#5868a4" type="submit" class="btnClick" to="/personajes">Click para visualizar</v-btn>
      </div>
      </div>
    </v-container>
  </template>
  
  <style scoped>
  .container {
    display: flex;
    justify-content: space-between; /* Espacio entre las divisiones */
    
  }
  
  .fotoMi{
    border-radius: 50% !important;
    width: 150px;
    height: 150px;
    overflow: hidden;
  }
  
  .left-content, .right-content {
    width: 50%; /* Cada división ocupa el 50% del contenedor */
    padding: 20px;
    text-align: center;
    justify-content: center; 
    
  }
  
  .left-content {
    justify-content: center;
    align-items: center;
   
  }
  
  .right-content {
  
    border-left:3px solid #5868a4;
  }
  
  
  
  </style>