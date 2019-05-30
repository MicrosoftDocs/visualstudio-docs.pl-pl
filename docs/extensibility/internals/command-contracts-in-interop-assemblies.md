---
title: Polecenie kontraktów w zestawach międzyoperacyjnych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80da2b521b151dfb88b80eb7ea96d88ef7b4d264
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351669"
---
# <a name="command-contracts-in-interop-assemblies"></a>Kontrakty poleceń w zestawach międzyoperacyjnych
Podstawowy kontrakt dla obsługi poleceń w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs jest, że środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody, które określają, czy polecenie jest obsługiwane, a jeśli jest obsługiwana, aby ustalić ich stan i tekst. Następnie wywołuje środowisko <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wykonać polecenie.

 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Metoda odbywa się tak samo dla wszystkich poleceń. Dalszej komunikacji, jeśli jest to wymagane (na przykład, z listy rozwijanej) odbywa się przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody za pomocą odpowiednich parametrów. Interpretacja tych parametrów, zależy od określone polecenie.

 Jeśli element docelowy polecenia zwraca wartości w parametrze danych wyjściowych, obiekt wywołujący zawsze jest odpowiedzialny za zwolnić wszystkie zasoby, które zostały przydzielone. Ponieważ ten parametr jest typu variant, czyszcząc wariant zwalnia zasoby.

 W przypadkach, gdzie polecenia musi działać w oknie hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejs musi być używany. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Interfejs ma podobny kontrakt, z podobnych metod: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.

## <a name="see-also"></a>Zobacz także
- [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementacja poleceń](../../extensibility/internals/command-implementation.md)