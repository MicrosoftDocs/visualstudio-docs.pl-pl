---
title: Uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: d375dfc4a53015f57546f7cbfcc8b940fa81bd0b
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559758"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017

Począwszy od programu Visual Studio 2017, Visual Studio umożliwia odnalezienie szablonów projektów i elementów, zainstalowanych przez msi lub plikiem typu .vsix w inny sposób do poprzednich wersji programu Visual Studio. Jeśli jesteś właścicielem rozszerzenia, które używają niestandardowego projektu lub szablonów elementów, musisz zaktualizować swoje rozszerzenia. W tym artykule opisano, co należy zrobić.

Ta zmiana dotyczy tylko programu Visual Studio 2017. Nie ma wpływu na poprzednie wersje programu Visual Studio.

Jeśli chcesz utworzyć szablon projektu lub elementu jako część rozszerzenia VSIX, zobacz [Tworzenie niestandardowych szablonów projektów i elementów](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Szablon skanowania

W poprzednich wersjach programu Visual Studio **devenv/Setup** lub **devenv/installvstemplates** skanowania dysku lokalnym, aby znaleźć szablonów projektów i elementów. Począwszy od programu Visual Studio 2017, skanowanie jest wykonywane tylko w przypadku lokalizacji poziomie użytkownika. Domyślna lokalizacja poziom użytkownika **%USERPROFILE%\Documents\\< wersja programu Visual Studio\>\Templates\\** . Ta lokalizacja jest używana dla szablonów generowane przez **projektu** > **Eksportuj szablony...**  polecenia, jeśli **automatycznie zaimportuj szablon do programu Visual Studio** opcja jest zaznaczona w kreatorze.

Do innych lokalizacji (niezwiązanych z użytkownikiem) musi zawierać plik manifest(.vstman), który określa lokalizację i innych parametrów szablonu. W pliku vstman jest generowany wraz z pliku .vstemplate, używany do szablonów. Po zainstalowaniu rozszerzenia za pomocą plikiem typu .vsix, można to zrobić przez kompilację rozszerzenia programu Visual Studio 2017. Ale jeśli używasz pliku .msi, musisz wprowadzić zmiany ręcznie. Aby uzyskać listę co należy zrobić, aby wprowadzić te zmiany, zobacz **uaktualnienia zainstalowane za pomocą rozszerzenia. MSI** dalej na tej stronie.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Jak zaktualizować rozszerzenia VSIX przy użyciu projektu lub szablonów elementów

1. Otwórz rozwiązanie w programie Visual Studio 2017. Użytkownik jest proszony o uaktualnienie kodu. Kliknij przycisk **OK**.

2. Po zakończeniu uaktualniania, konieczne może być zmiana wersji docelowej instalacji. W projekcie VSIX, otwórz plik source.extension.vsixmanifest, a następnie wybierz **Instaluj obiekty docelowe** kartę. Jeśli **zakres wersji** pole jest **[14.0]** , kliknij przycisk **Edytuj** i zmień go na obejmują program Visual Studio 2017. Na przykład można ustawić go **[14.0,15.0]** instalowania rozszerzenia do programu Visual Studio 2015 lub Visual Studio 2017 lub **[15.0]** go zainstalować, po prostu Visual Studio 2017.

3. Należy ponownie skompilować kod.

4. Zamknij program Visual Studio.

5. Zainstalować VSIX.

6. Aktualizację można sprawdzić, wykonując następujące czynności:

    1. Skanowania zmian plików jest aktywowany przez następujący klucz rejestru:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Po dodaniu klucza uruchomienia **devenv/installvstemplates**.

    3. Otwórz ponownie program Visual Studio. Szablon powinien znajdować się w oczekiwanej lokalizacji.

    > [!NOTE]
    > Szablony projektów Visual Studio Extensibility nie są dostępne, gdy klucz rejestru jest obecny. Należy usunąć klucz rejestru (i ponownie uruchom **devenv/installvstemplates**) z nich korzystać.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Inne zalecenia dotyczące wdrażania szablonów projektów i elementów

- Należy unikać używania plików zip szablonu. Pliki z rozszerzeniem zip szablonu, które pliki muszą mieć bez kompresji w celu pobrania zasobów i zawartości, więc będą one costlier do użycia. Zamiast tego należy wdrożyć szablonów projektów i elementów jako pojedyncze pliki, w ramach własnego katalogu w celu przyspieszenia inicjowanie szablonu. Rozszerzenia VSIX dla zadania kompilacji zestawu SDK zostanie automatycznie Rozpakuj dowolnego zip szablonu podczas tworzenia pliku VSIX.

- Należy unikać wpisy identyfikatorów pakietu/zasobów dla szablonu nazwę, opis, ikona lub aby uniknąć niepotrzebnych zasobów załadowań zestawów podczas odnajdywania szablonów w wersji zapoznawczej. Zamiast tego można użyć zlokalizowane manifesty można utworzyć wpisu szablonu dla poszczególnych ustawień regionalnych, który używa właściwości lub zlokalizowanych nazw.

- Jeśli w tym szablony jako elementy pliku generowania manifestu może nie dać oczekiwanych wyników. W takim przypadku należy dodać ręcznie wygenerowanego manifestu do projektu VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Zmiany plików szablonów projektów i elementów
Pokazujemy punkty różnica między Visual Studio 2015 i Visual Studio 2017 w wersji plików szablonów, aby mogli tworzyć nowe pliki poprawnie.

 W tym miejscu jest to domyślny plik .vstemplate projekt utworzony przez program Visual Studio 2015:

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

 Oto pliku vstman (możesz go znaleźć w katalogu manifestu projekt VSIX), który jest wynikiem ponownie skompilować projekt VSIX:

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

 Informacje dostarczone przez [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elementu pozostają bez zmian. **\<VSTemplateContainer >** elementu wskazuje plik .vstemplate dla skojarzonego szablonu.

 W tym miejscu jest to domyślny plik .vstemplate elementu utworzone przez program Visual Studio 2015:

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

 Oto pliku vstman (możesz go znaleźć w katalogu manifestu projekt VSIX), który jest wynikiem ponownie skompilować projekt VSIX:

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

 Informacje dostarczone przez  **\<TemplateData >** elementu pozostają bez zmian. **\<VSTemplateContainer >** elementu wskazuje plik .vstemplate dla skojarzonego szablonu

 Aby uzyskać więcej informacji na temat różnych elementów pliku vstman zobacz [Visual Studio Manifest odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Aktualizacje dla rozszerzeń zainstalowany za pomocą. TOŻSAMOŚCI USŁUGI ZARZĄDZANEJ

Niektóre rozszerzenia opartym na MSI wdrażania szablonów typowe lokalizacje szablonu, takie jak następujące katalogi:

- **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\\< ProjectTemplates/elementów\>**

- **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< Project/elementów\>**

Rozszerzenie wykonuje wdrożenie oparte na MSI, musisz ręcznie wygenerować manifest szablonu i upewnij się, że jest ona objęta Instalator rozszerzenia. Porównaj przykłady vstman wymienionych powyżej i [Visual Studio Manifest odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).

Utwórz oddzielne manifesty dla szablonów projektów i elementów, a powinien wskazywać szablonu katalog główny jak określono powyżej. Utwórz jeden manifest rozszerzenia i ustawień regionalnych.

## <a name="see-also"></a>Zobacz także

- [Rozwiązywanie problemów z odnajdywania szablonów](troubleshooting-template-discovery.md)
- [Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)
