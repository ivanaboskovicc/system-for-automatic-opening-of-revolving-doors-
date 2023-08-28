# system-for-automatic-opening-of-revolving-doors-
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Web;
using System.Net.Mail;

namespace seminar_racunalni_ivana_matej
{

    public partial class Form1 : Form
    {
        
        public Form1()
        {
            InitializeComponent();
            motor.InitMotoBee();
            int senzor = motor.DohvatiInput();
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            
            if (motor.DohvatiInput() == 1)
            {
              motor.SetMotors(1, 150, 0, 0, 0, 0, 0, 0, 0);

              
            }
            else
            {
               motor.SetMotors(0, 0, 0, 0, 0, 0, 0, 0, 0);
            }
        }

        private void Form1_FormClosed(object sender, FormClosedEventArgs e)
        {
            motor.SetMotors(0, 0, 0, 0, 0, 0, 0, 0, 0);
        }

        private void button1_Click(object sender, EventArgs e)
        {
            timer1.Start();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            motor.SetMotors(0, 0, 0, 0, 0, 0, 0, 0, 0);
            timer1.Stop();
        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

    }

}
 
