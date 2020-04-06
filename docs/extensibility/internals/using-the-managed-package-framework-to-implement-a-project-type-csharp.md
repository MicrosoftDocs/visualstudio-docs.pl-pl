---
title: Korzystanie z struktury pakietu zarządzanego dla typu projektu (C#) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704121"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Implementowanie typu projektu przy użyciu środowiska pakietu zarządzanego (C#)
Struktura pakietów zarządzanych (MPF) zapewnia klasy języka C#, których można użyć lub dziedziczyć w celu zaimplementowania własnych typów projektów. MPF implementuje wiele interfejsów Visual Studio oczekuje typu projektu, aby zapewnić, pozostawiając swobodę skoncentrowania się na implementacji szczegółowych informacji typu projektu.

## <a name="using-the-mpf-project-source-code"></a>Korzystanie z kodu źródłowego projektu MPF
 Struktura pakietu zarządzanego dla projektów (MPFProj) zapewnia klasy pomocnicze do tworzenia i zarządzania nowym systemem projektów. W przeciwieństwie do innych klas w MPF klasy projektu nie są uwzględniane w zestawach dostarczanych z programem Visual Studio. Zamiast tego klasy projektu są dostarczane jako kod źródłowy w [MPF dla projektów 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Aby dodać ten projekt do rozwiązania VSPackage, wykonaj następujące czynności:

1. Pobierz pliki MPFProj do *MPFProjectDir*.

2. W pliku *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file zmień następujący blok:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Utwórz projekt VSPackage.

2. Zwalnianie projektu VSPackage.

3. Edytuj plik VSPackage .csproj, dodając następujący `<Import>` blok przed innymi blokami:

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

2. Zamknij i ponownie otwórz rozwiązanie VSPackage.

3. Otwórz ponownie projekt VSPackage. Powinien zostać wyświetlony nowy katalog o nazwie ProjectBase.

4. Dodaj następujące odwołanie do projektu VSPackage:

     Microsoft.Build.Tasks.4.0

5. Skompiluj projekt.

## <a name="hierarchy-classes"></a>Klasy hierarchii
 W poniższej tabeli podsumowano klasy w MPFProj, które obsługują hierarchie projektu. Aby uzyskać więcej informacji, zobacz [Hierarchie i Zaznaczenie](../../extensibility/internals/hierarchies-and-selection.md).

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
 W poniższej tabeli wymieniono klasy w MPF, które obsługują obsługę dokumentów. Aby uzyskać więcej informacji, zobacz [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

|Nazwa klasy|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Klasy konfiguracji i wyjścia
 W poniższej tabeli wymieniono klasy w mpf, które umożliwiają typy projektów obsługuje wiele konfiguracji, takich jak debugowanie i wydanie i kolekcje danych wyjściowych projektu. Aby uzyskać więcej informacji, zobacz [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md).

|Nazwa klasy|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Klasy automatyzacji i wsparcia
 W poniższej tabeli wymieniono klasy w mpf, które obsługują automatyzację, dzięki czemu użytkownicy typu projektu mogą pisać dodatki.

|Nazwa klasy|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Klasy właściwości
 W poniższej tabeli wymieniono klasy w mpf, które umożliwiają typom projektów dodawanie właściwości, które użytkownicy mogą przeglądać i modyfikować w przeglądarce właściwości.

|Nazwa klasy|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
