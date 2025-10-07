<script lang="ts">
  export let userId: string

  const localdb: string = `http://localhost:3000/users/${userId}`
  const supadb: string = `http://localhost:3000/supa/users/${userId}`

  function handleDelete() {
    try {
      fetch(supadb, {
        method: 'DELETE'
      })
      alert("Usuario borrado correctamente")
      window.location.href = '/'
    } catch (e) {
      console.log(e)
      alert("No se ha podido borrar al usuario")
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

