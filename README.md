class Question:
    def __init__(self, text, answer, choices=None):
        self.text = text
        self.answer = answer
        self.choices = choices

    def check_answer(self, user_answer):
        return user_answer.lower() == self.answer.lower()


class Quiz:
    def __init__(self):
        self.questions = []
        self.score = 0

    def add_question(self, question):
        self.questions.append(question)

    def display_question(self, question):
        print(question.text)
        if question.choices:
            for i, choice in enumerate(question.choices):
                print(f"{i + 1}. {choice}")

    def play(self):
        print("Welcome to the Quiz Game!")
        print("--------------------------")

        for question in self.questions:
            self.display_question(question)
            user_answer = input("Your answer: ")

            if question.check_answer(user_answer):
                print("Correct!")
                self.score += 1
            else:
                print("Incorrect!")

            print()

        print(f"Quiz completed! Your score: {self.score}/{len(self.questions)}")


# Create a Quiz object
quiz = Quiz()

# Add questions to the quiz
question1 = Question("What is the capital of France?", "Paris")
quiz.add_question(question1)

question2 = Question("Which planet is known as the Red Planet?", "Mars")
quiz.add_question(question2)

question3 = Question("What is the largest ocean in the world?", "Pacific")
quiz.add_question(question3)

# Play the quiz
quiz.play()
