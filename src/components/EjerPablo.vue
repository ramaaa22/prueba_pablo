<template>
    <div class="grid-auto-columns: auto;">
        <el-alert 
            v-show="msj_alerta"
            title="Se ha superado el máximo permitido"
            type="info"
            show-icon>
        </el-alert>
        <div class="grid-auto-columns: auto;" @click="agregar">
            <p><el-button @click="cambiar" v-if="contador < cantidad && boton">Click para mostrar</el-button></p>
            <p><el-button @click="volver" v-show="!boton">Click para ocultar</el-button></p>
        </div>	
        <div class="grid-auto-columns: auto;" @click="alerta" v-show="contador == cantidad">
            <p><el-button>Click para mostrar</el-button></p>
        </div>
        <div class="grid-auto-columns: auto;">
            <template>
                <h3>Cantidad elegida</h3>
                <input type="number" v-model="cantidad">
            </template>
            <template v-if="contador < cantidad">
                <p class="text-center">
                    Veces clickeado: {{ contador }}
                </p>
            </template>
            <template v-if="contador < (cantidad+1) && bienvenido">
                <p class="text-center">Bienvenidos al curso</p>
            </template>
            <template v-else-if="contador > (cantidad-1)">
                <p class="text-center">Has superado el número de clicks permitido</p>
                <p><el-button @click="reiniciar">Reiniciar contador</el-button></p>
            </template>
        </div>
    </div>	
</template>
<script>
export default {
    data:()=>({
        texto: "Click para mostrar",
        msj_alerta: false,
        contador: 0,
        cantidad: 10,
        boton: true,
        bienvenido: false
	}),
	methods: {
		agregar(){
			this.contador += 1
		},
		cambiar(){
			this.boton = false,
			this.bienvenido = true
        },
        change(){
            this.boton=!this.boton;
            this.bienvenido=!this.bienvenido;
        },
		volver(){
			this.boton = true,
			this.bienvenido = false
		},
		reiniciar(){
			this.contador = 0,
			this.boton = true,
			this.bienvenido = false,
			this.msj_alerta = false,
			this.cantidad = 10
		},
		alerta(){
			this.msj_alerta = true
		}
	}
}

/*   COMENTARIOS
    Notar que los métodos cambiar() y volver() tienen la misma lógica pero
    a la inversa. Podría ser un único método que hiciera:
        change(){
            this.boton=!this.boton;
            this.bienvenido=!this.bienvenido;
        }
    Respecto a los botones, lo que se puede hacer para simplificar código, es hacer uso
    del operador ternario.

    <el-button @click="click">
            {{show? "Click para ocultar" : "Click para mostrar"}}
    </el-button>

    Evalúa la variable "show", que es un booleano que puede tomar valor true o false
    Si es true, mostrará el primer argumento ("Click para ocultar"), y si es false, 
    mostrará lo que sigue a los dos puntos (":"), que en ese caso es "Click para mostrar"

    Otro punto a tener en cuenta es el nombre de las variables: por convención

*/   

</script>


