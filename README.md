# StacksBasicStackOperation
solved task C# Advanced



using System;
using System.Collections.Generic;
using System.Linq;
namespace BasicStackOperations
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] firstLine = Console.ReadLine()                       // read the firstLine Input
                .Split(" ", StringSplitOptions.RemoveEmptyEntries)
                .Select(int.Parse)
                .ToArray();

            if (firstLine.Length != 3)
            {
                Environment.Exit(1);
            }

            int elemNPush = firstLine[0];
            int elemSRemove = firstLine[1];
            int elemXSearch = firstLine[2];

            int[] arr = Console.ReadLine()  // read sec line input
                .Split(" ", StringSplitOptions.RemoveEmptyEntries)
                .Select(int.Parse)
                .ToArray();

            if (arr.Length != elemNPush)
            {
                Environment.Exit(1);
            }

            Stack<int> stack = new Stack<int>();
            stack = FillStack(elemNPush, arr, stack);

            if (elemSRemove <= stack.Count)
            {
               stack = RemoveElementsStack(elemSRemove, stack);
            }

            if (stack.Contains(elemXSearch))
            {
                Console.WriteLine(true.ToString().ToLower());
            }
            else
            {
                if (stack.Count <= 0)
                {
                    Console.WriteLine(0);
                }
                else // there is elements into the stack
                {
                    Console.WriteLine(stack.Min());
                }
            } 
        }

        private static Stack<int> RemoveElementsStack(int elemSRemove, Stack<int> stack)
        {
            for (int i = 0; i < elemSRemove; i++)
            {
                stack.Pop(); 
            }

            return stack;
        }

        private static Stack<int> FillStack(int elemNPush, int[] arr, Stack<int> stack)
        {
            for (int i = 0; i < elemNPush; i++)
            {
                stack.Push(arr[i]);
            }

            return stack;
        }
    }
}
