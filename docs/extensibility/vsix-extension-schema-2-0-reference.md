---
title: Odwołanie do schematu rozszerzenia VSIX 2.0 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697910"
---
# <a name="vsix-extension-schema-20-reference"></a>Odwołanie do schematu rozszerzenia VSIX 2.0
Plik manifestu wdrożenia VSIX opisuje zawartość pakietu VSIX. Format pliku jest regulowany przez schemat. Wersja 2.0 tego schematu obsługuje dodawanie typów niestandardowych i atrybutów.  Schemat manifestu jest rozszerzalny. Moduł ładujący manifest ignoruje elementy XML i atrybuty, których nie rozumie.

> [!IMPORTANT]
> Visual Studio 2015 można załadować pliki VSIX w programach Visual Studio 2010, Visual Studio 2012 lub Visual Studio 2013 formatów.

## <a name="package-manifest-schema"></a>Schemat manifestu pakietu
 Głównym elementem pliku XML `<PackageManifest>`manifestu jest . Ma jeden atrybut `Version`, który jest wersją formatu manifestu. Jeśli zostaną wprowadzone istotne zmiany w formacie, format wersji zostanie zmieniony. W tym artykule opisano format manifestu w wersji 2.0, który jest określony w manifeście, ustawiając `Version` atrybut na wartość Version="2.0".

### <a name="packagemanifest-element"></a>Element PackageManifest
 W `<PackageManifest>` elemencie głównym można użyć następujących elementów:

- `<Metadata>`- Metadane i informacje reklamowe o samym pakiecie. Tylko `Metadata` jeden element jest dozwolony w manifeście.

- `<Installation>`- Ta sekcja określa sposób, w jaki można zainstalować ten pakiet rozszerzenia, w tym jednostki SKU aplikacji, w których można zainstalować. Tylko jeden `Installation` element jest dozwolony w manifeście. Manifest musi mieć `Installation` element lub ten pakiet nie zostanie zainstalowany w dowolnej jednostce SKU.

- `<Dependencies>`- Opcjonalna lista zależności dla tego pakietu są zdefiniowane w tym miejscu.

- `<Assets>`- Ta sekcja zawiera wszystkie zasoby zawarte w tym pakiecie. Bez tej sekcji ten pakiet nie będzie powierzchni żadnej zawartości.

