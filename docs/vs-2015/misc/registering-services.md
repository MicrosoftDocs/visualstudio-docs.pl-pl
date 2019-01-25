---
title: Rejestrowanie usługi | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775523"
---
# <a name="registering-services"></a>Rejestrowanie usługi
Aby zapewnić obsługę ładowania na żądanie, dostawca usług należy zarejestrować jego usług globalnych z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Podczas tworzenia aplikacji, dostawcom usług zarządzanych rejestracji usług i zastąpienia usługi przez dodawanie atrybutów do kodu źródłowego dla pakietów, a następnie tworzenia pakietów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Spowoduje to uruchomienie narzędzia RegPkg.exe na wynikowy zestaw rejestrowania pakietu i przygotowywanie wdrożenia. Aby uzyskać więcej informacji, zobacz [jak: Zarejestruj usługę](../misc/how-to-register-a-service.md).  
  
 Dostawcy usług niezarządzanych musisz się zarejestrować, usług, które dostarczają z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w usługach sekcji lub usługa zastępuje części rejestru systemowego. Poniższy fragment pliku reg pokazuje, jak usługa SVsTextManager, może zostać zarejestrowana:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 W powyższym przykładzie numer wersji jest wersją [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], takie jak w wersji 7.1 lub 8.0, klucz {F5E7E71D-1401-11d1-883B-0000F87579D2} jest identyfikatorem usługi (SID), usługi, SVsTextManager i {wartość domyślną F5E7E720-1401-11d1-883B-0000F87579D2} jest identyfikator GUID pakietu VSPackage, który udostępnia usługę Menedżera tekstu pakietu.  
  
## <a name="remote-services-and-background-threads"></a>Usługi zdalnej i wątków w tle  
 Udostępniane usługi nie są automatycznie dostępne zdalnie lub wątków w tle. Aby zapewnić ich dostępność, możesz tworzyć i zarejestrować bibliotekę typów.  
  
 Z niezarządzanego kodu, który używa programu Visual Studio biblioteki (VSL) można zarejestrować biblioteki typów w ten sposób:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Z poziomu kodu zarządzanego możesz dodać krok po kompilacji w następujący sposób:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z usług i dostarczanie](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)