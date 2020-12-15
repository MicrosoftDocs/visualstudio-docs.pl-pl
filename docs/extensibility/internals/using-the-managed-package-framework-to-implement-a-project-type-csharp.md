---
title: Używanie struktury pakietu zarządzanego dla typu projektu (C#)
description: Dowiedz się więcej na temat zarządzanej struktury pakietów, która dostarcza klasy .NET, których można użyć lub dziedziczyły z, aby zaimplementować własne typy projektów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b425962ed0f664b8255b6489ac8f0d38be7c13c
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487546"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Implementowanie typu projektu przy użyciu środowiska pakietu zarządzanego (C#)
Struktura pakietu zarządzanego (MPF) zawiera klasy języka C#, których można użyć lub dziedziczyły z, aby zaimplementować własne typy projektów. MPF implementuje wiele interfejsów program Visual Studio oczekuje typu projektu, który należy podać, dzięki czemu możesz skoncentrować się na implementowaniu szczegółowych informacji o typie projektu.

## <a name="using-the-mpf-project-source-code"></a>Korzystanie z kodu źródłowego projektu MPF
 Struktura pakietów zarządzanych dla projektów (MPFProj) zapewnia klasy pomocników do tworzenia nowego systemu projektu i zarządzania nim. W przeciwieństwie do innych klas w MPF, klasy projektu nie są uwzględnione w zestawach dostarczanych z programem Visual Studio. Zamiast tego klasy projektu są dostarczane jako kod źródłowy w [MPF for projects 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Aby dodać ten projekt do rozwiązania pakietu VSPackage, wykonaj następujące czynności:

1. Pobierz pliki MPFProj do *MPFProjectDir*.

2. W *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.File Zmień następujący blok:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Utwórz projekt pakietu VSPackage.

2. Zwolnij projekt pakietu VSPackage.

3. Edytuj plik pakietu VSPackage. csproj, dodając następujący blok przed innymi `<Import>` blokami:

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Zapisz projekt.

2. Zamknij i ponownie otwórz rozwiązanie pakietu VSPackage.

3. Ponownie otwórz projekt pakietu VSPackage. Powinien zostać wyświetlony nowy katalog o nazwie ProjectBase.

4. Dodaj następujące odwołanie do projektu pakietu VSPackage:

     Microsoft. Build. Tasks. 4.0

5. Skompiluj projekt.

## <a name="hierarchy-classes"></a>Klasy hierarchii
 Poniższa tabela zawiera podsumowanie klas w MPFProj, które obsługują hierarchie projektu. Aby uzyskać więcej informacji, zobacz [hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md).

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

## <a name="document-handling-classes"></a>Klasy Document-Handling
 Poniższa tabela zawiera listę klas w MPF, które obsługują obsługę dokumentów. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

|Nazwa klasy|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Klasy konfiguracji i wyjściowe
 Poniższa tabela zawiera listę klas w MPF, które zezwalają na typy projektów obsługują wiele konfiguracji, takich jak debugowanie i wydanie oraz kolekcje danych wyjściowych projektu. Aby uzyskać więcej informacji, zobacz [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

|Nazwa klasy|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Klasy Automation-Support
 Poniższa tabela zawiera listę klas w MPF, które obsługują automatyzację, tak aby użytkownicy typu projektu mogli pisać dodatki.

|Nazwa klasy|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Klasy właściwości
 Poniższa tabela zawiera listę klas w MPF, które umożliwiają dodawanie właściwości, które użytkownicy mogą przeglądać i modyfikować w przeglądarce właściwości.

|Nazwa klasy|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