- `<AnyElement>*`- Schemat manifestu jest wystarczająco elastyczny, aby umożliwić inne elementy. Wszystkie elementy podrzędne nie rozpoznawane przez moduł ładujący manifestu są widoczne w interfejsie API Menedżera rozszerzeń jako dodatkowe obiekty XmlElement. Za pomocą tych elementów podrzędnych rozszerzenia VSIX można zdefiniować dodatkowe dane w pliku manifestu, który kod uruchomiony w programie Visual Studio można uzyskać dostęp w czasie wykonywania. Zobacz [Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Element metadanych
 Ta sekcja jest metadane dotyczące pakietu, jego tożsamości i informacji reklamowych. `<Metadata>`zawiera następujące elementy:

- `<Identity>`- Definiuje informacje identyfikacyjne dla tego pakietu i zawiera następujące atrybuty:

  - `Id`- Ten atrybut musi być unikatowym identyfikatorem dla pakietu wybranego przez jego autora. Nazwa powinna być kwalifikowana w taki sam sposób, w jaki typy CLR są obszarami nazw: Company.Product.Feature.Name. Atrybut `Id` jest ograniczony do 100 znaków.

  - `Version`- Definiuje wersję tego pakietu i jego zawartość. Ten atrybut jest zgodny z formatem przechowywania wersji zestawu CLR: Major.Minor.Build.Revision (1.2.40308.00). Pakiet o wyższym numerze wersji jest uważany za aktualizacje pakietu i może być zainstalowany za pomocą istniejącej zainstalowanej wersji.

  - `Language`- Ten atrybut jest domyślnym językiem dla pakietu i odpowiada danych tekstowych w tym manifeście. Ten atrybut jest zgodny z konwencją kodu ustawień regionalnych CLR dla zestawów zasobów, na przykład: en-us, en, fr-fr. Można określić, `neutral` aby zadeklarować rozszerzenie neutralne dla języka, które będzie uruchamiane w dowolnej wersji programu Visual Studio. Wartością domyślną jest `neutral`.

  - `Publisher`- Ten atrybut identyfikuje wydawcę tego pakietu, nazwę firmy lub osoby. Atrybut `Publisher` jest ograniczony do 100 znaków.

- `<DisplayName>`- Ten element określa przyjazną dla użytkownika nazwę pakietu, która jest wyświetlana w interfejsie użytkownika Menedżera rozszerzeń. Zawartość `DisplayName` jest ograniczona do 50 znaków.

- `<Description>`- Ten opcjonalny element jest krótki opis pakietu i jego zawartość, który jest wyświetlany w interfejsie użytkownika Menedżera rozszerzeń. Zawartość `Description` może zawierać dowolny tekst, ale jest ograniczona do 1000 znaków.

- `<MoreInfo>`- Ten opcjonalny element jest adresem URL strony online, która zawiera pełny opis tego pakietu. Protokół musi być określony jako http.

- `<License>`- Ten opcjonalny element jest względną ścieżką do pliku licencji (txt, .rtf) zawartego w pakiecie.

- `<ReleaseNotes>`- Ten opcjonalny element jest ścieżką względną do pliku notatek wydania zawartego w pakiecie (.txt, .rtf) lub adresem URL do witryny sieci Web, która wyświetla informacje o wersji.

- `<Icon>`- Ten opcjonalny element jest względną ścieżką do pliku obrazu (png, bmp, jpeg, ico) zawartego w pakiecie. Obraz ikony powinien być 32x32 pikseli (lub zostanie zmniejszony do tego rozmiaru) i pojawia się w interfejsie widoku listy. Jeśli `Icon` żaden element nie jest określony, interfejs użytkownika używa wartości domyślnej.

- `<PreviewImage>`- Ten opcjonalny element jest względną ścieżką do pliku obrazu (png, bmp, jpeg) zawartego w pakiecie. Obraz podglądu powinien mieć rozmiar 200 x 200 pikseli i być wyświetlany w interfejsie użytkownika szczegółów. Jeśli `PreviewImage` żaden element nie jest określony, interfejs użytkownika używa wartości domyślnej.

- `<Tags>`- Ten opcjonalny element zawiera listę dodatkowych znaczników tekstowych rozdzielanych średnikami, które są używane do wskazówek dotyczących wyszukiwania. Element `Tags` jest ograniczony do 100 znaków.

- `<GettingStartedGuide>`- Ten opcjonalny element jest względną ścieżką do pliku HTML lub adresem URL do witryny sieci Web, który zawiera informacje o tym, jak używać rozszerzenia lub zawartości w tym pakiecie. Ten przewodnik jest uruchamiany jako część instalacji.

- `<AnyElement>*`- Schemat manifestu jest wystarczająco elastyczny, aby umożliwić inne elementy. Wszystkie elementy podrzędne, które nie są rozpoznawane przez moduł ładujący manifest są udostępniane jako lista XmlElement obiektów. Za pomocą tych elementów podrzędnych rozszerzenia VSIX można zdefiniować dodatkowe dane w pliku manifestu i wyliczyć je w czasie wykonywania.

### <a name="installation-element"></a>Element instalacji
 W tej sekcji zdefiniowano sposób, w jaki można zainstalować ten pakiet i jednostki SKU aplikacji, w których można go zainstalować. Ta sekcja zawiera następujące atrybuty:

- `Experimental`- Ustaw ten atrybut na true, jeśli masz rozszerzenie, które jest obecnie zainstalowane dla wszystkich użytkowników, ale tworzysz zaktualizowaną wersję na tym samym komputerze. Na przykład jeśli zainstalowano MyExtension 1.0 dla wszystkich użytkowników, ale chcesz debugować MyExtension 2.0 na tym samym komputerze, ustaw Experimental="true". Ten atrybut jest dostępny w programie Visual Studio 2015 Update 1 i nowszych.

- `Scope`- Ten atrybut może mieć wartość "Globalny" lub "ProductExtension":

  - "Globalny" określa, że instalacja nie jest objęty zakresem określonej jednostki SKU. Na przykład ta wartość jest używana, gdy jest zainstalowany pakiet SDK rozszerzenia.

  - "ProductExtension" określa, że jest zainstalowane tradycyjne rozszerzenie VSIX (wersja 1.0) o zakresie do poszczególnych jednostek SKU programu Visual Studio. Jest to wartość domyślna.

- `AllUsers`- Ten atrybut opcjonalny określa, czy ten pakiet zostanie zainstalowany dla wszystkich użytkowników. Domyślnie ten atrybut jest false, który określa, że pakiet jest na użytkownika. (Po ustawieniu tej wartości na true, użytkownik instalacji musi podnieść do poziomu uprawnień administracyjnych, aby zainstalować wynikowy VSIX.

- `InstalledByMsi`- Ten atrybut opcjonalny określa, czy ten pakiet jest zainstalowany przez MSI. Pakiety zainstalowane przez msi są instalowane i zarządzane przez MSI (Programy i funkcje), a nie przez Menedżera rozszerzeń programu Visual Studio.  Domyślnie ten atrybut jest false, który określa, że pakiet nie jest zainstalowany przez MSI.

- `SystemComponent`- Ten atrybut opcjonalny określa, czy ten pakiet należy uznać za składnik systemu. Składniki systemu nie są wyświetlane w interfejsie użytkownika Menedżera rozszerzeń i nie można ich zaktualizować. Domyślnie ten atrybut jest false, który określa, że pakiet nie jest składnikiem systemu.

- `AnyAttribute*`- `Installation` Element akceptuje otwarty zestaw atrybutów, które będą udostępniane w czasie wykonywania jako słownik pary nazwa-wartość.

- `<InstallationTarget>`-Ten element steruje lokalizacją, w której instalator VSIX instaluje pakiet. Jeśli wartość atrybutu `Scope` jest "ProductExtension" pakiet musi kierować jednostki SKU, który zainstalował plik manifestu jako część jego zawartości do anonsowania jego dostępności do rozszerzeń. Element `<InstallationTarget>` ma następujące atrybuty, gdy `Scope` atrybut ma jawną lub domyślną wartość "ProductExtension":

  - `Id`- Ten atrybut identyfikuje pakiet.  Atrybut jest zgodny z konwencją obszaru nazw: Company.Product.Feature.Name. Atrybut `Id` może zawierać tylko znaki alfanumeryczne i jest ograniczony do 100 znaków. Oczekiwane wartości:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version`- Ten atrybut określa zakres wersji z minimalną i maksymalną obsługiwaną wersją tej jednostki SKU. Pakiet można szczegółowo wersje jednostek SKU, które obsługuje. Notacja zakresu wersji to [10.0 - 11.0], gdzie

    - [ - minimalna wersja włącznie.

    - ] - maksymalna wersja włącznie.

    - ( - wersja minimalna wyłączna.

    - ) - maksymalna wersja wyłączna.

    - Pojedyncza wersja # - tylko określona wersja.

    > [!IMPORTANT]
    > Wersja 2.0 schematu VSIX została wprowadzona w programie Visual Studio 2012. Aby użyć tego schematu, musisz mieć zainstalowany program Visual Studio 2012 lub nowszy na komputerze i użyć programu VSIXInstaller.exe, który jest częścią tego produktu. Można kierować na wcześniejsze wersje programu Visual Studio z visual studio 2012 lub nowszym VSIXInstaller, ale tylko przy użyciu nowszych wersji instalatora.

    Numery wersji programu Visual Studio 2017 można znaleźć w [numerach kompilacji programu Visual Studio i datach wydania.](../install/visual-studio-build-numbers-and-release-dates.md)

    Podczas wyrażania wersji dla programu Visual Studio 2017 wersja pomocnicza powinna być zawsze **0**. Na przykład visual studio 2017 wersja 15.3.26730.0 powinny być wyrażone jako [15.0.26730.0,16.0). Jest to wymagane tylko dla programu Visual Studio 2017 i nowszych numerów wersji.

  - `AnyAttribute*`- `<InstallationTarget>` Element umożliwia otwarty zestaw atrybutów, który jest narażony w czasie wykonywania jako słownik pary nazwa-wartość.

### <a name="dependencies-element"></a>Element Zależności
 Ten element zawiera listę zależności, które ten pakiet deklaruje. Jeśli określono wszystkie zależności, te pakiety `Id`(identyfikowane przez ich) muszą być zainstalowane wcześniej.

- `<Dependency>`element — ten element podrzędny ma następujące atrybuty:

  - `Id`- Ten atrybut musi być unikatowym identyfikatorem pakietu zależnego. Ta wartość tożsamości `<Metadata><Identity>Id` musi odpowiadać atrybutowi pakietu, od których zależy ten pakiet. Atrybut `Id` jest zgodny z konwencją obszaru nazw: Company.Product.Feature.Name. Atrybut może zawierać tylko znaki alfanumeryczne i jest ograniczony do 100 znaków.

  - `Version`- Ten atrybut określa zakres wersji z minimalną i maksymalną obsługiwaną wersją tej jednostki SKU. Pakiet można szczegółowo wersje jednostek SKU, które obsługuje. Notacja zakresu wersji to [12.0, 13.0], gdzie:

    - [ - minimalna wersja włącznie.

    - ] - maksymalna wersja włącznie.

    - ( - wersja minimalna wyłączna.

    - ) - maksymalna wersja wyłączna.

    - Pojedyncza wersja # - tylko określona wersja.

  - `DisplayName`- Ten atrybut jest nazwą wyświetlaną pakietu zależnego, który jest używany w elementach interfejsu użytkownika, takich jak okna dialogowe i komunikaty o błędach. Atrybut jest opcjonalny, chyba że pakiet zależny jest zainstalowany przez MSI.

  - `Location`- Ten atrybut opcjonalny określa ścieżkę względną w tym VSIX do zagnieżdżonego pakietu VSIX lub adres URL do lokalizacji pobierania zależności. Ten atrybut jest używany do pomocy użytkownikowi zlokalizować pakiet warunek wstępny.

  - `AnyAttribute*`- `Dependency` Element akceptuje otwarty zestaw atrybutów, które będą udostępniane w czasie wykonywania jako słownik pary nazwa-wartość.

### <a name="assets-element"></a>Element Zasoby
 Ten element zawiera `<Asset>` listę tagów dla każdego rozszerzenia lub elementu zawartości ukazytowany przez ten pakiet.

- `<Asset>`- Ten element zawiera następujące atrybuty i elementy:

  - `Type`- Typ rozszerzenia lub zawartość reprezentowana przez ten element. Każdy `<Asset>` element musi `Type`mieć jeden `<Asset>` , ale `Type`wiele elementów może mieć to samo . Ten atrybut powinien być reprezentowany jako w pełni kwalifikowana nazwa, zgodnie z konwencjami obszaru nazw. Znane typy to:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefFirment

    3. Kontrola microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Płyta Microsoft.VisualStudio.ProjectTemplate

    6. Płyta Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Możesz tworzyć własne typy i nadać im unikalne nazwy. W czasie wykonywania w programie Visual Studio kod można wyliczyć i uzyskać dostęp do tych typów niestandardowych za pośrednictwem interfejsu API Menedżera rozszerzeń.

  - `Path`- względna ścieżka do pliku lub folderu w pakiecie, który zawiera zasób.

  - `TargetVersion`- zakres wersji, do którego ma zastosowanie dany składnik aktywów. Służy do wysyłania wielu wersji zasobów do różnych wersji programu Visual Studio. Wymaga programu Visual Studio 2017.3 lub nowsze, aby mieć wpływ.

  - `AnyAttribute*`- Otwarty zestaw atrybutów, który jest narażony w czasie wykonywania jako słownik pary nazwa-wartość.

    `<AnyElement>*`- Każda zawartość strukturalna jest `<Asset>` dozwolona między tagiem początkowym a końcowym. Wszystkie elementy są udostępniane jako lista XmlElement obiektów. Rozszerzenia VSIX można zdefiniować ustrukturyzowane metadane specyficzne dla typu w pliku manifestu i wyliczyć je w czasie wykonywania.

### <a name="sample-manifest"></a>Manifest próbki

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

- [Wysyłaj rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
