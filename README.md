# dsa-project-code
import tkinter as tk

from necessary_function import employee_feedback, print_data_feedback
from view_data import ViewData

FONT_HEADING = ("Arial", 40, "bold")
FONT_SUB_HEADING = ("Arial", 15, "bold")
FONT_BUTTON = ("Arial", 13, "bold")


class EmployeeFeedback:
    def __init__(self):
        self.window = tk.Tk()

        self.window.title("Employee Feedback")
        self.window.minsize(width=900, height=600)
        self.window.config(bg="#DBDFEA")

        # Heading
        self.heading = tk.Label(self.window, text="Employee Feedback", font=FONT_HEADING,
                                bg='#DBDFEA', fg='#3C486B')
        self.heading.place(x=275, y=40)

        # Name
        self.name_label = tk.Label(self.window, text="Name", font=FONT_SUB_HEADING,
                                   bg='#DBDFEA', fg='#3C486B')
        self.name_label.place(x=260, y=160)
        self.name_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.name_entry.place(x=365, y=160)

        # Feedback
        self.feedback_label = tk.Label(self.window, text="Feedback".title(), font=FONT_SUB_HEADING,
                                       bg='#DBDFEA', fg='#3C486B')
        self.feedback_label.place(x=260, y=200)
        self.feedback_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.feedback_entry.place(x=365, y=200)

        # Save data
        self.save_entry = tk.Button(self.window, text="Save",
                                    font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                    width=5, command=self.save_data)
        self.save_entry.place(x=260, y=240)

        # View data
        self.view_data_entry = tk.Button(self.window, text="View Data",
                                         font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                         width=10, command=self.view_data)
        self.view_data_entry.place(x=260, y=280)

        self.window.mainloop()

    def save_data(self):
        """Save data"""
        name = self.name_entry.get()
        feedback = self.feedback_entry.get()

        if name and feedback:
            employee_feedback(name=name, feedback=feedback)

    def view_data(self):
        """View data"""
        data = print_data_feedback(variant='employee')
        ViewData('Employee Feedbacks', data)

import tkinter
from tkinter import Tk

from employee_feedback import EmployeeFeedback
from leave_application import LeaveApplication
from recruitement_application import RecruitmentApplication
from hr_system import HRSystem
from pay_calculator import PayCalculator
from priority_task import PriorityTask

FONT_HEADING = ("Arial", 40, "bold")
FONT_BUTTON = ("Arial", 10, "bold")


class Home:
    def __init__(self):
        window = Tk()
        window.title("Employee Management System")
        window.minsize(width=900, height=600)
        window.config(bg="#DBDFEA")

        # Label
        label = tkinter.Label(text="Options", font=FONT_HEADING, bg='#DBDFEA', fg="#3C486B")
        label.place(x=375, y=20)

        # Pay Calculator Button
        pay_calculator_button = tkinter.Button(text="Pay calculator".title(), font=FONT_BUTTON,
                                               width=30, pady=10, bg='#3C486B', fg='white',
                                               command=PayCalculator)
        pay_calculator_button.place(x=350, y=140)

        # Calculate Priority task button
        calculate_priority_task_button = tkinter.Button(text="Calculate priority task".title(), font=FONT_BUTTON,
                                                        width=30, pady=10, bg='#3C486B', fg='white',
                                                        command=PriorityTask)
        calculate_priority_task_button.place(x=350, y=220)

        # Most Productive Employee Button
        most_productive_employee_button = tkinter.Button(text="Most productive employee".title(), font=FONT_BUTTON,
                                                         width=30, pady=10, bg='#3C486B', fg='white',
                                                         command=HRSystem)
        most_productive_employee_button.place(x=350, y=300)

        # Employee Feedback Button
        employee_feedback_button = tkinter.Button(text="Employee feedback".title(), font=FONT_BUTTON,
                                                  width=30, pady=10, bg='#3C486B', fg='white',
                                                  command=EmployeeFeedback)
        employee_feedback_button.place(x=350, y=380)

        # Leave Application Button
        leave_application_button = tkinter.Button(text="Leave Application".title(), font=FONT_BUTTON,
                                                  width=30, pady=10, bg='#3C486B', fg='white',
                                                  command=LeaveApplication)
        leave_application_button.place(x=350, y=460)

        # Recruitment Application Button
        recruitment_application_button = tkinter.Button(text="Recruitment Application".title(), font=FONT_BUTTON,
                                                        width=30, pady=10, bg='#3C486B', fg='white',
                                                        command=RecruitmentApplication)
        recruitment_application_button.place(x=350, y=540)

        window.mainloop()

