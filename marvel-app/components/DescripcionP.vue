<template>
    <v-card class="informacion">
        <v-row>
            <v-col cols="4">
                <v-img  aspect-ratio="2/4" class="imagenDescr" cover
                    :src="personaje.thumbnail.path + '.' + personaje.thumbnail.extension"></v-img>
            </v-col>
            <v-col cols="6" style="text-align: center;">
                <v-row>
                    <v-col>
                        <br>
                        <p>  
                        <h3>{{ personaje.description || 'La descripción de este personaje no está disponible' }}</h3>
                        </p>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <v-card class="info" >
                            <ul>
                                <li class="li"> {{personaje.name}} tiene {{ personaje.series.available }} series, entre estas :</li> <br>
                                <v-row text-align="center" color="#000" v-for=" (serie, index) in personaje.series.items" :key="index"> 
                                    <v-col cols="12" v-if="index < 3">
                                        <h4 class="li">  {{ index + 1 }} - {{ serie.name }}</h4>
                                    </v-col>
                                </v-row>
                                <br>
                                <li class="li"> {{ personaje.name }} Tiene  {{ personaje.comics.available }} comics </li> <br>
                                <li class="li"> {{personaje.name}} tiene {{ personaje.stories.available }} historias </li> <br>
                                <li class="li"> {{ personaje.name }} tiene {{ personaje.events.available }} eventos </li>
                            </ul>
                        </v-card>
                    </v-col>
                </v-row>
            </v-col>
            
        </v-row>
    </v-card>
</template>
<script>
export default {
    props: {
        personaje: Object
    }
}

</script>
<style>

    body{
        overflow-y: hidden;
    }

    .imagenDescr{
        width: 500px !important; /* Ancho de la imagen */
        height: 500px !important; /* Altura de la imagen */
        border-radius: 100%; /* Hace que la imagen sea circular */
    }

    .info{
        background-color: "white" !important;
        color: "black" !important;
        display: flex !important;
        align-items: center !important;
        justify-content: center !important;
        flex-direction: column !important;
        font-weight: bold !important;
    }

    .nombre{
        font-family:sans-serif !important;
        font-weight: bold !important;
        text-align: center !important;
    }

    .informacion{
        height: 1000px;
        width: 1000px;
        display: flex !important;
        align-items: center !important;
        justify-content: center !important;
        flex-direction: column !important;
    

    }
</style>
