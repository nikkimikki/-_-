using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp5
{
    public partial class Form1 : Form
    {
        Random r = new Random();
        private int i = 0;
        private int m;

        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {

            double a, b;
            a = Convert.ToDouble(number1.Text);
            b = Convert.ToDouble(number2.Text);
            Solution.Text = ((a + b) / 2).ToString();
        }

        private void number1_KeyPress(object sender, KeyPressEventArgs e)
        {
            char number = e.KeyChar;
            if ((e.KeyChar <= 47 || e.KeyChar >= 58) && number != 8 && number != 44)
            {
                e.Handled = true;
            }
        }

        private void number2_KeyPress(object sender, KeyPressEventArgs e)
        {
            char number = e.KeyChar;
            if ((e.KeyChar <= 47 || e.KeyChar >= 58) && number != 8 && number != 44)
            {
                e.Handled = true;
            }
        }

        private void btn_Gen_Calc_Click(object sender, EventArgs e)
        {
            double x = 0, y = 0;
            If_box.Text = (x = (r.NextDouble() * 200 - 100)).ToString();
            string Y = "";
            if (x <= -4)
            {
                y = 4 * x + 2 * x;
                Y = "y = 4 * x + 2 * x";
            }
            else
                if (x >= 2)
            {
                y = 3 * x;
                Y = "y = 3 * x";
            }
            else
            {
                y = 2 * x + 1;
                Y = "y = 2 * x + 1";
            }
            label4.Text = Y + "\t: " + y.ToString();
        }

        private void btn_arr_Click(object sender, EventArgs e)
        {
            Random rnd = new Random();
            int[] mass = new int[30];
            int[] massY = new int[30];
            for (int i = 0; i < mass.Length; i++)
            {
                mass[i] = rnd.Next(1, 10);
                textBox1.Text = textBox1.Text + " " + mass[i] + " ";
            }
            for (int i = 0, j = 0; i < mass.Length; i++)
            {
                if (mass[i] % 2 == 0)
                {
                    massY[j] = mass[i];
                    if (textBox1.Text.Length == 0)
                        textBox2.Text = massY[j] + " ";
                    else
                    {
                        textBox2.Text = textBox2.Text + " " + massY[j] + " ";
                    }
                    j++;
                }
            }
            btn_arr.Enabled = false;
        }

        private void tabPage3_Click(object sender, EventArgs e)
        {

        }

        private void btn_Martrix_Click(object sender, EventArgs e)
        {
            matrixLbl.Text = " ";

            const int n = 5;
            int[,] matrix = new int[n, n];

            for (int i = 0; i < n; i++)
            {
                for (int j = 0; j < n; j++)
                {
                    matrix[i, j] = r.Next(20) - 10;
                    matrixLbl.Text += matrix[i, j].ToString() + ' ';
                }

                matrixLbl.Text += '\n';
            }

            for (int i = 0; i < 5; i++)
            {
                int counter = 0;
                for (int j = 0; j < n; j++)
                {
                    if (matrix[i, j] > 0)
                        counter++;
                }
                PositiveCountLbl.Text = PositiveCountLbl.Text + "Row №" + (i + 1) + ":" + counter + "\n";
            }

            }

        private void tabPage4_Click(object sender, EventArgs e)
        {

        }

        private void Array_X_Click(object sender, EventArgs e)
        {

        }

        private void STR_Click(object sender, EventArgs e)
        {

            String string_name;
            bool IsDot = false;
            string_name = STRbox.Text;
            int Length = string_name.Length;

            for (int i = 0; i < Length; i++)
            {
                if (string_name[i] == ',')
                {
                    string_name = string_name.Remove(i, 1);
                    --i;
                    --Length;
                }
                if (string_name[i] == '.')
                    break;
            }

            for (int i = 0; i < Length; i++)
            {

                if (IsDot == true)
                {
                    if (string_name[i] >= '0' && string_name[i] <= '9')
                    {
                        string_name = string_name.Remove(i, 1).Insert(i, "0");
                    }
                }
                if (IsDot == false)
                {
                    if (string_name[i] == '.')
                    {
                        IsDot = true;
                    }
                }
            }

            STRbox.Text = string_name;
        }
    }
        }
        
    


