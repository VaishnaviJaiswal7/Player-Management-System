# Player-Management-Syste
#include<stdio.h>
#include<string.h>
typedef struct Player
{
   int jerseyNo;
   char name[20];
   int runs;
   int wickets;
   int playedMatches;
} Player;

void storePlayer(Player*);
void displayPlayer(Player*);
void addPlayer(Player*, int);
void searchPlayer(Player*);
void updatePlayer(Player*);
void deletePlayer(Player*);
void sortPlayer(Player*);
void maxRuns(Player*);
void maxWickets(Player*);	
void display(Player*, int);

int ctr=0;
void main()
{
	Player prr[50];
	//int n=4;
	int exit;
	
	printf("**********Menu**********\n");
	//printf("add number of players:-\n ");
    //scanf("%d", &n);
    
    storePlayer(prr);
	
	do
	{
		printf(" 1.Display Players\n 2.Add Player\n 3.Search Player\n 4.Update Player\n 5.Delete Player\n 6.Sort Players\n 7.Maximum Runs of 3 Player\n 8.Maximum Wickets of 3 PLayer");
		int choice;
		printf("\n\nEnter choice: ");
		scanf("%d",&choice);
		
		switch(choice)
		{
			case 1:
				displayPlayer(prr);
				break;
				
			case 2:
				addPlayer(prr, 50);	
				break;
			
			case 3:
         		searchPlayer(prr);
				break;
				
			case 4:
				updatePlayer(prr);
				break;
				
			case 5:
				deletePlayer(prr);
				break;
				
			case 6:
				sortPlayer(prr);
				break;
				
			case 7:
				maxRuns(prr);
				break;
				
			case 8:
				maxWickets(prr);
				break;						
		} 
		printf("\n\nDo you want to continue (0/1)?");
       	scanf("%d", &exit);
	}while(exit); 
	
}
void storePlayer(Player*prr)
{
	prr[0].jerseyNo=10;
	strcpy(prr[0].name,"Sachin");
	prr[0].runs=1000;
	prr[0].wickets=5;
	prr[0].playedMatches=6;
	ctr++;
	
	prr[1].jerseyNo=7;
	strcpy(prr[1].name,"Dhoni");
	prr[1].runs=1100;
	prr[1].wickets=3;
	prr[1].playedMatches=4;
	ctr++;
	
	prr[2].jerseyNo=45;
	strcpy(prr[2].name,"Rohit");
	prr[2].runs=1200;
	prr[2].wickets=4;
	prr[2].playedMatches=5;
	ctr++;
	
	prr[3].jerseyNo=18;
	strcpy(prr[3].name,"Virat");
	prr[3].runs=500;
	prr[3].wickets=6;
	prr[3].playedMatches=8;
	ctr++;
	
	prr[4].jerseyNo=19;
	strcpy(prr[4].name,"Rahul");
	prr[4].runs=600;
	prr[4].wickets=2;
	prr[4].playedMatches=6;
	ctr++;
	
	prr[5].jerseyNo=48;
	strcpy(prr[5].name,"Raina");
	prr[5].runs=800;
	prr[5].wickets=15;
	prr[5].playedMatches=7;
	ctr++;
	
	prr[6].jerseyNo=33;
	strcpy(prr[6].name,"Hardik");
	prr[6].runs=1020;
	prr[6].wickets=27;
	prr[6].playedMatches=5;
	ctr++;
	
	prr[7].jerseyNo=93;
	strcpy(prr[7].name,"Bumrah");
	prr[7].runs=450;
	prr[7].wickets=35;
	prr[7].playedMatches=7;
	ctr++;
	
	prr[8].jerseyNo=99;
	strcpy(prr[8].name,"Ashwin");
	prr[8].runs=550;
	prr[8].wickets=32;
	prr[8].playedMatches=4;
	ctr++;
	
	prr[9].jerseyNo=8;
	strcpy(prr[9].name,"Jadeja");
	prr[9].runs=750;
	prr[9].wickets=33;
	prr[9].playedMatches=5;
	ctr++;
	
	prr[10].jerseyNo=1;
	strcpy(prr[10].name,"KL Rahul");
	prr[10].runs=1150;
	prr[10].wickets=5;
	prr[10].playedMatches=7;
	ctr++;
}
void displayPlayer(Player*prr)
{
	int i;
	printf("\nPlayer Information\n");
	for(i=0;i<ctr;i++)
	{
		//printf("\nJersey no: %d\t Name: %s\t Runs: %d\t Wickets: %d\t PlayedMatches: %d",prr[i].jerseyNo,prr[i].name,prr[i].runs,prr[i].wickets,prr[i].playedMatches);
		display(prr, i);
	}
}
void addPlayer(Player*prr, int size)
{
	if(ctr<size)
	{
		printf("\n\nEnter the jersey no: ");
		scanf("%d",&prr[ctr].jerseyNo);
		printf("Enter the name: ");
		scanf("%s",&prr[ctr].name);
		printf("Enter the runs: ");
		scanf("%d",&prr[ctr].runs);
		printf("Enter the wickets: ");
		scanf("%d",&prr[ctr].wickets);
		printf("Enter the played match: ");
		scanf("%d",&prr[ctr].playedMatches);
		ctr++;
	}
	else
	{
		printf("\nyour array is full!");
	}
}
void searchPlayer(Player*prr)
{	
	if(ctr>0)
	{
		printf("search player by:\n1.jersey_number\n2.player_name");
		int choice1, jer_num;
		scanf("%d",&choice1);
		if(choice1==1)
		{
			printf("Enter the jersey_number you want to search: ");			
			scanf("%d",&jer_num);
			int flag=0, i;
			for(i=0; i<ctr; i++)
			{
				if(prr[i].jerseyNo==jer_num)
				{
					flag=1;
					display(prr, i);	
					break;
				}
			}
			if(flag==0)
			{
				printf("player not found\n");
			}
		}
		if(choice1==2)
		{
			int res,i,flag=0;
			char player_name[20];
			fflush(stdin);
			printf("Enter the player name you want search:");
			//scanf("%s",&player_name);
			gets(player_name);
			int len=strlen(player_name);
			for(i=0; i<ctr; i++)
			{
				res=strncmp(prr[i].name, player_name, len);
				if(res==0)
				{
					display(prr, i);
					flag=1;					
					//break;
				}				
			}
			if(flag==0)
			{
				printf("player not found");
			}
		}
	}
	else
	{
		printf("\n");
	}
}
void updatePlayer(Player*prr )
{	
	int i, jer_num, flag = 0;
	printf("Enter players jersy number to update player : ");
    scanf("%d", &jer_num);
    for (i=0; i<ctr; i++)
    {
        if (prr[i].jerseyNo==jer_num)
        {
        	
			flag = 1;

         	printf("Enter Runs: ");
         	scanf("%d", &prr[i].runs);
         	printf("Enter wickets : ");
         	scanf("%d", &prr[i].wickets);
         	printf("Enter no_of_matches: ");
         	scanf("%d", &prr[i].playedMatches);

         	printf("updated successfully! \n");
         	
         	display(prr, i);
         	break;
    	}
    }
    if (flag==0)
    {
    printf("No player found with jersey no %d\n", jer_num);
	}
}

