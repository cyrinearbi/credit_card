<template lang="pug">
  v-app
    v-container
      v-layout(row wrap)
        .title Credit Card

      br
      v-layout(row wrap)
        v-flex(xs12 md6)
          v-layout(row wrap)
            v-flex.pr-2(xs12 md6)
              v-text-field(
                name="number"
                label="Card number"
                v-model="cardDetail.number"
                )
            v-flex(xs12 md6)
              v-text-field(
                name="name"
                label="Full Name"
                v-model="cardDetail.name"
                )
          v-layout(row wrap)
            v-flex.pr-2(xs12 md6)
              v-text-field(
                name="expiry"
                label="MM/YY"
                v-model="cardDetail.expiry"
                )
            v-flex(xs12 md6)
              v-text-field(
                name="name"
                label="CVC"
                v-model="cardDetail.cvc"
                @focus="invertedCard = true"
                @blur="invertedCard = false"
                )
        v-spacer
        v-flex(xs12 md3)
          card(
            v-model="cardDetail"
            :invert-card.sync="invertedCard"
            format-data
            )
</template>

<script>
import Card from '@/components/Card'

const defaultCreditCardData = {
  number: '6703 0400 0000 0001 3',
  name: 'Owner name',
  expiry: '042019',
  cvc: '154'
}

export default {
  name: 'card-example',

  components: {
    Card
  },

  data: () => ({
    cardDetail: defaultCreditCardData,
    invertedCard: false
  })
}
</script>
