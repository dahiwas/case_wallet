# case_wallet

 As carteiras digitais, protegidas por "seed phrases", são essenciais para transações com criptomoedas. Contudo, para maior segurança, muitos preferem as Hardware Wallets, que isolam as chaves privadas da internet, reduzindo o risco de ataques cibernéticos. Aqui será descrito um exploit de um caso de uma pessoa que possuía mais de 1 milhão de dólares armazenados em um hardwallet, porém, não tinha mais o acesso.

# O que são carteiras digitais?
São softwares que permitem transacionar/mover criptoativos pela web3. A chamada web3, seria a terceira geração da internet, que busca criar uma rede descentralizada baseada na tecnologia blockchain. Possui o objetivo de promover uma internet mais segura.

# O que são seed phrases?
É o sistema de segurança dessas carteiras digitais, ou seja, dependendo da carteira alocada, é gerada 9 - 16 palavras aleatórias. A sequência dessas palavras é única/exclusiva para o usuário. Dessa forma, a única forma de poder acessá-la caso perca o acesso, é através da seed phrase.

# O que são Hardware Wallet
Como as carteiras digitais são softwares, elas podem ser invadidas por meio de softwares maliciosos, permitindo o saque da maior parte de seus criptoativos. Por isso, foram criadas as hardware wallets, ou seja, carteiras digitais físicas. A cada transação, é necessária uma verificação manual no dispositivo para confirmar a transação.

# O que é uma Trezor?
É um modelo de Hardware Wallet.

# Exploit 
## Caso: https://www.theverge.com/2022/1/24/22898712/crypto-hardware-wallet-hacking-lost-bitcoin-ethereum-nft
### Contexto
No início de 2018, Dan Reich e um amigo investiram $50.000 em tokens Theta, quando estavam cotados a 21 centavos cada. Devido a uma repressão à criptomoeda na China, eles transferiram seus tokens para uma carteira de hardware Trezor One para segurança. Eles esqueceram o PIN da carteira, que era na verdade um número de cinco dígitos. Após várias tentativas falhas, eles pararam de tentar para evitar a exclusão automática dos dados da carteira. 
O valor do token Theta disparou, atingindo mais de $3 milhões no pico. Esse aumento significativo no valor os motivou a encontrar uma maneira de acessar a carteira sem o PIN.
### Buscando uma Solução
Joe Grand: Um experiente hacker de hardware e engenheiro elétrico com um histórico de realizações notáveis. Grand comprou carteiras idênticas para praticar e desenvolveu um método para acessar a carteira usando injeção de falhas.
Em resumo, existem três níveis de segurança disponíveis para o microcontrolador usado nas carteiras Trezor:
- RDP2: Não permite leitura da RAM
- RDP1: Permite leitura da RAM
- RDP0: Permite leitura da RAM

O que se tentou fazer foi dar downgrade no firmware RDP2 -> RDP1, forçando-o entrar no modo de atualização.

Grand aperfeiçoou o método ao descobrir que, na versão do firmware da carteira de Reich, o PIN e a chave ainda eram copiados para a RAM ao ligar o dispositivo. Glitchando o dispositivo no momento certo, ele podia baixar o nível de segurança e acessar o PIN e a chave, mantendo-os seguros na memória flash caso a RAM fosse apagada precipitadamente. Esse método exigia brute force para descobrir o melhor ajuste da voltagem para atingir o momento exato de baixar a segurança, mas era mais seguro e eficaz, permitindo eventualmente acessar os fundos da carteira após várias horas de tentativas.

### Conclusão
Reitera-se os desafios contínuos de proteger contra técnicas de hacking, mesmo com hardware wallets, visto que são vistos como protegidos, sempre há formas de se extrair as informações necessárias.
