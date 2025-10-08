<script lang="ts">

  let name: string = ''
  let apellido: string = ''
  let correo: string = ''
  let rol: string = ''
  let id: string = ''

  const localdb = 'http://localhost:3000/users/add'
  const supadb = 'http://localhost:3000/supa/users/'

  function handleCreate(e: Event) {
    e.preventDefault()

    const newUser = {
      id: id,
      name: name,
      apellido: apellido,
      correo: correo, 
      rol: rol
    }

    try {
      fetch(supadb, {
        method: 'POST',
        body: JSON.stringify(newUser),
        headers: {
          'Content-Type': 'application/json'
        }
      })
      alert('Usuario creado con exito')
    }
    catch(e) {
      console.error(e)
      alert('Error al crear al usuario')
    }
  }

</script>

<article>
  <form on:submit={handleCreate}>
    <div>
      <label for="inputName">Ingrese un nombre:</label>
      <input id="inputName" type="text" placeholder="Juan Carlos" bind:value={name} />
    </div>

    <div>
      <label for="inputSurname">Ingrese un apellido:</label>
      <input id="inputSurname" type="text" placeholder="Garcia" bind:value={apellido} />
    </div>

    <div>
      <label for="inputEmail">Ingrese un correo:</label>
      <input id="inputEmail" type="text" placeholder="alguien@correo.com" bind:value={correo} />
    </div>

    <div>
      <label for="inputRol">Ingrese un rol:</label>
      <input id="inputRol" type="text" placeholder="Admin/Trabajador" bind:value={rol} />
    </div>

    <div>
      <label for="idField">Ingrese un id:</label>
      <input id="idField" type="text" bind:value={id} />
    </div>

    <button type="submit">Crear</button>
  </form>
</article>

<style>
  form {
    display: flex;
    width: 65%;
    margin: 0 auto;
    margin-top: 60px;
    margin-bottom: 50px;
    flex-direction: column;
  }

  div {
    display: grid;
    margin-block: 15px;

    & input {
      margin-top: 5px;
      width: 50%;
      border: 0;
      border-radius: 4px;
      background-color: #c7c7c7;
      padding: 7px;

      &:focus-visible {
          outline: none;
          background-color: #c0c0c1e6;
        }
    }
  }

  label {
    margin-right: 15px;
  }

  button:hover {
    cursor: pointer;
    background-color: #473d8bc6;
    color: whitesmoke;
  }

  button {
    width: 30%;
    margin: 0 auto;
    border-radius: 10px;
    margin-top: 25px;
    padding: 8px 15px;
    border: 0;
    transition: all 0.2s ease-in ;
  }
</style>