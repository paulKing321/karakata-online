<template>
<div id="main" class="bg-black">
  <c-box
    class="details_box"
    pos="absolute"
    top="18%"
    left="30%"
    bg="white"
    w="35%"
    h="70%"
    color="black"
    zIndex="1700"
  >
  <c-flex
      direction="row"
      align="center"
      justify="space-between"
    >
    <c-text fontSize="2xl" class="bolded" p="6" is-truncated>Interaction with {{ SalesInt.number}}</c-text>
    <div @click="closeInt()"  >
    <c-icon align="right" mr="8" class="border-rounded" name="close" />
    </div>
  </c-flex>
    <c-flex
      direction="column"
      align="flex-start"
      justify="space-between"
      class="interactions"
      pl="4"
      v-for="(sale, index) in SalesInt.interactions"
      :key="index"
    >
      <div class="flex flex-row justify-between items-center">
        <img :src="require('@/assets/img/Oval.svg')" /><c-text
          class="bolded"
          py="4"
          ml="3"
          fontSize="md"
          is-truncated
          >{{ sale.header }}</c-text
        >
      </div>
      <div
        id="transaction_details"
        v-for="(sub, index) in sale.sub_header"
        :key="index"
      >
        <div class="flex flex-row justify-between">
          <img :src="require('@/assets/img/OvalSM.svg')" /><c-text
            fontSize="sm"
            ml="3"
            is-truncated
            >{{ sub.title }}</c-text
          >
        </div>
      </div>
    </c-flex>
  </c-box>
</div>
</template>

<script>
import salesdetail from '@/data/salesdetails'
export default {
  name: 'salesdata',
  props: ['SalesInt'],
  methods: {
    closeInt (event) {
      this.$emit('close', false)
    }
  }
}
</script>

<style scoped>
.details_box::-webkit-scrollbar {
  width: 5px;
}
.details_box::-webkit-scrollbar-track {
  display: none;
}
.details_box::-webkit-scrollbar-thumb {
  background-color: grey;
  outline: 1px solid grey;
  border-radius: 60px;
}
.bolded {
  font-weight: 700;
}
.interactions:nth-child(even) {
  background: #FFFAF9;
}
.details_box {
  overflow-y: scroll;
  overflow-x: hidden;
  box-shadow: 0px 0px 15px #333;
}
.border-rounded {
  padding: 2px;
  border: 1px solid black;
  color: black;
  border-radius: 50%;
}
#transaction_details {
  padding: 5px 25px;
  font-weight: 600;
}
#transaction_details:last-child {
  color: green;
}
</style>
