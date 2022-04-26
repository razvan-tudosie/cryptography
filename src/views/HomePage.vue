<template>
    <h1>Home Page</h1>

    <div class="container">
        <h1>This is a simple page</h1>

        <form @submit.prevent="onSubmit">
            <textarea name="inputText" id="" cols="100" rows="20" v-model="myText"></textarea>
            <br>
            <button type="submit">Submit</button>
        </form>

        <table class="table">
            <thead>
                <tr>
                    <th>Litera</th>
                    <th>Frecventa</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(result, index) in frequencyInfo" :key="result" >
                    <td>{{ index }}</td>
                    <td>{{ result }}</td> 
                </tr>
            </tbody>
        </table>
        <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import {ref} from 'vue'

export default {
    name: 'HomePage',
    components: {
    // HelloWorld
    },

    setup () {
        let myText = ref('');
        let frequencyInfo = ref([]);
        let probAp = ref([]);

        function onSubmit() {
            getFrequency(myText.value);
            console.log('here', frequencyInfo.value);
        }

        // To RESOLV..this is not ok
        function probOfAp(fregChar) {
            var prob = {};
            // de scazut spatiile din texte
            var calc = fregChar / myText.value.length;
            probAp.value = prob;
            
            console.log('calcul', calc);
            console.log('prob', prob);
        
        }

        function getFrequency(string) {
            var freq = {};
            for (var i = 0; i < string.length; i++) {
                var character = string.charAt(i);
                if (freq[character]) {
                    freq[character]++;
                } else {
                    freq[character] = 1;
                }
                // probOfAp(freq[character]);
            }

            frequencyInfo.value = freq;
        }

        return {
            myText,
            frequencyInfo,
            onSubmit,
            probOfAp
        };
    }
}
</script>
