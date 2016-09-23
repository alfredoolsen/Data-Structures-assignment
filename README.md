# Data-Structures-assignment
//Student: Alfredo Olsen
//Program description:
//Create a new C# Console Application. In the Main function, add a new variable of type Queue that contains items of type string.
//Create a variable for a Queue with items of type string
//This variable will represent your line of customers waiting outside.
//Create a variable for a Dictionary with keys of type string and values of type int.
//This variable will hold information about each customer
//Put 100 customers into the queue
//You can use the randomName function below to generate random people for your line
//Add a random number of burgers to the total for each customer. Make sure there is a key in the dictionary for each customer before you try incrementing their total!
//Print out each customer and their total burgers eaten.

using       System;
using       System.Collections.Generic;
using       System.Linq;
using       System.Text;
using       System.Threading.Tasks;

namespace   Data_Structures_basic_assignment
{
    class Program
    {
        // creating the 'random' constructor 
        public static Random random = new Random();

        public static string randomName()
        {
            string[] names = new string[8] { "Dan Morain", "Emily Bell", "Carol Roche", "Ann Rose", "John Miller", "Greg Anderson", "Arthur McKinney", "Joann Fisher" };
            // the 7 is there 
            int randomIndex = Convert.ToInt32(random.NextDouble() * 7);
            return names[randomIndex];
        }

        public static int randomNumberInRange()
        {
            return Convert.ToInt32(random.NextDouble() * 20);
        }

        static void Main(string[] args)
        {
            Queue<string> myQueue = new Queue<string>();

            // key: string, value: int

            // create new Dictionary
            Dictionary<string, int> myDictionary = new Dictionary<string, int>();
          
            while (myQueue.Count < 100) {
                myQueue.Enqueue(randomName());
            }

            int iHamburg = 0; 
 
            foreach (string person in myQueue )
            {
                // add entries to Dictionary
                iHamburg = randomNumberInRange();
                if (myDictionary.ContainsKey(person))
                {
                    //this adds a random number of hambugers for the same person
                    myDictionary[person] += iHamburg;
                }

                else
                {
                    myDictionary.Add(person, iHamburg);
                }
            }
                
            // this is just displaying each value in the dictionary

            foreach (KeyValuePair<String, int> Cust in myDictionary)
            {
                Console.WriteLine(Cust.Key + "\t\t\t" + Cust.Value);
            }
            Console.ReadKey();
        }
                 
    }
}
