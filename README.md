#include <stdio.h>

// ===============================
// Função recursiva para Torre
// ===============================
void moverTorre(int casasRestantes) {
    if (casasRestantes == 0) return;
    printf("Direita\n");
    moverTorre(casasRestantes - 1); // Chamada recursiva
}

// ===============================
// Função recursiva para Rainha
// ===============================
void moverRainha(int casasRestantes) {
    if (casasRestantes == 0) return;
    printf("Esquerda\n");
    moverRainha(casasRestantes - 1); // Chamada recursiva
}

// ===============================
// Função recursiva + loops aninhados para Bispo
// ===============================
void moverBispoRecursivo(int linha, int limite) {
    if (linha >= limite) return;

    for (int coluna = linha; coluna < limite; coluna++) {
        printf("Cima Direita\n"); // Movimento diagonal
    }

    moverBispoRecursivo(linha + 1, limite); // Chamada recursiva
}

// ===============================
// Movimento complexo do Cavalo
// Usa loops aninhados, múltiplas variáveis e break/continue
// ===============================
void moverCavalo() {
    printf("Movimento do Cavalo:\n");

    // Duas casas para cima e uma para a direita
    int passosParaCima = 2;
    int passosParaDireita = 1;

    for (int i = 0; i < 3; i++) { // Controla o número de movimentos possíveis
        for (int j = 0; j < 3; j++) {
            if (i == 1 && j == 1) {
                // Caso específico a ignorar
                continue;
            }

            if (i == passosParaCima && j == passosParaDireita) {
                // Movimento válido do Cavalo encontrado
                for (int k = 0; k < passosParaCima; k++) {
                    printf("Cima\n");
                }
                printf("Direita\n");
                break; // Após executar um movimento, sair dos loops
            }
        }
    }
}

int main() {
    // ===============================
    // Torre - 5 casas para a Direita
    // ===============================
    printf("Movimento da Torre:\n");
    moverTorre(5);

    printf("\n");

    // ===============================
    // Bispo - 5 casas na diagonal (recursivo + loops aninhados)
    // ===============================
    printf("Movimento do Bispo:\n");
    moverBispoRecursivo(0, 5); // inicia na linha 0 até 4

    printf("\n");

    // ===============================
    // Rainha - 8 casas para Esquerda
    // ===============================
    printf("Movimento da Rainha:\n");
    moverRainha(8);

    printf("\n");

    // ===============================
    // Cavalo - Movimento em "L" para cima e direita
    // ===============================
    moverCavalo();

    return 0;
}
