<template>
  <div class="hello">
    <h1>Ayo kerjakan {{nama}}</h1>

    <p :style="'color: red'" v-if="poin < items.length-((items.length*3)/10)">Maaf, Anda Belum Lulus. Silahkan mengikuti Ujian Selanjutnya</p>
    <p :style="'color: green'" v-else>Selamat, Anda lulus</p>
    <p>{{ 'Poin Anda '+poin}}</p>

    <div v-for="(item,index) in items" :key="item.pertanyaan" :options="item.pertanyaan">
      <p>{{index+1}}. {{ item.pertanyaan}}</p>
      <div  v-for="pilih in item.pilihan" :key="pilih.pilihan" :options="pilih.pilihan">
        <input type="radio"  :name="'name'+index" 
         @click="checkJawaban(index,pilih.pilihan)" 
        :value="pilih.pilihan" >{{ pilih.pilihan }} 
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data: function(){
    return {
      nama: 'judzanhazimp',
      show: true,
      poin:0,
      jawabanbenar: [],
      items:[
      {
        name:'soal1',
        pertanyaan: 'Siapakah mentri kelautan ?',
        answer:String,
        check:true,
        pilihan:[
        { pilihan:'Susi Pudjiastuti' },
        { pilihan:'Hana' },
        { pilihan:'Rika'},
        { pilihan:'Semua jawaban benar' } ],
        jawaban:'Susi Pudjiastuti'
      },
      {
        pertanyaan: 'Siapakah calon presiden sekarang?',
        name:'soal2',
        check:true,
        answer:String,
        pilihan:[
        { pilihan:'jokowi dan Prabowo' },
        { pilihan:'Prabowo Sandi' },
        { pilihan:'Jokowi Maruf' },
        { pilihan:'Nomor urut 2 Jadi Presiden' }
        ],
        jawaban:'Nomor urut 2 Jadi Presiden'
      },
      {
        pertanyaan: 'SMKN4 Bandung terletak di negara?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'Indonesia' },
        { pilihan:'Jepang' },
        { pilihan:'Korea Selatan' },
        { pilihan:'China' }
        ],
        jawaban:'Indonesia'
      },
      {
        pertanyaan: 'Siapa nama pembalap F1 indonesia?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'Rio hariyanto ' },
        { pilihan:'Valentino rossi' },
        { pilihan:'Lionel messi' },
        { pilihan:'Cristiano ronaldo' }
        ],
        jawaban:'Rio hariyanto '
      },
      {
        pertanyaan: 'Ada berapa musim di indonesia?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'1' },
        { pilihan:'2' },
        { pilihan:'3' },
        { pilihan:'4' }
        ],
        jawaban:'2'
      }
      ]
    }
  },
  methods: {
    hideTitle () {
      this.show = !this.show
    },
    checkJawaban(i,jawab){

      if(this.items[i].jawaban === jawab){
        if(this.jawabanbenar.indexOf(i) == -1){
          this.poin++;
          this.jawabanbenar.push(i);
        }
      }
      if(this.items[i].jawaban !== jawab){
        if(this.jawabanbenar.indexOf(i) != -1){
          this.poin--;
          this.jawabanbenar.splice(this.jawabanbenar.indexOf(i), 1);
        }
      }

        this.items[i].check = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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