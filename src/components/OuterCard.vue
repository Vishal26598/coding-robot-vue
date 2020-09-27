<template>
    <b-container fluid>
        <b-row align-h="center">
            <b-col cols="12">
                <b-card class="shadow p-3 mb-5 bg-white rounded" border-variant="primary">
                    <b-row>
                        <b-col md="12" lg="6">
                            <InputCard @Convert="Convert" @Score="Score" :spinner="spinner"></InputCard>
                        </b-col>
                        <b-col md="12" lg="6">
                            <OutputCard :sourceCode="sourceCode" :outputText="outputText" :displayScore="displayScore" :score="score" :spinner="spinner"></OutputCard>
                        </b-col>
                    </b-row>
                </b-card>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
import InputCard from '@/components/InputCard.vue'
import OutputCard from '@/components/OutputCard.vue'
import axios from 'axios'
export default {
    name: 'OuterCard',
    data(){
        return{
            sourceCode:"",
            spinner: false,
            score:"",
            displayScore: false,
            outputText: true
        }
    },
    components: {
        InputCard,
        OutputCard
    },
    methods: {
        async Convert(pseudoCode){
            this.outputText = true;
            this.spinner=!this.spinner;
            this.displayScore=false;
            var data = {"pseudoCode":pseudoCode};
            this.sourceCode = await axios.post('/decode',data);
            this.spinner=!this.spinner;
            this.outputText=false;
            console.log(Object.keys(this.sourceCode.data).length, this.sourceCode);
        },
        async Score(expectedOutput){
            var data = {"expectedCode":expectedOutput};
            this.score = await axios.post('/score',data);
            this.displayScore = true;
            console.log(this.score.data);
        }
    }
}
</script>
