<template>
  <main class="bg-dark flex-fill overflow-auto">
    <div class="content d-flex h-100 flex-column">
      <!-- top menu -->
      <div class="pt-2 pt-md-4 pb-2 px-4">
        <div class="d-flex align-items-center">
          <b-button
            v-b-tooltip.hover
            title="Marcar como Favorito"
            class="shadow mr-2"
            size="sm"
            variant="outline-warning"
            ><b-icon icon="star" area-hidden="true"></b-icon>
          </b-button>
          <b-button
            v-b-tooltip.hover
            title="Guardar Snippet"
            class="shadow mr-2"
            size="sm"
            variant="outline-success"
            ><b-icon icon="cloud-upload" area-hidden="true"></b-icon>
          </b-button>
          <b-button
            v-b-tooltip.hover
            title="Modo Nocturno"
            class="shadow mr-2 ml-auto"
            size="sm"
            variant="outline-primary"
          >
            <b-icon icon="brightness-alt-high-fill" area-hidden="true"></b-icon>
          </b-button>
        </div>
      </div>
      <div
        v-if="Object.keys(snippet).length > 0"
        class="d-flex flex-column align-items-center mt-5"
      >
        <pre>{{ snippet.id }}</pre>
        <pre>{{ snippet.titulo }}</pre>
        <pre>{{ snippet.lenguaje }}</pre>
        <pre>{{ snippet.creado }}</pre>
        <pre>{{ snippet.contenido }}</pre>
      </div>
      <!-- if empty: empty template -->
      <div v-else class="d-flex flex-column align-items-center mt-5">
        <!-- icon -->
        <div class="pt-3 px-2">
          <b-icon
            icon="file-earmark"
            variant="secondary"
            font-scale="4"
            area-hidden="true"
          ></b-icon>
        </div>
        <div class="p-3">
          <!-- title -->
          <p class="lead text-white">
            Selecciona un Snippet para ver el contenido.
          </p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    snippet: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style></style>
