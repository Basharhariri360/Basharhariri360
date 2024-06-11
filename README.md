% تعريف المعاملات
L1 = 1; % H
L2 = 1; % H
C = 0.1e-6; % F
R = 10; % Ohm

% تعريف مصفوفات النظام
A = [0 1/L2 0;-1/C 0 -1/C;0 1/L1 -R/L1];
B = [0;1/C;0];
C = [0 1 -R];
D = 0;

% إنشاء النظام
sys = ss(A, B, C, D);

% تحديد زمن المحاكاة
t = linspace(0, 0.01, 10);

% إدخال خطوة وحدة كإشارة دخل
u = ones(size(t));

% محاكاة الاستجابة الزمنية
[y, t, x] = lsim(sys, u, t);

% رسم النتائج
figure;
subplot(3,1,1);
plot(t, x);
title('استجابة متغيرات الحالة');
xlabel('الزمن (ثانية)');
ylabel('القيم');
legend('i_{L1}(t)', 'i_{L2}(t)', 'v_C(t)');

subplot(3,1,2);
plot(t, y);
title('استجابة الجهد عبر المكثف v_C(t)');
xlabel('الزمن (ثانية)');
ylabel('الجهد (فولت)');

% رسم مسارات الطور لكل زوج من متغيرات الحالة
figure;
subplot(3,1,1);
plot(x(:,1), x(:,2));
title('مسار الطور بين i_{L1}(t) و i_{L2}(t)');
xlabel('i_{L1}(t)');
ylabel('i_{L2}(t)');
grid on;

subplot(3,1,2);
plot(x(:,1), x(:,3));
title('مسار الطور بين i_{L1}(t) و v_C(t)');
xlabel('i_{L1}(t)');
ylabel('v_C(t)');
grid on;

subplot(3,1,3);
plot(x(:,2), x(:,3));
title('مسار الطور بين i_{L2}(t) و v_C(t)');
xlabel('i_{L2}(t)');
ylabel('v_C(t)');
grid on;
<!---
Basharhariri360/Basharhariri360 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
