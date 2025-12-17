<script lang="ts">
  import Navbar from '$lib/components/Navbar.svelte';
  import ChatInterface from '$lib/components/ChatInterface.svelte';
  import Footer from '$lib/components/Footer.svelte';
</script>

<div class="min-h-screen font-sans selection:bg-primary-600 selection:text-white" style="background: var(--dark-bg);">
  <Navbar />
  <ChatInterface />
  <Footer />
</div>

