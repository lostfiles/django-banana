# 🍌 Django-Banana  
### Modern, React-like Templates — Without Leaving Django  

---

## 🚀 What is Banana?  
Banana is a **template DSL for Django** that makes templates feel like React or Vue — but 100% **server-side rendered**.  

It gives you:  
- **Sessions (state)** → `stats.total`, `stats.rate`  
- **Assignments** → `x = 5`, `names = ["a","b","c"]`  
- **Loops** → `for item in list … endfor`  
- **If statements** → `if … endif`  
- **Functions** → `len()`, `split()`, `order()` and extensible custom functions  
- **Imports** → `use "session:utils"` (like ES6 imports)  
- **Inline HTML output** inside Banana blocks  

---

## ✨ Why Banana?  
Traditional Django templates are deliberately limited.  
Banana gives you **just enough power** to:  

- Replace boilerplate `{% with %}`, `{% for %}`, `{% if %}` blocks with **clean declarative code**  
- Build **dashboards, reports, and CRUD apps** faster  
- Keep state organized via **namespaced sessions**  
- Prototype **faster** without rewriting views for simple display logic  

And it’s still:  
- 🔒 **Safe** (auto-escaping, no eval, no arbitrary Python execution)  
- 🛡️ **Server-side** (no hydration, no bundle pipeline)  
- ⚡ **Compatible** (works alongside Tailwind, htmx, AlpineJS, Django-Cotton)  

---

## 🛠 Install  

```bash
pip install django-banana
