<template>

    
  <div>
    <h3> NT2 - Parcial - Quintieri Mariano</h3>
    <input type="text" v-model="textInput" />
    <p>Cantidad de Caracteres = {{ charCount }}</p>
    <p>1 - {{ encodedText }} (Codificado)</p>
    <p>2 - {{ upperText }} (Mayuscula) </p>
    <p>3 - {{ lowerText }} (Minuscula) </p>
    <p>4 - {{ intercalatedText1 }} (Mayuscula / Minuscula) </p>
    <p>5 - {{ intercalatedText2 }} (Minuscula / Mayuscula) </p>
    
  </div>
</template>

<script>

export default {
  data() {
    return {
      textInput: ''
    }
  },
  computed: {
    encodedText() {
      return this.textInput.toLowerCase().replace(/[aeiou]/g, c => {
        switch(c) {
          case 'a': return 'u';
          case 'e': return 'o';
          case 'i': return 'i';
          case 'o': return 'e';
          case 'u': return 'a';
        }
      });
    },
    upperText() {
      return this.textInput.toUpperCase();
    },
    lowerText() {
      return this.textInput.toLowerCase();
    },
    intercalatedText1() {
      return this.intercalate(this.textInput, true);
    },
    intercalatedText2() {
      return this.intercalate(this.textInput, false);
    },
    charCount() {
      return this.textInput.length;
    }
  },
  methods: {
    intercalate(text, startWithUpper) {
      return text.split('').map((c, i) => {
        return (i % 2 === 0) === startWithUpper ? c.toUpperCase() : c.toLowerCase();
      }).join('');
    }
  }
}
</script>

