#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    srand(time(NULL));

    // Dados das cidades
    char nome1[] = "Manaus", estado1[] = "Amazonas";
    int populacao1 = 4281209;
    float area1 = 1571000.0, pib1 = 42968.0;
    int pontos1 = 10;
    float densidade1 = populacao1 / area1;

    char nome2[] = "Goiânia", estado2[] = "Goiás";
    int populacao2 = 7350483;
    float area2 = 340.086, pib2 = 55247.45;
    int pontos2 = 8;
    float densidade2 = populacao2 / area2;

    int opcao1 = 0, opcao2 = 0;

    printf("===== SUPER TRUNFO - COMPARAÇÃO DE CIDADES =====\n");

    // Menu para o primeiro atributo
    do {
        printf("\nEscolha o primeiro atributo para comparação:\n");
        printf("1 - População\n");
        printf("2 - Área\n");
        printf("3 - PIB\n");
        printf("4 - Pontos turísticos\n");
        printf("5 - Densidade demográfica\n");
        printf("Opção: ");
        scanf("%d", &opcao1);
        if (opcao1 < 1 || opcao1 > 5)
            printf("Opção inválida!\n");
    } while (opcao1 < 1 || opcao1 > 5);

    // Menu para o segundo atributo (dinâmico)
    do {
        printf("\nEscolha o segundo atributo (diferente do primeiro):\n");
        if (opcao1 != 1) printf("1 - População\n");
        if (opcao1 != 2) printf("2 - Área\n");
        if (opcao1 != 3) printf("3 - PIB\n");
        if (opcao1 != 4) printf("4 - Pontos turísticos\n");
        if (opcao1 != 5) printf("5 - Densidade demográfica\n");
        printf("Opção: ");
        scanf("%d", &opcao2);
        if (opcao2 < 1 || opcao2 > 5 || opcao2 == opcao1)
            printf("Opção inválida!\n");
    } while (opcao2 < 1 || opcao2 > 5 || opcao2 == opcao1);

    float v1_attr1 = 0, v2_attr1 = 0;
    float v1_attr2 = 0, v2_attr2 = 0;

    // Atribuição dos valores do primeiro atributo
    switch (opcao1) {
        case 1: v1_attr1 = populacao1; v2_attr1 = populacao2; break;
        case 2: v1_attr1 = area1; v2_attr1 = area2; break;
        case 3: v1_attr1 = pib1; v2_attr1 = pib2; break;
        case 4: v1_attr1 = pontos1; v2_attr1 = pontos2; break;
        case 5: v1_attr1 = densidade1; v2_attr1 = densidade2; break;
    }

    // Atribuição dos valores do segundo atributo
    switch (opcao2) {
        case 1: v1_attr2 = populacao1; v2_attr2 = populacao2; break;
        case 2: v1_attr2 = area1; v2_attr2 = area2; break;
        case 3: v1_attr2 = pib1; v2_attr2 = pib2; break;
        case 4: v1_attr2 = pontos1; v2_attr2 = pontos2; break;
        case 5: v1_attr2 = densidade1; v2_attr2 = densidade2; break;
    }

    // Exibição dos valores escolhidos
    printf("\n===== COMPARAÇÃO =====\n");
    printf("Cidade 1: %s (%s)\n", nome1, estado1);
    printf("Cidade 2: %s (%s)\n\n", nome2, estado2);

    printf("Atributo %d: %.2f x %.2f\n", opcao1, v1_attr1, v2_attr1);
    printf("Atributo %d: %.2f x %.2f\n", opcao2, v1_attr2, v2_attr2);

    // Comparações individuais
    int pontos1_attr = 0, pontos2_attr = 0;

    // Regra: densidade (5) é menor melhor
    if (opcao1 == 5) {
        if (v1_attr1 < v2_attr1) pontos1_attr++;
        else if (v2_attr1 < v1_attr1) pontos2_attr++;
    } else {
        if (v1_attr1 > v2_attr1) pontos1_attr++;
        else if (v2_attr1 > v1_attr1) pontos2_attr++;
    }

    if (opcao2 == 5) {
        if (v1_attr2 < v2_attr2) pontos1_attr++;
        else if (v2_attr2 < v1_attr2) pontos2_attr++;
    } else {
        if (v1_attr2 > v2_attr2) pontos1_attr++;
        else if (v2_attr2 > v1_attr2) pontos2_attr++;
    }

    // Soma final
    float soma1 = v1_attr1 + v1_attr2;
    float soma2 = v2_attr1 + v2_attr2;

    printf("\nSoma dos atributos:\n");
    printf("%s: %.2f\n", nome1, soma1);
    printf("%s: %.2f\n", nome2, soma2);

    // Resultado final
    printf("\n===== RESULTADO =====\n");
    if (soma1 > soma2) {
        printf("🏆 Vencedora: %s (%s)\n", nome1, estado1);
    } else if (soma2 > soma1) {
        printf("🏆 Vencedora: %s (%s)\n", nome2, estado2);
    } else {
        printf("⚖️  Empate!\n");
    }

    return 0;
}
