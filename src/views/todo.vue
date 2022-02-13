<template>
  <div class="topop">
    <op love="ลงทะเบียนเรียน" />
    <div class="rights">
      <v-row>
        <v-col cols="12" sm="6" md="4">
          <v-text-field
            v-model="namestu"
            label="ชื่อ"
            solo-inverted
          ></v-text-field>
        </v-col>

        <v-col cols="12" sm="6" md="4">
          <v-text-field
            v-model="lastname"
            label="นามสกุล"
            solo-inverted
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="6" md="4">
          <v-text-field
            v-model="idstu"
            label="รหัสบัตรประชาชน"
            solo-inverted
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="cs" label="คณะ" solo-inverted></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="cs2" label="สาขา" solo-inverted></v-text-field>
        </v-col>
      </v-row>
      <v-select
        v-model="subject"
        :items="items"
        label="จังหวัด"
        dense
        solo
      ></v-select>
      <v-btn @click="addTodo" class="ma-2" outlined color="indigo">
        ลงทะเบียนเรียน
      </v-btn>
      <v-list dense>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-list-item v-for="(item, i) in additems" :key="i">
            <v-list-item-content>
              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item-content>
            <v-btn
              class="mx-2"
              fab
              dark
              small
              color="error"
              @click="deleteTodo(i)"
            >
              <v-icon dark> mdi-minus </v-icon>
            </v-btn>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </div>
  </div>
</template>

<script>
import op from "../components/op.vue";
export default {
  data() {
    return {
      subject: "",
      namestu: "",
      lastname: "",
      cs: "",
      cs2: "",
      idstu: "",
      items: ["เชียงใหม่", "เชียงราย", "พะเยา", "กรุงเทพ"],
      selectedItem: 1,
      additems: [],
    };
  },
  components: {
    op,
  },

  methods: {
    addTodo() {
      //console.log(this.subject + this.work);
      this.additems.push({
        text:
          "คุณ" +
          this.namestu +
          " " +
          this.lastname +
          " " +
          " " +
          "รหัสบัตรประชาชน: " +
          this.idstu +
          " " +
          "คณะ: " +
          " " +
          this.cs +
          " " +
          "สาขา: " +
          " " +
          this.cs2 +
          " " +
          "ที่อยู่ " +
          this.subject,
      });
    },
    deleteTodo(index) {
      this.additems.splice(index, 1);
    },
  },
};
</script>

<style>
.topop {
  padding-top: 80px;
  padding-right: 90px;
}
.rights {
  padding-left: 40px;
}
</style>
