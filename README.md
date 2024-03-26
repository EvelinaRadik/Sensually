Вот пример кода, который реализует указанную функциональность:

java
import java.util.*;

class Plane {
    private int id;
    private String name;
    private int productionYear;

    public Plane(int id, String name, int productionYear) {
        this.id = id;
        this.name = name;
        this.productionYear = productionYear;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public int getProductionYear() {
        return productionYear;
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Name: " + name + ", Production Year: " + productionYear;
    }
}

public class Main {
    public static void main(String[] args) {
        List<Plane> planes = new ArrayList<>();
        planes.add(new Plane(1, "Plane1", 2000));
        planes.add(new Plane(2, "Plane2", 2010));
        // Добавить остальные самолеты

        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1) Sort by name");
            System.out.println("2) Sort by production year");
            System.out.println("3) Filter by name");
            System.out.println("4) Filter by production year");
            System.out.println("5) Filter by specific year");
            System.out.println("Enter your choice (1-5): ");

            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    Collections.sort(planes, Comparator.comparing(Plane::getName));
                    break;
                case 2:
                    Collections.sort(planes, Comparator.comparingInt(Plane::getProductionYear));
                    break;
                case 3:
                    System.out.println("Enter name filter: ");
                    String nameFilter = scanner.next();

                    List<Plane> filteredByName = new ArrayList<>();
                    for (Plane plane : planes) {
                        if (plane.getName().contains(nameFilter)) {
                            filteredByName.add(plane);
                        }
                    }
                    planes = filteredByName;
                    break;
                case 4:
                    System.out.println("Enter production year filter: ");
                    int yearFilter = scanner.nextInt();

                    List<Plane> filteredByYear = new ArrayList<>();
                    for (Plane plane : planes) {
                        if (plane.getProductionYear() == yearFilter) {
                            filteredByYear.add(plane);
                        }
                    }
                    planes = filteredByYear;
                    break;
                case 5:
                    System.out.println("Enter specific year: ");
                    int specificYear = scanner.nextInt();

                    List<Plane> filteredBySpecificYear = new ArrayList<>();
                    for (Plane plane : planes) {
                        if (plane.getProductionYear() == specificYear) {
                            filteredBySpecificYear.add(plane);
                        }
                    }
                    planes = filteredBySpecificYear;
                    break;
                default:
                    System.out.println("Invalid choice. Please enter a number from 1 to 5.");
            }

            for (Plane plane : planes) {
                System.out.println(plane);
            }
        }
    }
}


Вы можете добавить остальные самолеты в список planes в методе main. Далее, программное меню предлагает выбор опций сортировки и фильтрации. После выбора опции, список planes выводится с учетом выбранной сортировки или фильтрации. Программа продолжает работу до тех пор, пока не будет прервана пользователем.
