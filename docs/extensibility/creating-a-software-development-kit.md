---
title: Tworzenie zestawu do tworzenia oprogramowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739593"
---
# <a name="create-a-software-development-kit"></a>Tworzenie zestawu do tworzenia oprogramowania

Zestaw do tworzenia oprogramowania (SDK) to zbiór interfejsów API, do których można odwoływać się jako pojedynczy element w programie Visual Studio. Okno dialogowe **Menedżer odwołań** zawiera listę wszystkich sks, które są istotne dla projektu. Po dodaniu SDK do projektu interfejsy API są dostępne w programie Visual Studio.

Istnieją dwa typy sdków:

- Platformy SDK są obowiązkowe składniki do tworzenia aplikacji dla platformy. Na przykład [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK jest wymagane [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] do tworzenia aplikacji.

- ZestawY SDK rozszerzenia są opcjonalnymi składnikami, które rozszerzają platformę, ale nie są obowiązkowe do tworzenia aplikacji dla tej platformy.

W poniższych sekcjach opisano ogólną infrastrukturę sdków sdk i jak utworzyć sdk platformy i sdk rozszerzenia.

## <a name="platform-sdks"></a>Platformy SDK

Platformy SDK są wymagane do tworzenia aplikacji dla platformy. Na przykład [!INCLUDE[win81](../debugger/includes/win81_md.md)] sdk jest wymagane do [!INCLUDE[win81](../debugger/includes/win81_md.md)]tworzenia aplikacji dla .

### <a name="installation"></a>Instalacja

Wszystkie pakiety SDK platformy zostaną zainstalowane w *hklm\software\Microsoft\Microsoft SDKs\\[TPI]\v[TPV]\\ @InstallationFolder = [SDK root]*. W związku [!INCLUDE[win81](../debugger/includes/win81_md.md)] z tym pakiet SDK jest instalowany w witrynie *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

### <a name="layout"></a>Układ

SDK platformy mają następujący układ:

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| Węzeł | Opis |
|------------------------| - |
| *Folder Odwołania* | Zawiera pliki binarne zawierające interfejsy API, które mogą być kodowane. Mogą to być pliki lub zestawy metadanych systemu Windows (WinMD). |
| *Folder DesignTime* | Zawiera pliki, które są potrzebne tylko w czasie przed uruchomieniem/debugowaniem. Mogą to być dokumenty XML, biblioteki, nagłówki, pliki binarne czasu projektowania przybornika, artefakty MSBuild itd.<br /><br /> Dokumenty XML, najlepiej, być umieszczone w folderze *\DesignTime,* ale dokumenty XML dla odwołań będą nadal umieszczane obok pliku referencyjnego w programie Visual Studio. Na przykład doc XML dla odwołania<em>\References\\\\[config] [arch]\sample.dll</em> będzie *\\\References [config]\\[arch]\sample.xml*, a zlokalizowaną wersją tego doc będzie *\References\\[config]\\[arch]\\[locale]\sample.xml*. |
| *Folder konfiguracji* | Mogą istnieć tylko trzy foldery: *Debug*, *Retail* i *CommonConfiguration*. Autorzy zestawu SDK mogą umieszczać swoje pliki w obszarze *CommonConfiguration,* jeśli ten sam zestaw plików zestawu SDK powinien być używane, niezależnie od konfiguracji, do jakiej będzie kierować konsument zestawu SDK. |
| *Folder Architektury* | Może istnieć dowolny obsługiwany folder *architektury.* Visual Studio obsługuje następujące architektury: x86, x64, ARM i neutralne. Uwaga: Win32 mapuje na x86, a AnyCPU na neutralne.<br /><br /> MSBuild wygląda tylko w obszarze *\CommonConfiguration\neutral* dla sdk platformy. |
| *Sdkmanifest.xml* | W tym pliku opisano, jak program Visual Studio powinien korzystać z SDK. Spójrz na manifest SDK dla: [!INCLUDE[win81](../debugger/includes/win81_md.md)]<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Nazwa wyświetlacza:** Wartość wyświetlana przez przeglądarkę obiektów na liście Przeglądaj.<br /><br /> **PlatformaTożowość:** Istnienie tego atrybutu informuje Visual Studio i MSBuild, że SDK jest sdk platformy i że odwołania dodane z niego nie powinny być kopiowane lokalnie.<br /><br /> **TargetFramework:** Ten atrybut jest używany przez program Visual Studio, aby upewnić się, że tylko projekty, które są przeznaczone dla tych samych struktur, jak określono w wartości tego atrybutu może korzystać z SDK.<br /><br /> **MinVSVersion:** Ten atrybut jest używany przez program Visual Studio do korzystania tylko z SDK, które mają do niego zastosowanie.<br /><br /> **Odniesienie:** Ten atrybut musi być określony tylko dla tych odwołań, które zawierają formanty. Aby uzyskać informacje na temat określania, czy odwołanie zawiera formanty, zobacz poniżej. |

## <a name="extension-sdks"></a>SDK rozszerzenia

W poniższych sekcjach opisano, co należy zrobić, aby wdrożyć sdk rozszerzenia.

### <a name="installation"></a>Instalacja

SDK rozszerzenia można zainstalować dla określonego użytkownika lub dla wszystkich użytkowników bez określania klucza rejestru. Aby zainstalować pakiet SDK dla wszystkich użytkowników, użyj następującej ścieżki:

*%Program Files%\Microsoft\<SDKs\>target platform \v\><numer wersji platformy \ExtensionSDKs*

W przypadku instalacji specyficznej dla użytkownika należy użyć następującej ścieżki:

*%USERPROFILE%\AppData\Local\Microsoft SDKs\<\>target platform \v<\>numer wersji platformy \ExtensionSDKs*

Jeśli chcesz użyć innej lokalizacji, musisz wykonać jedną z dwóch czynności:

1. Określ go w kluczu rejestru:

     **HKLM\Software\Microsoft\Microsoft\<SDKs target platform>\v<\>numer wersji platformy \ExtensionSDKs\<SDKName \<>SDKVersion>**\

     i dodaj podklucz (domyślny), `<path to SDK><SDKName><SDKVersion>`który ma wartość .

2. Dodaj właściwość `SDKReferenceDirectoryRoot` MSBuild do pliku projektu. Wartość tej właściwości jest osikowo rozdzielona lista katalogów, w których znajdują się SDK rozszerzenia, do których chcesz się odwołać.

### <a name="installation-layout"></a>Układ instalacji

ZestawY SDK rozszerzeń mają następujący układ instalacji:

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\<SDKName\> \\<SDKVersion\>: nazwa i wersja rozszerzenia SDK pochodzi od odpowiednich nazw folderów w ścieżce do katalogu głównego SDK. MSBuild używa tej tożsamości, aby znaleźć SDK na dysku, a program Visual Studio wyświetla tę tożsamość w oknie **Właściwości** i **Menedżerze odwołań.**

2. *Folder Odwołania:* pliki binarne zawierające interfejsy API. Mogą to być pliki lub zestawy metadanych systemu Windows (WinMD).

3. *Folder Redist:* pliki, które są potrzebne do środowiska uruchomieniowego/debugowania i powinny zostać spakowane jako część aplikacji użytkownika. Wszystkie pliki binarne powinny być umieszczone pod *\redist\\<config\> \\<arch\>*, a nazwy binarne powinny mieć następujący format, aby zapewnić unikatowość: *]*\<> firmy. \<> produktu. \<celu>. \<>rozszerzenia <em>. Na przykład *Microsoft.Cpp.Build.dll</em>. Wszystkie pliki o nazwach, które mogą kolidować z nazwami plików z innych SDK (na przykład javascript, css, pri, xaml, png i jpg) powinny być umieszczone pod <em>\redist\\<config\> \\<\> \\ arch<\> \* sdkname z wyjątkiem plików skojarzonych z formantymi XAML. Pliki te powinny być umieszczone pod\\ *\redist\> \\<config\> \\<arch<componentname\></em>.

