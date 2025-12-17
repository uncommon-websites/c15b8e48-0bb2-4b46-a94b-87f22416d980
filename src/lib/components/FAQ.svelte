<script lang="ts">
  import { slide } from 'svelte/transition';
  
  interface FAQItem {
    question: string;
    answer: string;
  }

  const faqs: FAQItem[] = [
    { question: "How does Pump Oracle's AI analysis work?", answer: "Pump Oracle uses advanced machine learning algorithms to analyze token contracts, holder patterns, trading volume, social sentiment, and historical data from Pump.fun. Our AI oracle processes thousands of data points in real-time to generate comprehensive risk scores and trend predictions." },
    { question: "What makes Pump Oracle different from DEXTools or BubbleMaps?", answer: "While other tools provide raw data visualization, Pump Oracle delivers instant AI-powered insights and actionable recommendations. Our specialized oracle focuses specifically on Pump.fun tokens, providing faster analysis and higher accuracy for scam detection compared to general-purpose tools." },
    { question: "How accurate is the scam detection?", answer: "Our AI achieves a 95% accuracy rate in identifying scam tokens and rug pulls. The system continuously learns from new patterns and is updated daily with the latest scam techniques observed across Pump.fun and other platforms." },
    { question: "Can I integrate Pump Oracle into my trading bot?", answer: "Yes! We offer a comprehensive API that allows developers to integrate our AI analysis into trading bots, Discord servers, Telegram groups, or custom applications. API access is available on our Pro and Enterprise plans." },
    { question: "What is the pricing for Pump Oracle?", answer: "We offer a free trial with limited analyses per day. Paid plans start at $29/month for individual traders with unlimited analyses, and scale up to Enterprise plans for API access and high-volume usage." },
    { question: "How fast are the analyses?", answer: "Most token analyses are completed in under 3 seconds. Our AI-specialized oracle infrastructure is designed to handle 100K+ analyses daily while maintaining sub-second response times for critical risk assessments." },
    { question: "Do you support tokens beyond Pump.fun?", answer: "Currently, Pump Oracle is optimized specifically for Pump.fun tokens on Solana. We're expanding to support other DEXs and chains based on community demand. Join our Discord to vote on which platforms we should add next." }
  ];

  let openIndex: number | null = null;

  function toggle(index: number) {
    openIndex = openIndex === index ? null : index;
  }
</script>

<section class="bg-[#f5f5f5] px-6 py-24">
  <div class="max-w-[1400px] mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12">
    <div class="lg:col-span-4">
      <h2 class="font-serif text-4xl text-gray-900 mb-6">
        Frequently asked questions
      </h2>
      <a href="/" class="text-sm text-gray-900 border-b border-gray-300 pb-0.5 hover:border-black transition-colors">See all support</a>
    </div>
    
    <div class="lg:col-span-8">
      <div class="border-t border-gray-200">
        {#each faqs as faq, i}
          <div class="border-b border-gray-200">
            <button 
              class="w-full py-6 flex justify-between items-center text-left hover:bg-gray-50 transition-colors"
              on:click={() => toggle(i)}
            >
              <span class="text-lg text-gray-800">{faq.question}</span>
              <span class="text-2xl font-light text-gray-400 ml-4">
                {openIndex === i ? '−' : '+'}
              </span>
            </button>
            {#if openIndex === i}
              <div transition:slide class="pb-6 text-gray-500 leading-relaxed">
                {faq.answer}
              </div>
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>
