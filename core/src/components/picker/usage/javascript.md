```javascript
async function showSingleColumnPicker() {
  const pickerOptions = {
    buttons: [
      {
        text: "Cancel",
        role: "cancel",
      },
      {
        text: "Confirm",
      },
    ],
    columns: [
      {
        name: "Fruits",
        options: [
          { text: "Banana", value: "ban" },
          { text: "Apple", value: "app" },
          { text: "Guava", value: "gua" },
          { text: "Mango", value: "man" },
        ],
      },
    ],
  };
  const picker = await this.pickerController.create(pickerOptions);
  picker.present();
  picker.onDidDismiss().then(async (data) => {
    const column = await picker.getColumn("Fruits");
    const selColumnRow = column.options[column.selectedIndex];
    console.log("Selected fruit:", selColumnRow.text);
    console.log("Value of selected fruit:", selColumnRow.value);
  });
}

async function showMultiColumnPicker() {
  const pickerOptions = {
    buttons: [
      {
        text: "Cancel",
        role: "cancel",
      },
      {
        text: "Confirm",
      },
    ],
    columns: [
      {
        name: "Fruits",
        options: [
          { text: "Banana", value: "ban" },
          { text: "Apple", value: "app" },
          { text: "Guava", value: "gua" },
          { text: "Mango", value: "man" },
        ],
      },
      {
        name: "Vegetables",
        options: [
          { text: "Cabbage", value: "cab" },
          { text: "Carrot", value: "car" },
          { text: "Potato", value: "pot" },
          { text: "Pumpkin", value: "pum" },
          { text: "Garlic", value: "gar" },
        ],
      },
      {
        name: "Cereals",
        options: [
          { text: "Corn", value: "cor" },
          { text: "Rice", value: "ric" },
          { text: "Wheat", value: "whe" },
          { text: "Barley", value: "bar" },
        ],
      },
    ],
  };

  const picker = await this.pickerController.create(pickerOptions);
  picker.present();
  picker.onDidDismiss().then(async (data) => {
    const fruitsCol = await picker.getColumn("Fruits");
    const vegCol = await picker.getColumn("Vegetables");
    const cerealsCol = await picker.getColumn("Cereals");
    const selFruitRow = fruitsCol.options[fruitsCol.selectedIndex];
    const selVegetableRow = vegCol.options[vegCol.selectedIndex];
    const selCerealRow = cerealsCol.options[cerealsCol.selectedIndex];
    console.log(
      "Selected Fruit, Vegetable and Cereal: ",
      selFruitRow.text,
      selVegetableRow.text,
      selCerealRow.text
    );
    console.log(
      "Values of selected Fruit, Vegetable and Cereal: ",
      selFruitRow.value,
      selVegetableRow.value,
      selCerealRow.value
    );
  });
}
```
