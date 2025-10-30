<template>
    <div class="container-fluid my-3 border-bottom pb-3">
        <h1>Conversor de Temperaturas</h1>
    </div>
    <div class="container-fluid mt-3 " id="app">
        <div class="d-flex align-items-center">
            <p class="mb-0 me-3">Ingresa Temperatura en °C</p>
            <input type="number" class="form-control" id="entradaTemperatura" v-model="temperaturaCelsius"
                placeholder="Ingresa una temperatura en Celsius...">
        </div>
    </div>
    <div class=" container-fluid mt-3">
        <div class="d-flex align-items-center">
            <span class="me-3">Conv Temperatura °F:</span>
            <p class="mb-0 fw-semibold" :style="estiloTemperaturas">{{ convertirTemperaturas.temperaturaFahrenheit }}</p>
        </div>
        <div class="d-flex align-items-center mt-2">
            <span class="me-3">Conv Temperatura °K:</span>
            <p class="mb-0 fw-semibold" :style="estiloTemperaturas">{{ convertirTemperaturas.temperaturaKelvin }}</p>
        </div>
    </div>
    <div id="respuestas">
            Respuestas:
        <ul>
            <li>1- C</li>
            <li>2- C</li>
            <li>3- A</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Temperatura',
    data() {
        return {
            temperaturaCelsius: '',
            temperaturaFahrenheit: '',
            temperaturaKelvin: ''
        }
    },
    methods: {
        
    },
    computed: {
        convertirTemperaturas() {
            const celsius = parseFloat(this.temperaturaCelsius);

            if (!isNaN(celsius)) {
                this.temperaturaFahrenheit = (celsius * 9 / 5) + 32;
                this.temperaturaKelvin = celsius + 273.15;
            } else {
                this.temperaturaFahrenheit = '';
                this.temperaturaKelvin = '';
            }

            return {
                temperaturaFahrenheit: this.temperaturaFahrenheit,
                temperaturaKelvin: this.temperaturaKelvin
            }
        },

        estiloTemperaturas() {
            if (this.temperaturaCelsius <= 0) {
                return 'color: blue;';
            } else if (this.temperaturaCelsius > 0 && this.temperaturaCelsius < 15) {
                return 'color: magenta;';
            } else {
                return 'color: red;';
            }
        }
    }
}
</script>

<style>
#respuestas {
    margin-top: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-weight: bolder;
}

#entradaTemperatura {
    width: 700px;
}
</style>