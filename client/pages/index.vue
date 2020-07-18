<template>
  <div class="vh-100 d-flex">
    <!-- sidebar column -->
    <Sidebar
      :carpetas="carpetas"
      :etiquetas="etiquetas"
      :snippets="snippets"
      @selectedSnippet="showSnippet"
    />
    <!-- content column -->
    <Content :snippet="snippet" />
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
    snippet: {},
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
  methods: {
    showSnippet(snippetId) {
      this.snippet = this.snippets.find((snippet) => snippet.id === snippetId)
    },
  },
}
</script>

<style></style>
