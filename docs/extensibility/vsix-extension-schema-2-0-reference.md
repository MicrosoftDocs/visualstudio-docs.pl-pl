---
title: VsIX Extension Schema 2.0 Reference | (Schemat rozszerzenia VSIX 2.0 ) Microsoft Docs
description: Schemat rozszerzenia VSIX 2.0 definiuje format pliku manifestu wdrożenia VSIX, który opisuje zawartość pakietu VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66393bbe6383fcc6cae942a3d7e86f1d701a9634
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905244"
---
# <a name="vsix-extension-schema-20-reference"></a>Informacje o schemacie rozszerzenia VSIX 2.0
Plik manifestu wdrożenia VSIX opisuje zawartość pakietu VSIX. Format pliku podlega schematowi. Wersja 2.0 tego schematu obsługuje dodawanie niestandardowych typów i atrybutów.  Schemat manifestu jest rozszerzalny. Program ładujący manifest ignoruje elementy XML i atrybuty, których nie rozumie.

> [!IMPORTANT]
> Visual Studio 2015 można załadować pliki VSIX w formacie Visual Studio 2010, Visual Studio 2012 lub Visual Studio 2013 formatów.

## <a name="package-manifest-schema"></a>Schemat manifestu pakietu
 Element główny pliku XML manifestu to `<PackageManifest>` . Ma ona pojedynczy atrybut `Version` , który jest wersją formatu manifestu. Jeśli w formacie zostaną wprowadzone istotne zmiany, format wersji zostanie zmieniony. W tym artykule opisano format manifestu w wersji 2.0, który jest określony w manifeście przez ustawienie atrybutu na wartość `Version` Version="2.0".

### <a name="packagemanifest-element"></a>PackageManifest, element
 W `<PackageManifest>` elemencie głównym można użyć następujących elementów:

- `<Metadata>` — Metadane i informacje o samym pakiecie. W `Metadata` manifeście dozwolony jest tylko jeden element.

- `<Installation>` — W tej sekcji zdefiniowano sposób instalowania tego pakietu rozszerzenia, w tym jednostki SKU aplikacji, w których można go zainstalować. W `Installation` manifeście dozwolony jest tylko jeden element. Manifest musi mieć element lub ten pakiet nie `Installation` będzie instalowany w żadnej sku.

- `<Dependencies>` — Opcjonalna lista zależności dla tego pakietu jest zdefiniowana tutaj.

- `<Assets>` — Ta sekcja zawiera wszystkie zasoby zawarte w tym pakiecie. Bez tej sekcji ten pakiet nie będzie zawierał żadnej zawartości.

