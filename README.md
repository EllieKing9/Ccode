# Ccode

```
#include <stdio.h>
#define LEN_INPUT 1000001

#include <stdlib.h>

int main(void) {
    char s1[LEN_INPUT];
    scanf("%s", s1);
    
    // printf("%s", ptr_s2);
    
    // char *ptr_s2 = (char *)malloc(strlen(s1));
    // memcpy(ptr_s2, s1, sizeof(s1));
    char *ptr_s2 = s1;
    // char *ptr_s2 = &s1;
    // strcpy(ptr_s2, s1);
    // printf("%s\n", ptr_s2);

    // printf("%d\n", strlen(s1));
    // printf("%d\n", strlen(ptr_s2));
    // printf("%d\n", sizeof(s1));
    // printf("%d\n", sizeof(ptr_s2));
    // printf("%x\n", &ptr_s2);
    // printf("%x\n", ptr_s2);
    // printf("%x\n", s1);
    // printf("%d\n", sizeof(char));
    // printf("%d\n", sizeof(int));
    
    for(int i = 0; i < strlen(ptr_s2); i++) {
        printf("%c", ptr_s2[i]);
    }
    
    // free(ptr_s2);
    return 0;
}
```
