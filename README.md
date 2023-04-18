# Ladybug-SoftUni
The worst thing ever
using Microsoft.Win32.SafeHandles;
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data.SqlTypes;
using System.Diagnostics.CodeAnalysis;
using System.Diagnostics.SymbolStore;
using System.Globalization;
using System.IO;
using System.Linq;
using System.Net.Mail;
using System.Numerics;
using System.Resources;
using System.Runtime.ExceptionServices;
using System.Security.Cryptography;
using System.Xml.Schema;
using System.Text.RegularExpressions;
namespace _0._2Nums1to10
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int sizeOfField = int.Parse(Console.ReadLine());
            int[] field = new int[sizeOfField];
            bool doThing = false;
            BigInteger[] initialIndexes = Console.ReadLine().Split(' ').Select(BigInteger.Parse).ToArray();
            //helo
            foreach (var item in initialIndexes)
            {
                if (item > field.Length)
                {

                }
                else
                {
                    field[(int)item] = 1;
                }
            }
            //end
            string[] commands = Console.ReadLine().Split(' ').ToArray();
            while (commands[0] != "end")
            {
                if (commands[1] == "right")
                {
                    if (field[int.Parse(commands[0])] == 1)
                    {
                        field[int.Parse(commands[0])] = 0;
                        int firstIndex = int.Parse(commands[0]);
                        int moveBy = int.Parse(commands[2]);
                        if (field.Length - 1 < firstIndex + moveBy)
                        {
                        }
                        else
                        {
                            if (field[int.Parse(commands[0]) + int.Parse(commands[2])] == 0)
                            {
                                field[int.Parse(commands[0]) + int.Parse(commands[2])] = 1;
                            }
                            else if (field[int.Parse(commands[0]) + int.Parse(commands[2])] == 1)
                            {
                                int addon = 0;
                                while (field[int.Parse(commands[0]) + int.Parse(commands[2]) + addon] == 1 && int.Parse(commands[0]) + int.Parse(commands[2]) + addon < field.Length - 1)
                                {
                                    addon++;
                                    if (int.Parse(commands[2]) + addon > field.Length - 1)
                                    {
                                        doThing = true;
                                        break;
                                    }
                                }
                                if (doThing == false)
                                {
                                    field[int.Parse(commands[0]) + int.Parse(commands[2]) + addon] = 1;
                                }
                            }
                                field[int.Parse(commands[0]) + int.Parse(commands[2])] = 1;
                        }
                    }
                }else if (commands[1] == "left")
                {
                    if (field[int.Parse(commands[0])] == 1)
                    {
                        field[int.Parse(commands[0])] = 0;
                        int firstIndex = int.Parse(commands[0]);
                        int moveBy = int.Parse(commands[2]);
                        if (0 > firstIndex - moveBy)
                        {

                        }
                        else
                        {
                            if (field[int.Parse(commands[0]) - int.Parse(commands[2])] == 0)
                            {
                                field[int.Parse(commands[0]) - int.Parse(commands[2])] = 1;
                            }
                            else if (field[int.Parse(commands[0]) - int.Parse(commands[2])] == 1)
                            {
                                int addon = 0;
                                while (field[int.Parse(commands[0]) - int.Parse(commands[2]) - addon] == 1 && int.Parse(commands[0]) - int.Parse(commands[2]) - addon < 0)
                                {
                                    addon++;
                                    if (int.Parse(commands[2]) - addon < 0)
                                    {
                                        doThing = true;
                                        break;
                                    }
                                }
                                if (doThing == false)
                                {
                                    field[int.Parse(commands[0]) - int.Parse(commands[2]) - addon] = 1;
                                }
                            }
                            field[int.Parse(commands[0]) - int.Parse(commands[2])] = 1;
                        }
                    }
                }
             commands = Console.ReadLine().Split(' ').ToArray();
            }
            Console.WriteLine(string.Join(" ", field));
        }
    }
}
