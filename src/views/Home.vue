<template>
  <v-container>
    <v-row>
      <v-col cols="5">
        <v-card>
          <v-card-title>New vehicle entry</v-card-title>
          <v-container class="px-10">
            <v-row>
              <v-text-field
                label="Patent Number"
                type="number"
                v-model="formInput.patent"
              ></v-text-field>
            </v-row>
            <v-row>
              <v-text-field
                label="Check-in time"
                type="time"
                v-model="formInput.checkin"
              ></v-text-field>
            </v-row>
            <v-row>
              <v-select
                :items="vehicleSelect"
                label="Standard"
                v-model="formInput.vehicleType"
              ></v-select>
            </v-row>
          </v-container>
        </v-card>
      </v-col>
      <v-col cols="7">
        <v-card>
          <v-card-title>No maches elige uno wey</v-card-title>
          <v-container class="pa-5">
            <v-row>
              <v-col
                cols="1"
                style="border: 1px solid blue"
                class="pa-2"
                v-for="n in cantidadLugares"
                :key="n"
              >
              <div style="background: red; border: 1px solid white">
                {{ n }}
              </div>
              </v-col>
            </v-row>
          </v-container>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      formInput: {
        patent: 0,
        chekin: "",
        vehicleType: "",
      },
      vehicleSelect: ["Car", "Pickup truck", "Motorcycle"],
      cantidadLugares: 20,
    };
  }
};
</script>
