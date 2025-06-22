<template>
  <div class="min-h-screen bg-slate-900 text-white overflow-hidden">
    <MolecularAnimation />
    
    <!-- Floating Navigation -->
    <nav class="fixed top-4 right-4 sm:top-8 sm:right-8 z-50 bg-slate-800/80 backdrop-blur-md rounded-full p-1 sm:p-2 border border-primary-500/30">
      <div class="flex space-x-1 sm:space-x-2">
        <button @click="scrollToSection('hero')" 
                :class="activeSection === 'hero' ? 'bg-primary-600 shadow-lg shadow-primary-500/50' : 'bg-slate-700 hover:bg-primary-500'"
                class="w-11 h-11 sm:w-10 sm:h-10 rounded-full transition-all duration-300 flex items-center justify-center relative group">
          <svg class="w-4 h-4 text-white" fill="currentColor" viewBox="0 0 24 24">
            <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
          </svg>
          <div v-if="activeSection === 'hero'" class="absolute -inset-1 bg-primary-500/30 rounded-full blur animate-pulse"></div>
        </button>
        <button @click="scrollToSection('about')" 
                :class="activeSection === 'about' ? 'bg-primary-600 shadow-lg shadow-primary-500/50' : 'bg-slate-700 hover:bg-primary-500'"
                class="w-11 h-11 sm:w-10 sm:h-10 rounded-full transition-all duration-300 flex items-center justify-center relative group">
          <svg class="w-4 h-4 text-white" fill="currentColor" viewBox="0 0 24 24">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
          </svg>
          <div v-if="activeSection === 'about'" class="absolute -inset-1 bg-primary-500/30 rounded-full blur animate-pulse"></div>
        </button>
        <button @click="scrollToSection('timeline')" 
                :class="activeSection === 'timeline' ? 'bg-primary-600 shadow-lg shadow-primary-500/50' : 'bg-slate-700 hover:bg-primary-500'"
                class="w-11 h-11 sm:w-10 sm:h-10 rounded-full transition-all duration-300 flex items-center justify-center relative group">
          <svg class="w-4 h-4 text-white" fill="currentColor" viewBox="0 0 24 24">
            <path d="M23 8c0 1.1-.9 2-2 2-.18 0-.35-.02-.51-.07l-3.56 3.55c.05.16.07.34.07.52 0 1.1-.9 2-2 2s-2-.9-2-2c0-.18.02-.36.07-.52l-2.55-2.55c-.16.05-.34.07-.52.07s-.36-.02-.52-.07l-4.55 4.56c.05.16.07.33.07.51 0 1.1-.9 2-2 2s-2-.9-2-2 .9-2 2-2c.18 0 .35.02.51.07l4.56-4.55C8.02 9.36 8 9.18 8 9c0-1.1.9-2 2-2s2 .9 2 2c0 .18-.02.36-.07.52l2.55 2.55c.16-.05.34-.07.52-.07s.36.02.52.07l3.56-3.56C19.02 8.35 19 8.18 19 8c0-1.1.9-2 2-2s2 .9 2 2z"/>
          </svg>
          <div v-if="activeSection === 'timeline'" class="absolute -inset-1 bg-primary-500/30 rounded-full blur animate-pulse"></div>
        </button>
        <button @click="scrollToSection('skills')" 
                :class="activeSection === 'skills' ? 'bg-primary-600 shadow-lg shadow-primary-500/50' : 'bg-slate-700 hover:bg-primary-500'"
                class="w-11 h-11 sm:w-10 sm:h-10 rounded-full transition-all duration-300 flex items-center justify-center relative group">
          <svg class="w-4 h-4 text-white" fill="currentColor" viewBox="0 0 24 24">
            <path d="M22.7 19l-9.1-9.1c.9-2.3.4-5-1.5-6.9-2-2-5-2.4-7.4-1.3L9 6 6 9 1.6 4.7C.4 7.1.9 10.1 2.9 12.1c1.9 1.9 4.6 2.4 6.9 1.5l9.1 9.1c.4.4 1 .4 1.4 0l2.3-2.3c.5-.4.5-1.1.1-1.4z"/>
          </svg>
          <div v-if="activeSection === 'skills'" class="absolute -inset-1 bg-primary-500/30 rounded-full blur animate-pulse"></div>
        </button>
        <button @click="scrollToSection('publications')" 
                :class="activeSection === 'publications' ? 'bg-primary-600 shadow-lg shadow-primary-500/50' : 'bg-slate-700 hover:bg-primary-500'"
                class="w-11 h-11 sm:w-10 sm:h-10 rounded-full transition-all duration-300 flex items-center justify-center relative group">
          <svg class="w-4 h-4 text-white" fill="currentColor" viewBox="0 0 24 24">
            <path d="M6 2c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 2 2h8l6-6V8l-6-6H6zm7 7V3.5L18.5 9H13z"/>
          </svg>
          <div v-if="activeSection === 'publications'" class="absolute -inset-1 bg-primary-500/30 rounded-full blur animate-pulse"></div>
        </button>
        <button @click="scrollToSection('contact')" 
                :class="activeSection === 'contact' ? 'bg-primary-600 shadow-lg shadow-primary-500/50' : 'bg-slate-700 hover:bg-primary-500'"
                class="w-11 h-11 sm:w-10 sm:h-10 rounded-full transition-all duration-300 flex items-center justify-center relative group">
          <svg class="w-4 h-4 text-white" fill="currentColor" viewBox="0 0 24 24">
            <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
          </svg>
          <div v-if="activeSection === 'contact'" class="absolute -inset-1 bg-primary-500/30 rounded-full blur animate-pulse"></div>
        </button>
      </div>
    </nav>

    <!-- Hero Section with Innovative Design -->
    <section id="hero" class="relative min-h-screen flex items-center justify-center pt-20 pb-16 px-2 sm:px-4">
      <!-- Animated Background Elements -->
      <div class="absolute inset-0 overflow-hidden">
        <div class="absolute top-20 left-20 w-64 h-64 bg-primary-500/10 rounded-full blur-3xl animate-pulse"></div>
        <div class="absolute bottom-20 right-20 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl animate-pulse delay-1000"></div>
        <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] bg-gradient-to-r from-primary-600/5 to-emerald-600/5 rounded-full blur-3xl"></div>
      </div>

      <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <!-- Interactive Profile Circle -->
        <div class="relative mx-auto mb-6 sm:mb-8 md:mb-12 group">
          <div class="w-28 h-28 sm:w-36 sm:h-36 md:w-48 md:h-48 mx-auto relative">
            <!-- Rotating Ring -->
            <div class="absolute inset-0 rounded-full border-2 sm:border-4 border-primary-500/30 animate-spin-slow"></div>
            <div class="absolute inset-1 sm:inset-2 rounded-full border border-emerald-400/40 animate-spin-reverse"></div>
            
            <!-- Profile Avatar -->
            <div class="absolute inset-2 sm:inset-4 rounded-full bg-gradient-to-br from-primary-600 to-emerald-600 flex items-center justify-center text-3xl sm:text-4xl md:text-6xl font-bold group-hover:scale-110 transition-transform duration-500">
              AV
            </div>
            
            <!-- Floating Elements - Mobile Safe Positioning -->
            <div class="absolute top-0 right-0 w-6 h-6 sm:w-8 sm:h-8 bg-primary-500 rounded-full animate-bounce delay-500"></div>
            <div class="absolute bottom-0 left-0 w-4 h-4 sm:w-6 sm:h-6 bg-emerald-500 rounded-full animate-bounce delay-1000"></div>
            <div class="absolute top-1/2 left-0 transform -translate-x-1/2 w-3 h-3 sm:w-4 sm:h-4 bg-yellow-500 rounded-full animate-bounce delay-700"></div>
          </div>
        </div>

        <!-- Name with Typewriter Effect -->
        <h1 class="text-3xl sm:text-4xl md:text-6xl lg:text-8xl font-black mb-3 sm:mb-4 md:mb-6 relative leading-tight">
          <span class="bg-gradient-to-r from-white via-primary-300 to-emerald-300 bg-clip-text text-transparent">
            {{ displayedName }}
          </span>
          <span v-if="isTyping" class="animate-pulse">|</span>
        </h1>

        <!-- Dynamic Title -->
        <div class="mb-4 sm:mb-6 md:mb-8">
          <p class="text-base sm:text-lg md:text-2xl lg:text-3xl text-primary-300 font-light mb-2 text-center">
            Ph.D. in Materials Chemistry
          </p>
          <div class="flex flex-col sm:flex-row items-center justify-center space-y-2 sm:space-y-0 sm:space-x-4 text-slate-300 text-sm sm:text-base">
            <span class="flex items-center">
              <span class="w-2 h-2 bg-green-500 rounded-full mr-2 animate-pulse"></span>
              Available for Industry Roles
            </span>
            <span class="hidden sm:block">•</span>
            <span class="flex items-center">
              <span class="w-2 h-2 bg-primary-500 rounded-full mr-2"></span>
              4.0 GPA
            </span>
          </div>
          
          <!-- Professional Links -->
          <div class="flex items-center justify-center space-x-4 sm:space-x-6 mt-3 sm:mt-4">
            <a :href="profileData.linkedin" target="_blank" 
               class="flex items-center gap-2 text-slate-400 hover:text-primary-300 transition-colors duration-300 group">
              <svg class="w-5 h-5 group-hover:scale-110 transition-transform" fill="currentColor" viewBox="0 0 24 24">
                <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
              </svg>
              <span class="hidden sm:inline">LinkedIn</span>
            </a>
            
            <a :href="profileData.googleScholar" target="_blank" 
               class="flex items-center gap-2 text-slate-400 hover:text-emerald-300 transition-colors duration-300 group">
              <svg class="w-5 h-5 group-hover:scale-110 transition-transform" fill="currentColor" viewBox="0 0 24 24">
                <path d="M5.242 13.769L0 9.5 12 0l12 9.5-5.242 4.269C17.548 11.249 14.978 9.5 12 9.5c-2.977 0-5.548 1.748-6.758 4.269zM12 10a7 7 0 1 0 0 14 7 7 0 0 0 0-14z"/>
              </svg>
              <span class="hidden sm:inline">Google Scholar</span>
            </a>
          </div>
        </div>

        <!-- Key Metrics Cards -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-2 sm:gap-3 md:gap-4 mb-6 sm:mb-8 md:mb-12 max-w-4xl mx-auto px-2 sm:px-0">
          <div class="bg-slate-800/50 backdrop-blur-sm border border-primary-500/30 rounded-xl sm:rounded-2xl p-4 sm:p-6 hover:border-primary-400/50 transition-all duration-300 group">
            <div class="text-2xl sm:text-3xl font-bold text-primary-400 mb-1 sm:mb-2 group-hover:scale-110 transition-transform">9+</div>
            <div class="text-xs sm:text-sm text-slate-300">R&D Projects</div>
          </div>
          <div class="bg-slate-800/50 backdrop-blur-sm border border-emerald-500/30 rounded-xl sm:rounded-2xl p-4 sm:p-6 hover:border-emerald-400/50 transition-all duration-300 group">
            <div class="text-2xl sm:text-3xl font-bold text-emerald-400 mb-1 sm:mb-2 group-hover:scale-110 transition-transform">4</div>
            <div class="text-xs sm:text-sm text-slate-300">Publications</div>
          </div>
          <div class="bg-slate-800/50 backdrop-blur-sm border border-yellow-500/30 rounded-xl sm:rounded-2xl p-4 sm:p-6 hover:border-yellow-400/50 transition-all duration-300 group">
            <div class="text-2xl sm:text-3xl font-bold text-yellow-400 mb-1 sm:mb-2 group-hover:scale-110 transition-transform">7</div>
            <div class="text-xs sm:text-sm text-slate-300">Students Mentored</div>
          </div>
          <div class="bg-slate-800/50 backdrop-blur-sm border border-purple-500/30 rounded-xl sm:rounded-2xl p-4 sm:p-6 hover:border-purple-400/50 transition-all duration-300 group">
            <div class="text-2xl sm:text-3xl font-bold text-purple-400 mb-1 sm:mb-2 group-hover:scale-110 transition-transform">4+</div>
            <div class="text-xs sm:text-sm text-slate-300">Years Experience</div>
          </div>
        </div>

        <!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row gap-3 sm:gap-4 justify-center mb-12 sm:mb-20">
          <button @click="scrollToSection('contact')" class="group relative px-6 sm:px-8 py-3 sm:py-4 bg-gradient-to-r from-primary-600 to-emerald-600 rounded-xl sm:rounded-2xl font-semibold text-base sm:text-lg overflow-hidden transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-primary-500/25">
            <span class="relative z-10">Let's Connect</span>
            <div class="absolute inset-0 bg-gradient-to-r from-primary-500 to-emerald-500 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
          </button>
          <button @click="downloadResume" class="px-6 sm:px-8 py-3 sm:py-4 border-2 border-primary-500 rounded-xl sm:rounded-2xl font-semibold text-base sm:text-lg hover:bg-primary-500/10 transition-all duration-300 hover:scale-105">
            Download Resume
          </button>
        </div>
      </div>

      <!-- Enhanced Scroll Indicator - Mobile Optimized -->
      <div class="absolute bottom-4 sm:bottom-8 left-1/2 transform -translate-x-1/2 flex flex-col items-center animate-bounce cursor-pointer hover:scale-110 transition-transform duration-300 z-20" 
           @click="scrollToSection('about')">
        <div class="text-slate-400 text-xs mb-1 sm:mb-2 opacity-70 hidden sm:block">Scroll to explore</div>
        <div class="relative group">
          <!-- Outer glow ring -->
          <div class="absolute inset-0 w-6 h-6 sm:w-8 sm:h-8 bg-primary-500/20 rounded-full blur-md group-hover:bg-primary-500/30 transition-colors duration-300"></div>
          <!-- Main scroll indicator -->
          <div class="relative w-5 h-8 sm:w-6 sm:h-10 border-2 border-primary-400/60 rounded-full flex justify-center group-hover:border-primary-400 transition-colors duration-300">
            <div class="w-0.5 sm:w-1 h-2 sm:h-3 bg-gradient-to-b from-primary-400 to-transparent rounded-full mt-1 sm:mt-2 animate-pulse"></div>
          </div>
        </div>
        <!-- Chevron arrow -->
        <div class="flex flex-col items-center mt-0.5 sm:mt-1 opacity-60 group-hover:opacity-100 transition-opacity duration-300">
          <svg class="w-2.5 h-2.5 sm:w-3 sm:h-3 text-primary-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
          </svg>
        </div>
      </div>
    </section>

    <!-- About Section with Industry Focus -->
    <section id="about" class="py-16 sm:py-24 md:py-32 relative overflow-hidden">
      <!-- Background Pattern -->
      <div class="absolute inset-0 opacity-5">
        <div class="absolute inset-0" style="background-image: radial-gradient(circle at 2px 2px, rgba(20, 184, 166, 0.3) 1px, transparent 0); background-size: 40px 40px;"></div>
      </div>
      
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <div class="text-center mb-12 sm:mb-16 md:mb-20">
          <div class="inline-flex items-center bg-primary-600/10 border border-primary-500/30 rounded-full px-4 sm:px-6 py-2 sm:py-3 mb-4 sm:mb-6">
            <span class="w-2 h-2 bg-primary-500 rounded-full mr-2 sm:mr-3 animate-pulse"></span>
            <span class="text-primary-300 font-medium text-sm sm:text-base">Ready for Industry Impact</span>
          </div>
          <h2 class="text-3xl sm:text-4xl md:text-6xl lg:text-7xl font-black mb-4 sm:mb-6 bg-gradient-to-r from-white via-primary-300 to-emerald-300 bg-clip-text text-transparent leading-tight">
            <span class="block sm:inline">Transforming Research</span><br class="hidden sm:block"/><span class="block sm:inline">Into Innovation</span>
          </h2>
          <p class="text-base sm:text-lg md:text-xl text-slate-400 max-w-3xl mx-auto px-4">
            Bridging the gap between cutting-edge materials science and real-world industrial applications
          </p>
        </div>

        <div class="grid lg:grid-cols-12 gap-6 sm:gap-8 md:gap-12 items-start">
          <!-- Main Content -->
          <div class="lg:col-span-7 space-y-6 sm:space-y-8">
            <!-- Professional Summary -->
            <div class="relative group">
              <div class="absolute -inset-1 bg-gradient-to-r from-primary-600 to-emerald-600 rounded-3xl blur opacity-25 group-hover:opacity-40 transition duration-1000"></div>
              <div class="relative bg-slate-800/50 backdrop-blur-xl rounded-2xl sm:rounded-3xl p-4 sm:p-6 md:p-8 border border-slate-700/50">
                <div class="flex flex-col sm:flex-row sm:items-center gap-3 sm:gap-4 mb-4 sm:mb-6">
                  <div class="w-10 h-10 sm:w-12 sm:h-12 bg-gradient-to-r from-primary-500 to-emerald-500 rounded-lg sm:rounded-xl flex items-center justify-center">
                    <svg class="w-5 h-5 sm:w-6 sm:h-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M9 11H7v3h2v-3zm4 0h-2v3h2v-3zm4 0h-2v3h2v-3zm2-7h-2V2a1 1 0 0 0-1-1H8a1 1 0 0 0-1 1v2H5a1 1 0 0 0-1 1v16a1 1 0 0 0 1 1h14a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1zM9 2h6v2H9V2zm10 18H5V6h14v14z"/>
                    </svg>
                  </div>
                  <div>
                    <h3 class="text-lg sm:text-xl md:text-2xl font-bold text-white">Ph.D. Candidate & Research Leader</h3>
                    <p class="text-primary-300 text-sm sm:text-base">Materials Chemistry Innovation Expert</p>
                  </div>
                </div>
                <p class="text-sm sm:text-base md:text-lg leading-relaxed text-slate-200 mb-4 sm:mb-6">
                  A results-driven materials chemistry researcher with demonstrated expertise in translating fundamental science into industry-ready solutions. My 4+ years of experience spanning 9+ R&D projects have equipped me with deep technical knowledge and practical problem-solving skills essential for driving innovation in industrial settings.
                </p>
                <div class="grid sm:grid-cols-2 gap-4">
                  <div class="flex items-center gap-3">
                    <div class="w-8 h-8 bg-primary-600/20 rounded-lg flex items-center justify-center">
                      <svg class="w-4 h-4 text-primary-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                      </svg>
                    </div>
                    <span class="text-slate-300">4.0 GPA Excellence</span>
                  </div>
                  <div class="flex items-center gap-3">
                    <div class="w-8 h-8 bg-emerald-600/20 rounded-lg flex items-center justify-center">
                      <svg class="w-4 h-4 text-emerald-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
                      </svg>
                    </div>
                    <span class="text-slate-300">Award-Winning Research</span>
                  </div>
                </div>
              </div>
            </div>

            <!-- Core Competencies -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 sm:gap-6">
              <div class="group">
                <div class="bg-gradient-to-br from-blue-600/10 to-blue-800/10 rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-blue-500/30 hover:border-blue-400/50 transition-all duration-300 hover:scale-105">
                  <div class="flex items-center gap-2 sm:gap-3 mb-3 sm:mb-4">
                    <div class="w-8 h-8 sm:w-10 sm:h-10 bg-blue-600/20 rounded-lg sm:rounded-xl flex items-center justify-center">
                      <svg class="w-4 h-4 sm:w-5 sm:h-5 text-blue-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M9 11H7v3h2v-3zm4 0h-2v3h2v-3zm4 0h-2v3h2v-3zm2-7h-2V2a1 1 0 0 0-1-1H8a1 1 0 0 0-1 1v2H5a1 1 0 0 0-1 1v16a1 1 0 0 0 1 1h14a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1zM9 2h6v2H9V2zm10 18H5V6h14v14z"/>
                      </svg>
                    </div>
                    <h3 class="text-base sm:text-lg font-semibold text-blue-300">Research Excellence</h3>
                  </div>
                  <p class="text-slate-300 text-xs sm:text-sm mb-3 sm:mb-4">Advanced materials characterization, synthesis optimization, and structure-property relationships</p>
                  <div class="text-xs text-blue-400 font-medium">Published in Top-Tier Journals</div>
                </div>
              </div>
              
              <div class="group">
                <div class="bg-gradient-to-br from-green-600/10 to-green-800/10 rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-green-500/30 hover:border-green-400/50 transition-all duration-300 hover:scale-105">
                  <div class="flex items-center gap-2 sm:gap-3 mb-3 sm:mb-4">
                    <div class="w-8 h-8 sm:w-10 sm:h-10 bg-green-600/20 rounded-lg sm:rounded-xl flex items-center justify-center">
                      <svg class="w-4 h-4 sm:w-5 sm:h-5 text-green-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M7 2v11h3v9l7-12h-4l4-8z"/>
                      </svg>
                    </div>
                    <h3 class="text-base sm:text-lg font-semibold text-green-300">Industry Impact</h3>
                  </div>
                  <p class="text-slate-300 text-xs sm:text-sm mb-3 sm:mb-4">Process optimization, DOE implementation, and sustainable materials development for commercial applications</p>
                  <div class="text-xs text-green-400 font-medium">Real-World Solutions</div>
                </div>
              </div>

              <div class="group">
                <div class="bg-gradient-to-br from-purple-600/10 to-purple-800/10 rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-purple-500/30 hover:border-purple-400/50 transition-all duration-300 hover:scale-105">
                  <div class="flex items-center gap-2 sm:gap-3 mb-3 sm:mb-4">
                    <div class="w-8 h-8 sm:w-10 sm:h-10 bg-purple-600/20 rounded-lg sm:rounded-xl flex items-center justify-center">
                      <svg class="w-4 h-4 sm:w-5 sm:h-5 text-purple-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M16 4c0-1.11.89-2 2-2s2 .89 2 2-.89 2-2 2-2-.89-2-2zm4 18v-6h2.5l-2.54-7.63A1.997 1.997 0 0 0 18.05 7H16c-.8 0-1.54.37-2.01.99L12 10.5v3.5c0 .55-.45 1-1 1s-1-.45-1-1v-4l-1.8-2.4A1.993 1.993 0 0 0 6.6 7H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h2v-6.5c0-.28.22-.5.5-.5s.5.22.5.5V22h12z"/>
                      </svg>
                    </div>
                    <h3 class="text-base sm:text-lg font-semibold text-purple-300">Leadership & Mentoring</h3>
                  </div>
                  <p class="text-slate-300 text-xs sm:text-sm mb-3 sm:mb-4">Led cross-functional teams, mentored 7 students, and managed laboratory safety protocols</p>
                  <div class="text-xs text-purple-400 font-medium">Team-Ready Leader</div>
                </div>
              </div>

              <div class="group">
                <div class="bg-gradient-to-br from-orange-600/10 to-orange-800/10 rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-orange-500/30 hover:border-orange-400/50 transition-all duration-300 hover:scale-105">
                  <div class="flex items-center gap-2 sm:gap-3 mb-3 sm:mb-4">
                    <div class="w-8 h-8 sm:w-10 sm:h-10 bg-orange-600/20 rounded-lg sm:rounded-xl flex items-center justify-center">
                      <svg class="w-4 h-4 sm:w-5 sm:h-5 text-orange-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
                      </svg>
                    </div>
                    <h3 class="text-base sm:text-lg font-semibold text-orange-300">Data-Driven Insights</h3>
                  </div>
                  <p class="text-slate-300 text-xs sm:text-sm mb-3 sm:mb-4">Advanced statistical analysis, experimental design, and computational modeling expertise</p>
                  <div class="text-xs text-orange-400 font-medium">Evidence-Based Decision Making</div>
                </div>
              </div>
            </div>
          </div>

          <!-- Research Focus Areas - Compact Grid -->
          <div class="lg:col-span-5 mt-6 lg:mt-0">
            <div class="lg:sticky lg:top-8">
              <div class="bg-slate-800/30 backdrop-blur-xl rounded-2xl sm:rounded-3xl p-4 sm:p-6 md:p-8 border border-slate-700/50">
                <h3 class="text-lg sm:text-xl md:text-2xl font-bold text-white mb-4 sm:mb-6 flex items-center gap-2 sm:gap-3">
                  <div class="w-8 h-8 bg-gradient-to-r from-primary-500 to-emerald-500 rounded-lg flex items-center justify-center">
                    <svg class="w-4 h-4 text-white" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                    </svg>
                  </div>
                  Core Expertise
                </h3>
                
                <!-- Compact Grid Layout -->
                <div class="grid grid-cols-2 gap-3 mb-6">
                  <div class="bg-slate-700/30 rounded-lg p-3 border border-slate-600/30 hover:border-primary-500/40 transition-all duration-300 group">
                    <div class="flex items-center gap-2">
                      <svg class="w-4 h-4 text-primary-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M9 11H7v3h2v-3zm4 0h-2v3h2v-3zm4 0h-2v3h2v-3zm2-7h-2V2a1 1 0 0 0-1-1H8a1 1 0 0 0-1 1v2H5a1 1 0 0 0-1 1v16a1 1 0 0 0 1 1h14a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1zM9 2h6v2H9V2zm10 18H5V6h14v14z"/>
                      </svg>
                      <span class="text-sm font-medium text-white group-hover:text-primary-300 transition-colors">Materials Chemistry</span>
                    </div>
                    <div class="text-xs text-primary-400 mt-1">PhD Research</div>
                  </div>
                  
                  <div class="bg-slate-700/30 rounded-lg p-3 border border-slate-600/30 hover:border-emerald-500/40 transition-all duration-300 group">
                    <div class="flex items-center gap-2">
                      <svg class="w-4 h-4 text-emerald-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M6 2l1.5 4 4-1.5L10 7l2 2-2.5 1.5L11 12l-4 1.5L8.5 17 6 16l-1.5-4 1.5-1.5L4 8l2-2L4.5 4.5 6 2z"/>
                      </svg>
                      <span class="text-sm font-medium text-white group-hover:text-emerald-300 transition-colors">Semiconductors</span>
                    </div>
                    <div class="text-xs text-emerald-400 mt-1">Advanced</div>
                  </div>
                  
                  <div class="bg-slate-700/30 rounded-lg p-3 border border-slate-600/30 hover:border-blue-500/40 transition-all duration-300 group">
                    <div class="flex items-center gap-2">
                      <svg class="w-4 h-4 text-blue-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                      </svg>
                      <span class="text-sm font-medium text-white group-hover:text-blue-300 transition-colors">Characterization</span>
                    </div>
                    <div class="text-xs text-blue-400 mt-1">Expert</div>
                  </div>
                  
                  <div class="bg-slate-700/30 rounded-lg p-3 border border-slate-600/30 hover:border-orange-500/40 transition-all duration-300 group">
                    <div class="flex items-center gap-2">
                      <svg class="w-4 h-4 text-orange-400" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
                      </svg>
                      <span class="text-sm font-medium text-white group-hover:text-orange-300 transition-colors">Data Science</span>
                    </div>
                    <div class="text-xs text-orange-400 mt-1">Proficient</div>
                  </div>
                </div>

                <!-- Key Highlights -->
                <div class="space-y-3 mb-6">
                  <div class="flex items-center gap-3 text-sm">
                    <div class="w-2 h-2 bg-primary-500 rounded-full"></div>
                    <span class="text-slate-300">4+ years materials research</span>
                  </div>
                  <div class="flex items-center gap-3 text-sm">
                    <div class="w-2 h-2 bg-emerald-500 rounded-full"></div>
                    <span class="text-slate-300">9+ R&D projects led</span>
                  </div>
                  <div class="flex items-center gap-3 text-sm">
                    <div class="w-2 h-2 bg-blue-500 rounded-full"></div>
                    <span class="text-slate-300">Advanced instrumentation expert</span>
                  </div>
                </div>

                <!-- Industry Readiness Indicator -->
                <div class="p-4 bg-gradient-to-r from-primary-600/10 to-emerald-600/10 rounded-xl border border-primary-500/30">
                  <div class="flex items-center gap-3">
                    <div class="w-3 h-3 bg-green-500 rounded-full animate-pulse"></div>
                    <span class="text-primary-300 font-medium">Ready for Immediate Impact</span>
                  </div>
                  <p class="text-slate-400 text-sm mt-2">PhD completion: January 2025</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Interactive Career Timeline -->
    <section id="timeline" class="py-16 sm:py-24 md:py-32 bg-slate-800/20">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12 sm:mb-16">
          <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold mb-4 sm:mb-6 bg-gradient-to-r from-primary-400 to-emerald-400 bg-clip-text text-transparent">
            Career Journey
          </h2>
          <div class="w-16 sm:w-24 h-1 bg-gradient-to-r from-primary-500 to-emerald-500 mx-auto rounded-full"></div>
        </div>

        <div class="relative">
          <!-- Timeline Line - Hidden on Mobile -->
          <div class="hidden md:block absolute left-1/2 transform -translate-x-1/2 w-1 h-full bg-gradient-to-b from-primary-500 to-emerald-500 rounded-full"></div>

          <div class="space-y-8 sm:space-y-12 md:space-y-16">
            <div v-for="(exp, index) in profileData.experience" :key="exp.title" 
                 :class="index % 2 === 0 ? 'lg:flex-row' : 'lg:flex-row-reverse'"
                 class="flex flex-col lg:flex lg:items-center gap-6 sm:gap-8">
              
              <!-- Timeline Node - Hidden on Mobile -->
              <div class="hidden md:block absolute left-1/2 transform -translate-x-1/2 w-6 h-6 bg-gradient-to-r from-primary-500 to-emerald-500 rounded-full border-4 border-slate-900 z-10"></div>
              
              <!-- Content Card -->
              <div :class="index % 2 === 0 ? 'lg:mr-auto lg:pr-16' : 'lg:ml-auto lg:pl-16'"
                   class="w-full lg:w-1/2 group">
                <div class="bg-slate-800/50 backdrop-blur-sm rounded-2xl sm:rounded-3xl p-4 sm:p-6 md:p-8 border border-slate-700/50 hover:border-primary-500/50 transition-all duration-300 hover:scale-105">
                  <div class="flex flex-col sm:flex-row sm:justify-between sm:items-start gap-3 sm:gap-4 mb-4">
                    <div class="flex-1">
                      <h3 class="text-lg sm:text-xl md:text-2xl font-bold text-primary-300 mb-1 sm:mb-2">{{ exp.title }}</h3>
                      <p class="text-base sm:text-lg text-slate-300">{{ exp.company }}</p>
                      <p class="text-sm sm:text-base text-slate-400">{{ exp.location }}</p>
                    </div>
                    <span class="bg-primary-600/20 text-primary-300 px-2 sm:px-3 py-1 rounded-full text-xs sm:text-sm whitespace-nowrap self-start">
                      {{ exp.duration }}
                    </span>
                  </div>
                  
                  <ul class="space-y-2">
                    <li v-for="highlight in exp.highlights.slice(0, 3)" :key="highlight"
                        class="text-slate-300 flex items-start text-sm sm:text-base">
                      <span class="text-emerald-400 mr-2 sm:mr-3 mt-1 text-xs">●</span>
                      {{ highlight }}
                    </li>
                  </ul>
                  
                  <button v-if="exp.highlights.length > 3" 
                          @click="toggleExpanded(index)"
                          class="mt-3 sm:mt-4 text-primary-400 hover:text-primary-300 text-sm font-medium px-3 py-1 rounded-lg hover:bg-primary-500/10 transition-colors">
                    {{ expandedItems.includes(index) ? 'Show Less' : `+${exp.highlights.length - 3} more achievements` }}
                  </button>
                  
                  <div v-if="expandedItems.includes(index)" class="mt-3 sm:mt-4 space-y-2">
                    <li v-for="highlight in exp.highlights.slice(3)" :key="highlight"
                        class="text-slate-300 flex items-start text-sm sm:text-base">
                      <span class="text-emerald-400 mr-2 sm:mr-3 mt-1 text-xs">●</span>
                      {{ highlight }}
                    </li>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Visualization -->
    <section id="skills" class="py-16 sm:py-24 md:py-32 relative overflow-hidden">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <div class="text-center mb-12 sm:mb-16">
          <div class="inline-flex items-center bg-emerald-600/10 border border-emerald-500/30 rounded-full px-4 sm:px-6 py-2 sm:py-3 mb-4 sm:mb-6">
            <span class="w-2 h-2 bg-emerald-500 rounded-full mr-2 sm:mr-3 animate-pulse"></span>
            <span class="text-emerald-300 font-medium text-sm sm:text-base">Technical Capabilities</span>
          </div>
          <h2 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-black mb-4 sm:mb-6 bg-gradient-to-r from-white via-emerald-300 to-primary-300 bg-clip-text text-transparent">
            Technical Arsenal
          </h2>
          <p class="text-base sm:text-lg text-slate-400 max-w-2xl mx-auto px-4">
            Core expertise across experimental techniques, computational tools, and analytical methods
          </p>
        </div>

        <!-- Compact Skills Grid -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6">
          <div v-for="(skills, category) in profileData.skills" :key="category"
               class="bg-slate-800/40 backdrop-blur-sm rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-slate-700/50 hover:border-primary-500/30 transition-all duration-300 group">
            <!-- Category Header -->
            <div class="flex items-center gap-2 sm:gap-3 mb-4 sm:mb-6">
              <div class="w-8 h-8 sm:w-10 sm:h-10 bg-gradient-to-r from-primary-500 to-emerald-500 rounded-lg flex items-center justify-center">
                <component :is="'svg'" class="w-4 h-4 sm:w-5 sm:h-5 text-white" fill="currentColor" viewBox="0 0 24 24">
                  <path :d="getCategoryIconPath(category)"/>
                </component>
              </div>
              <div>
                <h3 class="text-base sm:text-lg font-bold text-white">{{ formatCategoryName(category) }}</h3>
                <p class="text-xs text-slate-400">{{ getSkillCount(category) }} {{ category === 'professional' ? 'capabilities' : 'tools' }}</p>
              </div>
            </div>
            
            <!-- Condensed Skills List -->
            <div class="space-y-2 sm:space-y-3">
              <div v-for="skill in skills" :key="skill.name" class="group/item">
                <div class="flex items-center justify-between mb-1 sm:mb-2">
                  <h4 class="text-xs sm:text-sm font-medium text-slate-200 group-hover/item:text-primary-300 transition-colors">
                    {{ skill.name }}
                  </h4>
                  <div class="flex gap-1">
                    <div v-for="i in getSkillLevel(skill.name)" :key="i" 
                         class="w-1 h-1 sm:w-1.5 sm:h-1.5 bg-gradient-to-r from-primary-500 to-emerald-500 rounded-full"></div>
                  </div>
                </div>
                <div class="flex items-center gap-1 sm:gap-2">
                  <span class="text-xs text-slate-400 bg-slate-700/50 px-1.5 sm:px-2 py-0.5 sm:py-1 rounded">
                    {{ getSkillExperience(skill.name) }}
                  </span>
                  <span v-if="isCore(skill.name)" class="text-xs text-emerald-300 bg-emerald-600/20 px-1.5 sm:px-2 py-0.5 sm:py-1 rounded">
                    Core
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Key Highlights -->
        <div class="mt-12 sm:mt-16 grid grid-cols-1 sm:grid-cols-3 gap-4 sm:gap-6">
          <div class="bg-slate-800/40 backdrop-blur-sm rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-primary-500/30 text-center">
            <div class="w-10 h-10 sm:w-12 sm:h-12 bg-primary-600/20 rounded-lg flex items-center justify-center mx-auto mb-3 sm:mb-4">
              <svg class="w-5 h-5 sm:w-6 sm:h-6 text-primary-400" fill="currentColor" viewBox="0 0 24 24">
                <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
              </svg>
            </div>
            <h3 class="text-base sm:text-lg font-semibold text-white mb-1 sm:mb-2">Advanced Analytics</h3>
            <p class="text-xs sm:text-sm text-slate-400">DOE, statistical analysis, and data-driven optimization</p>
          </div>
          
          <div class="bg-slate-800/40 backdrop-blur-sm rounded-2xl p-6 border border-emerald-500/30 text-center">
            <div class="w-12 h-12 bg-emerald-600/20 rounded-lg flex items-center justify-center mx-auto mb-4">
              <svg class="w-6 h-6 text-emerald-400" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
              </svg>
            </div>
            <h3 class="text-lg font-semibold text-white mb-2">Research Excellence</h3>
            <p class="text-sm text-slate-400">4+ years of materials characterization expertise</p>
          </div>
          
          <div class="bg-slate-800/40 backdrop-blur-sm rounded-2xl p-6 border border-purple-500/30 text-center">
            <div class="w-12 h-12 bg-purple-600/20 rounded-lg flex items-center justify-center mx-auto mb-4">
              <svg class="w-6 h-6 text-purple-400" fill="currentColor" viewBox="0 0 24 24">
                <path d="M16 1H4c-1.1 0-2 .9-2 2v14h2V3h12V1zm3 4H8c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h11c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2zm-1 16H9V7h9v14z"/>
              </svg>
            </div>
            <h3 class="text-lg font-semibold text-white mb-2">Industry Ready</h3>
            <p class="text-sm text-slate-400">Practical experience in real-world applications</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Publications Showcase -->
    <section id="publications" class="py-16 sm:py-24 md:py-32 bg-slate-800/20">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12 sm:mb-16">
          <h2 class="text-3xl sm:text-4xl md:text-5xl font-bold mb-4 sm:mb-6 bg-gradient-to-r from-primary-400 to-emerald-400 bg-clip-text text-transparent">
            Research Impact
          </h2>
          <div class="w-16 sm:w-24 h-1 bg-gradient-to-r from-primary-500 to-emerald-500 mx-auto rounded-full"></div>
        </div>

        <!-- Publication Stats -->
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 sm:gap-6 mb-8 sm:mb-12">
          <div class="text-center bg-slate-800/50 backdrop-blur-sm rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-primary-500/30">
            <div class="text-3xl sm:text-4xl font-bold text-primary-400 mb-1 sm:mb-2">4</div>
            <div class="text-sm sm:text-base text-slate-300">Publications</div>
          </div>
          <div class="text-center bg-slate-800/50 backdrop-blur-sm rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-emerald-500/30">
            <div class="text-3xl sm:text-4xl font-bold text-emerald-400 mb-1 sm:mb-2">2</div>
            <div class="text-sm sm:text-base text-slate-300">First Author</div>
          </div>
          <div class="text-center bg-slate-800/50 backdrop-blur-sm rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-yellow-500/30">
            <div class="text-3xl sm:text-4xl font-bold text-yellow-400 mb-1 sm:mb-2">5+</div>
            <div class="text-sm sm:text-base text-slate-300">In Progress</div>
          </div>
        </div>

        <!-- Publications List -->
        <div class="space-y-6 sm:space-y-8">
          <div v-for="(pub, index) in profileData.publications" :key="pub.title"
               class="bg-slate-800/50 backdrop-blur-sm rounded-2xl sm:rounded-3xl p-4 sm:p-6 md:p-8 border border-slate-700/50 hover:border-primary-500/50 transition-all duration-300 group">
            <div class="flex flex-col lg:flex-row lg:justify-between lg:items-start gap-4 sm:gap-6">
              <div class="flex-1">
                <div class="flex flex-wrap items-center gap-2 sm:gap-3 mb-3 sm:mb-4">
                  <span class="bg-primary-600 text-white w-6 h-6 sm:w-8 sm:h-8 rounded-full flex items-center justify-center text-xs sm:text-sm font-bold">
                    {{ index + 1 }}
                  </span>
                  <span :class="pub.status === 'Published' ? 'bg-green-600/20 text-green-300' : 'bg-yellow-600/20 text-yellow-300'"
                        class="px-2 sm:px-3 py-1 rounded-full text-xs font-medium">
                    {{ pub.status }}
                  </span>
                  <span v-if="pub.authors.includes('Verma, A.;') && pub.authors.indexOf('Verma, A.;') < 20" 
                        class="bg-primary-600/20 text-primary-300 px-2 sm:px-3 py-1 rounded-full text-xs font-medium">
                    First Author
                  </span>
                </div>
                
                <h3 class="text-lg sm:text-xl font-bold text-white mb-2 sm:mb-3 group-hover:text-primary-300 transition-colors leading-tight">
                  {{ pub.title }}
                </h3>
                
                <p class="text-sm sm:text-base text-slate-300 mb-2 sm:mb-3">{{ pub.authors }}</p>
                
                <div class="flex flex-wrap items-center gap-2 sm:gap-4 text-xs sm:text-sm text-slate-400">
                  <span class="font-medium text-primary-400">{{ pub.journal }}</span>
                  <span v-if="pub.volume">{{ pub.volume }}</span>
                  <span v-if="pub.pages">{{ pub.pages }}</span>
                  <span class="font-medium">{{ pub.year }}</span>
                </div>
              </div>
              
              <div class="flex flex-col items-end gap-2">
                <button v-if="pub.status === 'Published'" 
                        class="bg-primary-600 hover:bg-primary-500 text-white px-4 py-2 rounded-lg text-sm font-medium transition-colors">
                  View Paper
                </button>
                <div class="text-right text-xs text-slate-500">
                  Impact Factor: High
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Industry CTA Section -->
    <section id="contact" class="py-16 sm:py-24 md:py-32 relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-r from-primary-900/20 to-emerald-900/20"></div>
      
      <div class="relative z-10 max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h2 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-bold mb-6 sm:mb-8 bg-gradient-to-r from-white to-primary-300 bg-clip-text text-transparent leading-tight">
          Let's Drive Innovation Together
        </h2>
        
        <p class="text-base sm:text-lg md:text-xl text-slate-300 mb-8 sm:mb-12 max-w-2xl mx-auto leading-relaxed px-4">
          With my Ph.D. completion in January 2025, I'm actively pursuing opportunities to translate cutting-edge materials research into transformative industrial solutions. Ready to bring 4+ years of R&D expertise to your team.
        </p>

        <!-- Contact Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 sm:gap-6 mb-8 sm:mb-12">
          <!-- Phone Contact -->
          <div class="bg-slate-800/50 backdrop-blur-sm rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-primary-500/30 hover:border-primary-400/50 transition-all duration-300 text-center">
            <h3 class="text-base sm:text-lg font-semibold text-primary-300 mb-3 sm:mb-4">Schedule a Call</h3>
            <p class="text-sm sm:text-base text-slate-400 mb-4 sm:mb-6">Let's discuss opportunities and how I can contribute to your team</p>
            
            <!-- Phone Icon Button -->
            <a :href="`tel:${profileData.phone}`" 
               @click="contactClicked.phone = true"
               class="inline-flex items-center justify-center w-16 h-16 sm:w-20 sm:h-20 bg-primary-600/20 hover:bg-primary-600/30 border-2 border-primary-500/50 hover:border-primary-400 rounded-full transition-all duration-300 hover:scale-110 group mb-4">
              <svg class="w-6 h-6 sm:w-8 sm:h-8 text-primary-400 group-hover:text-primary-300" fill="currentColor" viewBox="0 0 24 24">
                <path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/>
              </svg>
            </a>
            
            <div class="text-xs sm:text-sm text-slate-400">
              Click to open dialer
            </div>
            
            <!-- Show phone number after clicking -->
            <div v-if="contactClicked.phone" class="mt-3 text-sm sm:text-base text-primary-300 font-medium">
              {{ profileData.phone }}
            </div>
          </div>
          
          <!-- Email Contact -->
          <div class="bg-slate-800/50 backdrop-blur-sm rounded-xl sm:rounded-2xl p-4 sm:p-6 border border-emerald-500/30 hover:border-emerald-400/50 transition-all duration-300 text-center">
            <h3 class="text-base sm:text-lg font-semibold text-emerald-300 mb-3 sm:mb-4">Send an Email</h3>
            <p class="text-sm sm:text-base text-slate-400 mb-4 sm:mb-6">Reach out directly for collaboration opportunities</p>
            
            <!-- Email Icon Button -->
            <a :href="`mailto:${profileData.email}`" 
               @click="contactClicked.email = true"
               class="inline-flex items-center justify-center w-16 h-16 sm:w-20 sm:h-20 bg-emerald-600/20 hover:bg-emerald-600/30 border-2 border-emerald-500/50 hover:border-emerald-400 rounded-full transition-all duration-300 hover:scale-110 group mb-4">
              <svg class="w-6 h-6 sm:w-8 sm:h-8 text-emerald-400 group-hover:text-emerald-300" fill="currentColor" viewBox="0 0 24 24">
                <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
              </svg>
            </a>
            
            <div class="text-xs sm:text-sm text-slate-400">
              Click to open email client
            </div>
            
            <!-- Show email after clicking -->
            <div v-if="contactClicked.email" class="mt-3 text-sm sm:text-base text-emerald-300 font-medium">
              {{ profileData.email }}
            </div>
          </div>
        </div>

        <!-- Professional Links -->
        <div class="flex flex-col sm:flex-row flex-wrap justify-center gap-3 sm:gap-4 md:gap-6">
          <a :href="profileData.linkedin" target="_blank"
             class="flex items-center justify-center bg-blue-600/20 hover:bg-blue-600/30 border border-blue-500/30 rounded-lg sm:rounded-xl px-4 sm:px-6 py-2 sm:py-3 transition-all duration-300 hover:scale-105">
            <svg class="w-4 h-4 sm:w-5 sm:h-5 mr-2 sm:mr-3" fill="currentColor" viewBox="0 0 24 24">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
            <span class="text-blue-300 text-sm sm:text-base">LinkedIn Profile</span>
          </a>
          <a :href="profileData.googleScholar" target="_blank"
             class="flex items-center justify-center bg-green-600/20 hover:bg-green-600/30 border border-green-500/30 rounded-lg sm:rounded-xl px-4 sm:px-6 py-2 sm:py-3 transition-all duration-300 hover:scale-105">
            <svg class="w-4 h-4 sm:w-5 sm:h-5 mr-2 sm:mr-3" fill="currentColor" viewBox="0 0 24 24">
              <path d="M5.242 13.769L0 9.5 12 0l12 9.5-5.242 4.269C17.548 11.249 14.978 9.5 12 9.5c-2.977 0-5.548 1.748-6.758 4.269zM12 10a7 7 0 1 0 0 14 7 7 0 0 0 0-14z"/>
            </svg>
            <span class="text-green-300 text-sm sm:text-base">Google Scholar</span>
          </a>
          <button @click="downloadResume"
                  class="flex items-center justify-center bg-purple-600/20 hover:bg-purple-600/30 border border-purple-500/30 rounded-lg sm:rounded-xl px-4 sm:px-6 py-2 sm:py-3 transition-all duration-300 hover:scale-105">
            <svg class="w-4 h-4 sm:w-5 sm:h-5 mr-2 sm:mr-3" fill="currentColor" viewBox="0 0 24 24">
              <path d="M14,2H6A2,2 0 0,0 4,4V20A2,2 0 0,0 6,22H18A2,2 0 0,0 20,20V8L14,2M18,20H6V4H13V9H18V20Z"/>
            </svg>
            <span class="text-purple-300 text-sm sm:text-base">Download Resume</span>
          </button>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import { profileData } from '@/data/profile.js'
