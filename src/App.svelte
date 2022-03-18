<script >


  let tarea = "";
  let listaTareas = [
    { texto: "Primera tarea", estado: true },
    { texto: "Segunda tarea", estado: false },
    { texto: "Tercera tarea", estado: false }
  ];

  function agregarTarea() {
    listaTareas = [
      ...listaTareas,
      {
        texto: tarea,
        estado: false
      }
    ];
    tarea = "";
  }

  function eliminarTarea(index) {
    listaTareas.splice(index, 1);
    listaTareas = [...listaTareas];
  }
</script>

<main>
  <h1>Tareas</h1>
  <div class="contenedor">
    <input bind:value={tarea} type="text" placeholder="Agregar nuevo item" />
    <button on:click={agregarTarea}>Agregar</button>
    <br />
  </div>

  {#each listaTareas as tarea, index}
    <div class="contenedor">
      <input type="checkbox" bind:checked={tarea.estado} />
      <span class:checked={tarea.estado}>{tarea.texto}</span>
      <span
        on:click={() => {
          eliminarTarea(index);
        }}>❌</span
      >
    </div>
  {/each}
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .contenedor {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }
  .contenedor > * {
    margin: 0.5rem;
  }
</style>
