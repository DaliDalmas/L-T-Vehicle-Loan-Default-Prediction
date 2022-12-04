<template>
<div fluid>
  <v-container class="question-container"  color="#114856" >
    <v-row class="text-center question-block" v-if="(index>=0)">
      <v-col cols="12">

      </v-col>
      <v-col class="mb-4 text-left" color="#114856">
        <p class="subheading font-weight-regular">
            {{questions[index].question}} <br/>
            --{{questions[index].asnwer_type}}--

        </p>
    
        <v-textarea
        name="input-7-1"
        filled
        label="text answer"
        auto-grow
        dark
        value=""
        class="my-textarea"
        v-if="questions[index].asnwer_type=='text'"
        :answer="answer"
        ></v-textarea>

        <v-text-field
        :rules="rules"
        v-if="questions[index].asnwer_type=='float' ||
              questions[index].asnwer_type=='integer'"></v-text-field>

        <v-date-picker 
        dark
        v-model="picker"
        v-if="questions[index].asnwer_type=='date'"></v-date-picker>

        <v-container fluid v-if="questions[index].asnwer_type=='bool'">
            <p>{{ radios || 'null' }}</p>
            <v-radio-group
            v-model="radios"
            mandatory
            >
            <v-radio
                label="Yes"
                value=True
                color="white"
                class="white--text"
            ></v-radio>
            <v-radio
                label="No"
                value=False
                color="white"
                class="white--text"
            ></v-radio>
            </v-radio-group>
        </v-container>

        <v-row>
            <v-btn
            class="mx-1"
            fab
            dark
            color="#561F11"
            @click="goBack"
            >
                <v-icon dark>
                    mdi-skip-previous
                </v-icon>
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn
            class="mx-1"
            fab
            dark
            color="#561F11"
            @click="goForward"
            >
                <v-icon dark>
                    mdi-skip-next
            </v-icon>
            </v-btn>
        </v-row>
      </v-col>
      
    </v-row>
  </v-container>
</div>
</template>

<script>
export default {
    name: 'QuestionContainer',
    props:['questions', 'question_len'],
//     created() {
//     console.log(this.question_len)
//   },
    data:()=>({
        index:0,
        rules: [
        value => !!value || 'Required.',
        value => (value || '').length <= 20 || 'Max 20 characters',
      ],
      picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
      radios: null
    }),
    methods:{
        goBack: function(){
            if (this.index>0){
                this.index-=1
            }
            console.log(this.index)

        },
        goForward: function(){
            if (this.index < this.question_len-1){
                this.index+=1
            }
            console.log(this.index)
            console.log(this.question_len)
        },      
    }
}
</script>

<style scoped>
.my-textarea textarea { 
    color:#f0f8ff !important

}
.answer{
    height: 60%;
    color: aliceblue;
}
.question-block{
    background: #114856;
    border-radius: 25px;
    padding: 15px;
}
.question-container{
    color: aliceblue;
    height: 50%;
    width: 60%;
}
.white--text /deep/ label {
    color: white;
}
</style>