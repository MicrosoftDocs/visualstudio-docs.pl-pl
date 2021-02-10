---
title: Kontrakty poleceń w zestawach międzyoperacyjnych | Microsoft Docs
description: Zapoznaj się z podstawową umową dotyczącą obsługi poleceń za pomocą interfejsu Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ed9435f4f0618ee0c0f4bc47cdb21e2cbf92f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940130"
---
# <a name="command-contracts-in-interop-assemblies"></a>Kontrakty poleceń w zestawach międzyoperacyjnych
Podstawową umową dotyczącą obsługi poleceń za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu jest to, że środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę w celu ustalenia, czy polecenie jest obsługiwane, a jeśli jest obsługiwane, w celu określenia jego stanu i tekstu. Następnie środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wykonać polecenie.

 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Metoda jest obsługiwana identycznie dla wszystkich poleceń. Dalsza komunikacja, jeśli jest to wymagane (na przykład przy użyciu list rozwijanych), jest zarządzana przez wywołanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody z odpowiednimi parametrami. Interpretacja tych parametrów zależy od podanego polecenia.

 Jeśli obiekt docelowy polecenia zwraca wartości w parametrze Output, obiekt wywołujący jest zawsze odpowiedzialny za zwalnianie wszelkich przyznanych zasobów. Ponieważ ten parametr jest wariantem, czyszczenie wariantu zwalnia zasoby.

 W przypadkach, gdy polecenia muszą działać w oknie hierarchii, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> należy użyć interfejsu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Interfejs ma podobną umowę z podobnymi metodami: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Zobacz też
- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing poleceń w pakietów VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementacja polecenia](../../extensibility/internals/command-implementation.md)
