<script lang="ts">
  type Message = {
    id: string;
    role: 'user' | 'assistant';
    content: string;
    timestamp: Date;
    analysis?: {
      riskScore: number;
      sentiment: 'bullish' | 'bearish' | 'neutral';
      confidence: number;
    };
  };

  let messages = $state<Message[]>([
    {
      id: '1',
      role: 'assistant',
      content: 'Welcome to Pump Oracle. I can analyze any Pump.fun token for risk assessment, holder patterns, and market trends. Just paste a token address or name to get started.',
      timestamp: new Date(),
    }
  ]);

  let inputValue = $state('');
  let isAnalyzing = $state(false);
  let chatContainer: HTMLDivElement;

  const exampleQueries = [
    'Analyze token: 7xKXtg2CW87d97TXJSDpbD5jBkheTqA83TZRuJosgAsU',
    'What are the red flags for new tokens?',
    'Show me trending Pump.fun tokens',
  ];

  function scrollToBottom() {
    if (chatContainer) {
      setTimeout(() => {
        chatContainer.scrollTop = chatContainer.scrollHeight;
      }, 100);
    }
  }

  async function handleSend() {
    if (!inputValue.trim() || isAnalyzing) return;

    const userMessage: Message = {
      id: Date.now().toString(),
      role: 'user',
      content: inputValue,
      timestamp: new Date(),
    };

    messages = [...messages, userMessage];
    inputValue = '';
    isAnalyzing = true;
    scrollToBottom();

    // Simulate AI analysis
    setTimeout(() => {
      const aiMessage: Message = {
        id: (Date.now() + 1).toString(),
        role: 'assistant',
        content: `I've analyzed your query. Here's what I found:\n\nBased on current market data and holder patterns, this token shows moderate risk indicators. The liquidity pool has been active for 3 days with consistent volume. However, the top 10 holders control 45% of supply, which presents concentration risk.\n\nKey metrics:\n• Holder count: 1,247\n• 24h volume: $127K\n• Liquidity: $89K\n• Contract verified: Yes`,
        timestamp: new Date(),
        analysis: {
          riskScore: 6.5,
          sentiment: 'neutral',
          confidence: 82,
        }
      };
      messages = [...messages, aiMessage];
      isAnalyzing = false;
      scrollToBottom();
    }, 1500);
  }

  function handleExampleClick(query: string) {
    inputValue = query;
    handleSend();
  }

  function handleKeydown(e: KeyboardEvent) {
    if (e.key === 'Enter' && !e.shiftKey) {
      e.preventDefault();
      handleSend();
    }
  }

  function getRiskColor(score: number) {
    if (score < 4) return 'text-primary-400';
    if (score < 7) return 'text-yellow-400';
    return 'text-red-400';
  }

  function getRiskLabel(score: number) {
    if (score < 4) return 'Low Risk';
    if (score < 7) return 'Moderate Risk';
    return 'High Risk';
  }
</script>

