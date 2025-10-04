<script lang="ts">
  export let productName: string

  function handleDelete () {
    try {
      fetch(`http://localhost:3000/${productName}`, {
        method: 'DELETE'
      })
      alert('Se ha borrado el producto correctamente')
      window.location.href = '/products'
    } catch (e) {
      console.log(e)
      alert("No se ha podido eliminar el producto")
    }
  }
</script>

<div>
  <button on:click={handleDelete}>Borrar</button>
</div>

<style>
  div {
    margin-block: 25px;
    align-items: center;
    text-align: center;
  }

  button:hover {
    background-color: #dc143ca4;
    color: white;
  }

  button {
    height: 45px;
    border: 0;
    line-height: 25px;
    padding: 10px 15px;
    background: crimson;
    color: whitesmoke;
    border-radius: 4px;
    text-decoration: none;
    transition: all 0.3s ease;
    cursor: pointer;
  }
</style>