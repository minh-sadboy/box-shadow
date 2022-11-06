<template>
  <div v-show="showPriceCar">
    <div :class="[$style.position]">
      <div :class="[$style.title]">
        <div :class="[$style.logo]">
          <svg
            width="24"
            height="24"
            viewBox="0 0 32 32"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-path="evenodd"
              d="M20.2449 6.68344C20.0967 6.94319 19.7603 7.03679 19.4935 6.89249L16.8428 5.4586L16.8909 9.34351C16.8946 9.64064 16.6503 9.88441 16.3451 9.888C16.04 9.89159 15.7896 9.65363 15.7859 9.3565L15.7371 5.41502L13.0935 6.74118C12.8222 6.87727 12.489 6.77345 12.3493 6.5093C12.2095 6.24515 12.3161 5.92069 12.5874 5.7846L16.0257 4.05974C16.19 3.97735 16.3856 3.98034 16.5471 4.0677L20.0302 5.95182C20.2969 6.09612 20.3931 6.42368 20.2449 6.68344ZM23.4318 7.55824C23.2625 7.80549 23.3312 8.13953 23.5851 8.30436L26.1081 9.94222L22.5394 11.6797C22.2664 11.8126 22.1558 12.1358 22.2923 12.4016C22.4287 12.6674 22.7606 12.7751 23.0336 12.6422L26.6543 10.8794V13.7751C26.6543 14.0722 26.9016 14.3131 27.2068 14.3131C27.512 14.3131 27.7594 14.0722 27.7594 13.7751V10.0088C27.7594 9.82893 27.667 9.66094 27.5133 9.56116L24.1981 7.40902C23.9441 7.24419 23.6011 7.311 23.4318 7.55824ZM8.32754 8.09628C8.49681 8.34353 8.4282 8.67758 8.17429 8.8424L5.65126 10.4803L9.21999 12.2178C9.49293 12.3507 9.60356 12.6738 9.46709 12.9396C9.33062 13.2054 8.99872 13.3131 8.72578 13.1802L5.10509 11.4174V14.3131C5.10509 14.6103 4.8577 14.8511 4.55254 14.8511C4.24738 14.8511 4 14.6103 4 14.3131V10.5469C4 10.367 4.09233 10.199 4.24605 10.0992L7.5613 7.94706C7.81521 7.78223 8.15827 7.84904 8.32754 8.09628ZM12.5057 14.3566C12.2252 14.2396 11.9004 14.3661 11.7802 14.6392C11.66 14.9123 11.7899 15.2286 12.0704 15.3457L15.6033 16.82V20.7695C15.6033 21.0667 15.8507 21.3076 16.1558 21.3076C16.461 21.3076 16.7084 21.0667 16.7084 20.7695V16.7978L19.7182 15.3324C19.9911 15.1995 20.1018 14.8763 19.9653 14.6105C19.8288 14.3448 19.4969 14.237 19.224 14.3699L16.1379 15.8724L12.5057 14.3566ZM4.96768 18.9307C5.27205 18.9522 5.50095 19.2098 5.47895 19.5062L5.26029 22.4512L8.85827 20.7718C9.13345 20.6434 9.46346 20.7565 9.59536 21.0244C9.72727 21.2924 9.61111 21.6137 9.33593 21.7422L5.68556 23.446L8.0345 25.2218C8.27554 25.404 8.31923 25.742 8.13209 25.9767C7.94495 26.2114 7.59784 26.254 7.3568 26.0717L4.30168 23.7621C4.15575 23.6518 4.0761 23.4777 4.08943 23.2983L4.37674 19.4286C4.39874 19.1322 4.66332 18.9093 4.96768 18.9307ZM26.609 19.5062C26.587 19.2098 26.8159 18.9522 27.1203 18.9307C27.4247 18.9093 27.6892 19.1322 27.7112 19.4286L27.9986 23.2983C28.0119 23.4777 27.9322 23.6518 27.7863 23.7621L24.7312 26.0717C24.4901 26.254 24.143 26.2114 23.9559 25.9767C23.7688 25.742 23.8124 25.404 24.0535 25.2218L26.4024 23.446L22.7521 21.7422C22.4769 21.6137 22.3607 21.2924 22.4926 21.0244C22.6245 20.7565 22.9545 20.6434 23.2297 20.7718L26.8277 22.4512L26.609 19.5062ZM12.5104 27.1944C12.2436 27.0501 11.9072 27.1437 11.759 27.4035C11.6108 27.6632 11.707 27.9908 11.9737 28.1351L15.4568 30.0192C15.6183 30.1065 15.814 30.1095 15.9782 30.0271L19.4165 28.3023C19.6878 28.1662 19.7944 27.8417 19.6547 27.5776C19.5149 27.3134 19.1817 27.2096 18.9104 27.3457L16.2668 28.6719L16.218 24.7304C16.2143 24.4333 15.9639 24.1953 15.6588 24.1989C15.3537 24.2025 15.1093 24.4463 15.113 24.7434L15.1611 28.6283L12.5104 27.1944Z"
              fill="currentColor"
            />
          </svg>
          &nbsp;&nbsp;Chi tiết gói
        </div>
        <div style="cursor: pointer;" @click="closePriceCar()">
          <v-icon dark size="22">mdi-close</v-icon>
        </div>
      </div>

      <div style="margin: 1rem;margin-bottom: 0px;">
        <div :class="[$style.divider]"></div>
        <div :class="[$style.menutext0]" hidden></div>
      </div>

      <v-list color="rgba(255, 0, 0, 0)">
        <v-list-group :value="false">
          <template v-slot:activator>
            <v-list-item-title>
              <p :class="[$style.menutext]">1. Dán ngoại thất</p>
            </v-list-item-title>
          </template>
          <v-list-item @click="changeCarPart(0)">
            <v-list-item-title>
              <p :class="[$style.menutext1]">Xuất xứ Trung Quốc</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(1)">
            <v-list-item-title>
              <p :class="[$style.menutext2]">Xuất xứ Teckwarp USA</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(2)">
            <v-list-item-title>
              <p :class="[$style.menutext3]">Xuất xứ OnePro Canada</p>
            </v-list-item-title>
          </v-list-item>
        </v-list-group>

        <v-list-group :value="false">
          <template v-slot:activator>
            <v-list-item-title>
              <p :class="[$style.menutext]">2. Dán decal đổi màu</p>
            </v-list-item-title>
          </template>
          <v-list-item @click="changeCarPart(3)">
            <v-list-item-title>
              <p :class="[$style.menutext4]">Xuất xứ TQ loại 2</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(4)">
            <v-list-item-title>
              <p :class="[$style.menutext5]">
                Xuất xứ TQ loại 1(AX Film,
                <br />xuất Nhật)
              </p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(5)">
            <v-list-item-title>
              <p :class="[$style.menutext6]">Xuất xứ Teckwarp USA</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(6)">
            <v-list-item-title>
              <p :class="[$style.menutext7]">
                Xuất xứ OnePro PANTONE
                <br />Canada
              </p>
            </v-list-item-title>
          </v-list-item>
        </v-list-group>

        <v-list-group :value="false">
          <template v-slot:activator>
            <v-list-item-title>
              <p :class="[$style.menutext]">3. Dán Duo-tone</p>
            </v-list-item-title>
          </template>
          <v-list-item @click="changeCarPart(7)">
            <v-list-item-title>
              <p :class="[$style.menutext8]">Thân trên</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(8)">
            <v-list-item-title>
              <p :class="[$style.menutext9]">Thân dưới</p>
            </v-list-item-title>
          </v-list-item>
        </v-list-group>

        <v-list-group :value="false">
          <template v-slot:activator>
            <v-list-item-title>
              <p :class="[$style.menutext]">4. Dán điểm chi tiết</p>
            </v-list-item-title>
          </template>
          <v-list-item @click="changeCarPart(9)">
            <v-list-item-title>
              <p :class="[$style.menutext10]">Nẹp viền cửa kính</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(10)">
            <v-list-item-title>
              <p :class="[$style.menutext11]">Mặt calant</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(11)">
            <v-list-item-title>
              <p :class="[$style.menutext12]">Gương xe</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(12)">
            <v-list-item-title>
              <p :class="[$style.menutext13]">Tay nắm cửa</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(13)">
            <v-list-item-title>
              <p :class="[$style.menutext14]">Logo</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(14)">
            <v-list-item-title>
              <p :class="[$style.menutext15]">Viền cốp</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(15)">
            <v-list-item-title>
              <p :class="[$style.menutext16]">Lazang</p>
            </v-list-item-title>
          </v-list-item>
        </v-list-group>

        <v-list-group :value="false">
          <template v-slot:activator>
            <v-list-item-title>
              <p :class="[$style.menutext]">5. Dán nóc + vai</p>
            </v-list-item-title>
          </template>
          <v-list-item @click="changeCarPart(16)">
            <v-list-item-title>
              <p :class="[$style.menutext17]">Dán nóc</p>
            </v-list-item-title>
          </v-list-item>

          <v-list-item @click="changeCarPart(17)">
            <v-list-item-title>
              <p :class="[$style.menutext18]">Dán nóc + vai</p>
            </v-list-item-title>
          </v-list-item>
        </v-list-group>
      </v-list>
    </div>

    <div :class="[$style.menucolor]"></div>
    <div :class="[$style.openprice]" v-show="openPrice" @click="openPriceFn">
      <v-icon dark size="26">mdi-information-variant</v-icon>
    </div>

    <v-app>
      <v-dialog v-model="dialog" width="500" light>
        <v-card>
          <v-card-title style="font-size: 1.8rem">Thông tin</v-card-title>
          <v-card-text style="font-size:1.2rem;line-height: 2rem;">
            Giá: {{ priceModal}}
            <br />
            Bảo hành: {{ baohanhModal}}
            <br />
            Thi công: {{ thicongModal}}
          </v-card-text>
          <v-divider></v-divider>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn text @click="dialog = false">
              <span style="font-size:1.2rem">Đóng</span>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-app>
  </div>
