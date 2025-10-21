#include <stdio.h>
#include <string.h>

#define MAX_TERRITORIOS 10
#define TAM_NOME 50

// Estrutura que representa um território
typedef struct {
    char nome[TAM_NOME];
    char continente[TAM_NOME];
    int exercitos;
} Territorio;

int main() {
    Territorio territorios[MAX_TERRITORIOS];
    int qtd, i;

    printf("=== CADASTRO DE TERRITORIOS ===\n");
    printf("Quantos territorios deseja cadastrar (max %d)? ", MAX_TERRITORIOS);
    scanf("%d", &qtd);
    getchar(); // limpa buffer do enter

    if (qtd > MAX_TERRITORIOS || qtd <= 0) {
        printf("Quantidade invalida!\n");
        return 1;
    }

    for (i = 0; i < qtd; i++) {
        printf("\n--- Territorio %d ---\n", i + 1);

        printf("Nome: ");
        fgets(territorios[i].nome, TAM_NOME, stdin);
        territorios[i].nome[strcspn(territorios[i].nome, "\n")] = 0;

        printf("Continente: ");
        fgets(territorios[i].continente, TAM_NOME, stdin);
        territorios[i].continente[strcspn(territorios[i].continente, "\n")] = 0;

        printf("Numero de exercitos: ");
        scanf("%d", &territorios[i].exercitos);
        getchar(); // limpa buffer
    }

    printf("\n=== LISTA DE TERRITORIOS ===\n");
    for (i = 0; i < qtd; i++) {
        printf("Territorio %d:\n", i + 1);
        printf("  Nome: %s\n", territorios[i].nome);
        printf("  Continente: %s\n", territorios[i].continente);
        printf("  Exercitos: %d\n", territorios[i].exercitos);
        printf("---------------------------\n");
    }

    return 0;
}
