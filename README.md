# Reajuste-de-Salario

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <conio.h>

typedef struct {
	
	float hrsdia, salario, salhora, hrstrab50, hrstrab100, hrmes, noturno, inss, fgts, irrf, salbruto, desc, saliquid, hr50, hr100;
	char nome[50];
	
}contrato;

contrato func[30];

int i=0;

int menu()
{
	
	int opcao;
		
		system("cls");
		printf("---MENU---");
		printf("\n1 - Cadastrar\n2 - Consultar\n3 - Listar\n0 - Sair");
		printf("\n\nOpcao: ");
		scanf("%i", &opcao);
		return opcao;
	
}

void cadastro()
{
	
	char resp, resp2;
	int j=0, k=0;
	
	do{
	system("cls");
		printf("Insira o seu nome: ");
		fflush(stdin);
		gets(func[i].nome);
		printf("Insira o seu salario: ");
		scanf("%f", &func[i].salario);
		printf("Informe quantas horas duram o seu expediente: ");
		scanf("%f", &func[i].hrsdia);
		printf("Informe o numero de horas extras 50%: ");
		scanf("%f", &func[j].hrstrab50);
		printf("Informe o numero de horas extras 100%: ");
		scanf("%f", &func[j].hrstrab100);
		printf("Deseja adicionar um adicional noturno? <S/N>\n");
		resp2=getche();
		
		if(toupper (resp2) == 'S')
		{
			printf("\nInforme o adicional noturno: ");
			scanf("%f", &func[j].noturno);
		}
		
		printf("\n\nDeseja cadastrar outro funcionario? <S/N>\n");
		resp=getche();
		
		j++;
		
	}while(toupper (resp) == 'S' && i<10);
	
	for(k=0; k<i; k++)
	{
		
	if(toupper (resp) == 'S')
	{
			func[j].salhora = func[j].salario / func[j].hrsdia;
	
	func[j].hr50 = (func[j].salhora / 2) * func[j].hrstrab50;
	func[j].hr100 = func[j].salhora * func[j].hrstrab100;
	
	func[j].salbruto = func[j].salario + func[j].noturno + func[j].hr50 + func[j].hr100;
		
		if(func[j].salbruto <= 1830.29)
		{
			func[j].inss = func[j].salbruto * 0.08;
		}
		else if(func[j].salbruto >= 1830.30 && func[j].salario <= 3050.52)
		{
			func[j].inss = func[j].salbruto * 0.09;
		}
		else
		{
			func[j].inss = func[j].salbruto * 0.11;
		}
		
		if(func[j].salbruto <= 1903.98)
		{
			func[j].irrf = 0;
		}
		else if(func[j].salbruto >= 193.99 && func[j].salbruto <= 2826.65)
		{
			func[j].irrf = func[j].salbruto * 0.075;
		}
		else if(func[j].salbruto >= 2826.66 && func[j].salbruto <= 3751.05)
		{
			func[j].irrf = func[j].salbruto * 0.15;
		}
		else if(func[j].salbruto >= 3751.06 && func[j].salbruto <= 4664.68)
		{
			func[j].irrf = func[j].salbruto * 0.225;
		}
		else
		{
			func[j].irrf = func[j].salbruto * 0.275;
		}
		
/////////////////////////////////////////////////////////////////////////////////////////////
		
		if(func[j].salbruto >= 0.01 && func[j].salbruto <= 500)
		{
			func[j].fgts = func[j].salbruto * 0.5;
		}
		else if(func[j].salbruto >= 500.01 && func[j].salbruto <= 1000)
		{
			func[j].fgts = func[j].salbruto * 0.4 + 50;
		}
		else if(func[j].salbruto >= 1000.01 && func[j].salbruto <= 5000)
		{
			func[j].fgts = func[j].salbruto * 0.3 + 150;
		}
		else if(func[j].salbruto >= 5000.01 && func[j].salbruto <= 10000)
		{
			func[j].fgts = func[j].salbruto * 0.2 + 650;
		}
		else if(func[j].salbruto >= 10000.01 && func[j].salbruto <= 15000)
		{
			func[j].fgts = func[j].salbruto * 0.15 + 1150;
		}
		else if(func[j].salbruto >= 15000.01 && func[j].salbruto <= 20000)
		{
			func[j].fgts = func[j].salbruto * 0.1 + 1900;
		}
		else
		{
			func[j].fgts = func[j].salbruto * 0.05 + 2900;
		}
		
		func[j].desc = func[j].inss + func[j].irrf;
		
		func[j].saliquid = func[j].salbruto - func[j].inss - func[j].irrf;
		
	
		}
		else
		{
			
			func[j].salbruto = func[j].salario + func[j].hr50 + func[j].hr100;
		
		if(func[j].salbruto <= 1830.29)
		{
			func[j].inss = func[j].salbruto * 0.08;
		}
		else if(func[j].salbruto >= 1830.30 && func[j].salario <= 3050.52)
		{
			func[j].inss = func[j].salbruto * 0.09;
		}
		else
		{
			func[j].inss = func[j].salbruto * 0.11;
		}
		
/////////////////////////////////////////////////////////////////////////////////////////////////
		
		if(func[j].salbruto <= 1903.98)
		{
			func[j].irrf = 0;
		}
		else if(func[j].salbruto >= 193.99 && func[j].salbruto <= 2826.65)
		{
			func[j].irrf = func[j].salbruto * 0.075;
		}
		else if(func[j].salbruto >= 2826.66 && func[j].salbruto <= 3751.05)
		{
			func[j].irrf = func[j].salbruto * 0.15;
		}
		else if(func[j].salbruto >= 3751.06 && func[j].salbruto <= 4664.68)
		{
			func[j].irrf = func[j].salbruto * 0.225;
		}
		else
		{
			func[j].irrf = func[j].salbruto * 0.275;
		}
		
///////////////////////////////////////////////////////////////////////////////////////////////////
		
		if(func[j].salbruto >= 0.01 && func[j].salbruto <= 500 )
		{
			func[j].fgts = func[j].salbruto * 0.5;
		}
		else if(func[j].salbruto >= 500.01 && func[j].salbruto <= 1000)
		{
			func[j].fgts = func[j].salbruto * 0.4 + 50;
		}
		else if(func[j].salbruto >= 1000.01 && func[j].salbruto <= 5000)
		{
			func[j].fgts = func[j].salbruto * 0.3 + 150;
		}
		else if(func[j].salbruto >= 5000.01 && func[j].salbruto <= 10000)
		{
			func[j].fgts = func[j].salbruto * 0.2 + 650;
		}
		else if(func[j].salbruto >= 10000.01 && func[j].salbruto <= 15000)
		{
			func[j].fgts = func[j].salbruto * 0.15 + 1150;
		}
		else if(func[j].salbruto >= 15000.01 && func[j].salbruto <= 20000)
		{
			func[j].fgts = func[j].salbruto * 0.1 + 1900;
		}
		else
		{
			func[j].fgts = func[j].salbruto * 0.05 + 2900;
		}
		
		func[j].desc = func[j].inss + func[j].irrf;
		
		func[j].saliquid = func[j].salbruto - func[j].inss - func[j].irrf;
		
		};
	
	}

}

