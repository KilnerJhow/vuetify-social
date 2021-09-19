<template>
  <v-app>
    <v-main class="grey lighten-4">
      <tool-bar />
      
      <add-publication @publish="addContent($event)"/>
      <div v-for="(publication, index) in publications" :key="index">
        <publications 
          :publicationProp="publication" 
          :index="index" 
          @change-content="changeContent($event)"
          @remove-content="removeContent($event)"/>
      </div>
    </v-main>
  </v-app>
</template>

<script>
import ToolBar from './components/ToolBar.vue';
import Publications from './components/Publications.vue'
import AddPublication from './components/AddPublication.vue'

export default {
  name: 'App',

  // computed: {
  //   reversePublication() {
  //     let arr = this.publications
  //     return arr.reverse()
  //   }
  // },

  components: {
    ToolBar,
    Publications,
    AddPublication
  },

  data () {
    return{
      publications: [
        {
          text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi vitae eleifend nibh. Donec volutpat tellus vel maximus scelerisque. Curabitur mattis odio lectus, non lacinia nisl imperdiet a. Pellentesque consectetur sapien lorem, id porta purus luctus nec. Aliquam sodales risus at lobortis dignissim. Mauris consectetur consectetur leo varius dictum. Sed euismod massa et arcu interdum interdum. Nulla ac sapien dolor. Maecenas id tortor urna. In mattis suscipit cursus. In eget accumsan tellus. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Suspendisse volutpat fringilla erat, a convallis nulla efficitur id. Morbi placerat luctus diam, placerat hendrerit est laoreet at.",
          name: "Jonathan Kilner"
        },
        {
          text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi vitae eleifend nibh. Donec volutpat tellus vel maximus scelerisque. Curabitur mattis odio lectus, non lacinia nisl imperdiet a. Pellentesque consectetur sapien lorem, id porta purus luctus nec. Aliquam sodales risus at lobortis dignissim. Mauris consectetur consectetur leo varius dictum. Sed euismod massa et arcu interdum interdum. Nulla ac sapien dolor. Maecenas id tortor urna. In mattis suscipit cursus. In eget accumsan tellus. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Suspendisse volutpat fringilla erat, a convallis nulla efficitur id. Morbi placerat luctus diam, placerat hendrerit est laoreet at.",
          name: "Fulano da silva"
        }
      ]
    }
  },
  methods: {
    changeContent(content){
      console.log("Retornou: "+ content.index)
      this.publications[content.index].text = content.text
    },
    removeContent(index){
      console.log(this.publications.splice(index, 1))
      this.publications.splice(index, 1)
    },
    addContent(content){
      this.publications.push(content)
    }
  }
};
</script>
