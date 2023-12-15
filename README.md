# Function4
def calculate_pay_rate(job_code):
    if job_code == 'L':
        return 25.00
    elif job_code == 'A':
        return 30.00
    elif job_code == 'J':
        return 50.00
    else:
        return 0.0

def calculate_gross_pay(hours_worked, pay_rate):
    regular_hours = min(hours_worked, 40)
    overtime_hours = max(hours_worked - 40, 0)
    return (regular_hours * pay_rate) + (overtime_hours * 1.5 * pay_rate)

def main():
    total_gross_pay = 0.0

    try:
        while True:
            # User input for employee information
            last_name = input("Enter employee's last name (Ctrl+Z to stop): ")
            job_code = input("Enter job code (L, A, J): ")
            hours_worked = float(input("Enter hours worked: "))

            # Calculate pay rate and gross pay
            pay_rate = calculate_pay_rate(job_code)
            gross_pay = calculate_gross_pay(hours_worked, pay_rate)

            # Display last name and gross pay
            print(f"{last_name}'s Gross Pay: ${gross_pay:.2f}")

            # Update total gross pay
            total_gross_pay += gross_pay

    except EOFError:
        # Display the total of all gross pay
        print(f"\nTotal Gross Pay: ${total_gross_pay:.2f}")

if __name__ == "__main__":
    main()