void deletePlayer(Player*prr)
{	
	int i, j, flag = 0;
	int jer_num;
	printf("Enter the jersey no. of the player to whom you want to delete\n");
    scanf("%d", &jer_num);
   for (i=0; i<ctr; i++)
   {
    	if(prr[i].jerseyNo==jer_num)
   	    {
   		    flag=1;
   		    for(j=i; j<ctr-1; j++)
   		    {
   		    prr[j] = prr[j + 1];
        	}
        	i--;
        	ctr--;
        	break;
        }
    }   	     
    if(flag==1)
    {
        printf("\nPlayer deleted successfully!");  
    }
    else
    {
    	printf("\nPlayer with jersey number %d not found.", jer_num);
	}
}
void sortPlayer(Player*prr)
{
	int choice;
	printf("\n Enter choice for sorting by\n1.Runs: \n2.Wickets\n");
	scanf("%d",&choice);
	if(choice==1)
	{
		int i,j;
		for(i=0; i<ctr; i++)
		{
			for(j=i+1; j<ctr; j++)
			{
				if(prr[i].runs<prr[j].runs)
				{
					Player temp=prr[i];
					prr[i]=prr[j];
					prr[j]=temp;
				}
			}
		}
		printf("\n Sorted Players in Descending order by Runs:\n");
		for(i=0; i<ctr; i++)
		{
			display(prr, i);
		}
	}
	else if(choice==2)
	{
		int i,j;
		for(i=0; i<ctr; i++)
		{
		for(j=i+1; j<ctr; j++)
			{
				if(prr[i].wickets<prr[j].wickets)
				{
					Player temp=prr[i];
					prr[i]=prr[j];
					prr[j]=temp;
				}
			}
		}
		printf("Sorted Players in Descending order by Wickets:\n");
		for(i=0; i<ctr; i++)
		{
			display(prr, i);
		}   
	} 
	if(choice!=0)
	printf("invalid choice!");
}
void maxRuns(Player* prr)
{
	int i,j;
	for(i=0;i<ctr;i++)
	{
		for(j=i+1;j<ctr;j++)
		{
			if(prr[i].runs<prr[j].runs)
			{
				Player temp=prr[i];
				prr[i]=prr[j];
				prr[j]=temp;
			}
		}
	}
	printf("\nTop 3 Players sorted by Runs:\n");
	for(i=0; i<3; i++)
	{
		display(prr, i);
	}
}
void maxWickets(Player* prr)
{
	int i,j;
	for(i=0;i<ctr;i++)
	{
		for(j=i+1;j<ctr;j++)
		{
			if(prr[i].wickets<prr[j].wickets)
			{
				Player temp=prr[i];
				prr[i]=prr[j];
				prr[j]=temp;
			}
		}
	}
	printf("\nTop 3 Players sorted by wickets:\n");
	for(i=0; i<3; i++)
	{
		display(prr, i);
	}
}
void display(Player*prr, int i)
{
	printf("\nJersey no: %d\t Name: %s\t Runs: %d\t Wickets: %d\t PlayedMatches: %d",prr[i].jerseyNo,prr[i].name,prr[i].runs,prr[i].wickets,prr[i].playedMatches);
}
