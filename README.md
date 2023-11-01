# restaurant-menu
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class MenuItem {
    private String name;
    private double price;

    public MenuItem(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }
}

class RestaurantMenu {
    private List<MenuItem> menuItems;

    public RestaurantMenu() {
        menuItems = new ArrayList<>();
    }

    public void addItem(String name, double price) {
        MenuItem newItem = new MenuItem(name, price);
        menuItems.add(newItem);
    }

    public void displayMenu() {
        System.out.println("Restaurant Menu:");
        for (int i = 0; i < menuItems.size(); i++) {
            MenuItem item = menuItems.get(i);
            System.out.println((i + 1) + ". " + item.getName() + " - $" + item.getPrice());
        }
    }

    public MenuItem getItem(int index) {
        if (index >= 0 && index < menuItems.size()) {
            return menuItems.get(index);
        }
        return null;
    }
}

public class RestaurantApp {
    public static void main(String[] args) {
        RestaurantMenu menu = new RestaurantMenu();
        
        // Add menu items
        menu.addItem("Spaghetti", 12.99);
        menu.addItem("Burger", 9.99);
        menu.addItem("Salad", 8.49);
        menu.addItem("Pizza", 14.99);
        
        Scanner scanner = new Scanner(System.in);
        
        while (true) {
            menu.displayMenu();
            
            System.out.println("Enter the number of the item you want to order (0 to exit):");
            int choice = scanner.nextInt();
            
            if (choice == 0) {
                System.out.println("Thank you for ordering. Enjoy your meal!");
                break;
            } else {
                MenuItem selectedItem = menu.getItem(choice - 1);
                if (selectedItem != null) {
                    System.out.println("You ordered: " + selectedItem.getName() + " - $" + selectedItem.getPrice());
                } else {
                    System.out.println("Invalid selection. Please try again.");
                }
            }
        }
        
        scanner.close();
    }
}
