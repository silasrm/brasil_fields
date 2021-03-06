# brasil_fields

O jeito mais fácil de utilizar padrões e formatos brasileiros em seu projeto.

## Apresentação

Este package facilita o desenvolvimento com a linguagem Dart em projetos que
utilizam campos com os padrões e formatos brasileiros.

### Instalação

```yaml
dependencies:
  brasil_fields: ^0.4.0
```

### Formatters

- CPF (999.999.99-99)
- CNPJ (99.999.999/9999-99)
- CEP (99.999-999)
- Real (R\$) (20.550)
- Centavos (R\$) (20,90)
- Telefone ( (99) 9999-9999)
- Data (01/01/1900)
- Hora (23:59)
- Cartão bancário (0000 1111 2222 3333 4444)
- Validade de cartão bancário (12/24)
- Altura (2,22)
- Peso (111,1)
- Cpf ou Cnpj (se adapta conforme os números são inseridos)

![Formatters](screenshots/formatters.png)

### Padrões

- Estados
- Meses
- Regiões
- Semana

![Formatters](screenshots/padroes.png)

### Como utilizar

Basta incluir o formatter que você quer que o campo tenha, na lista de `inputFormatters` :

**Para garantir que o campo aceite apenas valores numéricos, utilize em conjunto com o formatter `FilteringTextInputFormatter.digitsOnly` .**

```dart
TextFormField(
  inputFormatters: [
    FilteringTextInputFormatter.digitsOnly,
    CepInputFormatter(),
  ],
);
```

- `CpfInputFormatter()`
- `CnpjInputFormatter()`
- `CepInputFormatter()`
- `RealInputFormatter()`
- `TelefoneInputFormatter()`
- `DataInputFormatter()`
- `HoraInputFormatter()`
- `CartaoBancarioInputFormatter()`
- `ValidadeCartaoInputFormatter()`
- `AlturaInputFormatter()`
- `PesoInputFormatter()`
- `CpfOuCnpjFormatter()`

Caso precise de um DropdownButton com algumas das classes de padrões:

```dart
DropdownButton(
  items: Regioes.listaRegioes.map((String opcao) {
    return DropdownMenuItem<String>(
    value: opcao,
    child: Text(opcao),
  );
}).toList(),
```

### Métodos úteis

A classe `UtilData` possui métodos que facilitam obter o valor de um objeto `DateTime` em formato `String` (e no padrão brasileiro).

- `UtilData.obterDataDDMMAAAA` (DD/MM/AAAA)
- `UtilData.obterDataMMAAAA` (MM/AAAA)
- `UtilData.obterDataDDMM` (MM/AAAA)
- `UtilData.obterHoraHHMMSS` (hh:mm:ss)
- `UtilData.obterHoraHHMM` (hh:mm)

Para inicializar um `TextEditingController` com o texto já formatado, basta escolher o método com o formato desejado e setar no atributo `text`:

```dart
  final _textController = TextEditingController();
    _textController.text = UtilData.obterDataDDMMAAAA(DateTime.now());
```
