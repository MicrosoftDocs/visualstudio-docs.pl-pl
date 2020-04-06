---
title: Kontrakty dowodzenia w zespołach interop | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709684"
---
# <a name="command-contracts-in-interop-assemblies"></a>Kontrakty dowodzenia w zespołach międzyoperacyjnych
Podstawowa umowa obsługi poleceń <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> za pośrednictwem interfejsu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> jest, że środowisko wywołuje metodę, aby ustalić, czy polecenie jest obsługiwane i, jeśli jest obsługiwany, aby określić jego stan i tekst. Następnie środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wykonać polecenie.

 Metoda <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> jest obsługiwana identycznie dla wszystkich poleceń. Dalszej komunikacji, jeśli jest to wymagane (na przykład z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> listami rozwijanych), jest zarządzany przez wywołanie metody z odpowiednimi parametrami. Interpretacja tych parametrów zależy od określonego polecenia.

 Jeśli obiekt docelowy polecenia zwraca wartości w parametrze wyjściowym, obiekt wywołujący jest zawsze odpowiedzialny za zwalnianie wszystkich zasobów, które zostały przydzielone. Ponieważ ten parametr jest wariantem, wyczyszczenie wariantu zwalnia zasoby.

 W przypadkach, gdy polecenia muszą działać w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> oknie hierarchii, interfejs musi być używany. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> ma podobną umowę z <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>podobnymi metodami: i .

## <a name="see-also"></a>Zobacz też
- [Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing poleceń w pakietach VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementacja polecenia](../../extensibility/internals/command-implementation.md)
