using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace HomeWork_5_1_1
{
    class Program
    {   /// <summary>
        /// Метод позволяющий умножать матрицу на чило
        /// </summary>
        /// <param name="Matrix">Матрица в виде двураногово массива</param>
        /// <param name="Score">Число на которое унажается матрица</param>
        /// <returns>Возвращает матрицу - результат уножения входной матрицы на число</returns>
        static int[,] Matrix_x_Score(int[,] Matrix, int Score)
        {
            int I = Matrix.GetLength(0);
            int J = Matrix.GetLength(1);
            int[,] Temp = new int[I, J];

            for (int i = 0; i < I; i++)
            {
                for (int g = 0; g < J; g++)
                {
                    Temp[i, g] = Matrix[i, g] * Score;
                }
            }
            return Temp;
        }

        /// <summary>
        /// Метод для нахождения суммы матриц, где работает условие: число строк и стобцов матрцы 1 равно числу строк и столбцов матрицы 2 соответсвенно.
        /// </summary>
        /// <param name="Matrix1">Первая матрица</param>
        /// <param name="Matrix2">Вторая матрица</param>
        /// <returns>Возвращает матрицу - результат сложения двух входных матриц</returns>
        /// 
        static int[,] Matrix_S(int[,] Matrix1, int[,] Matrix2)
        {
            int I = Matrix1.GetLength(0), J = Matrix1.GetLength(1);
            int[,] Temp = new int[I, J];

            for (int i = 0; i < I; i++)
            {
                for (int j = 0; j < J; j++)
                {
                    Temp[i, j] = Matrix1[i, j] + Matrix2[i, j];
                }
            }
            return Temp;
        }

        /// <summary>
        /// Метод для нахождения разности матрица где работает условие : число строк и стобцов матрцы 1 равно числу строк и столбцов матрицы 2 соответсвенно
        /// </summary>
        /// <param name="Matrix1">Первая матрица</param>
        /// <param name="Matrix2">Вторая матрца</param>
        /// <returns>Возвращает матрицу - результат вычитания иза матрицы 1 матрицу 2</returns>
        static int[,] Matrix_R(int[,] Matrix1, int[,] Matrix2)
        {
            int I = Matrix1.GetLength(0), J = Matrix1.GetLength(1);
            int[,] Temp = new int[I, J];

            for (int i = 0; i < I; i++)
            {
                for (int j = 0; j < J; j++)
                {
                    Temp[i, j] = Matrix1[i, j] - Matrix2[i, j];
                }
            }
            return Temp;
        }
        /// <summary>
        /// Метод позволяющий перемножать две матрицы,где работает условие число столбцов матрицы 1 должно равнятся числу строк матрицы 2
        /// </summary>
        /// <param name="Matrix1">Матрица 1</param>
        /// <param name="Matrix2">Матрциа 2</param>
        /// <returns>Возвращает матрицу - результат перемножения матрицы1 на матрицу 2</returns>
        static int[,] Matrix_x_matrix(int[,] Matrix1, int[,] Matrix2)
        {
            int I = Matrix1.GetLength(0), J = Matrix2.GetLength(1), G = Matrix2.GetLength(0);
            int[,] Temp = new int[I, J];
            int N = 0;
            for (int i = 0; i < I; i++)
            {
                for (int j = 0; j < J; j++)
                {
                    for (int g = 0; g < G; g++)
                    {
                        N += Matrix1[i, g] * Matrix2[g, j];

                    }
                    Temp[i, j] = N;
                    N = 0;
                }
            }
            return Temp;
        }
        /// <summary>
        /// Функция отображения массива в косноль
        /// </summary>
        /// <param name="Matrix">Отображаемая массив</param>
        static void ShowMatrix(int[,] Matrix)
        {
            int k, l;
            k = Matrix.GetLength(0);
            l = Matrix.GetLength(1);
            for (int i = 0; i < k; i++)
            {
                for (int j = 0; j < l; j++)
                {
                    Console.Write($"{Matrix[i, j],5} ");
                }
                Console.WriteLine("");
            }
        }
        /// <summary>
        /// Проверка допустимых значений рамерности матрицы АхВ
        /// </summary>
        /// <param name="a">А</param>
        /// <param name="b">В</param>
        /// <returns>Возвращает истину если корректны А и В</returns>
        static bool CheckInput(int a, int b)
        {
            return a < 1 | b < 1 ? false : true;
        }
        /// <summary>
        /// Проверка на сложение и разность матриц
        /// </summary>
        /// <param name="a">Число строк матрицы 1</param>
        /// <param name="b">Число столбцов матрицы 1</param>
        /// <param name="d">Число столбцов матрицы 2</param>
        /// <param name="c">Число строк матрицы 2</param>>
        /// <returns>Возравщает истину если все условия верны</returns>
        static bool CheckMatix_S_R(int a, int b, int c, int d)
        {
            if (a != c | b != d)
            {
                return false;
            }
            return true;
        }
        /// <summary>
        /// Проверка на возможность умножения матриц A и B
        /// </summary>
        /// <param name="a">параметр а</param>
        /// <param name="b">параметр b</param>
        /// <param name="c">параметр с</param>
        /// <param name="d">парраметр d</param>
        /// <returns>вохвращает истину если можно умножить матрицы</returns>
        static bool CheckMatrixAxB(int a, int b, int c, int d)
        {
            if (b != c)
            {
                return false;
            }
            return true;
        }
        /// <summary>
        /// Заполнение массива соучайными числами от 0 до 99
        /// </summary>
        /// <param name="arr">Входной массив</param>
        /// <returns>Возвращает запоненный массив</returns>
        static int[,] FillMatrix(int[,] arr)
        {
            Random r = new Random();
            int row = arr.GetLength(0);
            int coll = arr.GetLength(1);
            for (int i = 0; i < row; i++)
            {
                for (int j = 0; j < coll; j++)
                {
                    arr[i,j] = r.Next(0, 99);
                }

            }
            return arr;
        }
        static void Main(string[] args)
        {
            //Нажмите CTRL+F5
            

            int a,b,c,d ;   // переменные хронящие коэффициенты раpмерности матриц
            bool T1,T2,T3;  // переменная хранщая результат проверки на корректность ввода c консоли
            int x;          // переменная хронящия число для уножения на матрицу
                            // создаем 2 матрицы для тестов и заполняем их
            do
            {
                Console.WriteLine( "Введидте размерность AxB матрицы 1" );
                Console.Write("A: ");
                T1 = int.TryParse(Console.ReadLine(), out a);
                Console.Write("B: ");
                T2 = int.TryParse(Console.ReadLine(),out b);
                T3 = CheckInput(a, b);
            } while (!T1|!T2|T3==false);

            int[,] Temp1 = new int[a,b];
            
            do
            {
                Console.WriteLine("Введидте размерность AxB матрицы 2");
                Console.Write("A: ");
                T1 = int.TryParse(Console.ReadLine(), out c);
                Console.Write("B: ");
                T2 = int.TryParse(Console.ReadLine(),out d);
                T3 = CheckInput(c, d);
            } while (!T1|!T2|T3 == false);

            int[,] Temp2 = new int[c, d];

            Temp1 = FillMatrix(Temp1);
            Temp2 = FillMatrix(Temp2);
            //Выводим на экран созданные матрицы

            Console.WriteLine("Матрица 1");
            ShowMatrix(Temp1);
            Console.WriteLine("Матрица 2");
            ShowMatrix(Temp2);
            //Выводим результаты функций 

            
            bool TryCheck;
            do
            {
                Console.Write("Введите число для умножения на  матрицу 1: ");
                TryCheck = int.TryParse(Console.ReadLine(), out x);
            }
            while (TryCheck == false);
            
            Console.WriteLine("Умножение матрицы 1 на число: "+x);
            ShowMatrix(Matrix_x_Score(Temp1, x));//Умножение на число x

            Console.WriteLine("Сумма матриц 1 и 2");
            if (CheckMatix_S_R(a, b, c, d))
            {
                ShowMatrix(Matrix_S(Temp1, Temp2));
            }// Сложение 2 матриц
            else { Console.WriteLine("Сложение матриц не возможно"); }

            Console.WriteLine("Разность матриц 1 и 2");
            if (CheckMatix_S_R(a, b, c, d))
            {
                ShowMatrix(Matrix_R(Temp1, Temp2));
            }// Разность матриц
            else { Console.WriteLine("Вычитание матриц невозможно"); }

            Console.WriteLine("Произведение матриц 1 и 2");
            if (CheckMatrixAxB(a, b, c, d))
            {
                ShowMatrix(Matrix_x_matrix(Temp1, Temp2));
            }
            else
            {
                Console.WriteLine("Умноженеи матриц не возможно");
            }
        }
    }
}
