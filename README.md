# Rezolvare-Probleme-Setul-1
1. Rezolvarea ecuatiei de gradul 1: ax + b = 0

using System;



public class Probleme {

    public static string EcuatieGrad1(double a, double b) {

        if (a == 0) {

            return b != 0 ? "Ecuatia nu are solutie (a = 0)." : "Ecuatia are o infinitate de solutii.";

        }

        return (-b / a).ToString();

    }



2. Rezolvarea ecuatiei de gradul 2: ax^2 + bx + c = 0

    public static string EcuatieGrad2(double a, double b, double c) {

        if (a == 0) {

            return EcuatieGrad1(b, c);

        }

        double delta = b * b - 4 * a * c;

        if (delta < 0) {

            return "Ecuatia nu are solutii reale.";

        } else if (delta == 0) {

            return (-b / (2 * a)).ToString();

        } else {

            double x1 = (-b - Math.Sqrt(delta)) / (2 * a);

            double x2 = (-b + Math.Sqrt(delta)) / (2 * a);

            return $"{x1}, {x2}";

        }

    }



3. Determinarea daca n se divide cu k

    public static bool SeDivide(int n, int k) {

        return n % k == 0;

    }



4. Determinarea daca un an este bisect

    public static bool AnBisect(int y) {

        return (y % 4 == 0 && y % 100 != 0) || (y % 400 == 0);

    }



5. A k-a cifra de la sfarsitul unui numar

    public static int KAaCifra(int n, int k) {

        n = Math.Abs(n);

        for (int i = 0; i < k - 1; i++) {

            n /= 10;

        }

        return n % 10;

    }



6. Determinarea daca trei numere pot fi laturi ale unui triunghi

    public static bool EsteTriunghi(double a, double b, double c) {

        return a + b > c && a + c > b && b + c > a;

    }



7. Inversarea valorilor a doua variabile

    public static void Swap(ref int a, ref int b) {

        int temp = a;

        a = b;

        b = temp;

    }



8. Inversarea valorilor fara variabile suplimentare

    public static void SwapRestrictionat(ref int a, ref int b) {

        a = a + b;

        b = a - b;

        a = a - b;

    }



9. Divizorii unui numar

    public static int[] Divizori(int n) {

        var divizori = new System.Collections.Generic.List<int>();

        for (int i = 1; i <= n; i++) {

            if (n % i == 0) {

                divizori.Add(i);

            }

        }

        return divizori.ToArray();

    }



10. Test de primalitate

    public static bool EstePrim(int n) {

        if (n < 2) return false;

        for (int i = 2; i <= Math.Sqrt(n); i++) {

            if (n % i == 0) return false;

        }

        return true;

    }



11. Cifrele unui numar in ordine inversa

    public static int InverseazaCifrele(int n) {

        int rezultat = 0;

        int absN = Math.Abs(n);

        while (absN > 0) {

            rezultat = rezultat * 10 + absN % 10;

            absN /= 10;

        }

        return n < 0 ? -rezultat : rezultat;

    }



12. Cate numere divizibile cu n sunt in intervalul [a, b]

    public static int NumereDivizibile(int n, int a, int b) {

        int count = 0;

        for (int i = a; i <= b; i++) {

            if (i % n == 0) {

                count++;

            }

        }

        return count;

    }



13. Cati ani bisecti intre doi ani

    public static int AniBisecti(int y1, int y2) {

        int count = 0;

        for (int y = Math.Min(y1, y2); y <= Math.Max(y1, y2); y++) {

            if (AnBisect(y)) count++;

        }

        return count;

    }



14. Determinarea daca un numar este palindrom

    public static bool EstePalindrom(int n) {

        string s = Math.Abs(n).ToString();

        char[] arr = s.ToCharArray();

        Array.Reverse(arr);

        return s == new string(arr);

    }



15. Afisarea a trei numere in ordine crescatoare

    public static int[] Sortare3(int a, int b, int c) {

        int[] nums = { a, b, c };

        Array.Sort(nums);

        return nums;

    }



16. Afisarea a cinci numere in ordine crescatoare (fara tablouri)

