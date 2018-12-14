import sys
import math
from PyQt5.QtWidgets import QApplication, QWidget, QCheckBox, QLineEdit, QLabel, QPushButton
from PyQt5.QtWidgets import QMainWindow, QInputDialog
from project import Ui_MainWindow


class MyWidget(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
        self.pushButton_22.clicked.connect(self.askgraph)
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
        self.gr1 = QLineEdit(self)
        self.gr2 = QLineEdit(self)
        self.gr3 = QLineEdit(self)
        self.gr4 = QLineEdit(self)
        self.gr5 = QLineEdit(self)
        self.l1 = QLabel(self)
        self.l2 = QLabel(self)
        self.l3 = QLabel(self)
        self.l4 = QLabel(self)
        self.l5 = QLabel(self)
        self.graphs = [self.gr1, self.gr2, self.gr3, self.gr4, self.gr5]
        self.li = [self.l1, self.l2, self.l3, self.l4, self.l5]
        self.build = QPushButton(self)


    def askgraph(self):
        self.number_of_schedules = 0
        j, okBtnPressed = QInputDialog.getInt(
            self, "Опрос", "Колво графиков", 1, 1, 5, 1)
        tx = ['f(x)=', 'g(x)=', 'a(x)=', 'b(x)=', 'm(x)=']
        for i in range(j):
            self.li[i].setText(tx[i])
            self.li[i].move(40, 400 + i * 50)
            self.graphs[i].move(90, 400 + i * 50)
        self.number_of_schedules = j
        self.build.move(240, 380)
        self.build.clicked.connect(self.buildgraph)

    def buildgraph(self):
        f = True
        try:
            self.graphicsView.clear()
            ox = []
            oy = []
            for i in range(self.number_of_schedules):
                for a in range(-10, 10):
                    for x in range(-1000, 1001):
                        try:
                            oy.append(eval(self.graphs[i].text()))
                            ox.append(x)
                            f = True
                        except:
                            self.graphicsView.plot(ox, oy, pen='b')
                            #self.graphicsView.plot([x for d in range(-1000, 1000)], [d for d in range(-1000, 1000)], pen='w')
                            ox.clear()
                            oy.clear()
                            f = False
                            continue
                    if f:
                        self.graphicsView.plot(ox, oy, pen='b')
                    ox.clear()
                    oy.clear()
        except:
            pass

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
