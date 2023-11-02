<template>
  <section class="home">
    <div class="container">
      <h1>Apple Store</h1>

      <div class="wrapper">
        <!-- Card -->
        <Card v-for="card in productArray" :productInfo="card" @action="openModal(card)" />
      </div>
    </div>
  </section>

  <!-- Modal -->
  <div class="modal-wrapper" v-if="isModalOpened">
    <Modal @closeModal="closeModal" :modalInfo="modalInfo" />
  </div>
</template>

<script>
import Card from './components/card.vue'
import Modal from './components/modal.vue'

export default {
  components: {
    Card,
    Modal
  },
  methods: {
    openModal(info) {
      this.isModalOpened = !this.isModalOpened
      this.modalInfo = info
    },
    closeModal() {
      this.isModalOpened = false
    }
  },
  data() {
    return {
      isModalOpened: false,
      modalInfo: '',
      productArray: [
        {
          name: 'iphone 15 Pro',
          image: "https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/iphone-card-40-iphone15prohero-202309?wid=680&hei=528&fmt=p-jpg&qlt=95&.v=1693086290312",
          text: 'The iPhone 15 and iPhone 15 Plus are smartphones designed, developed, and marketed by Apple Inc. They are the seventeenth-generation iPhones, succeeding the iPhone 14 and iPhone 14 Plus. The devices were announced on September 12, 2023, during the Apple Event at Apple Park in Cupertino, California alongside the higher-priced iPhone 15 Pro and 15 Pro Max flagships. Pre-orders began on September 15, 2023, and the devices were made available on September 22, 2023.'
        },
        {
          name: 'MacBook Pro 14',
          image: "https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/mac-card-40-macbookpro-14-16-202310?wid=1200&hei=1000&fmt=p-jpg&qlt=95&.v=1697730104429",
          text: 'The MacBook is a brand of Mac notebook computers designed and marketed by Apple Inc. that use Apple s macOS operating system since 2006. It replaced the PowerBook and iBook brands during the Mac transition to Intel processors, announced in 2005. The current lineup consists of the MacBook Air (2008–present) and the MacBook Pro (2006–present).'
        },
        {
          name: 'ipad Pro',
          image: 'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/ipad-card-40-pro-202210?wid=680&hei=528&fmt=p-jpg&qlt=95&.v=1664578794100',
          text: 'The original iPad Pro was introduced in September 2015, and ran iOS 9. It had an A9X chip, and came in two sizes: 9.7-inch and 12.9 inch. The second-generation iPad Pro, unveiled in June 2017, had an upgraded A10X Fusion chip and swapped the 9.7-inch screen for a larger 10.5-inch display. The third-generation iPad Pro, announced in October 2018, eliminated the home button, and featured Face ID.'
        },
        {
          name: 'Apple Watch Series 9',
          image: 'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/watch-card-40-s9-202309?wid=680&hei=528&fmt=p-jpg&qlt=95&.v=1693943487336',
          text: 'The Apple Watch is a line of smartwatches produced by Apple Inc. It incorporates fitness tracking, health-oriented capabilities, and wireless telecommunication, and integrates with iOS and other Apple products and services. The Apple Watch was released in April 2015.05.06'
        },
        {
          name: 'Airpods Max',
          image: "data:image/jpeg;base64,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",
          text: 'AirPods Max are wireless Bluetooth over-ear headphones designed by Apple, and released on December 15, 2020. They are Apples highest-end option in the AirPods lineup, sold alongside the base model AirPods and mid-range AirPods Pro. The main changes of the AirPods Max over the mid-range AirPods Pro are the over-ear design with larger speakers, inclusion of Apples Digital Crown found on the Apple Watch, more color options, and longer battery life.'
        },
        {
          name: 'AirTag',
          image: 'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/airtag-single-select-202104?wid=890&hei=890&fmt=jpeg&qlt=90&.v=1617761671000',
          text: 'AirTag is a tracking device developed by Apple. [1] AirTag is designed to act as a key finder, which helps people find personal objects (e.g. keys, bags, apparel, small electronic devices, vehicles). To locate lost items, AirTags use Apple is crowdsourced Find My network, estimated in early 2021 to consist of approximately one billion devices worldwide that detect and anonymously report emitted Bluetooth signals.'
        },
        {
          name: 'iPhone Accessories',
          image: 'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MT4J3?wid=532&hei=582&fmt=png-alpha&.v=1693594197616',
          text: 'For the physical care of the cell phone it is advisable to use cases that cover the entire back of the cell phone. Currently there are many distributors that offer different alternatives in models, materials, colors and custom designs.'
        },
        {
          name: 'Apple TV 4K ',
          image: 'https://openshop.uz/uploads/products/photos/202204/wPANtO9njBZbwf49yvHBVpuqhInvZv2C9TXEOE6f.jpg',
          text: 'Apple TV is a digital media player and microconsole developed and marketed by Apple Inc. It is a small network appliance hardware that sends received media data such as video and audio to a television set or external display. Its media services include streaming media, TV Everywhere-based services, local media sources, and sports journalism and broadcasts.'
        },
      ]
    }
  }
}
</script>

<style lang="scss">
.home {
  h1 {
    text-align: center;
    margin-top: 25px;
    text-decoration: underline;
    color: dodgerblue;
    font-size: 40px;
  }

  .wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
    gap: 25px;
    margin: 50px 0;
  }
}

.modal-wrapper {
  background: #0000008c;
  position: absolute;
  left: 0;
  top: 0;
  z-index: 99;
  width: 100%;
  height: 155%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: -190px;
}
</style>