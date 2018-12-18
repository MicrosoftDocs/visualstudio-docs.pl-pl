---
title: Uaktualnianie niestandardowe szablony projektów i elementów dla programu Visual Studio 2017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af60281e7211e7b16e86200c02aef791d26da274
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143481"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Uaktualnianie niestandardowe szablony projektów i elementów dla programu Visual Studio 2017 r.

Począwszy od programu Visual Studio 2017 Visual Studio umożliwia odnalezienie szablonów projektów i elementów, które zostały zainstalowane przez .vsix lub pliku .msi w inny sposób w poprzednich wersjach programu Visual Studio. Jeśli jesteś właścicielem rozszerzenia używające niestandardowych projektu lub szablony elementów, należy zaktualizować rozszerzenia. W tym temacie wyjaśniono, co należy zrobić.

Ta zmiana wpływa tylko 2017 programu Visual Studio. Nie ma ona wpływu na poprzednie wersje programu Visual Studio.

Jeśli chcesz utworzyć szablon projektu lub elementu w ramach rozszerzenia VSIX, zobacz [Tworzenie niestandardowych Project and Item Templates](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Szablon skanowania

W poprzednich wersjach programu Visual Studio **devenv/Setup** lub **devenv/installvstemplates** skanowania dysku lokalnym, aby znaleźć szablonów projektów i elementów. Począwszy od programu Visual Studio 2017 skanowanie jest wykonywane tylko dla lokalizacji na poziomie użytkownika. Domyślna lokalizacja na poziomie użytkownika **%USERPROFILE%\Documents\\< wersji programu Visual Studio\>\Templates\\**. Ta lokalizacja jest używana dla szablonów generowane przez **projektu** > **Eksportuj szablony...**  polecenia, jeśli **automatycznie zaimportuj szablon do programu Visual Studio** kreatora wybrano opcję.

Do innych lokalizacji (niezwiązanych z użytkownikiem) musi zawierać plik manifest(.vstman), który określa lokalizację i innych parametrów szablonu. Plik .vstman jest generowany wraz z pliku .vstemplate używane dla szablonów. Po zainstalowaniu rozszerzenia przy użyciu typu .vsix, można to zrobić przez kompilację rozszerzenie w Visual Studio 2017 r. Jednak użycie pliku .msi, musisz ręcznie wprowadzić zmiany. Aby uzyskać listę co należy zrobić, aby wprowadzić te zmiany, zobacz **uaktualnienia z zainstalowane rozszerzenia. MSI** dalszej części tego tematu.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Jak zaktualizować rozszerzenie VSIX z projektu lub szablony elementu  

1.  Otwórz rozwiązanie w Visual Studio 2017 r. Użytkownik jest proszony o uaktualnienie kodu. Kliknij przycisk **OK**.  
  
2.  Po zakończeniu uaktualniania, może być konieczna zmiana wersji docelowej instalacji. W projekcie VSIX, otwórz plik Source.Extension.vsixmanifest,a i wybierz **zainstalować obiekty docelowe** kartę. Jeśli **zakres wersji** pole jest **[14.0]**, kliknij przycisk **Edytuj** i zmień, aby uwzględnić Visual Studio 2017 r. Na przykład można ustawić go **[14.0,15.0]** można zainstalować rozszerzenia programu Visual Studio 2015 lub Visual Studio 2017 lub do **[15.0]** Aby zainstalować ją po prostu 2017 programu Visual Studio.  
  
3.  Skompiluj ponownie kod.  
  
4.  Zamknij program Visual Studio.  
  
5.  Zainstalować pliku VSIX.  
  
6.  Aktualizację można sprawdzić, wykonując następujące czynności:  
  
    1.  Skanowanie zmiany pliku jest aktywowany przez następujący klucz rejestru:  
  
         **Polecenie reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Po dodaniu klucza uruchomienia **devenv/installvstemplates**.  
  
    3.  Otwórz ponownie program Visual Studio. Szablon powinien znajdować się w oczekiwanej lokalizacji.  
  
    > [!NOTE]
    >  Szablony projektu Visual Studio Extensibility nie są dostępne, jeśli obecna jest wartość klucza rejestru. Należy usunąć ten klucz rejestru (i ponownie uruchom **devenv/installvstemplates**) z nich korzystać.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Inne zalecenia dotyczące wdrażania szablony projektów i elementów  
  
-   Unikaj używania plików zip szablonu. ZIP szablon, którego pliki muszą mieć nieskompresowanych w celu pobrania zasobów i zawartości, więc będą one costlier do użycia. Zamiast tego należy wdrożyć szablonów projektów i elementów jako pojedyncze pliki, w obszarze ich własnego katalogu w celu przyspieszenia inicjowania szablonu. Dla rozszerzenia VSIX zadania kompilacji zestawu SDK będą automatycznie Rozpakuj dowolnego zip szablonu podczas tworzenia pliku VSIX.  
  
-   Unikaj używania wpisy Identyfikator zasobu/pakietu do nazwy szablonu, opis, ikona lub Podgląd, aby uniknąć niepotrzebnych zasobów zestawu ładuje podczas odnajdowania szablonu. Zamiast tego można zlokalizowanych manifestów utworzyć wpis szablonu dla każdego ustawienia regionalne, które używa zlokalizowanych nazw lub właściwości.  
  
-   Jeśli w tym szablony jako elementy pliku Generowanie manifestu może nie zapewniają oczekiwanych rezultatów. W takim przypadku należy dodać ręcznie wygenerowane manifestu do projektu VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Zmiany pliku szablony projektów i elementów  
Zostanie przedstawiony punkty różnica między Visual Studio 2015 i wersji programu Visual Studio 2017 plików szablonów, dzięki czemu można tworzyć nowe pliki poprawnie.  
  
 Oto domyślny plik .vstemplate projektu utworzonych przez program Visual Studio 2015:  
  
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
  
 Oto plik .vstman (znajduje się on w katalogu manifestu VSIX projektu), który jest wynikiem odbudowywania projektu VSIX:  
  
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
  
 Informacje dostarczane przez [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element pozostaje bez zmian.  **\<VSTemplateContainer >** element wskazuje plik .vstemplate szablonu skojarzone.  
  
 Oto domyślny plik .vstemplate elementu utworzone w programie Visual Studio 2015:  
  
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
  
 Oto plik .vstman (znajduje się on w katalogu manifestu VSIX projektu), który jest wynikiem odbudowywania projektu VSIX:  
  
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
  
 Informacje dostarczane przez  **\<TemplateData >** element pozostaje bez zmian.  **\<VSTemplateContainer >** element wskazuje plik .vstemplate skojarzone szablonu  
  
 Aby uzyskać więcej informacji na temat różnych elementów pliku .vstman zobacz [programu Visual Studio manifestu odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Z zainstalowanym uaktualnień dla rozszerzeń. MSI

Niektóre rozszerzenia na podstawie MSI wdrażanie szablonów do wspólnej lokalizacji szablonu takie jak następujące:

- **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\\< ProjectTemplates/elementów >**

- **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< Project/elementów >**

Rozszerzenie wykonuje wdrażanie na podstawie MSI, musisz ręcznie wygenerować manifest szablonu i upewnij się, że jest uwzględnione w konfiguracji rozszerzenia. Porównaj powyższe przykłady .vstman i [programu Visual Studio manifestu odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).

Należy utworzyć oddzielny manifesty dla szablonów projektów i elementów i powinny wskazywać szablonu katalog główny określonych powyżej. Utwórz jeden manifest według rozszerzenia i ustawień regionalnych.

## <a name="see-also"></a>Zobacz także

[Rozwiązywanie problemów z odnajdywania szablonu](troubleshooting-template-discovery.md)  
[Tworzenie niestandardowych szablonów projektów i elementów](creating-custom-project-and-item-templates.md)