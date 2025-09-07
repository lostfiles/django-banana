# 🍌 Django-Banana  
### Modern, React-like Templates — Without Leaving Django  

---

## 🚀 What is Banana?  
Banana is a **template DSL for Django** that makes templates feel like React or Vue — but 100% **server-side rendered**.  

Out of the box, Django’s template engine is intentionally limited. That’s great for safety, but it often forces you to push even the simplest display logic into views or write custom filters. Banana fills that gap by giving you **just enough power** inside templates — without leaving Django’s ecosystem.  

With Banana you get:  
- **Sessions (state)** → `stats.total`, `stats.rate`  
- **Assignments** → `x = 5`, `names = ["a","b","c"]`  
- **Loops** → `for item in list … endfor`  
- **If statements** → `if … endif`  
- **Functions** → `len()`, `split()`, `order()` and extensible custom functions  
- **Imports** → `use "session:utils"` (like ES6 imports)  
- **Inline HTML output** → mix logic + markup naturally  

---

## ✨ Why Banana?  

### Traditional Django Templates
- Are deliberately **dumb**.  
- Require lots of `{% with %}`, `{% if %}`, and `{% for %}` blocks.  
- Push you to write boilerplate in views for simple counts, ordering, or string manipulation.  

### Banana Templates
- Feel more like **React/Vue components** with **state and props**.  
- Let you **declare logic and render HTML inline**.  
- Keep related variables **grouped in sessions** instead of polluting the context.  
- Speed up development by cutting out view boilerplate.  

Banana gives Django a **modern templating experience** without breaking its safety or philosophy.  

---

## 🛡️ Server-Side Safety  
Because Banana runs **entirely server-side**, you get all the advantages of Django’s template system:  

- 🔒 No sensitive logic leaks to the client.  
- 🛡️ Auto-escaping is preserved.  
- ⚡ First load is fast (full HTML rendered, no hydration).  
- 🧩 Works with SEO and accessibility out of the box.  

This makes Banana safer and simpler than client-side frameworks — you don’t need to set up JWT auth, hydration, or CORS just to render a dashboard.  

---

## 🛠 Install  

```bash
pip install django-banana

