---
title: Wdrażanie obsługi poleceń dla projektów zagnieżdżonych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707607"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementowanie obsługi poleceń dla zagnieżdżonych projektów
IDE może przekazywać polecenia, które <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> są <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> przekazywane przez interfejsy i do projektów zagnieżdżonych lub projektów nadrzędnych można filtrować lub zastąpić polecenia.

> [!NOTE]
> Tylko polecenia zwykle obsługiwane przez projekt nadrzędny mogą być filtrowane. Nie można filtrować poleceń, takich jak **Kompilacja** i **Wdrażanie,** które są obsługiwane przez IDE.

 W poniższych krokach opisano proces implementowania obsługi poleceń.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Aby zaimplementować obsługę poleceń

1. Gdy użytkownik wybierze projekt zagnieżdżony lub węzeł w projekcie zagnieżdżonego:

   1. IDE wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę.

      — lub —

   2. Jeśli polecenie pochodzi z okna hierarchii, takie jak polecenie menu skrótów <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> w Eksploratorze rozwiązań, IDE wywołuje metodę w łzowym projekcie.

2. Projekt nadrzędny może zbadać parametry, które mają być przekazywane do `QueryStatus`, takich jak `pguidCmdGroup` i `prgCmds`, aby ustalić, czy projekt nadrzędny powinien filtrować polecenia. Jeśli projekt nadrzędny jest implementowany do filtrowania poleceń, należy ustawić:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Następnie projekt nadrzędny `S_OK`powinien zwrócić .

    Jeśli projekt nadrzędny nie filtruje polecenia, `S_OK`powinien po prostu zwrócić . W takim przypadku IDE automatycznie kieruje polecenie do projektu podrzędnego.

    Projekt nadrzędny nie musi kierować polecenia do projektu podrzędnego. IDE wykonuje to zadanie..

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)
