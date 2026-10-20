# DotNet_Assignment_3
using System;

namespace ExceptionHandlingAssignment
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("=== TASK 3: SYSTEM & APPLICATION EXCEPTIONS ===\n");

            // ==========================================
            // 1. SYSTEM EXCEPTION (Built-in .NET Exception)
            // ==========================================
            Console.WriteLine("--- Testing System Exception ---");
            try
            {
                int numerator = 10;
                int denominator = 0; // This will trigger a built-in system exception
                int result = numerator / denominator;
                Console.WriteLine("Result: " + result);
            }
            catch (DivideByZeroException ex)
            {
                Console.WriteLine("[System Exception Caught]: Cannot divide by zero!");
                Console.WriteLine("Error Message: " + ex.Message);
            }


            // ==========================================
            // 2. APPLICATION / CUSTOM EXCEPTION
            // ==========================================
            Console.WriteLine("\n--- Testing Application (Custom) Exception ---");
            try
            {
                int userAge = 15; // Too young, will trigger our custom exception
                ValidateUserAge(userAge);
            }
            catch (InvalidAgeException ex)
            {
                Console.WriteLine("[Application Exception Caught]: Custom rule violated.");
                Console.WriteLine("Error Message: " + ex.Message);
            }
            finally
            {
                Console.WriteLine("\n--- Finally Block ---");
                Console.WriteLine("Exception handling demonstration finished execution.");
            }
        }

        // Method that checks age and throws a custom Application Exception
        static void ValidateUserAge(int age)
        {
            if (age < 18)
            {
                // Creating and throwing our own Application Exception
                throw new InvalidAgeException($"Access denied. Age {age} is below the minimum requirement of 18.");
            }
            Console.WriteLine("Access granted! Age is valid.");
        }
    }

    // Custom Application Exception class (inherits from the base Exception class)
    public class InvalidAgeException : Exception
    {
        public InvalidAgeException(string message) : base(message)
        {
        }
    }
}
