---
title: Tworzenie Software Development Kit | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acad28e365c70a89c50b77e141e428468b9a6df2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109793"
---
# <a name="creating-a-software-development-kit"></a>Tworzenie zestawu SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw software development kit (SDK) to zbiór interfejsów API, którego można się odwoływać jako pojedynczy element w programie Visual Studio. **Menadżer odwołań** okno dialogowe wyświetla listę wszystkich zestawów SDK, które mają zastosowanie do projektu. Po dodaniu zestawu SDK do projektu interfejsach API dostępnych w programie Visual Studio.  
  
 Istnieją dwa rodzaje zestawów SDK:  
  
- Zestawy SDK platformy są wymagane składniki do tworzenia aplikacji dla platformy. Na przykład [!INCLUDE[win81](../includes/win81-md.md)] zestawu SDK jest wymagany do tworzenia [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.  
  
- Zestawy SDK rozszerzenia są opcjonalne składniki, rozszerzyć platformę usługi, które nie są wymagane do tworzenia aplikacji dla danej platformy.  
  
  W poniższych sekcjach opisano ogólne infrastruktury zestawów SDK oraz sposób tworzenia zestawu SDK platformy i zestawu SDK rozszerzenia.  
  
- [Zestawy SDK platformy](#PlatformSDKs)  
  
- [Zestawów SDK rozszerzeń](#ExtensionSDKs)  
  
## <a name="PlatformSDKs"></a> Zestawy SDK platformy  
 Zestawy SDK platformy są wymagane do tworzenia aplikacji dla platformy. Na przykład [!INCLUDE[win81](../includes/win81-md.md)] zestawu SDK jest wymagany do tworzenia aplikacji dla [!INCLUDE[win81](../includes/win81-md.md)].  
  
### <a name="installation"></a>Instalacja  
 Wszystkich zestawów SDK dla platformy, zostaną zainstalowane w kluczu HKLM\Software\Microsoft\Microsoft zestawów SDK\\\v [TPI] [TPV]\\ @InstallationFolder = [katalogu głównym zestawu SDK]. W związku z tym [!INCLUDE[win81](../includes/win81-md.md)] zestaw SDK został zainstalowany w kluczu HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Układ  
 Zestawy SDK platformy mają następujące układu:  
  
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
  
|Węzeł|Opis|  
|----------|-----------------|  
|Folder Odwołania|Zawiera pliki binarne, które zawierają interfejsy API, które mogą być kodowane względem. Te mogą obejmować pliki Windows metadanych (WinMD) lub zespołów.|  
|Folder czasu projektowania|Zawiera pliki, które są wymagane tylko w czasie wstępnej — uruchamianie/debugowanie. Mogą być dokumenty XML, bibliotek, nagłówków, pliki binarne czasu projektowania przybornika, program MSBuild artefaktów i tak dalej<br /><br /> Dokumenty XML najlepiej, jeśli zostanie umieszczony w folderze \DesignTime, ale dokumenty XML dla odwołania będą w dalszym ciągu być umieszczane obok pliku odwołania w programie Visual Studio. Na przykład dokumentu XML \References odwołanie\\[Konfiguracja]\\[arch]\sample.dll będzie \References\\[Konfiguracja]\\[arch]\sample.xml i zlokalizowaną wersję tego dokumentu zostanie \References\\[Konfiguracja]\\[arch]\\[locale]\sample.xml.|  
|Folder konfiguracji|Może to być tylko trzy foldery: debugowania, handel detaliczny i CommonConfiguration. Autorzy zestawu SDK można umieścić swoje pliki w obszarze CommonConfiguration, jeśli ten sam zestaw plików zestawu SDK powinno być używane niezależnie od konfiguracji, przeznaczony dla konsumentów zestawu SDK.|  
|Architektura folderu|Obsługiwana architektura folderu może istnieć. Program Visual Studio obsługuje następujące architektury: x86, x64, ARM i neutral. Uwaga: Mapuje Win32 x86 oraz AnyCPU mapuje neutralne.<br /><br /> Program MSBuild szuka wyłącznie w ramach \CommonConfiguration\neutral zestawów SDK platformy.|  
|SDKManifest.xml|W tym pliku opisano, jak Visual Studio należy używać zestawu SDK. Przyjrzyj się manifestu SDK dla [!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Właściwość DisplayName:** Wartość, która wyświetla przeglądarki obiektów na liście przeglądania.<br /><br /> **PlatformIdentity:** Istnienie tego atrybutu informuje program Visual Studio i MSBuild, zestaw SDK jest zestaw SDK platformy, a nie można skopiować odwołania dodane z niego lokalnie.<br /><br /> **TargetFramework:** Ten atrybut jest używany przez program Visual Studio, aby upewnić się, że tylko projekty tej samej struktury jako określoną przez wartość tego atrybutu mogą używać zestawu SDK.<br /><br /> **Brakuje MinVSVersion:** Ten atrybut jest używany przez program Visual Studio korzystać tylko zestawy SDK, które go dotyczą.<br /><br /> **Odwołanie:** Ten atrybut musi być określona dla te odwołania, które zawierają formanty. Informacje o sposobie określania, czy odwołanie zawiera kontrolki można znaleźć poniżej.|  
  
## <a name="ExtensionSDKs"></a> Zestawów SDK rozszerzeń  
 W poniższych sekcjach opisano, co należy zrobić, aby wdrożyć zestawu SDK rozszerzenia.  
  
### <a name="installation"></a>Instalacja  
 Zestawów SDK rozszerzeń można zainstalować dla określonego użytkownika lub dla wszystkich użytkowników bez określenia klucza rejestru. Aby zainstalować zestaw SDK dla wszystkich użytkowników, należy użyć następującej ścieżki:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Instalacja specyficzne dla użytkownika należy użyć następującej ścieżki:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Jeśli chcesz użyć innej lokalizacji, należy wykonać jedną z dwóch kwestii:  
  
1. Określ ją w kluczu rejestru:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     i dodaj podklucz (ustawienie domyślne), który ma wartość `<path to SDK><SDKName><SDKVersion>`.  
  
2. Dodaj właściwość MSBuild `SDKReferenceDirectoryRoot` do pliku projektu. Wartość tej właściwości jest średnikami lista o częściowej lub listę katalogów, w których znajdują się zestawów SDK rozszerzeń ma dotyczyć odwołanie.  
  
### <a name="installation-layout"></a>Układ instalacyjny  
 Zestawów SDK rozszerzeń ma następujące układ instalacyjny:  
  
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
  
1. \\< SDKName\>\\< SDKVersion\>: Nazwa i wersja rozszerzenia SDK jest tworzony na podstawie odpowiedniej nazwy folderów w ścieżce do katalogu głównego zestawu SDK. Program MSBuild używa tej tożsamości można znaleźć zestawu SDK na dysku, a program Visual Studio Wyświetla tej tożsamości w **właściwości** okna i **Menadżer odwołań** okna dialogowego.  
  
2. Folder odwołania: pliki binarne, które zawierają interfejsy API. Mogą to być pliki Windows metadanych (WinMD) lub zespołów.  
  
3. Folder redystrybucyjny: pliki, które są wymagane do debugowania/środowiska uruchomieniowego i należy pobrać spakowanych jako część aplikacji przez użytkownika. Wszystkie pliki binarne, powinny zostać umieszczone pod \redist\\< config\>\\< arch\>, i nazwami plików binarnych powinna mieć następujący format w celu zapewnienia unikatowości:  **\<firmy >.\< produktu >. \<cel >. \<rozszerzenia >**. Na przykład Microsoft.Cpp.Build.dll. Wszystkie pliki z nazwami, których może dojść do kolizji z nazwami plików od innych zestawów SDK (na przykład pliki javascript, css, pri, xaml, png i jpg) należy umieścić pod \redist\\< config\>\\< arch\> \\< sdkname\>\ z wyjątkiem plików, które są skojarzone z XAML kontrolki. Te pliki powinny być umieszczone pod \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4. Folder czasu projektowania: pliki, które są potrzebne w tylko wstępnej — uruchamianie/debugowanie raz i nie powinien spakowane w ramach aplikacji przez użytkownika. Mogą to być dokumenty XML, bibliotek, nagłówków, pliki binarne czasu projektowania przybornika, program MSBuild artefaktów i tak dalej. Dowolnego zestawu SDK, który jest przeznaczony do użycia przez natywnego projektu musi mieć *SDKName*plik .props. Na poniższym obrazie przedstawiono przykład tego typu pliku.  
  
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
  
     Dokumenty referencyjne XML są umieszczane obok pliku odwołania. Na przykład odwołanie do dokumentu XML **\References\\< config\>\\< arch\>\sample.dll** zestaw jest **\References\\ < config\>\\< arch\>\sample.xml**, i jest zlokalizowana wersja tego dokumentu **\References\\< config\>\\< arch\>\\< ustawień regionalnych\>\sample.xml**.  
  
5. Folder konfiguracji: trzy podfoldery: Debugowanie, detaliczna i CommonConfiguration. Autorzy zestawu SDK można umieścić swoje pliki w obszarze CommonConfiguration, gdy ten sam zestaw plików zestawu SDK powinno być używane niezależnie od konfiguracji docelowej przez konsumenta zestawu SDK.  
  
6. Architektura folderu: obsługiwane są następujące architektury: x86, x64, ARM i neutral. Mapuje Win32 x86 oraz AnyCPU mapuje neutralne.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 W tym pliku opisano, jak Visual Studio należy używać zestawu SDK. Oto przykład.  
  
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
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 Poniższa lista zawiera elementy pliku.  
  
1. Właściwość DisplayName: wartość która jest wyświetlana w Menedżerze odwołań, Eksploratora rozwiązań, przeglądarki obiektów i inne lokalizacje w interfejsie użytkownika dla programu Visual Studio.  
  
2. ProductFamilyName: Ogólny nazwa produktu zestawu SDK. Na przykład [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK nosi nazwę "Microsoft.WinJS.1.0" i "Microsoft.WinJS.2.0", które należą do tej samej rodziny SDK produktów z rodziny "Microsoft.WinJS". Ten atrybut umożliwia programu Visual Studio i MSBuild, nawiązać połączenie. Jeśli ten atrybut nie istnieje, nazwa zestawu SDK jest używana jako nazwa rodziny produktów.  
  
3. FrameworkIdentity: określa zależność, na co najmniej jedną bibliotekę składnika Windows, który wartość tego atrybutu są umieszczane w manifeście aplikacja odbierająca komunikaty. Ten atrybut ma zastosowanie tylko do bibliotek składnika Windows.  
  
4. TargetFramework: Określa zestawy SDK, które są dostępne w Menedżerze odwołań i przybornika. Jest to rozdzielana średnikami lista target framework monikerów, na przykład ".NET Framework, wersja = v2.0; .NET Framework, wersja = v4.5.1". Jeśli nie określono kilka wersji tej samej platformy docelowej, Menadżer odwołań używa najniższą określonej wersji w celu ich filtrowania. Na przykład jeśli ".NET Framework w wersji = v2.0; .NET Framework, wersja = v4.5.1" jest określony, będzie używać Menedżera odwołań ".NET Framework w wersji = v2.0". Jeśli profil framework określony element docelowy jest określona, tylko ten profil będzie służyć Menadżer odwołań w celu ich filtrowania. Na przykład, gdy "Silverlight, wersja = w wersji 4.0, profil = WindowsPhone" jest określona, filtr tylko profilem Windows Phone; Menadżer odwołań nie widzi zestawu SDK w Menedżerze odwołań do projektu przeznaczonego dla pełnej wersji programu Silverlight 4.0 Framework.  
  
5. Brakuje MinVSVersion: minimalna wersja programu Visual Studio.  
  
6. MaxPlatformVerson: Wersja platformy docelowej maksymalna powinna służyć do określania wersje platformy, na których zestaw SDK rozszerzenia nie będą działać. Na przykład element programu Microsoft Visual C++ Runtime Package v11.0 powinna się odwoływać tylko do projektów systemu Windows 8. W efekcie MaxPlatformVersion projektu systemu Windows 8 jest 8.0. Oznacza to, że Menadżer odwołań odfiltrowuje programu Microsoft Visual C++ Runtime Package dla projektu Windows 8.1 i MSBuild zgłasza błąd podczas [!INCLUDE[win81](../includes/win81-md.md)] projekt odwołuje się do niej. Uwaga: ten element jest obsługiwany począwszy od [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
7. AppliesTo: Określa zestawy SDK, które są dostępne w Menedżerze odwołań, określając odpowiednie typy projektu programu Visual Studio. Dziewięć wartości są rozpoznawane: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed, and Native. Tworzenie zestawu SDK można używać i ("+"), lub ("&#124;"), a nie ("!") operatory, aby określić zakres dokładnie typów projektów, które są stosowane do zestawu SDK.  
  
     WindowsAppContainer identyfikuje projektów dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.  
  
8. SupportPrefer32Bit: Obsługiwane wartości to "True" i "False". Wartość domyślna to "True". Jeśli wartość jest ustawiona na "False", program MSBuild zwraca błąd dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektów (lub ostrzegawczy dla projektów pulpitu) Jeśli projekt, który odwołuje się zestaw SDK ma włączone Prefer32Bit. Aby uzyskać więcej informacji na temat Prefer32Bit zobacz [Stroka kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) lub [strona kompilowania, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: podzielona średnikami lista architektury, które obsługuje zestaw SDK. Program MSBuild zostanie wyświetlone ostrzeżenie, jeśli docelowa architektura zestawu SDK w projekcie odbierająca komunikaty nie jest obsługiwane. Jeśli ten atrybut nie jest określony, program MSBuild nigdy nie wyświetla tego typu Ostrzeżenie.  
  
10. SupportsMultipleVersions: Jeśli ten atrybut jest ustawiony na **błąd** lub **ostrzeżenie**, MSBuild wskazuje, że wiele wersji tej samej rodziny zestawu SDK nie może odwoływać się tego samego projektu. Jeśli ten atrybut nie istnieje lub została ustawiona na **Zezwalaj**, MSBuild nie wyświetla tego rodzaju błąd lub ostrzeżenie.  
  
11. Pakiet AppX: Określa ścieżkę do pakietów aplikacji dla Windows biblioteki składników na dysku. Ta wartość jest przekazywany do składnika rejestracji biblioteki składników Windows podczas lokalnego debugowania. Konwencja nazewnictwa dla nazwy pliku jest  **\<firmy >.\< Produktu >. \<Architektury >. \<Konfiguracji >. \<Wersji > .appx**. Architektura i konfiguracyjnych są opcjonalne w nazwie atrybutu, a wartość atrybutu, jeśli nie odnoszą się do biblioteki składników Windows. Ta wartość ma zastosowanie tylko do bibliotek składnika Windows.  
  
12. CopyRedistToSubDirectory: Określa, gdzie względem katalogu głównego pakietu aplikacji, w którym powinny zostać skopiowane pliki w folderze \redist (czyli **lokalizacji pakietu** wybrane w kreatorze tworzenia pakietu aplikacji) i główny obiekt układu środowiska uruchomieniowego. Domyślną lokalizacją jest katalog główny pakietu aplikacji i układ F5.  
  
13. DependsOn: Lista tożsamości zestawu SDK, definiujące zestawy SDK, od których zależy ten zestaw SDK. Ten atrybut jest wyświetlana w okienku szczegółów Menedżera odwołań.  
  
14. MoreInfo: adres URL strony sieci web, która udostępnia pomoc i więcej informacji. Ta wartość jest używana w użyj łącza więcej informacji, w okienku po prawej stronie Menadżer odwołań.  
  
15. Typ rejestracji: Określa rejestracji WinMD w manifeście aplikacji i jest wymagana dla natywnych WinMD, mającej z implementacją odpowiednika biblioteki DLL.  
  
16. Odwołanie do pliku: określone dla tych odwołań, które zawierają kontrolki lub natywnych plików Winmd. Aby uzyskać informacje o sposobie określania, czy odwołanie zawiera formanty, zobacz [określając lokalizację elementów przybornika](#ToolboxItems) poniżej.  
  
## <a name="ToolboxItems"></a> Określanie lokalizacji elementów przybornika  
 Element ToolBoxItems schematu SDKManifest.xml określa kategorię i lokalizację elementów przybornika w platformę i zestawy SDK rozszerzenia. Następujące przykłady przedstawiają sposób określania różnych lokalizacjach. Ma to zastosowanie do odwołania WinMD i bibliotek DLL.  
  
1. Umieść formanty w kategorii domyślnego przybornika.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2. Umieść formanty w obszarze nazwy określonej kategorii.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3. Umieść formanty w obszarze nazwy określonej kategorii.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4. Umieść formanty w obszarze nazwy inną kategorię w Blend i Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5. Wyliczanie określonych kontrolek inaczej w programie Blend i Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6. Wyliczanie określonych kontrolek i umieść je w ścieżce wspólnej Visual Studio lub tylko grupy wszystkich kontrolek.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7. Wyliczanie określonych kontrolek i wyświetlić tylko określone w ChooseItems bez nich w przyborniku.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Przewodnik: Tworzenie za pomocą zestawu SDK C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
