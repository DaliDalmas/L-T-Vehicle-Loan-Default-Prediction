<template>
  <v-container class="question_background"  color="#114856">
    <v-row class="text-center">
      <v-col cols="12">
       
      </v-col>

      <v-col class="mb-4 text-left" color="#114856">
        <p class="subheading font-weight-regular">
          This is the question this is the question this is the question.
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
            >
                <v-icon dark>
                    mdi-skip-next
            </v-icon>
            </v-btn>
        </v-row>
      </v-col>

    </v-row>
  </v-container>
</template>

<script>
export default {
    name: 'HelloWorld',
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
.question_background{
    background: #114856;
    color: aliceblue;
    height: 50%;
    width: 60%;
    padding: 3%;
    border-radius: 25px;
}
</style>