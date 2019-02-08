---
title: Lista rejestrów — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1a2361534f167a0b88b3f1b5b38c005915243d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934474"
---
# <a name="list-registers-command"></a>Lista rejestrów — Polecenie
Wyświetla wartość wybranego rejestruje i pozwala zmodyfikować listę rejestrów, aby pokazać.

## <a name="syntax"></a>Składnia

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Przełączniki
 / Wyświetlania [{`register`&#124;`registerGroup`} …]

 Wyświetla wartości określonego `register` lub `registerGroup`. Jeśli nie `register` lub `registerGroup` jest określony, wyświetlany jest domyślną listę rejestrów. Jeśli przełącznik nie zostanie określony, zachowanie jest takie same. Na przykład:

 `Debug.ListRegisters /Display eax`

 odpowiada wyrażeniu

 `Debug.ListRegisters eax`

 / List

 Wyświetla wszystkie zarejestrować grupy na liście.

 / Obejrzyj [{`register`&#124;`registerGroup`} …]

 Dodaje jeden lub więcej `register` lub `registerGroup` wartości do listy.

 / Cofnijwyrażeniekontrolne [{`register`&#124;`registerGroup`} …]

 Usuwa jeden lub więcej `register` lub `registerGroup` wartości z listy.

## <a name="remarks"></a>Uwagi
 Alias `r` mogą być używane zamiast `Debug.ListRegisters`.

## <a name="example"></a>Przykład
 W tym przykładzie użyto `Debug.ListRegisters` alias `r` do wyświetlania wartości grupy rejestru `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Podstawy debugowania: Okno rejestrów](../../debugger/debugging-basics-registers-window.md)
- [Instrukcje: Korzystanie z okna rejestrów](../../debugger/how-to-use-the-registers-window.md)