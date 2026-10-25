# Insurance_estimator
A simple Python program that estimates life insurance premium.
plans = {"term": 1.0, "whole life": 1.8, "endowment": 2.4}
 
print("--- Insurance Premium Estimator ---")
 
again = "yes"
while again == "yes":
    name = input("Enter name: ")
    age = int(input("Enter age: "))
 
    if age < 18 or age > 65:
        print("Sorry, we insure only ages 18 to 65.")
    else:
        smoker = input("Do you smoke? (yes/no): ")
        coverage = int(input("Enter coverage amount in Rs.: "))
        plan = input("Choose plan (term / whole life / endowment): ")
 
        # step 1: rate per Rs. 1000 of coverage, depends on age
        if age <= 30:
            rate = 1.2
        elif age <= 40:
            rate = 1.8
        elif age <= 50:
            rate = 3.0
        else:
            rate = 5.2
 
        # step 2: basic premium
        premium = coverage / 1000 * rate
 
        # step 3: smokers pay 50% more
        if smoker == "yes":
            premium = premium * 1.5
 
        # step 4: plan type changes the price
        if plan in plans:
            premium = premium * plans[plan]
            print("Yearly premium for", name, "is Rs.", premium)
            print("Monthly premium is about Rs.", round(premium / 12, 2))
        else:
            print("Wrong plan name, please try again.")
 
    again = input("Check another customer? (yes/no): ")
 
print("Thank you!")
