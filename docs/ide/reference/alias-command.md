---
title: Alias — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 031f1a4bab1acee3f3d0999b17c0b607f7808df9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596908"
---
# <a name="alias-command"></a>Alias — Polecenie
Tworzy nowy alias dla pełnego polecenia, polecenia complete i argumentów lub innego aliasu.

> [!TIP]
> Wpisywanie `>alias` bez żadnych argumentów powoduje wyświetlenie bieżącej listy aliasów i ich definicji.

## <a name="syntax"></a>Składnia

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumenty
`aliasname`\
Element opcjonalny. Nazwa nowego aliasu. Jeśli nie podano `aliasname`żadnej wartości, zostanie wyświetlona lista bieżących aliasów i ich definicje.

`aliasstring`\
Element opcjonalny. Pełna nazwa polecenia lub istniejący alias i wszelkie parametry, które chcesz utworzyć jako alias. Jeśli dla `aliasstring`tej wartości nie podano żadnej wartości, zostanie wyświetlona nazwa aliasu i aliasu dla określonego aliasu.

## <a name="switches"></a>Przełączniki
/delete lub /del lub /d\
Element opcjonalny. Usuwa określony alias, usuwając go z autouzupełniania.

/reset\
Element opcjonalny. Resetuje listę wstępnie zdefiniowanych aliasów do oryginalnych ustawień. Oznacza to, że przywraca wszystkie wstępnie zdefiniowane aliasy i usuwa wszystkie aliasy zdefiniowane przez użytkownika.

## <a name="remarks"></a>Uwagi
Ponieważ aliasy reprezentują polecenia, muszą znajdować się na początku wiersza polecenia.

Podczas wydawania tego polecenia należy dołączyć przełączniki natychmiast po poleceniu, a nie po aliasach, w przeciwnym razie sam przełącznik zostanie dołączony jako część ciągu aliasu.

Przełącznik `/reset` prosi o potwierdzenie przed przywróceniem aliasów. Nie ma krótkiej `/reset`formy .

## <a name="examples"></a>Przykłady
W tym przykładzie tworzy `upper`nowy alias, dla pełnego polecenia Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

W tym przykładzie usuwa `upper`alias, .

```cmd
>Tools.alias /delete upper
```

W tym przykładzie jest wyświetlana lista wszystkich bieżących aliasów i definicji.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
