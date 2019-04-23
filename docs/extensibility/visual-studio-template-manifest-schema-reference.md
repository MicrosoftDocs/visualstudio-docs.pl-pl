---
title: Szablon programu Visual Studio Manifest odwołanie do schematu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b447225580505959697e14f0c85855452906aa18
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108857"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Szablon usługi Visual Studio manifest odwołanie do schematu
Ten schemat opisuje format manifestu szablonu Visual Studio (*vstman*) plików, które są generowane dla szablonów projektu lub elementu programu Visual Studio. Schemat opisuje także lokalizacji i inne istotne informacje o szablonie.

 : Ponieważ istnieje osobnym i katalogi szablonu projektu, manifest nigdy nie powinna mieć różne szablony elementów i projektów.

> [!IMPORTANT]
>  Ten manifest jest dostępna, począwszy od programu Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest element
 Element główny manifestu.

### <a name="attributes"></a>Atrybuty

- **Wersja**: Ciąg reprezentujący wersja manifestu szablonu. Wymagana.

- **Ustawienia regionalne**: Ciąg reprezentujący ustawień regionalnych lub ustawień regionalnych manifestu szablonu. Wartość ustawienia regionalne ma zastosowanie do wszystkich szablonów. Należy użyć oddzielnych manifestu dla poszczególnych ustawień regionalnych. Opcjonalna.

### <a name="child-elements"></a>Elementy podrzędne

- **VSTemplateContainer** Optional.

- **VSTemplateDir** Optional.

### <a name="parent-element"></a>Element nadrzędny
 Brak.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Kontener szablonu manifestu elementów. Manifest zawiera jeden kontener szablonu dla każdego szablonu, który go definiuje.

### <a name="attributes"></a>Atrybuty
 **VSTemplateType**: Wartość ciągu, który określa typ szablonu (`"Project"`, `"Item"`, lub `"ProjectGroup"`). Wymagane

### <a name="child-elements"></a>Elementy podrzędne

- **RelativePathOnDisk**:  Ścieżka względna pliku szablonu na dysku. Ta lokalizacja definiuje również umieszczania szablonu w drzewie szablonu wyświetlane w **nowy projekt** lub **nowy element** okna dialogowego. Dla wdrożonych jako katalog i poszczególnych plików szablonów ta ścieżka odwołuje się do katalogu zawierającego pliki szablonów. Dla szablonów wdrożony jako *zip* pliku, ścieżka ta powinna być ścieżką do *zip* pliku.

- **VSTemplateHeader: A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element, który opisuje nagłówka.

### <a name="parent-element"></a>Element nadrzędny
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 W tym artykule opisano katalog, w którym znajduje się szablon. Manifest może zawierać więcej niż jednego **VSTemplateDir** wpisy zlokalizowane nazwy i sortowania kolejności w przypadku katalogów do kontrolowania sposobu ich wyświetlania w drzewie kategorii szablonu.

 Ze względu na ich projektu **VSTemplateDir** zapisy mają być wyświetlane tylko w określonych manifestów — ustawienia regionalne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

- **RelativePath**: Ścieżka szablonu. Może istnieć tylko jeden zapis dla ścieżki, więc pierwszy z nich zostanie zarejestrowane dla wszystkich manifestów.

- **LocalizedName**: A **NameDescriptionIcon** element, który określa zlokalizowana nazwa. Opcjonalna.

- **SortOrder**: Ciąg, który określa porządek sortowania. Opcjonalna.

- **ParentFolderOverrideName**: Zastąpiona nazwa folderu nadrzędnego. Opcjonalna. Ten element ma **nazwa** atrybut, który jest wartością ciągu, który określa nazwę.

### <a name="parent-element"></a>Element nadrzędny
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Określa nazwę i opis, prawdopodobnie zlokalizowane szablony. Zobacz **LocalizedName** powyżej.

### <a name="attributes"></a>Atrybuty

- **Pakiet**: Wartość ciągu, który określa pakiet. Opcjonalna.

- **ID**: Wartość ciągu, który określa identyfikator. Opcjonalna.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-element"></a>Element nadrzędny
 **LocalizedName**

## <a name="examples"></a>Przykłady
 Poniższy kod jest przykładem szablonu projektu *vstman* pliku.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Poniższy kod jest przykładem szablon elementu *vstman* pliku.

```xml
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```