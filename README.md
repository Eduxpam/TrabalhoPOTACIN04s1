# TrabalhoPOTACIN04s1
BuscaBinariaAluno
Detalhes#include<stdio.h>
#define TAM 3
struct Aluno{
	int matricula;
	char nome[40];
	float nota1,nota2;
};
struct Aluno v[TAM];


int buscaBin(int tam,struct Aluno v[], int pesq)//funcao buscabinaria
{
	int ini=0,fim=tam-1,meio;
	while(ini<=fim)
	{
		meio=(ini+fim)/2;
		if(pesq==v[meio].matricula)
		return meio;
		else if(v[meio].matricula<pesq) ini=meio+1;
		else fim=meio-1;
	}
	return -1;
}
int main ()
{
	int busca, i,j,temp; 
	char resp,tempnome[40],tempnota1,tempnota2;
	printf("Informe os dados :\n");
	for(i=0;i<TAM;i++)
	{
		printf("\nmatricula: ");
		scanf("%d",&v[i].matricula);
		getchar();
		printf("Nome: ");
		gets(v[i].nome);
		printf("Nota1: ");
		scanf("%f",&v[i].nota1);
		printf("Nota2: ");
		scanf("%f",&v[i].nota2);
	}
	//ordenação
	for(i=0;i<TAM;i++)
	for(j=i+1;j<TAM;j++)
	if(v[i].matricula>v[j].matricula){
		temp=v[i].matricula;		
		v[i].matricula=v[j].matricula;
		v[j].matricula=temp;
		
	}
	
	for(int i=0; (i < TAM); i++){
		printf("%i\t%s\t%1.2f\n",v[i].matricula,v[i].nome,
                        (v[i].nota1 + v[i].nota2)/2);

	}     

	printf("\nInforme a matricula a ser encontrada: ");
	scanf("%d",&busca);	
	resp=buscaBin(TAM,v,busca);
	if(resp==-1)
		printf("\nNao encontrado!\n\n");
	else
		printf("\nA matricula %d foi encontrada \n\n",v[resp].matricula);
			
return 0;
}
