# Sistema Bancário - Python POO

Sistema bancário desenvolvido em Python utilizando Programação Orientada a Objetos (POO), aplicando conceitos de classes, herança, polimorfismo e abstração.

## 📋 Descrição

Este é um sistema bancário completo que permite gerenciar clientes, contas correntes e transações financeiras (depósitos e saques). O sistema foi desenvolvido seguindo os princípios SOLID e boas práticas de programação orientada a objetos.

## 🚀 Funcionalidades

- **Gerenciamento de Clientes**
  - Cadastro de novos clientes (Pessoa Física)
  - Armazenamento de dados pessoais (CPF, nome, data de nascimento, endereço)

- **Gerenciamento de Contas**
  - Criação de contas correntes
  - Listagem de todas as contas cadastradas
  - Vinculação de contas aos clientes

- **Operações Bancárias**
  - **Depósito**: Adicionar valores à conta
  - **Saque**: Retirar valores (com limites de valor e quantidade)
  - **Extrato**: Visualizar histórico de transações e saldo atual

## 🏗️ Estrutura do Projeto

### Classes Principais

#### `Cliente`
Classe base para representar um cliente do banco.
- Atributos: `endereco`, `contas`
- Métodos: `realizar_transacao()`, `adicionar_conta()`

#### `PessoaFisica` (herda de Cliente)
Representa um cliente pessoa física.
- Atributos adicionais: `nome`, `data_nascimento`, `cpf`

#### `Conta`
Classe base para representar uma conta bancária.
- Atributos: `_saldo`, `_numero`, `_agencia`, `_cliente`, `_historico`
- Métodos: `sacar()`, `depositar()`, `nova_conta()`
- Properties: `saldo`, `numero`, `agencia`, `cliente`, `historico`

#### `ContaCorrente` (herda de Conta)
Implementação específica de conta corrente com limites.
- Atributos adicionais: `_limite` (R$ 500,00), `_limite_saques` (3 saques)
- Sobrescreve o método `sacar()` com validações adicionais

#### `Historico`
Gerencia o histórico de transações de uma conta.
- Métodos: `adicionar_transacao()`
- Property: `transacoes`

#### `Transacao` (ABC)
Classe abstrata base para transações.
- Métodos abstratos: `valor`, `registrar()`

#### `Saque` e `Deposito` (herdam de Transacao)
Implementações concretas de transações bancárias.

## 🎮 Como Usar

### Requisitos
- Python 3.6 ou superior

### Executando o Sistema

```bash
python sistema_bancario.py
```

### Menu de Opções

```
================ MENU ================
[d]    Depositar
[s]    Sacar
[e]    Extrato
[nc]   Nova conta
[lc]   Listar contas
[nu]   Novo usuário
[q]    Sair
```

## 📝 Fluxo de Uso Recomendado

1. **Criar um novo usuário** (`nu`)
   - Informe CPF (somente números)
   - Nome completo
   - Data de nascimento (dd-mm-aaaa)
   - Endereço completo

2. **Criar uma conta** (`nc`)
   - Informe o CPF do cliente cadastrado
   - Conta será criada automaticamente com agência "0001"

3. **Realizar operações** (`d`, `s`, `e`)
   - Informe o CPF do cliente
   - Execute a operação desejada

## 🔒 Regras de Negócio

### Limites da Conta Corrente
- **Limite por saque**: R$ 500,00
- **Número máximo de saques diários**: 3
- **Agência padrão**: 0001

### Validações
- ✅ Não é possível sacar valor superior ao saldo disponível
- ✅ Não é possível realizar mais de 3 saques por dia
- ✅ Valores negativos ou zero são rejeitados
- ✅ Cliente deve estar cadastrado para realizar operações
- ✅ Cliente deve possuir conta para realizar transações

## 🎯 Conceitos de POO Aplicados

### Encapsulamento
- Atributos privados (com underscore `_`)
- Acesso controlado através de properties

### Herança
- `PessoaFisica` herda de `Cliente`
- `ContaCorrente` herda de `Conta`
- `Saque` e `Deposito` herdam de `Transacao`

### Abstração
- Classe abstrata `Transacao` define interface comum
- Uso de `ABC` (Abstract Base Class)

### Polimorfismo
- Método `sacar()` sobrescrito em `ContaCorrente`
- Diferentes tipos de transações com comportamentos específicos

## 📊 Exemplo de Uso

```python
# 1. Criar cliente
Nome: João Silva
CPF: 12345678900
Data: 01-01-1990
Endereço: Rua A, 123 - Centro - São Paulo/SP

# 2. Criar conta
CPF: 12345678900
Conta criada: Agência 0001, C/C 1

# 3. Depositar
Valor: R$ 1000,00
✅ Depósito realizado com sucesso!

# 4. Sacar
Valor: R$ 300,00
✅ Saque realizado com sucesso!

# 5. Extrato
Deposito: R$ 1000.00
Saque: R$ 300.00
Saldo: R$ 700.00
```

## 🐛 Observações

- **FIXME**: Atualmente não permite ao cliente escolher a conta quando possui múltiplas contas (sempre usa a primeira)
- O sistema armazena dados apenas em memória (não há persistência em banco de dados)

## 🛠️ Possíveis Melhorias

- [ ] Adicionar persistência de dados (banco de dados ou arquivos)
- [ ] Implementar escolha de conta para clientes com múltiplas contas
- [ ] Adicionar autenticação e segurança
- [ ] Implementar outras modalidades de conta (Poupança, Salário)
- [ ] Adicionar mais tipos de transações (Transferência, PIX)
- [ ] Implementar testes unitários
- [ ] Adicionar validação de CPF
- [ ] Criar interface gráfica (GUI)

## 👨‍💻 Autor

Sistema desenvolvido como projeto de estudo de Programação Orientada a Objetos em Python.

## 📄 Licença

Este projeto é de uso educacional e livre para modificações.

---

**Desenvolvido com Python 🐍 | POO | Clean Code**