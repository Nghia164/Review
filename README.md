using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using DevExpress.XtraEditors;
using DevExpress.XtraEditors.ColorPick.Picker;

namespace Caculator
{
    public partial class Caculator : DevExpress.XtraEditors.XtraForm
    {
        public Caculator()
        {
            InitializeComponent();
        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox3_TextChanged(object sender, EventArgs e)
        {

        }
        
        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void textBox4_TextChanged(object sender, EventArgs e)
        {

        }

        private void Caculator_Load(object sender, EventArgs e)
        {
            textBox1.Text = "";
            textBox2.Text = "";
            textBox3.Text = "";         
            this.Text = "Caculator";
           
            comboBox1.Items.AddRange(new string[] { "+", "-", "x", "%" });
            comboBox1.SelectedIndex = 0; 
          
            MessageBox.Show("Chào mừng bạn đến với ứng dụng Caculator!", "Thông báo", MessageBoxButtons.OK, MessageBoxIcon.Information);
        }

        private void button5_Click(object sender, EventArgs e)
        {
            try
            {
                if (string.IsNullOrEmpty(textBox1.Text) && string.IsNullOrEmpty(textBox3.Text))
                {
                    MessageBox.Show("Vui lòng nhập đầy đủ số!", "Cảnh báo", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                    return;
                }
                if (comboBox1.SelectedItem == null)
                {
                    MessageBox.Show("Vui lòng chọn phép toán!", "Cảnh báo", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                    return;
                }
                double num1 = double.Parse(textBox1.Text);
                double num2 = double.Parse(textBox3.Text);
                double result = 0;
                string operation = comboBox1.SelectedItem.ToString();

                switch (operation)
                {
                    case "+":
                        result = num1 + num2;
                        break;
                    case "-":
                        result = num1 - num2;
                        break;
                    case "x":
                        result = num1 * num2;
                        break;
                    case "%":
                        if (num2 != 0)
                            result = num1 % num2;
                        else
                        {
                            MessageBox.Show("Không thể chia cho 0!", "Lỗi", MessageBoxButtons.OK, MessageBoxIcon.Error);
                            return;
                        }
                        break;
                    default:
                        MessageBox.Show("Vui lòng chọn phép toán!", "Cảnh báo", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                        return;
                }

                textBox2.Text = result.ToString();
            }
            catch (Exception)
            {
                MessageBox.Show("Vui lòng nhập số hợp lệ!", "Lỗi", MessageBoxButtons.OK, MessageBoxIcon.Warning);
            }
        }

    }
}
