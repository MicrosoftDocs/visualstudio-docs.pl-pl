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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0e52f42e495c2bac5e80195d360096947210980
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748694"
---
# <a name="list-registers-command"></a>Lista rejestrów — Polecenie
Wyświetla wartość wybranych rejestrów i pozwala modyfikować listę rejestrów do wyświetlenia.

## <a name="syntax"></a>Składnia

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Przełączniki
/Display [{`register`&#124;`registerGroup`}...]

Wyświetla wartości określonego `register` lub `registerGroup`. Jeśli nie określono `register` lub `registerGroup`, zostanie wyświetlona domyślna lista rejestrów. Jeśli nie określono przełącznika, zachowanie jest takie samo. Na przykład:

`Debug.ListRegisters /Display eax`

jest równoważny

`Debug.ListRegisters eax`

/List

Wyświetla wszystkie grupy rejestrów na liście.

/Watch [{`register`&#124;`registerGroup`}...]

Dodaje do listy co najmniej jedną wartość `register` lub `registerGroup`.

/Unwatch [{`register`&#124;`registerGroup`}...]

Usuwa co najmniej jedną `register` lub `registerGroup` wartości z listy.

## <a name="remarks"></a>Uwagi
Alias `r` może być używany zamiast `Debug.ListRegisters`.

## <a name="example"></a>Przykład
Ten przykład używa `r` aliasu `Debug.ListRegisters`, aby wyświetlić wartości `Flags` grupy rejestru.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Podstawy debugowania: okno rejestrów](../../debugger/debugging-basics-registers-window.md)
- [Instrukcje: korzystanie z okna rejestrów](../../debugger/how-to-use-the-registers-window.md)