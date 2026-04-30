package app;

import java.util.Scanner;

public class Main {
    public static void printMenu() {
        System.out.println("\n===== MENU =====");
        System.out.println("1. Add employee");
        System.out.println("2. Add cooperation");
        System.out.println("3. Remove employee");
        System.out.println("4. Find employee by ID");
        System.out.println("5. Run employee skill");
        System.out.println("6. Print employees alphabetically by groups");
        System.out.println("7. Print statistics");
        System.out.println("8. Print number of employees in groups");
        System.out.println("9. Save one employee to text file");
        System.out.println("10. Load all employees from text file");
        System.out.println("11. Save all employees to SQL");
        System.out.println("12. Load all employees from SQL");
        System.out.println("0. Exit");
        System.out.print("Choose: ");
    }

    public static void main(String[] args) {
        DatabaseManager.initializeDatabase();

        Scanner scanner = new Scanner(System.in);
        EmployeeDatabase database = new EmployeeDatabase();

        boolean loadedFromSql = database.loadAllFromSQL();
        if (!loadedFromSql) {
            database.loadAllFromFile("employees.txt");
        }

        int choice;

        do {
            printMenu();

            while (!scanner.hasNextInt()) {
                System.out.println("Please enter a valid number.");
                scanner.next();
            }

            choice = scanner.nextInt();
            scanner.nextLine();

            switch (choice) {
                case 1:
                    try {
                        System.out.print("Employee type (1 = DataAnalyst, 2 = SecuritySpecialist): ");
                        int type = Integer.parseInt(scanner.nextLine());

                        System.out.print("First name: ");
                        String firstName = scanner.nextLine();

                        System.out.print("Last name: ");
                        String lastName = scanner.nextLine();

                        System.out.print("Birth year: ");
                        int birthYear = Integer.parseInt(scanner.nextLine());

                        database.addEmployee(type, firstName, lastName, birthYear);
                    } catch (NumberFormatException e) {
                        System.out.println("Invalid input.");
                    }
                    break;

                case 2:
                    try {
                        System.out.print("Employee ID: ");
                        int id1 = Integer.parseInt(scanner.nextLine());

                        System.out.print("Colleague ID: ");
                        int id2 = Integer.parseInt(scanner.nextLine());

                        System.out.print("Cooperation level (0 = BAD, 1 = AVERAGE, 2 = GOOD): ");
                        int levelInt = Integer.parseInt(scanner.nextLine());

                        CooperationLevel level = CooperationLevel.fromInt(levelInt);
                        database.addCooperation(id1, id2, level);
                    } catch (Exception e) {
                        System.out.println("Invalid input.");
                    }
                    break;

                case 3:
                    try {
                        System.out.print("Employee ID to remove: ");
                        int removeId = Integer.parseInt(scanner.nextLine());
                        database.removeEmployee(removeId);
                    } catch (NumberFormatException e) {
                        System.out.println("Invalid input.");
                    }
                    break;

                case 4:
                    try {
                        System.out.print("Employee ID: ");
                        int findId = Integer.parseInt(scanner.nextLine());
                        database.printEmployeeById(findId);
                    } catch (NumberFormatException e) {
                        System.out.println("Invalid input.");
                    }
                    break;

                case 5:
                    try {
                        System.out.print("Employee ID: ");
                        int skillId = Integer.parseInt(scanner.nextLine());
                        database.runEmployeeSkill(skillId);
                    } catch (NumberFormatException e) {
                        System.out.println("Invalid input.");
                    }
                    break;

                case 6:
                    database.printAlphabeticallyByGroups();
                    break;

                case 7:
                    database.printStatistics();
                    break;

                case 8:
                    database.printGroupCounts();
                    break;

                case 9:
                    try {
                        System.out.print("Employee ID: ");
                        int saveId = Integer.parseInt(scanner.nextLine());
                        database.saveOneEmployeeToFile(saveId, "one_employee.txt");
                    } catch (NumberFormatException e) {
                        System.out.println("Invalid input.");
                    }
                    break;

                case 10:
                    database.loadAllFromFile("employees.txt");
                    break;

                case 11:
                    database.saveAllToSQL();
                    break;

                case 12:
                    database.loadAllFromSQL();
                    break;

                case 0:
                    database.saveAllToSQL();
                    database.saveAllToFile("employees.txt");
                    System.out.println("Program ended. Data saved.");
                    break;

                default:
                    System.out.println("Invalid choice.");
            }

        } while (choice != 0);

        scanner.close();
    }
}
