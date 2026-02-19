<!--
  ATOM: Input
  Campo de entrada de texto genérico.
  Props:
    - value (string)       : Valor del input (bind:value)
    - type (string)        : "text" | "password" | "email" | "number" (default: "text")
    - placeholder (string) : Texto de ayuda
    - label (string)       : Etiqueta opcional
    - disabled (boolean)   : Deshabilitar el input
    - id (string)          : ID único (opcional)
  Events:
    - on:input  : Se emite al escribir
    - on:change : Se emite al cambiar el valor
    - on:blur   : Se emite al perder el foco
-->
<script lang="ts">
  export let value: string = "";
  export let type: "text" | "password" | "email" | "number" = "text";
  export let placeholder: string = "";
  export let label: string = "";
  export let disabled: boolean = false;
  export let id: string = `input-${Math.random().toString(36).substr(2, 9)}`;
</script>

<div class="input-group">
  {#if label}
    <label class="input-label" for={id}>
      {label}
    </label>
  {/if}

  <div class="input-wrapper">
    <input
      {id}
      {type}
      class="input-control"
      {placeholder}
      {disabled}
      bind:value
      on:input
      on:change
      on:blur
      on:keydown
    />
  </div>
</div>

<style>
  .input-group {
    display: flex;
    flex-direction: column;
    gap: 6px;
    width: 40%;
    font-family: "Inter", sans-serif;
  }

  .input-label {
    font-size: 0.85rem;
    font-weight: 500;
    color: rgba(224, 231, 255, 0.7);
    margin-left: 2px;
  }

  .input-wrapper {
    position: relative;
    width: 100%;
  }

  .input-control {
    width: 100%;
    box-sizing: border-box;
    padding: 10px 14px;
    font-size: 0.95rem;
    color: #e0e7ff;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 8px;
    transition: all 0.2s ease;
    outline: none;
  }

  .input-control::placeholder {
    color: rgba(199, 210, 254, 0.3);
  }

  .input-control:hover:not(:disabled) {
    border-color: rgba(255, 255, 255, 0.2);
    background: rgba(255, 255, 255, 0.08);
  }

  .input-control:focus:not(:disabled) {
    border-color: #6366f1;
    box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.15);
    background: rgba(255, 255, 255, 0.1);
  }

  .input-control:disabled {
    opacity: 0.5;
    cursor: not-allowed;
    background: rgba(0, 0, 0, 0.2);
  }
</style>
