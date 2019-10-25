## [目前 APCS 支援的軟體](https://apcs.csie.ntnu.edu.tw/index.php/info/environment/)
- C (C99語法)
- C++ (2011版本)
- Java
- Python
  <br><br>

## [考前複習] 輸入&輸出 範例
- ### 輸入資料
    ```
    abc   123   3.14159265
    ```
    底下若使用線上測試，需在此處輸入測試資料
    <br>![](https://i.imgur.com/wuHDEs5.jpg)
    <br>
- ### 輸出資料
    ```
    line="abc   123  3.14159265"

    tokens[0] = "abc"
    tokens[1] = "123"
    tokens[2] = "3.14159265"

    [       123] -> [123       ](0000000123)
    [3.14159265] -> [3.142     ]
    ```
    <br>
    <br>
- ### 使用 C 實作
    - 線上測試：https://rextester.com/l/c_online_compiler_gcc
    ```c
    //gcc 5.4.0

    #include  <stdio.h>
    #include  <string.h>
    int main(void)
    {
        char line[100];
        gets(line );
        printf("line = \"%s\"\n", line);

        printf("%s", strtok(line, " "));

        //char token[100];
        //int num;
        //float pi;
        //scanf("%s %d %f", token, &num, &pi);
        //printf("%s %d %f\n", token, num, pi);

        return 0;
    }
    ```
    <br>
    <br>
- ### 使用 Java 實作 (基本上，都跟 C 相同)
    - 線上測試：https://rextester.com/l/java_online_compiler
    ```java
    //'main' method must be in a class 'Rextester'.
    //Compiler version 1.8.0_111

    import java.util.*;
    import java.lang.*;

    class Rextester
    {  
        public static void main(String args[])
        {
            Scanner scanner = new Scanner(System.in);
            String line = scanner.nextLine();
            System.out.println("line=\"" + line + "\"");
            System.out.println(String.format("line=\"%s\"", line));
            System.out.println();

            String regex = "\\s+";
            String[] tokens = line.split(regex);
            System.out.println("tokens[0] = \"" + tokens[0] + "\"");
            System.out.println("tokens[1] = \"" + tokens[1] + "\"");
            System.out.println("tokens[2] = \"" + tokens[2] + "\"");
            System.out.println();

            int num = Integer.parseInt(tokens[1]);
            System.out.println(String.format("[%10d] -> [%-10d](%010d)", num, num, num));
            double pi = Double.parseDouble(tokens[2]);
            System.out.println(String.format("[%10f] -> [%-10.3f]", pi, pi));

            java.text.DecimalFormat dFormat = new java.text.DecimalFormat("0.00000000");
            String piInStr = dFormat.format(pi);
            System.out.println(String.format("[%s] -> [%-10.3f]", piInStr, pi));
        }
    }
    ```
    輸出結果：
    ```
    line="abc   123   3.14159265"
    line="abc   123   3.14159265"

    tokens[0] = "abc"
    tokens[1] = "123"
    tokens[2] = "3.14159265"

    [       123] -> [123       ](0000000123)
    [  3.141593] -> [3.142     ]
    [3.14159265] -> [3.142     ]
    ```
    <br>
    <br>
- ### 使用 Python3 實作 (python 有兩種不同的輸出方法)
    - 線上測試：https://rextester.com/l/python3_online_compiler
    ```python3
    # read one line
    line = input()
    print('line="%s"' % line)
    print('line="{0}"'.format(line))
    print()

    # parse tokens
    tokens = line.split()
    for i in range(0, len(tokens)) :
        print("tokens[%d] = \"%s\"" % (i, tokens[i]))
        print('tokens[{0:d}] = "{1:s}"'.format(i, tokens[i]))
    print();

    # convert to int
    num = int(tokens[1])
    print('[%10s] -> [%-10d](%010d)' % (tokens[1], num, num))
    print('[{0:>10s}] -> [{1:<10d}]({1:010d})'.format(tokens[1], num))

    # convert to double
    pi = float(tokens[2])
    print('[%10s] -> [%-10.3f]' % (tokens[2], pi))
    print('[{:>10s}] -> [{:<10.3f}]'.format(tokens[2], pi)) # index can be ignored
    ```
    輸出結果：(python 有兩種不同的輸出方法)
    ```
    line="abc   123   3.14159265"
    line="abc   123   3.14159265"

    tokens[0] = "abc"
    tokens[0] = "abc"
    tokens[1] = "123"
    tokens[1] = "123"
    tokens[2] = "3.14159265"
    tokens[2] = "3.14159265"

    [       123] -> [123       ](0000000123)
    [       123] -> [123       ](0000000123)
    [3.14159265] -> [3.142     ]
    [3.14159265] -> [3.142     ]
    ```
    <br>
    <br>
- ### 使用 C# 實作
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
                Console.WriteLine("line=\"{0}\"", line);
                Console.WriteLine();

                // parse tokens
                string[] tokens = line.Split(new char[]{' '}, System.StringSplitOptions.RemoveEmptyEntries);
                for (int i = 0; i < tokens.Length; i++) {
                    Console.WriteLine("tokens[{0}] = \"{1}\"", i, tokens[i]);
                }
                Console.WriteLine();

                // convert to int
                int num = Int32.Parse(tokens[1]);
                Console.WriteLine("[{0,10:}] -> [{1,-10}]({1:D10})", tokens[1], num);

                // convert to double
                double pi = double.Parse(tokens[2]);
                Console.WriteLine("[{0}] -> [{1,-10:F3}]()", tokens[2], pi);
            }
        }
    }
    ```

