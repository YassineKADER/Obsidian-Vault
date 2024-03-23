```Java
package Matrice_Ex;

import java.util.Arrays;

public class Matrice {
	int numOfRows;
	int numOfColumns;
	int[][] elements;
	
	public Matrice(int numOfRows, int numOfColumns) {
		if((numOfRows > 0) && (numOfRows > 0)) {
			this.numOfColumns = numOfColumns;
			this.numOfRows = numOfRows;
			this.elements = new int[numOfRows][numOfColumns];
		}
		
		else {
			System.out.println("enter a valid number of rows and columns");;
		}
	}
	
	public int getNumOfRows() {
		return this.numOfRows;
	}
	
	public int getNumOfColumns() {
		return this.numOfColumns;
	}
	
	public void setElementAt(int element, int row, int column) {
		if((this.numOfRows > row) && (this.numOfColumns > column)) {
			this.elements[row][column] = element;
		}
		else {
			System.out.println("out of range !!");
		}
	}
	
	public Matrice addMatrice(Matrice matB){
		if((this.numOfRows == matB.numOfRows) && (this.numOfColumns == matB.numOfColumns)) {
			Matrice returnedMatrcie = new Matrice(this.numOfRows, this.numOfColumns);
			for(int i=0;i<this.numOfRows;i++) {
				for(int j=0;j<this.numOfColumns; j++) {
					returnedMatrcie.elements[i][j]=this.elements[i][j]+matB.elements[i][j];
				}
			}
			return returnedMatrcie;
		}
		else {
			System.out.println("Matrices cannot be added");
			return new Matrice(0, 0);
		}
		
	}
	
	public Matrice multipleMatrices(Matrice matB) {
		if(this.numOfColumns == matB.numOfRows) {
			Matrice returnedMatrice = new Matrice(this.numOfRows, matB.numOfColumns);
			for(int i=0;i<this.numOfRows;i++) {
				for(int j=0;j<matB.numOfColumns;j++) {
					returnedMatrice.setElementAt(0, i, j);
					for(int k=0; k<this.numOfColumns;k++) {
						returnedMatrice.elements[i][j] += this.elements[i][k] + matB.elements[k][j];
					}
				}
			}
			return returnedMatrice;
		}
		
		else {
			System.out.println("Matrices cannot be multiplyed");
			return new Matrice(0,0);
		}
	}

	@Override
	public String toString() {
		String arrayString = new String("");
		for(int i=0; i<this.numOfRows;i++) {
			for( int j=0; j<this.numOfColumns;j++) {
				System.out.print(this.elements[i][j] + "  |  ");
			}
			System.out.println("");
			System.out.println("________________________________________________________");
		}
		
		return "Matrice [numOfRows=" + numOfRows + ", numOfColumns=" + numOfColumns +"]";
	}
	
	
}
```