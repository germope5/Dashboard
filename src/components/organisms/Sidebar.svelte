<!--
  ORGANISM: Sidebar
  Sección completa de la interfaz compuesta por átomos y moléculas.
  Incluye: logo/título, navegación, y un botón de cerrar sesión.
  Props:
    - title (string) : Nombre de la aplicación
    - items (array)  : Lista de { icon, label, href, active? }
-->
<script>
  import Button from '../atoms/Button.svelte';

  /** @type {string} */
  export let title = 'Dashboard';

  /** @type {Array<{icon: string, label: string, href: string, active?: boolean}>} */
  export let items = [
    { icon: '🏠', label: 'Inicio', href: '#/', active: true },
    { icon: '📊', label: 'Analíticas', href: '#/analytics' },
    { icon: '👥', label: 'Usuarios', href: '#/users' },
    { icon: '⚙️', label: 'Configuración', href: '#/settings' },
  ];
</script>

<aside class="sidebar">
  <!-- Logo / Brand -->
  <div class="sidebar__brand">
    <div class="sidebar__logo">
      <svg viewBox="0 0 32 32" fill="none">
        <rect width="32" height="32" rx="8" fill="url(#logo-grad)" />
        <path d="M10 22V10l12 6-12 6z" fill="#fff" />
        <defs>
          <linearGradient id="logo-grad" x1="0" y1="0" x2="32" y2="32">
            <stop stop-color="#6366f1" />
            <stop offset="1" stop-color="#a78bfa" />
          </linearGradient>
        </defs>
      </svg>
    </div>
    <span class="sidebar__title">{title}</span>
  </div>

  <!-- Navigation -->
  <nav class="sidebar__nav">
    {#each items as item}
      <a
        href={item.href}
        class="sidebar__link"
        class:sidebar__link--active={item.active}
      >
        <span class="sidebar__link-icon">{item.icon}</span>
        <span class="sidebar__link-label">{item.label}</span>
      </a>
    {/each}
  </nav>

  <!-- Logout -->
  <div class="sidebar__footer">
    <Button label="Cerrar sesión" variant="secondary" size="sm" />
  </div>
</aside>

<style>
  .sidebar {
    display: flex;
    flex-direction: column;
    width: 250px;
    height: 100vh;
    background: linear-gradient(180deg, #0f0f23 0%, #1a1a3e 100%);
    border-right: 1px solid rgba(255, 255, 255, 0.07);
    padding: 24px 16px;
    font-family: 'Inter', sans-serif;
  }

  /* — Brand — */
  .sidebar__brand {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 36px;
    padding: 0 4px;
  }

  .sidebar__logo svg {
    width: 36px;
    height: 36px;
  }

  .sidebar__title {
    font-size: 1.2rem;
    font-weight: 700;
    color: #e0e7ff;
    letter-spacing: 0.02em;
  }

  /* — Nav — */
  .sidebar__nav {
    display: flex;
    flex-direction: column;
    gap: 4px;
    flex: 1;
  }

  .sidebar__link {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 10px 14px;
    border-radius: 10px;
    text-decoration: none;
    color: rgba(199, 210, 254, 0.7);
    font-size: 0.9rem;
    font-weight: 500;
    transition: background 0.2s ease, color 0.2s ease;
  }

  .sidebar__link:hover {
    background: rgba(255, 255, 255, 0.06);
    color: #e0e7ff;
  }

  .sidebar__link--active {
    background: rgba(99, 102, 241, 0.15);
    color: #a5b4fc;
    font-weight: 600;
  }

  .sidebar__link-icon {
    font-size: 1.15rem;
  }

  .sidebar__link-label {
    white-space: nowrap;
  }

  /* — Footer — */
  .sidebar__footer {
    padding-top: 16px;
    border-top: 1px solid rgba(255, 255, 255, 0.07);
  }
</style>
