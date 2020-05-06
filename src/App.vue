<template>
  <v-app>
    <v-app-bar app >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-btn>Button A</v-btn>
      <v-btn>按钮B</v-btn>
    </v-app-bar>
    <v-content>
      <v-row no-gutters>
        <v-toolbar>
          <v-toolbar-title>Title</v-toolbar-title>
          <v-btn>按钮1</v-btn>
          <v-btn>Button 2</v-btn>
        </v-toolbar>
      </v-row>
      <v-row no-gutters> 
        <v-col cols="3">
          <v-treeview :items="treeData"></v-treeview>
            <v-text-field label="中文regular"></v-text-field>
            <v-slider dense v-model="sliderMin" min="-100" max="100" label="Min"></v-slider>
            <v-checkbox dense v-model="checkbox" :label="`Checkbox 1: ${checkbox.toString()}`"></v-checkbox>
            <v-radio-group dense v-model="radioGroup">
              <v-radio v-for="n in 3" :key="n" :label="`Radio ${n}`" :value="n"></v-radio>
            </v-radio-group>
            <v-switch v-model="switch1" :label="`Switch 1: ${switch1.toString()}`"></v-switch>
            <v-select :items="selectItem" label="Standard"></v-select>
            <v-overflow-btn :items="selectItem" label="Foo" ></v-overflow-btn>
        </v-col>
        <v-col cols="9">
          <v-data-table dense :headers="table.header" :items="table.data" :items-per-page="5" ></v-data-table>
          <v-row no-gutters>
            <v-date-picker  v-model="datePicker"></v-date-picker>
            <v-time-picker v-model="timePicker"></v-time-picker>
            <v-menu offset-y>
              <template v-slot:activator="{ on }">
                <v-btn style="font-variant: small-caps" v-on="on">Dropdown1</v-btn>
              </template>
              <v-list dense>
                <v-list-item v-for="(item, index) in menuItems" :key="index">
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>

            <v-list>
              <v-subheader>listHeader</v-subheader>
              <v-list-item-group v-model="listItem" >
                <v-list-item  v-for="(item, i) in menuItems" :key="i">
                  <v-list-item-icon>
                    <v-icon v-text="item.icon"></v-icon>
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title v-text="item.title"></v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-item-group>
            </v-list>
          </v-row>
        </v-col>
      </v-row>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: "App",

  data: () => ({
    selectItem: ['Foo', 'Bar', 'Fizz', 'Buzz'],
    switch1: '',
    radioGroup: '',
    checkbox: '',
    sliderMin: 0,
    listItem: '',
    menuItems: [
      { title: 'Click Me', icon: 'mdi-clock' },
      { title: 'Click Me', icon: 'mdi-satellite'},
      { title: 'Click Me', icon: 'mdi-account'},
      { title: 'Click Me 2', icon: 'mdi-flag'},
    ],
    datePicker: '',
    timePicker: '',
    colorPicker: '',
    treeData: [
      {
        id: 1,
        name: '树根root :',
        children: [
          { id: 2, name: '子树A',
            children: [{id: 21, name: '子子树'}]
          },
          { id: 3, name: 'child 2' },
          { id: 4, name: 'child 3' },
        ],
      },
    ],
    table: {
      header: [
        {
          text: 'Dessert (100g serving)',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'Calories', value: 'calories' },
        { text: 'Fat (g)', value: 'fat' },
        { text: 'Carbs (g)', value: 'carbs' },
        { text: 'Protein (g)', value: 'protein' },
        { text: 'Iron (%)', value: 'iron' },
      ],
      data: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: '1%',
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: '1%',
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: '7%',
        },
        {
          name: 'Cupcake',
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: '8%',
        },
        {
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: '16%',
        },
        {
          name: 'Jelly bean',
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: '0%',
        },
        {
          name: 'Lollipop',
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: '2%',
        },
        {
          name: 'Honeycomb',
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: '45%',
        },
        {
          name: 'Donut',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: '22%',
        },
        {
          name: 'KitKat',
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: '6%',
        },
      ],
    }
    //
  })
};
</script>
