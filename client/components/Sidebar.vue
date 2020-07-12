<template>
  <div class="d-lg-flex">
    <!-- folders and tags -->
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
                <b-icon class="mr-2" icon="folder"></b-icon>{{ carpeta.titulo }}
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
            <div class="d-flex align-items-center justify-content-between">
              <div>
                <b-icon class="mr-2" icon="tag"></b-icon>{{ etiqueta.titulo }}
              </div>
              <b-avatar
                button
                size="2em"
                icon="x"
                variant="dark"
                @click="confirmTagDeletion"
              ></b-avatar>
            </div>
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
            <b-form-input placeholder="Términos de búsqueda..."></b-form-input>
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
</template>

<script>
export default {
  props: {
    carpetas: {
      type: Array,
      default: () => [],
    },
    etiquetas: {
      type: Array,
      default: () => [],
    },
    snippets: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      tagResponse: '',
      modalDeleteOptions: {
        title: 'Desea eliminar esto?',
        okVariant: 'danger',
        okTitle: 'Aceptar',
        cancelTitle: 'Cancelar',
        footerClass: 'p-2',
        hideHeaderClose: false,
      },
    }
  },
  methods: {
    confirmTagDeletion() {
      this.tagResponse = ''
      this.$bvModal
        .msgBoxConfirm(
          `Atención, la siguiente acción no se puede deshacer.
          Para seguir adelante confirme por favor.`,
          this.modalDeleteOptions
        )
        .then((res) => {
          this.tagResponse = res
          // eslint-disable-next-line
          console.log(res)
        })
        .catch((err) => {
          // eslint-disable-next-line
          console.log(err)
        })
    },
  },
}
</script>

<style></style>
