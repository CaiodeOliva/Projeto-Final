#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Veiculo {
    char proprietario[50];
    char combustivel[10];
    char modelo[50];
    char cor[20];
    char chassi[20];
    int ano;
    char placa[8];
    struct Veiculo *prox;
} Veiculo;

Veiculo *adicionaVeiculo(Veiculo *lista, char proprietario[], char combustivel[], char modelo[], char cor[], char chassi[], int ano, char placa[]) {
    Veiculo *novoVeiculo = (Veiculo *)malloc(sizeof(Veiculo));
    strcpy(novoVeiculo->proprietario, proprietario);
    strcpy(novoVeiculo->combustivel, combustivel);
    strcpy(novoVeiculo->modelo, modelo);
    strcpy(novoVeiculo->cor, cor);
    strcpy(novoVeiculo->chassi, chassi);
    novoVeiculo->ano = ano;
    strcpy(novoVeiculo->placa, placa);
    novoVeiculo->prox = lista;

    return novoVeiculo;
}

void listaPorAnoCombustivel(Veiculo *lista) {
    Veiculo *aux = lista;

    printf("\nProprietarios com carros de 2010 ou posterior e movidos a diesel:\n");
    while (aux != NULL) {
        if (aux->ano >= 2010 && strcmp(aux->combustivel, "diesel") == 0) {
            printf("Proprietario: %s\n", aux->proprietario);
        }
        aux = aux->prox;
    }
}

void listaPlacasJ(Veiculo *lista) {
    Veiculo *aux = lista;

    printf("\nPlacas que comecam com J e terminam com 0, 2, 4 ou 7, e seus proprietarios:\n");
    while (aux != NULL) {
        if (aux->placa[0] == 'J' && (aux->placa[6] == '0' || aux->placa[6] == '2' || aux->placa[6] == '4' || aux->placa[6] == '7')) {
            printf("Placa: %s, Proprietario: %s\n", aux->placa, aux->proprietario);
        }
        aux = aux->prox;
    }
}

void listaModeloCor(Veiculo *lista) {
    Veiculo *aux = lista;

    printf("\nModelo e cor dos veiculos com placas que possuem como segunda letra uma vogal e cuja soma dos valores numericos fornece um numero par:\n");
    while (aux != NULL) {
        if ((aux->placa[1] == 'A' || aux->placa[1] == 'E' || aux->placa[1] == 'I' || aux->placa[1] == 'O' || aux->placa[1] == 'U') &&
            (aux->placa[2] + aux->placa[3] + aux->placa[4] + aux->placa[5] != 0) && ((aux->placa[2] + aux->placa[3] + aux->placa[4] + aux->placa[5]) % 2 == 0)) {
            printf("Modelo: %s, Cor: %s\n", aux->modelo, aux->cor);
        }
        aux = aux->prox;
    }
}

void trocaProprietario(Veiculo *lista, char chassi[], char novoProprietario[]) {
    Veiculo *aux = lista;

    while (aux != NULL) {
        if (strcmp(aux->chassi, chassi) == 0 && strchr(aux->placa, '0') == NULL) {
            strcpy(aux->proprietario, novoProprietario);
            printf("Proprietario alterado com sucesso!\n");
            return;
        }
        aux = aux->prox;
    }

    printf("Carro nao encontrado ou placa possui algum digito igual a zero.\n");
}

void imprimeLista(Veiculo *lista) {
    Veiculo *aux = lista;

    while (aux != NULL) {
        printf("\nProprietario: %s\n", aux->proprietario);
        printf("Combustivel: %s\n", aux->combustivel);
        printf("Modelo: %s\n", aux->modelo);
        printf("Cor: %s\n", aux->cor);
        printf("Chassi: %s\n", aux->chassi);
        printf("Ano: %d\n", aux->ano);
        printf("Placa: %s\n", aux->placa);

        aux = aux->prox;
    }
}

int main() {
    Veiculo *lista = NULL;

    
    lista = adicionaVeiculo(lista, "Proprietario1", "diesel", "Modelo1", "Cor1", "Chassi1", 2015, "JAB1234");
    lista = adicionaVeiculo(lista, "Proprietario2", "gasolina", "Modelo2", "Cor2", "Chassi2", 2012, "JBC5678");
    lista = adicionaVeiculo(lista, "Proprietario3", "diesel", "Modelo3", "Cor3", "Chassi3", 2010, "JDE9012");

   
    listaPorAnoCombustivel(lista);
    listaPlacasJ(lista);
    listaModeloCor(lista);
    trocaProprietario(lista, "Chassi2", "NovoProprietario");
    imprimeLista(lista);

    return 0;
}