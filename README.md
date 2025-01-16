### Documentação Completa (README.md)



## Índice

1. [Introdução](#introdução)
2. [Configuração Inicial](#configuração-inicial)
3. [Estrutura Geral do Script](#estrutura-geral-do-script)
4. [Elementos Disponíveis](#elementos-disponíveis)
   - [Janela Principal](#janela-principal)
   - [Abas](#abas)
   - [Groupboxes](#groupboxes)
   - [Toggles](#toggles)
   - [Botões](#botões)
   - [Labels](#labels)
   - [Divisores](#divisores)
   - [Sliders](#sliders)
   - [Inputs de Texto](#inputs-de-texto)
   - [Dropdowns](#dropdowns)
   - [Pickers (Cor e Tecla)](#pickers-cor-e-tecla)
5. [Gerenciamento de Configurações e Temas](#gerenciamento-de-configurações-e-temas)
6. [Exemplo Completo](#exemplo-completo)
7. [Referências e Créditos](#referências-e-créditos)


## Introdução

Este script é baseado na biblioteca **LinoriaLib**, permitindo criar interfaces gráficas sofisticadas com suporte a várias funcionalidades, como:

- Abas e grupos.
- Controles interativos como sliders, toggles e dropdowns.
- Gerenciamento de configurações e temas.

---

## Configuração Inicial

### Passo 1: Carregar as Bibliotecas
Certifique-se de carregar as dependências necessárias diretamente de um repositório:

```lua
local repo = "https://raw.githubusercontent.com/deividcomsono/Obsidian/main/"
local Library = loadstring(game:HttpGet(repo .. "Library.lua"))()
local ThemeManager = loadstring(game:HttpGet(repo .. "addons/ThemeManager.lua"))()
local SaveManager = loadstring(game:HttpGet(repo .. "addons/SaveManager.lua"))()
```

### Passo 2: Configuração Básica
Defina opções gerais para o funcionamento da biblioteca:

```lua
Library.ShowToggleFrameInKeybinds = true
```

---

## Estrutura Geral do Script

A estrutura do script é organizada em seções que correspondem à criação e configuração de elementos de interface, como janelas, abas e controles interativos. 

1. **Criação da Janela Principal**
   ```lua
   local Window = Library:CreateWindow({
       Title = "Exemplo",
       Footer = "Versão 1.0",
       Icon = 1234567890,
       NotifySide = "Right",
       ShowCustomCursor = true,
   })
   ```

2. **Definição de Abas**
   ```lua
   local Tabs = {
       Main = Window:AddTab("Principal"),
       Settings = Window:AddTab("Configurações"),
   }
   ```

3. **Adição de Groupboxes**
   ```lua
   local GroupBox = Tabs.Main:AddLeftGroupbox("Configurações Gerais")
   ```

---

## Elementos Disponíveis

### Janela Principal

| **Propriedade**      | **Descrição**                                                     | **Valor Padrão** |
|----------------------|-------------------------------------------------------------------|------------------|
| `Title`             | Define o título da janela.                                       | `""`             |
| `Footer`            | Texto exibido no rodapé da janela.                               | `""`             |
| `Icon`              | Ícone do cabeçalho (ID de imagem do Roblox).                     | `nil`            |
| `NotifySide`        | Lado das notificações (`Left` ou `Right`).                       | `Left`           |
| `ShowCustomCursor`  | Exibe um cursor personalizado.                                   | `true`           |

---

### Abas

Adicione abas com o método `AddTab`:

```lua
local Tabs = {
    Main = Window:AddTab("Principal"),
    Settings = Window:AddTab("Configurações"),
}
```

---

### Groupboxes

Crie grupos de elementos em uma aba:

```lua
local GroupBox = Tabs.Main:AddLeftGroupbox("Configurações")
```

---

### Toggles

Interruptores ativáveis/desativáveis:

| **Propriedade**      | **Descrição**                          | **Valor Padrão** |
|----------------------|----------------------------------------|------------------|
| `Text`              | Texto exibido ao lado do toggle.       | `""`             |
| `Default`           | Estado inicial (`true` ou `false`).    | `false`          |
| `Callback`          | Função executada ao alterar o estado.  | `nil`            |

Exemplo:
```lua
GroupBox:AddToggle("MeuToggle", {
    Text = "Ativar Modo",
    Default = false,
    Callback = function(Value)
        print("Toggle alterado:", Value)
    end,
})
```

---

### Botões

Botões interativos com ações associadas:

| **Propriedade**      | **Descrição**                          | **Valor Padrão** |
|----------------------|----------------------------------------|------------------|
| `Text`              | Texto exibido no botão.               | `""`             |
| `Func`              | Função executada ao clicar.           | `nil`            |

Exemplo:
```lua
GroupBox:AddButton({
    Text = "Clique Aqui",
    Func = function()
        print("Botão clicado!")
    end,
})
```

---

### Labels

Rótulos para exibir textos:

```lua
GroupBox:AddLabel("Texto Informativo")
```

---

### Divisores

Adicione divisores visuais entre elementos:

```lua
GroupBox:AddDivider()
```

---

### Sliders

Controles deslizantes para seleção de valores numéricos:

| **Propriedade**      | **Descrição**                          | **Valor Padrão** |
|----------------------|----------------------------------------|------------------|
| `Text`              | Texto descritivo.                     | `""`             |
| `Min`               | Valor mínimo.                         | `0`              |
| `Max`               | Valor máximo.                         | `100`            |
| `Default`           | Valor inicial.                        | `0`              |
| `Callback`          | Função executada ao alterar o valor.  | `nil`            |

Exemplo:
```lua
GroupBox:AddSlider("Volume", {
    Text = "Volume",
    Min = 0,
    Max = 100,
    Default = 50,
    Callback = function(Value)
        print("Volume ajustado para:", Value)
    end,
})
```

---

### Inputs de Texto

Caixas de texto para entrada de dados:

```lua
GroupBox:AddInput("CaixaDeTexto", {
    Default = "",
    Text = "Digite algo",
    Callback = function(Value)
        print("Texto inserido:", Value)
    end,
})
```

---

### Dropdowns

Listas suspensas para seleção de opções:

```lua
GroupBox:AddDropdown("Opcoes", {
    Values = { "Opção 1", "Opção 2", "Opção 3" },
    Default = 1,
    Callback = function(Value)
        print("Opção selecionada:", Value)
    end,
})
```

---

### Pickers (Cor e Tecla)

Adicione seletores de cor ou teclas:

```lua
GroupBox:AddLabel("Cor"):AddColorPicker("Cor", {
    Default = Color3.new(1, 0, 0),
    Callback = function(Value)
        print("Cor escolhida:", Value)
    end,
})

GroupBox:AddLabel("Tecla"):AddKeyPicker("Tecla", {
    Default = "MB1",
    Callback = function(Value)
        print("Tecla selecionada:", Value)
    end,
})
```

---

## Gerenciamento de Configurações e Temas

Use os gerenciadores para salvar e carregar configurações e temas:

```lua
ThemeManager:SetLibrary(Library)
SaveManager:SetLibrary(Library)
SaveManager:SetFolder("Configurações")
SaveManager:BuildConfigSection(Tabs.Settings)
```

---

## Exemplo Completo

```lua
local Window = Library:CreateWindow({
    Title = "Exemplo Completo",
    Footer = "Versão 1.0",
})

local Tabs = {
    Main = Window:AddTab("Principal"),
}

local GroupBox = Tabs.Main:AddLeftGroupbox("Configurações")

GroupBox:AddToggle("Toggle1", { Text = "Habilitar", Default = true })
GroupBox:AddButton({ Text = "Clique Aqui", Func = function() print("Botão clicado!") end })
GroupBox:AddLabel("Texto de exemplo")
GroupBox:AddSlider("Slider1", { Text = "Ajuste", Min = 0, Max = 100, Default = 50 })
GroupBox:AddInput("Input1", { Text = "Digite algo", Default = "Texto padrão" })
GroupBox:AddDropdown("Dropdown1", { Values = { "Opção 1", "Opção 2" }, Default = 1 })
```

---

## Referências e Créditos

- [LinoriaLib](https://github.com/mstudio45/LinoriaLib)
- Modificado por Deivid.

---