</template>

<style>
.mdi-chevron-down {
  color: #ffffff !important;
}
.v-dialog__container {
  display: block;
}
</style>
<style module>
.position {
  position: fixed;
  top: 0rem;
  left: 0rem;
  width: 20rem;
  height: calc(80vh - 1rem);
  background-color: rgba(0, 0, 0, 0.4);
  backdrop-filter: blur(5px);
  overflow-y: scroll;
}

.position::-webkit-scrollbar {
  width: 5px;
}

/* Track */
.position::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
.position::-webkit-scrollbar-thumb {
  background: rgb(142, 141, 141);
  border-radius: 5rem;
}

/* Handle on hover */
.position::-webkit-scrollbar-thumb:hover {
  background: #555;
}

.title {
  display: flex;
  justify-content: space-between;
  margin: 1.5rem 1rem;
}

.logo {
  display: flex;
  align-items: center;
  color: #fff;
  font-size: 1.2rem;
  background-color: rgba(0, 0, 0, 0.2);
  border-radius: 32px;
  padding: 2px 8px 2px 6px;
  cursor: pointer;
}

.select {
  margin: 2rem 1rem;
  color: #fff;
  font-size: 1.2rem;
  background-color: rgba(0, 0, 0, 0.2);
  border-radius: 32px;
  padding: 2px 8px 2px 6px;
  display: flex;
  justify-content: space-between;
}
.selectcol {
  width: 50%;
  padding: 0.4rem 0rem;
  border: 1px solid #a9e3ff;
  box-shadow: 0 0 5px #4cc7f4, inset 0 0 5px #4cc7f4;
  text-align: center;
  border-radius: 32px;
  cursor: pointer;
}
.selectcol1 {
  width: 50%;
  padding: 0.4rem 0rem;
  text-align: center;
  border-radius: 32px;
  cursor: pointer;
}

