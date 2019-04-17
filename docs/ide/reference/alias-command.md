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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0072bbd770a6d4fa675010048f2d067eb0961d62
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662546"
---
# <a name="alias-command"></a>Alias — Polecenie
Tworzy nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty lub inny alias.

> [!TIP]
> Wpisywanie `>alias` bez żadnych argumentów Wyświetla bieżącą listę aliasów i ich definicje.

## <a name="syntax"></a>Składnia

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumenty
 `aliasname` Opcjonalnie. Nazwa nowego pola alias. Jeśli nie dostarczono żadnej wartości dla `aliasname`, zostanie wyświetlona lista bieżących aliasów i ich definicje.

 `aliasstring` Opcjonalnie. Pełna nazwa polecenia lub istniejący alias i wszystkie parametry, które chcesz utworzyć jako alias. Jeśli nie dostarczono żadnej wartości dla `aliasstring`, nazwa aliasu i ciągi aliasów dla określonych aliasów Wyświetla.

## <a name="switches"></a>Przełączniki
 / DELETE lub/DEL lub /d atrybut opcjonalny. Usuwa określony alias, usuwając go z automatycznego uzupełniania.

 / reset atrybut opcjonalny. Resetuje listę wstępnie zdefiniowanych aliasów pierwotne ustawienia. Oznacza to, że przywraca wszystkie wstępnie zdefiniowane aliasy i usuwa wszystkie aliasy zdefiniowane przez użytkownika.

## <a name="remarks"></a>Uwagi
 Ponieważ aliasy stanowią polecenia, muszą być umieszczone na początku wiersza polecenia.

 Po wykonaniu tego polecenia, należy uwzględnić przełączniki natychmiast po poleceniu nie po aliasach, w przeciwnym razie sam przełącznik zostanie dołączony jako część ciąg aliasu.

 `/reset` Przełącznik prosi o potwierdzenie zanim aliasy zostaną przywrócone. Brak żadnych krótkich form `/reset`.

## <a name="examples"></a>Przykłady
 Ten przykład tworzy nowy alias `upper`, dla pełnego polecenia Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

 W tym przykładzie Usuwa alias, `upper`.

```cmd
>Tools.alias /delete upper
```

 W tym przykładzie wyświetla listę wszystkich bieżących aliasów i definicji.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)