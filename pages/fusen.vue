<template>
  <section class="section">
    <div class="columns is-mobile">
      <!--
      <card
        title="Free"
        icon="github-circle"
      >
        Open source on <a href="https://github.com/buefy/buefy">
          GitHub
        </a>
      </card>
    -->
    <div class="input_wrapper">
      <b-field label="Subject">
        <b-input v-model="form.title"></b-input>
      </b-field>
      <b-field label="Description">
        <b-input
          v-model="form.description"
          maxlength="4000"
          type="textarea"
        ></b-input>
      </b-field>
      <b-button
        @click="addCard"
        type="is-info"
      >
        Submit
      </b-button>
    </div>
      <card
        v-for="(item, index) in items"
        :key="index"
        :title="item.title"
      >
        {{ item.description }}
        <b-button
          @click="removeCard(index)"
          type="is-light"
          icon-right="delete"
        />
      </card>
    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'

export default {
  name: 'HomePage',

  components: {
    Card
  },
  data() {
    return {
      items: [
        { title: 'Free', description: 'test project'},
        { title: 'Free', description: 'test project'},
      ],
      form: {
        title: '',
        description: '',
      }
    }
  },
  methods: {
    addCard() {
      let temp = []
      const data = JSON.parse(JSON.stringify(this.items))
      const model = JSON.parse(JSON.stringify(this.form))
      temp = data
      temp.push(model)
      this.items = temp
      this.form.title = ''
      this.form.description = ''
    },
    removeCard(key) {
      console.log(key)
      this.items.splice(key,1)
    }

  }
}
</script>
