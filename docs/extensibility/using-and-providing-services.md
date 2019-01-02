---
title: Korzystanie z usług i dostarczanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f547afd33166a6a7b10284e6cb55e73baeefc861
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886283"
---
# <a name="using-and-providing-services"></a>Korzystanie z usług i dostarczanie ich
Usługa jest Umowa między dwoma pakietami VSPackage. Jednego pakietu VSPackage oferuje zestaw określonych interfejsów dla innego pakietu VSPackage korzystać. Na przykład [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oferuje <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> do dowolnego pakietu VSPackage go obsłużyć obciążenia. Ta usługa zapewnia <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może służyć do zapisu w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).  
  
 Pakietów VSPackage może oferować swoje własne przy użyciu usług <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfejs...  
  
 Program Visual Studio udostępnia ważne usługi, takie jak następujące:  
  
|Usługa środowiska IDE|Opis|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Zapewnia dostęp do środowiska IDE usług radzenia sobie z podstawowych funkcji, pakietów VSPackage i rejestru.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Udostępnia podstawowe obsługi okien i związane z interfejsem użytkownika w środowisku IDE, takie jak możliwość tworzenia, narzędzi i oknami dokumentu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zapewnia podstawowe funkcje związane z rozwiązania, takimi jak wyliczyć projektów, Utwórz nowe projekty i monitorowanie zmian projektu.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)  
 Przedstawia informacje o ważnych elementów usługi Visual Studio.  
  
 [Instrukcje: Uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)  
 W tym artykule omówiono sposób żądania (Używanie) usługi.  
  
 [Instrukcje: Oferuje usługi](../extensibility/how-to-provide-a-service.md)  
 W tym artykule omówiono sposób zapewniania usług.  
  
 [Instrukcje: Zapewniają usługi asynchronicznego programu Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 W tym artykule omówiono sposób obsługi asynchronicznego.  
  
 [Instrukcje: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md)  
 W tym artykule omówiono typowe problemy i przedstawia informacje o rozwiązaniach do nich.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)