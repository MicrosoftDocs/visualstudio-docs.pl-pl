---
title: 'Instrukcje: korzystanie z GetGlobalService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948185"
---
# <a name="how-to-use-getglobalservice"></a>Instrukcje: korzystanie z GetGlobalService
Czasami może być konieczne uzyskanie usługi z okna narzędzi lub kontenera kontroli, który nie został zlokalizowany, lub w innym systemie, który jest zlokalizowany przez dostawcę usług, który nie wie o żądaną usługę. Na przykład możesz chcieć zapisać w dzienniku aktywności z poziomu kontrolki. Aby uzyskać więcej informacji na temat tych i innych scenariuszy, zobacz [How to: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md).  
  
 Większość usług można uzyskać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , wywołując metodę statyczną <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> opiera się na buforowanym dostawcy usług, który jest inicjowany po raz pierwszy każdy pakietu VSPackage z elementu <xref:Microsoft.VisualStudio.Shell.Package> jest zlokalizowany. Należy zastanowić się, że ten warunek jest spełniony lub został przygotowany dla usługi o wartości null.  
  
 Na szczęście <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> program działa prawidłowo w większości czasu.  
  
- Jeśli pakietu VSPackage zapewnia usługę znaną tylko innemu pakietu VSPackage, pakietu VSPackage żądający usługi jest zlokalizowana przed załadowaniem usługi pakietu VSPackage.  
  
- Jeśli okno narzędzi jest tworzone przez pakietu VSPackage, pakietu VSPackage jest zlokalizowane przed utworzeniem okna narzędzi.  
  
- Jeśli kontener formantów jest hostowany w oknie narzędzi utworzonym przez pakietu VSPackage, pakietu VSPackage jest zlokalizowane przed utworzeniem kontenera sterowania.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Aby uzyskać usługę z poziomu okna narzędzi lub kontenera kontrolek  
  
- Wstaw ten kod w konstruktorze, oknie narzędzi lub kontenerze formantów:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Ten kod uzyskuje usługę SVsActivityLog i rzutuje ją na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może być używany do zapisywania w dzienniku aktywności. Aby zapoznać się z przykładem, zobacz [How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md)   
 [Używanie i świadczenie usług](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)