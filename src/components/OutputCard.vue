<template>
    <b-container fluid>
        <b-row align-h="center">
            <b-col cols="12">
                <b-card class="shadow p-3 mb-5 bg-white rounded" border-variant="secondary">
                     <b-row><h3 class="output" v-if="outputText">Output...</h3></b-row>
                    <div class="text-center" v-if="spinner">
                        <b-spinner style="width: 3rem; height: 3rem;" label="Large Spinner" variant="primary"></b-spinner>
                    </div>
                    <div v-if="!spinner">
                    <b-list-group class="mb-3" v-for="(lines, index) in sourceCode.data" :key="index">
                        <b-row><p class="output">Output {{ index }} :</p></b-row>
                        <b-list-group-item class="list-item" v-for="line in lines" :key="line">{{ line }}</b-list-group-item>
                        <div v-if="displayScore">
                        <p>{{ score.data.score[index] }}</p>
                        </div>
                    </b-list-group>
                    </div>
                </b-card>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
export default {
    name: 'OutputCard',
    props: ['sourceCode','spinner', 'score', 'displayScore', 'outputText']
}
</script>
<style scoped>
p {
    text-align: right;
}
.output {
    text-align: left;;
}
.list-item {
    text-align: left;
}
</style>