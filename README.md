# ArrayList-
Creating ArrayList, inserting and modifying Values

import java.util.ArrayList;
import java.util.Scanner;

import static java.lang.System.in;

public class GroceryList {

    private ArrayList<String> groceryList = new ArrayList<String>();
    private static Scanner myScanner = new Scanner(in);

    public void addGroceryItems(String item) {
        groceryList.add(item);
    }

    public void printGroceryList(){
        System.out.println("You have " + groceryList.size() + " items in your grocery list");
        for (int i = 0; i < groceryList.size(); i++) {
            System.out.println((i+1) + ". " + groceryList.get(i));
        }
    }

    public void modifyGroceryItems(int position, String newItem) {
        groceryList.set(position, newItem);
        System.out.println("Grocery list " + (position+1) + " has been modified");
    }

    public void removeGroceryList(int position) {
        String theItem = groceryList.get(position);
        groceryList.remove(position);
    }

    public String findItems(String search) {
        boolean isAvailable = groceryList.contains(search);
        // System.out.println(search + "is available in the grocery list");
        int isIndex = groceryList.indexOf(search);
        if(isIndex >=0) {
            return groceryList.get(isIndex);
        }
        return null;
    }
}

import java.util.Scanner;

import static java.lang.System.in;

public class Main {
    private static Scanner isScanner = new Scanner(in);
    static GroceryList myGrocery = new GroceryList();

    public static void printOptionList(){
        System.out.println("Press : ");
        System.out.println("press 0 to show Menu ");
        System.out.println("press 1 to add grocery items ");
        System.out.println("press 2 to print grocery items ");
        System.out.println("press 3 to modify grocery items ");
        System.out.println("press 4 to remove grocery items ");
        System.out.println("press 5 to find grocery items ");
        System.out.println("press 6 to quit application ");
    }

    public static void addItems(){
        System.out.println("Please add grocery items");
        String addItemNow = isScanner.nextLine();
        myGrocery.addGroceryItems(addItemNow);
        System.out.println(addItemNow + " has been added to the grocery list");
    }

    public static void printItemsList() {
        myGrocery.printGroceryList();
    }

    public static void modifyItems() {
        System.out.println("Enter item Number ");
        int toModify = isScanner.nextInt();
        isScanner.nextLine();
        System.out.println("Put new item name");
        String itemName = isScanner.nextLine();
        myGrocery.modifyGroceryItems(toModify - 1, itemName);
    }

    public static void removeItems(){
        System.out.println("press item to be removed");
        int toRemove = isScanner.nextInt();
        myGrocery.removeGroceryList(toRemove-1);
        System.out.println("Item " + toRemove + " successfully removed ");
    }

    public static void findItem() {
        System.out.println("please type item you want to find");
        String itemToFind = isScanner.nextLine();
        String check = myGrocery.findItems(itemToFind);
        if (check != null) {
            System.out.println(itemToFind + " found in grocery list");
        } else {
            System.out.println(itemToFind + " not in grocery list");
        }
    }


    public static void main (String[] args) {
       printOptionList();
        boolean quit = false;
        int inputChoice = 0;

        while(!quit) {
            System.out.println("Enter your choice ");
            inputChoice = isScanner.nextInt();
            isScanner.nextLine();


            switch (inputChoice) {
                case 0: printOptionList();
                break;
                case 1: addItems();
                break;
                case 2: printItemsList();
                break;
                case 3: modifyItems();
                break;
                case 4: removeItems();
                break;
                case 5: findItem();
                break;
                case 6: quit = true;
                break;
                default:
                    System.out.println("Invalid option!");
                    break;
            }
        }
    }
}
