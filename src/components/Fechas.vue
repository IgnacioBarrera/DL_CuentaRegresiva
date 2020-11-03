<template>
  <div >
    <h1>Cuenta Regresiva</h1>
    <div>
      <h4>{{tiempoAtras(tiempo)}}</h4>
    </div>
    <div>
      <button @click="CuentaRegresiva(tiempos[0])">3S</button>
      <button @click="CuentaRegresiva(tiempos[1])">1m</button>
      <button @click="CuentaRegresiva(tiempos[2])">5m</button>
      <button @click="CuentaRegresiva(tiempos[3])">10m</button>
      <button @click="CuentaRegresiva(tiempos[4])">30m</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Fechas',
  data() {
    return {
      tiempo: 0,
      tiempos: [3,60,300,600,1800],
      resultado: "",
      intervalo: '',
      estado: {activo: false, boton: 'Iniciar'},
    }
  },
  methods: {
    tiempoAtras(tiempo) {
      let minutos = ('0' + Math.floor(tiempo/60)).slice(-2);
      let segundos = ('0' + tiempo%60).slice(-2);
      return `${minutos}:${segundos} min/seg`
    },
    CuentaRegresiva(cuenta){
      this.tiempo = cuenta;
      this.estado.activo = true;
      this.intervalo = setInterval(() => {
        if (this.tiempo > 0){
          this.tiempo --;
        } else {
          clearInterval(this.intervalo)
        }
      },1000);
    }
  }
}
</script>

<style scoped>

</style>
