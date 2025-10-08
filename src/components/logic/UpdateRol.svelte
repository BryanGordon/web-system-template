<script lang="ts">
  export let name: string;
  export let userRol: string;
  export let userId: string;

  let newRol = ""

  const localdb = `http://localhost:3000/users/${userId}`
  const supadb = `http://localhost:3000/supa/users/update/${userId}`

  async function handleSubmit(event: Event) {
    event.preventDefault()

    try {
      await fetch(supadb, {
        method: "PATCH",
        body: JSON.stringify({ rol: newRol}),
        headers: {
          "Content-Type": "application/json"
        }
      })
      alert("Se ha actualizado correctamente")
    }

    catch(e) {
      alert("No se ha podido actualizar.")
      console.error(e)
    }
  }

</script>

  <article>
    <header>
      <h1>Actualizar rol de usuario</h1>
      <p>Rol actual: {userRol}</p>
      <a href={`/users/${name}`}>Volver al usuario</a>
    </header>

    <form on:submit={handleSubmit}>
      <input id="newRol" type="text" placeholder="Coloque un nuevo rol" bind:value={newRol}/>
      <button type="submit">Cambiar</button>
    </form>
  </article>

   <style>
    h1 {
      text-align: center;
      margin-top: 50px;
    }

    p {
      color: #b5b3b9;
      font-weight: 500;
      width: 100%;
      text-align: center;
    }

    form {
      display: flex;
      width: 65%;
      margin: 0 auto;
      margin-top: 60px;
      flex-direction: column;
      
      & input, button {
        margin: 0 auto;
      }

      & input {
        padding: 5px 20px;
        border-radius: 5px;

        &:focus-visible {
          outline: none;
          background-color: #c0c0c1f7;
        }
      }

      & button {
        border: 0;
        padding: 10px;
        border-radius: 4px;
        margin-top: 45px;
      }
    }

    a {
      color: whitesmoke;
      margin-left: 60px;
      text-decoration: none;
    }
  </style>