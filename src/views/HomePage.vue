<template>
  <div class="home">
    <h1 class="name">Жорууд</h1>
    <div class="cooks">
      <div class="jor1">
        <h2>Овьёостой жимстэй шейк</h2>
        <ul>
          <li>Овьёос – 1/2 аяга</li>
          <li>Сүү – 1 аяга</li>
          <li>Банана – 1 ширхэг</li>
          <li>Жимс (нэрс, гүзээлзгэнэ) – 1/2 аяга</li>
          <li>Зөгийн бал – 1 халбага</li>
          <li>Чиа үр – 1 ц/х (хүсвэл)</li>
        </ul>
        <button @click="saveRecipe(recipe)">Хадгалах</button>
      </div>

      <div class="jor2">
        <h2>Гахайн махтай будаатай хуурга</h2>
        <ul>
          <li>Гахайн мах – 150–200 гр</li>
          <li>Будаа – 1 аяга</li>
          <li>Сонгино – 1/2 ширхэг</li>
          <li>Лууван – 1/2 ширхэг</li>
          <li>Сармис – 1 хумс</li>
          <li>Шар буурцагны сүмс – 1 халбага</li>
          <li>Давс, перец – амтлахаар</li>
        </ul>
        <button @click="saveRecipe(recipe)">Хадгалах</button>
      </div>

      <div class="jor3">
        <h2>Ногоотой шөл</h2>
        <ul>
          <li>Төмс – 1 ширхэг</li>
          <li>Лууван – 1 ширхэг</li>
          <li>Байцаа – 1 аяга хэрчсэн</li>
          <li>Сонгино – 1/2 ширхэг</li>
          <li>Сармис – 1 хумс</li>
          <li>Гурилтай банш (эсвэл гоймон) – 1 аяга</li>
          <li>Давс, перец – амтлахаар</li>
          <li>Ус – 1 литр</li>
        </ul>
        <button @click="saveRecipe(recipe)">Хадгалах</button>
      </div>
    </div>
    <p class="save">Хадгалсан жоруудыг <router-link to="/saved">Хадгалсан жор</router-link> хэсэгт харна уу.</p>
  </div>
</template>
<script setup>
import { db } from "@/firebase";
import { collection, addDoc } from "firebase/firestore";

const saveRecipe = async (recipe) => {
  try {
    await addDoc(collection(db, "recipes"), recipe);
    alert("Жор амжилттай хадгалагдлаа!");
  } catch (e) {
    console.error("Алдаа:", e);
    alert("Жор хадгалахад алдаа гарлаа.");
  }
};
</script>

<style>
.jor {
  position: relative;
  overflow: hidden;
  color: white;
}
.jor::before {
  content: "";
  position: absolute;
  top: 0; left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.5); /* маск */
  z-index: 0;
}
.jor * {
  position: relative;
  z-index: 1;
}


.jor h2 {
  font-size: 1.2em;
  color: #2c3e50;
  margin-bottom: 10px;
}

.jor ul {
  list-style: disc;
  padding-left: 20px;
  color: #34495e;
}

.cooks {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  justify-content: center;
}
.name {
  text-align: center;
  color: greenyellow  ;
  font-size: 4em;
  margin-bottom: 20px;

}
.home {
  padding: 20px;
  background-color: gray;
  min-height: 100vh;
  background-image: url("https://i.pinimg.com/736x/ea/a6/9f/eaa69f3911482afac4d1f9c2f058a8fe.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
button {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  cursor: pointer;
  justify-content: center;;
}
.save {
  text-align: center;
  margin-top: 10px;
  font-size: 1.2em;
  color: #2c3e50;
  font-weight: bold;
  border: 1px solid #2c3e50;
  padding: 10px;
  border-radius: 5px;
  background-color: #ecf0f1;
}
.jor1 {
  width: 250px;
  margin: 10px;
  padding: 15px;
  background-image: url("https://tse1.mm.bing.net/th/id/OIP.AsEZupyjnwPmP-B39RnmlwHaE8?rs=1&pid=ImgDetMain&o=7&rm=3");
  background-size: cover;
  background-position: center;
  color: black;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  text-align: left;
}
.jor2 {
  width: 250px;
  margin: 10px;
  padding: 15px;
  background-image: url("https://cdn.greensoft.mn/uploads/site/607/block/new_b9b486dcde4de8bbf1c41fa02075551a39db751a.jpg");
  background-size: cover;
  background-position: center;
  color: black;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  text-align: left;
}
.jor3 {
  width: 250px;
  margin: 10px;
  padding: 15px;
  background-image: url("https://scontent.fuln6-1.fna.fbcdn.net/v/t39.30808-6/311087036_182444921020473_1835102934631846510_n.jpg?_nc_cat=101&ccb=1-7&_nc_sid=6ee11a&_nc_ohc=RX6FhU8yGp8Q7kNvwEG5Sm-&_nc_oc=AdmYgQAjecrHxSZbcLw2uw0gugEqGkn1pSs-4I9PJld_5AtPA20dbWOrAb6OSUyq7HRfRtBoX5gGbTKEucVGBtiT&_nc_zt=23&_nc_ht=scontent.fuln6-1.fna&_nc_gid=Z7d5tCnhxnVvWqzO7iTsgQ&oh=00_AfNWUDYfimsLLUE2Njp5IIoPDy4JC_FoZs7aarYhuxjsDg&oe=686900A6");
  background-size: cover;
  background-position: center;
  color: black;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  text-align: left;
}


</style>