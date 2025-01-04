# Restaurant Billing System

## Objetive
[Brief Objetive]

Develop a Python-based billing system that simulates a restaurant menu ordering process, calculates the subtotal, applies tax, and provides a summarized total, while ensuring accurate data handling and a user-friendly interface.

### Skills Learned
[Bullet Points]

- Python Programming: Implemented functions, loops, and conditionals to create a functional billing system.
- Data Handling: Managed menu data using dictionaries and lists for efficient storage and retrieval.
- Modular Code Design: Developed modular functions for calculating subtotals, tax, and order summaries, promoting reusability and clarity.
- User Input Handling: Created a dynamic interface to take user input and validate it effectively.
- Mathematical Operations: Performed precise calculations with rounding for financial accuracy.

#### Tools Used
[Bullet Points]

- Python
- Visual Studio Code

##### Code

    menu = {
        1: {"name": 'espresso', "price": 1.99},
        2: {"name": 'coffee', "price": 2.50},
        3: {"name": 'cake', "price": 2.79},
        4: {"name": 'soup', "price": 4.50},
        5: {"name": 'sandwich', "price": 4.99},
    }
    
    def calculate_subtotal(order):
        """Calculates the subtotal of an order."""
        print('Calculating bill subtotal...')
        subtotal = sum(item["price"] for item in order)
        return round(subtotal, 2)
    
    def calculate_tax(subtotal):
        """Calculates the tax of an order."""
        print('Calculating tax from subtotal...')
        tax = round(subtotal * 0.15, 2)
        return tax
    
    def summarize_order(order):
        """Summarizes the order."""
        names = [item["name"] for item in order]
        subtotal = calculate_subtotal(order)
        tax = calculate_tax(subtotal)
        total = round(subtotal + tax, 2)
        return names, total
    
    def print_order(order):
        """Prints the items in the order."""
        print('You have ordered ' + str(len(order)) + ' items')
        items = [item["name"] for item in order]
        print(items)
    
    def display_menu():
        """Displays the menu."""
        print("------- Menu -------")
        for selection in menu:
            print(f"{selection}. {menu[selection]['name'] : <9} | {menu[selection]['price'] : >5}")
        print()
    
    def take_order():
        """Prompts the user to create an order."""
        display_menu()
        order = []
        for count in range(1, 4):
            item_num = int(input(f'Select menu item number {count} (from 1 to 5): '))
            if item_num in menu:
                order.append(menu[item_num])
            else:
                print("Invalid selection. Please try again.")
        return order
    
    def main():
        """Main function to run the program."""
        order = take_order()
        print_order(order)
    
        subtotal = calculate_subtotal(order)
        print("Subtotal for the order is: $" + str(subtotal))
    
        tax = calculate_tax(subtotal)
        print("Tax for the order is: $" + str(tax))
    
        items, total = summarize_order(order)
        print(f"Items in the order: {items}")
        print(f"Total for the order is: ${total}")
    
    if __name__ == "__main__":
        main()


