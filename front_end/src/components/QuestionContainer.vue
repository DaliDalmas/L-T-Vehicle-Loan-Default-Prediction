<template>
<div fluid>
  <v-container class="question-container"  color="#114856" >
    <v-row class="text-center question-block" v-if="(index>=0)">
      <v-col cols="12">

      </v-col>
      <v-col class="mb-4 text-left" color="#114856">
        <p class="subheading font-weight-regular">
            {{questions[index].question}} <br/>
            --{{questions[index].asnwer_type}}-- <br/>
        </p>
        <p v-if="this.index == this.question_len-1">last question</p>

        <v-textarea
            name="input-7-1"
            filled
            label="text answer"
            auto-grow
            dark
            value=""
            class="my-textarea"
            v-if="questions[index].asnwer_type=='text'"
            v-model="answer"
        ></v-textarea>

        <v-text-field
        v-model="answer"
        dark
        class="my-textfield"
        v-if="questions[index].asnwer_type=='float' ||
              questions[index].asnwer_type=='integer'"
        ></v-text-field>

        <v-date-picker 
        dark
        v-model="picker"
        v-if="questions[index].asnwer_type=='date'"></v-date-picker>

        <v-container fluid v-if="questions[index].asnwer_type=='bool'">
            <v-radio-group
            v-model="answer"
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
                <v-icon
                v-if="this.index != this.question_len-1"
                dark>
                    mdi-skip-next
                </v-icon>
                <v-icon
                v-if="this.index == this.question_len-1"
                dark>
                    mdi-send
                </v-icon>
            </v-btn>
        </v-row>
      </v-col>
      
    </v-row>
  </v-container>
</div>
</template>

<script>
import axios from "axios";
export default {
    name: 'QuestionContainer',
    props:['questions', 'question_len'],
    created() {
    this.answers = this.questions
  },
    data:()=>({
        answer:null,
        // answers:this.questions,
        index:0,
      picker: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
    }),
    methods:{
        goBack: function(){
            if (this.index>0){
                this.index-=1
                this.answer = this.answers[this.index]['answer']
            }
        },
        goForward: function(){
            if (this.index < this.question_len-1){
                if(this.answers[this.index]['asnwer_type']=='date'){
                    this.answer = this.picker
                }
                this.answers[this.index]['answer'] = this.answer
                this.index+=1
                this.answer = this.answers[this.index]['answer'] || null
            }else{
                console.log(this.answers)
                axios
                .post('url', this.answers)
                .then((response)=>(
                    this.data=response.data
                ))
            }
        },      
    }
}
</script>

<style scoped>
.my-textfield textfield{
    color:#f0f8ff !important
}
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