# دليل سريع للدوال الجديدة

## دوال الفلاتر والبحث

### `applyCompanyFilters()`
تطبيق جميع الفلاتر والبحث المفعلة حالياً. تُستدعى تلقائياً عند تغيير أي فلتر.

### `resetCompanyFilters()`
مسح جميع الفلاتر والبحث والعودة للعرض الكامل.

### `toggleAdvancedSearch()`
إظهار أو إخفاء نموذج البحث المتقدم.

### `switchCompanyView(view)`
تبديل بين طرق عرض الشركات ('all', 'unvisited', 'planned').

---

## دوال الإحصائيات

### `updateCompanyStats()`
تحديث لوحة الإحصائيات الرئيسية بالأرقام الحالية.

### `getCompanyVisitRate(companyName)`
حساب معدل الزيارات اليومي لشركة معينة (زيارات/يوم).

### `getCompanyPeakWeek(companyName)`
إيجاد الأسبوع الذي كانت فيه الشركة تحصل على أكثر الزيارات.

### `getCompanyVisitSpacing(companyName)`
حساب متوسط عدد الأيام بين الزيارات.

### `getContactsStatistics()`
الحصول على إحصائيات شاملة لجهات الاتصال.

### `getPerformanceMetrics()`
قياس أداء التطبيق (سرعة البحث والعرض).

### `getDataHealthReport()`
تقرير شامل عن صحة البيانات والمشاكل المحتملة.

---

## دوال التصدير

### `exportCompaniesData()`
تصدير البيانات الكاملة في صيغة JSON.

### `exportCompaniesDataWithStats()`
تصدير البيانات مع إحصائيات مفصلة لكل شركة.

### `exportCompaniesAsCSV()`
تصدير الشركات في صيغة CSV (Excel).

### `exportContactsAsVCF()`
تصدير جهات الاتصال في صيغة VCF (يمكن استيراده في الهاتف).

### `exportContactsAsCSV()`
تصدير جهات الاتصال في صيغة CSV.

---

## دوال الاستيراد والنسخ الاحتياطية

### `importDataWithValidation(event)`
استيراد نسخة احتياطية مع التحقق من الصحة والسلامة.

### `createAutoBackup()`
إنشاء نسخة احتياطية تلقائية (تُستدعى كل 30 دقيقة).

### `restoreAutoBackup()`
استعادة النسخة الاحتياطية التلقائية الأخيرة.

---

## دوال إدارة جهات الاتصال

### `searchContact(phoneOrName)`
البحث عن جهة اتصال برقم هاتف أو اسم.

### `addContactToMultipleCompanies(contactData, companyNames)`
إضافة نفس جهة الاتصال لعدة شركات دفعة واحدة.

### `deleteContactFromAllCompanies(contactName, contactPhone)`
حذف جهة اتصال من جميع الشركات.

### `findDuplicateContacts()`
البحث عن جهات الاتصال المكررة في النظام.

---

## دوال الصيانة والأداء

### `validateDataIntegrity()`
التحقق من سلامة البيانات والحقول المفقودة.

### `cleanupData()`
تنظيف البيانات من التكرارات والأخطاء.

### `clearSearchCache()`
مسح الكاش اليدوي.

### `clearOldCache()`
مسح الكاش القديم (تُستدعى تلقائياً).

### `logPerformanceMetrics()`
تسجيل مقاييس الأداء في وحدة التحكم.

---

## أمثلة الاستخدام

### البحث عن شركة معينة
```javascript
// البحث بالاسم
document.getElementById('comp-search').value = "شركة الأمل";
applyCompanyFilters();

// البحث برقم هاتف
document.getElementById('comp-search').value = "01000000000";
applyCompanyFilters();
```

### تصدير البيانات
```javascript
// تصدير JSON بسيط
exportCompaniesData();

// تصدير مع الإحصائيات
exportCompaniesDataWithStats();

// تصدير جهات الاتصال
exportContactsAsVCF();
exportContactsAsCSV();
```

### البحث عن التكرارات
```javascript
const duplicates = findDuplicateContacts();
console.log("جهات اتصال مكررة:", duplicates);
```

### التحقق من صحة البيانات
```javascript
const health = getDataHealthReport();
console.log("تقرير صحة البيانات:", health);
```

---

## اختصارات لوحة المفاتيح

- **Enter**: إضافة منتج في حقل المنتجات
- **Tab**: التنقل بين الحقول
- الضغط المطول على بطاقة الشركة = تعديل
- النقر على بطاقة الشركة = عرض التفاصيل

---

## الخطأ والحل السريع

### المشكلة: البحث بطيء
**الحل**: مسح الكاش والفلاتر
```javascript
clearSearchCache();
resetCompanyFilters();
```

### المشكلة: بيانات غير منسقة
**الحل**: تنظيف البيانات
```javascript
cleanupData();
refresh();
```

### المشكلة: شركة لا تظهر
**الحل**: التحقق من سلامة البيانات
```javascript
const validation = validateDataIntegrity();
console.log(validation);
```

---

**آخر تحديث**: 2026-05-10