import MolecularAnimation from '@/components/MolecularAnimation.vue'

export default {
  name: 'ProfileView',
  components: {
    MolecularAnimation
  },
  data() {
    return {
      profileData,
      displayedName: '',
      isTyping: true,
      expandedItems: [],
      activeSkill: null,
      activeSection: 'hero',
      // Contact state
      contactClicked: {
        email: false,
        phone: false
      }
    }
  },
  mounted() {
    this.typewriterEffect()
    this.setupScrollDetection()
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    typewriterEffect() {
      const fullName = this.profileData.name
      let index = 0
      
      const type = () => {
        if (index < fullName.length) {
          this.displayedName += fullName.charAt(index)
          index++
          setTimeout(type, 100)
        } else {
          this.isTyping = false
        }
      }
      
      type()
    },
    
    scrollToSection(sectionId) {
      document.getElementById(sectionId).scrollIntoView({ behavior: 'smooth' })
    },

    setupScrollDetection() {
      this.handleScroll = this.throttle(() => {
        const sections = ['hero', 'about', 'timeline', 'skills', 'publications', 'contact']
        const scrollPosition = window.scrollY + 200 // 200px offset from top
        
        // Default to hero
        let currentSection = 'hero'

        // Check each section
        for (const sectionId of sections) {
          const section = document.getElementById(sectionId)
          if (section) {
            const sectionTop = section.offsetTop
            const sectionBottom = sectionTop + section.offsetHeight
            
            // If scroll position is within this section
            if (scrollPosition >= sectionTop && scrollPosition < sectionBottom) {
              currentSection = sectionId
              break
            }
          }
        }

        // Update active section if it changed
        if (this.activeSection !== currentSection) {
          this.activeSection = currentSection
        }
      }, 50)

      window.addEventListener('scroll', this.handleScroll, { passive: true })
      this.handleScroll() // Call once to set initial state
    },

    throttle(func, limit) {
      let inThrottle
      return function() {
        const args = arguments
        const context = this
        if (!inThrottle) {
          func.apply(context, args)
          inThrottle = true
          setTimeout(() => inThrottle = false, limit)
        }
      }
    },
    
    toggleExpanded(index) {
      if (this.expandedItems.includes(index)) {
        this.expandedItems = this.expandedItems.filter(i => i !== index)
      } else {
        this.expandedItems.push(index)
      }
    },
    
    setActiveSkill(skill) {
      this.activeSkill = skill
    },
    
    getInterestIcon(interest) {
      const icons = {
        'Materials Chemistry': '🧪',
        'Semiconductor Materials': '💎',
        'Advanced Characterization Techniques': '🔬',
        'Process Optimization': '⚙️',
        'Design of Experiments (DOE)': '📊',
        'Data Science & Analytics': '📈',
        'Scientific Inquiry': '🔍',
        'Sustainable Materials': '🌱'
      }
      return icons[interest] || '⚛️'
    },

    getInterestIconPath(interest) {
      const paths = {
        'Materials Chemistry': 'M9 11H7v3h2v-3zm4 0h-2v3h2v-3zm4 0h-2v3h2v-3zm2-7h-2V2a1 1 0 0 0-1-1H8a1 1 0 0 0-1 1v2H5a1 1 0 0 0-1 1v16a1 1 0 0 0 1 1h14a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1zM9 2h6v2H9V2zm10 18H5V6h14v14z',
        'Semiconductor Materials': 'M6 2l1.5 4 4-1.5L10 7l2 2-2.5 1.5L11 12l-4 1.5L8.5 17 6 16l-1.5-4 1.5-1.5L4 8l2-2L4.5 4.5 6 2zm6 0l1.5 4 4-1.5L16 7l2 2-2.5 1.5L17 12l-4 1.5L14.5 17 12 16l-1.5-4 1.5-1.5L10 8l2-2L10.5 4.5 12 2z',
        'Advanced Characterization Techniques': 'M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z',
        'Process Optimization': 'M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z',
        'Design of Experiments (DOE)': 'M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z',
        'Data Science & Analytics': 'M16 6l2.29 2.29-4.88 4.88-4-4L2 16.59 3.41 18l6-6 4 4 6.3-6.29L22 12V6z',
        'Scientific Inquiry': 'M15.5 14h-.79l-.28-.27A6.471 6.471 0 0 0 16 9.5 6.5 6.5 0 1 0 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z',
        'Sustainable Materials': 'M17 8C8 10 5.9 16.17 3.82 21.34l1.89.66.95-2.34c.48-.07.96-.17 1.34-.34C9.37 18.75 12 15.91 12 11.5c0-4.14-2.5-6.5-6-6.5z'
      }
      return paths[interest] || 'M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z'
    },
    
    getExpertiseLevel(interest) {
      const levels = {
        'Materials Chemistry': 5,
        'Semiconductor Materials': 4,
        'Advanced Characterization Techniques': 5,
        'Process Optimization': 4,
        'Design of Experiments (DOE)': 4,
        'Data Science & Analytics': 4,
        'Scientific Inquiry': 5,
        'Sustainable Materials': 4
      }
      return levels[interest] || 3
    },

    getExpertiseDescription(interest) {
      const descriptions = {
        'Materials Chemistry': 'PhD Research',
        'Semiconductor Materials': 'Advanced',
        'Advanced Characterization Techniques': 'Expert',
        'Process Optimization': 'Advanced',
        'Design of Experiments (DOE)': 'Proficient',
        'Data Science & Analytics': 'Proficient',
        'Scientific Inquiry': 'Expert',
        'Sustainable Materials': 'Advanced'
      }
      return descriptions[interest] || 'Proficient'
    },

    getSkillLevel(skillName) {
      const coreSkills = {
        'Software & Analysis Tools': 5,
        'Advanced Characterization': 5,
        'Microscopy & Spectroscopy': 4,
        'Fabrication Techniques': 3,
        'Data Science & DOE': 5,
        'Statistical Analysis': 4,
        'Leadership & Management': 5,
        'Communication': 5,
        'Problem-Solving': 5
      }
      return coreSkills[skillName] || 3
    },

    getSkillExperience(skillName) {
      const experience = {
        'Software & Analysis Tools': '4+ Years',
        'Advanced Characterization': '4+ Years',
        'Microscopy & Spectroscopy': '3+ Years',
        'Fabrication Techniques': 'Familiar',
        'Data Science & DOE': '4+ Years',
        'Statistical Analysis': '3+ Years',
        'Leadership & Management': '2+ Years',
        'Communication': '4+ Years',
        'Problem-Solving': '4+ Years'
      }
      return experience[skillName] || 'Experienced'
    },

    isCore(skillName) {
      const coreSkills = [
        'Software & Analysis Tools',
        'Advanced Characterization',
        'Data Science & DOE',
        'Leadership & Management',
        'Problem-Solving'
      ]
      return coreSkills.includes(skillName)
    },
    
    downloadResume() {
      // Simulate resume download
      alert('Resume download would start here. Link to actual PDF file.')
    },

    getCategoryIcon(category) {
      const icons = {
        'computational': '💻',
        'experimental': '🔬',
        'analytical': '📊',
        'professional': '👥'
      }
      return icons[category] || '⚛️'
    },

    getCategoryIconPath(category) {
      const paths = {
        'computational': 'M20 6h-2.18c.11-.31.18-.65.18-1a2.996 2.996 0 0 0-5.5-1.65l-.5.67-.5-.68C10.96 2.54 10.05 2 9 2 7.34 2 6 3.34 6 5c0 .35.07.69.18 1H4c-1.11 0-1.99.89-1.99 2L2 19c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V8c0-1.11-.89-2-2-2zm-5-2c.55 0 1 .45 1 1s-.45 1-1 1-1-.45-1-1 .45-1 1-1zM9 4c.55 0 1 .45 1 1s-.45 1-1 1-1-.45-1-1 .45-1 1-1z',
        'experimental': 'M19.8 18.4L14 10.67V6.5l1.35-1.69c.26-.33.03-.81-.39-.81H9.04c-.42 0-.65.48-.39.81L10 6.5v4.17L4.2 18.4c-.49.66-.02 1.6.8 1.6h14c.82 0 1.29-.94.8-1.6z',
        'analytical': 'M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z',
        'professional': 'M16 4c0-1.11.89-2 2-2s2 .89 2 2-.89 2-2 2-2-.89-2-2zm4 18v-6h2.5l-2.54-7.63A1.997 1.997 0 0 0 18.05 7H16c-.8 0-1.54.37-2.01.99L12 10.5v3.5c0 .55-.45 1-1 1s-1-.45-1-1v-4l-1.8-2.4A1.993 1.993 0 0 0 6.6 7H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h2v-6.5c0-.28.22-.5.5-.5s.5.22.5.5V22h12z'
      }
      return paths[category] || 'M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z'
    },

    formatCategoryName(category) {
      return category.replace(/([A-Z])/g, ' $1').replace(/^./, str => str.toUpperCase())
    },

    getCategoryDescription(category) {
      const descriptions = {
        'computational': 'Software tools and data analysis platforms',
        'experimental': 'Laboratory techniques and characterization methods',
        'analytical': 'Statistical analysis and design methodologies',
        'professional': 'Leadership and communication capabilities'
      }
      return descriptions[category] || 'Specialized technical skills'
    },

    getSkillCount(category) {
      return this.profileData.skills[category]?.length || 0
    },

    getProficiencyLevel(level) {
      if (level >= 95) return 'Expert'
      if (level >= 85) return 'Advanced'
      if (level >= 70) return 'Proficient'
      return 'Intermediate'
    },

    getProficiencyBadgeClass(level) {
      if (level >= 95) return 'bg-emerald-600/20 text-emerald-300 border border-emerald-500/30'
      if (level >= 85) return 'bg-blue-600/20 text-blue-300 border border-blue-500/30'
      if (level >= 70) return 'bg-purple-600/20 text-purple-300 border border-purple-500/30'
      return 'bg-slate-600/20 text-slate-300 border border-slate-500/30'
    }
  }
}
</script>

<style scoped>
@keyframes spin-slow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes spin-reverse {
  from { transform: rotate(360deg); }
  to { transform: rotate(0deg); }
}

.animate-spin-slow {
  animation: spin-slow 8s linear infinite;
}

.animate-spin-reverse {
  animation: spin-reverse 6s linear infinite;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #1e293b;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #14b8a6, #0d9488);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #0d9488, #0f766e);
}
</style>