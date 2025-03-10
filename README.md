# SCT_SC_3
import re

def assess_password_strength(password):
    # Define criteria
    length_criteria = len(password) >= 8
    uppercase_criteria = re.search(r'[A-Z]', password)
    lowercase_criteria = re.search(r'[a-z]', password)
    letter_criteria = re.search(r'[A-Za-z]', password)
    number_criteria = re.search(r'[0-9]', password)
    special_char_criteria = re.search(r'[!@#$%^&*(),.?":{}|<>]', password)
    
    # Calculate score
    score = 0
    if length_criteria:
        score += 1
    if uppercase_criteria:
        score += 1
    if lowercase_criteria:
        score += 1
    if letter_criteria:
        score += 1
    if number_criteria:
        score += 1
    if special_char_criteria:
        score += 1
    
    # Assess strength
    if score == 6 and len(password) >= 12:
        strength = "Very Strong"
    elif score >= 5:
        strength = "Strong"
    elif score >= 4:
        strength = "Moderate"
    else:
        strength = "Weak"
    
    # Output detailed results
    print(f"\nPassword Strength: {strength}")
    print("\nDetailed Criteria Check:")
    print(f"- Length: {'OK' if length_criteria else 'Too Short'}")
    print(f"- Uppercase: {'OK' if uppercase_criteria else 'Missing'}")
    print(f"- Lowercase: {'OK' if lowercase_criteria else 'Missing'}")
    print(f"- Letter (Any Case): {'OK' if letter_criteria else 'Missing'}")
    print(f"- Numbers: {'OK' if number_criteria else 'Missing'}")
    print(f"- Special Characters: {'OK' if special_char_criteria else 'Missing'}")

    # Suggestions for improvement
    print("\nSuggestions for Improvement:")
    if not length_criteria:
        print("- Use at least 8 characters.")
    if not uppercase_criteria:
        print("- Include uppercase letters.")
    if not lowercase_criteria:
        print("- Include lowercase letters.")
    if not letter_criteria:
        print("- Include at least one letter.")
    if not number_criteria:
        print("- Include numbers.")
    if not special_char_criteria:
        print("- Include special characters.")
        
# Get user input
password = input("Enter a password to assess: ")
assess_password_strength(password)
