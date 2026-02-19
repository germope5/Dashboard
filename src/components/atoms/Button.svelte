<!--
  ATOM: Button
  El componente más básico e indivisible del sistema de diseño.
  Props:
    - label (string)   : Texto del botón
    - variant (string)  : "primary" | "secondary" | "danger"  (default: "primary")
    - disabled (boolean): Deshabilitar el botón
    - size (string)     : "sm" | "md" | "lg"  (default: "md")
  Events:
    - on:click : Se emite al hacer clic
-->
<script>
  /** @type {string} */
  export let label = 'Button';

  /** @type {'primary' | 'secondary' | 'danger'} */
  export let variant = 'primary';

  /** @type {boolean} */
  export let disabled = false;

  /** @type {'sm' | 'md' | 'lg'} */
  export let size = 'md';
</script>

<button
  class="btn btn--{variant} btn--{size}"
  {disabled}
  on:click
>
  {label}
</button>

<style>
  .btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    border: none;
    border-radius: 8px;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.2s ease, transform 0.1s ease, box-shadow 0.2s ease;
    font-family: 'Inter', sans-serif;
    letter-spacing: 0.02em;
  }

  .btn:active:not(:disabled) {
    transform: scale(0.97);
  }

  .btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }

  /* — Sizes — */
  .btn--sm {
    padding: 6px 14px;
    font-size: 0.8rem;
  }
  .btn--md {
    padding: 10px 22px;
    font-size: 0.95rem;
  }
  .btn--lg {
    padding: 14px 32px;
    font-size: 1.1rem;
  }

  /* — Variants — */
  .btn--primary {
    background: linear-gradient(135deg, #6366f1, #818cf8);
    color: #fff;
    box-shadow: 0 2px 8px rgba(99, 102, 241, 0.3);
  }
  .btn--primary:hover:not(:disabled) {
    background: linear-gradient(135deg, #4f46e5, #6366f1);
    box-shadow: 0 4px 14px rgba(99, 102, 241, 0.45);
  }

  .btn--secondary {
    background: rgba(255, 255, 255, 0.08);
    color: #c7d2fe;
    border: 1px solid rgba(199, 210, 254, 0.2);
  }
  .btn--secondary:hover:not(:disabled) {
    background: rgba(255, 255, 255, 0.14);
    border-color: rgba(199, 210, 254, 0.4);
  }

  .btn--danger {
    background: linear-gradient(135deg, #ef4444, #f87171);
    color: #fff;
    box-shadow: 0 2px 8px rgba(239, 68, 68, 0.3);
  }
  .btn--danger:hover:not(:disabled) {
    background: linear-gradient(135deg, #dc2626, #ef4444);
    box-shadow: 0 4px 14px rgba(239, 68, 68, 0.45);
  }
</style>
