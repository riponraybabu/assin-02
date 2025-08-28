
1. What is the difference between **getElementById, getElementsByClassName, and querySelector / querySelectorAll**?
2. How do you **create and insert a new element into the DOM**?
3. What is **Event Bubbling** and how does it work?
4. What is **Event Delegation** in JavaScript? Why is it useful?
5. What is the difference between **preventDefault() and stopPropagation()** methods?

   
ans -1. Difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll

getElementById("id") → একটি মাত্র এলিমেন্ট রিটার্ন করে (ID সবসময় ইউনিক হয়)।

getElementsByClassName("class") → একই ক্লাসের সবগুলো এলিমেন্টের লাইভ লিস্ট (HTMLCollection) রিটার্ন করে।

querySelector("cssSelector") → প্রথম যে এলিমেন্ট মিলে তাকে রিটার্ন করে।

querySelectorAll("cssSelector") → সব এলিমেন্টের NodeList রিটার্ন করে (লাইভ না, স্ট্যাটিক থাকে)।

👉 মূল পার্থক্য হলো রিটার্ন টাইপ আর কতগুলো এলিমেন্ট ধরতে পারবে।
ans-2. 1)createElement() দিয়ে নতুন element বানাবেন।

2)textContent / innerHTML বা attribute অ্যাড করবেন।

3)পছন্দমতো জায়গায় append, prepend, insertBefore ইত্যাদি দিয়ে ঢুকাবেন।
ans-3. কোনো element এ event ঘটলে, সেটা নিজের handler চালায় → তারপর উপরের parent → তারপর document → window পর্যন্ত যেতে থাকে।

এটাকে বাবলিং বলে কারণ event টা ওপরের দিকে বাবল হয়ে ওঠে।
html
<div id="outer">
   <button id="inner">Click</button>
</div>
js
outer.addEventListener("click", () => console.log("Outer clicked"));
inner.addEventListener("click", () => console.log("Inner clicked"));


👉 Button ক্লিক করলে output হবে:
Inner clicked → তারপর Outer clicked.
ans-4:একটা parent element এ listener বসিয়ে child গুলোকে handle করা।

কারণ বাবলিং এর জন্য event parent এও পৌঁছে যায়।

উপকারিতা:

1.আলাদা আলাদা listener বসাতে হয় না → কোড লাইটওয়েট থাকে।

2.নতুন element DOM এ ঢুকলেও কাজ করবে।
ans-5.
preventDefault() → event এর ডিফল্ট ব্রাউজার বিহেভিয়ার বন্ধ করে।
যেমন: লিঙ্কে ক্লিক করলে আর নতুন পেজে যাবে না।
stopPropagation() → event এর বাবলিং বন্ধ করে।
অর্থাৎ parent এ পৌঁছাতে দেবে না।
