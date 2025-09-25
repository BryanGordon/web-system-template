<script lang="ts">

</script>

<article>
  <form action="">
    <div>
      <label for="">Ingrese un nombre:</label>
      <input type="text" placeholder="Juan Carlos" />
    </div>

    <div>
      <label for="">Ingrese un apellido:</label>
      <input type="text" placeholder="Garcia" />
    </div>

    <div>
      <label for="">Ingrese un correo:</label>
      <input type="text" placeholder="alguien@correo.com">
    </div>

    <div>
      <label for="">Ingrese un rol:</label>
      <input type="text" placeholder="Admin/Trabajador" />
    </div>

    <div>
      <label for="">Ingrese un id:</label>
      <input type="text" />
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