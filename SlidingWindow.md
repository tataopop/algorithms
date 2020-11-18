# Sliding Window

```
int findSubstring(string s){
    int[] count = new int[128];
    int counter; // check whether the substring is valid
    int begin=0, end=0; //two pointers, one point to tail and one  head
    int d; //the length of substring

    for() { /* initialize the count[] here */ }

    while(end < s.size()){

        if(count[s.charAt(end++)]--){  /* modify counter here */ }

        while(/* counter condition */){ 

             /* update d here if finding minimum*/

            //increase begin to make it invalid/valid again

            if(count[s.charAt(begin++)]++){ /*modify counter here*/ }
        }  

        /* update d here if finding maximum*/
    }
    return d;
}
```
