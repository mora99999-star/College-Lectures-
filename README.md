<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>امتحان محاسبة التكاليف - المحاضرة الأولى</title>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800&display=swap" rel="stylesheet">
<style>
:root{--bg:#eef2f6;--card:#fff;--ink:#14213d;--mute:#5b6678;--line:#d5dce6;--acc:#1b5fa8;--ok:#1f8a4c;--okbg:#e4f5ec;--bad:#c0392b;--badbg:#fbe9e7}
@media(prefers-color-scheme:dark){:root{--bg:#0f1624;--card:#18223a;--ink:#e8edf6;--mute:#9aa6bd;--line:#2c3a58;--acc:#5aa2e8;--ok:#4cc585;--okbg:#14302350;--bad:#ef7f72;--badbg:#3a181850}}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:Tajawal,Tahoma,sans-serif;line-height:1.8;font-size:17px}
.wrap{max-width:720px;margin:0 auto;padding:20px 16px 48px}
.card{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:22px}
h1{font-size:26px;margin:0 0 6px;font-weight:800}
p.sub{color:var(--mute);margin:0 0 18px}
.bar{height:8px;background:var(--line);border-radius:8px;overflow:hidden;margin-bottom:6px}
.bar i{display:block;height:100%;background:var(--acc);width:0;transition:width .3s}
.meta{display:flex;justify-content:space-between;color:var(--mute);font-size:14px;margin-bottom:14px}
.q{font-size:20px;font-weight:700;margin:0 0 16px}
.opt{display:flex;gap:12px;align-items:flex-start;width:100%;text-align:right;background:var(--card);color:var(--ink);border:1.5px solid var(--line);border-radius:10px;padding:12px 14px;margin-bottom:10px;font:inherit;cursor:pointer}
.opt:hover{border-color:var(--acc)}
.opt:focus-visible,.btn:focus-visible{outline:3px solid var(--acc);outline-offset:2px}
.opt b{flex:none;width:28px;height:28px;border-radius:50%;border:1.5px solid var(--line);display:grid;place-items:center;font-size:14px}
.opt.sel{border-color:var(--acc);background:color-mix(in srgb,var(--acc) 10%,var(--card))}
.opt.sel b{background:var(--acc);color:#fff;border-color:var(--acc)}
.opt.ok{border-color:var(--ok);background:var(--okbg)}
.opt.no{border-color:var(--bad);background:var(--badbg)}
.row{display:flex;gap:10px;margin-top:16px}
.btn{font:inherit;font-weight:700;border:0;border-radius:10px;padding:11px 22px;cursor:pointer;background:var(--acc);color:#fff}
.btn.alt{background:transparent;color:var(--ink);border:1.5px solid var(--line)}
.btn:disabled{opacity:.4;cursor:not-allowed}
.score{font-size:54px;font-weight:800;margin:6px 0}
.rev{border-top:1px solid var(--line);padding-top:14px;margin-top:14px}
.rev .q{font-size:17px;margin-bottom:8px}
.tag{font-size:14px;margin:2px 0}
.good{color:var(--ok)}.bad{color:var(--bad)}
.opt:disabled{color:var(--ink);cursor:default}
.opt:disabled:hover{border-color:var(--line)}
.opt.ok:disabled:hover{border-color:var(--ok)}
.opt.no:disabled:hover{border-color:var(--bad)}
.fb{font-weight:700;margin:6px 0 0;min-height:1.8em}
.hide{display:none}
</style>
</head>
<body>
<div class="wrap">
 <div id="start" class="card">
  <h1>امتحان محاسبة التكاليف</h1>
  <p class="sub">المحاضرة الأولى · 15 سؤال اختيار من متعدد</p>
  <button class="btn" id="go">ابدأ الامتحان</button>
 </div>
 <div id="quiz" class="card hide">
  <div class="meta"><span id="cnt"></span><span id="sc"></span></div>
  <div class="bar"><i id="pb"></i></div>
  <p class="q" id="qt"></p>
  <div id="opts"></div>
  <p class="fb" id="fb"></p>
  <div class="row">
   <button class="btn alt" id="prev">السابق</button>
   <button class="btn" id="next">التالي</button>
  </div>
 </div>
 <div id="res" class="card hide"></div>
</div>
<script>
const L=["أ","ب","ج","د"];
const Q=[
{q:"ما هو التعريف الأساسي لمصطلح \"محاسبة التكاليف\" بناءً على محتوى المحاضرة؟",o:["سجل لحسابات العملاء والموردين في المنشأة.","نظام لإنتاج معلومات محاسبية تستخدم في اتخاذ القرارات بواسطة متخذي القرارات ومستخدمي المعلومات.","قائمة مالية تحدد صافي الربح والخسارة في نهاية السنة المالية.","نظام لتقييم أداء الإدارة العليا فقط."],a:1},
{q:"وفقاً للتفرقة بين المفاهيم في المحاضرة الأولى، كيف يتم تعريف \"المصروف\"؟",o:["التكلفة التي لم تستنفذ بعد.","النفقات التي تم إنفاقها في الماضي ولا يمكن تعديلها.","اللي استفدت بيه.","العائد الضائع لعدم استخدام أفضل بديل."],a:2},
{q:"ما هو التصنيف الصحيح لعناصر تكاليف الموارد المباشرة في العملية الإنتاجية؟",o:["أجور، مواد، ومصروفات.","أصول ثابتة ومتداولة.","تكاليف غارقة وتكاليف تفاضلية.","إيرادات ومصروفات نقدية."],a:0},
{q:"أي من الخيارات التالية يعتبر مثالاً صحيحاً لـ \"أجور غير مباشرة\"؟",o:["أجور عمال الإنتاج على خط التجميع المباشر.","رواتب المشرفين والصيانة العامة للآلات وإيجار المصنع والكهرباء العامة.","تكلفة المواد الخام الأساسية الداخلة في المنتج.","أجور العمالة المؤقتة المرتبطة مباشرة بالوحدة المنتجة."],a:1},
{q:"كيف تتصرف \"التكاليف الثابتة\" عند تغير حجم النشاط الإنتاجي؟",o:["تتغير طردياً مع حجم النشاط (زيادة ونقصاناً).","تتغير عكسياً مع حجم النشاط.","لا تتغير بتغير حجم النشاط.","تختفي تماماً عند توقف الإنتاج."],a:2},
{q:"ما هي المعادلة المحاسبية الأساسية للأصول الواردة في المحاضرة؟",o:["الأصول = الخصوم + حقوق الملكية","الأصول = الإيرادات - التكاليف","الأصول = الأرباح / إجمالي المبيعات","الأصول = التكاليف المباشرة + التكاليف المتغيرة"],a:0},
{q:"ماذا يقصد بمفهوم \"تكلفة الفرصة البديلة\" حسب تصنيفات التكاليف في المحاضرة؟",o:["التكاليف التي حصلت في الماضي ولا يمكن تعديلها.","العائد الضائع لعدم استخدام أفضل بديل من البدائل الموجودة.","النفقات الخارجية التي تتعهد المنشأة بدفعها مستقبلاً.","التكاليف التي لم تستنفذ بعد."],a:1},
{q:"ما هي سمة \"التكاليف الغارقة\" كما وردت في المحاضرة؟",o:["تختلف من بديل لآخر وتؤخذ في الاعتبار عند اتخاذ القرار.","حصلت في الماضي ولا يمكن تعديلها أو تغييرها.","تتغير كلياً بتغير حجم النشاط الإنتاجي.","تمثل المواد الخام غير المستخدمة حتى نهاية الفترة."],a:1},
{q:"فيما يتعلق بالالتزام بالمعايير، ما هو الفرق الجوهري بين المحاسبة المالية ومحاسبة التكاليف؟",o:["المحاسبة المالية تشتغل بمعايير المحاسبة، بينما محاسبة التكاليف لا تلتزم بمعايير المحاسبة.","محاسبة التكاليف تلتزم بمعايير صارمة، بينما المحاسبة المالية اختيارية.","كلاهما يلتزمان بنفس المعايير المحاسبية الدولية دون اختلاف.","المحاسبة المالية لا تعترف بالمصروفات نهائياً."],a:0},
{q:"أي مما يلي يُعد مثالاً على \"تكاليف متغيرة\"؟",o:["إيجار المصنع ومرتبات الإدارة.","إهلاك الآلات والمباني والتأمين.","المواد الخام، تكاليف التغليف، وأجور عمال الإنتاج بالساعة أو القطعة.","رواتب المشرفين والصيانة العامة."],a:2},
{q:"كيف تم تعريف \"التكاليف غير المستنفذة\"؟",o:["هي التكاليف التي تم إنفاقها بالفعل ولم يعد لها منفعة مستقبلية.","هي التكاليف التي لم تستنفذ بعد وتحتفظ بمنفعتها المستقبلية.","هي النفقات النقدية الخارجة عن المنشأة فوراً.","هي التكاليف التي تختلف من بديل لآخر."],a:1},
{q:"ما هو التوصيف الدقيق لـ \"التكلفة النقدية أو المنفقة\"؟",o:["هي العائد الضائع لعدم استخدام بديل.","هي النفقات الخارجية عن المنشأة والتعاهد بدفعها مستقبلاً.","هي المواد الخام غير المستخدمة في المخازن.","هي إهلاك الأصول الثابتة سنوياً."],a:1},
{q:"ما هو تعريف \"التكاليف التفاضلية\"؟",o:["التكاليف التي حصلت في الماضي ولا يمكن تغييرها.","التكاليف التي لا تتغير مهما تغير حجم النشاط.","التكاليف التي تختلف من بديل لآخر وتؤخذ في الاعتبار عند اتخاذ القرار.","تكلفة المواد غير المباشرة اللازمة للإنتاج."],a:2},
{q:"ماذا تعني كلمة \"التكلفة\" وفقاً للتقسيم الأولي في المحاضرة؟",o:["اللي استفدت بيه بالفعل.","اللي لسة مستفدتش بيه.","الإيرادات المحققة بالكامل.","الأرباح المحتجزة للمنشأة."],a:1},
{q:"تحت أي بند تقع أمثلة مثل: (إيجار المصنع، مرتبات الإدارة، التأمين، إهلاك الآلات والمباني)؟",o:["التكاليف المتغيرة","التكاليف المباشرة","التكاليف الثابتة","التكاليف الغارقة"],a:2}
];
const $=id=>document.getElementById(id);
let i=0,ans=[];
function show(id){["start","quiz","res"].forEach(x=>$(x).classList.toggle("hide",x!==id))}
function render(){
 const q=Q[i];
 $("cnt").textContent="سؤال "+(i+1)+" من "+Q.length;
 $("sc").textContent="تمت الإجابة على "+ans.filter(x=>x!==undefined).length;
 $("pb").style.width=((i+1)/Q.length*100)+"%";
 $("qt").textContent=(i+1)+". "+q.q;
 $("opts").innerHTML="";
 q.o.forEach((t,k)=>{
  const b=document.createElement("button");
  const done=ans[i]!==undefined;
  let c="opt";
  if(done){if(k===q.a)c+=" ok";else if(k===ans[i])c+=" no"}
  b.className=c;
  b.innerHTML="<b>"+L[k]+"</b><span></span>";
  b.lastChild.textContent=t;
  if(done)b.disabled=true;else b.onclick=()=>{ans[i]=k;render()};
  $("opts").appendChild(b);
 });
 const f=$("fb");
 if(ans[i]===undefined){f.textContent="";f.className="fb"}
 else if(ans[i]===q.a){f.textContent="إجابة صحيحة ✓";f.className="fb good"}
 else{f.textContent="إجابة غلط ✗ — الصحيحة: "+L[q.a];f.className="fb bad"}
 $("prev").disabled=i===0;
 $("next").textContent=i===Q.length-1?"إنهاء وعرض النتيجة":"التالي";
 $("next").disabled=ans[i]===undefined;
}
function finish(){
 const n=Q.filter((q,k)=>ans[k]===q.a).length;
 const p=Math.round(n/Q.length*100);
 let h="<h1>النتيجة</h1><div class='score'>"+n+" / "+Q.length+"</div><p class='sub'>"+p+"%</p><button class='btn' id='again'>إعادة الامتحان</button>";
 Q.forEach((q,k)=>{
  const okk=ans[k]===q.a;
  h+="<div class='rev'><p class='q'></p><p class='tag "+(okk?"good":"bad")+"'>إجابتك: "+L[ans[k]]+") <span class='u'></span></p>"+(okk?"":"<p class='tag good'>الإجابة الصحيحة: "+L[q.a]+") <span class='c'></span></p>")+"</div>";
 });
 $("res").innerHTML=h;
 const revs=$("res").querySelectorAll(".rev");
 Q.forEach((q,k)=>{
  const r=revs[k];
  r.querySelector(".q").textContent=(k+1)+". "+q.q;
  r.querySelector(".u").textContent=q.o[ans[k]];
  const c=r.querySelector(".c");if(c)c.textContent=q.o[q.a];
 });
 $("again").onclick=()=>{i=0;ans=[];show("quiz");render()};
 show("res");window.scrollTo(0,0);
}
$("go").onclick=()=>{show("quiz");render()};
$("prev").onclick=()=>{if(i>0){i--;render()}};
$("next").onclick=()=>{if(i<Q.length-1){i++;render()}else finish()};
</script>
</body>
</html>
