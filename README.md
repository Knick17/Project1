import sys
from PyQt5.QtWidgets import QApplication, QMainWindow
from gp import Ui_Dialog


class MyWidget(QMainWindow,  Ui_Dialog):











app = QApplication(sys.argv)
ex = MyWidget()
ex.show()
sys.exit(app.exec_())
