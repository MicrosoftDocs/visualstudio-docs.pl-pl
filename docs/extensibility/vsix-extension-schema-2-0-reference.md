---
title: Odwołanie do schematu rozszerzenia VSIX 2,0 | Microsoft Docs
description: Schemat rozszerzenia VSIX 2,0 definiuje format pliku manifestu wdrożenia VSIX, który opisuje zawartość pakietu VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d1b94c7b2cacb7ad78031721156bdd90cb666c4f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062294"
---
# <a name="vsix-extension-schema-20-reference"></a>Dokumentacja schematu rozszerzenia VSIX 2,0
Plik manifestu wdrożenia VSIX opisuje zawartość pakietu VSIX. Format pliku podlega schematowi. Wersja 2,0 tego schematu obsługuje Dodawanie niestandardowych typów i atrybutów.  Schemat manifestu jest rozszerzalny. Moduł ładujący manifest ignoruje elementy XML i atrybuty, które nie są zrozumiałe.

> [!IMPORTANT]
> Program Visual Studio 2015 może ładować pliki VSIX w formatach programu Visual Studio 2010, Visual Studio 2012 lub Visual Studio 2013.

## <a name="package-manifest-schema"></a>Schemat manifestu pakietu
 Głównym elementem pliku XML manifestu jest `<PackageManifest>` . Ma jeden atrybut `Version` , który jest wersją formatu manifestu. W przypadku wprowadzenia istotnych zmian w formacie format wersji zostanie zmieniony. W tym artykule opisano format manifestu w wersji 2,0, który jest określony w manifeście przez ustawienie `Version` atrybutu na wartość Version = "2.0".

### <a name="packagemanifest-element"></a>PackageManifest, element
 W `<PackageManifest>` elemencie głównym można użyć następujących elementów:

- `<Metadata>` — Metadane i informacje reklamowe dotyczące samego pakietu. `Metadata`W manifeście dozwolony jest tylko jeden element.

- `<Installation>` — W tej sekcji opisano sposób instalowania tego pakietu rozszerzenia, w tym jednostki SKU aplikacji, do których można się zainstalować. `Installation`W manifeście dozwolony jest tylko jeden element. Manifest musi mieć `Installation` element lub ten pakiet nie zostanie zainstalowany do żadnej jednostki SKU.

- `<Dependencies>` — Opcjonalna lista zależności dla tego pakietu została zdefiniowana w tym miejscu.

- `<Assets>` — Ta sekcja zawiera wszystkie zasoby zawarte w ramach tego pakietu. Bez tej sekcji ten pakiet nie będzie omawiał żadnej zawartości.

