## RELATÓRIO TÉCNICO - PROJETO FINAL LASD
AUTORA: YASMIN SANTOS GONÇALVES

  Este projeto teve como objetivo expandir as capacidades de um processador RISC-V de ciclo único, desenvolvido a partir da arquitetura da Sprint 8, através da implementação de novas instruções que aumentassem sua funcionalidade. Foram adicionadas as instruções JAL (Jump and Link) e JR (Jump Register) para melhorar o controle de fluxo, além das operações lógicas ANDI, ORI e o deslocamento SRL (Shift Right Logical), mantendo a estrutura básica de ciclo único e garantindo compatibilidade com o conjunto de instruções padrão do RISC-V.

  A  implementação da instrução JAL demandou várias modificações no caminho de dados, incluindo a expansão do MUX de seleção de imediato para suportar o tipo J, que combina bits não contíguos da instrução. O MUX ResultSrc foi ampliado de 2:1 para 4:1 para permitir a seleção de PC+4 como valor de retorno, enquanto a lógica de PCSrc foi atualizada para incluir o sinal Jump, resultando na equação PCSrc = (Branch & Zero) | Jump.

  Para as instruções ANDI e ORI, foram adicionados os sinais de controle correspondentes na Unidade de Controle, identificáveis pelo opcode 0010011 e pelos valores de funct3 (111 para ANDI e 110 para ORI). Ambas utilizam o caminho de dados existente, aproveitando a extensão de imediato tipo I e as operações lógicas já implementadas na ULA.

  A instrução SRL exigiu a inclusão de uma nova operação na ULA (código 101) para realizar o deslocamento à direita com preenchimento de zeros. A pseudo-instrução JR, implementada como JALR x0, x1, 0, necessitou da criação de um MUX JR adicional que seleciona entre PC e rd1SrcA baseado no sinal Jr, alimentando o cálculo de ImmPC como Imm + outJR para permitir saltos para endereços em registradores.

  Os testes realizados incluíram a verificação do armazenamento correto do endereço de retorno em JAL, a precisão dos saltos condicionais e incondicionais (JAL/JR), os resultados das operações lógicas e de deslocamento (ANDI/ORI/SRL), e a preservação do contexto dos registradores. Cada módulo foi testado individualmente antes da verificação integral do caminho de dados.

  O projeto foi concluído com sucesso, alcançando maior flexibilidade no controle de fluxo, novas operações lógicas e de deslocamento, manutenção da arquitetura de ciclo único e total compatibilidade com o RISC-V básico. Toda a documentação e versionamento estão disponíveis no repositório do projeto, com os detalhes de implementação e resultados de testes devidamente registrados.

YASMIN SANTOS GONÇALVES
DESENVOLVEDORA DO PROJETO

