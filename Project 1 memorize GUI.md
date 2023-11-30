# Project 1 memorize GUI



## ideas：



对于一个包含复杂功能的记录性application

既然要对一些记忆方式进行试验，那么就要包含相应功能，（是否能通过building blocks 类似的东西使之能够让任何一个人都能设定并发展其计划？）

包含引用和分组，由一个词汇或者短语引申到许多个子组，而子组中的词汇也可以互相“引申”

包含词汇与短语的记忆时间（参考oulu的方式）以及对应曲线，设定合适的复习逻辑，但是复习不一定一定得按照此逻辑，因为上面包含引用的分组实际上已经应当做得足够全面



关于自定引用和分组的具体实现方式，这应当是对每一次搜索来说的（但是一次搜索中应当可以新建窗口以便来回查看，从而抽象化的一次搜索应当被理解为一次关联性“延续”），在特定的搜索当中，产生了一些联系（同时在建立这些联系的时候需要进行comment（可以在这个搜索联系的单词应当创建一个临时的内存以存储连续搜索的词汇表），如同git，能够方便往后回顾时理解），而联系的实现应当是分叉树的形式，故而，每一个单词或词组都应当构建一个可以添加元素的类似简洁的思维导图一样的东西（或许将comment操作可视化也是一个不错的选择），而每次再次由别的词索引（索引是由词典决定的，而联系是自己定义的）到这个单词时，就能对已经构建的“联系”进行查看

关于如何实现内嵌词典的功能....

To add a dictionary function to your software and match it with the corresponding GUI, you would typically follow these steps:

1. **Define the dictionary function**: This function will handle the logic of your dictionary. It could be as simple as a Python dictionary with keys and values, or a more complex function that interacts with a database or an API.

```python
def dictionary_function(word):
    dictionary = {
        'word1': 'definition1',
        'word2': 'definition2',
        # ...
    }
    return dictionary.get(word, 'Word not found')
```

2. **Create the GUI**: Depending on the GUI library you're using, this could look different. Here's an example using Tkinter:

```
import tkinter as tk

def search_word():
    word = entry.get()
    definition = dictionary_function(word)
    result_label.config(text=definition)

root = tk.Tk()

entry = tk.Entry(root)
entry.pack()

search_button = tk.Button(root, text='Search', command=search_word)
search_button.pack()

result_label = tk.Label(root, text='')
result_label.pack()

root.mainloop()
```

In this example, when the 'Search' button is clicked, the search_word function is called. This function gets the word from the entry field, uses the dictionary_function to get the definition, and updates the label with the result.

Remember to replace 'word1', 'definition1', etc. with your actual words and definitions. If you're using a database or an API, you'll need to replace the dictionary_function with your actual function for fetching the definitions.



```python
import datetime
import json

class EbbinghausTool:
    def __init__(self, file_path):
        self.file_path = file_path
        try:
            with open(self.file_path, 'r') as f:
                self.data = json.load(f)
        except FileNotFoundError:
            self.data = {}

    def record(self, word):
        today = str(datetime.date.today())
        if today not in self.data:
            self.data[today] = []
        self.data[today].append(word)
    
        with open(self.file_path, 'w') as f:
            json.dump(self.data, f)
    
    def review(self):
        today = datetime.date.today()
        review_days = [1, 2, 4, 7, 15]  # Ebbinghaus's forgetting curve
        for i in review_days:
            day = str(today - datetime.timedelta(days=i))
            if day in self.data:
                print(f"Review words for {day}: {self.data[day]}")

tool = EbbinghausTool('ebbinghaus.json')
tool.record('example')
tool.review()
```

--gpt-4



Creating a full-fledged recording tool involves several components, including a user interface, data storage, and functionalities for recording and reviewing words. Given the complexity of such a tool, I'll provide you with a simplified example using Python and a basic console-based interface. This example will use a dictionary to store words and their corresponding memorization dates.



```python
import datetime
import pickle

class MemorizationTool:
    def __init__(self):
        self.words_dict = self.load_data()

    def load_data(self):
        try:
            with open('memorization_data.pkl', 'rb') as file:
                return pickle.load(file)
        except FileNotFoundError:
            return {}
    
    def save_data(self):
        with open('memorization_data.pkl', 'wb') as file:
            pickle.dump(self.words_dict, file)
    
    def record_word(self, word):
        current_date = datetime.date.today()
        if word not in self.words_dict:
            self.words_dict[word] = [current_date]
        else:
            self.words_dict[word].append(current_date)
    
    def review_words(self):
        for word, dates in self.words_dict.items():
            print(f"{word}: Memorized on {', '.join(map(str, dates))}")
    
    def run(self):
        while True:
            print("\nMemorization Tool Menu:")
            print("1. Record a word")
            print("2. Review memorized words")
            print("3. Exit")
    
            choice = input("Enter your choice (1/2/3): ")
    
            if choice == '1':
                word = input("Enter the word you want to record: ")
                self.record_word(word)
                print(f"{word} recorded on {datetime.date.today()}")
    
            elif choice == '2':
                print("\nMemorized Words:")
                self.review_words()
    
            elif choice == '3':
                self.save_data()
                print("Exiting Memorization Tool. Data saved.")
                break
    
            else:
                print("Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    tool = MemorizationTool()
    tool.run()
```

