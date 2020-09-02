---
title: Tworzenie zestawu Software Development Kit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 791400746247d71c06e133d10469132f38544b21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689993"
---
# <a name="creating-a-software-development-kit"></a>Tworzenie zestawu SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw SDK (Software Development Kit) to zbiór interfejsów API, które można odwołać jako pojedyncze elementy w programie Visual Studio. W oknie dialogowym **Menedżer odwołań** są wyświetlane wszystkie zestawy SDK, które są istotne dla projektu. Po dodaniu zestawu SDK do projektu interfejsy API są dostępne w programie Visual Studio.  
  
 Istnieją dwa typy zestawów SDK:  
  
- Zestawy SDK platformy są obowiązkowymi składnikami do tworzenia aplikacji dla platformy. Na przykład [!INCLUDE[win81](../includes/win81-md.md)] zestaw SDK jest wymagany do tworzenia [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.  
  
- Rozszerzenia SDK są opcjonalnymi składnikami, które rozszerzają platformę, ale nie są wymagane do tworzenia aplikacji dla tej platformy.  
  
  W poniższych sekcjach opisano ogólną infrastrukturę zestawów SDK oraz sposób tworzenia zestawu SDK platformy i rozszerzenia SDK.  
  
- [Zestawy SDK platformy](#PlatformSDKs)  
  
- [Zestawy SDK rozszerzenia](#ExtensionSDKs)  
  
## <a name="platform-sdks"></a><a name="PlatformSDKs"></a> Zestawy SDK platformy  
 Zestawy SDK platformy są wymagane do tworzenia aplikacji dla platformy. Na przykład [!INCLUDE[win81](../includes/win81-md.md)] zestaw SDK jest wymagany do tworzenia aplikacji dla programu [!INCLUDE[win81](../includes/win81-md.md)] .  
  
### <a name="installation"></a>Instalacja  
 Wszystkie zestawy SDK platformy zostaną zainstalowane w HKLM\Software\Microsoft\Microsoft SDK \\ [TPI] \v [TPV] \\ @InstallationFolder = [główny zestaw SDK]. W związku z tym [!INCLUDE[win81](../includes/win81-md.md)] zestaw SDK jest instalowany pod adresem HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Layout  
 Zestawy SDK platformy będą miały następujący układ:  
  
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
|Folder Odwołania|Zawiera pliki binarne, które zawierają interfejsy API, które można zakodować. Mogą to być pliki lub zestawy metadanych systemu Windows (WinMD).|  
|Folder DesignTime|Zawiera pliki, które są wymagane tylko w czasie przed uruchomieniem/debugowaniem. Mogą to być dokumenty XML, biblioteki, nagłówki, Przybornik plików binarnych czasu projektowania, artefakty programu MSBuild i tak dalej.<br /><br /> Dokumentacja XML zostałaby, najlepiej umieszczona w folderze \DesignTime, ale dokumentacja XML dla odwołań będzie nadal umieszczana obok pliku referencyjnego w programie Visual Studio. Na przykład dokument XML dla odwołania \References \\ [config] \\ [arch] \sample.dll będzie \References \\ [config] \\ [arch] \sample.xml, a zlokalizowana wersja tego dokumentu będzie \References \\ [config] \\ [arch] \\ [locale] \sample.xml.|  
|Folder konfiguracji|Może istnieć tylko trzy foldery: Debug, handel detaliczny i CommonConfiguration. Autorzy zestawu SDK mogą umieścić pliki w obszarze CommonConfiguration, jeśli ten sam zestaw plików zestawu SDK ma być używany, niezależnie od konfiguracji, która będzie celem odbiorcy zestawu SDK.|  
|Folder architektury|Może istnieć każdy obsługiwany folder architektury. Program Visual Studio obsługuje następujące architektury: x86, x64, ARM i neutralny. Uwaga: system Win32 jest mapowany na architekturę x86, a następnie jest mapowany na neutralną.<br /><br /> MSBuild sprawdza się tylko w obszarze \CommonConfiguration\neutral for Platform SDK.|  
|SDKManifest.xml|W tym pliku opisano, jak program Visual Studio powinien korzystać z zestawu SDK. Zapoznaj się z manifestem zestawu SDK dla [!INCLUDE[win81](../includes/win81-md.md)] :<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Nazwa wyświetlana:** Wartość, która Przeglądarka obiektów wyświetlana na liście Przeglądaj.<br /><br /> **PlatformIdentity:** Istnienie tego atrybutu nakazuje programowi Visual Studio i MSBuild, że zestaw SDK jest zestawem SDK platformy i że odwołania dodane z niego nie powinny zostać skopiowane lokalnie.<br /><br /> **TargetFramework:** Ten atrybut jest używany przez program Visual Studio, aby upewnić się, że tylko projekty, które są przeznaczone dla tych samych platform, jak określono w wartości tego atrybutu mogą korzystać z zestawu SDK.<br /><br /> **Brakuje MinVSVersion:** Ten atrybut jest używany przez program Visual Studio do korzystania tylko z zestawów SDK, które mają do nich zastosowanie.<br /><br /> **Dokumentacja:** Ten atrybut musi być określony tylko dla odwołań zawierających formanty. Aby uzyskać informacje na temat sposobu określania, czy odwołanie zawiera kontrolki, zobacz poniżej.|  
  
## <a name="extension-sdks"></a><a name="ExtensionSDKs"></a> Zestawy SDK rozszerzenia  
 W poniższych sekcjach opisano, co należy zrobić, aby wdrożyć zestaw SDK rozszerzenia.  
  
### <a name="installation"></a>Instalacja  
 Rozszerzenia SDK można zainstalować dla określonego użytkownika lub dla wszystkich użytkowników bez określania klucza rejestru. Aby zainstalować zestaw SDK dla wszystkich użytkowników, użyj następującej ścieżki:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 W przypadku instalacji specyficznej dla użytkownika należy użyć następującej ścieżki:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Jeśli chcesz użyć innej lokalizacji, musisz wykonać jedną z dwóch czynności:  
  
1. Określ ją w kluczu rejestru:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     i Dodaj podklucz (domyślny), który ma wartość `<path to SDK><SDKName><SDKVersion>` .  
  
2. Dodaj właściwość programu MSBuild `SDKReferenceDirectoryRoot` do pliku projektu. Wartość tej właściwości jest rozdzielaną średnikami listą katalogów, w których znajdują się zestawy SDK rozszerzenia, które chcesz odwołać.  
  
### <a name="installation-layout"></a>Układ instalacji  
 Zestawy SDK rozszerzeń mają następujący układ instalacji:  
  
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
  
1. \\<SDKName \> \\<SDKVersion \> : Nazwa i wersja rozszerzenia SDK są wyprowadzane z odpowiednich nazw folderów w ścieżce do katalogu głównego zestawu SDK. MSBuild używa tej tożsamości do znajdowania zestawu SDK na dysku, a program Visual Studio Wyświetla tę tożsamość w oknie **Właściwości** i w oknie dialogowym **Menedżer odwołań** .  
  
2. Folder References: pliki binarne, które zawierają interfejsy API. Mogą to być pliki lub zestawy metadanych systemu Windows (WinMD).  
  
3. Folder Redist: pliki, które są potrzebne do środowiska uruchomieniowego/debugowania, powinny być spakowane jako część aplikacji użytkownika. Wszystkie pliki binarne należy umieścić poniżej \redist \\<config \> \\<Arch \> , a nazwy binarne powinny mieć następujący format, aby zapewnić unikatowość: ** \<company> . \<product> \<purpose> \<extension> **... Na przykład Microsoft.Cpp.Build.dll. Wszystkie pliki o nazwach, które mogą koliduje z nazwami plików z innych zestawów SDK (na przykład JavaScript, CSS, pri, XAML, PNG i jpg), powinny być umieszczone poniżej \redist \\<config \> \\<Arch \> \\<SDKName \> \ z wyjątkiem plików, które są skojarzone z kontrolkami XAML. Pliki te powinny być umieszczone poniżej \redist \\<config \> \\<Arch \> \\<ComponentName \> \\ .  
  
4. Folder DesignTime: pliki, które są wymagane tylko w czasie przed uruchomieniem/debugowaniem i nie powinny być spakowane jako część aplikacji użytkownika. Mogą to być dokumenty XML, biblioteki, nagłówki, Przybornik plików binarnych czasu projektowania, artefakty programu MSBuild i tak dalej. Każdy zestaw SDK, który jest przeznaczony do użycia przez projekt natywny, musi mieć plik *SDKName*. props. Poniżej przedstawiono przykład tego typu pliku.  
  
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
  
     Dokumenty odwołań XML są umieszczane obok pliku referencyjnego. Na przykład dokument referencyjny XML dla zestawu **\References \\<config \> \\<Arch \>\sample.dll** jest **\References \\<konfiguracji \> \\<Arch \>\sample.xml**, a zlokalizowana wersja tego dokumentu to **\References \\<konfiguracja \> \\<Arch \> \\<ustawienia regionalne \>\sample.xml**.  
  
5. Folder konfiguracji: trzy podfoldery: debugowanie, sprzedaż detaliczna i CommonConfiguration. Autorzy zestawu SDK mogą umieszczać swoje pliki w CommonConfiguration, gdy ten sam zestaw plików zestawu SDK powinien być używany, niezależnie od konfiguracji wskazywanej przez klienta zestawu SDK.  
  
6. Folder architektury: obsługiwane są następujące architektury: x86, x64, ARM, neutralna. System Win32 jest mapowany na architekturę x86 i jest mapowany na neutralną.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 W tym pliku opisano, jak program Visual Studio powinien korzystać z zestawu SDK. Poniżej przedstawiono przykład.  
  
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
  
 Poniższa lista zawiera elementy pliku.  
  
1. DisplayName: wartość wyświetlana w Menedżerze odwołań, Eksplorator rozwiązań, Przeglądarka obiektów i innych lokalizacjach w interfejsie użytkownika programu Visual Studio.  
  
2. ProductFamilyName: ogólna nazwa produktu SDK. Na przykład [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] zestaw SDK nosi nazwę "Microsoft. WinJS. 1.0" i "Microsoft. WinJS. 2.0", który należy do tej samej rodziny produktów zestawu SDK "Microsoft. WinJS". Ten atrybut umożliwia programom Visual Studio i MSBuild nawiązanie tego połączenia. Jeśli ten atrybut nie istnieje, nazwa zestawu SDK jest używana jako nazwa rodziny produktów.  
  
3. FrameworkIdentity: określa zależność od co najmniej jednej biblioteki składników systemu Windows wartość tego atrybutu jest umieszczana w manifeście aplikacji zużywanej. Ten atrybut ma zastosowanie tylko do bibliotek składników systemu Windows.  
  
4. TargetFramework: określa zestawy SDK, które są dostępne w Menedżerze odwołań i przyborniku. Jest to rozdzielana średnikami lista monikerów platformy docelowej, na przykład ".NET Framework, Version = v 2.0, .NET Framework, Version = v 4.5.1". Jeśli określono kilka wersji tej samej platformy docelowej, Menedżer odwołań używa najniższej określonej wersji do celów filtrowania. Na przykład jeśli określono ".NET Framework, Version = v 2.0; .NET Framework, Version = v 4.5.1", Menedżer odwołań będzie używać ".NET Framework, Version = v 2.0". Jeśli określony jest konkretny Profil platformy docelowej, tylko ten profil będzie używany przez Menedżera odwołań do celów filtrowania. Na przykład jeśli określono "Silverlight, Version = v 4.0, profil = WindowsPhone", Menedżer odwołań filtruje tylko dla profilu Windows Phone; projekt przeznaczony dla pełnej struktury Silverlight 4,0 nie widzi zestawu SDK w Menedżerze odwołań.  
  
5. Brakuje MinVSVersion: minimalna wersja programu Visual Studio.  
  
6. MaxPlatformVerson: Maksymalna wersja platformy docelowej powinna być używana do określania wersji platformy, w których zestaw SDK rozszerzenia nie będzie działać. Na przykład pakiet środowiska uruchomieniowego Microsoft Visual C++ v 11.0 powinien być przywoływany tylko przez projekty systemu Windows 8. W tym przypadku MaxPlatformVersion projektu systemu Windows 8 to 8,0. Oznacza to, że Menedżer odwołań filtruje pakiet środowiska uruchomieniowego Microsoft Visual C++ dla projektu Windows 8.1, a MSBuild zgłasza błąd, gdy [!INCLUDE[win81](../includes/win81-md.md)] projekt odwołuje się do niego. Uwaga: ten element jest obsługiwany, rozpoczynając od [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] .  
  
7. AppliesTo: określa zestawy SDK, które są dostępne w Menedżerze odwołań przez określenie odpowiednich typów projektów programu Visual Studio. Są rozpoznawane dziewięć wartości: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, zarządzane i natywne. Autor zestawu SDK może używać i ("+") lub ("&#124;"), a nie ("!") Operatory, aby określić dokładnie zakres typów projektów, które są stosowane do zestawu SDK.  
  
     WindowsAppContainer identyfikuje projekty dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji.  
  
8. SupportPrefer32Bit: obsługiwane wartości to "true" i "false". Wartość domyślna to "true". Jeśli wartość jest równa "false", MSBuild zwraca błąd dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektów (lub ostrzeżenie dla projektów klasycznych), jeśli projekt, który odwołuje się do zestawu SDK, ma włączone Prefer32Bit. Aby uzyskać więcej informacji na temat Prefer32Bit, zobacz [stronę Kompilacja, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) lub [stronę kompilacji, projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: rozdzielana średnikami lista architektur obsługiwanych przez zestaw SDK. Program MSBuild wyświetla ostrzeżenie, jeśli dostosowanej architektury zestawu SDK w projekcie zużywanym nie jest obsługiwana. Jeśli ten atrybut nie jest określony, MSBuild nigdy nie wyświetla tego typu ostrzeżenia.  
  
10. SupportsMultipleVersions: Jeśli ten atrybut ma wartość **Error** lub **Warning**, MSBuild wskazuje, że ten sam projekt nie może odwoływać się do wielu wersji tej samej rodziny zestawów SDK. Jeśli ten atrybut nie istnieje lub jest ustawiony na **Zezwalaj**, MSBuild nie wyświetla tego typu błędu ani Ostrzeżenia.  
  
11. AppX: Określa ścieżkę do pakietów aplikacji dla biblioteki składników systemu Windows na dysku. Ta wartość jest przenoszona do składnika rejestracji biblioteki składników systemu Windows podczas lokalnego debugowania. Konwencja nazewnictwa dla nazwy pliku to ** \<Company> . \<Product> . \<Architecture> . \<Configuration> \<Version> . APPX**. Konfiguracja i architektura są opcjonalne w nazwie atrybutu i wartości atrybutu, jeśli nie mają zastosowania do biblioteki składników systemu Windows. Ta wartość ma zastosowanie tylko do bibliotek składników systemu Windows.  
  
12. CopyRedistToSubDirectory: określa, gdzie należy skopiować pliki w folderze \redist względem katalogu głównego pakietu aplikacji (czyli **lokalizacji pakietu** wybranej w Kreatorze tworzenia pakietu aplikacji) i katalogu głównego układu środowiska uruchomieniowego. Domyślną lokalizacją jest katalog główny pakietu aplikacji i układu F5.  
  
13. DependsOn: Lista tożsamości zestawu SDK, które definiują zestawy SDK, od których zależy ten zestaw SDK. Ten atrybut jest wyświetlany w okienku szczegółów w Menedżerze odwołań.  
  
14. MoreInfo: adres URL strony sieci Web, która zawiera pomoc i więcej informacji. Ta wartość jest używana w linku więcej informacji w prawym okienku w Menedżerze odwołań.  
  
15. Typ rejestracji: określa rejestrację WinMD w manifeście aplikacji i jest wymagana dla natywnej WinMD, która ma odpowiednią bibliotekę DLL implementacji.  
  
16. Odwołanie do pliku: określone tylko dla tych odwołań, które zawierają kontrolki lub natywnych WinMD. Aby uzyskać informacje na temat sposobu określania, czy odwołanie zawiera kontrolki, zobacz [Określanie lokalizacji elementów przybornika](#ToolboxItems) poniżej.  
  
## <a name="specifying-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> Określanie lokalizacji elementów przybornika  
 Element ToolBoxItems schematu SDKManifest.xml Określa kategorię i lokalizację elementów przybornika w zestawach SDK platformy i rozszerzenia. W poniższych przykładach pokazano, jak określić różne lokalizacje. Ma to zastosowanie do odwołań WinMD lub bibliotek DLL.  
  
1. Umieść formanty w domyślnej kategorii przybornika.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2. Umieść kontrolki pod nazwą określonej kategorii.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3. Umieść kontrolki pod określonymi nazwami kategorii.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4. Umieść kontrolki pod różnymi nazwami kategorii w programie Blend i Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5. Wyliczanie określonych kontrolek różni się w programie Blend i Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6. Wylicz określone kontrolki i umieść je w ramach wspólnej ścieżki programu Visual Studio lub tylko w grupie wszystkie kontrolki.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7. Wyliczanie określonych kontrolek i wyświetlanie tylko określonego zestawu w ChooseItems bez ich w przyborniku.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Przewodnik: Tworzenie zestawu SDK przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
