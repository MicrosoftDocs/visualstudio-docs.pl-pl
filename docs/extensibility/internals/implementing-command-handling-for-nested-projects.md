---
title: Implementowanie obsługi poleceń dla zagnieżdżonych projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66f89476e6d4a8fa009dbe921113c9e4cac54916
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313202"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementowanie obsługi poleceń dla zagnieżdżonych projektów
IDE można przekazać poleceń, które są przekazywane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsy zagnieżdżonych projektów lub projekty nadrzędny można filtrować lub zastąpienia polecenia.

> [!NOTE]
> Można filtrować tylko te polecenia, które zazwyczaj są obsługiwane przez nadrzędne projekt. Polecenia, takie jak **kompilacji** i **Wdróż** , są obsługiwane przez środowisko IDE nie mogą zostać odfiltrowane.

 W poniższych krokach opisano proces Implementowanie obsługi poleceń.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Aby zaimplementować obsługę

1. Gdy użytkownik wybierze projektu zagnieżdżonego lub węzła w zagnieżdżonych projektu:

   1. Wywołania środowiska IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody.

      — lub —

   2. Polecenie pochodziły w oknie hierarchii, takie jak polecenie menu skrótów w oknie Eksploratora rozwiązań IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metody nadrzędnego projektu.

2. Projekt nadrzędny można sprawdzić parametry do przekazania do `QueryStatus`, takich jak `pguidCmdGroup` i `prgCmds`, aby ustalić, czy projekt nadrzędny powinien filtrować poleceń. Jeśli projekt nadrzędny jest zaimplementowana do filtrowania poleceń, należy ustawić:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    A następnie projekt nadrzędny ma zwracać `S_OK`.

    Jeśli projekt nadrzędny nie filtruje polecenia, powinien zostać tylko zwrócony `S_OK`. W tym przypadku IDE automatycznie kieruje polecenia do projekt podrzędny.

    Projekt nadrzędny nie ma przekierowywać polecenia do projekt podrzędny. IDE wykonuje to zadanie...

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)