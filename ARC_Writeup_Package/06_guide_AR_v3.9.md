# دليل تقديم ورقة ARC Paper Track — v3.9 (تصحيحات مراجعة الجولة الثامنة — v14)

## 🎯 الوضع الحقيقي (مؤكَّد بفحصين حيَّين + فحص مجهول الهوية — 5–6 نوفمبر)
- **ورقتنا مُقدَّمة رسمياً منذ 12 سبتمبر 2026**: `https://www.kaggle.com/competitions/arc-prize-2026-paper-track/writeups/new-writeup-1789171832107` — شارة **"Submitted! — Main Track"** ✅.
- **لكن محتواها لم يُحدَّث بعد**: العنوان الفرعي والمتن ما زالا يعرضان التجربتين القديمتين (n=2، 30.97)، والغلاف والرسمان قديمان، والروابط فيها DSL **فقط**.
- **مجموعة البيانات الآن حيّة وعامة (تحقق مجهول الهوية، 6 نوفمبر): الإصدار 5 يعرض PDF v11 مطابقاً للأرشيف بايت-ببايت**، و`isPrivate:false` — يراها الجميع. *(تاريخي: فحص 4 نوفمبر أثبت أن الإصدار 4 كان يعرض v9 مطابقاً للأرشيف.)*
- ⚠ **تصحيحا الجولتين الخامسة والسادسة**: نوتبوك السحبات `defiaudit/arc-agi2-lb33-89-minimal-perfpatch` **ليس محذوفاً** — يعطي 404 للعامة لكنه حيّ **خاص ومُعاد تسميته**، وسجلّه الخادمي (32 إصداراً بينها V12 وV26؛ أفضل نتيجة 31.39 على V9) متاح بصلاحية المالك. لذلك: **لا تضفه في روابط الورقة**، ولا تعتمد أي ادعاء "حذف" — جملة الحذف الأخيرة في §1 من الـPDF صُحِّحت في v12. كما أن مرتبة mikelou1 النهائية **#33** (وليس 17 — لقطة أقدم)، و33.89 **self-label في الاسم فقط** (الصفحة تعرض 32.22)، و**أوصاف الإطلاق حاضرة في 39 من 44 سحبة بدرجة فقط (5 فارغة)**.
- **القاعدة الذهبية: لا تحذف الورقة، ولا تنشئ New Writeup — فقط Edit ثم Update Submission.**

## 🧾 الخطوة 1 — ارفع الإصدار 6 من مجموعة البيانات (الإصدار 5/v11 رُفع فعلاً يوم 5 نوفمبر 15:00 UTC)
المحتوى جاهز كاملاً في مجلد **`10_dataset_upload/`** (v14 PDF + سجل CSV + تصدير التسليمات + لقطتا LB + تقرير الحالة + `code_chapters/` بالأسماء الموحَّدة):
- **من المتصفح**: صفحة `defiaudit/arc-paper-track-2026` ← **New Version** ← اسحب محتويات المجلد كلها ← Save. (ملف `dataset-metadata.json` تُتجاهله الواجهة — اتركه.) الإصداران 4 (v9) و5 (v11) ستبقيان في تاريخ المجموعة تلقائياً.
- **أو بالسطر التنازلي**:
  `kaggle datasets version -p 10_dataset_upload -m "v14: paper v14 PDF (abstract: compare the fit with two related descriptive summaries; rerun-variance scoped to our entry; cover anchor limited to scores)" --dir-mode zip`
- تحقق بعدها: صفحة المجموعة تعرض `ARC_Paper_Track_defiaudit_v14.pdf`.

## ✏️ الخطوة 2 — تعديل الورقة (نفس الرابط — 15 دقيقة)
1. افتح رابط الورقة بحساب defiaudit → **Edit**.
2. **Subtitle**: استبدله كلياً بـ:
   `44 graded hidden-set draws: 43 on one public-notebook fork line, 1 on a second fork (NVARC+); spread 26.39-31.39, sigma 1.09`
   (124 حرفاً من حد 140 — تقول "سحبات الحملة" وتصرّح بالتقسيم 43+1).
3. **المتن**: احذف المتن القديم كاملاً والصق `02_writeup_body_PASTE.md` (**1488 كلمة ✅** من حد 1,500 — النسخة المصحَّحة من صديقك). العنوان لا يتغير.
4. **Media Gallery**:
   - **الغلاف**: استبدله بـ `04_images/cover_2400x1200.png` (نسبة **2:1**).
   - **الرسمان**: `04_images/fig1_draws44.png` (عنوانه "…draws of the campaign…" ونقطة NVARC+ برتقالية) + `04_images/fig2_emax_v5.png`.
5. **Project Links** (⚠ الفحص الحي: فيها DSL فقط):
   - **أضف**: مجموعة البيانات `arc-paper-track-2026` + النوتبوك المصدر `mikelou1/arc-agi2-lb33-89-minimal-perfpatch` (عام، 235 تصويتاً — يُستشهد به كمصدر الفورك).
   - **لا تضف** رابط نوتبوك السحبات القديم (خاص الآن؛ 404 للعامة). إن وُجد من قبل: احذفه.
   - التفاصيل في `05_project_links.txt`.