void consulta()
{
	int j, flag=0;
	char chave[51];
		
		system("cls");
		printf("Informe o nome a ser pesquisado: ");
		fflush(stdin);
		gets(chave);
		
		for(j=0; j<i; j++)
		{
			if(strcmp(strupr(chave),strupr(func[j].nome))==0)
			{
				printf("\n\nNome: %s\nSalario bruto: %.2f\nDescontos: %.2f\nSalario liquido: %.2f\nFGTS: %.2f\n\n", func[j].nome, func[j].salbruto, func[j].desc, func[j].saliquid, func[j].fgts);
				flag=1;
			}
		}
	
	if(flag == 0)
	{
		printf("\n\nFuncionario nao cadastrado\n\n");
	}
		
	system("pause");
	
}

void listar()
{
	int j=0;
	
		system("cls");
		for(j=0; j<i; j++)
		{
			printf("\n\nNome: %s\nSalario bruto: %.2f\nDescontos: %.2f\nSalario liquido: %.2f\nFGTS: %.2f\n\n", func[j].nome, func[j].salbruto, func[j].desc, func[j].saliquid, func[j].fgts);
		}
	system("pause");
}

main()
{
	int opcao;
	
		do{
			opcao = menu();
			
			switch(opcao)
			{
				case 1: cadastro();
					break;
				case 2: consulta();
					break;
				case 3: listar();
					break;
				case 0: exit(0);
					default:
						{
							printf("\n\n---Opcao Invalida---");
							system("pause");
						}
			}
		}while(opcao != 0);
}
