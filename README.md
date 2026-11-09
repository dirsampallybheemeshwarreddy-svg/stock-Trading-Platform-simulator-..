import java.util.*;

public class StockTradingPlatformSimulator {

    // Custom Exception
    static class InvalidOrderException extends Exception {
        InvalidOrderException(String message) {
            super(message);
        }
    }

    // Abstract Order class
    abstract static class Order {
        private String id;
        private int quantity;
        private double price;

        Order(String id, int quantity, double price)
                throws InvalidOrderException {
            if (quantity <= 0 || price <= 0) {
                throw new InvalidOrderException("Invalid order details!");
            }
            this.id = id;
            this.quantity = quantity;
            this.price = price;
        }

        public String getId() {
            return id;
        }

        public int getQuantity() {
            return quantity;
        }

        public double getPrice() {
            return price;
        }

        public void reduceQuantity(int amount) {
            quantity -= amount;
        }

        abstract String getType();
    }

    // Buy Order
    static class BuyOrder extends Order {
        BuyOrder(String id, int quantity, double price)
                throws InvalidOrderException {
            super(id, quantity, price);
        }

        String getType() {
            return "BUY";
        }
    }

    // Sell Order
    static class SellOrder extends Order {
        SellOrder(String id, int quantity, double price)
                throws InvalidOrderException {
            super(id, quantity, price);
        }

        String getType() {
            return "SELL";
        }
    }

    static ArrayList<BuyOrder> buyOrders = new ArrayList<>();
    static ArrayList<SellOrder> sellOrders = new ArrayList<>();

    // Place Buy Order
    static void placeBuy(String id, int qty, double price)
            throws InvalidOrderException {
        buyOrders.add(new BuyOrder(id, qty, price));
        System.out.println("Buy order placed: " + id);
    }

    // Place Sell Order
    static void placeSell(String id, int qty, double price)
            throws InvalidOrderException {
        sellOrders.add(new SellOrder(id, qty, price));
        System.out.println("Sell order placed: " + id);
    }

    // Match Buy and Sell Orders
    static void matchOrders() {
        buyOrders.sort((a, b) ->
                Double.compare(b.getPrice(), a.getPrice()));

        sellOrders.sort((a, b) ->
                Double.compare(a.getPrice(), b.getPrice()));

        System.out.println("\n--- Trade Execution ---");

        for (BuyOrder buy : buyOrders) {
            for (SellOrder sell : sellOrders) {

                if (buy.getQuantity() > 0 &&
                    sell.getQuantity() > 0 &&
                    buy.getPrice() >= sell.getPrice()) {

                    int traded = Math.min(
                            buy.getQuantity(), sell.getQuantity());

                    System.out.println(
                        traded + " shares traded at Rs."
                        + sell.getPrice());

                    buy.reduceQuantity(traded);
                    sell.reduceQuantity(traded);
                }
            }
        }
    }

    // Display Order Book
    static void displayOrders() {
        System.out.println("\n--- Remaining Buy Orders ---");

        for (BuyOrder b : buyOrders) {
            if (b.getQuantity() > 0) {
                System.out.println(b.getId() + " | Quantity: "
                        + b.getQuantity() + " | Price: Rs."
                        + b.getPrice());
            }
        }

        System.out.println("\n--- Remaining Sell Orders ---");

        for (SellOrder s : sellOrders) {
            if (s.getQuantity() > 0) {
                System.out.println(s.getId() + " | Quantity: "
                        + s.getQuantity() + " | Price: Rs."
                        + s.getPrice());
            }
        }
    }

    public static void main(String[] args) {
        try {
            System.out.println("STOCK TRADING PLATFORM");

            placeBuy("B1", 10, 100);
            placeSell("S1", 5, 95);
            placeSell("S2", 8, 98);

            matchOrders();
            displayOrders();

        } catch (InvalidOrderException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
