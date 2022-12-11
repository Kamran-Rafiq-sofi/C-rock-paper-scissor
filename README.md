# C-rock-paper-scissor

#include<stdio.h>
#include<conio.h>
#include<string.h>
#include<stdlib.h>
#include<time.h>
int main()
 {  
    int input;
    printf("enter length of your name\n");
    scanf("%d",&input);
    char *ptr;
    ptr=(char*)calloc((input+1),sizeof(char));
    //  char name[100];
    static int win=0;
    static int loose=0;
    static int draw=0;
    printf("*******welcome to the world of games*******\n");
    printf("please enter your name to contine\n");
    scanf("%s",ptr);
    printf("hii %s here are the values asigned to rock paper and scissor\n rock=0\n paper=1\n scissor=2\n",ptr );

    int rounds;
    int n;
    playagain:
    printf("Now please enter number of rounds you want to play\n");
    scanf("%d",&rounds);
    for(int i=0;i<rounds;i++){
        srand(time(NULL));
        int s=rand()%3;
        
        repeat:
        printf("%s it's your turn\n", ptr);
        scanf("%d",&n);
        // getchar();
        // if(n>2){
        //     printf("wrong input try again\n");
        //     goto repeat;
        // }
        // else{
        //     continue;
        // }
        printf("%s:%d\n",ptr,n);
        printf("player 2 turn\n");
        printf("Computerr:%d\n",s);
         
        if(n==s){
         printf("round drawn\n");
             draw++;
        }
        else if(n==0 && s==2 || n==1 & s==0 || n==2 && s==1){
            printf("you have won the round\n");
            win++;
        }
        else{
            printf("round lost computer won\n");
            loose++;
        }
          
    }
    printf("\n\n\n");


    if( win==loose || draw==rounds ){
        printf("match drawn\n");
    }
    else if( win>loose  || win>draw && draw>loose){
        printf("hurrah!!!! congratulations %s you have won the game here is your score\n", ptr);
        printf("%s:%d\n",ptr,win);
    }
    else if(win<loose || win<draw && draw<loose){
        printf("oops you have lost the game\n");
    }
int play;
    printf("do you want to play again if yes tab 1\n");
    scanf("%d",&play);
    if(play==1){
        goto playagain;
    }
    else{
        exit;
    }
    free(ptr);

     return 0;
}
