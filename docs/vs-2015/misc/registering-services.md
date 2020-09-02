---
title: Rejestrowanie usług | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 64f2afa6e853978e919e466f91475bed1e8d698c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62971293"
---
# <a name="registering-services"></a>Rejestrowanie usług
Aby można było obsługiwać ładowanie na żądanie, dostawca usług musi zarejestrować swoje usługi globalne w usłudze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Podczas opracowywania dostawcy usług zarządzanych rejestrują usługi i przesłonięcia usług przez dodanie atrybutów do kodu źródłowego dla pakietów, a następnie skompilowanie pakietów w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Spowoduje to uruchomienie narzędzia RegPkg.exe na wynikającym zestawie, zarejestrowanie pakietu i przygotowanie go do wdrożenia. Aby uzyskać więcej informacji, zobacz [How to: register a Service](../misc/how-to-register-a-service.md).  
  
 Niezarządzani dostawcy usług muszą rejestrować usługi, których zapewniają, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w sekcji usług lub w sekcji przesłonięcia usługi w rejestrze systemu. Poniższy fragment pliku reg zawiera informacje o tym, jak usługa, SVsTextManager może być zarejestrowana:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 W powyższym przykładzie numer wersji to wersja programu, na przykład [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 7,1 lub 8,0, klucz {F5E7E71D-1401-11D1-883B-0000F87579D2} to identyfikator usługi (SID) usługi, SVsTextManager i wartość domyślna {F5E7E720-1401-11D1-883B-0000F87579D2} to identyfikator GUID pakietu pakietu vspackageego Menedżera tekstu, który udostępnia usługę.  
  
## <a name="remote-services-and-background-threads"></a>Usługi zdalne i wątki w tle  
 Udostępniane usługi nie są automatycznie dostępne zdalnie lub w tle wątków. Aby udostępnić te elementy, należy skompilować i zarejestrować bibliotekę typów.  
  
 Z niezarządzanego kodu, który korzysta z biblioteki programu Visual Studio (VSL), możesz zarejestrować bibliotekę typów w następujący sposób:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 W kodzie zarządzanym można dodać krok po kompilacji podobny do tego:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie i świadczenie usług](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)