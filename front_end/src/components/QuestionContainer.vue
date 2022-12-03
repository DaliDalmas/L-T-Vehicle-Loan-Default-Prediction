<template>
<div>
  <v-container class="question-container"  color="#114856" >
    <v-row class="text-center question-block" v-if="(index>=0)">
      <v-col cols="12">

      </v-col>
      <v-col class="mb-4 text-left" color="#114856">
        <p class="subheading font-weight-regular">
            {{questions[index].question}}
            {{len}}
        </p>
    
        <v-textarea
        name="input-7-1"
        filled
        label="text answer"
        auto-grow
        dark
        value=""
        class="my-textarea"
        ></v-textarea>
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
    props:['questions', 'len'],
    data:()=>({
        index:0
    }),
    methods:{
        goBack: function(){
            this.index-=1
            console.log(this.len)
        },
        goForward: function(){
            this.index+=1
            
        },      
    }
}
</script>

<style>
.my-textarea textarea { 
    color:#f0f8ff !important
}
.answer{
    height: 90%;
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
</style>