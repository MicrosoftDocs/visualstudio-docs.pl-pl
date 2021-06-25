---
title: Uaktualnianie niestandardowych szablonów projektów i elementów dla Visual Studio 2017
titleSuffix: ''
description: Dowiedz się, jak zaktualizować niestandardowy szablon projektu i elementu z poprzednich wersji zestawu VISUAL STUDIO SDK do użycia z Visual Studio 2017 i nowszymi wersjami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0d07af0a00ab840df8a9af437bcddc427f606948
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903063"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Uaktualnianie programu Custom Szablony projektów i elementów dla programu Visual Studio 2017

Począwszy od Visual Studio 2017 r., program Visual Studio odnajduje szablony projektów i elementów, które zostały zainstalowane przez element vsix lub .msi w inny sposób niż poprzednie wersje Visual Studio. Jeśli jesteś właścicielem rozszerzeń, które używają niestandardowych szablonów projektów lub elementów, musisz zaktualizować rozszerzenia. W tym artykule wyjaśniono, co należy zrobić.

Ta zmiana dotyczy tylko Visual Studio 2017 r. Nie ma to wpływu na poprzednie wersje Visual Studio.

Jeśli chcesz utworzyć szablon projektu lub elementu w ramach rozszerzenia VSIX, zobacz Creating Custom Project and Item Templates (Tworzenie niestandardowych szablonów [projektów i elementów).](../extensibility/creating-custom-project-and-item-templates.md)

## <a name="template-scanning"></a>Skanowanie szablonów

W poprzednich wersjach programu Visual Studio **devenv /setup** lub **devenv /installvstemplates** skanowało dysk lokalny w celu znalezienia szablonów projektów i elementów. Począwszy od Visual Studio 2017 roku skanowanie jest wykonywane tylko dla lokalizacji na poziomie użytkownika. Domyślna lokalizacja na poziomie użytkownika to **%USERPROFILE%\Documents \\<Visual Studio \> \Templates. \\** Ta lokalizacja jest używana w przypadku szablonów generowanych przez polecenie **Project**  >  **Export Templates...,** jeśli w kreatorze wybrano opcję Automatycznie zaimportuj szablon do Visual Studio szablonu. 

W przypadku innych lokalizacji (niebędących użytkownikami) należy dołączyć plik manifestu (.vstman), który określa lokalizację i inne cechy szablonu. Plik .vstman jest generowany wraz z plikiem .vstemplate używanym dla szablonów. Jeśli zainstalujesz rozszerzenie przy użyciu pliku vsix, możesz to zrobić, ponownie skomponuj rozszerzenie w programie Visual Studio 2017. Jeśli jednak używasz .msi, musisz wprowadzić zmiany ręcznie. Aby uzyskać listę zadań, które należy wykonać, aby wprowadzić te zmiany, zobacz Uaktualnienia rozszerzeń zainstalowanych za pomocą .MSI **w** dalszej części tej strony.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>How to Update a VSIX Extension with Project or Item Templates

1. Otwórz rozwiązanie w programie Visual Studio 2017. Zostaniesz poproszony o uaktualnienie kodu. Kliknij przycisk **OK**.

2. Po zakończeniu uaktualniania może być konieczne zmiana wersji obiektu docelowego instalacji. W projekcie VSIX otwórz plik source.extension.vsixmanifest i wybierz **kartę Install Targets (Cele instalacji).** Jeśli pole **Zakres wersji** to **[14.0],** kliknij przycisk **Edytuj** i zmień je, aby uwzględnić Visual Studio 2017. Na przykład można ustawić go na **[14.0,15.0],** aby zainstalować rozszerzenie do programu Visual Studio 2015 lub Visual Studio 2017 albo **na [15.0],** aby zainstalować je tylko do Visual Studio 2017.

3. Skompiluj ponownie kod.

4. Zamknij program Visual Studio.

5. Zainstaluj vsix.

