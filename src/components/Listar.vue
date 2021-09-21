<template>
    <div>
        <div >
            <input 
            type="checkbox"
            v-click="filterFieldInactive = 0"
            v-model="filterFieldActive">
            <v-card>
                <v-card-title>
                Nutrition
                <v-spacer></v-spacer>
                <v-text-field
                    
                    append-icon="mdi-magnify"
                    label="Search"
                    single-line
                    hide-details
                ></v-text-field>
                </v-card-title>
                <v-data-table
                :headers="headers"
                :items="peliculas"
                :search="search"
                ></v-data-table>
            </v-card>
            
        </div>
    </div>
</template>
<script>
  export default {
        data(){
            return{
                peliculas:[],
                search: '',
                headers: [
                { text: 'imagen', value: 'imagen' },
                { text: 'Título', value: 'Título' },
                { text: 'Descripción', value: 'Descripción' },
                { text: 'Duración', value: 'Duración' },
                { text: 'categoria', value: 'categoria' },
                { text: 'Trailer_youtube', value: 'Trailer_youtube' },
                { text: 'Fecha_estreno', value: 'Fecha_estreno' },
                { text: 'visualizacion', value: 'visualizacion' },
                { text: 'calificacion', value: 'calificacion' },
                ],
            }
        },
        
        created:function(){
            this.consultarEmpleados()
        },
        methods:{
        
        consultarEmpleados(){
            fetch('http://localhost:9000/api')
            .then(respuesta=>respuesta.json())
            .then((datosRespuesta)=>{
                console.log(datosRespuesta)
                this.peliculas=[]
                if(typeof datosRespuesta[0].success==='undefined')
                {
                    this.peliculas=datosRespuesta;
                }
                
            })
            .catch(console.log())
        },
        
        
        }
      }
    
  
</script>
