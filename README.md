# mohith
expense tracker
expenses = []

def menu():
    print("\n--- Expense Tracker ---")
    print("1. Add Expense")
    print("2. View Expenses")
    print("3. Total Expense")
    print("4. Category Wise Expense")
    print("5. Exit")


def add_expense():
    category = input("Enter category: ")
    amount = float(input("Enter amount: "))

    expense = {
        "category": category,
        "amount": amount
    }

    expenses.append(expense)
    print("✅ Expense Added Successfully")


def view_expenses():
    if not expenses:
        print("No expenses found")
        return

    print("\nCategory\tAmount")
    for e in expenses:
        print(e["category"], "\t\t", e["amount"])


def total_expense():
    total = 0
    for e in expenses:
        total += e["amount"]

    print("💰 Total Expense:", total)


def category_wise():
    summary = {}

    for e in expenses:
        cat = e["category"]
        amt = e["amount"]

        if cat in summary:
            summary[cat] += amt
        else:
            summary[cat] = amt

    print("\nCategory Wise Expense:")
    for cat, amt in summary.items():
        print(cat, ":", amt)


while True:
    menu()
    choice = input("Enter your choice: ")

    if choice == "1":
        add_expense()
    elif choice == "2":
        view_expenses()
    elif choice == "3":
        total_expense()
    elif choice == "4":
        category_wise()
    elif choice == "5":
        print("Thank you 👋")
        break
    else:
        print("❌ Invalid choice")