    public static int[] Sortare5(int a, int b, int c, int d, int e) {

        int[] nums = { a, b, c, d, e };

        for (int i = 0; i < nums.Length; i++) {

            for (int j = i + 1; j < nums.Length; j++) {

                if (nums[i] > nums[j]) {

                    int temp = nums[i];

                    nums[i] = nums[j];

                    nums[j] = temp;

                }

            }

        }

        return nums;

    }



17. CMMDC si CMMMC folosind algoritmul lui Euclid

    public static int Cmmdc(int a, int b) {

        while (b != 0) {

            int temp = b;

            b = a % b;

            a = temp;

        }

        return a;

    }



    public static int Cmmmc(int a, int b) {

        return Math.Abs(a * b) / Cmmdc(a, b);

    }



18. Descompunerea in factori primi

    public static System.Collections.Generic.Dictionary<int, int> FactoriPrimi(int n) {

        var factori = new System.Collections.Generic.Dictionary<int, int>();

        int d = 2;

        while (d * d <= n) {

            while (n % d == 0) {

                if (factori.ContainsKey(d)) {

                    factori[d]++;

                } else {

                    factori[d] = 1;

                }

                n /= d;

            }

            d++;

        }

        if (n > 1) {

            factori[n] = 1;

        }

        return factori;

    }



Problema 19: Verificați dacă un număr este format folosind doar două cifre unice.

using System;

using System.Linq;



class Program

{

    static bool IsFormedByTwoDigits(int number)

    {

        string numStr = Math.Abs(number).ToString();

        var uniqueDigits = numStr.Distinct();

        return uniqueDigits.Count() <= 2;

    }



    static void Main()

    {

        Console.WriteLine("Introduceți un număr:");

        int number = int.Parse(Console.ReadLine());



        if (IsFormedByTwoDigits(number))

        {

            Console.WriteLine($"{number} este format din cel mult două cifre unice.");

        }

        else

        {

            Console.WriteLine($"{number} nu este format doar din două cifre unice.");

        }

    }

}



Problema 20: Afișați o fracție în format zecimal cu partea periodică între paranteze.

using System;

using System.Collections.Generic;



class FractionToDecimal

{

    static string FractionToDecimalString(int numerator, int denominator)

    {

        if (denominator == 0)

            throw new DivideByZeroException("Numitorul nu poate fi zero.");



        int integerPart = numerator / denominator;

        int remainder = numerator % denominator;

        string result = integerPart.ToString();



        if (remainder == 0)

            return result; // Fără parte fracționară



        result += ".";

        Dictionary<int, int> remainderPositions = new Dictionary<int, int>();

        List<int> decimals = new List<int>();



        while (remainder != 0)

        {

            if (remainderPositions.ContainsKey(remainder))

            {

                int start = remainderPositions[remainder];

                string nonRepeating = string.Join("", decimals.Take(start));

                string repeating = string.Join("", decimals.Skip(start));

                return result + nonRepeating + "(" + repeating + ")";

            }



            remainderPositions[remainder] = decimals.Count;

            remainder *= 10;

            decimals.Add(remainder / denominator);

            remainder %= denominator;

        }



        result += string.Join("", decimals);

        return result;

    }



    static void Main()

    {

        Console.WriteLine("Introduceți numărătorul:");

        int numerator = int.Parse(Console.ReadLine());



        Console.WriteLine("Introduceți numitorul:");

        int denominator = int.Parse(Console.ReadLine());



        try

        {

            string result = FractionToDecimalString(numerator, denominator);

            Console.WriteLine($"{numerator}/{denominator} = {result}");

        }

        catch (DivideByZeroException e)

        {

            Console.WriteLine(e.Message);

        }

    }

}



Problema 21: Ghiciți un număr între 1 și 1024 folosind strategia de căutare binară.

using System;



class GuessNumber

{

    static void Main()

    {

        int low = 1, high = 1024;

        Console.WriteLine("Gândiți-vă la un număr între 1 și 1024.");



        while (low < high)

        {

            int mid = (low + high) / 2;

            Console.WriteLine($"Numărul este mai mare sau egal cu {mid}? (da/nu)");

            string response = Console.ReadLine().ToLower();



            if (response == "da")

                low = mid;

            else

                high = mid - 1;

        }



        Console.WriteLine($"Numărul dumneavoastră este {low}!");

    }

}

