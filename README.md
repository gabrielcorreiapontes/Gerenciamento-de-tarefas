# 📋 API de Gerenciamento de Tarefas (To-Do List)

Uma API REST completa para gerenciamento de tarefas pessoais, desenvolvida com **Flask**.

## 📖 Descrição

Este projeto é uma API REST que permite criar, ler, atualizar e deletar tarefas (CRUD completo). A API foi desenvolvida utilizando funções integradas do Flask e oferece funcionalidades como filtragem, estatísticas e marcação de tarefas como concluídas.

## 🚀 Funcionalidades

### Operações CRUD
- **Criar tarefa** - Adiciona uma nova tarefa com título, descrição e prioridade
- **Listar tarefas** - Retorna todas as tarefas cadastradas
- **Buscar tarefa** - Busca uma tarefa específica pelo ID
- **Atualizar tarefa** - Modifica os dados de uma tarefa existente
- **Remover tarefa** - Exclui uma tarefa do sistema

### Funcionalidades Extras
- **Marcar como concluída** - Marca rapidamente uma tarefa como finalizada
- **Filtrar tarefas** - Filtra por status (concluída/pendente) ou prioridade (baixa/média/alta)
- **Estatísticas** - Exibe métricas como total de tarefas, taxa de conclusão e contagem por prioridade

## 🛠️ Funções Flask Utilizadas

| Função | Descrição |
|--------|-----------|
| `Flask()` | Inicializa a aplicação Flask |
| `@app.route()` | Define rotas/endpoints da API |
| `request.get_json()` | Obtém dados JSON do corpo da requisição |
| `request.args.get()` | Obtém parâmetros da query string |
| `jsonify()` | Converte dados Python para resposta JSON |
| `@app.errorhandler()` | Tratamento personalizado de erros |
| `app.run()` | Inicia o servidor de desenvolvimento |

## 📦 Instalação

1. Clone ou baixe este projeto

2. Crie um ambiente virtual (recomendado):
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

3. Instale as dependências:
```bash
pip install -r requirements.txt
```

4. Execute o servidor:
```bash
python app.py
```

O servidor estará disponível em `http://localhost:5000`

## 📡 Endpoints da API

### Informações
| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/` | Informações da API e lista de endpoints |

### Tarefas
| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/tarefas` | Lista todas as tarefas |
| GET | `/tarefas/<id>` | Busca tarefa por ID |
| POST | `/tarefas` | Cria nova tarefa |
| PUT | `/tarefas/<id>` | Atualiza tarefa |
| DELETE | `/tarefas/<id>` | Remove tarefa |
| PUT | `/tarefas/<id>/concluir` | Marca como concluída |
| GET | `/tarefas/estatisticas` | Estatísticas gerais |
| GET | `/tarefas/filtrar` | Filtra tarefas |

## 📝 Exemplos de Uso

### Criar uma tarefa
```bash
curl -X POST http://localhost:5000/tarefas \
  -H "Content-Type: application/json" \
  -d '{"titulo": "Estudar Flask", "descricao": "Aprender sobre rotas e requisições", "prioridade": "alta"}'
```

### Listar todas as tarefas
```bash
curl http://localhost:5000/tarefas
```

### Buscar tarefa específica
```bash
curl http://localhost:5000/tarefas/1
```

### Atualizar uma tarefa
```bash
curl -X PUT http://localhost:5000/tarefas/1 \
  -H "Content-Type: application/json" \
  -d '{"titulo": "Estudar Flask Avançado", "prioridade": "media"}'
```

### Marcar tarefa como concluída
```bash
curl -X PUT http://localhost:5000/tarefas/1/concluir
```

### Filtrar tarefas pendentes de alta prioridade
```bash
curl "http://localhost:5000/tarefas/filtrar?status=pendente&prioridade=alta"
```

### Ver estatísticas
```bash
curl http://localhost:5000/tarefas/estatisticas
```

### Remover uma tarefa
```bash
curl -X DELETE http://localhost:5000/tarefas/1
```

## 📊 Estrutura da Tarefa

```json
{
  "id": 1,
  "titulo": "Estudar Flask",
  "descricao": "Aprender sobre rotas e requisições",
  "prioridade": "alta",
  "concluida": false,
  "criada_em": "2024-01-15T10:30:00",
  "atualizada_em": "2024-01-15T10:30:00"
}
```

### Campos
- **id** (int): Identificador único da tarefa
- **titulo** (string): Título da tarefa (obrigatório)
- **descricao** (string): Descrição detalhada (opcional)
- **prioridade** (string): "baixa", "media" ou "alta" (padrão: "media")
- **concluida** (boolean): Status de conclusão
- **criada_em** (datetime): Data/hora de criação
- **atualizada_em** (datetime): Data/hora da última atualização

## 🏗️ Estrutura do Projeto

```
todo_api/
├── app.py              # Aplicação principal Flask
├── requirements.txt    # Dependências do projeto
└── README.md          # Documentação
```

## 🔧 Tecnologias Utilizadas

- **Python 3.8+**
- **Flask 3.0.0** - Microframework web
- **Werkzeug 3.0.1** - Biblioteca WSGI

## 📄 Licença

Este projeto é de código aberto e pode ser utilizado livremente para fins educacionais.
