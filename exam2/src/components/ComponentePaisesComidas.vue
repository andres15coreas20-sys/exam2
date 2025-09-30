<template>
  <div class="card">
    <h1>Países y sus comidas típicas</h1>

    <section v-for="country in countries" :key="country.code" class="country">
      <h2>{{ country.name }}</h2>
      <p>Plato típico: <strong>{{ country.dish }}</strong></p>
    </section>

    <h2>Tabla de precios (local y en USD)</h2>
    <table>
      <thead>
        <tr>
          <th>Plato</th>
          <th>País</th>
          <th>Precio (local)</th>
          <th>Precio (USD)</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <td>{{ item.name }}</td>
          <td>{{ item.country }}</td>
          <td>{{ formatLocal(item.price, item.currency) }}</td>
          <td>{{ formatUSD(convertToUSD(item.price, item.currency)) }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'ComponentePaisesComidas',
  data() {
    return {
      // Datos de ejemplo: 4 países con su plato típico
      countries: [
        { code: 'MX', name: 'México', dish: 'Tacos' },
        { code: 'JP', name: 'Japón', dish: 'Sushi' },
        { code: 'IT', name: 'Italia', dish: 'Pizza' },
        { code: 'AR', name: 'Argentina', dish: 'Asado' }
      ],

      // Lista para la tabla: nombre del plato, país, precio en moneda local
      items: [
        { id: 1, name: 'Tacos al pastor', country: 'México', price: 120, currency: 'MXN' },
        { id: 2, name: 'Sushi mixto', country: 'Japón', price: 1500, currency: 'JPY' },
        { id: 3, name: 'Porción de pizza', country: 'Italia', price: 8, currency: 'EUR' },
        { id: 4, name: 'Porción de asado', country: 'Argentina', price: 3000, currency: 'ARS' }
      ],

      // Tasas de conversión a USD (valores de ejemplo, fijos)
      ratesToUSD: {
        MXN: 0.056, // 1 MXN = 0.056 USD
        JPY: 0.0067,
        EUR: 1.07,
        ARS: 0.0033
      }
    }
  },
  methods: {
    convertToUSD(amount, currency) {
      const rate = this.ratesToUSD[currency] || 1
      return +(amount * rate).toFixed(2)
    },
    formatLocal(amount, currency) {
      // Formatea una cantidad con la moneda local simple
      return `${amount} ${currency}`
    },
    formatUSD(amount) {
      return `$ ${amount}`
    }
  }
}
</script>

<style scoped>
.card {
  max-width: 700px;
  margin: 16px auto;
  padding: 16px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
}
.country { margin-bottom: 8px }
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 8px;
}
th, td {
  border: 1px solid #ccc;
  padding: 8px;
  text-align: left;
}
th { background: #f7f7f7 }
</style>
