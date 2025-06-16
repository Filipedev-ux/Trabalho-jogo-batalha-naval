# Trabalho-jogo-batalha-naval
#include <stdio.h>
#include <stdlib.h>

int main() {
    char tabuleiro[5][5];
    int linha, coluna;
    int navios = 3;
    int i, j;

    for (i = 0; i < 5; i++) {
        for (j = 0; j < 5; j++) {
            tabuleiro[i][j] = '~';
        }
    }

    int naviosPosicoes[3][2] = {{0, 4}, {2, 0}, {3, 2}};

    printf("--- BATALHA NAVAL ---\n");
    printf("Existem %d navios de 1x1 para afundar.\n\n", navios);

    while (navios > 0) {
        printf("  0 1 2 3 4\n");
        for (i = 0; i < 5; i++) {
            printf("%d ", i);
            for (j = 0; j < 5; j++) {
                if (tabuleiro[i][j] == 'S') {
                    printf("~ ");
                } else {
                    printf("%c ", tabuleiro[i][j]);
                }
            }
            printf("\n");
        }

        printf("\nDigite a linha para atirar: ");
        scanf("%d", &linha);
        printf("Digite a coluna para atirar: ");
        scanf("%d", &coluna);

        int acertou = 0;
        for (i = 0; i < 3; i++) {
            if (naviosPosicoes[i][0] == linha && naviosPosicoes[i][1] == coluna) {
                acertou = 1;
                break;
            }
        }

        if (linha < 0 || linha > 4 || coluna < 0 || coluna > 4) {
            printf("\nPosicao invalida! Tente novamente.\n\n");
        } else if (tabuleiro[linha][coluna] == 'X' || tabuleiro[linha][coluna] == 'O') {
            printf("\nVoce ja atirou ai! Tente outra posicao.\n\n");
        } else if (acertou) {
            printf("\nFOGO! Voce acertou um navio!\n\n");
            tabuleiro[linha][coluna] = 'X';
            navios--;
        } else {
            printf("\nAGUA! Voce errou.\n\n");
            tabuleiro[linha][coluna] = 'O';
        }
    }

    printf("\n*** PARABENS! Voce afundou todos os navios! ***\n");

    return 0;
}
