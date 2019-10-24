### 輸入 / 輸出

## C# 實作
- 線上測試 https://rextester.com/l/csharp_online_compiler
```C#
using System;

namespace Rextester
{
    public class Program
    {
        public static void Main(string[] args)
        {
            // read one line
            string line = Console.ReadLine();
            Console.WriteLine("line={0}", line);
            Console.WriteLine();
            
            string[] tokens = line.Split(new char[]{' '}, System.StringSplitOptions.RemoveEmptyEntries);
            for (int i = 0; i < tokens.Length; i++) {
                Console.WriteLine("tokens[{0}] = \"{1}\"", i, tokens[i]);
            }
            Console.WriteLine();
            
            int num = Int32.Parse(tokens[1]);
            Console.WriteLine("[{0,10:}] -> [{1,-10}]({1:D10})", tokens[1], num);
            
            double pi = double.Parse(tokens[2]);
            Console.WriteLine("[{0}] -> [{1,-10:F3}]()", tokens[2], pi);
        }
    }
}
```
