# دليل الميزات المتقدمة - StudioFlow v6

## 1. نظام المستخدمين والمصادقة

### الدوال الرئيسية:
- `checkLogin()` - التحقق من تسجيل الدخول عند بدء التطبيق
- `handleLogin()` - معالجة دخول المستخدم
- `handleLogout()` - تسجيل خروج المستخدم
- `toggleSignup()` - إنشاء حساب جديد

### البيانات المخزنة:
```javascript
{
  id: number,
  username: string,
  password: string,
  name: string
}
```

---

## 2. نظام الإشعارات

### الدالة الرئيسية:
```javascript
showNotification(message, type)
```

### أنواع الإشعارات:
- `success` - رسالة النجاح (أخضر)
- `error` - رسالة الخطأ (أحمر)
- `info` - رسالة معلومات (أزرق)

### مثال الاستخدام:
```javascript
showNotification('تم الحفظ بنجاح', 'success');
showNotification('حدث خطأ ما', 'error');
```

---

## 3. إدارة المستأجرين

### الدالة الرئيسية:
```javascript
showTenantForm()
```

### بنية بيانات المستأجر:
```javascript
{
  tenantId: number,
  name: string,
  phone: string,
  email: string,
  id: string,        // رقم الهوية/الجواز
  dateAdded: string
}
```

### العمليات:
- إضافة مستأجر جديد: `showTenantForm()`
- حذف مستأجر: `deleteTenant(tenantId)`
- عرض المستأجرين: تبويب "المستأجرين" في لوحة الوحدة

---

## 4. نظام الفواتير

### الدوال الرئيسية:
- `createInvoice()` - إنشاء فاتورة جديدة
- `markInvoicePaid(invoiceId)` - تأكيد دفع الفاتورة

### بنية البيانات:
```javascript
{
  id: number,
  bookingId: number,      // الحجز المرتبط
  amount: number,
  date: string,           // تاريخ الإنشاء
  status: string,         // "معلق" أو "مدفوع"
  paidDate: string,       // تاريخ الدفع (إن وجد)
  guestName: string
}
```

### حالات الفاتورة:
- **معلق** (Pending) - بلون أصفر
- **مدفوع** (Paid) - بلون أخضر

---

## 5. التقارير والإحصائيات

### الدالة الرئيسية:
```javascript
showReports()
```

### المقاييس المعروضة:
1. **إجمالي الإيرادات** - مجموع جميع الحجوزات
2. **إجمالي المصروفات** - مجموع جميع المصروفات
3. **الفواتير المدفوعة** - المبلغ الذي تم استلامه
4. **الفواتير المعلقة** - المبلغ المتبقي
5. **صافي الربح** - الإيرادات - المصروفات

### مثال الحساب:
```
إجمالي الإيرادات: 10,000 ج.م
إجمالي المصروفات: 2,000 ج.م
صافي الربح: 8,000 ج.م
```

---

## 6. تبويبات الوحدة

### التبويبات الأربعة:
1. **سجل الحجوزات** - قائمة بجميع الحجوزات
2. **المستأجرين** - بيانات المستأجرين المسجلين
3. **الفواتير** - الفواتير والدفعات
4. **المصروفات** - تسجيل المصروفات

### التنقل بين التبويبات:
```javascript
switchTab(tab)
```

---

## 7. حفظ البيانات

### النقاط المهمة:
- جميع البيانات تحفظ في `localStorage`
- مفاتيح التخزين:
  - `studioflow_v5` - الوحدات والحجوزات والمصروفات
  - `studioflow_users` - بيانات المستخدمين
  - `studioflow_current_user` - المستخدم الحالي

### دالة الحفظ:
```javascript
function save() { 
  localStorage.setItem('studioflow_v5', JSON.stringify(items)); 
}
```

---

## 8. هيكل البيانات الكامل

### الوحدة (Unit):
```javascript
{
  id: number,
  name: string,
  color: string,          // gradient CSS
  bookings: [             // الحجوزات
    {
      id: number,
      guest: string,
      amount: number,
      date: string,
      endDate: string
    }
  ],
  expenses: [             // المصروفات
    {
      id: number,
      title: string,
      amount: number,
      date: string
    }
  ],
  tenants: [              // المستأجرون
    {
      tenantId: number,
      name: string,
      phone: string,
      email: string,
      id: string,
      dateAdded: string
    }
  ],
  invoices: [             // الفواتير
    {
      id: number,
      bookingId: number,
      amount: number,
      date: string,
      status: string,
      paidDate: string,
      guestName: string
    }
  ]
}
```

---

## 9. الألوان والتصميم

### نظام الألوان:
- **الأزرق (Indigo)** - اللون الأساسي: `#6366f1`
- **الرمادي** - الخلفية والنصوص
- **الأحمر** - الحذف والتحذيرات
- **الأخضر** - النجاح والمدفوع
- **البرتقالي** - المعلق/الانتظار

### تدرجات الوحدات:
يتم اختيارها عشوائياً من:
1. `#4f46e5 → #7c3aed` (أزرق-بنفسجي)
2. `#1e293b → #334155` (رمادي)
3. `#059669 → #2563eb` (أخضر-أزرق)
4. `#db2777 → #4f46e5` (وردي-أزرق)

---

## 10. تعليقات إضافية

### الميزات المستقبلية الممكنة:
- [ ] تصدير التقارير إلى PDF
- [ ] نسخ احتياطية سحابية
- [ ] إرسال إشعارات بالبريد الإلكتروني
- [ ] تطبيق موبايل
- [ ] دعم العملات المختلفة
- [ ] نظام الأذونات والأدوار

### معايير الأداء:
- الحد الأقصى للوحدات: غير محدود
- الحد الأقصى للحجوزات: غير محدود
- حجم التخزين: يعتمد على متصفح المستخدم (عادة 5-10 MB)

---

**تم التطوير بعناية لضمان أفضل تجربة مستخدم**
