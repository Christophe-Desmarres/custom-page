<template>
  <div>
  <div class="about">
    <h2>About</h2>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Earum dolorem nesciunt at, sit corrupti quod molestias ullam fuga recusandae eum saepe ipsum rem vitae a.
    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Dicta vitae qui optio.
    Lorem ipsum, dolor sit amet consectetur adipisicing elit. Esse fuga laborum id excepturi molestias, numquam, dignissimos quectetur adipisicing elit. Dolores laboriosam sint eos doloribus minima magnam explicabo at saepe a repudiandae.</p>
  </div>
  <div class="about">
    <h2>About</h2>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Earum dolorem nesciunt at, sit corrupti quod molestias ullam fuga recusandae eum saepe ipsum rem vitae a.
    Lorem ipsum, dolor sit amet consectetur adipisicing elit. Esse fuga laborum id excepturi molestias, numquam, dignissimos qui obcaecati sunt enim libero! Dolore molestiae animi, nisi quod quis labore architecto explicabo sit ipsam quam. Quo error animi ipsuciendis neque nemo excepturi vitae labore. Eveniet.
    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Dicta vitae qui optio.
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores laboriosam sint eos doloribus minima magnam explicabo at saepe a repudiandae.</p>
  </div>
  <div class="about">
    <h2>About</h2>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Earum dolorem nesciunt at, sit corrupti quod molestias ullam fuga recusandae eum saepe ipsum rem vitae a.
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores laboriosam sint eos doloribus minima magnam explicabo at saepe a repudiandae.
    Lorem ipsum, dolor sit amet consectetur adipisicing elit. Esse fuga laborum id excepturi molestias, numquam, dignissimos qui obcaecati sunt enim libero! Dolore molestiae animi, nisi quod quis labore architecto explicabo sit ipsam quam. Quo error animi ipsum beatae? Exercitationem reiciendis neque nemo excepturi vitae labore. Eveniet.</p>
  </div>
</div>
</template>

<style scoped>

 .about {
    width: 70%;
    padding: 2rem;
    margin: 2rem auto;
    border: 1px solid #ccc;
    border-radius: 5px;
    color: #2c3e50;
    box-shadow: 0 0 10px #14141433;
    counter-increment: about;
  }

  .about h2 {
    font-size: 2rem;
    margin-bottom: 1rem;
    text-align: center;
  }

  .about h2::after{
    content: "#magical_after_counter " counter(about);
    margin-left: 1rem;
    font-size: 1rem;
    font-style: italic;
  }

  p {
    margin-bottom: 1rem;
    text-align: justify;
  }

</style>
