---
title: Implementowanie obsługi poleceń dla zagnieżdżonych projektów | Microsoft Docs
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
ms.openlocfilehash: 628fde153441104e4bb504253d96235270b4b8fb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727083"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementowanie obsługi poleceń dla zagnieżdżonych projektów
IDE może przekazać polecenia, które są przekazywane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> i interfejsy <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> do projektów zagnieżdżonych, lub projekty nadrzędne mogą filtrować lub przesłaniać polecenia.

> [!NOTE]
> Można filtrować tylko polecenia zwykle obsługiwane przez projekt nadrzędny. Nie można filtrować poleceń, takich jak **Kompilowanie** i **wdrażanie** , które są obsługiwane przez IDE.

 Poniższe kroki opisują proces wdrażania obsługi poleceń.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Aby zaimplementować obsługę poleceń

1. Gdy użytkownik wybierze zagnieżdżony projekt lub węzeł w projekcie zagnieżdżonym:

   1. IDE wywołuje metodę <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>.

      oraz

   2. Jeśli polecenie pochodzi z okna hierarchii, takiego jak polecenie menu skrótów w Eksplorator rozwiązań, IDE wywoła metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> w elemencie nadrzędnym projektu.

2. Projekt nadrzędny może sprawdzać parametry, które mają zostać przesłane do `QueryStatus`, takich jak `pguidCmdGroup` i `prgCmds`, aby określić, czy projekt nadrzędny powinien filtrować polecenia. Jeśli projekt nadrzędny jest zaimplementowany do filtrowania poleceń, powinien on zostać ustawiony:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Następnie projekt nadrzędny powinien zwrócić `S_OK`.

    Jeśli projekt nadrzędny nie filtruje polecenia, powinien po prostu zwrócić `S_OK`. W takim przypadku IDE automatycznie kieruje polecenie do projektu podrzędnego.

    Projekt nadrzędny nie musi kierować polecenia do projektu podrzędnego. IDE wykonuje to zadanie...

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)