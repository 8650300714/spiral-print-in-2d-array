# spiral-print-in-2d-array
#include <iostream>
#include <vector>
using namespace std;

vector<int> spiralPrint(vector<vector<int>>& matrix) {
    vector<int> ans;
    int row = matrix.size();
    int col = matrix[0].size();
    int count = 0;
    int total = row * col;
    
    int startingRow = 0;
    int startingCol = 0;
    int endingCol = col - 1;
    int endingRow = row - 1;
    
    while (count < total) {
        // Print the top row
        for (int index = startingCol; count < total && index <= endingCol; index++) {
            ans.push_back(matrix[startingRow][index]);
            count++;
        }
        startingRow++;
        
        // Print the rightmost column
        for (int index = startingRow; count < total && index <= endingRow; index++) {
            ans.push_back(matrix[index][endingCol]);
            count++;
        }
        endingCol--;
        
        // Print the bottom row
        for (int index = endingCol; count < total && index >= startingCol; index--) {
            ans.push_back(matrix[endingRow][index]);
            count++;
        }
        endingRow--;
        
        // Print the leftmost column
        for (int index = endingRow; count < total && index >= startingRow; index--) {
            ans.push_back(matrix[index][startingCol]);
            count++;
        }
        startingCol++;
    }
    
    return ans;
}

int main() {
    int n, m;
    cout << "Enter the number of rows: ";
    cin >> n;
    cout << "Enter the number of columns: ";
    cin >> m;
    
    vector<vector<int>> matrix(n, vector<int>(m));
    
    cout << "Enter the elements of the 2D array:" << endl;
    for (int row = 0; row < n; row++) {
        for (int col = 0; col < m; col++) {
            cin >> matrix[row][col];
        }
    }
    
    vector<int> num = spiralPrint(matrix);
    
    cout << "Spiral Order: ";
    for (int i : num) {
        cout << i << " ";
    }
    cout << endl;
    
    return 0;
}
