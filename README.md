# Logica-Super-trunfo-Novato
#include <stdio.h>
#define TAM_COD  4
#define TAM_NOME 100

typedef struct {
    char estado;
    char codigo[TAM_COD];
    char cidade[TAM_NOME];
    int  populacao;
    float area_km2;
    float pib;
    int  pontos_turisticos;
} Carta;

void ler_carta(Carta *c, int idx) {
    printf("\n=== Cadastrar a Carta %d ===\n", idx);

    printf("Estado (A-H): ");
    scanf(" %c", &c->estado);

    printf("Codigo da Carta (ex.: A01): ");
    scanf("%3s", c->codigo);

    printf("Nome da Cidade: ");
    getchar(); // limpa \n que sobrou
    fgets(c->cidade, TAM_NOME, stdin);

    // remover quebra de linha do fgets
    for (int i = 0; c->cidade[i] != '\0'; i++) {
        if (c->cidade[i] == '\n') {
            c->cidade[i] = '\0';
            break;
        }
    }

    printf("Populacao: ");
    scanf("%d", &c->populacao);

    printf("Area (km²): ");
    scanf("%f", &c->area_km2);

    printf("PIB (R$): ");
    scanf("%f", &c->pib);

    printf("Número de Pontos Turisticos: ");
    scanf("%d", &c->pontos_turisticos);
}

void imprimir_carta(Carta c, int idx) {
    printf("\n--- Carta %d ---\n", idx);
    printf("Estado: %c\n", c.estado);
    printf("Codigo: %s\n", c.codigo);
    printf("Cidade: %s\n", c.cidade);
    printf("Populacao: %d\n", c.populacao);
    printf("Area: %.2f km²\n", c.area_km2);
    printf("PIB: %.2f R$\n", c.pib);
    printf("Pontos Turisticos: %d\n", c.pontos_turisticos);
}

int comparar_pib(Carta c1, Carta c2) {
    if (c1.pib > c2.pib) return 1;
    else if (c2.pib > c1.pib) return 2;
    else return 0;
}

int main() {
    Carta c1, c2;

    printf("=== Cadastro de Cartas Super Trunfo ===\n");

    ler_carta(&c1, 1);
    ler_carta(&c2, 2);

    printf("\n=== Cartas Cadastradas ===\n");
    imprimir_carta(c1, 1);
    imprimir_carta(c2, 2);

    // Comparação pelo PIB
    int vencedor = comparar_pib(c1, c2);
    printf("\n=== Resultado da Comparacao (PIB) ===\n");
    if (vencedor == 1)
        printf("Carta 1 venceu!\n");
    else if (vencedor == 2)
        printf("Carta 2 venceu!\n");
    else
        printf("Empate!\n");

    return 0;
}
