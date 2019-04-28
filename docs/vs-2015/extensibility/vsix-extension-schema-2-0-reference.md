---
title: Odwołanie do schematu 2.0 rozszerzenia VSIX | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a8c6d236f9f11f53e79e4239868815c7bbe9137
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436931"
---
# <a name="vsix-extension-schema-20-reference"></a>Odwołanie do schematu 2.0 rozszerzenia VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Plik manifestu VSIX wdrożenia w tym artykule opisano zawartość pakietu VSIX. Format pliku jest regulowane przez schemat. W wersji 2.0 tego schematu obsługuje dodawanie niestandardowych typów i atrybutów.  Schematu manifestu jest rozszerzalny. Moduł ładujący manifestu ignoruje elementów XML oraz atrybuty, które go nie rozumie.  
  
> [!IMPORTANT]
> Program Visual Studio 2015 można ładować plików VSIX w formatach programu Visual Studio 2010, Visual Studio 2012 lub Visual Studio 2013.  
  
## <a name="package-manifest-schema"></a>Schematu manifestu pakietu  
 Element główny pliku manifestu XML jest `<PackageManifest>`, o jeden atrybut `Version`, która jest wersją format manifestu. W przypadku istotnych zmian do formatu, zostanie zmieniony format wersji. W tym temacie opisano format manifestu w wersji 2.0, określany w manifeście, ustawiając `Version` atrybutu, wartość wersji = "w wersji 2.0".  
  
### <a name="packagemanifest-element"></a>PackageManifest Element  
 W ramach `<PackageManifest>` elementu głównego można użyć następujących elementów:  
  
- `<Metadata>` -Metadanych i reklamy informacji na temat pakietu. Tylko jeden `Metadata` element jest dozwolony w manifeście.  
  
- `<Installation>` — W tej sekcji definiuje sposób, który można zainstalować ten pakiet rozszerzenia, jednostki SKU w aplikacji, które można zainstalować w tym. Tylko jeden `Installation` element jest dozwolony w manifeście. Manifest musi mieć `Installation` elementu lub ten pakiet nie można zainstalować w dowolnej jednostce SKU.  
  
- `<Dependencies>` -Opcjonalną listę zależności dla tego pakietu są zdefiniowane w tym miejscu.  
  
- `<Assets>` — Ta sekcja zawiera wszystkie zasoby zawarte w tym pakiecie. Bez tej sekcji ten pakiet nie Prezentuj zawartości.  
  
- `<AnyElement>*` Schematu manifestu jest na tyle elastyczna, aby zezwolić na inne elementy. Wszystkie elementy podrzędne, które nie są rozpoznawane przez moduł ładujący manifestu są widoczne w interfejsie API Menedżera rozszerzeń jako dodatkowe obiekty atrybutu XmlElement. Korzystając z tych elementów podrzędnych, rozszerzenia VSIX, można zdefiniować dodatkowe dane w pliku manifestu, który kod uruchomiony w programie Visual Studio mogą uzyskać dostęp w czasie wykonywania. Zobacz <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> i <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Element metadanych  
 Ta sekcja dotyczy metadane dotyczące pakietu, jego tożsamość i reklam informacji. `<Metadata>` zawiera następujące elementy:  
  
- `<Identity>` — Definiuje informacje identyfikacyjne tego pakietu i zawiera następujące atrybuty:  
  
    - `Id` — Ten atrybut musi być unikatowy identyfikator pakietu wybranego przez jego autora. Nazwa powinna być kwalifikowana taki sam sposób, który namespaced są typy CLR: Company.Product.Feature.Name. `Id` Atrybut jest ograniczona do 100 znaków.  
  
    - `Version` — Definiuje wersję tego pakietu i jego zawartość. Ten atrybut następujący format wersji zestawów CLR: Główna.pomocnicza.kompilacja.poprawka (1.2.40308.00). Pakiet o wyższy numer wersji jest uznawany za aktualizacje pakietu i można zainstalować za pośrednictwem istniejących zainstalowanej wersji.  
  
    - `Language` — Ten atrybut jest to domyślny język dla pakietu i odnosi się do danych tekstowych, w tym manifeście. Ten atrybut następuje po Konwencji kod ustawień regionalnych środowiska CLR dla zestawów zasobów, na przykład: en-us, en, fr-fr. Można określić `neutral` do deklarowania rozszerzenia niezależny od języka, który będzie uruchamiany w dowolnej wersji programu Visual Studio. Wartość domyślna to `neutral`.  
  
    - `Publisher` — Ten atrybut określa wydawcę tego pakietu, firma lub nazwy użytkownika. `Publisher` Atrybut jest ograniczona do 100 znaków.  
  
