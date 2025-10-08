<script lang="ts">

  let name: string = ''
  let total: number | null = null
  let price: number | null = null
  let id: string = ''

  function handleCreate(e: Event) {
    e.preventDefault()

    const newProduct = {
      id: id,
      name: name,
      total: total,
      price: price, 
    }

    try {
      fetch('http://localhost:3000/add', {
        method: 'POST',
        body: JSON.stringify(newProduct),
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
      <input id="inputName" type="text" placeholder="Pan" bind:value={name} />
    </div>

    <div>
      <label for="inputSurname">Ingrese la cantidad total de productos:</label>
      <input id="inputSurname" type="number" placeholder="20" bind:value={total} />
    </div>

    <div>
      <label for="inputEmail">Ingrese el precio del producto:</label>
      <input id="inputEmail" type="number" step="0.01" placeholder="1.50" bind:value={price} />
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

  input[type="number"]::-webkit-inner-spin-button,
  input[type="number"]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
</style>