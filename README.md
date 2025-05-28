![LinkedIn cover - 22](https://github.com/user-attachments/assets/4c83fd04-0518-4c96-bbc9-f96b2cae5638)


# Sistema de Consultas Médicas - Clean Architecture

## 📋 Sobre o Projeto

Sistema para gerenciamento de consultas médicas desenvolvido em Java com Spring Boot, seguindo os princípios da Clean Architecture. O sistema permite o cadastro e gerenciamento de pacientes, médicos, usuários e consultas médicas.

## 🏗️ Arquitetura

O projeto segue os princípios da Clean Architecture, organizando o código em camadas bem definidas:

```
src/main/java/io/github/clean_arquiteture/
├── application/
│   └── DTO/
│       ├── request/     # DTOs para requisições
│       └── response/    # DTOs para respostas
├── domain/
│   └── enumerator/      # Enums do domínio
└── infrastructure/
    └── persistence/
        ├── entity/      # Entidades JPA
        └── repository/  # Repositórios Spring Data
```

### Camadas da Arquitetura

- **Application Layer**: Contém os DTOs (Data Transfer Objects) para comunicação entre as camadas
- **Domain Layer**: Contém as regras de negócio e enumeradores do domínio
- **Infrastructure Layer**: Contém a implementação de persistência com JPA/Hibernate

## 🚀 Tecnologias Utilizadas

- **Java 17+**
- **Spring Boot**
- **Spring Data JPA**
- **Hibernate**
- **Bean Validation**
- **Lombok**
- **Maven**

## 📊 Modelo de Dados

### Entidades Principais

#### Paciente
- ID, Nome, CPF, Endereço, Telefone
- Data de Nascimento
- Lista de Consultas

#### Médico
- ID, Nome, CRM
- Lista de Consultas

#### Consulta
- ID, Data da Consulta, Status
- Referência ao Paciente e Médico

#### Usuário
- ID, Nome, Email, Senha
- Perfil (ATENDENTE, MEDICO, PACIENTE)

### Enumeradores

#### StatusConsultaEnum
- `CONFIRMADA`
- `NAO_CONFIRMADA`
- `CANCELADA`
- `REAGENDADA`
- `EM_ATENDIMENTO`

#### PerfilEnum
- `ATENDENTE`
- `MEDICO`
- `PACIENTE`

#### EspecialidadeEnum
- `CARDIOLOGISTA`
- `ORTOPEDISTA`
- `PEDIATRIA`
- `OFTAMOLOGISTA`
- `NEUROLOGISTA`

## 🔧 Configuração e Instalação

### Pré-requisitos

- Java 17 ou superior
- Maven 3.6+
- Banco de dados (configuração necessária)

### Passos para Executar

1. **Clone o repositório**
```bash
git clone <url-do-repositorio>
cd clean-arquiteture
```

2. **Configure o banco de dados**
   - Edite o arquivo `application.properties` ou `application.yml`
   - Configure as propriedades de conexão com o banco

3. **Execute o projeto**
```bash
mvn spring-boot:run
```

## 📝 Validações Implementadas

### PacienteRequestDTO
- Nome: obrigatório, 2-100 caracteres
- CPF: obrigatório, formato 123.456.789-00 ou 12345678900
- Endereço: máximo 200 caracteres
- Telefone: formato (99) 99999-9999 ou (99) 9999-9999
- Data de nascimento: obrigatória, no passado ou presente

### MedicoRequestDTO
- Nome: obrigatório, 3-100 caracteres
- CRM: obrigatório, formato 123456-SP

### UsuarioRequestDTO
- Nome: obrigatório, 2-100 caracteres
- Email: obrigatório, formato válido, máximo 100 caracteres
- Senha: obrigatória, 8-50 caracteres, deve conter:
  - Pelo menos uma letra maiúscula
  - Pelo menos uma letra minúscula
  - Pelo menos um número
  - Pelo menos um caractere especial

### ConsultaRequestDTO
- Data da consulta: obrigatória, deve estar no futuro
- Status: obrigatório
- Paciente e Médico: obrigatórios com validação completa

## 🛠️ Estrutura de DTOs

### Request DTOs
Utilizados para receber dados das requisições com validações completas.

### Response DTOs
Utilizados para retornar dados nas respostas, sem exposição de informações sensíveis como senhas.

## 🔐 Segurança

- Validação de entrada em todos os DTOs
- Senha com critérios de segurança obrigatórios
- Validação de CPF utilizando anotação específica do Hibernate Validator

## 📋 Funcionalidades

- ✅ Cadastro e gerenciamento de pacientes
- ✅ Cadastro e gerenciamento de médicos
- ✅ Cadastro e gerenciamento de usuários
- ✅ Agendamento e controle de consultas
- ✅ Validação completa de dados de entrada
- ✅ Estrutura preparada para diferentes perfis de usuário

## 🚧 Próximos Passos

- [ ] Implementação da camada de Use Cases
- [ ] Implementação dos Controllers REST
- [ ] Autenticação e autorização
- [ ] Testes unitários e de integração
- [ ] Documentação da API com Swagger
- [ ] Implementação de logs e monitoramento

## 🤝 Contribuição

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`)
3. Commit suas mudanças (`git commit -am 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/nova-feature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença [MIT](LICENSE).

## 👥 Autores

- Desenvolvido seguindo os princípios da Clean Architecture
- Estrutura modular e extensível para fácil manutenção

---

**Nota**: Este projeto está em desenvolvimento ativo. Algumas funcionalidades podem estar em implementação.
