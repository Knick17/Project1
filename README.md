import sys
import math
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
        self.pushButton.clicked.connect(self.n0)
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
        self.pushButton_23.clicked.connect(self.sin)
        self.pushButton_24.clicked.connect(self.cos)
        self.pushButton_25.clicked.connect(self.tg)
        self.pushButton_26.clicked.connect(self.ctg)
        self.pushButton_29.clicked.connect(self.delete)
        self.pushButton_28.clicked.connect(self.mod)
        self.pushButton_27.clicked.connect(self.div)
        self.g1 = 



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
        if self.text == '' or self.text[-1].isdigit() or self.text[-1] == ' ' or self.text[-1] == '-':
            self.text += '.'
            self.label.setText(self.text)
        else:
            pass
    def plus(self):
        if self.flag:
            self.text += ' + '
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def minus(self):
        if self.flag:
            self.text += ' - '
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def comp(self):
        if self.flag:
            self.text += ' * '
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def division(self):
        if self.flag:
            self.text += ' / '
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def modlike(self):
        if self.text == '' or self.text[-1] == ' ':
            self.text += '-'
            self.label.setText(self.text)
        else:
            pass
    def step(self):
        if self.flag:
            self.text += ' ^ '
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def sqrt(self):
        if self.flag:
            self.text += ' ^ 0.5'
            self.label.setText(self.text)
            self.flag = False
        else:
            pass

    def factor(self):
        if self.flag:
            self.text += '!'
            self.label.setText(self.text)
        else:
            pass
    def sin(self):
        if self.text == '':
            self.text += 'sin '
            self.flag = False
            self.label.setText(self.text)
        else:
            pass

    def cos(self):
        if self.text == '':
            self.text += 'cos '
            self.flag = False
            self.label.setText(self.text)
        else:
            pass
    def tg(self):
        if self.text == '':
            self.text += 'tg '
            self.flag = False
            self.label.setText(self.text)
        else:
            pass
    def ctg(self):
        if self.text == '':
            self.text += 'ctg '
            self.flag = False
            self.label.setText(self.text)
        else:
            pass
    def delete(self):
            self.text = self.text[:-1]
            self.label.setText(self.text)
    def mod(self):
        if self.flag:
            self.text += ' mod '
            self.label.setText(self.text)
            self.flag = False
        else:
            pass
    def div(self):
        if self.flag:
            self.text += ' div '
            self.label.setText(self.text)
            self.flag = False
        else:
            pass

    def equal(self):
        try:
            for lu in [' + ', ' - ', ' * ', ' / ',
                       ' ^ ', '!', 'sin ', 'cos ', 'tg ', 'ctg ', ' div ', ' mod ']:
                if lu in self.text:
                    break
            numbs = self.text.split(lu)
            if lu == "!":
                n1 = float(numbs[0])
                if n1 == int(n1) >= 0:
                    n = int(float(n1))
                    fac = 1
                    i = 0
                    while i < n:
                        i += 1
                        fac = fac * i
                    if n == 0:
                        self.fact = 1
                    self.fact = fac
                    self.label.setText(str(self.fact))
                    self.text = str(self.fact)
                else:
                    self.label.setText('Error')
                    self.text = ''
            elif lu == ' + ':
                n1 = float(numbs[0])
                self.label.setText(str((n1) + float(numbs[1])))
                self.text = str((n1) + float(numbs[1]))
            elif lu == ' - ':
                n1 = float(numbs[0])
                self.label.setText(str((n1) - float(numbs[1])))
                self.text = str((n1) - float(numbs[1]))
            elif lu == ' * ':
                n1 = float(numbs[0])
                self.label.setText(str((n1) * float(numbs[1])))
                self.text = str((n1) * float(numbs[1]))
            elif lu == ' / ':
                try:
                    n1 = float(numbs[0])
                    self.label.setText(str((n1) / float(numbs[1])))
                    self.text = str((n1) / float(numbs[1]))
                except:
                    self.label.setText('Error')
                    self.text = ''
            elif lu == ' ^ ':
                try:
                    n1 = float(numbs[0])
                    self.label.setText(str((n1) ** float(numbs[1])))
                    self.text = str((n1) ** float(numbs[1]))
                except:
                    self.label.setText('Error')
                    self.text = ''
            elif lu == 'sin ':
                    n2 = float(numbs[1])
                    self.label.setText(str(math.sin(n2)))
                    self.text = str(str(math.sin(n2)))
            elif lu == 'cos ':
                    n2 = float(numbs[1])
                    self.label.setText(str(math.cos(n2)))
                    self.text = str(str(math.cos(n2)))
            elif lu == 'tg ':
                    n2 = float(numbs[1])
                    self.label.setText(str(math.tan(n2)))
                    self.text = str(str(math.tan(n2)))
            elif lu == 'ctg ':
                    n2 = float(numbs[1])
                    self.label.setText(str(1/ math.tan(n2)))
                    self.text = str(1 / math.tan(n2))
            elif lu == ' mod ':
                    n1 = float(numbs[0])
                    self.label.setText(str((n1) % float(numbs[1])))
                    self.text = str((n1) % float(numbs[1]))
            elif lu == ' div ':
                    n1 = float(numbs[0])
                    self.label.setText(str((n1) // float(numbs[1])))
                    self.text = str((n1) // float(numbs[1]))
            self.flag = True
        except:
            self.flag = True
            self.label.setText('Error')
            self.text = ''

app = QApplication(sys.argv)
ex = MyWidget()
ex.show()
sys.exit(app.exec_())
