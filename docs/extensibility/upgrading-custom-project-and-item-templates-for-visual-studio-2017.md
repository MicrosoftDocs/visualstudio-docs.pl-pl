---
title: Uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017
titleSuffix: ''
description: Dowiedz się, jak zaktualizować niestandardowy szablon projektu i elementu z poprzednich wersji programu Visual Studio SDK do użycia z programem Visual Studio 2017 i nowszymi wersjami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 84e9b08350cf5977269bfbcf28ca5335e17f024d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893408"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Uaktualnij niestandardowy Szablony projektów i elementów dla programu Visual Studio 2017

Począwszy od programu Visual Studio 2017, program Visual Studio odnajduje szablony projektów i elementów, które zostały zainstalowane przez plik. vsix lub. msi w inny sposób do poprzednich wersji programu Visual Studio. Jeśli masz własne rozszerzenia, które używają niestandardowych szablonów projektów lub elementów, musisz zaktualizować rozszerzenia. W tym artykule opisano, co należy zrobić.

Ta zmiana dotyczy tylko programu Visual Studio 2017. Nie ma to wpływu na poprzednie wersje programu Visual Studio.

Jeśli chcesz utworzyć projekt lub szablon elementu jako część rozszerzenia VSIX, zobacz [Tworzenie niestandardowych szablonów projektów i elementów](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Skanowanie szablonu

W poprzednich wersjach programu Visual Studio **devenv/setup** lub **devenv/InstallVSTemplates** przeskanował dysk lokalny, aby znaleźć szablony projektów i elementów. Począwszy od programu Visual Studio 2017, skanowanie jest wykonywane tylko dla lokalizacji na poziomie użytkownika. Domyślna lokalizacja na poziomie użytkownika to **%USERPROFILE%\Documents \\<Visual Studio w wersji \> \Templates \\**. Ta lokalizacja jest używana w szablonach wygenerowanych przez   >  **Szablony eksportu projektu...** , jeśli w kreatorze zostanie wybrana opcja **automatycznie Importuj szablon do programu Visual Studio** .

W przypadku innych lokalizacji (niebędących użytkownikami) należy dołączyć plik manifestu (. vstman), który określa lokalizację i inne cechy szablonu. Plik. vstman jest generowany wraz z plikiem. vstemplate używanym w szablonach. Jeśli instalujesz rozszerzenie przy użyciu pliku. vsix, możesz to zrobić przez ponowne skompilowanie rozszerzenia w programie Visual Studio 2017. Ale jeśli używasz pliku MSI, musisz wprowadzić zmiany ręcznie. Aby zapoznać się z listą czynności, które należy wykonać, aby wprowadzić te zmiany, zobacz  **uaktualnienia rozszerzeń instalowanych z programem. Plik MSI** później na tej stronie.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Jak zaktualizować rozszerzenie VSIX przy użyciu szablonów projektów lub elementów

1. Otwórz rozwiązanie w programie Visual Studio 2017. Zostanie wyświetlony monit o uaktualnienie kodu. Kliknij przycisk **OK**.

2. Po zakończeniu uaktualniania może zajść potrzeba zmiany wersji celu instalacji. W projekcie VSIX Otwórz plik source. Extension. vsixmanifest i wybierz kartę **Zainstaluj obiekty docelowe** . Jeśli pole **zakres wersji** ma wartość **[14,0]**, kliknij przycisk **Edytuj** i zmień je, aby zawierało program Visual Studio 2017. Na przykład możesz ustawić ją na **[14.0, 15.0]** , aby zainstalować rozszerzenie w programie visual Studio 2015 lub visual Studio 2017 lub do **[15,0]** , aby zainstalować je tylko w programie Visual Studio 2017.

3. Ponownie Skompiluj kod.

4. Zamknij program Visual Studio.

5. Zainstaluj VSIX.

6. Możesz przetestować aktualizację, wykonując następujące czynności:

    1. Zmiana skanowania plików jest uaktywniana przez następujący klucz rejestru:

         **reg Add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg: 32**

    2. Po dodaniu klucza Uruchom polecenie **devenv/InstallVSTemplates**.

    3. Otwórz ponownie program Visual Studio. Szablon powinien znajdować się w oczekiwanej lokalizacji.

    > [!NOTE]
    > Szablony projektów rozszerzalności programu Visual Studio nie są dostępne, gdy istnieje klucz rejestru. Należy usunąć klucz rejestru (i ponownie uruchomić **devenv/InstallVSTemplates**), aby móc z nich korzystać.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Inne zalecenia dotyczące wdrażania szablonów projektów i elementów

- Unikaj używania spakowanych plików szablonów. Pliki szablonów spakowanych muszą być dekompresowane, aby można było pobrać zasoby i zawartość, dzięki czemu będą one costlier do użycia. Zamiast tego należy wdrożyć szablony projektów i elementów jako pojedyncze pliki w ich własnym katalogu w celu przyspieszenia inicjowania szablonu. W przypadku rozszerzeń VSIX zadania kompilacji zestawu SDK będą automatycznie rozpakować każdy spakowany szablon podczas tworzenia pliku VSIX.

- Unikaj używania wpisów pakietów/zasobów dla szablonu nazwa, opis, ikona lub Podgląd, aby uniknąć niepotrzebnych obciążeń zestawu zasobów podczas odnajdywania szablonu. Zamiast tego można użyć zlokalizowanych manifestów, aby utworzyć wpis szablonu dla każdej ustawień regionalnych, który używa zlokalizowanych nazw lub właściwości.

- W przypadku dołączania szablonów jako elementów plików generowanie manifestu może nie dać oczekiwanych wyników. W takim przypadku należy dodać ręcznie wygenerowany manifest do projektu VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Zmiany plików w szablonach projektów i elementów
Pokazujemy punkty różnic między wersjami plików szablonów programu Visual Studio 2015 i Visual Studio 2017, aby można było poprawnie utworzyć nowe pliki.

 Oto domyślny plik Project. vstemplate utworzony przez program Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Poniżej znajduje się plik. vstman (można go znaleźć w katalogu manifestu projektu VSIX), który spowodował ponowne skompilowanie projektu VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Informacje dostarczone przez element [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) pozostają takie same. **\<VSTemplateContainer>** Element wskazuje plik. vstemplate dla skojarzonego szablonu.

 Oto domyślny plik Item. vstemplate utworzony przez program Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Poniżej znajduje się plik. vstman (można go znaleźć w katalogu manifestu projektu VSIX), który spowodował ponowne skompilowanie projektu VSIX:

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

 Informacje podane przez **\<TemplateData>** element pozostają takie same. **\<VSTemplateContainer>** Element wskazuje plik. vstemplate dla skojarzonego szablonu

 Aby uzyskać więcej informacji na temat różnych elementów pliku. vstman, zobacz [odwołania do schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Uaktualnienia dla rozszerzeń zainstalowanych za pomocą programu. Pakiet

Niektóre rozszerzenia oparte na MSI wdrażają szablony do popularnych lokalizacji szablonów, takich jak następujące katalogi:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/elementów\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<extensionname \> \\<Project/elementów\>**

Jeśli rozszerzenie wykonuje wdrożenie oparte na instalatorze MSI, należy wygenerować manifest szablonu ręcznie i upewnić się, że jest on uwzględniony w instalatorze rozszerzenia. Porównaj przykłady. vstman wymienione powyżej oraz odwołanie do [schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Utwórz oddzielne manifesty dla szablonów projektów i elementów, a następnie wskaż katalog główny szablonu zgodnie z powyższym opisem. Utwórz jeden manifest na rozszerzenie i ustawienia regionalne.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z odnajdywaniem szablonów](troubleshooting-template-discovery.md)
- [Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)