import tkinter as tk

from necessary_function import hr_system_save_data, most_productive_employee

FONT_HEADING = ("Arial", 40, "bold")
FONT_SUB_HEADING = ("Arial", 15, "bold")
FONT_BUTTON = ("Arial", 13, "bold")


class HRSystem:
    def __init__(self):
        self.window = tk.Tk()

        self.window.title("HR System")
        self.window.minsize(width=900, height=600)
        self.window.config(bg="#DBDFEA")

        # Heading
        self.heading = tk.Label(self.window, text="HR System", font=FONT_HEADING,
                                bg='#DBDFEA', fg='#3C486B')
        self.heading.place(x=275, y=40)

        # Name Entry
        self.name_label = tk.Label(self.window, text="Name", font=FONT_SUB_HEADING,
                                   bg='#DBDFEA', fg='#3C486B')
        self.name_label.place(x=260, y=160)
        self.name_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.name_entry.place(x=400, y=160)

        # Priority Score Entry
        self.priority_label = tk.Label(self.window, text="priority score".title(), font=FONT_SUB_HEADING,
                                       bg='#DBDFEA', fg='#3C486B')
        self.priority_label.place(x=260, y=200)
        self.priority_score_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.priority_score_entry.place(x=400, y=200)

        # Total Hours Entry
        self.total_hours_label = tk.Label(self.window, text="Total Hours", font=FONT_SUB_HEADING,
                                          bg='#DBDFEA', fg='#3C486B')
        self.total_hours_label.place(x=260, y=240)
        self.total_hours_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.total_hours_entry.place(x=400, y=240)

        # Calculate the most productive employee
        self.save_data_button = tk.Button(self.window, text="Save",
                                          font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                          width=7, command=self.save_data)
        self.save_data_button.place(x=260, y=280)

        # Calculate the most productive employee
        self.most_productive_employee_entry = tk.Button(self.window, text="Most Productive Employee",
                                                        font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                                        width=22, command=self.calculate_most_productive_employee)
        self.most_productive_employee_entry.place(x=260, y=320)

        # Result Label
        self.result_label = tk.Label(self.window, text='Result:', font=FONT_SUB_HEADING, bg='#DBDFEA',
                                     fg='#3C486B')
        self.result_label.place(x=330, y=375)

        self.window.mainloop()

    def save_data(self):
        name = self.name_entry.get()
        total_hours = self.total_hours_entry.get()
        priority_score = self.priority_score_entry.get()

        if name and total_hours and priority_score:
            result = hr_system_save_data(name=name, total_hours=total_hours, priority_score=priority_score)
            if result:
                self.show_result(value=result)

    def calculate_most_productive_employee(self):
        """Calculate most productive employee"""
        productive_employee = most_productive_employee()
        self.show_result(value=productive_employee)

    def show_result(self, value):
        """Show the final result"""
        self.result_label.config(text=f'Result: {value}')


import tkinter as tk

from necessary_function import leave_application, print_data_feedback
from view_data import ViewData

FONT_HEADING = ("Arial", 40, "bold")
FONT_SUB_HEADING = ("Arial", 15, "bold")
FONT_BUTTON = ("Arial", 13, "bold")


