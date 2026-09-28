class Student:
    def __init__(self, name, surname, gender):
        self.name = name
        self.surname = surname
        self.gender = gender
        self.finished_courses = []
        self.courses_in_progress = []
        self.grades = {}

    def rate_lecture(self, lector, course, grade):
        if not isinstance(lecturer, Lecturer):
            return 'Ошибка'
        if course not in self.courses_in_progress or course not in lecturer.courses_attached:
            return 'Ошибка'
        if not (isinstance(grade, int) and 1 <= grade <= 10):
            return 'Ошибка'
        lecturer.grades.setdefault(course, []).append(grade)
    def __str__(self):
        return f'{self.name} {self.surname} {self.grades} {self.courses_in_progress} {self.finished_courses}'






class Mentor:
    def __init__(self, name, surname):
        self.name = name
        self.surname = surname
        self.courses_attached = []


class Lecturer(Mentor):
    def __init__(self, name, surname):
        super().__init__(name, surname)
        self.grades = {}
    def __str__(self):
        return f'{self.name} {self.surname} {self.grades}'



class Reviewer(Mentor):
    def __init__(self, name, surname):
        super().__init__(name, surname)
    def rate_lecture(self, lector, course, grade):
        if (isinstance(student, Student)
                and course in self.courses_attached
                and course in student.courses_in_progress
                and isinstance(grade, int) and 1 <= grade <= 10):
            student.grades.setdefault(course, []).append(grade)
        else:
            return 'Ошибка'
    def __str__(self):
        return f'{self.name} {self.surname}


lecturer = Lecturer('Иван', 'Иванов')
reviewer = Reviewer('Петр', 'Петров')
student = Student('Алехина', 'Ольга', 'Ж')
student.courses_in_progress += ['Python', 'Java']
lecturer.courses_attached += ['Python', 'C++']
reviewer.courses_attached += ['Python', 'C++']
print(student.rate_lecture(lecturer, 'Python', 7))
print(student.rate_lecture(lecturer, 'Java', 8))
print(student.rate_lecture(lecturer, 'C++', 8))
print(student.rate_lecture(lecturer, 'Python', 6))

print(lecturer.grades)  # {'Python': [7]}


# best_student = Student('Ruoy', 'Eman',21)
# best_student.finished_courses += ['Git']
# best_student.courses_in_progress += ['Python']
# best_student.grades['Git'] = [10, 10, 10, 10]
# best_student.grades['Pyton'] = [10, 10]
# print(best_student.finished_courses)
# print(best_student.courses_in_progress)
# print(best_student.grades)
# print(isinstance(lecture, Mentor))

# cool_mentor = Mentor('Some', 'Buddy')
# cool_mentor.courses_attached += ['Pyton']
# print(cool_mentor.courses_attached)

# print(isinstance(lecturer, Mentor))
# print(isinstance(reviewer, Mentor))
# print(lecturer.courses_attached)
# print(reviewer.courses_attached)