----gpt-3.5

This Python script defines a `MemorizationTool` class with methods for recording words, reviewing memorized words, loading and saving data, and running the tool. The data is stored in a dictionary where each word is associated with a list of memorization dates.

You can run this script, and it will prompt you with a simple console-based menu to record words, review memorized words, or exit the tool. The data will be saved to a file (`memorization_data.pkl`) for persistent storage. Keep in mind that this is a basic example, and for a more polished tool, you might want to consider developing a graphical user interface (GUI) using a library like Tkinter or PyQt.





Q.can you give me a brief introduction of how to use Tkinter or PyQt?

## Tkinter:

**Tkinter** is the standard GUI toolkit that comes with Python. It's simple to use and is suitable for small to medium-sized projects. Here's a simple example to create a basic window with Tkinter:



```python
import tkinter as tk

class MyGUI:
    def __init__(self, master):
        self.master = master
        master.title("My Tkinter GUI")

        self.label = tk.Label(master, text="Hello, Tkinter!")
        self.label.pack()
    
        self.quit_button = tk.Button(master, text="Quit", command=master.quit)
        self.quit_button.pack()

if __name__ == "__main__":
    root = tk.Tk()
    my_gui = MyGUI(root)
    root.mainloop()


```



In this example, a basic Tkinter window is created with a label and a quit button. Tkinter uses a geometry manager (here, `pack()`) to organize and display widgets.



## PyQt:

**PyQt** is a set of Python bindings for the Qt application framework. Qt is a powerful and feature-rich framework widely used for developing cross-platform applications. PyQt provides both GPL and commercial licenses. Here's a simple PyQt example:



```
from PyQt5.QtWidgets import QApplication, QLabel, QPushButton, QVBoxLayout, QWidget
import sys

class MyGUI(QWidget):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("My PyQt GUI")
    
        self.label = QLabel("Hello, PyQt!")
        self.quit_button = QPushButton("Quit")
        self.quit_button.clicked.connect(self.close)
    
        layout = QVBoxLayout()
        layout.addWidget(self.label)
        layout.addWidget(self.quit_button)
    
        self.setLayout(layout)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    my_gui = MyGUI()
    my_gui.show()
    sys.exit(app.exec_())
```

In this PyQt example, a `QMainWindow` is subclassed to create a simple window with a label and a quit button. PyQt uses layouts (here, `QVBoxLayout`) to organize widgets.



## Choosing Between Tkinter and PyQt:

The choice between Tkinter and PyQt often depends on the complexity of your project, licensing requirements, and personal preference. Tkinter is easier to learn and suitable for simpler applications, while PyQt offers more advanced features and a more extensive set of tools for larger projects.

Both libraries have extensive documentation and communities, making it easy to find resources and support. Choose the one that best fits your project requirements and your comfort level with the toolkit.



## learning website:

### for tkinter

1. 1.*Tkinter* 8.5 reference: a GUI for Pythonhttps://anzeljg.github.io/rin2/book2/2405/docs/tkinter/index.html
2. 2.real python https://realpython.com/python-gui-tkinter/
3. 3.https://docs.python.org/3/library/tkinter.html



### for PyQt

https://www.riverbankcomputing.co.uk/news

https://www.riverbankcomputing.com/static/Docs/PyQt5/

#### **Books:**

- "Rapid GUI Programming with Python and Qt" by Mark Summerfield:
  - This book provides a good introduction to PyQt.
- "Python GUI Programming with Tkinter and PyQt" by Alan D. Moore:
  - Covers both Tkinter and PyQt, giving you a broader perspective.

#### **Tutorials and Courses:**

- ZetCode's PyQt5 Tutorial:
  - [PyQt5 Tutorial](http://zetcode.com/gui/pyqt5/)
- Sentdex's PyQt5 GUI Programming Tutorials (YouTube):
  - [PyQt5 GUI Programming Tutorials](https://www.youtube.com/playlist?list=PLQVvvaa0QuDdVpDFNq4FwY9APZPGSUyR4)



#### some interesting articles:

difference bewteen qt5 and qt6:

https://www.pythonguis.com/faq/pyqt5-vs-pyqt6/







## 补足内容

### Python 中print(f ‘ ‘) or print(f “ “) 的用法

```python
from matplotlib_inline import backend_inline
from mxnet import np, npx
from d2l import mxnet as d2l

npx.set_np()

def f(x):
    return 3 * x ** 2 - 4 * x
    
def numerical_lim(f, x, h):
    return (f(x + h) - f(x)) / h

h = 0.1
for i in range(5):
    print(f'h={h:.5f}, numerical limit={numerical_lim(f, 1, h):.5f}')
    h *= 0.1


```



**注：** 其中 { : } :及:**后**的内容代表结果保留位数可省略，:**前**的内容为变量或表达式![df1b3d28d67b621df48d337a4802c58](E:\video\WeChat Files\wxid_1x4mvdq19v6f22\FileStorage\Temp\df1b3d28d67b621df48d337a4802c58.png)

### sys module

#### **sys 模块的作用**

sys 模块提供访问Python 解释器使用或维护的属性，以及与Python 解释器进行交互的方法。简单来讲，sys 模块负责程序与Python 解释器的交互，并提供了一系列的属性和方法，用于操控Python 运行时的环境。