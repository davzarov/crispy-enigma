<template>
  <div class="vh-100 d-flex">
    <!-- sidebar column -->
    <div class="d-lg-flex">
      <!-- directories, favs and tags -->
      <nav class="vh-100 bg-dark py-4 d-inline-block" style="width: 240px;">
        <div class="h-100 px-4 text-white overflow-auto">
          <!-- libraries -->
          <p class="lead mb-4">Librería</p>
          <div class="d-flex flex-column">
            <p class="text-white mb-0 p-3 rounded-pill">
              <b-icon class="mr-2" icon="file-earmark"></b-icon>Todos
            </p>
            <p class="text-white mb-0 p-3 rounded-pill">
              <b-icon class="mr-2" icon="star"></b-icon>Favoritos
            </p>
          </div>
          <!-- folders -->
          <div class="d-flex align-items-center justify-content-between">
            <p class="lead my-4">Carpetas</p>
            <b-avatar
              v-b-tooltip.hover
              title="Nueva Carpeta"
              button
              size="2em"
              icon="plus-circle"
              variant="dark"
            ></b-avatar>
          </div>
          <div class="d-flex flex-column">
            <div
              v-for="carpeta in carpetas"
              :key="carpeta.id"
              class="text-white mb-0 p-3 rounded-pill"
            >
              <div class="d-flex align-items-center justify-content-between">
                <div>
                  <b-icon class="mr-2" icon="folder"></b-icon
                  >{{ carpeta.titulo }}
                </div>
                <b-avatar
                  button
                  size="2em"
                  icon="three-dots"
                  variant="dark"
                ></b-avatar>
              </div>
            </div>
          </div>
          <!-- etiquetas -->
          <div class="d-flex align-items-center justify-content-between">
            <p class="lead my-4">Etiquetas</p>
            <b-avatar
              v-b-tooltip.hover
              title="Nueva Etiqueta"
              button
              size="2em"
              icon="plus-circle"
              variant="dark"
            ></b-avatar>
          </div>
          <div class="d-flex flex-column">
            <div
              v-for="etiqueta in etiquetas"
              :key="etiqueta.id"
              class="text-white mb-0 p-3 rounded-pill"
            >
              <b-icon class="mr-2" icon="tag"></b-icon>{{ etiqueta.titulo }}
            </div>
          </div>
        </div>
      </nav>
      <!-- snippet list -->
      <div
        class="position-relative bg-secondary d-inline-block"
        style="width: 300px;"
      >
        <!-- top input -->
        <div class="pt-4 px-4">
          <div class="d-flex align-items-center">
            <!-- search input -->
            <b-input-group size="sm">
              <template v-slot:prepend>
                <b-input-group-text>
                  <b-icon icon="search"></b-icon>
                </b-input-group-text>
              </template>
              <b-form-input
                placeholder="Términos de búsqueda..."
              ></b-form-input>
            </b-input-group>
          </div>
        </div>
        <!-- snippet list container -->
        <div
          class="mt-3 pt-3 pb-4 px-4 overflow-auto"
          style="height: calc(-5rem + 100vh);"
        >
          <!-- snippet cards -->
          <!-- TODO: cambiar border-variant al hacer click -->
          <b-card
            v-for="snippet in snippets"
            :key="snippet.id"
            :title="snippet.titulo"
            bg-variant="dark"
            text-variant="white"
            class="shadow mb-3"
            sub-title=""
          >
            <div class="clearfix">
              <b-card-text class="float-left mb-0">{{
                snippet.lenguaje
              }}</b-card-text>
              <b-card-text class="float-right mb-0">{{
                snippet.creado
              }}</b-card-text>
            </div>
          </b-card>
        </div>
      </div>
    </div>
    <!-- content column -->
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
              <b-icon
                icon="brightness-alt-high-fill"
                area-hidden="true"
              ></b-icon>
            </b-button>
          </div>
        </div>
        <!-- if empty: empty template -->
        <div class="d-flex flex-column align-items-center mt-5">
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
        <!-- else: content template -->
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data: () => ({
    snippets: [
      {
        id: 1,
        titulo: 'Hola, mundo!',
        lenguaje: 'Python',
        creado: new Date().toLocaleString(undefined, {
          month: 'long',
          year: 'numeric',
        }),
        contenido: `Lorem, ipsum dolor sit amet consectetur adipisicing elit.
          Delectus porro officiis quo ullam eius culpa.
          Lorem, ipsum dolor sit amet consectetur adipisicing elit.
          Delectus porro officiis quo ullam eius culpa.
          Lorem, ipsum dolor sit amet consectetur adipisicing elit.
          Delectus porro officiis quo ullam eius culpa.`,
      },
      {
        id: 2,
        titulo: 'Segundo Snippet',
        lenguaje: 'Vue.js',
        creado: new Date().toLocaleString(undefined, {
          month: 'long',
          year: 'numeric',
        }),
        contenido: `Lorem, ipsum dolor sit amet consectetur adipisicing elit.
          Delectus porro officiis quo ullam eius culpa.
          Lorem, ipsum dolor sit amet consectetur adipisicing elit.
          Delectus porro officiis quo ullam eius culpa.
          Lorem, ipsum dolor sit amet consectetur adipisicing elit.
          Delectus porro officiis quo ullam eius culpa.`,
      },
    ],
    carpetas: [
      { id: 1, titulo: 'Mi Carpeta' },
      { id: 2, titulo: 'Python' },
      { id: 3, titulo: 'Vue.js' },
      { id: 4, titulo: 'Frontend' },
    ],
    etiquetas: [
      { id: 1, titulo: 'Python' },
      { id: 2, titulo: 'Javascript' },
      { id: 3, titulo: 'Django' },
      { id: 4, titulo: 'Flask' },
      { id: 5, titulo: 'Nuxt.js' },
      { id: 6, titulo: 'Vue.js' },
    ],
  }),
}
</script>

<style></style>