4. *Folder DesignTime:* pliki, które są potrzebne tylko w czasie przed uruchomieniem/debugowaniem i nie powinny być pakowane jako część aplikacji użytkownika. Mogą to być dokumenty XML, biblioteki, nagłówki, pliki binarne czasu projektowania przybornika, artefakty MSBuild i tak dalej. Każdy SDK, który jest przeznaczony do użycia przez projekt macierzysty musi mieć plik *SDKName.props.* Poniżej przedstawiono przykład tego typu pliku.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    Dokumenty referencyjne XML są umieszczane obok pliku referencyjnego. Na przykład dokumentem referencyjnym XML dla *\References\\ \> \\<config\><arch \sample.dll* assembly jest *\References\\<config\> \\<\>arch \sample.xml*, a zlokalizowana wersja tego dokumentu to *\References\\<config\>\> \\<arch\> \\<locale \sample.xml*.

5. *Folder konfiguracji:* trzy podfoldery: *Debug*, *Handel detaliczny*i *CommonConfiguration*. Autorzy zestawu SDK mogą umieszczać swoje pliki w obszarze *CommonConfiguration,* gdy ten sam zestaw plików zestawu SDK powinien być zużywany, niezależnie od konfiguracji, do jakiej ma dążyć konsument zestawu SDK.

