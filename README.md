
## 자바 스윙을 이용하여 자판기 구현하기


저희 팀은 커피,차,물을 뽑을 수 있는 자판기를 구현하였습니다.
밑에는 코드와 결과 화면입니다.

```

import java.awt.*;
import java.awt.Color;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.*;
import javax.swing.BorderFactory;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JMenu;
import javax.swing.JMenuBar;
import javax.swing.JMenuItem;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;
import java.awt.GridLayout;
import java.awt.FlowLayout;
import javax.swing.JOptionPane;
import java.util.Arrays;
import java.awt.event.*;
public class TestUI extends JFrame{
    Container cPane;
    ImageIcon img;
    JLabel ImgBox;


  
    JMenu menu;
    JMenuBar menuBar;
    JMenuItem ExitItem;

    //Panel, button 및 JtextArea
    JPanel panel;
    JTextArea testArea;
    JButton a,b,c,d,m;
    JButton e1,e2,e3,e4,e5,e6;
    int num1=0;
    int num2=0;
    int num3=0;
    int k3value=0; 
    int val1=0;
    int mvalue=0;
    int num10=0;
    int[] array=new int[100]; 
    int[] num8= new int[100]; 
    JTextField a3,b3,d3,c3,k3,p3,y3;
    TestListenr listener;


    public TestUI(){

        setLayout(null); 
        CreateMenu();
        CreatePanel();
        setTitle("자판기");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); 
        setSize(400, 700); 
        setVisible(true); 



    }

    public void CreateMenu() {

        menuBar = new JMenuBar(); 
        menu = new JMenu("파일"); 
        menuBar.add(menu); 
        ExitItem = new JMenuItem("종료"); 
        menu.add(ExitItem); 
        menuBar.setBorder(BorderFactory.createLineBorder(Color.gray));

        listener = new TestListenr(); 
        ExitItem.addActionListener(listener); 
        setJMenuBar(menuBar);
    }


    public void CreatePanel() {

        panel = new JPanel(); 
        panel.setLayout(null); 
        panel.setBounds(0, 0, 500, 600); 

        testArea = new JTextArea(); 
        testArea.setBounds(110, 510,200,30); 
        testArea.setEditable(false); 


        a = new JButton(new ImageIcon("img/coffee.jpg"));
        b = new JButton(new ImageIcon("img/tea.jpg"));
        c = new JButton(new ImageIcon("img/water.jpg"));
        d = new JButton("주문");
        m = new JButton("입력");
        e1 = new JButton("∧");
        e2 = new JButton("∨");
        e3 = new JButton("∧");
        e4 = new JButton("∨");
        e5 = new JButton("∧");
        e6 = new JButton("∨");

        a.setBounds(50, 50, 80, 120); 
        b.setBounds(160,50, 80, 120);
        c.setBounds(270,50, 80, 120);
        d.setBounds(170,450, 60, 50);
        m.setBounds(270,390, 60, 40);

        e1.setBounds(60, 235,50,25);
        e2.setBounds(60, 275,50,25); 
        e3.setBounds(175, 235,50,25);
        e4.setBounds(175, 275,50,25);
        e5.setBounds(285, 235,50,25); 
        e6.setBounds(285, 275,50,25);


        panel.add(a);
        panel.add(b);
        panel.add(c);
        panel.add(d);
        panel.add(m);
        panel.add(e1);
        panel.add(e2);
        panel.add(e3);
        panel.add(e4);
        panel.add(e5);
        panel.add(e6);
        panel.add(testArea);

        a.addActionListener(listener);
        b.addActionListener(listener);
        c.addActionListener(listener);
        d.addActionListener(listener);
        m.addActionListener(listener);
        e1.addActionListener(listener);
        e2.addActionListener(listener);
        e3.addActionListener(listener);
        e4.addActionListener(listener);
        e5.addActionListener(listener);
        e6.addActionListener(listener);

        add(panel); 

        JLabel a1 = new JLabel("가격 500원");
        JLabel b1 = new JLabel("가격 200원");
        JLabel c1 = new JLabel("가격 100원");
        JLabel d1= new JLabel("총금액:");
        JLabel k1 = new JLabel("돈 넣기:");
        JLabel p1 = new JLabel("돈의 종류:");
        JLabel t1 = new JLabel("거스름돈:");
        a1.setBounds(60, 60,100,200); 
        b1.setBounds(170, 60,100,200);
        c1.setBounds(280, 60,100,200);
        d1.setBounds(150,230,100,200);
        k1.setBounds(145,270,100,200);
        p1.setBounds(100,310,100,200);
        t1.setBounds(50,425,100,200);
        panel.add(a1);
        panel.add(b1);
        panel.add(c1);
        panel.add(d1);
        panel.add(k1);
        panel.add(p1);
        panel.add(t1);
        add(panel);
        p3 = new JTextField();
        y3 = new JTextField();
        d3 = new JTextField("0");
        k3 = new JTextField("0");

        a3 = new JTextField("0");
        JLabel a4 = new JLabel("개");


        b3 = new JTextField("0");
        JLabel b4 = new JLabel("개");


        c3 = new JTextField("0");
        JLabel c4 = new JLabel("개");


        a3.setBounds(70, 190,30,20);
        a4.setBounds(100, 175,50,50);

        b3.setBounds(180, 190,30,20);
        b4.setBounds(210, 175,50,50);

        c3.setBounds(290, 190,30,20);
        c4.setBounds(320, 175,50,50);

        d3.setBounds(200, 320,50,20);
        k3.setBounds(200, 360,50,20);
        p3.setBounds(180, 400,80,20);
        y3.setBounds(130, 510,150,30);
        a3.setHorizontalAlignment(a3.CENTER);
        b3.setHorizontalAlignment(b3.CENTER);
        c3.setHorizontalAlignment(c3.CENTER);
        d3.setHorizontalAlignment(d3.RIGHT);
        k3.setHorizontalAlignment(d3.RIGHT);
        p3.setHorizontalAlignment(d3.RIGHT);
        panel.add(a3);
        panel.add(a4);

        panel.add(b3);
        panel.add(b4);

        panel.add(c3);
        panel.add(c4);

        panel.add(d3);
        panel.add(k3);
        panel.add(p3);

        add(panel);



    }



    public void Label() {

    }
    class TestListenr implements ActionListener {

        public void actionPerformed(ActionEvent event) {


            if (event.getSource() == ExitItem) {  
                System.exit(1);   
            } else if (event.getSource() ==e1){
                val1=Integer.parseInt(d3.getText());

                val1=val1+500;

                num1=num1+1;

                a3.setText(String.valueOf(num1));
                d3.setText(String.valueOf(val1));
            }else if(event.getSource()==e2) {
            	 val1=Integer.parseInt(d3.getText());
            	 if(val1>0&&num1>0)
            	 {
            	 val1=val1-500;
            	 
            	 num1=num1-1;
            	 a3.setText(String.valueOf(num1));
                 d3.setText(String.valueOf(val1));
            	 }
            }
            else if(event.getSource()==e4) {
           	 val1=Integer.parseInt(d3.getText());
           	 if(val1>0&&num2>0)
           	 {
           	 val1=val1-200;
           	 
           	 num2=num2-1;
           	 a3.setText(String.valueOf(num2));
                d3.setText(String.valueOf(val1));
           	 }
           }
            else if(event.getSource()==e6) {
           	 val1=Integer.parseInt(d3.getText());
           	 if(val1>0&&num3>0)
           	 {
           	 val1=val1-100;
           	 
           	 num3=num3-1;
           	 a3.setText(String.valueOf(num3));
                d3.setText(String.valueOf(val1));
           	 }
           }
            else if (event.getSource() == e3){

                val1=Integer.parseInt(d3.getText());
                val1=val1+200;

                num2=num2+1;

                b3.setText(String.valueOf(num2));
                d3.setText(String.valueOf(val1));
            }else if (event.getSource() == e5){
                val1=Integer.parseInt(d3.getText());

                val1=val1+100;

                num3=num3+1;

                c3.setText(String.valueOf(num3));
                d3.setText(String.valueOf(val1));

            }else if(event.getSource()==d) { 
                k3value=Integer.parseInt(k3.getText());
                k3value-=val1;

                for(int i=0;i<array.length;i++)
                {
                    if(k3value/array[i]>0&&k3value>=array[i])
                    {
                        num8[i]=k3value/array[i];
                        k3value=k3value-num8[i]*array[i];
                    }
                    else
                    {
                        break;
                    }
                    testArea.append(array[i]+"원 "+num8[i]+"개  ");
                }
            }
            else if(event.getSource()==m) {
                mvalue=Integer.parseInt(p3.getText());
                array[num10]=mvalue;
                num10++;
                p3.requestFocus();

                p3.selectAll();//
                p3.setText(String.valueOf(""));
            }
        }
    }
 
    public static void main(String args[]) {

        TestUI test = new TestUI();
    }
}
```


![image](https://user-images.githubusercontent.com/62733796/79951104-0e2c0600-84b3-11ea-9871-b20b1971f8f7.png)


커피,차,물 사진 밑에 있는 위를 가리키는 화살표 버튼과 아래를 가리키는 화살표 버튼은 화살표 버튼의 위에있는 메뉴의 주문수량을 결정할수 있는 버튼입니다. 커피 밑의 화살표 버튼을 클릭하면 총금액 창에 500이 증가하거나 감소하고 차는 200, 물은 100이 증가하거나 감소합니다.

그리고 돈넣기 창에 자판기 사용자가 넣을 돈 금액을 입력할수 있습니다.

동전의 종류 창은 거스름돈으로 받을수 있는 동전의 종류를 입력할수 있는 창으로 예를 들어 1000원, 500원, 200원으로 거스름돈을 받고 싶다면
1000을 입력하고 입력 버튼을 누르고 다시 500을 입력하고 입력 버튼을 누르고 마지막으로 200을 입력하고 입력 버튼을 누르면 됩니다.

주문 버튼을 누르면 사용자가 입력한 동전의 종류로만 최소 동전의 개수가 나오게 거스름돈을 출력해줍니다.
