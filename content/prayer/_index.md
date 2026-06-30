---
title: "기도 요청"
layout: "simple"
---

<div class="py-6 max-w-xl mx-auto font-sans leading-relaxed text-slate-700 dark:text-neutral-300">

<div class="text-center mb-10">
<p class="text-lg text-slate-600 dark:text-neutral-400">
"혼자서 감당하기 어려운 슬픔과 기도의 제목이 있으신가요? 최세나 담임목사님이 성도님의 기도제목을 직접 읽고 마음을 다해 함께 기도합니다. 모든 내용은 철저히 비밀이 보장됩니다."
</p>
</div>

<!-- 기도 요청 폼 -->
<div class="bg-white dark:bg-neutral-800 rounded-3xl border border-slate-100 dark:border-neutral-700 p-8 shadow-sm">
<form onsubmit="alert('소중한 기도 제목이 담임목사님께 전달되었습니다. 함께 마음을 모아 기도하겠습니다.'); this.reset(); return false;" class="space-y-6">

<!-- 이름 -->
<div>
<label for="name" class="block text-sm font-semibold text-slate-700 dark:text-neutral-200 mb-2">이름</label>
<input 
type="text" 
id="name" 
name="name" 
placeholder="익명으로 남기셔도 좋습니다" 
class="w-full px-4 py-3 bg-slate-50 dark:bg-neutral-900 border border-slate-200 dark:border-neutral-700 rounded-xl focus:outline-none focus:ring-2 focus:ring-sky-500 focus:border-transparent transition-all"
>
</div>

<!-- 연락처 -->
<div>
<label for="contact" class="block text-sm font-semibold text-slate-700 dark:text-neutral-200 mb-2">연락처 (선택)</label>
<input 
type="text" 
id="contact" 
name="contact" 
placeholder="답변을 원하시면 연락처를 남겨주세요" 
class="w-full px-4 py-3 bg-slate-50 dark:bg-neutral-900 border border-slate-200 dark:border-neutral-700 rounded-xl focus:outline-none focus:ring-2 focus:ring-sky-500 focus:border-transparent transition-all"
>
</div>

<!-- 기도 제목 -->
<div>
<label for="prayer-request" class="block text-sm font-semibold text-slate-700 dark:text-neutral-200 mb-2">기도 제목</label>
<textarea 
id="prayer-request" 
name="prayer-request" 
rows="5" 
required 
placeholder="여기에 기도 제목을 마음 편히 적어주세요. 담임목사님만 읽고 기도합니다." 
class="w-full px-4 py-3 bg-slate-50 dark:bg-neutral-900 border border-slate-200 dark:border-neutral-700 rounded-xl focus:outline-none focus:ring-2 focus:ring-sky-500 focus:border-transparent transition-all"
></textarea>
</div>

<!-- 비공개 안내 배너 -->
<div class="flex items-start gap-2 text-xs text-emerald-600 dark:text-emerald-400 bg-emerald-50/50 dark:bg-emerald-950/20 p-4 rounded-xl">
<svg class="w-4 h-4 mt-0.5 fill-current shrink-0" viewBox="0 0 20 20">
<path fill-rule="evenodd" d="M2.166 2.22a.75.75 0 00-1.096 1.024L3 5.182v10.568A2.25 2.25 0 005.25 18h9.5A2.25 2.25 0 0017 15.75V5.182l1.93-1.938a.75.75 0 10-1.096-1.024L2.166 2.22zM5.25 4.5h8.924L5.25 13.424V4.5zm1.5 12h7.5a.75.75 0 00.75-.75V7.424l-8.25 8.25v.076a.75.75 0 00.75.75zm10.75-9.75v6a.75.75 0 11-1.5 0v-6a.75.75 0 111.5 0z" clip-rule="evenodd"/>
</svg>
<span>
🔒 작성해주신 기도의 제목은 담임목사 개인 메일로 직송되며, 어떠한 경우에도 외부나 타인에게 일절 공개되지 않음을 약속드립니다.
</span>
</div>

<!-- 제출 버튼 -->
<div>
<button 
type="submit" 
class="w-full py-4 text-center text-sm font-semibold text-white bg-sky-500 hover:bg-sky-600 rounded-xl shadow-sm transition-transform hover:-translate-y-0.5"
>
🙏 담임목사님께 기도 요청 전송
</button>
</div>

</form>
</div>
</div>
