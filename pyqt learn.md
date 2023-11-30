# pyqt learn



```python
QPushButton(string text, QWidget parent = None)
```

The `text` parameter is a text that will be displayed on the button. The `parent` is a widget on which we place our button. In our case it will be a `QWidget`. Widgets of an application form a hierarchy. In this hierarchy, most widgets have their parents. Widgets without parents are toplevel windows.

```python
qbtn.clicked.connect(QApplication.instance().quit)
```

name.clicked.connect(QApplication.instance().quit)





#### 补充

##### logic count

 & 与

 | 或

 ^ 按位异或

~ 按位取反

<< 左移

\>>右移



