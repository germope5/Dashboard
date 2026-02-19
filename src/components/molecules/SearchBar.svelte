<!--
  MOLECULE: SearchBar
  Combina un input de texto + un Button (átomo) para formar
  una barra de búsqueda reutilizable.
  Props:
    - placeholder (string) : Placeholder del input
    - value (string)       : Valor actual del input (bind:value)
  Events:
    - on:search : Se emite con el valor actual al hacer clic en buscar
-->
<script>
  import Button from '../atoms/Button.svelte';

  /** @type {string} */
  export let placeholder = 'Buscar...';

  /** @type {string} */
  export let value = '';

  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  function handleSearch() {
    dispatch('search', { query: value });
  }

  function handleKeydown(e) {
    if (e.key === 'Enter') handleSearch();
  }
</script>

<div class="search-bar">
  <div class="search-input-wrapper">
    <svg class="search-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
      <circle cx="11" cy="11" r="8" />
      <path d="m21 21-4.35-4.35" />
    </svg>
    <input
      type="text"
      class="search-input"
      {placeholder}
      bind:value
      on:keydown={handleKeydown}
    />
  </div>
  <Button label="Buscar" variant="primary" size="sm" on:click={handleSearch} />
</div>

<style>
  .search-bar {
    display: flex;
    align-items: center;
    gap: 10px;
    background: rgba(255, 255, 255, 0.06);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 12px;
    padding: 6px 8px 6px 6px;
    transition: border-color 0.2s ease, box-shadow 0.2s ease;
  }

  .search-bar:focus-within {
    border-color: rgba(99, 102, 241, 0.5);
    box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.15);
  }

  .search-input-wrapper {
    display: flex;
    align-items: center;
    flex: 1;
    gap: 8px;
  }

  .search-icon {
    width: 18px;
    height: 18px;
    color: rgba(199, 210, 254, 0.5);
    flex-shrink: 0;
    margin-left: 6px;
  }

  .search-input {
    flex: 1;
    border: none;
    outline: none;
    background: transparent;
    color: #e0e7ff;
    font-size: 0.9rem;
    font-family: 'Inter', sans-serif;
    padding: 6px 4px;
  }

  .search-input::placeholder {
    color: rgba(199, 210, 254, 0.4);
  }
</style>
