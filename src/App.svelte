<!-- @format -->
<script>
  import ButtonGoUp from "./ButtonGoUp.svelte"

  let date = new Date().toISOString().slice(0, 10)
  $: src = `https://www.google.com/search?q=%http://www.patriarchia.ru/bu/${date}/print.html`
</script>
<div
  id="top"
  class="d-flex flex-column"
  style="min-height: 100vh;"
>
  <div
    class="sticky-bottom d-flex gap-1 align-items-center w-100 bg-light text-dark p-2"
  >
    <div class="d-flex flex-grow-1">
      <div class="input-group">
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <span
          class="btn btn-light text-dark bg-transparent border"
          style="cursor:default;"
          on:click={() => {
            date = new Date().toISOString().slice(0, 10)
          }}>Дата:</span
        >
        <input
          type="date"
          class="form-control bg-opacity-10"
          title="Выберите дату"
          bind:value={date}
        />
        <button
          class="btn btn-light text-dark border"
          title="Предыдущий день"
          on:click={() => {
            let dateNext = new Date(date)
            dateNext.setDate(dateNext.getDate() - 1)
            date = dateNext.toISOString().slice(0, 10)
          }}><i class="fa-solid fa-arrow-left" /></button
        >
        <button
          class="btn btn-light text-dark border"
          title="Следующий день"
          on:click={() => {
            let dateNext = new Date(date)
            dateNext.setDate(dateNext.getDate() + 1)
            date = dateNext.toISOString().slice(0, 10)
          }}><i class="fa-solid fa-arrow-right" /></button
        >
      </div>
    </div>

    <div class="d-flex">
      <div class="input-group">
        <button
          class="btn btn-light text-dark border"
          on:click={() => (date = new Date().toISOString().slice(0, 10))}
          >Сегодня</button
        >
      </div>
    </div>
  </div>

  <!-- svelte-ignore a11y-missing-attribute -->
  <iframe
    class="flex-grow-1"
    src={src}
    frameborder="0"
  />
</div>
