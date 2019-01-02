---
title: Lista rejestrów — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 942ab10a1d660ea5e33ca2cb679e4655bd6b3fbc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959968"
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