class LeaveApplication:
    def __init__(self):
        self.window = tk.Tk()

        self.window.title("Leave Application")
        self.window.minsize(width=900, height=600)
        self.window.config(bg="#DBDFEA")

        # Heading
        self.heading = tk.Label(self.window, text="Leave Application", font=FONT_HEADING,
                                bg='#DBDFEA', fg='#3C486B')
        self.heading.place(x=275, y=40)

        # Name Entry
        self.name_label = tk.Label(self.window, text="Name", font=FONT_SUB_HEADING,
                                   bg='#DBDFEA', fg='#3C486B')
        self.name_label.place(x=260, y=160)
        self.name_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.name_entry.place(x=440, y=160)

        # Date of Leave
        self.date_of_leave_label = tk.Label(self.window, text="Date of Leave".title(), font=FONT_SUB_HEADING,
                                            bg='#DBDFEA', fg='#3C486B')
        self.date_of_leave_label.place(x=260, y=200)
        self.date_of_leave_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.date_of_leave_entry.place(x=440, y=200)

        # Purpose of Leave
        self.purpose_of_leave_label = tk.Label(self.window, text="Purpose of Leave", font=FONT_SUB_HEADING,
                                               bg='#DBDFEA', fg='#3C486B')
        self.purpose_of_leave_label.place(x=260, y=240)
        self.purpose_of_leave_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.purpose_of_leave_entry.place(x=440, y=240)

        # Save data
        self.save_entry = tk.Button(self.window, text="Save",
                                    font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                    width=5, command=self.save_data)
        self.save_entry.place(x=260, y=280)

        # View data
        self.view_data_entry = tk.Button(self.window, text="View Data",
                                         font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                         width=10, command=self.view_data)
        self.view_data_entry.place(x=260, y=320)

        self.window.mainloop()

    def save_data(self):
        """Save data"""
        name = self.name_entry.get()
        date_of_leave = self.date_of_leave_entry.get()
        purpose_of_leave = self.purpose_of_leave_entry.get()

        if name and date_of_leave and purpose_of_leave:
            leave_application(name=name, date_of_leave=date_of_leave, purpose_of_leave=purpose_of_leave)

    def view_data(self):
        """View data"""
        data = print_data_feedback(variant='leave')
        ViewData('Leave Applications', data)

from home import Home

home_tkinter_page = Home()


import math

employee_feedback_list = {}
leave_application_list = {}
recruitment_application_list = {}
hash_priority_queue = [None] * 500
priority_queue = []
calculate_pay_dict = {}
hr_system_dict = {}


def save_calculated_pay(name, hours_worked, overtime, break_hrs, rate=2):
    global calculate_pay_dict
    try:
        hours_worked = math.ceil(float(hours_worked))
        overtime = math.ceil(float(overtime))
        break_hrs = math.ceil(float(break_hrs))
    except ValueError:
        return "One of the value is not an integer or a float number"
    pay = (hours_worked + overtime - break_hrs) * rate
    append_value = {'hours': hours_worked, 'overtime': overtime, 'break': break_hrs, 'pay': math.ceil(pay)}
    calculate_pay_dict[name] = append_value
    print('ent', calculate_pay_dict)


def calculate_pay(name):
    global calculate_pay_dict
    if name not in calculate_pay_dict:
        return 'Name does not exist'
    pay = calculate_pay_dict[name]['pay']
    print('ent', pay, calculate_pay_dict)
    return int(pay)


def highest_paid_employee():
    global calculate_pay_dict
    if len(calculate_pay_dict) == 0:
        return "No data inserted"
    temp = [val['pay'] for val in calculate_pay_dict.values()]
    name = [key for key in calculate_pay_dict.keys()]
    pay = max(temp)
    print('ent', pay, calculate_pay_dict)
    return name[temp.index(pay)]


def hash_function(key, size):
    if isinstance(key, int):
        return key % size
    else:
        unicodes = 0
        for i in key:
            unicodes += ord(i)
        return unicodes % size


def add_priority_queue(item, priority):
    global priority_queue, hash_priority_queue
    try:
        priority = math.ceil(float(priority))
    except ValueError:
        return "One of the value is not an integer or a float number"
    if priority > 10:
        return "Priority should be within 0 and 10 (inclusive)"
    temp = (item, priority)
    # here apply hash
    index = hash_function(key=item, size=500)
    hash_priority_queue[index] = temp
    priority_queue = [x for x in hash_priority_queue if x is not None]
    priority_queue.sort()
    priority_queue.reverse()
    print('ent', priority_queue)


def is_empty():
    global priority_queue
    if len(priority_queue) == 0:
        return True
    else:
        return False


def max_priority_queue():
    global priority_queue
    # if is_empty(priority_queue):
    #     return "queue is empty"
    # else:
    #     minn = 999999999
    #     for i in priority_queue:
    #         if i[1] <= minn:
    #             minn = int(i[1])
    #     for i in priority_queue:
    #         if int(i[1]) == minn:
    #             return i
    y = [z for z in priority_queue if z is not None]
    if len(y) == 0:
        return "No data inserted"
    x = [val for (key, val) in y]
    val = x.index(max(x))
    print('ent', val, priority_queue)
    return y[val][0]