6. **Track**: يبقى كما هو (ARC-AGI-2 / Main Track).
7. اضغط **Update Submission** مرة واحدة فقط.

## ✅ الخطوة 3 — التحقق بعد التحديث (دقيقتان)
نفّذ `09_live_check.md` قسم ج (6 بنود): الشارة، الـSubtitle حرفياً، بداية/نهاية المتن وعدّاد الكلمات، المعرض (نقطة NVARC+ البرتقالية)، الروابط الثلاثة، وصفحة المجموعة تعرض v14.
(الأقسام ب و ب2 = نتائج الفحصين الحيَّين المنفَّذَين قبل التحديث، للسجل.)

## ما تغيّر في v14 (الجولة الثامنة — مراجعة صديقك لمستودع GitHub عند f19359e)
1. **الملخص**: «validate the fitted distribution against two distinct observables» صارت «compare the fitted distribution with two related descriptive summaries» — بنفس صياغة المتن و§6 (ملخصان وصفيان مرتبطان، وليسا تحققاً مستقلاً).
2. **حصر التعميم**: «أكبر مصدر للتباين في fork-cluster entry» صارت «in **our** fork-cluster entry» في الملخص و§12 — فالعينة 43 سحبة من خط تطوير واحد + سحبة واحدة من NVARC+.
3. **الغلاف**: «every number anchored to a public artifact» صارت «every score anchored to a submission ID» — مطابقة لمتن الصفحة («Graded scores map to submission IDs in the public ledger») وللدليل.
4. **تصحيح روابط قديمة**: README الجذري كان يشير إلى دليل v3.7 (رابط مكسور) وجدوله يقول PDF v12 — صار v3.9 وv14؛ وخطوة التحقق أعلاه كانت تقول v12 — صارت v14؛ ومتن الصفحة نفسه: «this v12 PDF» صارت «this v14 PDF» (ما زال 1488 كلمة ✅).

## ما تغيّر في v13 (الجولة السابعة — مواءمة الورقة مع المتن المصحَّح)
صديقك صحّح متن الصفحة (1488 كلمة) ليقول: اتفاق الحد الأقصى وعدّ تجاوز عتبة البرونز مع الملاءمة **ملخصان وصفيان مرتبطان، ليسا تحققاً مستقلاً ولا دليلاً على قابلية التبادل**. الـPDF v12 كان ما زال يقول "two independent observables … strongest evidence". v13 يواءم الورقة مع المتن في 4 مواضع: الملخص ("two distinct observables")، §2 ("σ barely moves" + "a descriptive similarity that does not by itself establish exchangeability")، §6 ("Two distinct observables" + "the strongest descriptive check … not independent validation of it")، §11 ("we treat draws … as only approximately exchangeable"). المتن المعتمد في الحزمة هو نسخة صديقك المصحَّحة نفسها.

## ما تغيّر في v12 (الجولة السادسة — ملاحظات صديقك)
1. **آخر جملة حذف في الـPDF (§1)**: "Kaggle reports that notebook removed after the campaign" أصبحت "it was later renamed and set private, its 32-version history intact" — تتسق مع §10 وData availability وملفات الحالة.
2. **عدّ أوصاف الإطلاق**: 5 سحبات بدرجة بلا وصف (المراجع 56075910، 56100667، 56125103، 56316858، 56344456 — منها الأفضل 31.39). صُحِّح "fire-time descriptions carry each draw's code label" إلى **39 من 44** في المتن (§2)، وأُضيف العدّ إلى Data availability و§10 من الـPDF وREADME المجموعة و08 README.
3. **صيغة الحاضر**: الدليل (v3.7) وملف الروابط يعرضان الإصدار 5/v11 كواقع حي وعام، مع تمييز فحص v9/الإصدار 4 كتاريخي.
4. الـPDF: v11 → v12 (10 صفحات ✅). المتن: 1499 كلمة ✅. مجموعة البيانات: الإصدار 6.

## ما تغيّر في v11 (للسجل)
1. تصحيح ادعاء الحذف في §10 وData availability والملخص: الدفتر حيّ خاص ومُعاد التسمية، سجله (32 إصداراً؛ v12، v26؛ 31.39 على v9) متاح للمالك — والسجل العام يبقى أوصاف الإطلاق + لقطات الكود.
2. المرتبة: rank 17 (لقطة 29 أكتوبر) → **rank 33 of 3,627** (سحبة 5 نوفمبر).
3. 33.89 → **self-label غير موثَّق مستقلاً** في كل مواضعها (§1 ×2، الملخص، Data availability)، مع 32.22 الحالية؛ "strongest" → "top".
4. §5: "exchangeable samples from one stable generating distribution" → "approximately exchangeable samples of one stable distribution" (توحيد مع §11 و§2).
5. المتن: نفس التصحيحات (1499 كلمة). الـPDF: v10 → v11 (10 صفحات). مجموعة البيانات: الإصدار 5.
