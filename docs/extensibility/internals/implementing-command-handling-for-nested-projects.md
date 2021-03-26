---
title: Implementowanie obsługi poleceń dla zagnieżdżonych projektów | Microsoft Docs
description: Dowiedz się, jak zaimplementować obsługę poleceń dla zagnieżdżonych projektów w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fad154fd3739369b0ccf7e5d896d1b9f1728c68e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085783"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementowanie obsługi poleceń dla zagnieżdżonych projektów
IDE może przekazać polecenia, które są przekazywane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsów do projektów zagnieżdżonych, lub projekty nadrzędne mogą filtrować lub przesłaniać polecenia.

> [!NOTE]
> Można filtrować tylko polecenia zwykle obsługiwane przez projekt nadrzędny. Nie można filtrować poleceń, takich jak **Kompilowanie** i **wdrażanie** , które są obsługiwane przez IDE.

 Poniższe kroki opisują proces wdrażania obsługi poleceń.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Aby zaimplementować obsługę poleceń

1. Gdy użytkownik wybierze zagnieżdżony projekt lub węzeł w projekcie zagnieżdżonym:

   1. IDE wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę.

      oraz

   2. Jeśli polecenie pochodzi z okna hierarchii, takiego jak polecenie menu skrótów w Eksplorator rozwiązań, IDE wywoła <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metodę w obiekcie nadrzędnym projektu.

2. Projekt nadrzędny może sprawdzić parametry, które mają zostać przesłane do `QueryStatus` , takie jak `pguidCmdGroup` i `prgCmds` , aby określić, czy projekt nadrzędny powinien filtrować polecenia. Jeśli projekt nadrzędny jest zaimplementowany do filtrowania poleceń, powinien on zostać ustawiony:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Następnie projekt nadrzędny powinien zwrócić `S_OK` .

    Jeśli projekt nadrzędny nie filtruje polecenia, powinien po prostu zwrócić `S_OK` . W takim przypadku IDE automatycznie kieruje polecenie do projektu podrzędnego.

    Projekt nadrzędny nie musi kierować polecenia do projektu podrzędnego. IDE wykonuje to zadanie...

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)
