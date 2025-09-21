# ipl_ticket_booking
import random
import string

teams = {
    "CSK": {"stadium": "M. A. Chidambaram Stadium", "ticket_prices": {"premium": 2000, "vip": 1500, "basic": 800}},
    "MI": {"stadium": "Wankhede Stadium", "ticket_prices": {"premium": 2200, "vip": 1600, "basic": 1000}},
    "RCB": {"stadium": "M. Chinnaswamy Stadium", "ticket_prices": {"premium": 1800, "vip": 1300, "basic": 900}},
    "KKR": {"stadium": "Eden Gardens", "ticket_prices": {"premium": 1900, "vip": 1400, "basic": 850}},
    "RR": {"stadium": "Sawai Mansingh Stadium", "ticket_prices": {"premium": 1700, "vip": 1200, "basic": 850}},
    "DC": {"stadium": "Arun Jaitley Stadium", "ticket_prices": {"premium": 2000, "vip": 1500, "basic": 800}},
    "PBKS": {"stadium": "PCA Stadium", "ticket_prices": {"premium": 2100, "vip": 1550, "basic": 850}},
    "SRH": {"stadium": "Rajiv Gandhi International Cricket Stadium", "ticket_prices": {"premium": 1900, "vip": 1350, "basic": 900}},
    "LSG": {"stadium": "EKANA Stadium", "ticket_prices": {"premium": 1950, "vip": 1450, "basic": 900}},
    "GG": {"stadium": "Narendra Modi Stadium", "ticket_prices": {"premium": 1850, "vip": 1250, "basic": 800}}
}

# Define payment methods
payment_methods = ["PhonePay", "GooglePay", "NetBanking"]

def generate_ticket_number():
    ticket_number = ''.join(random.choices(string.ascii_uppercase + string.digits, k=6))
    return ticket_number

def display_teams():
    print("Select a team to watch the match:")
    for index, team in enumerate(teams.keys(), start=1):
        print(f"{index}. {team}")

def select_stadium(team):
    print(f"\nYou've selected {team}.")
    print(f"The match will be played at {teams[team]['stadium']}.")
    print("\nSelect your ticket type:")
    for ticket_type, price in teams[team]['ticket_prices'].items():
        print(f"{ticket_type.capitalize()}: ${price}")

    ticket_type = input("Enter your ticket type (premium/vip/basic): ").lower()
    while ticket_type not in teams[team]['ticket_prices']:
        print("Invalid ticket type. Please try again.")
        ticket_type = input("Enter your ticket type (premium/vip/basic): ").lower()

    return ticket_type

def select_payment_method():
    print("\nSelect your payment method:")
    for index, method in enumerate(payment_methods, start=1):
        print(f"{index}. {method}")

    choice = input("Enter your choice: ")
    while not choice.isdigit() or int(choice) < 1 or int(choice) > len(payment_methods):
        print("Invalid choice. Please enter a valid number.")
        choice = input("Enter your choice: ")

    return payment_methods[int(choice) - 1]

def main():
    print("Welcome to IPL Ticket Booking System!\n")
    display_teams()

    team_choice = int(input("Enter the number of the team you want to watch: "))
    while team_choice < 1 or team_choice > len(teams):
        print("Invalid team number. Please try again.")
        team_choice = int(input("Enter the number of the team you want to watch: "))

    team = list(teams.keys())[team_choice - 1]
    ticket_type = select_stadium(team)

    print("\nYou've selected the ticket type:", ticket_type.capitalize())

    payment_method = select_payment_method()
    print("\nYou've selected the payment method:", payment_method)

    ticket_number = generate_ticket_number()
    print("\nYour ticket has been booked successfully!")
    print("Ticket Number:", ticket_number)

if name == "main":
    main()
