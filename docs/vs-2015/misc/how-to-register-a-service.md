---
title: 'Instrukcje: Rejestrowanie usługi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: f41578f2522487f746a469933a2269a621390f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784863"
---
# <a name="how-to-register-a-service"></a>Instrukcje: Rejestrowanie usługi
Struktura pakietu zarządzanego (MPF) zawiera atrybuty umożliwiające kontrolę rejestracji usług zarządzanych. Narzędzie RegPkg używa tych atrybutów do zarejestrowania usługi w usłudze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="example"></a>Przykład  
 Poniższy kod pochodzi z [przykładów VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>Rejestruje usługę SMyGlobalService w usłudze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aby uzyskać więcej informacji na temat usługi <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> i <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , zobacz [Rejestrowanie i Wyrejestrowywanie pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Aby zarejestrować usługę, która zastępuje inną usługę o tej samej nazwie, użyj <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> zamiast <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby ułatwić ponowne skompilowanie dostawcy usług bez zmiany klienta usługi lub odwrotnie, można zdefiniować usługę i jej interfejsy w osobnym module zestawu. Poniższy kod pochodzi z pliku IMyGlobalService.cs w przykładzie Reference. Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>Jest to wymagane do uzyskania interfejsu z kodu niezarządzanego.  
  
> [!NOTE]
> Chociaż można użyć tego samego typu lub identyfikatora GUID dla usługi i interfejsu, zalecamy oddzielenie dwóch, ponieważ usługa może uwidaczniać różne interfejsy.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie pakietów VSPackage](../extensibility/internals/registering-vspackages.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)