- `<AnyElement>*` — Schemat manifestu jest wystarczająco elastyczny, aby zezwolić na inne elementy. Wszystkie elementy podrzędne, które nie są rozpoznawane przez modułu ładującego manifestu, są udostępniane w interfejsie API menedżera rozszerzeń jako dodatkowe obiekty XmlElement. Przy użyciu tych elementów podrzędnych rozszerzenia VSIX mogą definiować dodatkowe dane w pliku manifestu, do których kod uruchomiony w programie Visual Studio uzyskać dostęp w czasie działania. Zobacz [Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Element metadanych
 Ta sekcja zawiera metadane dotyczące pakietu, jego tożsamości i informacji reklamowych. `<Metadata>` Zawiera następujące elementy:

- `<Identity>` - Definiuje informacje identyfikacyjne dla tego pakietu i zawiera następujące atrybuty:

  - `Id` - Ten atrybut musi być unikatowym identyfikatorem pakietu wybranego przez jego autora. Nazwa powinna być kwalifikowana w taki sam sposób, w jaki typy CLR są przestrzeniami nazw: Company.Product.Feature.Name. Atrybut `Id` jest ograniczony do 100 znaków.

  - `Version` - Definiuje wersję tego pakietu i jego zawartość. Ten atrybut jest zgodny z formatem wersji zestawu CLR: Major.Minor.Build.Revision (1.2.40308.00). Pakiet o wyższym numerze wersji jest traktowany jako aktualizacje pakietu i można go zainstalować za pośrednictwem istniejącej zainstalowanej wersji.

  - `Language` - Ten atrybut jest domyślnym językiem pakietu i odpowiada danych tekstowych w tym manifeście. Ten atrybut jest zgodny z konwencją kodu dla kodów regionalnych CLR dla zestawów zasobów, na przykład: en-us, en, fr-fr. Można określić, `neutral` aby zadeklarować rozszerzenie neutralne dla języka, które będzie uruchamiane w dowolnej wersji Visual Studio. Wartość domyślna to `neutral`.

  - `Publisher` - Ten atrybut identyfikuje wydawcę tego pakietu — nazwę firmy lub nazwę indywidualną. Atrybut `Publisher` jest ograniczony do 100 znaków.

- `<DisplayName>` - Ten element określa przyjazną dla użytkownika nazwę pakietu wyświetlaną w interfejsie użytkownika Menedżera rozszerzeń. Zawartość `DisplayName` jest ograniczona do 50 znaków.

- `<Description>` - Ten opcjonalny element to krótki opis pakietu i jego zawartości, który jest wyświetlany w interfejsie użytkownika Menedżera rozszerzeń. Zawartość może zawierać dowolny tekst, ale może zawierać tylko `Description` 1000 znaków.

- `<MoreInfo>` — Ten opcjonalny element to adres URL strony online, która zawiera pełny opis tego pakietu. Protokół musi być określony jako http.

- `<License>` - Ten opcjonalny element jest ścieżką względną do pliku licencji (.txt, RTF) zawartego w pakiecie.

- `<ReleaseNotes>` — Ten opcjonalny element jest ścieżką względną do pliku informacji o wersji zawartego w pakiecie (.txt, RTF) lub adresem URL witryny sieci Web, która wyświetla informacje o wersji.

- `<Icon>` - Ten opcjonalny element jest ścieżką względną do pliku obrazu (png, bmp, jpeg, ico) zawartego w pakiecie. Obraz ikony powinien mieć rozmiar 32 x 32 piksele (lub będzie mieć ten rozmiar) i powinien zostać wyświetlony w interfejsie użytkownika widoku listy. Jeśli nie `Icon` określono żadnego elementu, interfejs użytkownika używa wartości domyślnej.

- `<PreviewImage>` - Ten opcjonalny element jest ścieżką względną do pliku obrazu (png, bmp, jpeg) zawartego w pakiecie. Obraz podglądu powinien mieć rozmiar 200 x 200 pikseli i powinien być wyświetlany w interfejsie użytkownika szczegółów. Jeśli nie `PreviewImage` określono żadnego elementu, interfejs użytkownika używa wartości domyślnej.

- `<Tags>` - Ten opcjonalny element zawiera listę dodatkowych tagów tekstowych rozdzielonych średnikami, które są używane dla wskazówek wyszukiwania. Element `Tags` jest ograniczony do 100 znaków.

- `<GettingStartedGuide>` - Ten opcjonalny element jest ścieżką względną do pliku HTML lub adresem URL witryny sieci Web, który zawiera informacje o witrynie internetowej dotyczącej sposobu używania rozszerzenia lub zawartości w tym pakiecie. Ten przewodnik jest uruchomiony w ramach instalacji.

- `<AnyElement>*` — Schemat manifestu jest wystarczająco elastyczny, aby zezwolić na inne elementy. Wszystkie elementy podrzędne, które nie są rozpoznawane przez modułu ładującego manifestu, są widoczne jako lista obiektów XmlElement. Przy użyciu tych elementów podrzędnych rozszerzenia VSIX mogą definiować dodatkowe dane w pliku manifestu i wyliczać je w czasie działania.

### <a name="installation-element"></a>Element instalacji
 W tej sekcji zdefiniowano sposób instalowania tego pakietu oraz jednostki SKU aplikacji, w których można go zainstalować. Ta sekcja zawiera następujące atrybuty:

- `Experimental` - Ustaw ten atrybut na wartość true, jeśli masz rozszerzenie, które jest obecnie zainstalowane dla wszystkich użytkowników, ale opracowujesz zaktualizowaną wersję na tym samym komputerze. Jeśli na przykład zainstalowano program MyExtension 1.0 dla wszystkich użytkowników, ale chcesz debugować program MyExtension 2.0 na tym samym komputerze, ustaw wartość Experimental="true". Ten atrybut jest dostępny w wersji Visual Studio 2015 Update 1 i nowszych.

- `Scope` - Ten atrybut może przyjmować wartość "Global" lub "ProductExtension":

  - "Globalne" określa, że instalacja nie jest w zakresie określonej sku. Na przykład ta wartość jest używana podczas instalu zestawu SDK rozszerzenia.

  - "ProductExtension" określa, że jest zainstalowane tradycyjne rozszerzenie VSIX (wersja 1.0) o zakresie poszczególnych Visual Studio SKU. Jest to wartość domyślna.

- `AllUsers` - Ten opcjonalny atrybut określa, czy ten pakiet zostanie zainstalowany dla wszystkich użytkowników. Domyślnie ten atrybut ma wartość false, co oznacza, że pakiet jest dla każdego użytkownika. (Jeśli ustawisz tę wartość na true, użytkownik instaljący musi podnieść poziom uprawnień administracyjnych, aby zainstalować wynikowy vsix.

- `InstalledByMsi` - Ten opcjonalny atrybut określa, czy ten pakiet jest instalowany przez plik MSI. Pakiety instalowane przez pakiet MSI są instalowane i zarządzane przez rozszerzenie MSI (programy i funkcje), a nie przez menedżera Visual Studio rozszerzenia.  Domyślnie ten atrybut ma wartość false, co oznacza, że pakiet nie jest instalowany przez plik MSI.

- `SystemComponent` - Ten opcjonalny atrybut określa, czy ten pakiet powinien być traktowany jako składnik systemowy. Składniki systemowe nie są wyświetlane w interfejsie użytkownika menedżera rozszerzeń i nie można ich zaktualizować. Domyślnie ten atrybut ma wartość false, co oznacza, że pakiet nie jest składnikiem systemowym.

- `AnyAttribute*` - Element akceptuje otwarty zestaw atrybutów, które zostaną ujawnione w czasie uruchamiania jako słownik pary `Installation` nazwa-wartość.

- `<InstallationTarget>` —Ten element kontroluje lokalizację, w której instalator VSIX instaluje pakiet. Jeśli wartość atrybutu to "ProductExtension", pakiet musi być ukierunkowany na SKU, która zainstalowała plik manifestu jako część jego zawartości w celu anonsowania dostępności dla `Scope` rozszerzeń. Element ma następujące atrybuty, gdy atrybut ma jawną lub domyślną wartość `<InstallationTarget>` `Scope` "ProductExtension":

  - `Id` - Ten atrybut identyfikuje pakiet.  Atrybut jest zgodny z konwencją przestrzeni nazw: Company.Product.Feature.Name. Atrybut `Id` może zawierać tylko znaki alfanumeryczne i może zawierać tylko 100 znaków. Oczekiwane wartości:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version` - Ten atrybut określa zakres wersji z minimalną i maksymalną obsługiwaną wersją tej wersji SKU. Pakiet może szczegółowo określić wersje jednostki SKU, które obsługuje. Notacja zakresu wersji to [10.0–11.0], gdzie

    - [ — minimalna wersja włącznie.

    - ] — maksymalna wersja włącznie.

    - ( — minimalna wersja wyłącznie.

    - ) — maksymalna wersja wyłącznie.

    - Numer pojedynczej wersji — tylko określona wersja.

    > [!IMPORTANT]
    > Wersja 2.0 schematu VSIX została wprowadzona w Visual Studio 2012 r. Aby użyć tego schematu, Visual Studio 2012 lub nowszy musi być zainstalowany na maszynie i używać VSIXInstaller.exe, który jest częścią tego produktu. Można wybrać wcześniejsze wersje programu Visual Studio z programem vsixinstaller Visual Studio 2012 lub nowszym, ale tylko przy użyciu nowszych wersji instalatora.

    Visual Studio 2017 można znaleźć na stronie [Visual Studio kompilacji i datach wydania.](../install/visual-studio-build-numbers-and-release-dates.md)

    Podczas wyrażania wersji dla wersji Visual Studio 2017 wersja pomocnicza powinna zawsze mieć **0**. Na przykład Visual Studio 2017 wersja 15.3.26730.0 powinna być wyrażona jako [15.0.26730.0,16.0). Jest to wymagane tylko w przypadku Visual Studio 2017 i nowszych wersji.

  - `AnyAttribute*` - Element umożliwia otwarty zestaw atrybutów, które są udostępniane w czasie uruchamiania jako słownik pary `<InstallationTarget>` nazwa-wartość.

### <a name="dependencies-element"></a>Element zależności
 Ten element zawiera listę zależności, które deklaruje ten pakiet. Jeśli zostaną określone jakiekolwiek zależności, te pakiety (identyfikowane przez ) `Id` muszą zostać zainstalowane wcześniej.

- `<Dependency>` element — ten element podrzędny ma następujące atrybuty:

  - `Id` - Ten atrybut musi być unikatowym identyfikatorem pakietu zależnego. Ta wartość tożsamości musi odpowiadać `<Metadata><Identity>Id` atrybutowi pakietu, od których zależy ten pakiet. Atrybut `Id` jest zgodny z konwencją przestrzeni nazw: Company.Product.Feature.Name. Atrybut może zawierać tylko znaki alfanumeryczne i może zawierać tylko 100 znaków.

  - `Version` - Ten atrybut określa zakres wersji z minimalną i maksymalną obsługiwaną wersją tej wersji SKU. Pakiet może szczegółowo określić wersje jednostki SKU, które obsługuje. Notacja zakresu wersji to [12.0, 13.0], gdzie:

    - [ — minimalna wersja włącznie.

    - ] — maksymalna wersja włącznie.

    - ( — minimalna wersja wyłącznie.

    - ) — maksymalna wersja wyłącznie.

    - Numer pojedynczej wersji — tylko określona wersja.

  - `DisplayName` - Ten atrybut to nazwa wyświetlana pakietu zależnego, która jest używana w elementach interfejsu użytkownika, takich jak okna dialogowe i komunikaty o błędach. Atrybut jest opcjonalny, chyba że pakiet zależny jest instalowany przez pakiet MSI.

  - `Location` - Ten opcjonalny atrybut określa ścieżkę względną w tym vsix do zagnieżdżonych pakietów VSIX lub adres URL lokalizacji pobierania zależności. Ten atrybut jest używany, aby ułatwić użytkownikowi zlokalizowanie pakietu wymagań wstępnych.

  - `AnyAttribute*` - Element akceptuje otwarty zestaw atrybutów, które zostaną ujawnione w czasie uruchamiania jako słownik pary `Dependency` nazwa-wartość.

### <a name="assets-element"></a>Assets, element
 Ten element zawiera listę `<Asset>` tagów dla każdego rozszerzenia lub elementu zawartości, który jest dostępny w tym pakiecie.

- `<Asset>` - Ten element zawiera następujące atrybuty i elementy:

  - `Type` - Typ rozszerzenia lub zawartości reprezentowanej przez ten element. Każdy `<Asset>` element musi mieć jeden element , ale wiele elementów może mieć ten sam element `Type` `<Asset>` `Type` . Ten atrybut powinien być reprezentowany jako w pełni kwalifikowana nazwa zgodnie z konwencjami przestrzeni nazw. Znane typy to:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Możesz tworzyć własne typy i nadawać im unikatowe nazwy. W czasie działania Visual Studio kod może wyliczać te typy niestandardowe i uzyskać do nich dostęp za pośrednictwem interfejsu API menedżera rozszerzeń.

  - `Path` — ścieżka względna do pliku lub folderu w pakiecie zawierającym zasób.

  - `TargetVersion` — zakres wersji, do którego odnosi się dany zasób. Służy do wysyłki wielu wersji zasobów do różnych wersji Visual Studio. Wymaga Visual Studio 2017.3 lub nowszego.

  - `AnyAttribute*` — otwarty zestaw atrybutów, który jest ujmowany w czasie uruchamiania jako słownik pary nazwa-wartość.

    `<AnyElement>*` — Dowolna zawartość ustrukturyzowana jest dozwolona między `<Asset>` tagiem rozpoczęcia i zakończenia. Wszystkie elementy są widoczne jako lista obiektów XmlElement. Rozszerzenia VSIX mogą definiować metadane specyficzne dla typu strukturalnego w pliku manifestu i wyliczać je w czasie działania.

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

- [Wysyłka Visual Studio rozszerzenia](../extensibility/shipping-visual-studio-extensions.md)
