---
title: Odwołanie do schematu manifestu szablonu programu Visual Studio | Microsoft Docs
description: Ten schemat zawiera opis formatu plików manifestu szablonu programu Visual Studio, które są generowane dla szablonów projektów lub elementów programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d712f2cb95b2df9680c4476805e9dfb6809cf038
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863840"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Odwołanie do schematu manifestu szablonu programu Visual Studio
Ten schemat opisuje format plików manifestu szablonu programu Visual Studio (*. vstman*), które są generowane dla szablonów projektów lub elementów programu Visual Studio. Schemat opisuje również lokalizację i inne istotne informacje dotyczące szablonu.

 : Ponieważ istnieją osobne katalogi elementów i szablonów projektu, manifest nigdy nie powinien zawierać kombinacji elementów i szablonów projektów.

> [!IMPORTANT]
> Ten manifest jest dostępny w programie Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest, element
 Element główny manifestu.

### <a name="attributes"></a>Atrybuty

- **Wersja**: ciąg reprezentujący wersję manifestu szablonu. Wymagane.

- **Ustawienia regionalne**: ciąg reprezentujący ustawienia regionalne lub wartości lokalne manifestu szablonu. Wartość ustawień regionalnych dotyczy wszystkich szablonów. Należy użyć oddzielnego manifestu dla każdego ustawienia regionalnego. Opcjonalny.

### <a name="child-elements"></a>Elementy podrzędne

- **VSTemplateContainer** Obowiązkowe.

- **VSTemplateDir** Obowiązkowe.

### <a name="parent-element"></a>Element nadrzędny
 Brak.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Kontener elementów manifestu szablonu. Manifest ma jeden kontener szablonu dla każdego zdefiniowanego przez niego szablonu.

### <a name="attributes"></a>Atrybuty
 **VSTemplateType**: wartość ciągu, która określa typ szablonu ( `"Project"` , `"Item"` lub `"ProjectGroup"` ). Wymagane

### <a name="child-elements"></a>Elementy podrzędne

- **RelativePathOnDisk**: ścieżka względna pliku szablonu na dysku. Ta lokalizacja definiuje również położenie szablonu w drzewie szablonów pokazanym w oknie dialogowym **Nowy projekt** lub **nowy element** . W przypadku szablonów wdrożonych jako katalog i pojedyncze pliki ta ścieżka odnosi się do katalogu zawierającego pliki szablonów. W przypadku szablonów wdrożonych jako plik *zip* ścieżka powinna być ścieżką do pliku *. zip* .

- * * VSTemplateHeader: element [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) , który opisuje nagłówek.

### <a name="parent-element"></a>Element nadrzędny
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Opisuje katalog, w którym znajduje się szablon. Manifest może zawierać wiele wpisów **VSTemplateDir** , aby zapewnić zlokalizowaną nazwę i kolejność sortowania dla katalogów kontrolujących ich wygląd w drzewie kategorii szablonów.

 Ze względu na ich projekt wpisy **VSTemplateDir** powinny być wyświetlane tylko w manifestach określonych poza ustawieniami regionalnymi.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

- **RelativePath**: ścieżka szablonu. Może istnieć tylko jeden wpis na ścieżkę, więc pierwszy z nich zostanie wygrany dla wszystkich manifestów.

- Nazwa **zlokalizowana**: element **NameDescriptionIcon** , który określa zlokalizowaną nazwę. Opcjonalny.

- **SortOrder**: ciąg określający porządek sortowania. Opcjonalny.

- **ParentFolderOverrideName**: zastąpiona nazwa folderu nadrzędnego. Opcjonalny. Ten element ma atrybut **name** , który jest wartością ciągu, która określa nazwę.

### <a name="parent-element"></a>Element nadrzędny
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Określa nazwę i opis, prawdopodobnie dla zlokalizowanych szablonów. Zobacz **zlokalizowany** powyżej.

### <a name="attributes"></a>Atrybuty

- **Package**: wartość ciągu określająca pakiet. Opcjonalny.

- **ID**: wartość ciągu określająca identyfikator. Opcjonalny.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-element"></a>Element nadrzędny
 **Zlokalizowana**

## <a name="examples"></a>Przykłady
 Poniższy kod jest przykładem pliku szablonu projektu *. vstman* .

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

 Poniższy kod stanowi przykład pliku szablonu elementu *. vstman* .

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
