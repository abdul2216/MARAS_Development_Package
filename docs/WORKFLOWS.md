# قواعد سير العمل

## الحالات
NEW, TRIAGE, INSPECTION_REQUIRED, QUOTE_PENDING, APPROVAL_PENDING, SCHEDULED, IN_PROGRESS, AWAITING_ACCEPTANCE, COMPLETED, CANCELLED, REJECTED, DELAYED, AWAITING_PARTS, DISPUTED.

## انتقالات مسموحة
NEW→TRIAGE.
TRIAGE→INSPECTION_REQUIRED أو QUOTE_PENDING أو APPROVAL_PENDING أو REJECTED.
INSPECTION_REQUIRED→QUOTE_PENDING أو DELAYED أو DISPUTED.
QUOTE_PENDING→APPROVAL_PENDING أو INSPECTION_REQUIRED أو CANCELLED.
APPROVAL_PENDING→SCHEDULED أو CANCELLED أو QUOTE_PENDING عند إصدار تعديل.
SCHEDULED→IN_PROGRESS أو DELAYED أو CANCELLED وفق السياسة.
IN_PROGRESS→AWAITING_PARTS أو AWAITING_ACCEPTANCE أو DELAYED أو DISPUTED.
AWAITING_PARTS→SCHEDULED أو IN_PROGRESS أو CANCELLED وفق السياسة.
AWAITING_ACCEPTANCE→COMPLETED أو IN_PROGRESS لإعادة العمل أو DISPUTED.
الحالات النهائية لا تفتح من جديد إلا بإجراء مخول ومسجل.

## قواعد عامة
- كل انتقال يسجل الفاعل والوقت والحالة السابقة والجديدة والسبب عند اللزوم.
- لا يبدأ العمل غير الطارئ قبل موافقة سعر صالحة.
- السعر المعتمد غير قابل للتعديل؛ ينشأ إصدار جديد.
- التغيير في النطاق أو السعر يتطلب موافقة جديدة.
- لا يُغلق الطلب دون تقرير الإنجاز ومتطلبات الفئة والاستلام أو تصعيد معتمد.
- إعادة الإسناد لا تمحو سجل المرشحين السابقين.
- لا تؤكد المخزون أو الدفع أو GPS دون مصدر موثوق.

## التوجيه
أهلية أولًا: تخصص، مؤهلات/تراخيص لازمة، تغطية جغرافية، توفر، وعدم وجود حظر. بعد ذلك ترتيب تجريبي: الجودة 30%، الوصول 25%، السعر 20%، الاستجابة 15%، الالتزام والضمان 10%. عاير الأوزان ببيانات حقيقية. السعر لا يعوض غياب التأهيل.

## الأسعار والموردون
عرض السعر يحفظ إصدارًا ووقت صلاحية وبنودًا مفصلة. عرض المورد القديم لا يظهر كتوفّر مؤكد. البدائل المؤثرة تحتاج موافقة. افصل إجمالي العميل عن إيراد المنصة ومستحقات المورد ومقدم الخدمة.

## الدفع
تحقق من webhooks وتوقيعها، امنع إعادة التشغيل، ولا تعتمد على حالة يرسلها المتصفح. استخدم idempotency للعمليات المناسبة ولا تخزن بيانات بطاقات حساسة.