- `<DisplayName>` — Ten element Określa nazwę pakietu przyjazny dla użytkownika, która jest wyświetlana w Interfejsie użytkownika Menedżera rozszerzenia. `DisplayName` Zawartości jest ograniczona do 100 znaków.  
  
- `<Description>` — W tym opcjonalny element jest krótki opis pakietu i jego zawartość, która jest wyświetlana w interfejsie użytkownika Menedżera rozszerzeń. `Description` Zawartości może zawierać dowolny tekst, który ma, ale ma ograniczone do 1000 znaków.  
  
- `<MoreInfo>` — W tym opcjonalny element to adres URL strony online, która zawiera pełen opis tego pakietu. Protokół muszą być określone jako protokołu http.  
  
- `<License>` — W tym opcjonalny element jest ścieżką względną do pliku licencji (.txt, RTF) zawartych w pakiecie.  
  
- `<ReleaseNotes>` — W tym opcjonalny element jest względna ścieżka do zawartych w pakiecie (.txt, RTF) lub — w przeciwnym razie adres URL witryny sieci Web, która wyświetla informacje o wersji pliku informacje o wersji.  
  
- `<Icon>` — W tym opcjonalny element jest ścieżką względną do pliku obrazu (png, bmp, jpeg, ico) zawartych w pakiecie. Obraz ikony powinny być 32 x 32 piksele (lub zostanie zmniejszony do tego rozmiaru) oraz jest wyświetlany w widoku listy interfejsu użytkownika. Jeśli nie `Icon` element jest określony, domyślnie korzysta z interfejsu użytkownika.  
  
- `<PreviewImage>` — W tym opcjonalny element jest ścieżką względną do pliku obrazu (png, bmp, jpeg) zawartych w pakiecie. Obraz podglądu powinien być 200 x 200 pikseli i wyświetlane w szczegółach interfejsu użytkownika. Jeśli nie `PreviewImage` element jest określony, domyślnie korzysta z interfejsu użytkownika.  
  
- `<Tags>` — W tym opcjonalny element zawiera listę tagów dodatkowy tekst rozdzielaną średnikami, które są używane na potrzeby wskazówki dotyczące wyszukiwania. `Tags` Element jest ograniczona do 100 znaków.  
  
- `<GettingStartedGuide>` — W tym opcjonalny element jest ścieżką względną do pliku HTML lub adres URL witryny sieci Web, który zawiera informacje o sposobie używania rozszerzenia lub zawartości w ramach tego pakietu. Ten przewodnik jest uruchamiany jako część instalacji.  
  
- `<AnyElement>*` Schematu manifestu jest na tyle elastyczna, aby zezwolić na inne elementy. Wszystkie elementy podrzędne, które nie są rozpoznawane przez moduł ładujący manifestu są widoczne jako listę obiektów, XmlElement. Korzystając z tych elementów podrzędnych, rozszerzenia VSIX można zdefiniować dodatkowe dane w pliku manifestu i wyliczenia w czasie wykonywania.  
  
### <a name="installation-element"></a>Element instalacji  
 Ta sekcja definiuje sposób instalowania tego pakietu i jednostki SKU w aplikacji, które można zainstalować w. Ta sekcja zawiera następujące atrybuty:  
  
- `Experimental` — Ustaw ten atrybut na wartość true, jeśli mają rozszerzenie, które jest obecnie zainstalowane dla wszystkich użytkowników, ale tworzysz zaktualizowaną wersję na tym samym komputerze. Na przykład jeśli zainstalowano MyExtension 1.0 dla wszystkich użytkowników, ale chcesz debugować MyExtension 2.0 na tym samym komputerze, należy ustawić eksperymentalne = "true". Ten atrybut jest dostępne w programie Visual Studio 2015 Update 1 lub nowszy.  
  
- `Scope` — Ten atrybut można wykonać wartości "Global" lub "ProductExtension":  
  
    - "Global" Określa, że instalacja jest poza zakresem do określonej jednostki SKU. Na przykład ta wartość jest używana, gdy jest zainstalowany zestaw SDK rozszerzeń.  
  
    - "ProductExtension" Określa zainstalowanie tradycyjnych rozszerzenia VSIX (w wersji 1.0) obejmuje poszczególne jednostki SKU z programu Visual Studio. Jest to wartość domyślna.  
  
