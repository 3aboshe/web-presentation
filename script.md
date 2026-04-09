# Presentation Script — Web Fundamentals for CTF
# سكريبت المحاضرة — أساسيات الويب للـ CTF

---

## Slide 1 — Title / العنوان

**EN:**
Hey everyone — welcome. Today we're going to cover the fundamentals of how the web works. Not from a user perspective, but from a hacker's perspective. By the end of this, you'll understand exactly what's happening every time a browser loads a page — and more importantly, where things can go wrong.

**AR:**
أهلاً وسهلاً بالجميع. اليوم رح نتكلم عن أساسيات الويب — مش كمستخدمين، كـ hackers. بنهاية هالسيشن، رح تفهموا بالضبط شو يصير كل ما المتصفح يفتح صفحة، وأهم من هيك — وين الأمور ممكن تنكسر.

---

## Slide 2 — Client and Server / الكلايِنت والسيرفر

**EN:**
So first question — when you type google.com into your browser, what actually happens? Most people think the website is "somewhere on the internet." But it's more specific than that. Every website lives on a server — a computer that's always on, always connected, always waiting. And your browser? That's the client. It connects to that server and says: "give me your homepage." The server finds it and sends it back.

**AR:**
أول سؤال — لما بتكتب google.com بالمتصفح، شو بيصير فعلياً؟ معظم الناس بتقول "الموقع موجود على الإنترنت." بس الموضوع أدق من هيك. كل موقع عايش على سيرفر — كمبيوتر شغال على طول، متصل على الإنترنت، ومستني طلبات. ومتصفحك؟ هو الـ client. بيتصل على السيرفر وبيقوله: "عطيني الهوم بيج." السيرفر بيلاقيها وبيبعثها.

---

## Slide 3 — What the Server Holds / شو عند السيرفر

**EN:**
Now, everything on a server that you can request is called a resource. Think of it like a file system. Every resource has a path — `/index.html`, `/login`, `/api/users`. This is important. In CTF challenges, a huge amount of finding flags comes down to knowing what paths exist on a server. Sometimes there are resources the developer forgot about — files that aren't linked anywhere, but they're still there if you know what to ask for. Like `/flag.txt`.

**AR:**
كل شي على السيرفر ممكن تطلبه بنسميه resource. فكروا فيه متل نظام الملفات. كل resource عنده path — `/index.html`، `/login`، `/api/users`. هاد مهم. بكتير من تحديات الـ CTF، الفلاق بتلاقيه لما تعرف شو الـ paths الموجودة على السيرفر. أحياناً في resources المطور نسيها — ملفات مش مربوطة بأي مكان، بس موجودة إذا حدا عرف يطلبها. متل `/flag.txt`.

---

## Slide 4 — How They Talk / كيف بيتكلموا

**EN:**
OK so the client wants to talk to the server. But here's a problem — your laptop might run Windows, the server is running Linux. They're completely different systems. How do they understand each other? They agree on a shared set of rules. That agreement is called a protocol. And the protocol of the web is HTTP — HyperText Transfer Protocol. It defines exactly how a request should look and exactly how a response should look. So it doesn't matter what OS or language either side uses — as long as both speak HTTP, they understand each other.

**AR:**
تمام، الـ client بده يتكلم مع السيرفر. بس في مشكلة — لابتوبك ممكن يشتغل على Windows، والسيرفر شغال على Linux. أنظمة مختلفة بالكامل. كيف بيفهموا بعض؟ بيتفقوا على مجموعة قواعد مشتركة. هاد الاتفاق اسمه protocol. وبروتوكول الويب هو HTTP — HyperText Transfer Protocol. بيحدد بالضبط كيف يكون شكل الـ request وكيف يكون شكل الـ response. فمهما كان الـ OS أو اللغة — طالما الطرفين بيحكوا HTTP، بيفهموا بعض.

---

## Slide 5 — Request and Response / الطلب والرد

**EN:**
Every single thing that happens on the web is a request followed by a response. The request is what the client sends — it has a method, a path, headers, and sometimes a body. The response is what the server sends back — a status code, headers, and the actual content. Look at the image — this is what they actually look like. In CTF, everything you do — logging in, accessing pages, calling APIs — you're crafting requests and reading responses.

