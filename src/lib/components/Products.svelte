<script>
  import SectionLabel from './SectionLabel.svelte';
</script>

<section class="bg-[#f5f5f5] px-6 py-24 border-t border-gray-200">
  <div class="max-w-[1400px] mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12">
    <div class="lg:col-span-3">
      <SectionLabel label="Features" />
    </div>
    
    <div class="lg:col-span-9">
      <div class="mb-16">
        <h2 class="font-serif text-4xl md:text-5xl text-gray-900 mb-2">
          AI-powered analysis
        </h2>
        <h2 class="font-serif text-4xl md:text-5xl text-gray-400">
          for smarter crypto decisions
        </h2>
      </div>

      <div class="grid gap-0 border-t border-gray-200">
        <!-- Item 1 -->
        <a href="/" class="group grid grid-cols-1 md:grid-cols-12 gap-6 py-10 border-b border-gray-200 hover:bg-white transition-colors px-4 -mx-4">
          <div class="md:col-span-4">
            <div class="text-xs text-gray-400 mb-1">Real-time protection</div>
            <h3 class="text-2xl font-medium text-gray-900">Risk Scoring & Scam Detection</h3>
          </div>
          <div class="md:col-span-7">
            <p class="text-gray-500 leading-relaxed">
              Instantly identify risky tokens with our AI-powered risk scoring system. Get alerts on potential scams, rug pulls, and suspicious holder patterns before you invest.
            </p>
          </div>
          <div class="md:col-span-1 flex justify-end items-start pt-2">
            <svg class="w-6 h-6 text-gray-400 group-hover:text-black transform group-hover:translate-x-1 transition-all" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
          </div>
        </a>

        <!-- Item 2 -->
        <a href="/" class="group grid grid-cols-1 md:grid-cols-12 gap-6 py-10 border-b border-gray-200 hover:bg-white transition-colors px-4 -mx-4">
          <div class="md:col-span-4">
            <div class="text-xs text-gray-400 mb-1">Market intelligence</div>
            <h3 class="text-2xl font-medium text-gray-900">Trend Analysis & Predictions</h3>
          </div>
          <div class="md:col-span-7">
            <p class="text-gray-500 leading-relaxed">
              Track market trends and get AI-powered predictions on token performance. Analyze holder behavior, trading volume, and social sentiment to spot opportunities early.
            </p>
          </div>
          <div class="md:col-span-1 flex justify-end items-start pt-2">
            <svg class="w-6 h-6 text-gray-400 group-hover:text-black transform group-hover:translate-x-1 transition-all" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
          </div>
        </a>

        <!-- Item 3 -->
        <a href="/" class="group grid grid-cols-1 md:grid-cols-12 gap-6 py-10 border-b border-gray-200 hover:bg-white transition-colors px-4 -mx-4">
          <div class="md:col-span-4">
            <div class="text-xs text-gray-400 mb-1">Developer access</div>
            <h3 class="text-2xl font-medium text-gray-900">API Integration</h3>
          </div>
          <div class="md:col-span-7">
            <p class="text-gray-500 leading-relaxed">
              Integrate Pump Oracle's AI analysis directly into your trading bots, platforms, or applications. Scale to 100K+ analyses with our specialized oracle infrastructure.
            </p>
          </div>
          <div class="md:col-span-1 flex justify-end items-start pt-2">
            <svg class="w-6 h-6 text-gray-400 group-hover:text-black transform group-hover:translate-x-1 transition-all" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
          </div>
        </a>
      </div>
    </div>
  </div>
</section>
