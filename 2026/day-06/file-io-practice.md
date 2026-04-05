# 1- create a file : 
                   1- touch notes.txt
                   2- ls (verify it)

# 2- Write 3 lines into the file using redirection (> and >>)
                   1- echo "Line 1: Linux io" >notes.txt
                   2- echo "Line 2: Linux fo" >>notes.txt
                   3- echo "Line 3: Linux co" >>>notes.txt

# 3- Using cat read the file : 
                  1- cat notes.txt -
                     OUTPUT:
                  (Line 1: linus file io
                   Line 2: linux file co
                   Line3: linux file fo)   

# 4- using head & tail : 
                 1- Read First Lines : head -n 2 notes.txt : (Line 1: linus file io
                                                              Line 2: linux file co)

                 2- Read last 2 lines : tail -n 2 notes.txt : (Line 2: linux file co
                                                              Line3: linux file fo) 

# 5- Use tee once to write and display at the same time:
                 1- echo "line 4: using tee cammand" | tee -a notes.txt (line 4: using tee cammand) 

# 6- Add More Lines (to reach 8–12 lines):
                  1- echo "line 5:using head" >> notes.txt
                     echo "line 6: using tail" >> notes.txt
                     echo "line 7: tee " >>notes.txt
                     echo "line 8: done it" >>notes.txt

                  2- cat notes.txt:
                    (Line 1: linus file io
                     Line 2: linux file co
                     Line3: linux file fo
                     line 4: using tee cammand
                     line 5:using head
                     line 6: using tail
                     line 7: tee
                     line 8: done it)
                                                              

                 

                   
                   
                   
