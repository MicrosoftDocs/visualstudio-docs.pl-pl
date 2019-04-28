---
title: Zarządzane klasy Framework pakietu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: 75f7cb153a976614ff790095141a820af80b5834
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422754"
---
# <a name="managed-package-framework-classes"></a>Zarządzane klasy Framework pakietu
Pakiet zarządzanych klas framework (MPF) może służyć do tworzenia pakietów VSPackage przy użyciu kodu zarządzanego. Zapewniają one domyślnej implementacji dla wielu interfejsów pakietu VSPackage. Ukrywając szczegółów implementacji i złożoności MPF pozwala na tworzenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integracji produktów za pomocą minimalnej ilości kodu.  
  
> [!WARNING]
> Większość zestawów zawierających klasy środowiska pakietu zarządzanego są dostarczane za pomocą programu Visual Studio SDK. Możesz pobrać kod źródłowy dla zarządzanych w pakiecie struktury dla projektów w [zarządzanego środowiska pakietu dla projektów](http://mpfproj11.codeplex.com/).  
  
## <a name="mpf-namespaces"></a>Przestrzenie nazw MPF  
 W poniższej tabeli wymieniono MPF przestrzenie nazw, dostarczone przez [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Przestrzeń nazw|Spis treści|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Zawiera przydatne klasy obsługi błędów COM [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stałe i Win32 dla systemu windows.|  
|<xref:Microsoft.VisualStudio.Package>|Zawiera kod zarządzany otok dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektów, edytory i MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Zawiera klasy bazowe MPF, z których mogą pochodzić implementację wielu obiektów programu Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Zawiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia projektanta.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Zawiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia projektanta serializacji.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Zawiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia projektanta CodeDom.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Obsługuje projektu podtypy (znany także jako "odmian").|  
  
## <a name="see-also"></a>Zobacz też  
 [Pakietów VSPackage i środowiska pakietu zarządzanego](../misc/vspackages-and-the-managed-package-framework.md)   
 [Przy użyciu zestawów międzyoperacyjnych programu Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Pakietów VSPackage i środowiska pakietu zarządzanego](../misc/vspackages-and-the-managed-package-framework.md)