**AR:**
كل شي بيصير على الويب هو request وبعده response. الـ request هو اللي الـ client بيبعثه — فيه method وpath وheaders وأحياناً body. الـ response هو اللي السيرفر بيرد فيه — status code وheaders والمحتوى الفعلي. شوفوا الصورة — هاد شكلهم الحقيقي. بالـ CTF، كل شي بتعمله — تسجيل دخول، وصول لصفحات، استدعاء APIs — أنت عم تصنع requests وتقرأ responses.

---

## Slide 6 — Request-Response Cycle (Animation) / دورة الطلب والرد

**EN:**
Let me show you this as an animation. Watch — the client sends a request. The server receives it, processes it, and sends a response back. Then the browser renders whatever came in the body. This is it. This is the entire web. Every website, every API, every login form — it all comes down to this one cycle, over and over.

**AR:**
خليني أريكم هاد على شكل animation. شوفوا — الـ client بيبعث request. السيرفر بيستقبله، بيشتغل عليه، وبيرجع response. بعدين المتصفح بيرسم اللي وصل بالـ body. هاد هو كل شي. هاد هو الويب بأكمله. كل موقع، كل API، كل فورم دخول — كلهم بيرجعوا لهاد الـ cycle الواحد، مرة ومرة ومرة.

---

## Slide 7 — Recap: Web Basics / ملخص

**EN:**
Quick recap before we go deeper. Client and server — one asks, one answers. Resources — everything on the server has a path. HTTP — the protocol that makes communication possible. And every message has the same structure: a method, a path, a status code, a body. Keep these in your head. Everything we do from here is built on top of this.

**AR:**
ملخص سريع قبل ما نكمل. الـ client والسيرفر — واحد بيسأل والثاني بيجاوب. الـ resources — كل شي على السيرفر عنده path. الـ HTTP — البروتوكول اللي بيخلي التواصل ممكن. وكل رسالة عندها نفس الشكل: method وpath وstatus code وbody. خلوا هاد في بالكم. كل شي رح نعمله من هون هو مبني فوق هاد.

---

## Slide 8 — HTTP Status Codes Overview / نظرة عامة على Status Codes

**EN:**
Now let's talk about status codes. Every response comes with a three-digit number that tells you what happened. They're grouped into ranges. 2xx means success. 3xx means redirect — go somewhere else. 4xx means the client made a mistake. 5xx means the server broke. You need to know these by heart. In CTF, the status code alone often tells you whether you're on the right track.

**AR:**
هلق خلينا نحكي عن الـ status codes. كل response بيجي مع رقم من ثلاث خانات بيقلك شو صار. مرتبين بمجموعات. 2xx يعني نجاح. 3xx يعني redirect — روح لمكان ثاني. 4xx يعني الـ client غلط. 5xx يعني السيرفر انكسر. لازم تحفظوا هاد. بالـ CTF، الـ status code لحاله كتير بيقلك إذا كنت على الطريق الصح.

---

## Slide 9 — Common Status Codes / أهم Status Codes

**EN:**
Here are the ones you'll actually see. 200 — worked fine. 201 — something was created. 301 and 302 — redirects, permanent and temporary. 403 — you're not allowed, but the resource exists. 404 — doesn't exist at all. 500 — server crashed. Pay special attention to 403. In CTF, a 403 means the thing is there — you just don't have permission yet. That's valuable information.

**AR:**
هاد هو اللي رح تشوفوه فعلياً. 200 — اشتغل. 201 — شي انخلق. 301 و302 — redirects، واحد دائم وواحد مؤقت. 403 — مش مسموح لك، بس الـ resource موجود. 404 — مش موجود أصلاً. 500 — السيرفر وقع. ركزوا على الـ 403. بالـ CTF، الـ 403 يعني الشي موجود — بس ما عندك إذن بعد. هاد معلومة ثمينة.

---

## Slide 10 — HTTP Methods Overview / نظرة عامة على الـ Methods

**EN:**
Every request has a method — a verb that tells the server what you want to do. GET means retrieve something. POST means send something. PUT means replace something entirely. PATCH means update part of it. DELETE means remove it. OPTIONS asks what methods are even allowed. In web CTF, GET and POST are the ones you'll use most. But knowing the others matters — especially OPTIONS, which can sometimes reveal what a server is hiding.

