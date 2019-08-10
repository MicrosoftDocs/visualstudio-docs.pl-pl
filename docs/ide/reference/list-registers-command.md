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
ms.openlocfilehash: 95edb5098d73e8fccb47f9f059473394afe5f542
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919109"
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

Wyświetla wartości określonego `register` lub `registerGroup`. Jeśli nie `register` `registerGroup` jest określona, zostanie wyświetlona domyślna lista rejestrów. Jeśli nie określono przełącznika, zachowanie jest takie samo. Przykład:

`Debug.ListRegisters /Display eax`

odpowiada wyrażeniu

`Debug.ListRegisters eax`

/List

Wyświetla wszystkie grupy rejestrów na liście.

/Watch [{`register`&#124;`registerGroup`}...]

Dodaje co najmniej jedną `register` `registerGroup` wartość do listy.

/Unwatch [{`register`&#124;`registerGroup`}...]

Usuwa co najmniej jedną `register` `registerGroup` z wartości z listy.

## <a name="remarks"></a>Uwagi
Alias `r` może być używany `Debug.ListRegisters`zamiast.

## <a name="example"></a>Przykład
Ten przykład używa `Debug.ListRegisters` aliasu `r` , aby wyświetlić wartości grupy `Flags`rejestru.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Podstawy debugowania: Okno rejestrów](../../debugger/debugging-basics-registers-window.md)
- [Instrukcje: Korzystanie z okna rejestrów](../../debugger/how-to-use-the-registers-window.md)