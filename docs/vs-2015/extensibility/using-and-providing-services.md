---
title: Korzystanie z usług i dostarczanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 189ff14c566c3007810ef35cd63ec03a5958e07c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779713"
---
# <a name="using-and-providing-services"></a>Korzystanie z usług i dostarczanie ich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usługa jest Umowa między dwoma pakietami VSPackage. Jednego pakietu VSPackage oferuje zestaw określonych interfejsów dla innego pakietu VSPackage korzystać. Na przykład [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oferuje <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> do dowolnego pakietu VSPackage go obsłużyć obciążenia. Ta usługa zapewnia <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może służyć do zapisu w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).  
  
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
  
 [Instrukcje: uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)  
 W tym artykule omówiono sposób żądania (Używanie) usługi.  
  
 [Instrukcje: dostarczanie usługi](../extensibility/how-to-provide-a-service.md)  
 W tym artykule omówiono sposób zapewniania usług.  
  
 [Instrukcje: dostarczanie asynchronicznej usługi programu Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 W tym artykule omówiono sposób obsługi asynchronicznego.  
  
 [Instrukcje: rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md)  
 W tym artykule omówiono typowe problemy i przedstawia informacje o rozwiązaniach do nich.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

