# Learning-Activity-2.2
using System;

class Program
{
    static void Main(string[] args)
    {
        LearningActivity22();
    }

    static void LearningActivity22()
    {
        Random rnd = new Random();

        // Simulate 4 dice rolls
        int diceRoll1 = rnd.Next(1, 7);
        int diceRoll2 = rnd.Next(1, 7);
        int diceRoll3 = rnd.Next(1, 7);
        int diceRoll4 = rnd.Next(1, 7);

        // Sum the dice rolls to get the total points
        int totalPoints = diceRoll1 + diceRoll2 + diceRoll3 + diceRoll4;

        Console.WriteLine($"You rolled: {diceRoll1}, {diceRoll2}, {diceRoll3}, {diceRoll4}.");
        Console.WriteLine($"Total skill points available: {totalPoints}");

        // Assign skill points
        int strength = AssignSkillPoints("Strength", ref totalPoints);
        int dexterity = AssignSkillPoints("Dexterity", ref totalPoints);
        int defense = AssignSkillPoints("Defense", ref totalPoints);
        int intelligence = AssignSkillPoints("Intelligence", ref totalPoints);

        // Output final stats
        Console.WriteLine("\nYour final stats:");
        Console.WriteLine($"Strength: {strength}");
        Console.WriteLine($"Dexterity: {dexterity}");
        Console.WriteLine($"Defense: {defense}");
        Console.WriteLine($"Intelligence: {intelligence}");
    }

    static int AssignSkillPoints(string skillName, ref int totalPoints)
    {
        Console.Write($"{skillName} (Remaining points: {totalPoints}): ");

        if (int.TryParse(Console.ReadLine(), out int points) && points <= totalPoints && points >= 0)
        {
            totalPoints -= points;
            return points;
        }
        else
        {
            Console.WriteLine("Invalid input or not enough points. Exiting the program.");
            Environment.Exit(0);
            return 0; // This line will never be reached
        }
    }
}
