# Atividade 2
Implementar as funcionalidades relacionadas na função `main()` no arquivo fonte `14-agregacao.dart`.
Evidenciar o código e o `print` da saída no GitHub e o _link_ da atividade no Google Classroom.

## Código-fonte
```dart
import 'dart:convert';

// Agregação e Composição

class Dependente {
  late String _nome;

  Dependente(String nome) {
    this._nome = nome;
  }

  Map<String, dynamic> toJson() {
    return {'nome': _nome};
  }
  
}

class Funcionario {
  late String _nome;
  late List<Dependente> _dependentes;

  Funcionario(String nome, List<Dependente> dependentes) {
    this._nome = nome;
    this._dependentes = dependentes;
  }

  Map<String, dynamic> toJson() {
    return {
      'nome': _nome,
      'dependentes': _dependentes.map((d) => d.toJson()).toList(),
    };
  }
}

class EquipeProjeto {
  late String _nomeProjeto;
  late List<Funcionario> _funcionarios;

  EquipeProjeto(String nomeprojeto, List<Funcionario> funcionarios) {
    _nomeProjeto = nomeprojeto;
    _funcionarios = funcionarios;
  }

  Map<String, dynamic> toJson() {
    return {
      'nomeProjeto': _nomeProjeto,
      'funcionarios': _funcionarios.map((f) => f.toJson()).toList(),
    };
  }

}

void main() {
  // 1. Criar vários objetos Dependente
  Dependente dependente1 = Dependente('João');
  Dependente dependente2 = Dependente('Maria');
  Dependente dependente3 = Dependente('Pedro');
  Dependente dependente4 = Dependente('Ana');

  // 2. Criar vários objetos Funcionario
  Funcionario funcionario1 = Funcionario('Carlos', [dependente1, dependente2]);
  Funcionario funcionario2 = Funcionario('Fernanda', [dependente3, dependente4]);

  // 3. Associar os Dependentes criados aos respectivos funcionários
  // (Já feito acima no construtor)

  // 4. Criar uma lista de Funcionários
  List<Funcionario> funcionarios = [funcionario1, funcionario2];

  // 5. Criar um objeto EquipeProjeto
  EquipeProjeto equipe = EquipeProjeto('Projeto Dart', funcionarios);

  // 6. Printar no formato JSON
  String jsonOutput = jsonEncode(equipe.toJson());
  print(jsonOutput);
}

```
# Saída

<img width="1202" alt="image" src="https://github.com/user-attachments/assets/e4780b4d-7468-4b0d-98ea-9cbf6d04434a">

