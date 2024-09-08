import re

def password_strength_checker(password):

    length = len(password)
    has_upper = bool(re.search(r'[A-Z]', password))
    has_lower = bool(re.search(r'[a-z]', password))
    has_digit = bool(re.search(r'\d', password))
    has_special = bool(re.search(r'[!@#$%^&*(),.?":{}|<>]', password))


    strength_score = sum([length >= 8, has_upper, has_lower, has_digit, has_special])


    if strength_score == 5:
        return "Very Strong", "Your password meets all the recommended criteria."
    elif strength_score == 4:
        return "Strong", "Your password is strong, but adding more characters or a special character could make it even stronger."
    elif strength_score == 3:
        return "Moderate", "Your password is decent, but it could be improved by adding more character variety and increasing its length."
    elif strength_score == 2:
        return "Weak", "Your password is weak. Consider adding uppercase letters, numbers, and special characters."
    else:
        return "Very Weak", "Your password is very weak. Consider making it longer and including uppercase letters, numbers, and special characters."

def main():
    print("Password Complexity Checker")
    password = input("Enter your password: ").strip()

    strength, feedback = password_strength_checker(password)
    print(f"Password Strength: {strength}")
    print(f"Feedback: {feedback}")

if __name__ == "__main__":
    main()
