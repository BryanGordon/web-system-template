<script lang="ts">
  export let userName: string
  export let userId: string

  let newName = ''

  function handleName(e: Event) {
    e.preventDefault()

    try {
      fetch(`http://localhost:3000/users/update/${userId}`, {
        method: 'PATCH',
        body: JSON.stringify({name: newName}),
        headers: {
          'Content-Type': 'application/json'
        }
      })

      alert('Nombre de usuario actualizado correctamente.')
    }
    catch (e) {
      console.error(e)
      alert('No se ha podido actualizar el nombre del usuario.')
    }
  }
</script>

<article>
  <header>
    <h1>Actualizar nombre de usuario</h1>
    <p>Nombre actual: {userName}</p>
    <!--Cambiar el parametro de otra maner asi no funciona bien, chapucero-->
    <a href={`/users/${newName}`}>Volver al usuario</a>
  </header>
  <form on:submit={handleName}>
    <input id="newName" type="text" placeholder="Raul" bind:value={newName}/>
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