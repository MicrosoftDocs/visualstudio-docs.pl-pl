---
title: Lista rejestrów — Polecenie
description: Dowiedz się więcej na temat listy rejestrów i sposobu wyświetlania wartości wybranych rejestrów i pozwala modyfikować listę rejestrów do wyświetlenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5459ded60ea90ae00a3f943f829065a82548d160
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305296"
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
/Display [{ `register`&#124;`registerGroup` }...]

Wyświetla wartości określonego `register` lub `registerGroup` . Jeśli nie `register` `registerGroup` jest określona, zostanie wyświetlona domyślna lista rejestrów. Jeśli nie określono przełącznika, zachowanie jest takie samo. Przykład:

`Debug.ListRegisters /Display eax`

jest równoważny

`Debug.ListRegisters eax`

/List

Wyświetla wszystkie grupy rejestrów na liście.

/Watch [{ `register`&#124;`registerGroup` }...]

Dodaje co najmniej jedną `register` `registerGroup` wartość do listy.

/Unwatch [{ `register`&#124;`registerGroup` }...]

Usuwa co najmniej jedną `register` `registerGroup` z wartości z listy.

## <a name="remarks"></a>Uwagi
Alias `r` może być używany zamiast `Debug.ListRegisters` .

## <a name="example"></a>Przykład
Ten przykład używa `Debug.ListRegisters` aliasu, `r` Aby wyświetlić wartości grupy rejestru `Flags` .

```cmd
r /Display Flags
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Podstawy debugowania: okno rejestrów](../../debugger/debugging-basics-registers-window.md)
- [Porady: korzystanie z okna rejestrów](../../debugger/how-to-use-the-registers-window.md)
