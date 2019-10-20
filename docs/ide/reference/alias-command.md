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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48fa131514f82ec13538b8f5a0662fde7388ddea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651987"
---
# <a name="alias-command"></a>Alias — Polecenie
Tworzy nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty lub inny alias.

> [!TIP]
> Wpisanie `>alias` bez żadnych argumentów wyświetla bieżącą listę aliasów i ich definicje.

## <a name="syntax"></a>Składnia

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumenty
`aliasname`\
Opcjonalny. Nazwa nowego aliasu. Jeśli nie podano żadnej wartości dla `aliasname`, zostanie wyświetlona lista bieżących aliasów i ich definicji.

`aliasstring`\
Opcjonalny. Pełna nazwa polecenia lub istniejący alias oraz wszystkie parametry, które chcesz utworzyć jako alias. Jeśli nie podano wartości dla `aliasstring`, zostanie wyświetlona nazwa aliasu i ciąg aliasu dla określonego aliasu.

## <a name="switches"></a>Przełączniki
/DELETE lub/del lub/d\
Opcjonalny. Usuwa określony alias, usuwając go z autouzupełniania.

/Reset
Opcjonalny. Resetuje listę wstępnie zdefiniowanych aliasów do jej oryginalnych ustawień. Oznacza to, że przywraca wszystkie wstępnie zdefiniowane aliasy i usuwa wszystkie aliasy zdefiniowane przez użytkownika.

## <a name="remarks"></a>Uwagi
Ponieważ aliasy reprezentują polecenia, muszą one znajdować się na początku wiersza polecenia.

Po wydaniu tego polecenia, należy uwzględnić przełączniki natychmiast po poleceniu, nie po aliasach, w przeciwnym razie sam przełącznik zostanie dołączony jako część ciągu aliasu.

Przełącznik `/reset` prosi o potwierdzenie przed przywróceniem aliasów. Nie ma żadnej krótkiej formy `/reset`.

## <a name="examples"></a>Przykłady
W tym przykładzie tworzony jest nowy alias, `upper` w celu wykonania polecenia Edit. MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Ten przykład usuwa alias, `upper`.

```cmd
>Tools.alias /delete upper
```

Ten przykład wyświetla listę wszystkich bieżących aliasów i definicji.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)