# def calculate_priority_task(tasks):
#     """tasks will be a nested tuple in the form ( (task1,priority_number) , (task2,prioirty_number) ,
#     # (task3,priority_number) )"""
#     return min(tasks)


def hr_system_save_data(name, total_hours, priority_score):
    global hr_system_dict
    try:
        total_hours = math.ceil(float(total_hours))
        priority_score = math.ceil(float(priority_score))
    except ValueError:
        return "One of the value is not an integer or a float number"
    final_score = total_hours + priority_score
    hr_system_dict[name] = final_score
    print('ent', hr_system_dict)


def most_productive_employee():
    global hr_system_dict
    if len(hr_system_dict) == 0:
        return "No data inserted"
    names = [key for key in hr_system_dict.keys()]
    scores = [val for val in hr_system_dict.values()]
    ans = names[scores.index(max(scores))]
    return ans


def employee_feedback(name, feedback):
    global employee_feedback_list
    employee_feedback_list[name] = {'feedback': feedback}
    print('ent', employee_feedback_list)


def leave_application(name, date_of_leave, purpose_of_leave):
    global leave_application_list
    append_value = {'dol': date_of_leave, 'pol': purpose_of_leave}
    leave_application_list[name] = append_value
    print('ent', leave_application_list)


def recruitment_application(name, certifications, job_title):
    global recruitment_application_list
    append_value = {'certifications': certifications, 'job_title': job_title}
    recruitment_application_list[name] = append_value
    print('ent', recruitment_application_list)


def print_data_feedback(variant):
    global employee_feedback_list, leave_application_list, recruitment_application_list
    if variant == 'employee':
        temp = employee_feedback_list
        val = 1
    elif variant == 'leave':
        temp = leave_application_list
        val = 2
    else:
        temp = recruitment_application_list
        val = 3
    ans = ""
    if len(temp) == 0:
        return "No data inserted"
    for (x, y) in temp.items():
        # if val == 1:
        ans += f"Name: {x}\n"
        for (key, value) in y.items():
            ans += key.title() + ": " + value + "\n"
        # elif val == 2:
        #     for value in x.values
        ans += "\n"
    print('ent')
    print(ans)
    print('out')
    return ans.strip("\n")

import tkinter as tk

from necessary_function import calculate_pay, save_calculated_pay, highest_paid_employee

FONT_HEADING = ("Arial", 40, "bold")
FONT_SUB_HEADING = ("Arial", 15, "bold")
FONT_BUTTON = ("Arial", 13, "bold")


