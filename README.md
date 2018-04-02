using System;
using System.Collections.Generic;
//using System.Collections.Generic.Stack;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace ProjectNew
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            //rdTrue.AutoCheck = false;
            //rdFalse.AutoCheck = false;
        }
        Stack<string> MyStack = new Stack<string>();
        string[] mas1 = new string[3] { "(", "{", "[" };
        string stroka;
        // string c = "\\";
        private void Form1_Load(object sender, EventArgs e)
        {
            stroka = txtString.Text;
        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void btnCheck_Click(object sender, EventArgs e)
        {
            if (txtString.TextLength <= 0)
            {
                MessageBox.Show("Введите текст", "Ошибка");
                txtString.Focus();
            }
            else
            {
                for (int i = 0; i < txtString.TextLength; i++)
                {
                    if (txtString.Text[i].ToString() == "(")
                    {
                        MyStack.Push(txtString.Text[i].ToString());

                    }
                    else if (txtString.Text[i].ToString() == ")")
                    {
                        if (MyStack.Count == 0)
                        {
                            MessageBox.Show("Нет баланса1", "Результат");
                            //MyStack.Clear();
                            txtString.SelectAll();
                            break;
                        }
                        else if (MyStack.Peek() != "(")
                        {
                            MessageBox.Show("Нет баланса1/1", "Результат");
                            //MyStack.Clear();
                            break;
                        }
                        else if (MyStack.Count == 0)
                        {
                            MessageBox.Show("Нет баланса1", "Результат");
                            //MyStack.Clear();
                            txtString.SelectAll();
                            break;
                        }
                        else
                            MyStack.Pop();
                    }
                    if (txtString.Text[i].ToString() == "{")
                    {
                        MyStack.Push(txtString.Text[i].ToString());

                    }

                    else if (txtString.Text[i].ToString() == "}")
                    {

                        if (MyStack.Count == 0)
                        {
                            MessageBox.Show("Нет баланса2", "Результат");
                            // MyStack.Clear();
                            txtString.SelectAll();
                            break;
                        }
                        if (MyStack.Peek() != "{")
                        {
                            MessageBox.Show("Нет баланса1/2", "Результат");
                            break;
                        }
                        else
                            MyStack.Pop();
                    }
                    if (txtString.Text[i].ToString() == "[")
                    {
                        MyStack.Push(txtString.Text[i].ToString());
                        //MessageBox.Show("asd", "sda");
                    }
                    else if (txtString.Text[i].ToString() == "]")
                    {
                        if (MyStack.Count == 0)
                        {
                            MessageBox.Show("Нет баланса3", "Результат");
                            // MyStack.Clear();
                            txtString.SelectAll();
                            break;
                        }
                        else if (MyStack.Peek() != "[")
                        {
                            MessageBox.Show("Нет баланса1/3", "Результат");
                            // MyStack.Clear();
                            break;
                        }
                        else
                            MyStack.Pop();

                    }








                }
                if (MyStack.Count == 0)
                {
                    MessageBox.Show("Есть баланс1", "Результат");

                    //MyStack.Clear();

                }


            }
            MyStack.Clear();
        }
    }
}
