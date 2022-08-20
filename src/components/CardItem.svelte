<script>
  export let item;
</script>

<div class="card">
  <img src={item.url} alt="" class="img-fluid">
  <h3 class="__title">{item.title}</h3>
  <p class="__text">{item.body}</p>
</div>
  
<style>
  .card {
    display: flex;
    flex-direction: column;
    gap: 20px;
    border: 1px solid #b2bac2;
    background-color: #132f4c;
    color: #fff;
    border-radius: 15px;
    padding: 1rem;
    /* margin: 20px; */
    position: relative;
  }
  img{
    height: 160px;
    width: 100%;
    object-fit: cover;
  }
  .__title{
    font-size: 1rem;
    font-weight: semi-bold;
  }
</style>