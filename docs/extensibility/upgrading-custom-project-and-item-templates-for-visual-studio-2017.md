---
title: Uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698857"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Uaktualnianie szablonów niestandardowych projektów i elementów dla programu Visual Studio 2017

Począwszy od programu Visual Studio 2017 program Visual Studio odnajduje szablony projektów i elementów, które zostały zainstalowane przez .vsix lub .msi w inny sposób niż poprzednie wersje programu Visual Studio. Jeśli jesteś właścicielem rozszerzeń, które używają szablonów niestandardowych projektów lub elementów, należy zaktualizować rozszerzenia. W tym artykule wyjaśniono, co należy zrobić.

Ta zmiana dotyczy tylko programu Visual Studio 2017. Nie ma to wpływu na poprzednie wersje programu Visual Studio.

Aby utworzyć szablon projektu lub elementu jako część rozszerzenia VSIX, zobacz [Tworzenie szablonów projektów niestandardowych i elementów](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Skanowanie szablonów

W poprzednich wersjach programu Visual Studio **devenv /setup** lub **devenv /installvstemplates** skanował dysk lokalny w celu znalezienia szablonów projektów i elementów. Począwszy od programu Visual Studio 2017 skanowanie jest wykonywane tylko dla lokalizacji na poziomie użytkownika. Domyślną lokalizacją na poziomie użytkownika jest **\\ %USERPROFILE%\Documents\><\\wersja programu Visual Studio \Templates**. Ta lokalizacja jest używana dla szablonów generowanych przez polecenie**Szablony eksportu** **projektu...** > jeśli w kreatorze jest zaznaczona opcja **Automatycznie importuj szablon do programu Visual Studio.**

W przypadku innych lokalizacji (nienauczalnych) należy dołączyć plik manifestu(vstman), który określa lokalizację i inne cechy szablonu. Plik .vstman jest generowany wraz z plikiem vstemplate używanym do szablonów. Jeśli rozszerzenie zostanie zainstalowane przy użyciu programu .vsix, można to osiągnąć, ponownie kompilowanie rozszerzenia w programie Visual Studio 2017. Ale jeśli używasz .msi, musisz wprowadzić zmiany ręcznie. Aby uzyskać listę rzeczy, które należy zrobić, aby wprowadzić te zmiany, zobacz **Uaktualnienia dla rozszerzeń zainstalowanych z programem . MSI** później na tej stronie.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Jak zaktualizować rozszerzenie VSIX za pomocą szablonów projektów lub elementów

1. Otwórz rozwiązanie w programie Visual Studio 2017. Zostaniesz poproszony o uaktualnienie kodu. Kliknij przycisk **OK**.

2. Po zakończeniu uaktualniania może być konieczna zmiana wersji obiektu docelowego instalacji. W projekcie VSIX otwórz plik source.extension.vsixmanifest i wybierz kartę **Zainstaluj obiekty docelowe.** Jeśli pole **Zakres wersji** to **[14.0]** kliknij przycisk **Edytuj** i zmień go tak, aby uwzględnił program Visual Studio 2017. Na przykład można ustawić go na **[14.0,15.0],** aby zainstalować rozszerzenie do programu Visual Studio 2015 lub Visual Studio 2017 lub **[15.0],** aby zainstalować je tylko visual studio 2017.

3. Ponownie skompiluj kod.

4. Zamknij program Visual Studio.

5. Zainstaluj VSIX.

6. Aktualizację można przetestować, wykonując następujące czynności:

    1. Zmiana skanowania plików jest aktywowana przez następujący klucz rejestru:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Po dodaniu klucza uruchom **devenv /installvstemplates**.

    3. Otwórz ponownie program Visual Studio. Szablon powinien znajdować się w oczekiwanej lokalizacji.

    > [!NOTE]
    > Szablony projektu rozszerzalności programu Visual Studio nie są dostępne, gdy klucz rejestru jest obecny. Aby z nich korzystać, należy usunąć klucz rejestru (i ponownie **uruchomić devenv /installvstemplates).**

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Inne zalecenia dotyczące wdrażania szablonów projektów i elementów

- Unikaj używania spakowanych plików szablonów. Spakowane pliki szablonów muszą być nieskompresowane, aby pobrać zasoby i zawartość, więc będą one bardziej kosztowne w użyciu. Zamiast tego należy wdrożyć szablony projektów i elementów jako pojedyncze pliki w ich własnym katalogu, aby przyspieszyć inicjowanie szablonów. W przypadku rozszerzeń VSIX zadania kompilacji SDK automatycznie rozpakowują dowolny spakowany szablon podczas tworzenia pliku VSIX.

- Należy unikać używania wpisów identyfikatora pakietu/zasobu dla nazwy szablonu, opisu, ikony lub podglądu, aby uniknąć niepotrzebnych obciążeń zestawu zasobów podczas odnajdywania szablonu. Zamiast tego można użyć zlokalizowanych manifestów, aby utworzyć wpis szablonu dla każdego ustawienia regionalne, który używa zlokalizowanych nazw lub właściwości.

- Jeśli są dołączenie szablonów jako elementy pliku, generowanie manifestu może nie daje oczekiwanych wyników. W takim przypadku należy dodać ręcznie wygenerowany manifest do projektu VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Zmiany plików w szablonach projektów i elementów
Pokazujemy punkty różnicy między visual studio 2015 i Visual Studio 2017 wersje plików szablonów, dzięki czemu można utworzyć nowe pliki poprawnie.

 Oto domyślny plik .vstemplate projektu utworzony przez program Visual Studio 2015:

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

 Oto plik vstman (można go znaleźć w katalogu manifestu projektu VSIX), który powstał w wyniku przebudowy projektu VSIX:

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

 Informacje dostarczone przez [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element pozostaje taka sama. ** \<VsTemplateContainer>** element wskazuje na plik vstemplate dla skojarzonego szablonu.

 Oto domyślny plik elementu .vstemplate utworzony przez program Visual Studio 2015:

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

 Oto plik vstman (można go znaleźć w katalogu manifestu projektu VSIX), który powstał w wyniku przebudowy projektu VSIX:

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

 Informacje dostarczone przez ** \<TemplateData>** element pozostaje taka sama. ** \<Element VSTemplateContainer wskazuje>** plik vstemplate dla skojarzonego szablonu

 Aby uzyskać więcej informacji na temat różnych elementów pliku vstman, zobacz [Odwołanie do schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Uaktualnienia dla rozszerzeń zainstalowanych z . Msi

Niektóre rozszerzenia oparte na msi wdrażają szablony w typowych lokalizacjach szablonów, takich jak następujące katalogi:

- **\<Katalog instalacji programu Visual Studio>\Common7\IDE\\<projecttemplates/ItemTemplates\>**

- **\<Katalog instalacji programu Visual Studio>\Common7\IDE\Extensions\\<ExtensionName\> \\<Project/ItemTemplates\>**

Jeśli rozszerzenie wykonuje wdrożenie oparte na msi, należy ręcznie wygenerować manifest szablonu i upewnić się, że jest on uwzględniony w konfiguracji rozszerzenia. Porównaj wymienione powyżej przykłady vstmana i [odwołanie do schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Tworzenie oddzielnych manifestów dla szablonów projektów i elementów i powinny wskazywać katalog szablonów głównych, jak określono powyżej. Utwórz jeden manifest na rozszerzenie i ustawienia regionalne.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z odnajdywaniem szablonów](troubleshooting-template-discovery.md)
- [Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)
