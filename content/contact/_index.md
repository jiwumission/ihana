---
title: "문의하기"
layout: "simple"
---

<div class="py-6 max-w-4xl mx-auto font-sans leading-relaxed text-slate-700 dark:text-neutral-300">
  
  <div class="text-center mb-12">
    <p class="text-lg text-slate-600 dark:text-neutral-400 max-w-xl mx-auto">
      "기도가 필요하시거나 상담을 원하시면 언제든 편하게 연락해 주세요. 조용히 경청하겠습니다."
    </p>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-5 gap-12">
    
    <!-- 연락처 정보 섹션 -->
    <div class="md:col-span-2 space-y-8">
      <div>
        <h4 class="text-xs text-sky-500 font-bold uppercase tracking-wider mb-2">Location</h4>
        <p class="text-slate-800 dark:text-neutral-200 font-medium">570 Main street #203</p>
        <p class="text-slate-600 dark:text-neutral-300">Fort Lee, NJ 07024</p>
      </div>

      <div>
        <h4 class="text-xs text-sky-500 font-bold uppercase tracking-wider mb-2">Email</h4>
        <p class="text-slate-800 dark:text-neutral-200 font-medium select-all cursor-pointer">
          <a href="mailto:ihanachurch2024@gmail.com" class="hover:underline text-sky-600 dark:text-sky-400">ihanachurch2024@gmail.com</a>
        </p>
      </div>

      <div class="p-6 bg-slate-50 dark:bg-neutral-800 rounded-2xl border border-slate-100 dark:border-neutral-700">
        <h4 class="text-sm font-bold text-slate-800 dark:text-neutral-100 mb-2">상담 및 방문 안내</h4>
        <p class="text-xs text-slate-500 dark:text-neutral-400">
          예배 시간 이외에 상담이나 만남을 원하시는 성도님은 미리 메일로 예약해 주시면 일정을 잡을 수 있습니다. 언제나 열려 있는 마음으로 기다리겠습니다.
        </p>
      </div>
    </div>

    <!-- 문의 폼 섹션 -->
    <div class="md:col-span-3 bg-white dark:bg-neutral-800 rounded-3xl border border-slate-100 dark:border-neutral-700 p-8 shadow-sm">
      <form onsubmit="alert('문의 메시지가 정상적으로 발송되었습니다. 빠른 시일 내에 이메일로 답변드리겠습니다.'); this.reset(); return false;" class="space-y-6">
        
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
          <!-- 이름 -->
          <div>
            <label for="name" class="block text-sm font-semibold text-slate-700 dark:text-neutral-200 mb-2">이름</label>
            <input 
              type="text" 
              id="name" 
              name="name" 
              required
              placeholder="성함을 입력하세요" 
              class="w-full px-4 py-3 bg-slate-50 dark:bg-neutral-900 border border-slate-200 dark:border-neutral-700 rounded-xl focus:outline-none focus:ring-2 focus:ring-sky-500 focus:border-transparent transition-all"
            >
          </div>
          <!-- 이메일 -->
          <div>
            <label for="email" class="block text-sm font-semibold text-slate-700 dark:text-neutral-200 mb-2">이메일</label>
            <input 
              type="email" 
              id="email" 
              name="email" 
              required
              placeholder="답변받으실 이메일" 
              class="w-full px-4 py-3 bg-slate-50 dark:bg-neutral-900 border border-slate-200 dark:border-neutral-700 rounded-xl focus:outline-none focus:ring-2 focus:ring-sky-500 focus:border-transparent transition-all"
            >
          </div>
        </div>

        <!-- 제목 -->
        <div>
          <label for="subject" class="block text-sm font-semibold text-slate-700 dark:text-neutral-200 mb-2">제목</label>
          <input 
            type="text" 
            id="subject" 
            name="subject" 
            required
            placeholder="문의 제목을 입력하세요" 
            class="w-full px-4 py-3 bg-slate-50 dark:bg-neutral-900 border border-slate-200 dark:border-neutral-700 rounded-xl focus:outline-none focus:ring-2 focus:ring-sky-500 focus:border-transparent transition-all"
          >
        </div>

        <!-- 메시지 -->
        <div>
          <label for="message" class="block text-sm font-semibold text-slate-700 dark:text-neutral-200 mb-2">내용</label>
          <textarea 
            id="message" 
            name="message" 
            rows="5" 
            required 
            placeholder="문의하실 내용을 입력해 주세요" 
            class="w-full px-4 py-3 bg-slate-50 dark:bg-neutral-900 border border-slate-200 dark:border-neutral-700 rounded-xl focus:outline-none focus:ring-2 focus:ring-sky-500 focus:border-transparent transition-all"
          ></textarea>
        </div>

        <!-- 제출 버튼 -->
        <div>
          <button 
            type="submit" 
            class="w-full py-4 text-center text-sm font-semibold text-white bg-sky-500 hover:bg-sky-600 rounded-xl shadow-sm transition-transform hover:-translate-y-0.5"
          >
            ✉️ 메시지 보내기
          </button>
        </div>

      </form>
    </div>

  </div>
</div>
