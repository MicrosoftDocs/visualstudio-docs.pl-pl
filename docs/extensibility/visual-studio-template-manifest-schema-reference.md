---
title: Visual Studio schematu manifestu szablonu | Microsoft Docs
description: W tej informacji o schemacie opisano format Visual Studio manifestu szablonu, które są generowane Visual Studio szablonów projektów lub elementów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 259d2dd050f4681053f331bfd4ec39dd7b214059
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905387"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio schematu manifestu szablonu
W tym schemacie opisano format Visual Studio manifestu szablonu *(vstman),* które są generowane Visual Studio szablonów projektów lub elementów. Schemat opisuje również lokalizację i inne istotne informacje o szablonie.

 : ponieważ istnieją oddzielne katalogi szablonów elementów i projektów, manifest nigdy nie powinien mieć kombinacji szablonów elementów i projektów.

> [!IMPORTANT]
> Ten manifest jest dostępny od Visual Studio 2017 r.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest, element
 Element główny manifestu.

### <a name="attributes"></a>Atrybuty

- **Wersja:** ciąg reprezentujący wersję manifestu szablonu. Wymagane.

- **Locale**: ciąg reprezentujący wartości regionalnych lub regionalnych manifestu szablonu. Wartość regionalnych ma zastosowanie do wszystkich szablonów. Należy użyć oddzielnego manifestu dla poszczególnych danych regionalnych. Opcjonalny.

### <a name="child-elements"></a>Elementy podrzędne

- **VSTemplateContainer** Opcjonalne.

- **VSTemplateDir** Opcjonalne.

### <a name="parent-element"></a>Element nadrzędny
 Brak.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Kontener elementów manifestu szablonu. Manifest ma jeden kontener szablonów dla każdego szablonu, który definiuje.

### <a name="attributes"></a>Atrybuty
 **VSTemplateType:** wartość ciągu określająca typ szablonu ( `"Project"` , `"Item"` lub `"ProjectGroup"` ). Wymagane

### <a name="child-elements"></a>Elementy podrzędne

- **RelativePathOnDisk:** ścieżka względna pliku szablonu na dysku. Ta lokalizacja definiuje również umieszczanie szablonu w drzewie szablonów wyświetlanym w oknie dialogowym **Nowy** projekt lub **Nowy** element. W przypadku szablonów wdrożonych jako katalog i poszczególne pliki ta ścieżka odnosi się do katalogu zawierającego pliki szablonu. W przypadku szablonów wdrożonych *.zip* pliku ta ścieżka powinna być ścieżką do *.zip* pliku.

- **VSTemplateHeader: element [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) opisujący nagłówek.

### <a name="parent-element"></a>Element nadrzędny
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Opisuje katalog, w którym znajduje się szablon. Manifest może zawierać wiele **wpisów VSTemplateDir** w celu zapewnienia zlokalizowanej nazwy i sortowania katalogów w celu kontrolowania ich wyglądu w drzewie kategorii szablonów.

 Ze względu na projekt wpisy **VSTemplateDir** powinny pojawiać się tylko w manifestach innych niż określone przez zmiany regionalnych.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

- **RelativePath:** ścieżka szablonu. Na ścieżkę może być tylko jeden wpis, więc pierwszy z nich wygra dla wszystkich manifestów.

- **LocalizedName:** element **NameDescriptionIcon** określający nazwę zlokalizowanej. Opcjonalny.

- **SortOrder:** ciąg określający kolejność sortowania. Opcjonalny.

- **ParentFolderOverrideName:** zastąpiona nazwa folderu nadrzędnego. Opcjonalny. Ten element ma **atrybut Name,** który jest wartością ciągu określającą nazwę.

### <a name="parent-element"></a>Element nadrzędny
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Określa nazwę i opis, prawdopodobnie dla zlokalizowanych szablonów. Zobacz **LocalizedName** powyżej.

### <a name="attributes"></a>Atrybuty

- **Pakiet:** wartość ciągu określająca pakiet. Opcjonalny.

- **ID:** wartość ciągu określająca identyfikator. Opcjonalny.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-element"></a>Element nadrzędny
 **Localizedname**

## <a name="examples"></a>Przykłady
 Poniższy kod jest przykładem pliku *vstman* szablonu projektu.

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

 Poniższy kod jest przykładem pliku *vstman* szablonu elementu.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
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