**AR:**
كل request عنده method — فعل بيقلك شو بدك تعمل. GET يعني جيب شي. POST يعني ارسل شي. PUT يعني استبدل شي بالكامل. PATCH يعني حدّث جزء منه. DELETE يعني احذفه. OPTIONS بيسأل شو الـ methods المسموح فيها أصلاً. بالـ CTF، الـ GET والـ POST هم اللي رح تستخدموهم أكتر. بس معرفة الباقيين مهمة — خصوصاً الـ OPTIONS، اللي ممكن أحياناً يكشف شو السيرفر عم يخبي.

---

## Slide 11 — GET / الـ GET

**EN:**
GET is the simplest method. It says: give me this resource. Every time you open a website, your browser is sending a GET request. The key thing about GET — the data is in the URL. Right there in the address bar, in your browser history, in the server logs. Which means: never put anything sensitive in a GET request. If you see a login system passing passwords in the URL, that's already a vulnerability.

**AR:**
الـ GET هو أبسط method. بيقول: عطيني هالـ resource. كل مرة بتفتح موقع، متصفحك عم يبعث GET request. الشي المهم عن الـ GET — البيانات في الـ URL. مباشرة بشريط العنوان، بتاريخ المتصفح، بـ logs السيرفر. يعني: لا تحط أي شي حساس بـ GET request. إذا شفتوا نظام تسجيل دخول بيمرر كلمات المرور بالـ URL، هاد أصلاً vulnerability.

---

## Slide 12 — POST / الـ POST

**EN:**
POST is for sending data. The difference from GET is where the data lives — in POST, it's in the request body, not the URL. So it's not visible in the address bar. But — and this is critical — that doesn't mean it's secure. Without HTTPS, anyone on the same network can still read the body. The body is not encrypted by default. HTTPS is what encrypts it. And in CTF, you're often looking at HTTP, not HTTPS.

**AR:**
الـ POST هو لإرسال البيانات. الفرق عن الـ GET هو وين البيانات — بالـ POST هي بالـ body مش بالـ URL. يعني مش ظاهرة بشريط العنوان. بس — وهاد مهم جداً — هاد مش معناه أنها آمنة. بدون HTTPS، أي واحد على نفس الشبكة ممكن يقرأ الـ body. الـ body مش مشفر بشكل افتراضي. الـ HTTPS هو اللي بيشفره. وبالـ CTF، كتير بتشتغلوا على HTTP مش HTTPS.

---

## Slide 13 — GET vs POST / مقارنة

**EN:**
Side by side. GET — data in the URL, bookmarkable, cached by the browser, limited size. POST — data in the body, not in the URL, not cached, no size limit. The practical rule: GET is for fetching things, POST is for submitting things. Mixing them up — like a server that accepts sensitive data via GET — is a classic vulnerability you'll find in CTF challenges.

**AR:**
جنب بجنب. GET — البيانات بالـ URL، ممكن تعمله bookmark، المتصفح بيحفظه، محدود بالحجم. POST — البيانات بالـ body، مش بالـ URL، مش محفوظ، مافي حد للحجم. القاعدة العملية: GET لجلب الأشياء، POST لإرسال الأشياء. الخلط بينهم — متل سيرفر بيقبل بيانات حساسة عبر GET — هي vulnerability كلاسيكية رح تلاقوها بتحديات الـ CTF.

---

## Slide 14 — HTTP Request Anatomy / تشريح الـ Request

**EN:**
Now you know what methods and status codes are — let's see what an actual HTTP request looks like. The first line has three things: the method, the path, and the HTTP version. Then come the headers — key-value pairs that carry metadata. Host tells the server which domain you're talking to. User-Agent tells it what browser you're using. Accept tells it what format you want back. After all the headers, there's a blank line, and then the body if there is one.

**AR:**
هلق بتعرفوا شو هو الـ method والـ status code — خليني نشوف كيف يبدو الـ HTTP request فعلياً. السطر الأول فيه ثلاث أشياء: الـ method، الـ path، وإصدار الـ HTTP. بعدين بيجو الـ headers — أزواج مفتاح-قيمة بتحمل معلومات إضافية. الـ Host بيقلك شو الـ domain. الـ User-Agent بيقلك شو المتصفح. الـ Accept بيقلك شو الصيغة اللي بدك ترجعها. بعد كل الـ headers في سطر فاضي، وبعدين الـ body إذا كان موجود.

---

## Slide 15 — HTTP Response Anatomy / تشريح الـ Response

**EN:**
And the response follows the same pattern. First line — HTTP version and the status code. Then headers. Content-Type tells you what's in the body. Set-Cookie is how the server assigns you a session — this is massive for CTF. Then the blank line, then the body — the actual HTML, JSON, whatever. Everything you see in your browser was inside a response body.

