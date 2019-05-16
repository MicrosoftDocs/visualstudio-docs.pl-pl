---
title: Pakietów VSPackage i środowiska pakietu zarządzanego | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5b72b2c3bd6b03d1d3f3e50135c2ddf4758a4bd9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683046"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Pakietów VSPackage i środowiska pakietu zarządzanego
Tworząc pakietu VSPackage przy użyciu pakietu zarządzanych klas framework (MPF) zamiast przy użyciu klas międzyoperacyjnego modelu COM, można zmniejszyć czas opracowywania.  
  
 Istnieją dwa sposoby tworzenia zarządzanego pakietu VSPackage:  
  
- Użyj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablon projektu pakietu  
  
     Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie polecenia Menu za pomocą szablonu pakietu programu Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Twórz swoje pakietu VSPackage bez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablon projektu pakietu  
  
     Można na przykład skopiuj przykład pakietu VSPackage i zmieniać identyfikatory GUID i nazw. Przykłady można znaleźć w sekcji VSX [galerii kodów](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzane klasy Framework pakietu](../misc/managed-package-framework-classes.md)  
 W tym artykule opisano i przedstawiono MPF klasy w przestrzeni nazw i pliki DLL.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przewodnik: Tworzenie polecenia Menu za pomocą szablonu pakietu programu Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Wyjaśnia sposób tworzenia zarządzanego pakietu VSPackage.  
  
 [Managed VSPackages](../misc/managed-vspackages.md)  
 Wprowadza aspektów pakietów VSPackage, które są stosowane do kodu zarządzanego.