# N-queen-problem
Reference - My Leetcode
class Solution {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>>allboards=new ArrayList<>();
        char[][] board=new char[n][n];
        
        helper(board,allboards,0);
        return allboards;
    }
  #Helper function is for placing the Queen at right position.
    public void helper(char[][] board, List<List<String>>allboards,int col)
    {
        if(col==board.length)
        {
            saveboard(board,allboards);
            return;
        }
        for(int row=0;row<board.length;row++)
        {
          if(isSafe(board,row,col))
           {
              board[row][col]='Q';
              helper(board,allboards,col+1);
              board[row][col]='.';
           }  
        }
    }
       # isSafe function is for checking the place for the Queen is safe or not.
        public boolean isSafe(char[][]board,int row,int col)
        {
            //Horizontal
            for(int j=0;j<board.length;j++)
            {
                if(board[row][j]=='Q')
                {
                    return false;
                }
            }
            //Vertical
            for(int i=0;i<board.length;i++)
            {
                if(board[i][col]=='Q')
                {
                    return false;
                }
            }
            
            //upper left
            int r=row;
            for(int c=col ; c>=0 && r>=0 ; c-- , r--)
            {
                if(board[r][c]=='Q')
                {
                    return false;
                }
            }
            // upper right
            r=row;
            for(int c=col;c<board.length && r>=0;r--, c++)
            {
               if(board[r][c]=='Q')
                {
                    return false;
                } 
            }
            //lower left
            r=row;
            for(int c=col;c>=0 && r<board.length;r++,c--)
            {
                if(board[r][c]=='Q')
                {
                    return false;
                }
            }
            // lower right
            r=row;
            for(int c=col;c<board.length && r<board.length;r++,c++)
            {
                if(board[r][c]=='Q')
                {
                    return false;
                }
            }
            return true;
        }
       #saveboard function is for saving the final board.
        public void saveboard(char[][] board, List<List<String>>allboards)
        {
            String row="";
            List<String> newboard=new ArrayList<>();
            for(int i=0;i<board.length;i++)
            {
                row="";
                for(int j=0;j<board[0].length;j++)
                {
                    if(board[i][j]=='Q')
                    {
                        row+='Q';
                    }
                    else
                    {
                        row+='.';
                    }
                }
                newboard.add(row);
            }
            allboards.add(newboard);
        }
    }



