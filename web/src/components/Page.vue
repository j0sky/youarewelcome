<template>
  <div class="page-wrapper">
    <div class="content">
      <h1>Hello, world!</h1>
      <h2>Cats are better than dogs. Or not?</h2>
      <div class="cats-are-better-than-dogs-wrapper">
        <p>The Best Reasons Why Cats Are Better Than Dogs. Lorem ipsum dolor sit amet consectetur, adipisicing elit. Et dolore iste eius dicta tempora quo delectus, excepturi eveniet laborum dolores magnam labore quisquam eos suscipit tempore ipsam, minima voluptatem illo?</p>
        <img src="../assets/img/kitten.png" alt="kitten">
      </div>

      <div class="cta-wrapper">
        <a href="#" class="cta-button">Call to action</a>
      </div>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores modi dolore ea amet numquam, animi, perferendis fugiat deserunt laboriosam omnis debitis deleniti recusandae id voluptas, nemo dignissimos assumenda commodi quisquam?</p>

      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Tenetur officiis provident neque tempora, earum blanditiis. Accusantium, ipsum! At sunt error excepturi qui perspiciatis. Natus, distinctio libero debitis aliquid aliquam eveniet?</p>
      <ol>
        <li>lorem</li>
        <li>ipsum</li>
        <li>etc</li>
      </ol>
      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Fugiat, tenetur quaerat. Eaque iure voluptates perferendis error reprehenderit quod, alias voluptatum blanditiis, possimus quos sapiente. Est quam illo delectus totam illum!</p>
      <p>
        <span>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Suscipit illo reiciendis consequatur odit similique dolore dolorem perferendis voluptate eveniet? Eaque laborum consequuntur adipisci nemo porro voluptatibus minima ea voluptatem fugiat?</span>
        <span>Quasi fugiat reprehenderit eligendi dicta eum similique repudiandae reiciendis nam a dignissimos recusandae quod illo commodi ullam obcaecati numquam laboriosam, exercitationem perferendis? Laborum qui officia quaerat animi, est nihil expedita.</span>
        <span>Quam doloribus tenetur labore nobis maxime nostrum hic et quibusdam nemo! Ex, dignissimos aliquid nostrum impedit quas, nulla veniam aut, reprehenderit laudantium praesentium harum dicta fuga ut! Ipsum, dolorem voluptatem?</span>
        <span>Sequi ipsum facilis nihil, possimus perferendis itaque similique? Debitis expedita officiis mollitia ex suscipit voluptatum amet aliquid quo! Blanditiis unde architecto optio sit a libero voluptatibus corporis totam sint maxime.</span>
        <span>Ducimus vero, est nesciunt a illum obcaecati ipsam similique quod blanditiis. Deserunt amet labore exercitationem quae quaerat quasi, modi inventore sapiente numquam, itaque rem doloribus reiciendis error quidem totam aliquam.</span>
        <span>Quod praesentium necessitatibus facilis, laudantium nihil nobis aperiam blanditiis minima velit dolores repudiandae nam impedit cum voluptatum ratione natus voluptatem, quisquam asperiores maiores. Rem repellendus quo nulla excepturi sequi distinctio?</span>
        <span>Animi qui modi blanditiis tenetur veniam aperiam vitae. Tempora quidem corporis eveniet tempore, aut excepturi quae veritatis dicta dolores optio, odit odio nemo, obcaecati nam ex a? Nobis, aspernatur repudiandae?</span>
        <span>Quod voluptatibus fugiat iure dolorum fugit laborum quam totam ex at! Assumenda quia neque ea et? Fugiat debitis dignissimos sapiente alias facilis laudantium? Architecto facilis quam maxime ea animi soluta.</span>
        <span>Quae molestiae quibusdam eos odit consectetur adipisci, ab, suscipit harum consequatur blanditiis ducimus perferendis! Iure, ex harum cum enim aut fugiat debitis nobis laboriosam ipsam natus ducimus quis nesciunt nemo.</span>
        <span>Quia, enim minus vel rerum corporis sed repellendus at corrupti facilis deserunt provident sunt laborum ex explicabo ratione fugiat dolore sit tenetur recusandae a quibusdam! Similique et quas hic voluptatum.</span>
      </p>
      <Todo />
    </div>

  </div>
</template>

<script>
import Todo from '../components/Todo.vue'
export default {
  name: 'Page',
  components: {
    Todo
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.page-wrapper {
  margin: 0;
  padding-top: 100px;
  width: 100wh;
  min-height: 100vh;
  color: #fff;
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: Gradient 15s ease infinite;
}

.content {
  max-width: 980px;
  margin: 0 auto;
  font-family: "flow-circular";
  padding: 50px;
  font-size: 24px;
}

h1 {
  font-size: 72px;
}

.cats-are-better-than-dogs-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;

  img {
    max-width: 300px;
    max-height: 300px;
  }

  @media screen and (min-width: 720px) {
    flex-direction: row;
  }
}

.cta-wrapper {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  padding-bottom: 50px;
}

.cta-button {
  font-size: 32px;
  text-decoration: none;
  color: #fff;
  outline: 4px solid #fff;
  padding: 15px 40px;
  transition: .3s;

  &:hover {
    outline: 10px solid rgb(209, 24, 255);
    color: rgb(209, 24, 255);
  }
}

@keyframes Gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

@font-face {
  font-family: "flow-circular";
  src: url("../assets/fonts/flow-circular.woff") format("woff")
}

</style>