**AR:**
والـ response بنفس النمط. السطر الأول — إصدار HTTP والـ status code. بعدين headers. الـ Content-Type بيقلك شو بالـ body. الـ Set-Cookie هو كيف السيرفر بيعطيك session — وهاد ضخم بالـ CTF. بعدين السطر الفاضي، بعدين الـ body — الـ HTML أو الـ JSON أو شو كان. كل شي بتشوفه بمتصفحك كان جوا response body.

---

## Slide 16 — URL Anatomy / تشريح الـ URL

**EN:**
One more thing before the recap — the URL itself. It has parts. The protocol — HTTPS or HTTP — tells you how to connect. The domain — the address of the server. The path — which resource you want. Then the query parameters — extra data passed as key-value pairs in the URL, everything after the question mark. And the fragment — the part after the hash, which is handled by the browser, not the server. In CTF, query parameters are one of the first places you look for injection points.

**AR:**
شي واحد قبل الملخص — الـ URL نفسه. عنده أجزاء. الـ protocol — HTTPS أو HTTP — بيقلك كيف تتصل. الـ domain — عنوان السيرفر. الـ path — شو الـ resource اللي بدك. بعدين الـ query parameters — بيانات إضافية بتتمرر كـ key-value بالـ URL، كل شي بعد علامة الاستفهام. والـ fragment — الجزء بعد الـ hash، بيتعامل معه المتصفح مش السيرفر. بالـ CTF، الـ query parameters هي من أول الأماكن اللي بتفتشوا فيها عن injection points.

---

## Slide 17 — HTTP Recap / ملخص HTTP

**EN:**
That's HTTP. Status codes — 2xx good, 3xx redirect, 4xx your fault, 5xx their fault. Methods — GET reads, POST sends. Request and response both have a first line, headers, and a body. This is the language of the web. Everything in web security — SQL injection, XSS, authentication bypass, IDOR — happens inside HTTP messages. When you understand the message format, you understand where to attack.

**AR:**
هاد هو HTTP. الـ Status codes — 2xx تمام، 3xx redirect، 4xx غلطتك، 5xx غلطتهم. الـ Methods — GET بيقرأ، POST بيرسل. الـ Request والـ response كلهم عندهم سطر أول وheaders وbody. هاد هو لغة الويب. كل شي بأمن الويب — SQL injection، XSS، تجاوز الـ authentication، IDOR — بيصير جوا رسائل HTTP. لما تفهم شكل الرسالة، بتفهم وين تهاجم.

---

## Slide 18 — HTML / الـ HTML

**EN:**
So what does a server actually send back in the body? Usually HTML. HTML is the structure of a webpage. This is what it looks like with no styling — just raw HTML rendered by the browser with its default styles. Ugly, but it works. Every element you see on a page — a heading, a paragraph, a form, a button — is an HTML tag. And in CTF, you'll read HTML source constantly. Hidden fields, comments in the code, links that aren't visible — all of it is in the HTML.

**AR:**
شو السيرفر فعلياً بيبعث بالـ body؟ عادةً HTML. الـ HTML هو هيكل صفحة الويب. هاد شكله بدون أي تنسيق — مجرد HTML خام المتصفح عم يرسمه بأسلوبه الافتراضي. مش حلو، بس بيشتغل. كل عنصر بتشوفه على الصفحة — عنوان، فقرة، فورم، زر — هو HTML tag. وبالـ CTF، رح تقرأوا الـ HTML source على طول. حقول مخفية، تعليقات بالكود، روابط مش ظاهرة — كلها موجودة بالـ HTML.

---

## Slide 19 — CSS / الـ CSS

**EN:**
Same page, but now with CSS. CSS is what controls how things look — colors, spacing, fonts, layout. Notice the difference: same structure, completely different appearance. For CTF purposes, CSS is less critical than HTML — but it's important to understand that it's a separate layer. Sometimes developers leave sensitive information in CSS files, or use CSS to hide elements they think users can't see.

**AR:**
نفس الصفحة، بس هلق مع CSS. الـ CSS هو اللي بيتحكم بشكل الأشياء — الألوان، المسافات، الخطوط، التخطيط. لاحظوا الفرق: نفس الهيكل، شكل مختلف بالكامل. لأغراض الـ CTF، الـ CSS أقل أهمية من الـ HTML — بس مهم تفهموا أنه طبقة منفصلة. أحياناً المطورين بيتركوا معلومات حساسة بملفات الـ CSS، أو بيستخدموا الـ CSS يخبوا عناصر يظنوا المستخدمين ما يشوفوها.

