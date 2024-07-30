<template>
  <div class="hello">
  <form @submit="pesquisa">
    
  <input type="" name="" v-model="mainSearch" placeholder= "Digite sua pesquisa e adicione os filtros necessários" class="mainInput">

  <div> Antes de:
  <input  v-model="yearBefore"/>
    

  </div>
  <div > Depois de:
  <input  v-model="yearAfter"/>
    

  
</div>
  <div> Tipo de arquivo:
  <select v-model="fileType">

  <option value="">selecione</option>
  <option value="filetype%3Apdf">pdf</option>
  <option value="filetype%3Adoc">doc</option>
  <option value="filetype%3Axls">xls</option>
  <option value="filetype%3Appt">ppt</option>
  <option value="filetype%3Atxt">txt</option>
    
  </select>
  </div>
  
  

  <button type="submit">PESQUISAR</button>
  </form>

  </div>
</template>

<script>


export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      mainSearch: "",
      fileType:"",
      yearAfter : "",
      yearBefore: "",


    }
  },
   computed: {
    paramAfter() {
      return this.yearAfter ? `after%3A${this.yearAfter}` : '';
    },
    paramBefore() {
      return this.yearBefore ? `before%3A${this.yearBefore}` : '';
    }
  },
    methods: {
    pesquisa() {
      const searchTerms = this.mainSearch.trim().replace(/\s+/g, '+');
      const atributos = [this.fileType, this.paramAfter, this.paramBefore].filter(e => e);
      const searchQuery = [searchTerms, ...atributos].filter(Boolean).join('+');
      window.open(`https://google.com/search?q=${searchQuery}`, '_blank');
      this.mainSearch = "";
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

input, select {
  padding: 1em;
  border: none;
  border-radius: 5px;

}

.mainInput {
    min-width: 30vw;
}
input:focus {
 outline:none
}
.hello {
  background-color: #000000;
  padding:1em;
  border-radius: 10px;

}
.hello form {
  display:flex;
  flex-direction:column;
  gap:1em;
  color: white;
  text-align: left;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
