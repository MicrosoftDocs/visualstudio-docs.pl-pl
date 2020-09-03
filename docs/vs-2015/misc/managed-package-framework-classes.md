---
title: Zarządzane klasy struktury pakietów | Microsoft Docs
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
ms.openlocfilehash: 2e9fe1abb82d3d64232e3e5e2a6d117c1068aa1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297701"
---
# <a name="managed-package-framework-classes"></a>Zarządzane klasy struktury pakietów
Klasy Managed Package Framework (MPF) mogą służyć do tworzenia pakietów VSPackage przy użyciu kodu zarządzanego. Zapewniają one domyślne implementacje dla wielu interfejsów pakietu VSPackage. Ukrywając szczegóły i złożoność implementacji, MPF umożliwia tworzenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] produktów integracyjnych o minimalnej ilości kodu.  
  
> [!WARNING]
> Większość zestawów zawierających zarządzane klasy struktury pakietów jest dostarczana z zestawem SDK programu Visual Studio. Możesz pobrać kod źródłowy zarządzanej platformy dla projektów w [strukturze pakietów zarządzanych dla projektów](https://archive.codeplex.com/?p=mpfproj11).  
  
## <a name="mpf-namespaces"></a>Przestrzenie nazw MPF  
 W poniższej tabeli wymieniono przestrzenie nazw MPF udostępniane przez program [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
|Przestrzeń nazw|Zawartość|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Zawiera użyteczne klasy do obsługi błędów COM, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stałych i Windows Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Obejmuje otoki kodu zarządzanego dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektów, edytorów i programu MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Zawiera klasy bazowe MPF, z których można utworzyć wiele popularnych obiektów programu Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Zawiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia projektanta.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Zawiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia projektanta serializacji.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Zawiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia projektanta CodeDOM.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Obsługuje podtypy projektu (nazywane również "wersjami").|  
  
## <a name="see-also"></a>Zobacz też  
 [Pakietów VSPackage i struktura pakietu zarządzanego](../misc/vspackages-and-the-managed-package-framework.md)   
 [Używanie zestawów międzyoperacyjnych programu Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Pakietów VSPackage i struktura pakietu zarządzanego](../misc/vspackages-and-the-managed-package-framework.md)