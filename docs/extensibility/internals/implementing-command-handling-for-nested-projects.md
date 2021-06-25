---
title: Implementowanie obsługi poleceń dla zagnieżdżonych projektów | Microsoft Docs
description: Dowiedz się, jak zaimplementować obsługę poleceń dla zagnieżdżonych projektów w Visual Studio zintegrowanym środowisku projektowym (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4324e207d7b424295137f9523ed0bed538b3d806
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899989"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementowanie obsługi poleceń dla zagnieżdżonych projektów
Ide może przekazywać polecenia przekazywane za pośrednictwem interfejsów i do zagnieżdżonych projektów, a projekty nadrzędne mogą filtrować <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lub zastępować polecenia.

> [!NOTE]
> Tylko polecenia zwykle obsługiwane przez projekt nadrzędny mogą być filtrowane. Poleceń, takich **jak kompilowanie** **i** wdrażanie obsługiwanych przez ideę , nie można filtrować.

 W poniższych krokach opisano proces implementowania obsługi poleceń.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Aby zaimplementować obsługę poleceń

1. Gdy użytkownik wybierze projekt zagnieżdżony lub węzeł w projekcie zagnieżdżonych:

   1. Ide wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę .

      — lub —

   2. Jeśli polecenie pochodzi z okna hierarchii, takiego jak polecenie menu skrótów w Eksplorator rozwiązań, ide wywołuje metodę w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> oknie nadrzędnym projektu.

2. Projekt nadrzędny może sprawdzać parametry, które mają być przekazywane do , takie jak i , w celu określenia, czy projekt nadrzędny `QueryStatus` `pguidCmdGroup` ma `prgCmds` filtrować polecenia. Jeśli projekt nadrzędny jest implementowany w celu filtrowania poleceń, należy ustawić:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Następnie projekt nadrzędny powinien zwrócić `S_OK` .

    Jeśli projekt nadrzędny nie filtruje polecenia, powinien po prostu zwrócić `S_OK` . W takim przypadku idee automatycznie kieruje polecenie do projektu podrzędnego.

    Projekt nadrzędny nie musi przekierowyywać polecenia do projektu podrzędnego. To zadanie wykonuje idee.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)