<section class="relative min-h-[calc(100vh-80px)] flex items-center justify-center px-6 py-12 animated-gradient-bg overflow-hidden">
  <!-- Futuristic animated background effects -->
  <div class="absolute inset-0 overflow-hidden pointer-events-none">
    <!-- Animated gradient orbs -->
    <div class="absolute top-0 left-1/4 w-96 h-96 rounded-full blur-[120px] opacity-30" style="background: var(--neon-blue); animation: float 8s ease-in-out infinite, pulse-glow 4s ease-in-out infinite;"></div>
    <div class="absolute bottom-0 right-1/4 w-96 h-96 rounded-full blur-[120px] opacity-30" style="background: var(--neon-purple); animation: float 10s ease-in-out infinite reverse, pulse-glow 5s ease-in-out infinite;"></div>
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] rounded-full blur-[150px] opacity-20" style="background: var(--neon-pink); animation: rotate-slow 20s linear infinite, pulse-glow 6s ease-in-out infinite;"></div>
    
    <!-- Grid pattern overlay -->
    <div class="absolute inset-0 opacity-10" style="background-image: linear-gradient(var(--neon-cyan) 1px, transparent 1px), linear-gradient(90deg, var(--neon-cyan) 1px, transparent 1px); background-size: 50px 50px;"></div>
  </div>

  <div class="relative w-full max-w-5xl">
    <!-- Header -->
    <div class="text-center mb-8">
      <div class="flex items-center justify-center gap-3 mb-4">
        <svg class="w-8 h-8 neon-glow" style="color: var(--neon-cyan); animation: float 3s ease-in-out infinite;" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
        </svg>
        <h1 class="text-5xl md:text-6xl font-black gradient-text tracking-tight">
          AI Token Analysis
        </h1>
      </div>
      <p class="text-xl font-medium" style="color: var(--dark-text-secondary);">
        Get instant risk scoring and market insights for any Pump.fun token
      </p>
    </div>

    <!-- Chat Container -->
    <div 
      class="rounded-3xl overflow-hidden glass-morph relative"
      style="border: 2px solid; border-image: linear-gradient(135deg, var(--neon-blue), var(--neon-purple), var(--neon-pink)) 1; box-shadow: 0 0 40px rgba(0, 150, 255, 0.3), inset 0 0 60px rgba(0, 150, 255, 0.05);"
    >
      <!-- Messages -->
      <div 
        bind:this={chatContainer}
        class="h-[500px] overflow-y-auto p-6 space-y-6 chat-scroll"
      >
        {#each messages as message (message.id)}
          <div class={[
            'flex gap-4',
            message.role === 'user' ? 'justify-end' : 'justify-start'
          ]}>
            {#if message.role === 'assistant'}
              <div class="flex-shrink-0 w-10 h-10 rounded-full flex items-center justify-center glass-morph neon-glow" style="background: linear-gradient(135deg, var(--neon-blue), var(--neon-purple)); animation: pulse-glow 3s ease-in-out infinite;">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
                </svg>
              </div>
            {/if}

            <div class={[
              'max-w-[80%] rounded-2xl px-5 py-4 transform transition-all duration-300 hover:scale-[1.02]',
              message.role === 'user' 
                ? 'text-white neon-glow' 
                : 'glass-morph'
            ]}
            style={message.role === 'user' ? 'background: linear-gradient(135deg, var(--neon-blue), var(--neon-purple)); box-shadow: 0 0 20px var(--neon-blue);' : 'color: var(--dark-text-primary); border: 1px solid rgba(255, 255, 255, 0.1);'}
            >
              <p class="text-sm leading-relaxed whitespace-pre-line">{message.content}</p>
              
              {#if message.analysis}
                <div class="mt-4 pt-4 border-t space-y-3" style="border-color: var(--dark-border);">
                  <div class="flex items-center justify-between">
                    <span class="text-xs" style="color: var(--dark-text-secondary);">Risk Score</span>
                    <span class={['text-sm font-bold', getRiskColor(message.analysis.riskScore)]}>
                      {message.analysis.riskScore}/10 - {getRiskLabel(message.analysis.riskScore)}
                    </span>
                  </div>
                  <div class="flex items-center justify-between">
                    <span class="text-xs" style="color: var(--dark-text-secondary);">Sentiment</span>
                    <span class="text-sm font-medium capitalize" style="color: var(--dark-text-primary);">
                      {message.analysis.sentiment}
                    </span>
                  </div>
                  <div class="flex items-center justify-between">
                    <span class="text-xs" style="color: var(--dark-text-secondary);">Confidence</span>
                    <span class="text-sm font-medium" style="color: var(--dark-text-primary);">
                      {message.analysis.confidence}%
                    </span>
                  </div>
                </div>
              {/if}
            </div>

            {#if message.role === 'user'}
              <div class="flex-shrink-0 w-10 h-10 rounded-full flex items-center justify-center glass-morph neon-glow-pink" style="background: linear-gradient(135deg, var(--neon-pink), var(--neon-purple)); border: 2px solid var(--neon-pink);">
                <span class="text-xs font-bold text-white">YOU</span>
              </div>
            {/if}
          </div>
        {/each}

        {#if isAnalyzing}
          <div class="flex gap-4 justify-start">
            <div class="flex-shrink-0 w-10 h-10 rounded-full flex items-center justify-center glass-morph neon-glow" style="background: linear-gradient(135deg, var(--neon-blue), var(--neon-purple)); animation: pulse-glow 1.5s ease-in-out infinite;">
              <svg class="w-5 h-5 text-white animate-pulse" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
              </svg>
            </div>
            <div class="rounded-2xl px-5 py-4 glass-morph" style="border: 1px solid rgba(255, 255, 255, 0.1);">
              <div class="flex gap-2">
                <div class="w-3 h-3 rounded-full animate-bounce neon-glow" style="background: var(--neon-cyan); animation-delay: 0ms;"></div>
                <div class="w-3 h-3 rounded-full animate-bounce neon-glow-purple" style="background: var(--neon-purple); animation-delay: 150ms;"></div>
                <div class="w-3 h-3 rounded-full animate-bounce neon-glow-pink" style="background: var(--neon-pink); animation-delay: 300ms;"></div>
              </div>
            </div>
          </div>
        {/if}
      </div>

      <!-- Example Queries (shown when no messages) -->
      {#if messages.length === 1}
        <div class="px-6 pb-6">
          <p class="text-xs mb-3 font-semibold" style="color: var(--neon-cyan);">⚡ Try these examples:</p>
          <div class="flex flex-wrap gap-3">
            {#each exampleQueries as query}
              <button
                onclick={() => handleExampleClick(query)}
                class="text-xs px-4 py-2.5 rounded-xl glass-morph transition-all duration-300 transform hover:scale-105 hover:neon-glow font-medium"
                style="border: 1px solid var(--dark-border); color: var(--dark-text-secondary);"
              >
                {query}
              </button>
            {/each}
          </div>
        </div>
      {/if}

      <!-- Input Area -->
      <div class="border-t p-5 glass-morph" style="border-color: var(--dark-border);">
        <div class="flex gap-3">
          <input
            type="text"
            bind:value={inputValue}
            onkeydown={handleKeydown}
            placeholder="Ask about a token or paste token address..."
            class="flex-1 px-5 py-4 rounded-xl glass-morph focus:outline-none transition-all text-sm font-medium"
            style="border: 2px solid var(--dark-border); color: var(--dark-text-primary); box-shadow: inset 0 0 20px rgba(0, 150, 255, 0.05);"
            disabled={isAnalyzing}
          />
          <button
            onclick={handleSend}
            disabled={!inputValue.trim() || isAnalyzing}
            class={[
              'px-7 py-4 rounded-xl font-bold transition-all flex items-center gap-2 transform hover:scale-105',
              inputValue.trim() && !isAnalyzing
                ? 'text-white neon-glow'
                : 'bg-gray-800 text-gray-500 cursor-not-allowed'
            ]}
            style={inputValue.trim() && !isAnalyzing ? 'background: linear-gradient(135deg, var(--neon-blue), var(--neon-purple)); box-shadow: 0 0 30px var(--neon-blue);' : ''}
          >
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8" />
            </svg>
            <span class="hidden sm:inline">Analyze</span>
          </button>
        </div>
      </div>
    </div>

    <!-- Stats Bar -->
    <div class="mt-8 grid grid-cols-3 gap-4">
      <div class="text-center p-6 rounded-2xl glass-morph transform transition-all duration-300 hover:scale-105 hover:neon-glow group" style="border: 1px solid var(--dark-border);">
        <div class="flex items-center justify-center gap-2 mb-2">
          <svg class="w-5 h-5 group-hover:animate-pulse" style="color: var(--neon-cyan);" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
          <span class="text-3xl font-black gradient-text">100K+</span>
        </div>
        <span class="text-xs font-semibold" style="color: var(--dark-text-tertiary);">Tokens Analyzed</span>
      </div>
      <div class="text-center p-6 rounded-2xl glass-morph transform transition-all duration-300 hover:scale-105 hover:neon-glow-purple group" style="border: 1px solid var(--dark-border);">
        <div class="flex items-center justify-center gap-2 mb-2">
          <svg class="w-5 h-5 group-hover:animate-pulse" style="color: var(--neon-purple);" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" />
          </svg>
          <span class="text-3xl font-black gradient-text">95%</span>
        </div>
        <span class="text-xs font-semibold" style="color: var(--dark-text-tertiary);">Scam Detection Rate</span>
      </div>
      <div class="text-center p-6 rounded-2xl glass-morph transform transition-all duration-300 hover:scale-105 hover:neon-glow-pink group" style="border: 1px solid var(--dark-border);">
        <div class="flex items-center justify-center gap-2 mb-2">
          <svg class="w-5 h-5 group-hover:animate-pulse" style="color: var(--neon-pink);" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" />
          </svg>
          <span class="text-3xl font-black gradient-text">&lt;2s</span>
        </div>
        <span class="text-xs font-semibold" style="color: var(--dark-text-tertiary);">Average Response Time</span>
      </div>
    </div>
  </div>
</section>
