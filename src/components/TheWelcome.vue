<template>
  <div>
    <input 
      v-model="text"
      @input="onInput('helo')"
    >
    <!-- <br> -->
    <!-- {{ text }} -->
    <!-- <br> -->
    <!-- {{getParams}} -->
    <div v-for="(product, index) in products" :key="index">
      {{ product?.name }} - {{  index  }}
    </div>
    <div v-if="getParams">
      betul ini kucing
    </div>
    <!-- Manual -->
    <div key="1">Baso</div>
    <!-- Potensi Error -->
    <!-- Key itu Harus Unique -->
    <div key="2">Ikan</div>  
    <!--  -->
  </div>
</template>

<script>
const testText = 'Ini Variable dari Luar';
// document.getElementById('asdas').addEventListener('input', (value) => {
//   return value;
// });



/**
 * 
 * Case Vmodel saja
 * Ketika hanya ingin menampilkan Nilai-nya saja, tidak ada action tambahan
 * 
 * 
 * Terus ketika ingin memiliki action tambahan gimana ??
 * Evenlisterner Bawaan vue @input @change @click dll,
 * 
 */
export default {
  name: 'ThemeWelcome',
  data() {
    // vaRIABLE Yang dapat di ubah ubah
    return {
      text: 'Kucing',
      testText,
      products: [
        {
          name: 'Baso'
        },
        {
          name: 'Baso'
        },
      ],
    };
  },
  computed: {
    // Getter -> menampilkan data
    // Hanya Menampilkan saja tidak dapat di ubah secara paksa, assign
    getParams() {
      return this.text === 'Kucing';
    },
  },
  methods: {
    // Setter -> mengubah data
    onInput(event) {
      // console.log("🚀 ~ onInput ~ text:", text)
      console.log(event);

      // const target = event?.target?.value;
      // console.log("🚀 ~ oninput ~ target:", target)
    },
    getData() {
      const axios = {
        get: () => {}
      }
      axios.get('/halo', {}).then(res => {
        this.products = res?.data?.data; // pasti bisa karena data()
        this.getParams = true; // Ini pasti error karena computed
      })
    },
  },
}
</script>
