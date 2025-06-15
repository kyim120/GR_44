# *Online Shopping Cart System*

* ✅ **User input for product details**
* ✅ **Dynamic product creation using a menu**
* ✅ **Repeatable shopping session**
* ✅ **Improved formatting**
* ✅ **Same OOP concepts**: Inheritance, Polymorphism, Encapsulation, Operator Overloading, File Handling

---

### 🧾 Final Menu-Based Version

```cpp
#include <iostream>
#include <vector>
#include <fstream>
using namespace std;

// ======================= Base Class =========================
class Product {
protected:
    string name;
    double basePrice;

public:
    Product(string n = "", double p = 0.0) : name(n), basePrice(p) {}
    virtual double getPrice() const = 0;
    virtual void display() const = 0;
    virtual string getDetails() const = 0;
    virtual ~Product() {}
};

// ======================= Derived Classes =========================

class Electronics : public Product {
    int warranty;
public:
    Electronics(string n, double p, int w) : Product(n, p), warranty(w) {}
    double getPrice() const override { return basePrice + (warranty * 10); }
    void display() const override {
        cout << "📱 Electronics - " << name << " | Price: $" << getPrice()
             << " | Warranty: " << warranty << " months\n";
    }
    string getDetails() const override {
        return "Electronics," + name + "," + to_string(getPrice()) + "," + to_string(warranty) + "\n";
    }
};

class Clothing : public Product {
    string size;
public:
    Clothing(string n, double p, string s) : Product(n, p), size(s) {}
    double getPrice() const override { return basePrice * 1.1; }
    void display() const override {
        cout << "👕 Clothing - " << name << " | Price: $" << getPrice()
             << " | Size: " << size << "\n";
    }
    string getDetails() const override {
        return "Clothing," + name + "," + to_string(getPrice()) + "," + size + "\n";
    }
};

class Grocery : public Product {
    double weight;
public:
    Grocery(string n, double p, double w) : Product(n, p), weight(w) {}
    double getPrice() const override { return basePrice * weight; }
    void display() const override {
        cout << "🍎 Grocery - " << name << " | Price: $" << getPrice()
             << " | Weight: " << weight << " kg\n";
    }
    string getDetails() const override {
        return "Grocery," + name + "," + to_string(getPrice()) + "," + to_string(weight) + "kg\n";
    }
};

// ======================= Shopping Cart =========================

class ShoppingCart {
    vector<Product*> items;

public:
    void operator+(Product* p) {
        items.push_back(p);
    }

    void showCart() const {
        if (items.empty()) {
            cout << "\n🛒 Cart is empty.\n";
            return;
        }

        cout << "\n🛒 Shopping Cart Contents:\n";
        double total = 0;
        for (auto& item : items) {
            item->display();
            total += item->getPrice();
        }
        cout << "💰 Total: $" << total << "\n";
    }

    void saveToFile(string filename = "cart.txt") {
        ofstream outFile(filename);
        for (auto& item : items) {
            outFile << item->getDetails();
        }
        outFile.close();
        cout << "✅ Cart saved to file: " << filename << "\n";
    }

    ~ShoppingCart() {
        for (auto& item : items)
            delete item;
    }
};

// ======================= Main Menu =========================

void displayMenu() {
    cout << "\n========= 🛍 SHOPPING MENU =========\n";
    cout << "1. Add Electronics\n";
    cout << "2. Add Clothing\n";
    cout << "3. Add Grocery\n";
    cout << "4. View Cart\n";
    cout << "5. Save and Exit\n";
    cout << "====================================\n";
    cout << "Choose an option: ";
}

int main() {
    ShoppingCart cart;
    int choice;

    do {
        displayMenu();
        cin >> choice;

        if (cin.fail()) {
            cin.clear();
            cin.ignore(10000, '\n');
            cout << "❌ Invalid input. Try again.\n";
            continue;
        }

        string name, size;
        double price, weight;
        int warranty;

        switch (choice) {
        case 1:
            cout << "Enter name of Electronic item: ";
            cin >> ws;
            getline(cin, name);
            cout << "Enter base price: ";
            cin >> price;
            cout << "Enter warranty (months): ";
            cin >> warranty;
            cart + new Electronics(name, price, warranty);
            break;

        case 2:
            cout << "Enter name of Clothing item: ";
            cin >> ws;
            getline(cin, name);
            cout << "Enter base price: ";
            cin >> price;
            cout << "Enter size (S/M/L): ";
            cin >> size;
            cart + new Clothing(name, price, size);
            break;

        case 3:
            cout << "Enter name of Grocery item: ";
            cin >> ws;
            getline(cin, name);
            cout << "Enter price per kg: ";
            cin >> price;
            cout << "Enter weight (kg): ";
            cin >> weight;
            cart + new Grocery(name, price, weight);
            break;

        case 4:
            cart.showCart();
            break;

        case 5:
            cart.saveToFile();
            cout << "👋 Exiting... Thank you for shopping!\n";
            break;

        default:
            cout << "❌ Invalid choice. Please try again.\n";
        }

    } while (choice != 5);

    return 0;
}
```

---

## ✅ Features Added

| Feature                 | Description                               |
| ----------------------- | ----------------------------------------- |
| ✅ Menu-driven interface | Easy navigation to add/view/save products |
| ✅ Input validation      | Prevents crash on invalid input           |
| ✅ Dynamic product entry | User types name, price, etc.              |
| ✅ Operator overloading  | `cart + new Product(...)`                 |
| ✅ File handling         | Saves cart to `cart.txt`                  |

---

---

### 🖥️ **Sample Console Output**

```
========= 🛍 SHOPPING MENU =========
1. Add Electronics
2. Add Clothing
3. Add Grocery
4. View Cart
5. Save and Exit
====================================
Choose an option: 1
Enter name of Electronic item: Laptop
Enter base price: 1000
Enter warranty (months): 12

========= 🛍 SHOPPING MENU =========
1. Add Electronics
2. Add Clothing
3. Add Grocery
4. View Cart
5. Save and Exit
====================================
Choose an option: 2
Enter name of Clothing item: Jacket
Enter base price: 150
Enter size (S/M/L): L

========= 🛍 SHOPPING MENU =========
1. Add Electronics
2. Add Clothing
3. Add Grocery
4. View Cart
5. Save and Exit
====================================
Choose an option: 3
Enter name of Grocery item: Rice
Enter price per kg: 2
Enter weight (kg): 5

========= 🛍 SHOPPING MENU =========
1. Add Electronics
2. Add Clothing
3. Add Grocery
4. View Cart
5. Save and Exit
====================================
Choose an option: 4

🛒 Shopping Cart Contents:
📱 Electronics - Laptop | Price: $1120 | Warranty: 12 months
👕 Clothing - Jacket | Price: $165 | Size: L
🍎 Grocery - Rice | Price: $10 | Weight: 5 kg
💰 Total: $1295

========= 🛍 SHOPPING MENU =========
1. Add Electronics
2. Add Clothing
3. Add Grocery
4. View Cart
5. Save and Exit
====================================
Choose an option: 5
✅ Cart saved to file: cart.txt
👋 Exiting... Thank you for shopping!
```

---

### 🗃️ Contents of `cart.txt` (after saving)

```
Electronics,Laptop,1120.000000,12
Clothing,Jacket,165.000000,L
Grocery,Rice,10.000000,5kg
```

---
