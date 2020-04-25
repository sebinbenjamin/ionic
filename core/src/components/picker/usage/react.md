```tsx
import React, { useState } from "react";
import { IonButton, IonContent, IonPicker } from "@ionic/react";
import { PickerColumn } from "@ionic/core";

export const LoadingExample: React.FC = () => {
  const [singleColumnPicker, setSingleColumnPicker] = useState(false);
  const [multiColumnPicker, setMultiColumnPicker] = useState(false);

  const fruitsCol = {
    name: "Fruits",
    options: [
      { text: "Banana", value: "ban" },
      { text: "Apple", value: "app" },
      { text: "Guava", value: "gua" },
      { text: "Mango", value: "man" },
    ],
  } as PickerColumn;
  const vegsCol = {
    name: "Vegetables",
    options: [
      { text: "Cabbage", value: "cab" },
      { text: "Carrot", value: "car" },
      { text: "Potato", value: "pot" },
      { text: "Pumpkin", value: "pum" },
      { text: "Garlic", value: "gar" },
    ],
  } as PickerColumn;
  const cerealsCol = {
    name: "Cereals",
    options: [
      { text: "Corn", value: "cor" },
      { text: "Rice", value: "ric" },
      { text: "Wheat", value: "whe" },
      { text: "Barley", value: "bar" },
    ],
  } as PickerColumn;
  return (
    <IonContent fullscreen class="ion-padding">
      <IonButton expand="block" onClick={() => setSingleColumnPicker(true)}>
        Show Loading
      </IonButton>
      <IonButton expand="block" onClick={() => setMultiColumnPicker(true)}>
        Show Loading
      </IonButton>
      <IonPicker
        isOpen={singleColumnPicker}
        columns={[fruitsCol]}
        buttons={[
          {
            text: "Cancel",
            role: "cancel",
            handler: () => {
              setSingleColumnPicker(false);
            },
          },
          {
            text: "Confirm",
            handler: ({ Fruits }: any) => {
              setSingleColumnPicker(false);
              console.log("Selected fruit", Fruits.text);
              console.log("Value of selected fruit", Fruits.text);
            },
          },
        ]}
      ></IonPicker>
      <IonPicker
        isOpen={multiColumnPicker}
        columns={[fruitsCol, vegsCol, cerealsCol]}
        buttons={[
          {
            text: "Cancel",
            role: "cancel",
            handler: () => {
              setMultiColumnPicker(false);
            },
          },
          {
            text: "Confirm",
            handler: ({ Fruits, Vegetables, Cereals }: any) => {
              setMultiColumnPicker(false);
              console.log(
                "Selected Fruit, Vegetable and Cereal: ",
                Fruits.text,
                Vegetables.text,
                Cereals.text
              );
              console.log(
                "Values of selected Fruit, Vegetable and Cereal: ",
                Fruits.value,
                Vegetables.value,
                Cereals.value
              );
            },
          },
        ]}
      ></IonPicker>
    </IonContent>
  );
};
```
