from flask import Flask, render_template

app = Flask(name)

قائمة بالكتب (يمكنك استبدالها بقاعدة بيانات لاحقًا)

books = [ {"title": "كتاب 1", "author": "المؤلف الأول", "description": "وصف مختصر للكتاب الأول"}, {"title": "كتاب 2", "author": "المؤلف الثاني", "description": "وصف مختصر للكتاب الثاني"}, {"title": "كتاب 3", "author": "المؤلف الثالث", "description": "وصف مختصر للكتاب الثالث"} ]

@app.route('/') def home(): return render_template('index.html', books=books)

if name == 'main': app.run(debug=True)

ملف HTML (templates/index.html)

index_html = """

<!DOCTYPE html><html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مكتبة Moh Ma</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
    <h1>مرحبًا بكم في مكتبة Moh Ma</h1>
    <div class="book-list">
        {% for book in books %}
        <div class="book">
            <h2>{{ book.title }}</h2>
            <p><strong>المؤلف:</strong> {{ book.author }}</p>
            <p>{{ book.description }}</p>
        </div>
        {% endfor %}
    </div>
</body>
</html>
"""ملف CSS (static/style.css)

style_css = """ body { font-family: Arial, sans-serif; text-align: center; background-color: #f4f4f4; }

h1 { color: #333; }

.book-list { display: flex; flex-direction: column; align-items: center; }

.book { background: white; padding: 15px; margin: 10px; border-radius: 5px; box-shadow: 0 0 5px rgba(0, 0, 0, 0.2); width: 300px; } """

إنشاء الملفات تلقائيًا عند تشغيل البرنامج

import os

ios.makedirs("templates", exist_ok=True) ios.makedirs("static", exist_ok=True)

with open("templates/index.html", "w", encoding="utf-8") as f: f.write(index_html)

with open("static/style.css", "w", encoding="utf-8") as f: f.write(style_css)

