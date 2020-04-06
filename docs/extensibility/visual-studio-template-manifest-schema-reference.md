---
title: Odwołanie do schematu manifestu szablonu programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697989"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Odwołanie do schematu manifestu szablonu programu Visual Studio
Ten schemat opisuje format manifestu szablonu programu Visual Studio (*vstman*) plików, które są generowane dla projektu programu Visual Studio lub szablonów elementów. Schemat opisuje również lokalizację i inne istotne informacje o szablonie.

 : Ponieważ istnieją oddzielne katalogi szablonów elementów i projektów, manifest nigdy nie powinien mieć kombinacji szablonów elementów i projektów.

> [!IMPORTANT]
> Ten manifest jest dostępny od programu Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Element VSTemplateManifest
 Element główny manifestu.

### <a name="attributes"></a>Atrybuty

- **Wersja**: Ciąg reprezentujący wersję manifestu szablonu. Wymagany.

- **Ustawienia regionalne:** Ciąg reprezentujący ustawienia regionalne lub ustawienia regionalne manifestu szablonu. Wartość ustawień regionalnych ma zastosowanie do wszystkich szablonów. Należy użyć oddzielnego manifestu dla każdego ustawienia regionalne. Element opcjonalny.

### <a name="child-elements"></a>Elementy podrzędne

- **VSTemplateKontainer** Opcjonalne.

- **VSTemplateDir** Opcjonalne.

### <a name="parent-element"></a>Element nadrzędny
 Brak.

## <a name="vstemplatecontainer"></a>VSTemplateKontainer
 Kontener elementów manifestu szablonu. Manifest ma jeden kontener szablonu dla każdego szablonu, który definiuje.

### <a name="attributes"></a>Atrybuty
 **VSTemplateType**: Wartość ciągu określająca typ szablonu (`"Project"`, , `"Item"`lub `"ProjectGroup"`). Wymagany

### <a name="child-elements"></a>Elementy podrzędne

- **RelativePathOnDisk**: Ścieżka względna pliku szablonu na dysku. Ta lokalizacja definiuje również położenie szablonu w drzewie szablonów wyświetlanych w oknie dialogowym **Nowy projekt** lub **Nowy element.** W przypadku szablonów wdrożonych jako katalog i pojedyncze pliki ta ścieżka odnosi się do katalogu zawierającego pliki szablonów. W przypadku szablonów wdrożonych jako plik *zip* ta ścieżka powinna być ścieżką do pliku *zip.*

- **VSTemplateHeader: Element [TemplateData opisujący](../extensibility/templatedata-element-visual-studio-templates.md) nagłówek.

### <a name="parent-element"></a>Element nadrzędny
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Opisuje katalog, w którym znajduje się szablon. Manifest może zawierać wiele wpisów **VSTemplateDir,** aby zapewnić zlokalizowaną nazwę i sortowanie kolejności katalogów, aby kontrolować ich wygląd w drzewie kategorii szablonu.

 Ze względu na ich projekt **wpisy VSTemplateDir** powinny być wyświetlane tylko w manifestach określonych w ustawieniach regionalnych.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

- **RelativePath**: Ścieżka szablonu. Na ścieżkę może być tylko jeden wpis, więc pierwszy z nich wygra dla wszystkich manifestów.

- **LocalizedName:** A **NameDescriptionIcon** element, który określa zlokalizowaną nazwę. Element opcjonalny.

- **SortOrder**: Ciąg określający kolejność sortowania. Element opcjonalny.

- **ParentFolderOverrideName**: Zastąpiona nazwa folderu nadrzędnego. Element opcjonalny. Ten element ma atrybut **Name,** który jest wartością ciągu, która określa nazwę.

### <a name="parent-element"></a>Element nadrzędny
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NazwaDescriptionIcon
 Określa nazwę i opis, prawdopodobnie dla zlokalizowanych szablonów. Zobacz **LocalizedName** powyżej.

### <a name="attributes"></a>Atrybuty

- **Package**: Wartość ciągu określająca pakiet. Element opcjonalny.

- **ID**: Wartość ciągu określająca identyfikator. Element opcjonalny.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-element"></a>Element nadrzędny
 **Localizedname**

## <a name="examples"></a>Przykłady
 Poniższy kod jest przykładem pliku *.vstman* szablonu projektu.

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

 Poniższy kod jest przykładem pliku *.vstman* szablonu elementu.

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