class PayCalculator:
    def __init__(self):
        self.window = tk.Tk()

        self.window.title("Pay Calculator")
        self.window.minsize(width=900, height=600)
        self.window.config(bg="#DBDFEA")

        # Heading
        self.heading = tk.Label(self.window, text="pay calculator".title(), font=FONT_HEADING,
                                bg='#DBDFEA', fg='#3C486B')
        self.heading.place(x=275, y=40)

        # Name Entry
        self.name_label = tk.Label(self.window, text="Name", font=FONT_SUB_HEADING,
                                   bg='#DBDFEA', fg='#3C486B')
        self.name_label.place(x=260, y=160)
        self.name_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.name_entry.place(x=410, y=160)

        # Hours Worked Entry
        self.hours_worked_label = tk.Label(self.window, text="hours worked".title(), font=FONT_SUB_HEADING,
                                           bg='#DBDFEA', fg='#3C486B')
        self.hours_worked_label.place(x=260, y=200)
        self.hours_worked_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.hours_worked_entry.place(x=410, y=200)

        # # Clock Out Entry
        # self.clock_out_label = tk.Label(self.window, text="Clock Out", font=FONT_SUB_HEADING,
        #                                 bg='#DBDFEA', fg='#3C486B')
        # self.clock_out_label.place(x=260, y=240)
        # self.clock_out_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        # self.clock_out_entry.place(x=365, y=240)

        # Break
        self.break_label = tk.Label(self.window, text="Break", font=FONT_SUB_HEADING,
                                    bg='#DBDFEA', fg='#3C486B')
        self.break_label.place(x=260, y=240)
        self.break_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.break_entry.place(x=410, y=240)

        # Overtime
        self.overtime_label = tk.Label(self.window, text="Overtime", font=FONT_SUB_HEADING,
                                       bg='#DBDFEA', fg='#3C486B')
        self.overtime_label.place(x=260, y=280)
        self.overtime_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.overtime_entry.place(x=410, y=280)

        # Save data button
        self.save_data_button = tk.Button(self.window, text="Save", font=FONT_BUTTON,
                                          fg="#DBDFEA", bg='#3C486B', width=13,
                                          command=self.save_data)
        self.save_data_button.place(x=260, y=320)

        # Calculate Pay Button
        self.calculate_pay_entry = tk.Button(self.window, text="Calculate Pay", font=FONT_BUTTON,
                                             fg="#DBDFEA", bg='#3C486B', width=13,
                                             command=self.calculate_pay)
        self.calculate_pay_entry.place(x=260, y=360)

        # Calculate Best Employee Button
        self.calculate_best_employee_entry = tk.Button(self.window, text="Calculate Best Employee",
                                                       font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                                       width=22, command=self.calculate_highest_paid_employee)
        self.calculate_best_employee_entry.place(x=420, y=360)

        # Result Label
        self.result_label = tk.Label(self.window, text='Result:', font=FONT_SUB_HEADING, bg='#DBDFEA',
                                     fg='#3C486B')
        self.result_label.place(x=330, y=435)

        self.window.mainloop()

    def save_data(self):
        """Calculate the employee's pay"""
        name = self.name_entry.get()
        hours_worked = self.hours_worked_entry.get()
        break_time = self.break_entry.get()
        overtime = self.overtime_entry.get()
        if name != "" and hours_worked != "" and break_time != "" and overtime != "":
            print('hi')
            result = save_calculated_pay(name=name, hours_worked=hours_worked,
                                         break_hrs=break_time, overtime=overtime)
            if result:
                self.show_result(value=result)
        else:
            print('bye')
            print(name != "", hours_worked != "", break_time != "", overtime != "")

    def calculate_pay(self):
        """Calculate employee's pay"""
        name = self.name_entry.get()
        if name != "":
            result = str(calculate_pay(name=name))
        else:
            result = "No data inserted"
        self.show_result(value=result)

    def calculate_highest_paid_employee(self):
        """Calculate highest paid employee"""
        name = highest_paid_employee()
        self.show_result(value=name)

    def show_result(self, value):
        """Show the final result"""
        self.result_label.config(text=f'Result: {value}')

import tkinter as tk

from necessary_function import add_priority_queue, max_priority_queue

FONT_HEADING = ("Arial", 40, "bold")
FONT_SUB_HEADING = ("Arial", 15, "bold")
FONT_BUTTON = ("Arial", 13, "bold")


class PriorityTask:
    def __init__(self):
        self.window = tk.Tk()

        self.window.title("Task Priority")
        self.window.minsize(width=900, height=600)
        self.window.config(bg="#DBDFEA")

        # Heading
        self.heading = tk.Label(self.window, text="Task Priority", font=FONT_HEADING,
                                bg='#DBDFEA', fg='#3C486B')
        self.heading.place(x=275, y=40)

        # Task Entry
        self.task_label = tk.Label(self.window, text="Task", font=FONT_SUB_HEADING,
                                   bg='#DBDFEA', fg='#3C486B')
        self.task_label.place(x=260, y=160)
        self.task_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.task_entry.place(x=365, y=160)

        # Priority Entry
        self.priority_label = tk.Label(self.window, text="priority".title(), font=FONT_SUB_HEADING,
                                       bg='#DBDFEA', fg='#3C486B')
        self.priority_label.place(x=260, y=200)
        self.priority_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.priority_entry.place(x=365, y=200)

        # Save data
        self.save_data_button = tk.Button(self.window, text="Save",
                                          font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                          width=7, command=self.save_data)
        self.save_data_button.place(x=260, y=240)

        # Calculate the highest priority task
        self.highest_priority_task_button = tk.Button(self.window, text="Highest Priority Task",
                                                      font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                                      width=22, command=self.calculate_highest_priority_task)
        self.highest_priority_task_button.place(x=260, y=280)

        # Result Label
        self.result_label = tk.Label(self.window, text='Result:', font=FONT_SUB_HEADING, bg='#DBDFEA',
                                     fg='#3C486B')
        self.result_label.place(x=330, y=335)

        self.window.mainloop()

    def save_data(self):
        """Save data"""
        task = self.task_entry.get()
        priority = self.priority_entry.get()
        if task != "" and priority != "":
            result = add_priority_queue(item=task, priority=priority)
            if result:
                self.show_result(value=result)

    def calculate_highest_priority_task(self):
        """Calculate best employee"""
        highest_priority_task = max_priority_queue()
        self.show_result(value=highest_priority_task)

    def show_result(self, value):
        """Show the final result"""
        self.result_label.config(text=f'Result: {value}')

