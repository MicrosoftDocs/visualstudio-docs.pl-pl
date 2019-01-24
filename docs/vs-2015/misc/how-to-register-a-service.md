---
title: 'Instrukcje: Zarejestruj usługę | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 14124e84ad7f49326bb9e5346868c177e9d32087
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761619"
---
# <a name="how-to-register-a-service"></a>Instrukcje: Zarejestruj usługę
Środowiska pakietu zarządzanego (MPF) zawiera atrybuty kontrolować rejestracji usług zarządzanych. Narzędzie RegPkg korzysta z tych atrybutów do zarejestrowania usługi za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Przykład  
 Kod, który następuje po pochodzi z [przykłady VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Rejestruje usługę SMyGlobalService z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji na temat <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> i <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, zobacz [rejestrowanie i wyrejestrowywanie pakietów VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Aby zarejestrować to usługa, która zastępuje inną usługę o takiej samej nazwie, użyj <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> zamiast <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby ułatwić ponowną kompilację usługodawcy bez zmieniania klienta usługi lub odwrotnie, można zdefiniować usługę i jego interfejsy w module osobny zestaw. Następujący kod pochodzi z pliku IMyGlobalService.cs w przykładzie Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Jest wymagana do uzyskania interfejsu z niezarządzanego kodu.  
  
> [!NOTE]
>  Mimo że można użyć tego samego typu lub identyfikator GUID dla usługi oraz interfejs, firma Microsoft zaleca, oddziel dwa, ponieważ usługa może narazić różne interfejsy.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie pakietów VSPackage](http://msdn.microsoft.com/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)