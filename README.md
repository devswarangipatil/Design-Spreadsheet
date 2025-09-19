# Design-Spreadsheet

A spreadsheet is a grid with 26 columns (labeled from 'A' to 'Z') and a given number of rows. Each cell in the spreadsheet can hold an integer value between 0 and 105.

Implement the Spreadsheet class:

Spreadsheet(int rows) Initializes a spreadsheet with 26 columns (labeled 'A' to 'Z') and the specified number of rows. All cells are initially set to 0.
void setCell(String cell, int value) Sets the value of the specified cell. The cell reference is provided in the format "AX" (e.g., "A1", "B10"), where the letter represents the column (from 'A' to 'Z') and the number represents a 1-indexed row.
void resetCell(String cell) Resets the specified cell to 0.
int getValue(String formula) Evaluates a formula of the form "=X+Y", where X and Y are either cell references or non-negative integers, and returns the computed sum.
Note: If getValue references a cell that has not been explicitly set using setCell, its value is considered 0.


class Spreadsheet(object):

    def __init__(self, rows):
        """
        :type rows: int
        """
        self.r=rows #specifies the number of rows
        self.cells={} #creating a hashmap for cells
        

    def setCell(self, cell, value):
        """
        :type cell: str
        :type value: int
        :rtype: None
        """
        self.cells[cell]=value
        #putting the value in the cellname specified to cell 
        #if cell name not there we create one

    def resetCell(self, cell):
        """
        :type cell: str
        :rtype: None
        """
        if cell in self.cells: #if the specified cell is in  hashmap
            del self.cells[cell] #we delete that cell
        

    def getValue(self, formula):
        """
        :type formula: str
        :rtype: int
        """
        f=formula[1:].split('+') #getting the names from the formula
        def v(i): #value getting function
            if i.isdigit():
                return int(i) #if integer named just return the integer
            return self.cells.get(i,0) #gets the value
        v1=v(f[0]) #getting the value of the first
        v2=v(f[1]) # value of the second
        return v1+v2 #returning the sum
