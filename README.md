using System;

class Calculator
{
    static void Main()
    {
        char choice = 'Y';

        while (choice == 'Y' || choice == 'y')
        {
            Console.WriteLine("Press any following key to perform an arithmetic operation:");
            Console.WriteLine("1 - Addition");
            Console.WriteLine("2 - Subtraction");
            Console.WriteLine("3 - Multiplication");
            Console.WriteLine("4 - Division");

            int operation;
            while (!int.TryParse(Console.ReadLine(), out operation) || operation < 1 || operation > 4)
            {
                Console.Write("Invalid choice. Please enter 1, 2, 3, or 4: ");
            }

            double value1, value2;

            Console.Write("Enter Value 1: ");
            while (!double.TryParse(Console.ReadLine(), out value1))
            {
                Console.Write("Invalid input. Enter a valid number for Value 1: ");
            }

            Console.Write("Enter Value 2: ");
            while (!double.TryParse(Console.ReadLine(), out value2))
            {
                Console.Write("Invalid input. Enter a valid number for Value 2: ");
            }

            double result = 0;
            string symbol = "";

            switch (operation)
            {
                case 1:
                    result = Add(value1, value2);
                    symbol = "+";
                    break;
                case 2:
                    result = Subtract(value1, value2);
                    symbol = "-";
                    break;
                case 3:
                    result = Multiply(value1, value2);
                    symbol = "*";
                    break;
                case 4:
                    if (value2 == 0)
                    {
                        Console.WriteLine("Division by zero is not allowed.");
                        break;
                    }
                    result = Divide(value1, value2);
                    symbol = "/";
                    break;
            }

            if (!(operation == 4 && value2 == 0))
            {
                Console.WriteLine($"{value1} {symbol} {value2} = {result}");
            }

            Console.Write("Do you want to continue again (Y/N)? ");
            choice = Console.ReadKey().KeyChar;
            Console.WriteLine("\n");
        }

        Console.WriteLine("Program terminated. Thank you!");
    }

    // Separate methods for operations
    static double Add(double a, double b)
    {
        return a + b;
    }

    static double Subtract(double a, double b)
    {
        return a - b;
    }

    static double Multiply(double a, double b)
    {
        return a * b;
    }

    static double Divide(double a, double b)
    {
        return a / b;
    }
}
