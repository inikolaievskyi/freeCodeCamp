---
title: CSS Syntax and Selectors
localeTitle: CSS المختار والقواعد
---
## CSS المختار والقواعد

عندما نتحدث عن صيغة CSS ، نتحدث عن كيفية وضع الأشياء. توجد قواعد حول أين تذهب ، حيث يمكنك كتابة CSS باستمرار ويمكن أن يفسرها أحد البرامج (مثل المتصفح) ويطبقها على الصفحة بشكل صحيح.

هناك طريقتان رئيسيتان لكتابة CSS.

### مضمنة المغلق

تفاصيل محددة على خصوصية [CSS](https://css-tricks.com/specifics-on-css-specificity/) : [CSS الخدع](https://css-tricks.com/specifics-on-css-specificity/)

تطبق CSS مضمنة التصميم على عنصر واحد وأطفاله ، حتى يتم اكتشاف نمط آخر يتجاوز الأول.

لتطبيق CSS المضمّن ، أضف سمة "النمط" إلى عنصر HTML ترغب في تعديله. داخل علامات اقتباس ، قم بتضمين قائمة مفصولة بفواصل منقوطة من أزواج المفاتيح / القيم (كل منها مفصولة بنقطتين) تشير إلى أنماط لتعيينها.

إليك مثال على CSS المضمّن. سيكون للكلمات "One" و "Two" لون خلفية باللون الأصفر ولون النص باللون الأحمر. تحتوي كلمة "ثلاثة" على نمط جديد يتجاوز الأول ، وسيكون له لون خلفية باللون الأخضر ونص اللون السماوي. في المثال ، نحن نطبق الأنماط على علامات `<div>` ، ولكن يمكنك تطبيق نمط على أي عنصر HTML.

```html
<div style="color:red; background:yellow">
  One
  <div>
    Two
  </div>
  <div style="color:cyan; background:green">
    Three
  </div>
</div>
``` 

### CSS داخلي

بينما تعد كتابة نمط مضمَّن طريقة سريعة لتغيير عنصر واحد ، فهناك طريقة أكثر فاعلية لتطبيق نفس النمط على العديد من عناصر الصفحة في وقت واحد.

تحتوي CSS الداخلية على الأنماط المحددة في علامة `<style>` ، وهي مدمجة في العلامة `<head>` .

في ما يلي مثال له تأثير مماثل لمثال "مضمنة" أعلاه ، باستثناء أنه تم استخراج CSS إلى منطقته الخاصة. ستتطابق الكلمتان "One" و "Two" مع محدد `div` ويكون النص الأحمر على خلفية صفراء. تتطابق الكلمتان "Three" و "Four" مع محدد `div` أيضًا ، ولكنهما يتطابقان أيضًا مع محدد `.nested_div` الذي ينطبق على أي عنصر HTML يشير إلى هذه الفئة. يتجاوز هذا المحدد المحدد الأول ، وينتهي ظهرا في الظهور كنص أزرق سماوي على خلفية خضراء.

```html
<style type="text/css">
  div { color: red; background: yellow; }
  .nested_div { color: cyan; background: green; }
</style>

<div>
  One
  <div>
    Two
  </div>
  <div class="nested_div">
    Three
  </div>
  <div class="nested_div">
    Four
  </div>
</div>
``` 

تعتبر المحددات المبينة أعلاه بسيطة للغاية ، ولكنها قد تكون معقدة للغاية. على سبيل المثال ، من الممكن تطبيق الأنماط فقط على العناصر المتداخلة ؛ وهذا هو ، العنصر الذي هو طفل لعنصر آخر.

في ما يلي مثال على تحديدنا للنمط الذي يجب تطبيقه فقط على عناصر `div` التي تمثل طفلًا مباشرًا لعناصر `div` الأخرى. والنتيجة هي أن "Two" و "Three" سيظهران كنص أحمر على خلفية صفراء ، لكن "One" و "Four" سيظلان غير متأثران (وعلى الأرجح نص أسود على خلفية بيضاء).

```html
<style type="text/css">
  div > div { color: red; background: yellow; }
</style>

<div>
  One
  <div>
    Two
  </div>
  <div>
    Three
  </div>
</div>
<div>
  Four
</div>
``` 

### CSS خارجي

يحتوي كل التصميم على مستند خاص به مرتبط في العلامة `<head>` . امتداد الملف المرتبط هو `.css`

#### معلومات اكثر:

*   [CSS Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax) @ MDN
*   [CSS Selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) @ MDN
*   [CSS المختارات المرجعية](https://www.w3schools.com/cssref/css_selectors.asp)
*   [خصوصية مختارات CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)