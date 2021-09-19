<template>
    <v-row justify="center" class="ma-2" no-gutters>
        <v-col lg="8">
            <v-card flat width="100%" class="pa-3">
                <v-avatar color="primary white--text">JK</v-avatar>
                <span class="pa-3">Jonathan Kilner</span>
                <v-textarea v-model="text" auto-grow placeholder="Bora postar?" class="pa-3" height="1%"></v-textarea>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn @click="publish()">Publicar</v-btn>
                    <v-btn @click="cancel()">Cancelar</v-btn>
                </v-card-actions>
            </v-card>
        </v-col> 
    </v-row>
</template> 

<script>
export default {
    data() {
        return {
            text: ''
        }
    },
    methods: {
        publish() {
            if(this.text.trim() != "") {
                let publication = {
                    text: this.text,
                    name: "Jonathan Kilner"
                }
                // console.log("Adicionando " + this.text)
                this.$emit('publish', publication)
                this.text=''
            }
        },
        cancel(){
            this.text=''
        }
    }
}
</script>