- `AllUsers` — To opcjonalny atrybut określa, czy ten pakiet zostanie zainstalowany dla wszystkich użytkowników. Domyślnie ten atrybut ma wartość FAŁSZ, określa, że pakiet jest dla użytkownika. (Jeśli ta wartość jest ustawiona na wartość true, użytkownik musi podnieść poziom do poziomu uprawnień administracyjnych, aby zainstalować VSIX wynikowe.  
  
- `InstalledByMsi` — To opcjonalny atrybut określa, czy ten pakiet jest zainstalowany za pomocą pakietu MSI. Zainstalowane pakiety za pomocą pakietu MSI są zainstalowane i zarządzane za pomocą pakietu MSI (programy i funkcje), a nie przez Visual Studio Extension Manager.  Domyślnie ten atrybut ma wartość FAŁSZ, która określa, że pakiet nie jest instalowany przez Instalatora MSI.  
  
- `SystemComponent` — To opcjonalny atrybut określa, czy ten pakiet należy uwzględnić składnikiem systemu. Składniki systemowe nie pokazuj w Interfejsie użytkownika Menedżera rozszerzeń i nie można zaktualizować. Domyślnie ten atrybut ma wartość FAŁSZ, która określa, że pakiet jest składnikiem systemu.  
  
- `AnyAttribute*` — `Installation` Akceptuje nieograniczony zbiór atrybutów, które będą dostępne w czasie wykonywania jako słownik par nazwa wartość.  
  
- `<InstallationTarget>` — Ten element określa lokalizację, w której Instalator VSIX instaluje pakiet. Jeśli wartość `Scope` atrybut jest "ProductExtension" pakiet musi być przeznaczony dla jednostki SKU, która ma zainstalowany plik manifestu w ramach jego zawartość, aby anonsować jej dostępność rozszerzenia. `<InstallationTarget>` Element ma następujące atrybuty kiedy `Scope` atrybut ma jawnie lub wartość domyślną "ProductExtension":  
  
    - `Id` — Ten atrybut określa pakiet.  Ten atrybut następującą konwencją nazw: Company.Product.Feature.Name. `Id` Atrybut może zawierać tylko znaki alfanumeryczne i jest ograniczona do 100 znaków. Oczekiwane wartości:  
  
        - Microsoft.VisualStudio.IntegratedShell  
  
        - Microsoft.VisualStudio.Pro  
  
        - Microsoft.VisualStudio.Premium  
  
        - Microsoft.VisualStudio.Ultimate  
  
        - Microsoft.VisualStudio.VWDExpress  
  
        - Microsoft.VisualStudio.VPDExpress  
  
        - Microsoft.VisualStudio.VSWinExpress  
  
        - Microsoft.VisualStudio.VSLS  
  
        - My.Shell.App  
  
    - `Version` — Ten atrybut określa zakres wersji za pomocą minimalnej i maksymalnej obsługiwanej wersji tej jednostki SKU. Pakiet można szczegółowo wersji jednostki SKU, które obsługuje. Gdzie jest notacji zakresu wersji [10.0 — 11.0]  
  
        - [— minimalna wersja (włącznie).  
  
        - ] — maksymalna wersja (włącznie).  
  
        - (— minimalna wersja wyłączności.  
  
        - ) — maksymalna wersja wyłączności.  
  
        - Jednej wersji # - określonej wersji.  
  
        > [!IMPORTANT]
        > Wersja 2.0 schematu VSIX został wprowadzony w programie Visual Studio 2012. Aby użyć tego schematu jest posiadanie programu Visual Studio 2012 lub później zainstalowane na komputerze i używać VSIXInstaller.exe należącego do tego produktu. Można wskazać wcześniejszych wersji programu Visual Studio za pomocą programu Visual Studio 2012 lub nowszym Instalator VSIX, ale tylko przy użyciu nowszej wersji Instalatora.  
  
    - `AnyAttribute*` — `<InstallationTarget>` Elementu umożliwia nieograniczony zbiór atrybutów, które będą dostępne w czasie wykonywania jako słownik par nazwa wartość.  
  
### <a name="dependencies-element"></a>Element zależności  
 Ten element zawiera listę zależności, które deklaruje tego pakietu. Jeśli nie określono żadnych zależności, te pakiety (identyfikowane przez ich `Id`) musi być zainstalowane przed.  
  
- `<Dependency>` Element — ten element podrzędny ma następujące atrybuty:  
  
    - `Id` — Ten atrybut musi być unikatowy identyfikator dla pakietu zależnego. Ta wartość tożsamości musi odpowiadać `<Metadata><Identity>Id` atrybut, który ten pakiet jest zależny od pakietu. `Id` Atrybut następuje po Konwencji przestrzeni nazw: Company.Product.Feature.Name. Ten atrybut może zawierać tylko znaki alfanumeryczne i jest ograniczona do 100 znaków.  
  
    - `Version` — Ten atrybut określa zakres wersji za pomocą minimalnej i maksymalnej obsługiwanej wersji tej jednostki SKU. Pakiet można szczegółowo wersji jednostki SKU, które obsługuje. Wersja zakresu jest [12.0, 13,0], gdzie:  
  
        - [— minimalna wersja (włącznie).  
  
        - ] — maksymalna wersja (włącznie).  
  
        - (— minimalna wersja wyłączności.  
  
        - ) — maksymalna wersja wyłączności.  
  
        - Jednej wersji # - określonej wersji.  
  
    - `DisplayName` — Ten atrybut jest nazwa wyświetlana pakietu zależnego, który jest używany w elementy interfejsu użytkownika, takie jak okna dialogowe i komunikaty o błędach. Ten atrybut jest opcjonalny, jeśli nie zainstalowano zależnego pakietu za pomocą pakietu MSI.  
  
    - `Location` — To opcjonalny atrybut określa ścieżkę względną w tym pliku VSIX do zagnieżdżonych pakietu VSIX albo adres URL do lokalizacji pobierania dla zależności. Ten atrybut służy do pomocy użytkownika Znajdź pakietu wstępnie wymaganych składników.  
  
    - `AnyAttribute*` — `Dependency` Akceptuje nieograniczony zbiór atrybutów, które będą dostępne w czasie wykonywania jako słownik par nazwa wartość.  
  
### <a name="assets-element"></a>Zasoby — Element  
 Element ten zawiera listę `<Asset>` tagi dla każdego elementu rozszerzenia lub zawartości udostępniane przez ten pakiet.  
  
- `<Asset>` — Ten element zawiera następujące atrybuty i elementy:  
  
  - `Type` — Jest to typ rozszerzenia lub zawartości, reprezentowany przez ten element. Każdy `<Asset>` elementu musi mieć pojedynczy `Type`, ale wiele `<Asset>` elementy mogą mieć takie same `Type`. Ten atrybut powinna być reprezentowana jako w pełni kwalifikowana nazwa, zgodnie z konwencjami przestrzeni nazw. Znane typy to:  
  
    1. Microsoft.VisualStudio.VsPackage  
  
    2. Microsoft.VisualStudio.MefComponent  
  
    3. Microsoft.VisualStudio.ToolboxControl  
  
    4. Microsoft.VisualStudio.Samples  
  
    5. Microsoft.VisualStudio.ProjectTemplate  
  
    6. Microsoft.VisualStudio.ItemTemplate  
  
    7. Microsoft.VisualStudio.Assembly  
  
       Możesz utworzyć własne typy i nadaj im nazwy unikatowe. W czasie wykonywania w programie Visual Studio Twój kod można wyliczyć i dostęp do tych typów niestandardowych przy użyciu interfejsu API Menedżera rozszerzeń.  
  
  - Ścieżka — ścieżkę względną do pliku lub folderu w pakiecie, który zawiera element zawartości.  
  
  - `AnyAttribute*` — Nieograniczony zbiór atrybutów, które będą dostępne w czasie wykonywania jako słownik par nazwa wartość.  
  
     `<AnyElement>*` — Żadnej ze strukturą zawartości jest dozwolone między `<Asset>` rozpoczęcia i zakończenia znacznika. Wszystkie elementy są widoczne jako listę obiektów, XmlElement. Rozszerzenia VSIX można zdefiniować ze strukturą metadanych dla określonego typu w pliku manifestu i wyliczenia w czasie wykonywania.  
  
### <a name="sample-manifest"></a>Manifest próbki  
  
```  
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
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
