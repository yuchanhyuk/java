# java
팀플 프로젝트


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
 

 //메뉴바를 위한 변수
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
 int k3value=0; //돈 넣기 입력창에서 입력한 값
 int val1=0;
 int mvalue=0;
 int num10=0;//동전 종류 개수
 int[] array=new int[100]; //동전 종류 입력 배열
 int[] num8= new int[100]; //거스름돈 동전의 개수
 JTextField a3,b3,d3,c3,k3,p3,y3;
 //이벤트 등록을 위한 변수
 TestListenr listener;
 
 
 
 /*****************************************************************************
  * 생성자 
  ****************************************************************************/
 public TestUI(){
  
  setLayout(null); //Layout을 NULL로 설정 (컴포넌트의 위치를 사용자가 설정해주어야 함)  
  CreateMenu(); //메뉴바를 추가한다.
  CreatePanel();
  setTitle("자판기"); //Frame의 타이틀 이름 주기
  setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); //Frame의 X를 누를경우 종료
  setSize(400, 550); //Frame의 크기 설정
  setVisible(true); //생성한 Frame을 윈도우에 뿌리기
 
  

 }
 
 /*****************************************************************************
  * 메뉴바를 생성
  ****************************************************************************/
 public void CreateMenu() {
  
  menuBar = new JMenuBar(); //메뉴바를 생성
  menu = new JMenu("파일"); //'파일'이라는 메뉴를 생성 
  menuBar.add(menu); //메뉴바에 '파일'이라는 메뉴를 추가
  ExitItem = new JMenuItem("종료"); //'종료'라는 메뉴아이템 생성 
  menu.add(ExitItem);  //'파일' 메뉴 안에 '종료'라는 메뉴아이템 추가
  menuBar.setBorder(BorderFactory.createLineBorder(Color.gray)); //메뉴바 색상 지정
  
  listener = new TestListenr(); //아래의 컴포넌트 리스너 클래스 생성
  ExitItem.addActionListener(listener); //'종료' 메뉴 아이템 선택시 발생하는 이벤트 지정
  setJMenuBar(menuBar);
 }

 
 public void CreatePanel() {
     
     panel = new JPanel(); //패널을 생성
     panel.setLayout(null); //패널의 Layout을 NULL
     panel.setBounds(0, 0, 500, 600); //패널의 크기 및 위치 지정 (x,y로 부터 넓이(width, 높이(height))
     
      testArea = new JTextArea();  //JTextArea 생성
      testArea.setBounds(130, 440,150,30); //JTeatArea 크기 및 위치 지정
      testArea.setEditable(false); //실행시 JtextArea edit 금지 (글을 쓸 수 없음) true면 가능
     
      
     a = new JButton("커피");  
     b = new JButton("차");
     c = new JButton("물");
     d = new JButton("주문");
     m = new JButton("입력");
     e1 = new JButton("∧");  
     e2 = new JButton("∨");
     e3 = new JButton("∧");
     e4 = new JButton("∨");  
     e5 = new JButton("∧");
     e6 = new JButton("∨");
     
     a.setBounds(50, 100, 80, 50); //크기 지정 (x좌표, y좌표,가로,세로)
     b.setBounds(160,100, 80, 50);
     c.setBounds(270,100, 80, 50);
     d.setBounds(170,380, 60, 50);
     m.setBounds(270,320, 60, 40);
    
     e1.setBounds(75, 170,15,15);
     e2.setBounds(75, 215,30,30); //크기 지정 (x좌표, y좌표,가로,세로)
     e3.setBounds(185, 120,15,15);
     e4.setBounds(185, 150,15,15);
     e5.setBounds(295, 120,15,15); //크기 지정 (x좌표, y좌표,가로,세로)
     e6.setBounds(295, 150,15,15);
    
     
     panel.add(a); //패널에 버튼 add
     panel.add(b); 
     panel.add(c);
     panel.add(d);
     panel.add(m);
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
    
     add(panel);  //Frame에 Panel add (JFrame을 상속받았기에 this(생략가능)가 JFrame)
     
     JLabel a1 = new JLabel("가격 500원");//글씨 넣기
     JLabel b1 = new JLabel("가격 200원");
     JLabel c1 = new JLabel("가격 100원");
      JLabel d1= new JLabel("총금액:"); //총금액
      JLabel k1 = new JLabel("돈 넣기:");
      JLabel p1 = new JLabel("동전의 종류:");
      a1.setBounds(60, 60,100,200); //글씨 위치와 사이즈 조정
      b1.setBounds(170, 60,100,200); 
      c1.setBounds(280, 60,100,200); 
        d1.setBounds(150,160,100,200);
        k1.setBounds(145,200,100,200);
        p1.setBounds(100,240,100,200);
      panel.add(a1);
      panel.add(b1);
      panel.add(c1);
      panel.add(d1);
      panel.add(k1);
      panel.add(p1);
      add(panel);
      p3 = new JTextField();//동전의 종류 입력창
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
         
         d3.setBounds(200, 250,50,20);
         k3.setBounds(200, 290,50,20);
         p3.setBounds(180, 330,80,20);
         y3.setBounds(130, 440,150,30);
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
        
        
      if (event.getSource() == ExitItem) {   //이벤트가 ExitItem이라면
       System.exit(1);   //'종료' 선택시 프로그램 종료
      } else if (event.getSource() ==a){
         val1=Integer.parseInt(d3.getText());
        
        val1=val1+500;
        
        num1=num1+1;
        
        a3.setText(String.valueOf(num1));
        d3.setText(String.valueOf(val1));
      }else if (event.getSource() == b){
         
         val1=Integer.parseInt(d3.getText());
           val1=val1+200;
          
           num2=num2+1;
           
           b3.setText(String.valueOf(num2));
           d3.setText(String.valueOf(val1));
      }else if (event.getSource() == c){
         val1=Integer.parseInt(d3.getText());
           
           val1=val1+100;
           
           num3=num3+1;
           
           c3.setText(String.valueOf(num3));
           d3.setText(String.valueOf(val1));
       
      }else if(event.getSource()==d) { //주문 버튼 눌렀을 때
        k3value=Integer.parseInt(k3.getText());
         k3value-=val1;
         
            for(int i=0;i<array.length;i++)
            {
         if(k3value/array[i]>0)
         {
            num8[i]=k3value/array[i];
            k3value=k3value-num8[i]*array[i];
         }
         else
         {
            break;
         }
         testArea.append(array[i]+"원 "+num8[i]+"개  ");
         //y3.setText(String.valueOf(array[i]+"원 "+num8[i]+"개  "));
            }
      }
      else if(event.getSource()==m) {//입력 버튼 동작
         mvalue=Integer.parseInt(p3.getText());
         array[num10]=mvalue;
         num10++;
         p3.requestFocus(); 
        
           p3.selectAll();// 
           p3.setText(String.valueOf(""));
      }
     }
    }
 /*****************************************************************************
  * 메인 함수
  ****************************************************************************/
 public static void main(String args[]) {
  
  TestUI test = new TestUI();
 }
}
