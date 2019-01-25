---
title: Polecenie kontraktów w zestawach międzyoperacyjnych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799262"
---
# <a name="command-contracts-in-interop-assemblies"></a>Kontrakty poleceń w zestawach międzyoperacyjnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podstawowy kontrakt dla obsługi poleceń w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs jest, że środowisko wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody, które określają, czy polecenie jest obsługiwane, a jeśli jest obsługiwana, aby ustalić ich stan i tekst. Następnie wywołuje środowisko <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodę, aby wykonać polecenie.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Metoda odbywa się tak samo dla wszystkich poleceń. Dalszej komunikacji, jeśli jest to wymagane (na przykład, z listy rozwijanej) odbywa się przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody za pomocą odpowiednich parametrów. Interpretacja tych parametrów, zależy od określone polecenie.  
  
 Jeśli element docelowy polecenia zwraca wartości w parametrze danych wyjściowych, obiekt wywołujący zawsze jest odpowiedzialny za zwolnić wszystkie zasoby, które zostały przydzielone. Ponieważ ten parametr jest typu variant, czyszcząc wariant zwalnia zasoby.  
  
 W przypadkach, gdzie polecenia musi działać w oknie hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejs musi być używany. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Interfejs ma podobny kontrakt, z podobnych metod: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementacja](../../extensibility/internals/command-implementation.md)
