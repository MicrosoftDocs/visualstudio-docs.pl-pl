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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e87b10a7827b5365b507abb2c72a21506e59c19e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568688"
---
# <a name="list-registers-command"></a>Lista rejestrów — Polecenie
Wyświetla wartość wybranych rejestrów i umożliwia modyfikowanie listy rejestrów do wyświetlenia.

## <a name="syntax"></a>Składnia

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Przełączniki
/Display [{`register`&#124;`registerGroup`}...]

Wyświetla wartości określonego `register` lub `registerGroup`. Jeśli `register` nie `registerGroup` określono lub jest określony, wyświetlana jest domyślna lista rejestrów. Jeśli nie określono przełącznika, zachowanie jest takie samo. Przykład:

`Debug.ListRegisters /Display eax`

jest równoważny

`Debug.ListRegisters eax`

/Lista

Wyświetla wszystkie grupy rejestru na liście.

/Watch [{`register`&#124;`registerGroup`}...]

Dodaje do `register` listy `registerGroup` co najmniej jedną lub więcej wartości.

/Unwatch [{`register`&#124;`registerGroup`}...]

Usuwa jedną lub `register` `registerGroup` więcej wartości z listy.

## <a name="remarks"></a>Uwagi
Alias `r` może być używany `Debug.ListRegisters`zamiast pliku .

## <a name="example"></a>Przykład
W tym przykładzie użyto aliasu `Debug.ListRegisters` `r` do `Flags`wyświetlania wartości grupy rejestru .

```cmd
r /Display Flags
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Podstawy debugowania: okno rejestrów](../../debugger/debugging-basics-registers-window.md)
- [Porady: korzystanie z okna rejestrów](../../debugger/how-to-use-the-registers-window.md)
