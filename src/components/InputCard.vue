<template>
    <b-container fluid>
        <b-row align-h="center">
            <b-col cols="12">
                <b-card class="shadow p-3 mb-5 bg-white rounded" border-variant="dark">
                    <b-row><label for="pseudoCode"><h5>Input</h5></label></b-row>
                    <b-row><b-form-textarea id="pseudoCode" 
                        v-model="pseudoCode" 
                        placeholder="Enter pseudoCode..." 
                        rows="7"></b-form-textarea>
                    </b-row>
                    <b-row align-h="end">
                        <b-button  variant="outline-primary" @click="Convert(pseudoCode)">Convert</b-button>
                    </b-row>
                </b-card>
            </b-col>
        </b-row>
        <b-row>
            <b-col cols="12">
                <b-card class="shadow p-3 mb-5 bg-white rounded" border-variant="dark">
                    <b-row><label for="expectedOutput"><h2>Expected Output</h2></label></b-row>
                    <b-row><b-form-textarea id="expectedOutput" 
                        v-model="expectedOutput" 
                        placeholder="Enter expected output..." 
                        rows="7"></b-form-textarea>
                        <p>At least 5 lines of input required.</p>
                    </b-row>
                    <b-row align-h="end">
                        <b-button  variant="outline-primary" :disabled="spinner" @click="Score(expectedOutput)">Score</b-button>
                    </b-row>
                </b-card>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
export default {
    name: 'InputCard',
    props: ['spinner'],
    data() {
            return {
                pseudoCode:'',
                expectedOutput:''
            }
        },
    methods: {
        Convert(pseudoCode){
            this.$emit('Convert',pseudoCode);
        },
        Score(expectedOutput){
            this.$emit('Score', expectedOutput);
        }
    }
}
</script>
<style scoped>
button {
    margin-top: 10px;
}
p {
    margin-bottom: 0;
}
</style>