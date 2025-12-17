<script>
  import Navbar from '$lib/components/Navbar.svelte';
  import Hero from '$lib/components/Hero.svelte';
  import Logos from '$lib/components/Logos.svelte';
  import WhyUs from '$lib/components/WhyUs.svelte';
  import Products from '$lib/components/Products.svelte';
  import Founders from '$lib/components/Founders.svelte';
  import FAQ from '$lib/components/FAQ.svelte';
  import BottomCTA from '$lib/components/BottomCTA.svelte';
  import Footer from '$lib/components/Footer.svelte';
</script>

<div class="min-h-screen bg-[#f5f5f5] font-sans selection:bg-primary-600 selection:text-white">
  <Navbar />
  <Hero />
  <Logos />
  <WhyUs />
  <Products />
  <Founders />
  <FAQ />
  <BottomCTA />
  <Footer />
</div>

