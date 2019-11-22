---
title: Pakietów VSPackage i struktura pakietu zarządzanego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298233"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Pakietów VSPackage i struktura pakietu zarządzanego
Możesz skrócić czas opracowywania, tworząc pakietu VSPackage przy użyciu klas struktury zarządzanego pakietu (MPF), a nie przy użyciu klas międzyoperacyjnych modelu COM.  
  
 Istnieją dwa sposoby tworzenia zarządzanego pakietu VSPackage:  
  
- Użyj szablonu projektu pakietu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
     Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie polecenia menu przy użyciu szablonu pakietu programu Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Kompiluj swój pakietu VSPackage bez szablonu projektu pakietu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
     Na przykład można skopiować przykładową pakietu VSPackage i zmienić identyfikatory GUID i nazwy. 
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzane klasy struktury pakietów](../misc/managed-package-framework-classes.md)  
 Opisuje i wyświetla listę przestrzeni nazw klas MPF i plików DLL.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przewodnik: Tworzenie polecenia menu przy użyciu szablonu pakietu Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Wyjaśnia, jak utworzyć zarządzany pakietu VSPackage.  
  
 [Zarządzane pakietów VSPackage](../misc/managed-vspackages.md)  
 Wprowadza aspekty pakietów VSPackage, które mają zastosowanie do kodu zarządzanego.