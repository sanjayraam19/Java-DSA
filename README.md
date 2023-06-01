package CollectionFramework;

import java.util.Scanner;
class dynamicArrayDemo{
	
	//variable and methods
	
	  private static final int initialCapacity=16;
	  int arr[];
      private int size ;
	  private int capacity ;
	  
	  //constructor for initialization 
	  
	  dynamicArrayDemo(){
		  size=0;
		  arr = new int[initialCapacity];
		  capacity = initialCapacity;
	  }
	  
	  // Methods for Insert value
	  
	  public void add(int val) {
		  if(size==capacity) {
			  expandArray();
		  }
		  arr[size]=val;
		  size++;		  
	  }
	  //expand the array for making it dynamic 
	  private void  expandArray() {
		  capacity*=2;
		  arr = java.util.Arrays.copyOf(arr, capacity);
	  }
	  
	  //Display the value
	  
	public void   Display(){
		System.out.println("Elements in the List : \n");
		for(int i =0;i<size;i++) {
			System.out.print(arr[i]+ " ");
		}  
	  }
	// Inserting value at the User's Position
	
	public void addPos(int pos,int val) {
		if(size==capacity)
			expandArray();
		for(int i=size-1;i>=pos;i--)
			arr[i+1] = arr[i];	
		arr[pos] = val;
		size++;	
		
	}
	// Deleting value at the User's Position
	
		public void deletePos(int pos) {
			for(int i = pos+1 ; i<size;i++) {
				arr[i-1]=arr[i];
				size--;
				if(capacity > initialCapacity && capacity > 3*size)
			    	shrinkArray();
				
			}
		
		
		}
		
		// shrink the array for memory management 
		
		private void 	shrinkArray() {
			capacity /= 2;
			arr =java.util.Arrays.copyOf(arr, capacity);	
		}
		public int length() {
			return size;
		}
	
}

public class dynamicArray {
	public static void main(String[] args) {
		int val,pos ;
		
	dynamicArrayDemo list = new dynamicArrayDemo();
		
	
		Scanner sc = new Scanner(System.in);
		
	while(true){
			System.out.println("\n--------------LIST MENU---------------\n");
			System.out.println("1 . Insert value \n");
			System.out.println("2 . Display the value \n");
			System.out.println("3 . Insert the value at User Position\n");
			System.out.println("4 . Delete the value at User Position\n");
			System.out.println("5 . Exit \n");
			System.out.println("-----------------------------------------");
			System.out.println("Enter the choice");
			
		int choice = sc.nextInt();
		switch(choice) {
		case 1 : 
			System.out.println("Enter the value : ");
			val = sc.nextInt();
			list.add(val);
			break;
			
		case 2 : 
			System.out.println("Elements in the list : \n");
			list.Display();
			break;
		case 3 :
			System.out.println("Enter the position \n");
			pos = sc.nextInt();
			if(pos<0) {
				System.out.println("invalid pos");
				break;
			}
			System.out.println("Enter the value ");
			val=sc.nextInt();
			list.addPos(pos,val);
			break;
			
		case 4 : System.out.println("Enter the position \n");
		pos = sc.nextInt();
		if(pos<0) {
			System.out.println("invalid pos");
			break;
		}
		      list.deletePos(pos);
		       break;
		case 5 :
			System.exit(0);
			break;
		  default: System.out.println("Invalid Choice ");
          
			
		}
			
			
		}
	
	
	}

}