import tkinter as tk

from necessary_function import recruitment_application, print_data_feedback
from view_data import ViewData

FONT_HEADING = ("Arial", 40, "bold")
FONT_SUB_HEADING = ("Arial", 15, "bold")
FONT_BUTTON = ("Arial", 13, "bold")


class RecruitmentApplication:
    def __init__(self):
        self.data = ""

        self.window = tk.Tk()

        self.window.title("Recruitment Application")
        self.window.minsize(width=900, height=600)
        self.window.config(bg="#DBDFEA")

        # Heading
        self.heading = tk.Label(self.window, text="Recruitment Application", font=FONT_HEADING,
                                bg='#DBDFEA', fg='#3C486B')
        self.heading.place(x=275, y=40)

        # Name Entry
        self.name_label = tk.Label(self.window, text="Name", font=FONT_SUB_HEADING,
                                   bg='#DBDFEA', fg='#3C486B')
        self.name_label.place(x=260, y=160)
        self.name_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.name_entry.place(x=400, y=160)

        # Certifications
        self.certifications_label = tk.Label(self.window, text="Certifications".title(), font=FONT_SUB_HEADING,
                                             bg='#DBDFEA', fg='#3C486B')
        self.certifications_label.place(x=260, y=200)
        self.certifications_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.certifications_entry.place(x=400, y=200)

        # Job Title
        self.job_title_label = tk.Label(self.window, text="Job Title", font=FONT_SUB_HEADING,
                                        bg='#DBDFEA', fg='#3C486B')
        self.job_title_label.place(x=260, y=240)
        self.job_title_entry = tk.Entry(self.window, font=FONT_SUB_HEADING, width=20)
        self.job_title_entry.place(x=400, y=240)

        # Save data
        self.save_entry = tk.Button(self.window, text="Save",
                                    font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                    width=5, command=self.save_data)
        self.save_entry.place(x=260, y=280)

        # View data
        self.view_data_entry = tk.Button(self.window, text="View Data",
                                         font=FONT_BUTTON, fg='#DBDFEA', bg='#3C486B',
                                         width=10, command=self.view_data)
        self.view_data_entry.place(x=260, y=320)

        self.window.mainloop()

    def save_data(self):
        """Save data"""
        name = self.name_entry.get()
        certifications = self.certifications_entry.get()
        job_title = self.job_title_entry.get()

        if name and certifications and job_title:
            recruitment_application(name=name, certifications=certifications, job_title=job_title)

    def view_data(self):
        """View data"""
        self.data = print_data_feedback(variant='recruitment')
        ViewData('Recruitment Applications', self.data)


import tkinter as tk

FONT_HEADING = ("Arial", 40, "bold")
FONT_SUB_HEADING = ("Arial", 15, "bold")


class ViewData:
    def __init__(self, topic, data):
        self.window = tk.Tk()

        self.window.title(f"View {topic}")
        self.window.minsize(width=900, height=600)
        self.window.config(bg="#DBDFEA")

        # Heading
        self.heading = tk.Label(self.window, text=f"View {topic}", font=FONT_HEADING,
                                bg='#DBDFEA', fg='#3C486B')
        self.heading.place(x=150, y=40)

        self.data = tk.Label(self.window, text=data, font=FONT_SUB_HEADING,
                             bg='#DBDFEA', fg='#3C486B')
        self.data.place(x=150, y=160)

        self.window.mainloop()

