---
title: 'Instrukcje: Use GetGlobalService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 0161b3e44b44567166a337d94101778074561e80
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54833751"
---
# <a name="how-to-use-getglobalservice"></a>Instrukcje: Use GetGlobalService
Czasami może być konieczne uzyskiwanie usługi okno narzędzia lub kontroli kontenera, które nie zostały zlokalizowane; w przeciwnym razie ma zostały umieszczone u dostawcy usług, które nie wie o usługę, którą chcesz. Na przykład można zapisywać w dzienniku aktywności ze znajdujących się pod kontrolą. Aby uzyskać więcej informacji na temat tych i innych scenariuszy, zobacz [jak: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md).  
  
 Możesz uzyskać większość [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usług przez wywołanie metody statyczne <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> opiera się na pamięci podręcznej usługodawcy, który jest zainicjowany po raz pierwszy pochodną dowolnego pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> jest ulokowany. Musisz gwarantować, że ten warunek jest spełniony; w przeciwnym razie należy przygotować usługę o wartości null.  
  
 Na szczęście <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> działa prawidłowo w większości przypadków.  
  
-   Jeśli pakietu VSPackage udostępnia usługę znanego tylko innego pakietu VSPackage, pakietu VSPackage żądania usługi jest ulokowany przed pakietu VSPackage warunkiem, że usługa jest ładowany.  
  
-   Jeśli okno narzędzia jest tworzony przez pakietu VSPackage, pakietu VSPackage jest ulokowany przed utworzeniem okna narzędzia.  
  
-   Jeśli formant kontenera jest hostowana przez okna narzędzia utworzonego przez pakietu VSPackage, pakietu VSPackage jest ulokowany przed utworzeniem kontenera kontrolki.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Aby uzyskać to usługa firmy znajdujące się w kontenerze okna lub kontroli narzędzi  
  
-   Wstaw ten kod w konstruktorze, okno narzędzia lub kontroli kontenera:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Ten kod uzyskuje usługi SVsActivityLog i rzutuje je na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może służyć do zapisu w dzienniku aktywności. Aby uzyskać przykład, zobacz [jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md)   
 [Korzystanie z usług i dostarczanie](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)