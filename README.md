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

---

## 🛠 Install  

```bash
pip install django-banana
```

---

## ➕ Add to Installed Apps  

```python
INSTALLED_APPS = [
    "banana",
]
```

---

## 📥 Load Banana in Your Template  

```html
{% load banana %}
```

---

## 📝 Example: Dashboard Stats  

```html
{% banana session="stats" %}
    this.total = len({{ users }})
    this.active = 0

    for u in {{ users }}
        if u.is_active
            this.active++
        endif
    endfor

    this.rate = (this.active / this.total) * 100

    <p>Total Users: {{ this.total }}</p>
    <p>Active: {{ this.active }}</p>
    <p>Rate: {{ this.rate }}%</p>
{% endbanana %}
```

---

## 📦 Example: Imports Between Sessions  

```html
{% banana session="constants" %}
    this.roles = ["Admin", "Editor", "Viewer"]
    this.greeting = "Welcome"
{% endbanana %}

{% banana session="page" %}
    use "session:constants"

    <h2>{{ constants.greeting }} to the Team Page</h2>

    <ul>
    for role in constants.roles
        <li>{{ role }}</li>
    endfor
    </ul>
{% endbanana %}
```

---

## ⚡ Example: One-Liner Rendering  

```html
<ul>
  {{ "u in {{ users }} -> '<li>' + u + '</li>'"|banana }}
</ul>
```

---

## ⚖️ Before & After  

### Counting Users  

**Before (classic Django):**  
```html
{% with total=users|length %}
  <p>Total Users: {{ total }}</p>
{% endwith %}

<ul>
{% for u in users %}
  <li>{{ u.username }}</li>
{% endfor %}
</ul>
```

**After (Banana):**  
```html
{% banana session="stats" %}
    this.total = len({{ users }})

    <ul>
    for u in {{ users }}
        <li>{{ u.username }}</li>
    endfor
    </ul>
{% endbanana %}

<p>Total Users: {{ stats.total }}</p>
```

---

### Sorting Items  

**Before (classic Django):**  
```html
{% with ordered=items|dictsort:"name" %}
<ul>
{% for i in ordered %}
  <li>{{ i.name }}</li>
{% endfor %}
</ul>
{% endwith %}
```

**After (Banana):**  
```html
{% banana %}
    ordered = order({{ items }}, "a-z")

    <ul>
    for i in ordered
        <li>{{ i }}</li>
    endfor
    </ul>
{% endbanana %}
```

---

## 📦 Features
- ✅ **Sessions** (state objects for each block)  
- ✅ **Assignments** (`x = 10`, `list = [1,2,3]`)  
- ✅ **Safe functions** (`len`, `split`, `order`)  
- ✅ **Control flow** (`for`, `if`)  
- ✅ **String concatenation** (`"Hello " + name`)  
- ✅ **Imports** (`use "session:foo"`)  
- ✅ **Inline HTML output**  
- ✅ **One-liners** for rendering loops  

---

## 🧩 Works Great With
Banana plays perfectly with modern Django tooling:  
- 🎨 **TailwindCSS** → utility-first styling  
- 🧵 **Django-Cotton** → declarative components (`<Card />`, `<Flex />`)  
- ⚡ **htmx** → dynamic interactions (AJAX without JS)  
- 🪶 **AlpineJS** → lightweight reactivity  

Together, you get **React-like ergonomics** with Django’s **simplicity and safety**.  

---

## 🏗 Roadmap
- [ ] Error handling (`Banana.errors` → console logging)  
- [ ] More built-in functions (`join`, `slice`, `unique`)  
- [ ] Selective imports (`use "session:utils" only foo, bar`)  
- [ ] Devtools integration (debug panel for Banana sessions)  
- [ ] Component shorthands (`include("partials/card", data)`)  

---

## ❤️ Contributing
Pull requests are welcome! 🍌  
We’re building Banana into the **React-like template engine Django never had**.  

---

## 📜 License
MIT License © 2025  
