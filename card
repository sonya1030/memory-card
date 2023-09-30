from PyQt5.QtCore import Qt
from PyQt5.QtWidgets import ( QApplication, QWidget, QLabel, QVBoxLayout, QHBoxLayout, QRadioButton, QGroupBox, QPushButton, QButtonGroup)
from random import shuffle

class Question():
    def __init__(self, question, right_ans, q1, q2, q3):
        self.question = question
        self.right_ans = right_ans
        self.wrong_ans1 = q1
        self.wrong_ans2 = q2
        self.wrong_ans3 = q3



question_list = []
q1 = Question('Кто убил Марка?', "Ваня", "Дворецкий", "пёсель", 'повар')
question_list.append(q1)
q2 = Question('Сколько длилась столетняя война?' , '116', '110', '100', '99')
question_list.append(q2)
q3 = Question('Какой есть цвет на флаге Китая?', "красный", "белый", "голубой", 'зелёный')
question_list.append(q3)

app = QApplication([])
main_win = QWidget()
main_win.setWindowTitle('Окно')
main_win.resize(500,300)

ques = QLabel('Самый сложный вопрос')
okk = QPushButton('Ответить')
group_ques = QGroupBox('Варианты ответов:')

ans1 = QRadioButton('Лёгкий ответ')
ans2 = QRadioButton('Средний ответ')
ans3 = QRadioButton('Тяжёлый ответ')
ans4 = QRadioButton('Жоский ответ')
line1 = QHBoxLayout()
line2 = QVBoxLayout()
line3 = QVBoxLayout()
line2.addWidget(ans1)
line2.addWidget(ans2)
line3.addWidget(ans3)
line3.addWidget(ans4)
line1.addLayout(line2)
line1.addLayout(line3)
group_ques.setLayout(line1)

group_ans = QGroupBox('Результаты теста')
result = QLabel('---')
correct = QLabel('Тяжёлый ответ')

group_ans.hide()

line_result = QVBoxLayout()
line_result.addWidget(result, alignment=(Qt.AlignLeft | Qt.AlignTop))
line_result.addWidget(correct, alignment=Qt.AlignCenter)
group_ans.setLayout(line_result)

line_Layout1 = QHBoxLayout()
line_Layout2 = QHBoxLayout()
line_Layout3 = QHBoxLayout()
line_Layout1.addWidget(ques, alignment=Qt.AlignCenter)
line_Layout2.addWidget(group_ans)
line_Layout2.addWidget(group_ques)
line_Layout3.addWidget(okk, alignment=Qt.AlignCenter)

main_line = QVBoxLayout()
main_line.addLayout(line_Layout1)
main_line.addLayout(line_Layout2)
main_line.addLayout(line_Layout3)

main_win.setLayout(main_line)

def show_result():
    group_ans.show()
    group_ques.hide()
    okk.setText('Следующий вопрос')

ButGroup = QButtonGroup()
ButGroup.addButton(ans1)
ButGroup.addButton(ans2)
ButGroup.addButton(ans3)
ButGroup.addButton(ans4)


def show_ques():
    group_ans.hide()
    group_ques.show()
    ButGroup.setExclusive(False)
    ans1.setChecked(False)
    ans2.setChecked(False)
    ans3.setChecked(False)
    ans4.setChecked(False)
    ButGroup.setExclusive(True)

    okk.setText('Ответить')


answers = [ans1, ans2, ans3, ans4]

def add_ques(q: Question):
    shuffle(answers)
    answers[0].setText(q.right_ans)
    answers[1].setText(q.wrong_ans1)
    answers[2].setText(q.wrong_ans2)
    answers[3].setText(q.wrong_ans3)
    correct.setText(q.right_ans)
    ques.setText(q.question)
    show_ques()

def show_correct(res):
    result.setText(res)
    show_result()

def check_answer():
    if answers[0].isChecked():
        show_correct('Правильно')
    else:
        if answers[1].isChecked() or answers[2].isChecked() or answers[3].isChecked():
            show_correct('NOO')


def start():
    if "Ответить" == okk.text():
        check_answer()
    else:
        next_question()

main_win.num_question = 0

def next_question():
    main_win.num_question += 1
    if main_win.num_question == len(question_list):
        main_win.num_question = 0 

    add_ques(question_list[main_win.num_question])



okk.clicked.connect(start)





main_win.show()
app.exec_()
