---
title: List rejestrów — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3476244d3044eb80dbfce3559479421b012cc5fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659498"
---
# <a name="list-registers-command"></a>Lista rejestrów — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla wartość wybranych rejestrów i pozwala modyfikować listę rejestrów do wyświetlenia.

## <a name="syntax"></a>Składnia

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Przełączniki
 /Display [{ `register`&#124;`registerGroup` }...] Wyświetla wartości określonego `register` lub `registerGroup` . Jeśli nie `register` `registerGroup` jest określona, zostanie wyświetlona domyślna lista rejestrów. Jeśli nie określono przełącznika, zachowanie jest takie samo. Na przykład:

 `Debug.ListRegisters /Display eax`

 jest równoważny

 `Debug.ListRegisters eax`

 /List Wyświetla wszystkie grupy rejestrów na liście.

 /Watch [{ `register`&#124;`registerGroup` }...] Dodaje co najmniej jedną `register` `registerGroup` wartość do listy.

 /Unwatch [{ `register`&#124;`registerGroup` }...] Usuwa co najmniej jedną `register` `registerGroup` z wartości z listy.

## <a name="remarks"></a>Uwagi
 Alias `r` może być używany zamiast `Debug.ListRegisters` .

## <a name="example"></a>Przykład
 Ten przykład używa `Debug.ListRegisters` aliasu, `r` Aby wyświetlić wartości grupy rejestru `Flags` .

```
r /Display Flags
```

## <a name="see-also"></a>Zobacz też
 Podstawowe informacje dotyczące debugowania [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md) [: rejestruje okno](../../debugger/debugging-basics-registers-window.md) [jak: korzystanie z okna Rejestry](../../debugger/how-to-use-the-registers-window.md)