.menutext {
  font-size: 1.2rem;
  color: #fff;
  cursor: pointer;
  margin: 2em 0rem;
}

.menutext0,
.menutext1,
.menutext2,
.menutext3,
.menutext4,
.menutext5,
.menutext6,
.menutext7,
.menutext8,
.menutext9,
.menutext10,
.menutext11,
.menutext12,
.menutext13,
.menutext14,
.menutext15,
.menutext16,
.menutext17,
.menutext18 {
  font-size: 1.2rem;
  color: #fff;
  margin-left: 1.5rem;
  cursor: pointer;
}

.menuimg {
  width: 3em;
  height: 3rem;
}

.divider {
  background-color: #b8b5b5;
  height: 0.5px;
}
.menucolor {
  position: fixed;
  top: calc(80vh - 1rem);
  left: 0px;
  border-right: 5px solid #f1f1f1;
  width: 20rem;
  background-color: rgba(0, 0, 0, 0.4);
  backdrop-filter: blur(5px);
  border-bottom-right-radius: 1rem;
  padding-left: 1rem;
  padding-bottom: 1rem;
  padding-right: 1rem;
}

.openprice {
  position: fixed;
  left: 21rem;
  top: 1rem;
  width: 4rem;
  height: 4rem;
  border-radius: 0.4rem;
  background-color: #039be5;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

<script>
export default {
  props: ["openPriceCar"],
  data() {
    return {
      showPriceCar: false,
      menuTexBefore: 0,
      dialog: false,
      priceID: 0,
      openPrice: false,
      dataPrice: [
        {
          price: "16.500.000",
          baohanh: "3 năm",
          thicong: "8h"
        },
        {
          price: "19.500.000",
          baohanh: "5 năm",
          thicong: "8h"
        },
        {
          price: "54.500.000",
          baohanh: "5 năm",
          thicong: "8h"
        },
        {
          price:
            "10.000.000 (Xe cỡ nhỏ); 11.500.000 (Xe cỡ trung); 13.000.000 (Xe cỡ lớn)",
          baohanh: "1 năm",
          thicong: "8h"
        },
        {
          price:
            "14.000.000 (Xe cỡ nhỏ); 15.500.000 (Xe cỡ trung); 17.000.000 (Xe cỡ lớn)",
          baohanh: "3 năm",
          thicong: "8h"
        },
        {
          price:
            "18.000.000 (Xe cỡ nhỏ); 20.000.000 (Xe cỡ trung); 22.000.000 (Xe cỡ lớn)",
          baohanh: "5 năm",
          thicong: "8h"
        },
        {
          price:
            "52.500.000 (Xe cỡ nhỏ); 55.500.000 (Xe cỡ trung); 58.500.000 (Xe cỡ lớn)",
          baohanh: "5 năm",
          thicong: "8h"
        }
      ],
      priceModal: null,
      baohanhModal: null,
      thicongModal: null
    };
  },
  methods: {
    changeCarPart(number) {
      this.openPrice = true;
      this.priceID = number;
      const menutext = Number(number) + 1;
      document.getElementsByClassName(
        this.$style["menutext" + this.menuTexBefore]
      )[0].style.color = "#ffffff";
      document.getElementsByClassName(
        this.$style["menutext" + menutext]
      )[0].style.color = "#48ceff";
      this.menuTexBefore = menutext;
      this.hideCarPart(number);
    },
    openPriceFn() {
      this.dialog = true;
      const dataPrice = this.dataPrice;
      const number = this.priceID;
      this.priceModal = dataPrice[number].price;
      this.baohanhModal = dataPrice[number].baohanh;
      this.thicongModal = dataPrice[number].thicong;
    },
    hideCarPart(number) {
      if (number == 0) {
        this.$emit("hideCarPart", "hideoutfullcar");
      }
      if (number == 1) {
        this.$emit("hideCarPart", "hideoutfullcar");
      }
      if (number == 2) {
        this.$emit("hideCarPart", "hideoutfullcar");
      }
      if (number == 3) {
        this.$emit("hideCarPart", "hideoutfullcar");
      }
      if (number == 4) {
        this.$emit("hideCarPart", "hideoutfullcar");
      }
      if (number == 5) {
        this.$emit("hideCarPart", "hideoutfullcar");
      }
      if (number == 6) {
        this.$emit("hideCarPart", "hideoutfullcar");
      }
      if (number == 7) {
        this.$emit("hideCarPart", "hideoutduotoneup");
      }
      if (number == 8) {
        this.$emit("hideCarPart", "hideoutduotonedown");
      }
      if (number == 9) {
        this.$emit("hideCarPart", "nepvienkinh");
      }
      if (number == 10) {
        this.$emit("hideCarPart", "matcalant");
      }
      if (number == 11) {
        this.$emit("hideCarPart", "guongxe");
      }
      if (number == 12) {
        this.$emit("hideCarPart", "taynamcua");
      }
      if (number == 13) {
        this.$emit("hideCarPart", "logo");
      }
      if (number == 14) {
        this.$emit("hideCarPart", "viencop");
      }
      if (number == 15) {
        this.$emit("hideCarPart", "lazang");
      }
      if (number == 16) {
        this.$emit("hideCarPart", "noc");
      }
      if (number == 17) {
        this.$emit("hideCarPart", "nocvai");
      }
    },
    closePriceCar(){
      this.$emit("closePriceCar");
    }
  },
  watch: {
    openPriceCar: function(newVal, oldVal) {
      // watch it
      if (newVal == 1) {
        this.showPriceCar = true;
      } else {
        this.showPriceCar = false;
      }
    }
    // carpart: function(newVal, oldVal) {
    //   // watch it
    //   if (newVal) {
    //     console.log(this.carpart)
    //     // if (this.carpart == 0) {
    //     //   this.$emit("changeColor", "fullcar", this.color);
    //     // }
    //     // if (this.carpart == 1) {
    //     //   this.$emit("changeColor", "duotoneup", this.color);
    //     // }
    //     // if (this.carpart == 2) {
    //     //   this.$emit("changeColor", "duotonedown", this.color);
    //     // }
    //     // if (this.carpart == 3) {
    //     //   this.$emit("changeColor", "nocup", this.color);
    //     // }
    //     // if (this.carpart == 4) {
    //     //   this.$emit("changeColor", "nocvai", this.color);
    //     // }
    //     // if (this.carpart == 5) {
    //     //   this.$emit("changeColor", "vienkinh", this.color);
    //     // }
    //     // if (this.carpart == 6) {
    //     //   this.$emit("changeColor", "calant", this.color);
    //     // }
    //     // if (this.carpart == 7) {
    //     //   this.$emit("changeColor", "guong", this.color);
    //     // }
    //     // if (this.carpart == 8) {
    //     //   this.$emit("changeColor", "namcua", this.color);
    //     // }
    //     // if (this.carpart == 9) {
    //     //   this.$emit("changeColor", "logo", this.color);
    //     // }
    //     // if (this.carpart == 10) {
    //     //   this.$emit("changeColor", "viencop", this.color);
    //     // }
    //     // if (this.carpart == 11) {
    //     //   this.$emit("changeColor", "lazang", this.color);
    //     // }
    //     // if (this.carpart == 12) {
    //     //   this.$emit("changeColor", "alldiem", this.color);
    //     // }
    //   }
    // }
  }
};
</script>