---

## Slide 20 — JavaScript / الـ JavaScript

**EN:**
And now JavaScript. This is what makes the page actually do something. Try it — type anything and click Log In. JavaScript is handling that click, reading your input, making a decision, and showing a response. Without JavaScript, that button does nothing at all. For CTF, JavaScript is gold. The source code runs in your browser — you can read it, modify it, and bypass client-side checks. If a website is doing validation in JavaScript, that validation can be disabled. If tokens or API endpoints are in the JavaScript, you can find them.

**AR:**
وهلق الـ JavaScript. هاد اللي بيخلي الصفحة تعمل شي فعلياً. جربوا — اكتبوا أي شي واضغطوا Log In. الـ JavaScript عم يتعامل مع الضغطة، عم يقرأ الـ input، عم يقرر، وعم يعرض رد. بدون الـ JavaScript، الزر ما بيعمل شي خالص. للـ CTF، الـ JavaScript هو ذهب. الكود بيشتغل بمتصفحك — ممكن تقرأه، تعدله، وتتجاوز الـ checks اللي على مستوى الـ client. إذا الموقع عم يعمل validation بالـ JavaScript، هالـ validation ممكن تعطله. إذا في tokens أو API endpoints بالـ JavaScript، ممكن تلاقيهم.

---

## Slide 21 — DevTools / أدوات المطور

**EN:**
Which brings us to your first real tool — browser DevTools. F12. Open it right now on any website and you can see everything. The Elements tab shows you the full HTML of the page, live. The Console lets you run JavaScript directly. The Network tab — this is the one you'll live in during CTF — shows every single HTTP request and response. You can see the method, the URL, the status code, the headers, the body. The Application tab shows cookies and local storage. This is all you need to start.

**AR:**
وهاد بيجيبنا على أول أداة حقيقية — الـ DevTools بالمتصفح. F12. افتحوها هلق على أي موقع وبتشوفوا كل شي. تاب الـ Elements بيريكم كامل الـ HTML للصفحة، مباشرة. الـ Console بيخليكم تشغلوا JavaScript مباشرة. تاب الـ Network — هاد اللي رح تعيشوا فيه بالـ CTF — بيعرض كل request وresponse HTTP. بتشوفوا الـ method، الـ URL، الـ status code، الـ headers، الـ body. تاب الـ Application بيعرض الـ cookies والـ local storage. هاد كل اللي تحتاجوه تبدأوا.

---

## Slide 22 — Final Recap / الملخص النهائي

**EN:**
Let's close with the full picture. Client and server — request and response. Resources have paths. HTTP is the protocol. Status codes tell you what happened. Methods tell the server what to do. HTML is structure, CSS is style, JavaScript is behavior. And DevTools lets you see all of it. This is the foundation. Everything in web CTF — every injection, every bypass, every token leak — happens on top of what you just learned.

**AR:**
خليني نختم بالصورة الكاملة. الـ Client والـ server — request وresponse. الـ Resources عندها paths. الـ HTTP هو البروتوكول. الـ Status codes بتقلك شو صار. الـ Methods بتقلك شو تعمل. HTML هو الهيكل، CSS هو الشكل، JavaScript هو التصرف. والـ DevTools بيخليك تشوف كل شي. هاد هو الأساس. كل شي بالـ CTF — كل injection، كل bypass، كل token leak — بيصير فوق اللي تعلمتوه هلق.

---

## Slide 23 — End / الختام

**EN:**
That's it for today. If you take one thing from this — open DevTools on the next website you visit. Look at the Network tab. You'll see everything we talked about in action. Read the requests, read the responses, try to understand what the site is doing. That habit alone will get you far. Good luck.

**AR:**
هاد كل شي لليوم. إذا بتاخذوا شي واحد من هالمحاضرة — افتحوا الـ DevTools على أول موقع بتزوروه. شوفوا تاب الـ Network. رح تشوفوا كل شي حكيناه عنه وهو يشتغل. اقرأوا الـ requests، اقرأوا الـ responses، حاولوا تفهموا شو الموقع عم يعمل. هالعادة لحالها رح توصلكم بعيد. حظ موفق.
