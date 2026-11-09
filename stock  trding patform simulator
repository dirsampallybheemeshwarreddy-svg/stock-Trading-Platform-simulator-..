import java.io.FileWriter;
import java.io.IOException;

public class StockTradingPlatformSimulator {

    public static void main(String[] args) {

        String readme =
            "# Stock Trading Platform Simulator (Zerodha Style)\n\n" +

            "## Project Overview\n\n" +
            "Stock Trading Platform Simulator is a Java-based " +
            "application that simulates stock trading operations. " +
            "It allows users to place Buy and Sell orders and " +
            "automatically matches orders based on price priority.\n\n" +

            "## Features\n\n" +
            "- **User & Stock Order Input:** Place Buy and Sell orders.\n" +
            "- **Order Book Display:** Displays Buy and Sell orders.\n" +
            "- **Trade Matching Algorithm:** Matches orders when " +
            "Buy Price is greater than or equal to Sell Price.\n" +
            "- **Order Management:** Maintains active trading orders.\n" +
            "- **Exception Handling:** Handles invalid order details.\n\n" +

            "## Java & OOP Concepts Used\n\n" +
            "- **Abstraction:** Uses an abstract Order class.\n" +
            "- **Inheritance:** BuyOrder and SellOrder extend Order.\n" +
            "- **Encapsulation:** Uses private variables and getters.\n" +
            "- **Collections Framework:** Uses ArrayList.\n" +
            "- **Exception Handling:** Uses custom exceptions.\n\n" +

            "## Tech Stack\n\n" +
            "- **Programming Language:** Java\n" +
            "- **IDE:** Eclipse / IntelliJ IDEA\n" +
            "- **Platform:** Java Application\n";

        try {
            FileWriter writer =
                new FileWriter("README.md");

            writer.write(readme);
            writer.close();

            System.out.println(
                "====================================");
            System.out.println(
                " STOCK TRADING PLATFORM SIMULATOR");
            System.out.println(
                "====================================");
            System.out.println();
            System.out.println("Project README created successfully!");
            System.out.println("File Name: README.md");
            System.out.println();
            System.out.println("Project Sections:");
            System.out.println("1. Project Overview");
            System.out.println("2. Features");
            System.out.println("3. Java & OOP Concepts Used");
            System.out.println("4. Tech Stack");
            System.out.println();
            System.out.println("====================================");

        } catch (IOException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
