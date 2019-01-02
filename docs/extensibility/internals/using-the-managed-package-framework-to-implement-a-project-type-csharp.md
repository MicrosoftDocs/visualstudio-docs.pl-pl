---
title: Przy użyciu środowiska pakietu zarządzanego dla typu projektu (C#) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 489537560d43246097d00121142d729be130ec9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961637"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Implementowanie typu projektu przy użyciu środowiska pakietu zarządzanego (C#)
Framework pakietu zarządzanego (MPF) udostępnia klasy C#, możesz użyć lub dziedziczyć zaimplementować swój własny typ projektu. MPF implementuje wiele interfejsów programu Visual Studio oczekuje, że typ projektu, aby zapewnić, pozostawiając użytkownika na skoncentrowanie się na implementowaniu dane tego typu projektu.  
  
## <a name="using-the-mpf-project-source-code"></a>Za pomocą kodu źródłowego MPF projektów  
 Środowiska pakietu zarządzanego dla projektów (MPFProj) udostępnia klasy pomocy do tworzenia i zarządzania nowy system projektów. W przeciwieństwie do innych klas w MPF klasy projektu nie są uwzględnione w zestawach dostarczane z programem Visual Studio. Zamiast tego klasy projektu są dostarczane jako kod źródłowy w [MPF projektów 2013](https://github.com/tunnelvisionlabs/MPFProj10).  
  
 Aby dodać ten projekt do rozwiązania pakietu VSPackage, wykonaj następujące czynności:  
  
1.  Pobierz pliki MPFProj do *MPFProjectDir*.  
  
2.  W *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, zmień następujący blok:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Tworzenie projektu pakietu VSPackage.  
  
2.  Cofnij ładowanie projektu pakietu VSPackage.  
  
3.  Edytuj plik csproj pakietu VSPackage, dodając następujący blok przed innymi `<Import>` bloków:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Zapisz projekt.  
  
2.  Zamknij i ponownie otwórz rozwiązanie pakietu VSPackage.  
  
3.  Otwórz projekt pakietu VSPackage. Powinien zostać wyświetlony nowy katalog o nazwie ProjectBase.  
  
4.  Dodaj następujące odwołanie do projektu pakietu VSPackage:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Skompiluj projekt.  
  
## <a name="hierarchy-classes"></a>Hierarchia klas  
 Poniższa tabela zawiera podsumowanie klas w MPFProj, które obsługują hierarchii projektu. Aby uzyskać więcej informacji, zobacz [hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Klasy obsługi dokumentów  
 Poniższa tabela zawiera listę klas w MPF, które obsługują obsługi dokumentów. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Konfiguracja i klas danych wyjściowych  
 Poniższa tabela zawiera listę klas w MPF, które umożliwiają typów projektów obsługuje wiele konfiguracji, takich jak debugowania i wydania i kolekcje danych wyjściowych projektu. Aby uzyskać więcej informacji, zobacz [zarządzanie opcje konfiguracji](../../extensibility/internals/managing-configuration-options.md).  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Klasy obsługi automatyzacji  
 Poniższa tabela zawiera listę klas w MPF, które obsługują automatyzacji, dzięki czemu użytkownicy tego typu projektu mogą tworzyć dodatki.  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Właściwości klasy  
 Następująca tabela zawiera listę klas w MPF, które umożliwiają typów projektów Dodaj właściwości, że użytkownicy mogą przeglądać i modyfikować w przeglądarce właściwości.  
  
|Nazwa klasy|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|