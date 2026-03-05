# Automated-Hybrid-Zero-Trust-Media-Networking-Lab
<div dir="rtl">
مبدئيا بتكلم ليش سويت سيرفر هذا بذات بسبب سبب بسيطة جداً الي هو فكرة الأشتراكات بشكل عام وفي كل شيء انا أكره شيء اسم اشتراك سواء في منصات تخزين زي Google Drive او أي منصة تطلب الأشتراك أي ما كانت بلا استثناء

 # اسم المشروع الأساسي:

Automated (مؤتمت): لأن الخدمات فيه تعمل تلقائيًا بمجرد تشغيل الجهاز دون تدخل بشري مني فقط اوصلها بالكهرب ويشتغل كل شيء حتى إذا انطفى الكهرب بمجرد انه رجع راح يشتغل كل شيء فيه
<br>
<br>
Hybrid (هجين): لأنه يجمع بين الوصول المحلي (Local) داخل البيت والوصول عن بُعد (Remote) بسلاسة
<br>
<br>
Zero-Trust (انعدام الثقة): قاعدة هي: "لا تثق بأحد أبداً، وتحقق من كل شيء دائماً" حيث لا يتم الوثوق بأي اتصال إلا بعد التحقق من الهوية، والمشروع مافي بورتات مفتوحة برا كل شيء محدد مسبقا.
<br>
<br>
Media & Networking (الميديا والشبكات): الميديا هي هنا هو سيرفر لتخزين ومشاهدة الميديا بكل أنواعها وأشكالها, الشبكات هو مراقبة الشبكة وأي شيء يحدث فيها وأيضا تعلم الشبكات وكيف تشتغل وأي شيء يخصها.
<br>
<br>
Lab (مختبر): المشروع أصبح بيئة للتجارب والتعلم المستمر
# أهدافي الأساسية من السيرفر هي: 
1-ابي شيء خاص فيني عندي كل الصلاحيات والتحكم يعني ابي يكون لي بشكل كامل بنسبة 100%
<br>
<br>
2-أني اتعلم الشبكات و docker و Self-hosted وإدارة السيرفرات
<br>
<br>
3-اني أخزن أشياء بدون لاأشترك في ولا أي منصة تقدم أشتراكات
<br>
<br>
4-اني استفيد منه بحياتي من كل النواحي ترفيهيًا وعلمياً
<br>
<br>
5-اخزن فيه بيانات ومقاطع فيديو اشوفها بأي مكان في العالم سواء كان محلي او خارجي
<br>
<br>
6-استضيف عليه موقعي الخاص [رابطه](http://heronyaa.dev/) ويكون عندي التحكم الكامل له
<br>
<br>

# الأدوات
1-الهاردوير هو raspberry pi 5 4GB
<br>
2-نظام لينكس تحديداً ديبيان
<br>
3-[Docker](https://github.com/docker)
<br>
4-[Cloudflare](https://www.cloudflare.com/)
<br>
5-[Tailscale](https://tailscale.com/)



# نظرة عامة على الخدمات (media-system)

| الحاوية | الوظيفة  |
| :--- | :--- |
| <br> **[Jellyfin](https://github.com/linuxserver/docker-jellyfin)** <br><br> | نظام لبث الوسائط (Media Server) مفتوح المصدر بالكامل، يوفر تجربة مشاهدة سينمائية بدون قيود
| <br> **[Jellyseerr](https://github.com/seerr-team/seerr)** <br><br> | واجهة أمامية (Frontend) لإدارة طلبات المحتوى، تسهل على المستخدمين العثور على ما يريدون
| <br> **[Prowlarr](https://github.com/linuxserver/docker-prowlarr)** <br><br> | محرك البحث المركزي لإدارة الـ Indexers ومواقع التورنت وتوفير الروابط للحاويات الأخرى
| <br> **[Transmission](https://github.com/linuxserver/docker-transmission)** <br><br> | عميل تورنت (BitTorrent Client) خفيف جداً وموثوق، مخصص للأجهزة ذات الموارد المحدودة
| <br> **[Sonarr](https://github.com/linuxserver/docker-sonarr)** <br><br> | الأداة المسؤولة عن أتمتة وتنظيم المسلسلات التلفزيونية (TV Shows) وجدولة الحلقات الجديدة


# Media-System The Media Stack OSI Model
![Media-System The Media Stack OSI Model](Media-System%20The%20Media%20Stack%20OSI%20Model.png)

| الطبقة (OSI Layer) | الحاوية/المكون (Container) | الدور الوظيفي (Functional Role) | المنطق البرمجي والشبكي (Logic Flow) |
| :--- | :--- | :--- | ---: |
| **L7 - Application** | `Jellyseerr` | User Interface & Request | نقطة انطلاق "الطلب" (**HTTP Request**). يستقبل بحث المستخدم ويرسله عبر **API** |
| **L6 - Presentation** | `Jellyfin` | Media Visualization | تحويل الملفات الخام إلى مكتبة بصرية، وإدارة الـ **Transcoding** لضمان العرض |
| **L5 - Session** | `Sonarr` & `Prowlarr` | Automation Orchestration | إدارة "حوار" البحث والتنسيق. يفتح جلسة عمل لترجمة الطلبات ومراقبة حالة المحتوى |
| **L4 - Transport** | `Transmission` | Data Download Engine | تنفيذ عملية نقل البيانات الفعلية باستخدام بروتوكولات الـ **P2P** وضمان وصول الملفات |
| **L3 - Network** | `Zero-Trust Tunnel` | Secure Routing | التوجيه الآمن والتحقق من الهوية قبل السماح بالوصول (من **Local** إلى **Remote**) |
| **L2 - Data Link** | `Docker Volumes` | Logical Storage Mapping | ربط الحاويات بالمجلدات الفعلية على الهاردسك وإدارة صلاحيات الملفات (**Permissions**) |
| **L1 - Physical** | `Raspberry PI 5` | Hardware Resources | العتاد الصلب (**Raspberry Pi 5**) الذي يوفر القوة الحوسبية لتشغيل النظام |

---

# المراقبة (Monitoring-stack)
| الأداة (Tool) | الوظيفة (Role) | الوصف التشغيلي (Operational Description) |
| :--- | :--- | ---: |
| <br> **[Homarr](https://homarr.dev/)** <br><br> | البوابة التشغيلية (Operational Dashboard) | يعمل كواجهة مركزية للسيرفر؛ يجمع لك كل خدماتك في واجهة بصرية واحدة سهلة الوصول |
| <br> **[Pi-hole](https://pi-hole.net/)** <br><br> | حارس جودة الشبكة (Network Health) | يعمل كـ "مصفاة" ذكية للشبكة، حيث يقوم بحجب الإعلانات وتتبع البيانات قبل وصولها لأجهزتك |
| <br> **[Dashdot](https://getdashdot.com/)** <br><br> | مراقب العلامات الحيوية (Resource Monitor) | يوفر قراءة "لحظية" وشاملة لصحة العتاد (CPU, RAM, Storage, Network) بتصميم عصري |
| <br> **[Dockge](https://dockge.kuma.pet/)** <br><br> | مدير الحاويات (Docker Stack Manager) | واجهة رسومية تفاعلية لإدارة ملفات docker-compose.yml؛ تسمح لك بإنشاء، تعديل، وتشغيل الحاويات بسهولة مع عرض حي للحالة والـ Logs |

---

# الأستضافة الذاتية (self hosted)
| المكون (Component) | الوظيفة (Role) | الوصف التشغيلي (Operational Description) |
| :--- | :--- | ---: |
| <br> **[Hugo](https://gohugo.io/)** <br><br> |استضافة موقع شخصي | منشئ مواقع ستاتيك (Static Site Generator) يتميز بسرعة عالية جداً وأمان فائق لعدم وجود قاعدة بيانات |
| <br> **[Cloudflared](https://www.cloudflare.com)** <br><br> | نفق الاتصال (Tunnel) | يوفر وصولاً خارجياً آمناً للموقع بنسبة 100% عبر نفق مشفر دون الحاجة لفتح أي بورتات في الشبكة |



# ماهو tailscale
هو خدمة تجعل إنشاء شبكة افتراضية خاصة (VPN) بين أجهزتك أمراً سهلاً للغاية، وكأنها جميعاً متصلة بنفس سلك الشبكة في منزلك، حتى لو كان كل جهاز في مدينة أو دولة مختلفة.

يعتمد Tailscale على بروتوكول WireGuard الشهير، وهو معروف بسرعته العالية وأمانه القوي.

كيف يعمل Tailscale؟
بدلاً من الطريقة التقليدية التي تتطلب إعدادات معقدة في الراوتر (مثل فتح المنافذ Port Forwarding)، يقوم Tailscale بإنشاء ما يسمى Mesh Network:

اتصال مباشر: يربط الأجهزة ببعضها مباشرة (Point-to-Point) دون المرور بخادم مركزي يبطئ السرعة

تجاوز جدران الحماية: يستطيع العمل من خلف أي "مودم" أو "راوتر" دون الحاجة لتغيير إعدادات الأمان لديك

عناوين IP ثابتة: يعطي كل جهاز من أجهزتك عنوان IP خاصاً به (يبدأ غالباً بـ 100.x.y.z) يظل ثابتاً ولا يتغير
