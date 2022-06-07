<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "DefaultFooter",
  data() {
    return {
      addresses: [
        {
          id: 1,
          name: "TECHNOLOGY DEPARTMENT",
          address:
            "Tech - Jl. Lembong No 8 Kel. Braga Kec. Sumur Bandung, Kota Bandung, Jawa Barat",
        },
        {
          id: 2,
          name: "LOGISTIC DEPARTMENT",
          address:
            "Log - Jl. Lembong No 8 Kel. Braga Kec. Sumur Bandung, Kota Bandung, Jawa Barat",
        },
        {
          id: 3,
          name: "FINANCE DEPARTMENT",
          address:
            "Fin - Jl. Lembong No 8 Kel. Braga Kec. Sumur Bandung, Kota Bandung, Jawa Barat",
        },
      ],
      selectedAddressOption: 1,
    };
  },
  computed: {
    defineSelectedAddress(): string {
      return (
        this.addresses.find((address) => {
          return address.id === this.selectedAddressOption;
        })?.address || ""
      );
    },
  },
});
</script>

<template>
  <div class="footer">
    <div class="vector-layer-1">
      <div class="vector-layer-2">
        <div class="container">
          <div class="footer-content">
            <div class="footer-logo">
              <a href="#">
                <img src="/white-company-logo.png" alt="Company Logo White" />
              </a>
            </div>
            <div class="footer-infos">
              <div class="footer-address">
                <select v-model="selectedAddressOption">
                  <option
                    v-for="option in addresses"
                    :key="`address-option-${option.id}`"
                    :value="option.id"
                  >
                    {{ option.name }}
                  </option>
                </select>
                <p>
                  {{ defineSelectedAddress }}
                </p>
              </div>
              <div class="footer-menu">
                <a href="#about" class="footer-menu__item">Who We Are</a>
                <a href="#core-value" class="footer-menu__item">Our Values</a>
                <a href="#speciality" class="footer-menu__item">The Perks</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.footer {
  background-color: #07477a;
  color: #fff;
}

.container {
  padding: 40px;
}

.vector-layer-1 {
  background-image: url("/footer-vector-1.svg");
}

.vector-layer-2 {
  background-image: url("/footer-vector-2.svg");
}

.footer-logo {
  margin-bottom: 30px;
}

.footer-address {
  background-color: #fff;
  padding: 20px;
  color: #25a0d8;
  font-size: 18px;
  margin-bottom: 30px;
}

.footer-menu {
  a {
    color: #fff;
    text-decoration: none;
    display: block;
    padding: 20px 0;
  }
}

select {
  display: block;
  width: 100%;
  border: 1px solid #c4c4c4;
  margin-bottom: 20px;
  padding: 10px;
  background-color: #fff;
  font-weight: bolder;
  border-radius: 4px;
  color: #00537c;
}

@media only screen and (min-width: 480px) {
  .container {
    padding: 40px 0;
  }
  .footer-content {
    display: flex;
    justify-content: space-between;
  }

  .footer-infos {
    display: flex;
    justify-content: space-between;
    flex-direction: row-reverse;

    & div {
      flex: 1;
    }
  }
}
</style>
