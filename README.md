import sys
from PyQt5.QtWidgets import QApplication, QWidget
from PyQt5.QtWidgets import QMainWindow
from project import Ui_MainWindow


class MyWidget(QMainWindow, Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
        self.pushButton.clicked.connect(self.run)

    def run(self):
        s = float(self.function.text().split('^')[1])
        self.graphicsView.clear()
        self.graphicsView.plot(range(0, 10000),
                         [i ** s for i in range(0, 10000)],
                               pen='r', name='first')

app = QApplication(sys.argv)
ex = MyWidget()
ex.show()
sys.exit(app.exec_())
