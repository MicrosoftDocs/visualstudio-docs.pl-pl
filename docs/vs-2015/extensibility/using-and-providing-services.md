---
title: Używanie i świadczenie usług | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f58e29797e9a7760aa0f48c68868199f51b3c92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177440"
---
# <a name="using-and-providing-services"></a>Korzystanie z usług i dostarczanie ich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usługa jest umową między dwoma pakietów VSPackage. Jeden pakietu VSPackage oferuje określony zestaw interfejsów dla innego pakietu VSPackage do użycia. Program udostępnia na przykład [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> usługę pakietu VSPackage. Ta usługa udostępnia <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może być używany do zapisywania w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).  
  
 Pakietów VSPackage mogą oferować własne usługi przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfejsu.  
  
 Program Visual Studio oferuje ważne usługi, takie jak następujące:  
  
|Usługa IDE|Opis|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Zapewnia dostęp do usług IDE związanych z podstawowymi funkcjami, pakietów VSPackage i rejestrem.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Zapewnia podstawowe funkcje związane z oknami i interfejsem użytkownika w IDE, takie jak możliwość tworzenia narzędzi i okien dokumentów.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zawiera podstawowe funkcje związane z rozwiązaniami, takie jak możliwość wyliczania projektów, tworzenia nowych projektów i monitorowania zmian w projekcie.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)  
 Przedstawia ważne elementy usługi Visual Studio.  
  
 [Instrukcje: uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)  
 W tym artykule omówiono sposób żądania (użytkowania) usługi.  
  
 [Instrukcje: dostarczanie usługi](../extensibility/how-to-provide-a-service.md)  
 W tym artykule omówiono sposób świadczenia usługi.  
  
 [Instrukcje: dostarczanie asynchronicznej usługi programu Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 W tym artykule omówiono sposób dostarczania usługi asynchronicznej.  
  
 [Instrukcje: rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md)  
 Omawia typowe problemy i prezentuje do nich rozwiązania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
