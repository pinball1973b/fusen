<template>
  <section class="section">
    <div class="input_wrapper">
      <b-field label="Subject">
        <b-input
          v-model="form.title"
          placeholder="title"
        ></b-input>
      </b-field>
      <b-field label="Description">
        <b-input
          v-model="form.description"
          maxlength="4000"
          type="textarea"
          placeholder="description"
        ></b-input>
      </b-field>
      <b-button
        @click="addCard"
        type="is-info"
      >
        Submit
      </b-button>
    </div>
    <div class="cardWrap">
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
      <card
        class="fusen_card"
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
        { title: 'Free', description: 'test project'}
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
      this.items.splice(key,1)
    }

  }
}
</script>
<style lang="scss" scoped>
.cardWrap {
  display: flex;
  flex-wrap: wrap;
  justify-content: left;
  .fusen_card {
    flex-grow: 0;
    flex-basis: 32%;
  }
}

</style>
