# utl-find-the-unique-letter-in-a-sentence
Find the unique letters in a sentence
    Find the unique letters in a sentence                                                                                                     
                                                                                                                                              
    github                                                                                                                                    
    https://github.com/rogerjdeangelis/utl-find-the-unique-letter-in-a-sentence                                                               
                                                                                                                                              
      Five Solutions  (Sorry experts, I lost some of the links)                                                                               
                                                                                                                                              
           a.  Perl the mover of Regular Expression and a powerful string processor                                                           
           b.  SAS Add letters to a second string whe letter is not present in second string                                                  
           c.  R strsplit - split into a vector of letters apply unique function then concatenate                                             
           d.  R use function ChartoRaw to split into a vector of bytes apply unique and concatenate                                          
           e.  Python                                                                                                                         
               Macin                                                                                                                          
               https://stackoverflow.com/users/248823/marcin                                                                                  
                                                                                                                                              
    StackOverflow Python                                                                                                                      
    https://tinyurl.com/y3v5xjbb                                                                                                              
    https://stackoverflow.com/questions/28823323/python-check-for-unique-characters-on-a-string                                               
                                                                                                                                              
    SAS forum (related to this 'sticky finger' problem. But I solve a slighty different problem)                                              
    https://communities.sas.com/t5/SAS-Programming/how-to-remove-mulitple-word/m-p/680963                                                     
     /*                   _                                                                                                                   
    (_)_ __  _ __  _   _| |_                                                                                                                  
    | | `_ \| `_ \| | | | __|                                                                                                                 
    | | | | | |_) | |_| | |_                                                                                                                  
    |_|_| |_| .__/ \__,_|\__|                                                                                                                 
            |_|                                                                                                                               
    */                                                                                                                                        
                                                                                                                                              
    Note: this string has every letter in the alpabet                                                                                         
                                                                                                                                              
    %let str=%qcompress(%qlowcase(The quickee brownee foxxy jumps allover the lazy dog),%str( ));                                             
    %put &=str;                                                                                                                               
                                                                                                                                              
    STR=thequickeebrowneefoxxyjumpsalloverthelazydog                                                                                          
                                                                                                                                              
                                                                                                                                              
    /*           _               _                                                                                                            
      ___  _   _| |_ _ __  _   _| |_                                                                                                          
     / _ \| | | | __| `_ \| | | | __|                                                                                                         
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                          
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                         
                    |_|                                                                                                                       
    */                                                                                                                                        
                                                                                                                                              
    All 26 letters in alphabet                                                                                                                
                                                                                                                                              
    1........10.......20....26                                                                                                                
                                                                                                                                              
    thequickbrownfxyjmpsalvzdg                                                                                                                
                                                                                                                                              
    and in alphabetical order (R solution)                                                                                                    
                                                                                                                                              
    1........10.......20....26                                                                                                                
    abcdefghijklmnopqrstuvwxyz                                                                                                                
                                                                                                                                              
                                                                                                                                              
    /*                         _                                                                                                              
      __ _     _ __   ___ _ __| |                                                                                                             
     / _` |   | `_ \ / _ \ `__| |                                                                                                             
    | (_| |_  | |_) |  __/ |  | |                                                                                                             
     \__,_(_) | .__/ \___|_|  |_|                                                                                                             
              |_|                                                                                                                             
    */                                                                                                                                        
                                                                                                                                              
    Explanation of the regex (I lost the link)                                                                                                
                                                                                                                                              
    The regex used is: (.)(?=.*?\1)                                                                                                           
                                                                                                                                              
       . : to match any char.                                                                                                                 
       first () : remember the matched single char.                                                                                           
       (?=...) : +ve lookahead                                                                                                                
       .*? : to match anything in between                                                                                                     
       \1 : the remembered match.                                                                                                             
       (.)(?=.*?\1) : match and remember any char only if it appears again later in the string.                                               
       s/// : Perl way of doing the substitution.                                                                                             
       g: to do the substitution globally...that is don't stop after first substitution.                                                      
                                                                                                                                              
       s/(.)(?=.*?\1)//g : this will delete a char from the input string only if that char appears again later in the string.                 
                                                                                                                                              
    %let str=%qcompress(%qlowcase(The quickee brownee foxxy jumps allover the lazy dog),%str( ));                                             
                                                                                                                                              
    %utl_submit_pl64(resolve("                                                                                                                
      use Win32::Clipboard;`                                                                                                                  
      $s='&str';`                                                                                                                             
      $s =~ s/(.)(?=.*?\1)//g;`                                                                                                               
      print $s;`                                                                                                                              
      $CLIP = Win32::Clipboard();`                                                                                                            
      $CLIP->Set($s);`                                                                                                                        
    "));                                                                                                                                      
                                                                                                                                              
    * read the clipboad to get the result back to sas;                                                                                        
                                                                                                                                              
    filename clp clipbrd ;                                                                                                                    
    data _null_;                                                                                                                              
     infile clp;                                                                                                                              
     input;                                                                                                                                   
     put "from PERL the unique letters are " _infile_;                                                                                        
    run;quit;                                                                                                                                 
                                             26 letters                                                                                       
                                     1........10.......20.....6                                                                               
    from PERL the unique letters are qickbwnfxjumpsvrthelazydog                                                                               
                                                                                                                                              
    /*                                                                                                                                        
    | |__     ___  __ _ ___                                                                                                                   
    | `_ \   / __|/ _` / __|                                                                                                                  
    | |_) |  \__ \ (_| \__ \                                                                                                                  
    |_.__(_) |___/\__,_|___/                                                                                                                  
                                                                                                                                              
    */                                                                                                                                        
                                                                                                                                              
    %let str=%qcompress(%qlowcase(The quickee brownee foxxy jumps allover the lazy dog),%str( ));                                             
                                                                                                                                              
    * add letter to string only if the letter is not in the strin;                                                                            
    data want;                                                                                                                                
      length lst $200;                                                                                                                        
      str="&str";                                                                                                                             
      str=lowcase(str);                                                                                                                       
      do i=1 to length(str);                                                                                                                  
         if index(lst,substr(str,i,1))=0 then lst=cats(lst,substr(str,i,1));                                                                  
      end;                                                                                                                                    
      put lst=;                                                                                                                               
      stop;                                                                                                                                   
    run;quit;                                                                                                                                 
                                                                                                                                              
    All letters in alphabet                                                                                                                   
                                                                                                                                              
    1........10.......10.....6                                                                                                                
                                                                                                                                              
    thequickbrownfxyjmpsalvzdg                                                                                                                
                                                                                                                                              
    /*      ____        _                  _ _ _                                                                                              
      ___  |  _ \   ___| |_ _ __ ___ _ __ | (_) |_                                                                                            
     / __| | |_) | / __| __| `__/ __| `_ \| | | __|                                                                                           
    | (__  |  _ <  \__ \ |_| |  \__ \ |_) | | | |_                                                                                            
     \___| |_| \_\ |___/\__|_|  |___/ .__/|_|_|\__|                                                                                           
                                    |_|                                                                                                       
    */                                                                                                                                        
                                                                                                                                              
    %let str=thisisacheckstring;                                                                                                              
                                                                                                                                              
    %let str=%qcompress(%qlowcase(The quickee brownee foxxy jumps allover the lazy dog),%str( ));                                             
                                                                                                                                              
    %utl_submit_r64(resolve('                                                                                                                 
    vec<-sort(unique(unlist(strsplit("&str", ""))));                                                                                          
    res<-paste0(vec,collapse="");                                                                                                             
    writeClipboard(res);                                                                                                                      
    '),returnVar=from_r );                                                                                                                    
                                                                                                                                              
                                                                                                                                              
    %put from_r=&from_r;                                                                                                                      
                                                                                                                                              
    from_r=abcdefghijklmnopqrstuvwxyz                                                                                                         
                                                                                                                                              
    /*   _   ____         _               ____                                                                                                
      __| | |  _ \    ___| |__   __ _ _ _|___ \ _ __ __ ___      __                                                                           
     / _` | | |_) |  / __| `_ \ / _` | `__|__) | `__/ _` \ \ /\ / /                                                                           
    | (_| |_|  _ <  | (__| | | | (_| | |  / __/| | | (_| |\ V  V /                                                                            
     \__,_(_)_| \_\  \___|_| |_|\__,_|_| |_____|_|  \__,_| \_/\_/                                                                             
                                                                                                                                              
    */                                                                                                                                        
                                                                                                                                              
                                                                                                                                              
                                                                                                                                              
    %let str=%qcompress(%qlowcase(the quickee brownee foxxy jumps allover the lazy dog),%str( ));                                             
                                                                                                                                              
    %utl_submit_r64(resolve('                                                                                                                 
    res<-rawToChar(unique(charToRaw("thisisacheckstring")));                                                                                  
    writeClipboard(res);                                                                                                                      
    ')),returnVar=from_r);                                                                                                                    
                                                                                                                                              
    %put from_r=&from_r;                                                                                                                      
                                                                                                                                              
    %utl_submit_r64(resolve('                                                                                                                 
    res<-rawToChar(unique(charToRaw("&str")));                                                                                                
    res<-as.character(res);                                                                                                                   
    str(res);                                                                                                                                 
    writeClipboard(res);                                                                                                                      
    writeClipboard(res);                                                                                                                      
    '),returnVar=from_r );                                                                                                                    
                                                                                                                                              
    %put from_r=&from_r;                                                                                                                      
                                                                                                                                              
    /*                    _   _                                                                                                               
      ___     _ __  _   _| |_| |__   ___  _ __                                                                                                
     / _ \   | `_ \| | | | __| `_ \ / _ \| `_ \                                                                                               
    |  __/_  | |_) | |_| | |_| | | | (_) | | | |                                                                                              
     \___(_) | .__/ \__, |\__|_| |_|\___/|_| |_|                                                                                              
             |_|    |___/                                                                                                                     
    */                                                                                                                                        
                                                                                                                                              
    %let str=thisisacheckstring;                                                                                                              
                                                                                                                                              
    %let str=%qcompress(%qlowcase(the quickee brownee foxxy jumps allover the lazy dog),%str( ));                                             
                                                                                                                                              
    %utl_submit_py64_38("                                                                                                                     
    import pyperclip;                                                                                                                         
    from collections import OrderedDict;                                                                                                      
    s  ='&str';                                                                                                                               
    od = OrderedDict.fromkeys(s).keys();                                                                                                      
    res=''.join(od);                                                                                                                          
    print(res);                                                                                                                               
    pyperclip.copy(res);                                                                                                                      
    ",return=from_py);                                                                                                                        
                                                                                                                                              
    %put from_py=&from_py;                                                                                                                    
                                                                                                                                              
    from_py=thequickbrownfxyjmpsalvzdg                                                                                                        
                                                                                                                                              
                                                                                                                                              