- `<AnyElement>*` -Schemat manifestu jest wystarczająco elastyczny, aby można było zezwolić na inne elementy. Wszystkie elementy podrzędne, które nie są rozpoznawane przez moduł ładujący manifest, są ujawniane w interfejsie API Menedżera rozszerzeń jako dodatkowe obiekty XmlElement. Przy użyciu tych elementów podrzędnych rozszerzenia VSIX mogą definiować dodatkowe dane w pliku manifestu, który kod uruchomiony w programie Visual Studio może uzyskać dostęp w czasie wykonywania. Zobacz [Microsoft. VisualStudio. ExtensionManager. IExtension. AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Element metadanych
 Ta sekcja zawiera metadane dotyczące pakietu, jego tożsamości i informacji reklamowych. `<Metadata>` zawiera następujące elementy:

- `<Identity>` -Definiuje informacje identyfikacyjne dla tego pakietu i zawiera następujące atrybuty:

  - `Id` -Ten atrybut musi być unikatowym IDENTYFIKATORem pakietu wybranego przez jego autora. Nazwa powinna być kwalifikowana w taki sam sposób, w jaki typy CLR mają przestrzeń nazw: Company.Product.Feature.Name. `Id`Atrybut jest ograniczony do 100 znaków.

  - `Version` -Definiuje wersję tego pakietu i jego zawartość. Ten atrybut jest zgodny z formatem wersji zestawu CLR: główna. pomocnicza. kompilacja. poprawka (1.2.40308.00). Pakiet o wyższym numerze wersji jest uznawany za aktualizacje pakietu i można go zainstalować za pomocą istniejącej zainstalowanej wersji.

  - `Language` -Ten atrybut jest domyślnym językiem pakietu i odpowiada danych tekstowych w tym manifeście. Ten atrybut jest zgodny z Konwencją kodu locale języka CLR dla zestawów zasobów, na przykład: en-us, EN, fr-fr. Można określić, `neutral` Aby zadeklarować niezależne od języka rozszerzenie, które będzie uruchamiane w dowolnej wersji programu Visual Studio. Wartość domyślna to `neutral`.

  - `Publisher` — Ten atrybut służy do identyfikowania wydawcy tego pakietu, czyli nazwy firmy lub osoby. `Publisher`Atrybut jest ograniczony do 100 znaków.

- `<DisplayName>` -Ten element określa przyjazną dla użytkownika nazwę pakietu, która jest wyświetlana w interfejsie użytkownika Menedżera rozszerzeń. `DisplayName`Zawartość jest ograniczona do 50 znaków.

- `<Description>` -Ten opcjonalny element to krótki opis pakietu i jego zawartość, która jest wyświetlana w interfejsie użytkownika Menedżera rozszerzeń. `Description`Zawartość może zawierać dowolny tekst, ale jest ograniczona do 1000 znaków.

- `<MoreInfo>` -Ten opcjonalny element to adres URL strony online, która zawiera pełen opis tego pakietu. Protokół musi być określony jako http.

- `<License>` -Ten opcjonalny element jest ścieżką względną do pliku licencji (. txt,. rtf) zawartego w pakiecie.

- `<ReleaseNotes>` -Ten opcjonalny element to ścieżka względna do pliku informacji o wersji znajdującego się w pakiecie (. txt,. rtf) lub w innym adresie URL do witryny sieci Web, w której są wyświetlane informacje o wersji.

- `<Icon>` -Ten opcjonalny element jest ścieżką względną do pliku obrazu (PNG, BMP, JPEG, ICO) zawartego w pakiecie. Obraz ikony powinien mieć 32x32 pikseli (lub zostanie zmniejszony do tego rozmiaru) i pojawi się w interfejsie użytkownika ListView. Jeśli żaden `Icon` element nie jest określony, interfejs użytkownika używa domyślnego.

- `<PreviewImage>` -Ten opcjonalny element jest ścieżką względną do pliku obrazu (PNG, BMP, JPEG) zawartego w pakiecie. Obraz podglądu powinien mieć 200x200 pikseli i być wyświetlany w interfejsie użytkownika szczegółów. Jeśli żaden `PreviewImage` element nie jest określony, interfejs użytkownika używa domyślnego.

- `<Tags>` -Ten opcjonalny element Wyświetla listę dodatkowych znaczników tekstu rozdzielonych średnikami, które są używane na potrzeby wskazówek wyszukiwania. `Tags`Element jest ograniczony do 100 znaków.

- `<GettingStartedGuide>` -Ten opcjonalny element to ścieżka względna do pliku HTML lub adres URL witryny sieci Web, która zawiera informacje na temat używania rozszerzenia lub zawartości w ramach tego pakietu. Ten przewodnik jest uruchamiany w ramach instalacji.

- `<AnyElement>*` -Schemat manifestu jest wystarczająco elastyczny, aby można było zezwolić na inne elementy. Wszystkie elementy podrzędne, które nie są rozpoznawane przez moduł ładujący manifest, są ujawniane jako lista obiektów XmlElement. Przy użyciu tych elementów podrzędnych rozszerzenia VSIX mogą definiować dodatkowe dane w pliku manifestu i wyliczać je w czasie wykonywania.

### <a name="installation-element"></a>Element instalacji
 W tej sekcji opisano sposób instalacji tego pakietu oraz jednostki SKU aplikacji, do których można się zainstalować. Ta sekcja zawiera następujące atrybuty:

- `Experimental` -Ustaw ten atrybut na true, jeśli masz rozszerzenie, które jest obecnie zainstalowane dla wszystkich użytkowników, ale jest tworzona zaktualizowana wersja na tym samym komputerze. Na przykład jeśli zainstalowano rozszerzenie 1,0 dla wszystkich użytkowników, ale chcesz debugować rozszerzenie 2,0 na tym samym komputerze, ustaw wartość eksperymentalną = "true". Ten atrybut jest dostępny w programie Visual Studio 2015 Update 1 lub nowszym.

- `Scope` -Ten atrybut może przyjmować wartość "Global" lub "ProductExtension":

  - "Globalny" określa, że instalacja nie jest objęta zakresem określonej jednostki SKU. Na przykład ta wartość jest używana podczas instalowania rozszerzenia SDK.

  - "ProductExtension" określa, że zainstalowano tradycyjne rozszerzenie VSIX (wersja 1,0) w zakresie poszczególnych jednostek SKU programu Visual Studio. Jest to wartość domyślna.

- `AllUsers` -Ten opcjonalny atrybut określa, czy ten pakiet zostanie zainstalowany dla wszystkich użytkowników. Domyślnie ten atrybut ma wartość false, co oznacza, że pakiet jest na użytkownika. (W przypadku ustawienia tej wartości na wartość true użytkownik instalujący musi podnieść poziom uprawnień administracyjnych, aby zainstalować wynikowy VSIX.

- `InstalledByMsi` -Ten opcjonalny atrybut określa, czy ten pakiet jest instalowany przez plik MSI. Pakiety zainstalowane przez plik MSI są instalowane i zarządzane przez Instalatora MSI (programy i funkcje), a nie przez Menedżera rozszerzeń programu Visual Studio.  Domyślnie ten atrybut ma wartość false, co oznacza, że pakiet nie jest instalowany przez plik MSI.

- `SystemComponent` -Ten opcjonalny atrybut określa, czy ten pakiet powinien być uważany za składnik systemowy. Składniki systemowe nie są wyświetlane w interfejsie użytkownika Menedżera rozszerzeń i nie można ich zaktualizować. Domyślnie ten atrybut ma wartość false, co oznacza, że pakiet nie jest składnikiem systemowym.

- `AnyAttribute*` - `Installation` Element akceptuje otwarty zestaw atrybutów, które będą uwidaczniane w czasie wykonywania jako słownik par nazwa-wartość.

- `<InstallationTarget>` — Ten element określa lokalizację, w której Instalator VSIX instaluje pakiet. Jeśli wartość `Scope` atrybutu jest "ProductExtension", pakiet musi być celem jednostki SKU, która zainstalowała plik manifestu w ramach jego zawartości, aby anonsować jego dostępność do rozszerzeń. `<InstallationTarget>`Element ma następujące atrybuty, gdy `Scope` atrybut ma wartość jawną lub domyślną "ProductExtension":

  - `Id` — Ten atrybut identyfikuje pakiet.  Ten atrybut jest zgodny z Konwencją przestrzeni nazw: Company.Product.Feature.Name. `Id`Atrybut może zawierać tylko znaki alfanumeryczne i jest ograniczony do 100 znaków. Oczekiwane wartości:

    - Microsoft. VisualStudio. IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft. VisualStudio. Premium

    - Microsoft. VisualStudio. Ultimate

    - Microsoft. VisualStudio. VWDExpress

    - Microsoft. VisualStudio. VPDExpress

    - Microsoft. VisualStudio. VSWinExpress

    - Microsoft. VisualStudio. VSLS

    - My.Shell.App

  - `Version` -Ten atrybut określa zakres wersji o minimalnej i maksymalnej obsługiwanej wersji tej jednostki SKU. Pakiet może szczegółowo określać wersje jednostek SKU obsługiwanych przez program. Notacja zakresu wersji to [10,0-11,0], gdzie

    - [-minimalna wersja włącznie.

    - ] — Maksymalna wersja włącznie.

    - (— wersja minimalna.

    - ) — Maksymalna wersja na wyłączność.

    - Jedna wersja # — tylko określona wersja.

    > [!IMPORTANT]
    > W programie Visual Studio 2012 wprowadzono wersję 2,0 schematu VSIX. Aby użyć tego schematu, musisz mieć zainstalowany program Visual Studio 2012 lub nowszy i korzystać z VSIXInstaller.exe, który jest częścią tego produktu. Możesz kierować do starszych wersji programu Visual Studio, używając programu Visual Studio 2012 lub nowszego Instalator VSIX, ale tylko przy użyciu nowszych wersji Instalatora.

    Numery wersji programu Visual Studio 2017 można znaleźć pod [numerem kompilacji programu Visual Studio i datami wydania](../install/visual-studio-build-numbers-and-release-dates.md).

    Podczas wyrażania wersji programu Visual Studio 2017 wersja pomocnicza powinna zawsze mieć **wartość 0**. Na przykład program Visual Studio 2017 w wersji 15.3.26730.0 powinien być wyrażony jako [15.0.26730.0, 16.0). Jest to wymagane tylko w przypadku programu Visual Studio 2017 i nowszych wersji.

  - `AnyAttribute*` - `<InstallationTarget>` Element zezwala na otwarty zestaw atrybutów, które są ujawniane w czasie wykonywania jako słownik par nazwa-wartość.

### <a name="dependencies-element"></a>Element zależności
 Ten element zawiera listę zależności zadeklarowanych przez ten pakiet. Jeśli zostaną określone jakiekolwiek zależności, te pakiety (identyfikowane przez nich `Id` ) muszą zostać wcześniej zainstalowane.

- `<Dependency>` element — ten element podrzędny ma następujące atrybuty:

  - `Id` -Ten atrybut musi być unikatowym IDENTYFIKATORem pakietu zależnego. Ta wartość tożsamości musi być zgodna z `<Metadata><Identity>Id` atrybutem pakietu, od którego jest zależny ten pakiet. Ten `Id` atrybut jest zgodny z Konwencją przestrzeni nazw: Company.Product.feature.Name. Atrybut może zawierać tylko znaki alfanumeryczne i jest ograniczony do 100 znaków.

  - `Version` -Ten atrybut określa zakres wersji o minimalnej i maksymalnej obsługiwanej wersji tej jednostki SKU. Pakiet może szczegółowo określać wersje jednostek SKU obsługiwanych przez program. Notacja zakresu wersji to [12,0, 13,0], gdzie:

    - [-minimalna wersja włącznie.

    - ] — Maksymalna wersja włącznie.

    - (— wersja minimalna.

    - ) — Maksymalna wersja na wyłączność.

    - Jedna wersja # — tylko określona wersja.

  - `DisplayName` -Ten atrybut jest nazwą wyświetlaną pakietu zależnego, który jest używany w elementach interfejsu użytkownika, takich jak okna dialogowe i komunikaty o błędach. Ten atrybut jest opcjonalny, o ile pakiet zależny nie został zainstalowany przez plik MSI.

  - `Location` -Ten opcjonalny atrybut określa ścieżkę względną w tym VSIX do zagnieżdżonego pakietu VSIX lub adres URL do lokalizacji pobierania dla zależności. Ten atrybut jest używany do ułatwienia użytkownikom lokalizowania wstępnie wymaganego pakietu.

  - `AnyAttribute*` - `Dependency` Element akceptuje otwarty zestaw atrybutów, które będą uwidaczniane w czasie wykonywania jako słownik par nazwa-wartość.

### <a name="assets-element"></a>Element Assets
 Ten element zawiera listę `<Asset>` tagów dla każdego rozszerzenia lub elementu zawartości, które są objęte tym pakietem.

- `<Asset>` -Ten element zawiera następujące atrybuty i elementy:

  - `Type` -Typ rozszerzenia lub zawartości reprezentowanej przez ten element. Każdy `<Asset>` element musi mieć pojedynczą `Type` , ale wiele `<Asset>` elementów może być taka sama `Type` . Ten atrybut powinien być reprezentowany jako w pełni kwalifikowana nazwa, zgodnie z konwencjami przestrzeni nazw. Znane typy to:

    1. Microsoft. VisualStudio. pakietu VSPackage

    2. Microsoft. VisualStudio. MefComponent

    3. Microsoft. VisualStudio. ToolboxControl

    4. Microsoft. VisualStudio. Samples

    5. Microsoft. VisualStudio. ProjectTemplate

    6. Microsoft. VisualStudio. ItemTemplate

    7. Microsoft. VisualStudio. Assembly

       Możesz utworzyć własne typy i nadać im unikatowe nazwy. W czasie wykonywania w programie Visual Studio kod może wyliczyć i uzyskać dostęp do tych typów niestandardowych za pomocą interfejsu API Menedżera rozszerzeń.

  - `Path` -ścieżka względna do pliku lub folderu w pakiecie, który zawiera element zawartości.

  - `TargetVersion` — zakres wersji, do którego odnosi się dany zasób. Służy do wysyłania wielu wersji zasobów do różnych wersji programu Visual Studio. Wymaga programu Visual Studio w wersji 2017,3 lub nowszej.

  - `AnyAttribute*` -Otwarty zestaw atrybutów, które są ujawniane w czasie wykonywania jako słownik par nazwa-wartość.

    `<AnyElement>*` -Każda zawartość strukturalna jest dozwolona między `<Asset>` tagiem BEGIN i End. Wszystkie elementy są uwidocznione jako lista obiektów XmlElement. Rozszerzenia VSIX mogą definiować metadane specyficzne dla typu strukturalnego w pliku manifestu i wyliczać je w czasie wykonywania.

### <a name="sample-manifest"></a>Przykładowy manifest

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Zobacz też

- [Wyślij rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