6. Aktualizację można przetestować, wykonując następujące czynności:

    1. Zmiana skanowania plików jest aktywowana za pomocą następującego klucza rejestru:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Po dodaniu klucza uruchom **devenv /installvstemplates.**

    3. Otwórz ponownie Visual Studio. Szablon powinien znaleźć się w oczekiwanej lokalizacji.

    > [!NOTE]
    > Szablony Visual Studio rozszerzalności nie są dostępne, gdy jest obecny klucz rejestru. Należy usunąć klucz rejestru (i ponownie uruchomić **devenv /installvstemplates**), aby ich użyć.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Inne zalecenia dotyczące wdrażania szablonów projektów i elementów

- Unikaj używania plików szablonów mapowanych. Pliki szablonów zmapowanych muszą być nieskompresowane w celu pobrania zasobów i zawartości, więc korzystanie z nich będzie bardziej kosztowne. Zamiast tego należy wdrożyć szablony projektów i elementów jako pojedyncze pliki w ich własnym katalogu, aby przyspieszyć inicjowanie szablonu. W przypadku rozszerzeń VSIX zadania kompilacji zestawu SDK będą automatycznie rozpakować dowolny szablon zip podczas tworzenia pliku VSIX.

- Unikaj używania wpisów identyfikatora pakietu/zasobu dla nazwy szablonu, opisu, ikony lub podglądu, aby uniknąć niepotrzebnych obciążeń zestawu zasobów podczas odnajdywania szablonu. Zamiast tego można użyć zlokalizowanych manifestów, aby utworzyć wpis szablonu dla każdego z nich, który używa zlokalizowanych nazw lub właściwości.

- Jeśli dodasz szablony jako elementy plików, generowanie manifestu może nie dać oczekiwanych wyników. W takim przypadku należy dodać ręcznie wygenerowany manifest do projektu VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Zmiany plików w szablonach projektów i elementów
Pokazujemy punkty różnic między wersjami plików szablonu Visual Studio 2015 i Visual Studio 2017, dzięki czemu można poprawnie tworzyć nowe pliki.

 Oto domyślny plik vstemplate projektu utworzony przez program Visual Studio 2015:

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

 Oto plik vstman (można go znaleźć w katalogu manifestu projektu VSIX), który został wynikły z ponownego skompilowania projektu VSIX:

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

 Informacje udostępniane przez [element TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) pozostają takie same. Element **\<VSTemplateContainer>** wskazuje plik vstemplate skojarzonego szablonu.

 Oto plik vstemplate elementu domyślnego utworzony przez program Visual Studio 2015:

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

 Oto plik vstman (można go znaleźć w katalogu manifestu projektu VSIX), który został wynikły z ponownego skompilowania projektu VSIX:

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

 Informacje dostarczone przez **\<TemplateData>** element pozostają takie same. Element **\<VSTemplateContainer>** wskazuje plik vstemplate skojarzonego szablonu

 Aby uzyskać więcej informacji na temat różnych elementów pliku vstman, zobacz [Visual Studio manifestu szablonu .](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Uaktualnienia rozszerzeń zainstalowanych z .MSI

Niektóre rozszerzenia oparte na pliku MSI wdrażają szablony w typowych lokalizacjach szablonów, takich jak następujące katalogi:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<Project/ItemTemplates\>**

Jeśli rozszerzenie wykonuje wdrożenie oparte na pliku MSI, należy wygenerować manifest szablonu ręcznie i upewnić się, że jest uwzględniony w konfiguracji rozszerzenia. Porównaj przykłady pliku .vstman wymienione powyżej i odwołanie [Visual Studio manifestu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).

Utwórz oddzielne manifesty dla szablonów projektów i elementów i powinny one wskazać główny katalog szablonów, jak określono powyżej. Utwórz jeden manifest dla każdego rozszerzenia i jego danych regionalnych.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z odnajdywaniem szablonów](troubleshooting-template-discovery.md)
- [Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)
