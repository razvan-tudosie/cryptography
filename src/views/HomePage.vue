<template>
    <h1>Home Page</h1>

    <div class="container">
        <h1>This is a simple page</h1>

        <form @submit.prevent="onSubmit">
            <textarea name="inputText" id="" cols="100" rows="20" v-model="myText"></textarea>
            <br>
            <button type="submit">Submit</button>
        </form>

        <table>
            <thead>
                <tr>
                    <th>Litera</th>
                    <th>Frecventa</th>
                </tr>
            </thead>

            <tr v-for="(test, index) in frequencyInfo" v-bind:key="test.value" >
                <td>{{ index }}</td>
                <td>{{ test }}</td>
            </tr>
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

        function onSubmit() {
            //  console.log(myText.value);
            getFrequency(myText.value);
            console.log(frequencyInfo.value);
            
        }

        function getFrequency(string) {
            var freq = {};
            for (var i=0; i<string.length;i++) {
                var character = string.charAt(i);
                if (freq[character]) {
                freq[character]++;
                } else {
                freq[character] = 1;
                }
            }

            frequencyInfo.value = freq;
            // return freq;
            // console.log(freq);
        }

        return {
            myText,
            frequencyInfo,
            onSubmit,
            getFrequency
        };
    }
}
</script>
