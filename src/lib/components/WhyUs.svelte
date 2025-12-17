<script>
  import SectionLabel from './SectionLabel.svelte';
</script>

<section class="bg-[#f5f5f5] px-6 py-24">
  <div class="max-w-[1400px] mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12">
    <div class="lg:col-span-3">
      <SectionLabel label="Why Pump Oracle" />
    </div>
    
    <div class="lg:col-span-9 grid grid-cols-1 md:grid-cols-2 gap-16">
      <div>
        <h2 class="font-serif text-3xl md:text-4xl leading-tight text-gray-900 mb-6">
          Stop wasting hours on risky Pump.fun tokens—get instant AI-powered insights
        </h2>
        <p class="text-gray-500 leading-relaxed">
          Our AI oracle analyzes token risks, holder patterns, and market trends in real-time, helping you make confident decisions in seconds instead of hours.
        </p>
      </div>
      
      <div class="flex gap-12 items-end pb-2">
        <div class="flex flex-col gap-1">
            <span class="text-4xl font-bold text-gray-900">100K+</span>
            <span class="text-xs text-gray-400">tokens analyzed</span>
        </div>
        <div class="flex flex-col gap-1">
            <span class="text-4xl font-bold text-gray-900">95%</span>
            <span class="text-xs text-gray-400">scam detection rate</span>
        </div>
      </div>
    </div>
  </div>
</section>