6. *Folder architektury:* obsługiwane są następujące architektury: x86, x64, ARM, neutralne. Win32 mapuje na x86, a AnyCPU na neutralne.

### <a name="sdkmanifestxml"></a>Sdkmanifest.xml

Plik *SDKManifest.xml* opisuje, jak program Visual Studio powinien korzystać z SDK. Poniżej przedstawiono przykład:

```
<FileList>
DisplayName = "My SDK"
ProductFamilyName = "My SDKs"
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
MinVSVersion = "14.0"
MaxPlatformVersion = "8.1"
AppliesTo = "WindowsAppContainer + WindowsXAML"
SupportPrefer32Bit = "True"
SupportedArchitectures = "x86;x64;ARM"
SupportsMultipleVersions = "Error"
CopyRedistToSubDirectory = "."
DependsOn = "SDKB, version=2.0"
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

Poniższa lista zawiera elementy pliku:

1. DisplayName: wartość, która pojawia się w Menedżerze odwołań, Eksploratorze rozwiązań, przeglądarce obiektów i innych lokalizacjach w interfejsie użytkownika programu Visual Studio.

2. ProductFamilyName: Ogólna nazwa produktu SDK. Na przykład [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] pakiet SDK nosi nazwy "Microsoft.WinJS.1.0" i "Microsoft.WinJS.2.0", które należą do tej samej rodziny produktów Z rodziny produktów SDK,"Microsoft.WinJS". Ten atrybut umożliwia Visual Studio i MSBuild do tego połączenia. Jeśli ten atrybut nie istnieje, nazwa SDK jest używana jako nazwa rodziny produktu.

3. FrameworkIdentity: Określa zależność od co najmniej jednej bibliotek składników systemu Windows. Wartość tego atrybutu jest umieszczana w manifeście aplikacji zużywającej. Ten atrybut ma zastosowanie tylko do bibliotek składników systemu Windows.

4. TargetFramework: Określa zestawy SDK, które są dostępne w Menedżerze odwołań i przyborniku. Jest to lista wstępnie rozdzielanych średnikami monikerów struktury docelowej, na przykład ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1". Jeśli określono kilka wersji tej samej struktury docelowej, Menedżer odwołań używa najniższej określonej wersji do celów filtrowania. Na przykład jeśli określono ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1", Menedżer odwołań użyje ".NET Framework, version=v2.0". Jeśli określony profil struktury docelowej jest określony, tylko ten profil będzie używany przez Menedżera odwołań do celów filtrowania. Na przykład po określeniu "Silverlight, version=v4.0, profile=WindowsPhone" Menedżer odwołań filtruje tylko profil systemu Windows Phone; projekt docelowy pełnej silverlight 4.0 Framework nie widzi SDK w Menedżerze odwołań.

5. MinVSVersion: minimalna wersja programu Visual Studio.

6. MaxPlatformVerson: Maksymalna wersja platformy docelowej powinna służyć do określenia wersji platformy, na których nie będzie działać moduł SDK rozszerzenia. Na przykład pakiet środowiska wykonawczego programu Microsoft Visual C++ w wersji 11.0 powinien odwoływać się tylko do projektów systemu Windows 8. Tak więc, Projekt Systemu Windows 8 MaxPlatformVersion jest 8.0. Oznacza to, że Menedżer odwołań odfiltruje pakiet środowiska wykonawczego programu Microsoft Visual C++ dla projektu systemu [!INCLUDE[win81](../debugger/includes/win81_md.md)] Windows 8.1, a program MSBuild zgłasza błąd, gdy projekt odwołuje się do niego. Uwaga: ten element jest [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]obsługiwany począwszy od .

7. AppliesTo: Określa szepy SDK, które są dostępne w Menedżerze odwołań, określając odpowiednie typy projektów programu Visual Studio. Rozpoznawano dziewięć wartości: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed i Native. Autor SDK może używać i ("+"), lub ("&#124;"), nie ("!") operatorów, aby dokładnie określić zakres typów projektów, które mają zastosowanie do SDK.

    WindowsAppContainer identyfikuje projekty [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] dla aplikacji.

8. SupportPrefer32Bit: Obsługiwane wartości to "True" i "False". Wartość domyślna to "Prawda". Jeśli wartość jest ustawiona na "False", MSBuild zwraca błąd dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projektów (lub ostrzeżenie dla projektów pulpitu), jeśli projekt, który odwołuje się do zestawu SDK ma Prefer32Bit włączone. Aby uzyskać więcej informacji na temat Prefer32Bit, zobacz [Strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) lub [Strona Kompilacja, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. ObsługiwaneArchitektury: Lista ograniczona średnikami architektury, które obsługuje zestaw SDK. MSBuild wyświetla ostrzeżenie, jeśli architektura docelowego SDK w projekcie zużywającym nie jest obsługiwana. Jeśli ten atrybut nie jest określony, MSBuild nigdy nie wyświetla tego typu ostrzeżenia.

10. SupportsMultipleVersions: Jeśli ten atrybut jest ustawiony na **Błąd** lub **Ostrzeżenie,** MSBuild wskazuje, że ten sam projekt nie może odwoływać się do wielu wersji tej samej rodziny zestawu SDK. Jeśli ten atrybut nie istnieje lub jest ustawiony na **Zezwalaj,** MSBuild nie wyświetla tego typu błędu lub ostrzeżenia.

11. AppX: Określa ścieżkę do pakietów aplikacji dla biblioteki składników systemu Windows na dysku. Ta wartość jest przekazywana do składnika rejestracji biblioteki składników systemu Windows podczas debugowania lokalnego. Konwencją nazewnictwa nazwy pliku jest * \<firma\<>.> produktu. \<> architektury. \<> konfiguracyjne. Wersja \<>.appx*. Konfiguracja i architektura są opcjonalne w nazwie atrybutu i wartości atrybutu, jeśli nie mają zastosowania do biblioteki składników systemu Windows. Ta wartość ma zastosowanie tylko do bibliotek składników systemu Windows.

12. CopyRedistToSubDirectory: Określa, gdzie pliki w *folderze \redist* powinny być kopiowane względem katalogu głównego pakietu aplikacji (czyli **lokalizacji pakietu** wybranego w Kreatorze tworzenia **pakietu aplikacji)** i katalogu głównego układu środowiska uruchomieniowego. Domyślną lokalizacją jest katalog główny pakietu aplikacji i układu **F5.**

13. DependsOn: Lista tożsamości SDK, które definiują SDK, od których zależy ten SDK. Ten atrybut jest wyświetlany w okienku szczegółów Menedżera odwołań.

14. MoreInfo: Adres URL strony sieci Web, który zapewnia pomoc i więcej informacji. Ta wartość jest używana w łączu Więcej informacji w prawym okienku Menedżera odwołań.

15. Typ rejestracji: Określa rejestrację WinMD w manifeście aplikacji i jest wymagany dla natywnego winmd, który ma bibliotekę DLL implementacji odpowiednika.

16. Odwołanie do pliku: Określono tylko dla tych odwołań, które zawierają formanty lub są natywnymi winmdami. Aby uzyskać informacje dotyczące określania, czy odwołanie zawiera formanty, zobacz [Określanie lokalizacji elementów przybornika](#ToolboxItems) poniżej.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Określanie lokalizacji elementów przybornika

**ToolBoxItems** element schematu *SDKManifest.xml* określa kategorię i lokalizację elementów przybornika w platformie i rozszerzenia SDK. Poniższe przykłady pokazują, jak określić różne lokalizacje. Dotyczy to odwołań do winmd lub biblioteki DLL.

1. Umieść formanty w kategorii domyślnej przybornika.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Umieść formanty pod określoną nazwą kategorii.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Umieszczaj formanty pod określonymi nazwami kategorii.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Umieść formanty w różnych nazwach kategorii w programie Blend i Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Wyliczaj określone formanty inaczej w blendu i programie Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Wyliczyć określone formanty i umieścić je w visual studio wspólnej ścieżki lub tylko w grupie Wszystkie formanty.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Wyliczanie określonych formantów i pokaż tylko określonego zestawu w ChooseItems bez ich w przyborniku.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Zobacz też

- [Instruktaż: Tworzenie sdk przy użyciu języka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Instruktaż: Tworzenie sdk przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
