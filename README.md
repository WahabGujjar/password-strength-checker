import re

def check_password_strength(password):
    strength = 0
    remarks = ""

    if len(password) < 6:
        remarks = "Password is too short!"
        return strength, remarks

    if len(password) >= 8:
        strength += 1

    if re.search(r"[A-Z]", password) and re.search(r"[a-z]", password):
        strength += 1

    if re.search(r"\d", password):
        strength += 1

    if re.search(r"[@$!%*?&]", password):
        strength += 1

    if strength == 1:
        remarks = "Weak password."
    elif strength == 2:
        remarks = "Medium strength."
    elif strength == 3:
        remarks = "Strong password."
    elif strength == 4:
        remarks = "Very strong password!"
    else:
        remarks = "Very weak password."

    return strength, remarks


if __name__ == "__main__":
    password = input("Enter a password to check strength: ")
    score, feedback = check_password_strength(password)
    print(f"Score: {score}/4 --> {feedback}")

