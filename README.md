git clone https://github.com/seu-usuario/todo-list-app.git
cd todo-list-app
# ToDo List App

## Objetivo
Desenvolver um aplicativo simples para gerenciar tarefas do dia a dia.

## Funcionalidades
1. Adicionar uma tarefa.
2. Listar tarefas.
3. Remover uma tarefa.

## Cronograma de Desenvolvimento
| Etapa                | Descrição                                | Prazo        |
|----------------------|------------------------------------------|--------------|
| Configuração Inicial | Criar repositório e planejar projeto     | Dia 1        |
| Interface do Usuário | Desenvolver interface CLI básica         | Dias 2 - 3   |
| Funcionalidades      | Implementar lógica de adicionar tarefas | Dias 4 - 5   |
| Testes e Ajustes     | Revisão e melhorias                      | Dia 6        |
| Finalização          | Documentação final e entrega            | Dia 7        |
git add README.md
git commit -m "Adiciona README inicial"
git push origin main
# Criando a branch para a interface
git checkout -b feature/interface

# Criando a branch para a lógica de adicionar tarefas
git checkout -b feature/add-task

# Criando a branch para a lógica de remover tarefas
git checkout -b feature/remove-task
# todo.py

class ToDoApp:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        """Adiciona uma tarefa à lista."""
        self.tasks.append(task)
        print(f"Tarefa '{task}' adicionada com sucesso!")

    def list_tasks(self):
        """Lista todas as tarefas."""
        if not self.tasks:
            print("Nenhuma tarefa encontrada.")
        else:
            print("Tarefas:")
            for index, task in enumerate(self.tasks, start=1):
                print(f"{index}. {task}")

    def remove_task(self, task_index):
        """Remove uma tarefa pelo índice."""
        if 0 < task_index <= len(self.tasks):
            removed = self.tasks.pop(task_index - 1)
            print(f"Tarefa '{removed}' removida com sucesso!")
        else:
            print("Índice inválido.")

def main():
    app = ToDoApp()
    while True:
        print("\n--- ToDo List App ---")
        print("1. Adicionar tarefa")
        print("2. Listar tarefas")
        print("3. Remover tarefa")
        print("4. Sair")

        choice = input("Escolha uma opção: ")

        if choice == "1":
            task = input("Digite a tarefa: ")
            app.add_task(task)
        elif choice == "2":
            app.list_tasks()
        elif choice == "3":
            try:
                task_index = int(input("Digite o índice da tarefa para remover: "))
                app.remove_task(task_index)
            except ValueError:
                print("Por favor, insira um número válido.")
        elif choice == "4":
            print("Saindo do aplicativo. Até logo!")
            break
        else:
            print("Opção inválida. Tente novamente.")

if __name__ == "__main__":
    main()
git add todo.py
git commit -m "Implementa interface do usuário"
# Volte para a branch principal
git checkout main

# Faça o merge de cada branch
git merge feature/interface
git merge feature/add-task
git merge feature/remove-task
git push origin main
# duda
