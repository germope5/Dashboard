<!--
  App.svelte — Showcase de componentes Atomic Design
  Esta vista de ejemplo muestra los tres niveles: Átomo, Molécula y Organismo.
-->
<script lang="ts">
  import Button from "./components/atoms/Button.svelte";
  import Input from "./components/atoms/Input.svelte";
  import SearchBar from "./components/molecules/SearchBar.svelte";
  import Sidebar from "./components/organisms/Sidebar.svelte";



  // Opción 2: Objeto con propiedades (más escalable para formularios)
  let formData = {
     nombre: "",
     apellido: "",
     email: "",
     password: "",
     number: "",
     disabled: ""
   };

  let searchQuery: string = "";

  function handleSearch(e: CustomEvent<{ query: string }>): void {
    alert(`Buscando: ${e.detail.query}`);
  }
</script>

<div class="app">
  <!-- ORGANISM: Sidebar -->
  <Sidebar />

  <!-- Main Content Area -->
  <main class="main">
    <header class="main__header">
      <h1 class="main__title">🧪 Atomic Design — Componentes de ejemplo</h1>
      <p class="main__subtitle">
        Cada nivel del sistema de diseño representado con un componente
        funcional.
      </p>
    </header>

    <!-- ATOM Section -->
    <section class="section">
      <h2 class="section__title">
        <span class="section__badge section__badge--atom">Átomos</span>
        Button
      </h2>
      <p class="section__desc">
        El componente más básico e indivisible. Acepta <code>variant</code>,
        <code>size</code>
        y <code>disabled</code> como props.
      </p>
      <div class="section__demo">
        <Button label="Primary" variant="primary" />
        <Button label="Secondary" variant="secondary" />
        <Button label="Danger" variant="danger" />
        <Button label="Small" variant="primary" size="sm" />
        <Button label="Large" variant="primary" size="lg" />
        <Button label="Disabled" variant="primary" disabled={true} />
      </div>
    </section>
    <section class="section">
      <h2 class="section__title">
        <span class="section__badge section__badge--atom">Átomos</span>
        Input
      </h2>
      <p class="section__desc">
        Te permite ingresar una entrada de: texto,contraseña,etc Acepta
        <code>type</code>,
        <code>placeholder</code>,
        <code>label</code>,
        <code>disabled</code> como props.
      </p>
      <div class="section__demo">
        <Input
          id="nombre"
          label="Nombre"
          bind:value={formData.nombre}
          type="text"
        />
        <Input
          id="apellido"
          label="Apellido"
          bind:value={formData.apellido}
          type="text"
        />
        <Input id="email" label="Email" bind:value={formData.email} type="email" />
        <Input
          id="password"
          label="Password"
          bind:value={formData.password}
          type="password"
        />
        <Input
          id="number"
          label="Number"
          bind:value={formData.number}
          type="number"
        />
        <Input
          id="disabled"
          label="Disabled"
          bind:value={formData.disabled}
          disabled={true}
        />
      </div>
    </section>

    <!-- MOLECULE Section -->
    <section class="section">
      <h2 class="section__title">
        <span class="section__badge section__badge--molecule">Moléculas</span>
        SearchBar
      </h2>
      <p class="section__desc">
        Combina un <code>input</code> + <code>Button</code> para crear una barra
        de búsqueda funcional.
      </p>
      <div class="section__demo">
        <SearchBar bind:value={searchQuery} on:search={handleSearch} />
      </div>
    </section>

    <!-- ORGANISM Section -->
    <section class="section">
      <h2 class="section__title">
        <span class="section__badge section__badge--organism">Organismos</span>
        Sidebar
      </h2>
      <p class="section__desc">
        Una sección completa de UI: logo + navegación + botón de cerrar sesión.
        Se muestra a la izquierda de esta página.
      </p>
    </section>
  </main>
</div>

<style>
  :global(body) {
    margin: 0;
    background: #0a0a1a;
    color: #e0e7ff;
    font-family:
      "Inter",
      system-ui,
      -apple-system,
      sans-serif;
  }

  .app {
    display: flex;
    min-height: 100vh;
  }

  .main {
    flex: 1;
    padding: 40px 48px;
    overflow-y: auto;
  }

  .main__header {
    margin-bottom: 40px;
  }

  .main__title {
    font-size: 1.8rem;
    font-weight: 800;
    margin: 0 0 8px;
    background: linear-gradient(135deg, #a78bfa, #6366f1);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .main__subtitle {
    color: rgba(199, 210, 254, 0.6);
    font-size: 1rem;
    margin: 0;
  }

  /* — Sections — */
  .section {
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.07);
    border-radius: 16px;
    padding: 28px 32px;
    margin-bottom: 24px;
  }

  .section__title {
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 1.15rem;
    font-weight: 700;
    margin: 0 0 8px;
  }

  .section__badge {
    font-size: 0.7rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    padding: 3px 10px;
    border-radius: 6px;
  }

  .section__badge--atom {
    background: rgba(99, 102, 241, 0.2);
    color: #a5b4fc;
  }
  .section__badge--molecule {
    background: rgba(16, 185, 129, 0.2);
    color: #6ee7b7;
  }
  .section__badge--organism {
    background: rgba(245, 158, 11, 0.2);
    color: #fcd34d;
  }

  .section__desc {
    color: rgba(199, 210, 254, 0.6);
    font-size: 0.9rem;
    margin: 0 0 20px;
    line-height: 1.5;
  }

  .section__desc code {
    background: rgba(99, 102, 241, 0.15);
    padding: 2px 6px;
    border-radius: 4px;
    font-size: 0.85rem;
    color: #a5b4fc;
  }

  .section__demo {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    align-items: center;
  }
</style>
