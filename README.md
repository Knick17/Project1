import sys
from PyQt5.QtWidgets import QApplication, QWidget
from PyQt5.QtWidgets import QMainWindow
from project import Ui_MainWindow


class MyWidget(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
        self.pushButton_22.clicked.connect(self.run)
        self.text = ''
        self.flag = True
        self.pushButton_4.clicked.connect(self.n1)
        self.pushButton_9.clicked.connect(self.n2)
        self.pushButton_14.clicked.connect(self.n3)
        self.pushButton_2.clicked.connect(self.n4)
        self.pushButton_8.clicked.connect(self.n5)
        self.pushButton_13.clicked.connect(self.n6)
        self.pushButton_3.clicked.connect(self.n7)
        self.pushButton_7.clicked.connect(self.n8)
        self.pushButton_12.clicked.connect(self.n9)
        self.pushButton_10.clicked.connect(self.point)
        self.pushButton_15.clicked.connect(self.factor)
        self.pushButton_20.clicked.connect(self.equal)
        self.pushButton_19.clicked.connect(self.sqrt)
        self.pushButton_18.clicked.connect(self.step)
        self.pushButton_17.clicked.connect(self.minus)
        self.pushButton_16.clicked.connect(self.plus)
        self.pushButton_11.clicked.connect(self.division)
        self.pushButton_6.clicked.connect(self.comp)
        self.pushButton_5.clicked.connect(self.modlike)
        self.pushButton_21.clicked.connect(self.clear)

    def run(self):
        #s = float(self.function.text().split('^')[1])
        self.graphicsView.clear()
        self.graphicsView.plot(range(-50, 50),
                               [i ** 2 - 10 for i in range(-50, 50)], pen='b')
    def clear(self):
        self.text = ''
        self.label.setText(self.text)
        self.flag = True
    def n1(self):
        self.text += '1'
        self.label.setText(self.text)
    def n2(self):
        self.text += '2'
        self.label.setText(self.text)
    def n3(self):
        self.text += '3'
        self.label.setText(self.text)
    def n4(self):
        self.text += '4'
        self.label.setText(self.text)
    def n5(self):
        self.text += '5'
        self.label.setText(self.text)
    def n6(self):
        self.text += '6'
        self.label.setText(self.text)
    def n7(self):
        self.text += '7'
        self.label.setText(self.text)
    def n8(self):
        self.text += '8'
        self.label.setText(self.text)
    def n9(self):
        self.text += '9'
        self.label.setText(self.text)
    def n0(self):
        self.text += '0'
        self.label.setText(self.text)
    def point(self):
        if self.text[-1].isdigit():
            self.text += '.'
            self.label.setText(self.text)
        else:
            pass
    def plus(self):
        if self.flag:
            self.text += '+'
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def minus(self):
        if self.flag:
            self.text += '-'
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def comp(self):
        if self.flag:
            self.text += '*'
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def division(self):
        if self.flag:
            self.text += '/'
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def modlike(self):
        if self.text == '':
            self.text += '-'
            self.label.setText(self.text)
        else:
            pass
    def step(self):
        if self.flag:
            self.text += '^'
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def sqrt(self):
        if self.flag:
            self.text += '^0.5'
            self.label.setText(self.text)
            self.flag = False
        else:
            pass

    def factor(self):
        if self.flag:
            n = int(float(self.text))
            fac = 1
            i = 0
            while i < n:
                i += 1
                fac = fac * i
            self.fact = fac
            self.text += '!'
            self.label.setText(self.text)
    def equal(self):
        try:
            for lu in ['+', '-', '*', '/', '^', '!']:
                if lu in self.text:
                    break
            numbs = self.text.split(lu)
            n1 = float(numbs[0])
            if lu == "!":
                if n1 == int(n1) >= 0:
                    self.label.setText(str(self.fact))
                    self.text = str(self.fact)
                else:
                    self.label.setText('Error')
                    self.text = ''
            elif lu == '+':
                self.label.setText(str((n1) + float(numbs[1])))
                self.text = str((n1) + float(numbs[1]))
            elif lu == '-':
                self.label.setText(str((n1) - float(numbs[1])))
                self.text = str((n1) - float(numbs[1]))
            elif lu == '*':
                self.label.setText(str((n1) * float(numbs[1])))
                self.text = str((n1) * float(numbs[1]))
            elif lu == '/':
                try:
                    self.label.setText(str((n1) / float(numbs[1])))
                    self.text = str((n1) / float(numbs[1]))
                except:
                    self.label.setText('Error')
                    self.text = ''
            elif lu == '^':
                try:
                    self.label.setText(str((n1) ** float(numbs[1])))
                    self.text = str((n1) ** float(numbs[1]))
                except:
                    self.label.setText('Error')
                    self.text = ''
            self.flag = True
        except:
            self.flag = False
            self.text = ''

app = QApplication(sys.argv)
ex = MyWidget()
ex.show()
sys.exit(app.exec_())
