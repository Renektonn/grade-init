//excel成績

import java.util.Scanner;
class Project {
  
  public static void main(String[] args) {
    Scanner cin=new Scanner (System.in);
    
    Student [] numStu = new Student [10+1];
    int [] rankStu = new int [10+1];
    
    for(int i = 1;i <= 10;i++){
      int Chinese=cin.nextInt();
      int Math=cin.nextInt();
      int English=cin.nextInt();
      numStu[i] = new Student(Chinese , Math , English);
    }

    for(int i = 1;i <= 10;i++){
      rankStu[i]=i;
    }

    for(int i = 1;i <= 10;i++){ // compute rank
      for(int j = i + 1;j <= 10 ;j++){
        if(numStu[i].average < numStu[j].average){
          int tem = rankStu[i];
          rankStu[i] = rankStu[j];
          rankStu[j] = tem ;
        }
      }
    }
    
    

    System.out.printf("%-7s","num");
    System.out.printf("|");
    System.out.printf("%-7s","Chinese");
    System.out.printf("|");
    System.out.printf("%-7s","Math");
    System.out.printf("|");
    System.out.printf("%-7s","English");
    System.out.printf("|");
    System.out.printf("%-7s","average");
    System.out.printf("|");
    System.out.println();

    System.out.println("----------------------------------------");

    
    for(int i = 1;i <= 10;i++){
      int j=rankStu[i];
      System.out.printf("%7d",j);
      System.out.printf("|");
      System.out.printf("%7d",numStu[j].Chinese);
      System.out.printf("|");
      System.out.printf("%7d",numStu[j].Math);
      System.out.printf("|");
      System.out.printf("%7d",numStu[j].English);
      System.out.printf("|");
      System.out.printf("%7.2f",numStu[j].average);
      System.out.printf("|");
      System.out.println();
      System.out.println("----------------------------------------");
    }
  }

}
class Student{
  int Chinese;
  int Math;
  int English;
  double average;
  int rank;
  
  public Student(int Chinese , int Math , int English){
    this.Chinese = Chinese;
    this.Math = Math;
    this.English = English;
    this.average = (Chinese + Math + English)/3.0; 
  }

}
