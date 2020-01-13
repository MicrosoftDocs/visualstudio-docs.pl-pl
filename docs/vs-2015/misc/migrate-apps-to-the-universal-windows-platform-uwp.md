---
title: Migrowanie aplikacji do platforma uniwersalna systemu Windows (platformy UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60951091914474f07f19672799fb59c8b2d0aa56
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919142"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migracja aplikacji na platformę uniwersalną systemu Windows
Wprowadź niezbędne zmiany ręczne do istniejących plików projektu dla aplikacji ze sklepu Windows 8,1, aplikacji Windows Phone 8,1 lub uniwersalnych aplikacji systemu Windows utworzonych przy użyciu programu Visual Studio 2015 RC, aby mogły być używane w programie Visual Studio 2015 RTM. (Jeśli masz aplikację uniwersalną Windows 8.1 z projektem aplikacji systemu Windows i projektem Windows Phone, musisz postępować zgodnie z instrukcjami, aby zmigrować każdy projekt).

 Za pomocą platforma uniwersalna systemu Windows teraz aplikacja jest docelowa do co najmniej jednej rodziny urządzeń. Jeśli chcesz uzyskać więcej informacji na temat uniwersalnych aplikacji systemu Windows, zapoznaj się z tym [przewodnikiem](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx)dotyczącym platformy.

- [Przeprowadź migrację istniejących C#aplikacji/VB ze sklepu Windows 8,1 lub Windows Phone 8,1](#MigrateCSharp) , aby korzystać z platforma uniwersalna systemu Windows.

- [Migruj istniejące C++ aplikacje ze sklepu Windows 8,1 lub Windows Phone 8,1](#MigrateCPlusPlus) , aby korzystać z platforma uniwersalna systemu Windows.

- [Zmiany wymagane przez istniejące aplikacje uniwersalne systemu Windows utworzone za pomocą programu Visual Studio 2015 RC](#PreviousVersions).

- [Zmiany wymagane dla istniejących projektów testów jednostkowych dla aplikacji uniwersalnych systemu Windows utworzonych za pomocą programu Visual Studio 2015 RC](#MigrateUnitTest).

  Jeśli nie chcesz wprowadzać wszystkich tych zmian, Dowiedz się, jak [przenieść istniejące aplikacje](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) do nowego projektu uniwersalnego systemu Windows.

## <a name="MigrateCSharp"></a>Migruj aplikacje C#/VB ze sklepu Windows 8,1 lub Windows Phone 8,1, aby użyć platforma uniwersalna systemu Windows

#### <a name="migrate-your-cvb-project-files"></a>Migrowanie C#plików projektu/VB

1. Aby znaleźć zainstalowaną platforma uniwersalna systemu Windows, otwórz ten folder: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Zawiera listę folderów dla każdej zainstalowanej platforma uniwersalna systemu Windows. Nazwa folderu jest zainstalowaną platforma uniwersalna systemu Windows wersją. Na przykład na tym urządzeniu z systemem Windows 10 jest zainstalowana wersja 10.0.10240.0 platforma uniwersalna systemu Windows.

     ![Otwórz folder, aby wyświetlić zainstalowane wersje](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Można zainstalować więcej niż jedną wersję platforma uniwersalna systemu Windows. Zalecamy użycie najnowszej wersji aplikacji.

2. Korzystając z Eksploratora plików, przejdź do folderu, w którym przechowywany jest projekt platformy UWP. Utwórz plik JSON w tym folderze. Nazwij plik: Project. JSON, a następnie Dodaj do tego pliku następującą zawartość:

    ```json
    {
      "dependencies": {
        "Microsoft.ApplicationInsights": "1.0.0",
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
      },
      "frameworks": {
        "uap10.0": {}
      },
      "runtimes": {
        "win10-arm": {},
        "win10-arm-aot": {},
        "win10-x86": {},
        "win10-x86-aot": {},
        "win10-x64": {},
        "win10-x64-aot": {}
      }
    }

    ```

3. Utwórz plik o nazwie Default. Rd. XML z następującą zawartością. Jeśli masz projekt VB, Dodaj ten plik do katalogu my Project dla projektu. Jeśli masz C# projekt, Dodaj ten plik do katalogu właściwości dla projektu.

    ```xml
    <?xml version="1.0"?>
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->
    <Assembly Dynamic="Required All" Name="*Application*"/>
    <!-- Add your application specific runtime directives here. -->
    </Application></Directives>
    ```

4. Otwórz rozwiązanie, które zawiera istniejącą aplikację ze sklepu Windows 8,1 lub aplikację Windows Phone 8,1 w programie Visual Studio.

5. Kliknij prawym przyciskiem myszy istniejący projekt dla aplikacji w Eksplorator rozwiązań, a następnie wybierz polecenie **Zwolnij projekt**. Po usunięciu projektu ponownie kliknij prawym przyciskiem myszy plik projektu i wybierz polecenie Edytuj plik. csproj lub. vbproj.

     ![Kliknij prawym przyciskiem myszy projekt i wybierz polecenie Edytuj](../misc/media/uap-editproject.png "UAP_EditProject")

6. Znajdź \<Właściwość > element, który zawiera \<elementu > TargetPlatformVersion o wartości 8,1. Wykonaj następujące kroki dla tego \<Właściwość > element:

    1. Ustaw wartość \<platformy >, aby: **x86**.

    2. Dodaj element \<TargetPlatformIdentifier > i ustaw jego wartość na: **UAP**.

    3. Zmień istniejącą wartość elementu \<TargetPlatformVersion > na wartość zainstalowanej platforma uniwersalna systemu Windows wersji. Dodaj również \<elementu > element targetplatformminversion i nadaj mu tę samą wartość.

    4. Zmień wartość \<elementu > MinimumVisualStudioVersion na: **14**.

    5. Zastąp element \<ProjectTypeGuids >, jak pokazano poniżej:

         Dla języka C#:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         Dla języka VB:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Dodaj element \<EnableDotNetNativeCompatibleProfile > i ustaw jego wartość na: **true**.

    7. Domyślna Skala zasobów dla aplikacji uniwersalnych systemu Windows to 200. Jeśli projekt zawiera zasoby, które nie są skalowane o 200, należy dodać element \<UapDefaultAssetScale > z wartością skali zasobów do tej właściwości. Dowiedz się więcej o [zasobach i skalowaniu](https://msdn.microsoft.com/library/jj679352.aspx).

         Teraz element \<właściwości > powinien wyglądać podobnie do tego przykładu:

        ```xml
        <PropertyGroup>
            …
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

7. Zastąp wszystkie wystąpienia 12,0 z 14,0, aby odzwierciedlić używaną wersję programu Visual Studio. Podobne wystąpienia:

    ```xml
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

    ```
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">
        <VisualStudioVersion>14.0</VisualStudioVersion>
    ```

8. Znajdź \<właściwości > elementy, które są skonfigurowane dla platformy AnyCPU jako część atrybutu warunku. Usuń te elementy i wszystkie ich elementy podrzędne. Program AnyCPU nie jest obsługiwany w przypadku aplikacji systemu Windows 10 w programie Visual Studio 2015. Na przykład należy usunąć \<właściwości > elementy takie jak te:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
    ```

9. Dla każdego pozostałego elementu \<właściwości >, sprawdź, czy element ma atrybut Condition z konfiguracją wydania. Jeśli tak, ale nie zawiera elementu \<UseDotNetNativeToolchain >, Dodaj go. Dla elementu \<UseDotNetNativeToolchain > Ustaw wartość true, np.:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">
        <OutputPath>bin\x64\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <Optimize>true</Optimize>
        <NoWarn>;2008</NoWarn>
        <DebugType>pdbonly</DebugType>
        <PlatformTarget>x64</PlatformTarget>
        <UseVSHostingProcess>false</UseVSHostingProcess>
        <ErrorReport>prompt</ErrorReport>
        <Prefer32Bit>true</Prefer32Bit>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

10. Tylko w przypadku projektów Windows Phone, Usuń element > Właściwości \<, który zawiera element \<TargetPlatformIdentifier > z wartością WindowsPhoneApp. Usuń także wszystkie elementy podrzędne tego elementu:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. Znajdź element \<Item >, który zawiera element \<AppxManifest >. Dodaj następujący \<none > elementu jako element podrzędny elementu \<elementu >:

    ```xml
    <None Include="project.json" />
    ```

12. Znajdź element \<Item >, który zawiera inne zasoby, które są dodawane do projektu, takie jak pliki logo. png (\<Content include = "Assets\Logo.scale-100.png"/>). Dodaj następujący \<Content > elementu podrzędnego do tego elementu \<elementu >:

     **Dla C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **Dla języka VB:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. Znajdź element \<Item >, który zawiera \<odwołanie > elementów podrzędnych do pakietów NuGet. Zanotuj używane pakiety NuGet, ponieważ trzeba będzie pobrać je za pomocą Menedżera pakietów NuGet po ponownym załadowaniu projektu. Usuń ten \<element > wraz z jego elementami podrzędnymi. Na przykład projekt platformy UWP może mieć następujące pakiety NuGet, które muszą zostać usunięte:

    ```xml
    <ItemGroup>
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
          <Private>True</Private>
        </Reference>
      </ItemGroup>
    ```

14. Zapisz zmiany.

15. Zamknij plik. csproj lub. vbproj.

16. Kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie Załaduj ponownie projekt z menu kontekstowego. Wszystkie pliki w projekcie powinny teraz być wyświetlane w Eksplorator rozwiązań.

17. Użyj Menedżera NuGet do dodania pakietów usuniętych w poprzednim kroku.

     Teraz musisz postępować zgodnie z instrukcjami, aby [zaktualizować pliki manifestu pakietu](#PackageManifest) dla wszystkich projektów Windows Store 8,1 lub Windows Phone 8,1.

## <a name="MigrateCPlusPlus"></a>Migruj aplikacje C++ ze sklepu Windows 8,1 lub Windows Phone 8,1, aby użyć platforma uniwersalna systemu Windows

#### <a name="migrate-your-c-project-files"></a>Migrowanie C++ plików projektu

1. Aby znaleźć zainstalowaną platforma uniwersalna systemu Windows, otwórz ten folder: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Zawiera listę folderów dla każdej zainstalowanej platforma uniwersalna systemu Windows. Nazwa folderu jest zainstalowaną platforma uniwersalna systemu Windows wersją. Na przykład na tym urządzeniu z systemem Windows 10 jest zainstalowana wersja 10.0.10240.0 platforma uniwersalna systemu Windows.

     ![Otwórz folder, aby wyświetlić zainstalowane wersje](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Można zainstalować więcej niż jedną wersję platforma uniwersalna systemu Windows. Zalecamy użycie najnowszej wersji aplikacji.

2. Otwórz rozwiązanie, które zawiera istniejącą C++ aplikację ze sklepu Windows 8,1 lub aplikację Windows Phone 8,1 w programie Visual Studio.

     Kliknij prawym przyciskiem myszy istniejący projekt w Eksploratorze rozwiązań, a następnie wybierz polecenie **Zwolnij projekt**. Po usunięciu projektu ponownie kliknij prawym przyciskiem myszy plik projektu i wybierz polecenie Edytuj plik. vcxproj.

     ![Kliknij&#45;prawym przyciskiem myszy plik projektu i wybierz polecenie Edytuj](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. Znajdź \<Właściwość > element, który zawiera \<elementu > ApplicationTypeRevision o wartości 8,1. Wykonaj następujące kroki dla tego \<Właściwość > element:

    1. Dodaj element \<WindowsTargetPlatformVersion > i element \<WindowsTargetPlatformMinVersion > i nadaj im wartość zainstalowanej wersji platforma uniwersalna systemu Windows.

    2. Zaktualizuj wartość elementu ApplicationTypeRevision z 8,1 do 10,0.

    3. Zmień wartość \<elementu > MinimumVisualStudioVersion na: 14.

    4. Dodaj element \<EnableDotNetNativeCompatibleProfile > i ustaw jego wartość na: true.

    5. Domyślna Skala zasobów dla aplikacji uniwersalnych systemu Windows to 200. Jeśli projekt zawiera zasoby, które nie są skalowane o 200, należy dodać element \<UapDefaultAssetScale > z wartością skali zasobów do tej właściwości. Dowiedz się więcej o [zasobach i skalowaniu](https://msdn.microsoft.com/library/jj679352.aspx).

    6. W przypadku projektów Windows Phone należy zmienić wartość \<ApplicationType > z Windows Phone na Sklep Windows.

         Teraz element \<właściwości > powinien wyglądać podobnie do tego przykładu:

        ```xml
        <PropertyGroup>
            …
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
             <ApplicationType>Windows Store</ApplicationType>
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

4. Zmień wszystkie wystąpienia elementu \<PlatformToolset >, aby miał wartość wersji 140. Na przykład:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. Dla każdego pozostałego elementu \<właściwości >, sprawdź, czy element ma atrybut Condition z konfiguracją wydania. Jeśli tak, ale nie zawiera elementu \<UseDotNetNativeToolchain >, Dodaj go. Dla elementu \<UseDotNetNativeToolchain > Ustaw wartość true, np.:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

6. Zapisz zmiany. Następnie zamknij plik projektu.

7. Kliknij prawym przyciskiem myszy plik projektu w Eksplorator rozwiązań, a następnie wybierz polecenie Załaduj ponownie projekt z menu kontekstowego. Wszystkie pliki w projekcie powinny teraz być wyświetlane w Eksplorator rozwiązań.

     Teraz musisz postępować zgodnie z instrukcjami, aby [zaktualizować pliki manifestu pakietu](#PackageManifest) dla wszystkich projektów Windows Store 8,1 lub Windows Phone 8,1.

## <a name="PackageManifest"></a>Aktualizowanie pliku manifestu pakietu dla wszystkich projektów sklepu Windows 8,1 lub Windows Phone 8,1
 Należy zaktualizować plik manifestu pakietu dla każdego projektu w rozwiązaniu.

#### <a name="update-your-package-manifest-file"></a>Aktualizowanie pliku manifestu pakietu

1. Otwórz plik Package. appxmanifest w projekcie. Musisz edytować plik Package. AppxManifest dla każdego ze sklepu Windows i projektów Windows Phone.

2. Należy zaktualizować pakiet \<> elementu z nowymi schematami opartymi na istniejącym typie projektu. Najpierw usuń poniższe schematy w zależności od tego, czy masz projekt Windows Store czy Windows Phone.

    **Stary projekt dla Sklepu Windows:** Pakiet \<> elementu będzie wyglądać podobnie do tego.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **Stary projekt Windows Phone:** Pakiet \<> elementu będzie wyglądać podobnie do tego.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **Nowość dla platforma uniwersalna systemu Windows:** Dodaj poniższe schematy do > elementu \<pakietu. Usuń wszystkie skojarzone prefiksy identyfikatorów przestrzeni nazw z elementów dla właśnie usuniętych schematów. Zaktualizuj Właściwość IgnorableNamespaces do: UAP MP. Nowy pakiet \<> powinien wyglądać podobnie do tego.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Dodaj \<zależności > elementu podrzędnego do elementu > pakietu \<. Następnie Dodaj element podrzędny \<Targetdevicefamily elementu > do tej \<zależności > elementu z atrybutami Name, MinVersion i MaxVersionTested. Nadaj nazwę atrybutowi Value: Windows. Universal. Nadaj MinVersion i MaxVersionTested wartość zainstalowanej wersji platforma uniwersalna systemu Windows. Ten element powinien wyglądać podobnie do tego:

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **Tylko dla Sklepu Windows:** Należy dodać element podrzędny \<MP: PhoneIdentity > do elementu > pakietu \<. Dodaj atrybut PhoneProductId i atrybut PhonePublisherId. Ustaw PhoneProductId tak, aby miała taką samą wartość jak atrybut Name w elemencie \<Identity >. Ustaw wartość PhonePublishedId na: 00000000-0000-0000-0000-000000000000. Jak to:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Znajdź element \<wstępnie wymaganych elementów > i Usuń ten element oraz wszystkie elementy podrzędne, które ma.

6. Dodaj przestrzeń nazw **UAP** do \<następujących elementów > zasobów: skala, DXFeatureLevel. Na przykład:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. Dodaj przestrzeń nazw **UAP** do następującej \<możliwości > elementy: DocumentsLibrary, PicturesLibrary, VideosLibrary, MusicLibrary, EnterpriseAuthentication, funkcję sharedusercertificates, removableStorage, terminy i kontakty. Na przykład:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. Dodaj przestrzeń nazw **UAP** do elementu \<VisualElements > i wszystkich jego elementów podrzędnych. Na przykład:

   ```xml
   <uap:VisualElements
       DisplayName="My WWA App"
       Square150x150Logo="images/150x150.png"
       Square44x44Logo="images/44x44.png"
       Description="My WWA App"
       BackgroundColor="#777777">
     <uap:SplashScreen Image="images/splash.png"/>
   </uap:VisualElements>

   ```

    **Dotyczy tylko sklepu Windows:** Zmieniono nazwy rozmiarów kafelków. Zmień atrybuty w elemencie \<VisualElements >, aby odzwierciedlały nowe zbieżne rozmiary kafelków. 70x70 zostaje 71x71, a 30x30 zostanie 44x44.

    **Stary:** nazwy rozmiarów kafelków

   ```xml
   <m2:VisualElements
       …
       Square30x30Logo="Assets\SmallLogo.png"
       …>
    <m2:DefaultTile
         …
         Square70x70Logo="images/70x70.png">
   </m2:VisualElements>

   ```

    **Nowość:** nazwy rozmiarów kafelków

   ```xml
   <uap:VisualElements
       …
       Square44x44Logo="Assets\SmallLogo.png"
       …>
    <uap:DefaultTile
         …
         Square71x71Logo="images/70x70.png">
   </uap:VisualElements>

   ```

9. Dodaj przestrzeń nazw **UAP** do > \<ApplicationContentUriRules i wszystkich jej elementów podrzędnych. Na przykład:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Dodaj przestrzeń nazw **UAP** do następującego rozszerzenia \<> elementy i wszystkie jego elementy podrzędne: Windows. accountPictureProvide, Windows. alarm, Windows. appointmentsProvider Windows. autoPlayContent, Windows. autoPlayDevice, Windows. cachedFileUpdate, Windows. cameraSettings, Windows. fileOpenPicker, Windows. fileTypeAssociation, Windows. fileSavePicke, Windows. lockScreenCall, Windows. printTaskSettings, Windows. Protocol, Windows. Search, Windows. shareTarget. Na przykład:

    ```xml
    <Extensions>
      <uap:Extension Category="windows.alarm"/>
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>
      <uap:Extension Category="windows.protocol">
        <uap:Protocol Name="mailto" DesiredView="useHalf">
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>
        </uap:Protocol>
      </uap:Extension>
    </Extensions>

    ```

11. Dodaj przestrzeń nazw **UAP** do zadań w tle typu chatMessageNotification. Na przykład:

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
     <BackgroundTasks ServerName="MyBackgroundTasks">
        <uap:Task Type="chatMessageNotification"/>
      </BackgroundTasks>
    </Extension>

    ```

12. Zmień zależności struktury. Dodaj nazwę wydawcy do wszystkich \<PackageDependency > elementów i określ MinVersion, jeśli nie została jeszcze określona.

     **Stary:** \<PackageDependency > elementu

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **New:** \<PackageDependency > element

    ```xml
    <Dependencies>
     <PackageDependency
          Name="Microsoft.VCLibs.120.00"
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
          MinVersion="12.0.30113.0" />
    </Dependencies>

    ```

     Użyj odpowiednich wartości wydawcy i MinVersion dla rzeczywistej platformy, z której korzystasz. Należy pamiętać, że te nazwy mogą ulec zmianie w systemie Windows 10.

13. Zastąp zadania typu gattCharacteristicNotification i rfcommConnection w tle typem zadania Bluetooth. Na przykład:

     **STARSZE**

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
                <Task Type="rfcommConnection"/>
               <Task Type="gattCharacteristicNotification"/>
    </BackgroundTasks>
    </Extension>
    ```

     **Nowy:** Z typem zadania Bluetooth.

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
               <Task Type="bluetooth"/>
    </BackgroundTasks>
    </Extension>
    ```

14. Zastąp możliwości urządzeń Bluetooth Bluetooth. RFCOMM i Bluetooth. genericAttributeProfile za pomocą ogólnej funkcji Bluetooth. Na przykład:

     **STARSZE**

    ```xml
    <Capabilities>
      <m2:DeviceCapability Name="bluetooth.rfcomm">
        <m2:Device Id="any">
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>
        </m2:Device>
      </m2:DeviceCapability>
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">
        <m2:Device Id="any">
         <m2:Function Type="name:heartRate"/>
        </m2:Device>
      </m2:DeviceCapability>
    </Capabilities>
    ```

     **Nowy:** Zastąpiono ogólną funkcją Bluetooth.

    ```xml
    <Capabilities>
      <uap:DeviceCapability Name="bluetooth"/>
    </Capabilities>

    ```

15. Usuń wszystkie elementy przestarzałe.

    1. Te atrybuty dla \<VisualElements > są przestarzałe i powinny zostać usunięte:

       - Atrybuty \<VisualElements >: ForegroundText, ToastCapable

       - \<DefaultTile > atrybut DefaultSize

       - Element \<ApplicationView >

         Na przykład:

       ```xml
       <m2:VisualElements
           …
           ForegroundText="dark"
           ToastCapable="true">
       <m2:DefaultTile DefaultSize="square150x150Logo"/>
         <m2:ApplicationView MinWidth="width320"/>
       </m2:VisualElements>

       ```

    2. Usuń rozszerzenia Windows. Contact i Windows. contactPicker oraz wszystkie elementy w ramach tych rozszerzeń.

16. Zapisz plik Package. appxmanifest. Następnie zamknij program Visual Studio.

17. Aby można było ponownie otworzyć rozwiązanie, należy usunąć niektóre ukryte pliki.

    1. Otwórz Eksploratora plików, kliknij przycisk **Widok** na pasku narzędzi i wybierz pozycję **elementy ukryte** i **rozszerzenia nazw plików**. Otwórz ten folder na maszynie: \<ścieżka do lokalizacji > rozwiązania\\. vs\\{nazwa projektu} \v14. Jeśli istnieje plik z rozszerzeniem. suo, usuń go.

    2. Teraz wróć do folderu, w którym znajduje się Twoje rozwiązanie. Otwórz wszystkie foldery dla projektów istniejących w rozwiązaniu. Jeśli plik w dowolnym z tych folderów projektu ma rozszerzenie. csproj. user lub. vbproj. User, usuń go.

         Teraz możesz ponownie otworzyć rozwiązanie w programie Visual Studio. Możesz przystąpić do tworzenia kodu, kompilowania i debugowania aplikacji przy użyciu platforma uniwersalna systemu Windows.

         Dowiedz się, jak [dostosować kod](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) , aby skorzystać z nowości w platforma uniwersalna systemu Windows.

## <a name="PreviousVersions"></a>Zmiany wymagane przez istniejące aplikacje uniwersalne systemu Windows utworzone za pomocą programu Visual Studio 2015 RC
 Jeśli aplikacje uniwersalne systemu Windows 10 zostały utworzone za pomocą programu Visual Studio 2015 RC, należy przekierować projekt, aby użyć wersji platforma uniwersalna systemu Windows zainstalowanej z najnowszą wersją programu Visual Studio 2015. Żadna Poprzednia wersja nie jest obsługiwana. Wymagane zmiany są różne w zależności od języka użytego do utworzenia aplikacji:

- [C#Aplikacje/VB](#RCUpdate10CSharp)

- [C++korzysta](#RCUpdate10CPlusPlus)

### <a name="RCUpdate10CSharp"></a>Aktualizowanie projektów C#/VB do korzystania z najnowszych platforma uniwersalna systemu Windows
 Po otwarciu rozwiązania dla istniejącej aplikacji zobaczysz, że aplikacja wymaga aktualizacji:

 ![Wyświetl projekt w Eksplorator rozwiązań](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 W przypadku wybrania opcji Załaduj ponownie ten projekt z Eksplorator rozwiązań zostanie wyświetlone następujące okno dialogowe:

 ![Przekieruj aplikację, aby użyć poprawnego zestawu SDK](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Ponieważ zestaw platforma uniwersalna systemu Windows SDK dla projektu jest teraz nieobsługiwany, nie będzie można go zainstalować. Po prostu kliknij przycisk OK, a następnie wykonaj poniższe kroki.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Aktualizowanie projektów C#/VB do korzystania z najnowszych platforma uniwersalna systemu Windows

1. Aby znaleźć zainstalowaną platforma uniwersalna systemu Windows, otwórz ten folder: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Zawiera listę folderów dla każdej zainstalowanej platforma uniwersalna systemu Windows. Nazwa folderu jest zainstalowaną platforma uniwersalna systemu Windows wersją. Na przykład na tym urządzeniu z systemem Windows 10 jest zainstalowana wersja 10.0.10240.0 platforma uniwersalna systemu Windows.

    ![Otwórz folder, aby wyświetlić zainstalowane wersje](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

    Można zainstalować więcej niż jedną wersję platforma uniwersalna systemu Windows. Zalecamy użycie najnowszej wersji aplikacji.

2. Korzystając z Eksploratora plików, przejdź do folderu, w którym przechowywany jest projekt platformy UWP. Usuń plik Packages. config i Utwórz nowy plik JSON w tym folderze. Nazwij plik: Project. JSON, a następnie Dodaj do tego pliku następującą zawartość:

   ```json

   {
     "dependencies": {
       "Microsoft.ApplicationInsights": "1.0.0",
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
     },
     "frameworks": {
       "uap10.0": {}
     },
     "runtimes": {
       "win10-arm": {},
       "win10-arm-aot": {},
       "win10-x86": {},
       "win10-x86-aot": {},
       "win10-x64": {},
       "win10-x64-aot": {}
     }
   }

   ```

3. Za pomocą programu Visual Studio Otwórz rozwiązanie, które zawiera C#aplikację/VB Universal Windows. Zobaczysz, że plik projektu (. csproj lub. vbproj) musi zostać zaktualizowany. Kliknij prawym przyciskiem myszy plik projektu i wybierz polecenie Edytuj ten plik.

    ![Kliknij prawym przyciskiem myszy projekt i wybierz polecenie Edytuj](../misc/media/uap-editproject.png "UAP_EditProject")

4. Znajdź \<właściwości > element, który zawiera \<\<> i > element targetplatformminversion. Zmień istniejącą wartość \<TargetPlatformVersion > i \<element targetplatformminversion > elementów, aby była taka sama jak wersja zainstalowanego platforma uniwersalna systemu Windows.

    Domyślna Skala zasobów dla aplikacji uniwersalnych systemu Windows to 200. Projekty utworzone za pomocą programu Visual Studio 2015 RC obejmują zasoby skalowane na 100, należy dodać \<element > UapDefaultAssetScale z wartością 100 do tej właściwości. Dowiedz się więcej o [zasobach i skalowaniu](https://msdn.microsoft.com/library/jj679352.aspx).

5. Jeśli dodano odwołania do zestawów SDK rozszerzenia platformy UWP (na przykład: Windows Mobile SDK), należy zaktualizować wersję zestawu SDK. Na przykład ten \<SDKReference > element:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

    Należy zmienić na:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

6. Znajdź \<element docelowy > z atrybutem nazwy, który ma wartość: EnsureNuGetPackageBuildImports. Usuń ten element i wszystkie jego elementy podrzędne.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Znajdź i Usuń \<Importuj elementy > z atrybutami Project i Condition odwołującymi się do Microsoft. Diagnostics. Tracing. EventSource i Microsoft. ApplicationInsights, jak to:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. Znajdź element \<Item >, który ma \<odwołanie > elementów podrzędnych do pakietów NuGet. Zwróć uwagę na pakiety NuGet, do których istnieją odwołania, ponieważ te informacje będą potrzebne do przyszłego kroku. Istotna różnica między formatem projektu systemu Windows 10 między programami Visual Studio 2015 RC i Visual Studio 2015 RTM polega na tym, że format RTM używa [NuGet](/nuget/) w wersji 3.

    Usuń element \<Item > i jego wszystkie elementy podrzędne. Na przykład projekt platformy UWP utworzony za pomocą programu Visual Studio RC będzie miał następujące pakiety NuGet, które muszą zostać usunięte:

   ```xml
   <ItemGroup>
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
         <Private>True</Private>
       </Reference>
     </ItemGroup>

   ```

9. Znajdź element \<Item >, który zawiera \<elementu > AppxManifest. Jeśli istnieje element \<none > z atrybutem include ustawionym na: Packages. config, usuń go. Ponadto Dodaj element \<none > z atrybutem include i ustaw jego wartość na: Project. JSON.

10. Zapisz zmiany. Następnie zamknij plik projektu.

11. Kliknij prawym przyciskiem myszy plik projektu w Eksplorator rozwiązań, a następnie wybierz polecenie Załaduj ponownie projekt z menu kontekstowego. Wszystkie pliki w projekcie powinny teraz być wyświetlane w Eksplorator rozwiązań.

12. Wybierz plik ApplicationInsights. config w Eksplorator rozwiązań i otwórz jego właściwości. Ustaw właściwość Akcja kompilacji na wartość "zawartość" i Właściwość Kopiuj do katalogu wyjściowego na wartość "Kopiuj jeśli nowszy".

13. Otwórz plik Package. appxmanifest w projekcie.

    1. Znajdź element \<Targetdevicefamily elementu >. Zmień atrybuty MinVersion i MaxVersionTested, aby odpowiadały zainstalowanej wersji platforma uniwersalna systemu Windows. Jak to:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Zapisz zmiany.

14. Za pomocą Menedżera NuGet Dodaj pakiety usunięte we wcześniejszym kroku. Istotna różnica między formatem projektu systemu Windows 10 między programami Visual Studio 2015 RC i Visual Studio 2015 RTM polega na tym, że format RTM używa [NuGet](/nuget/) w wersji 3.

    Teraz można kod, skompilować i debugować aplikację.

    Jeśli masz projekty testów jednostkowych dla aplikacji uniwersalnych systemu Windows, musisz również wykonać [te kroki](#MigrateUnitTest).

### <a name="RCUpdate10CPlusPlus"></a>Zaktualizuj swoje C++ projekty, aby użyć najnowszych platforma uniwersalna systemu Windows

1. Aby znaleźć zainstalowaną platforma uniwersalna systemu Windows, otwórz ten folder: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Zawiera listę folderów dla każdej zainstalowanej platforma uniwersalna systemu Windows. Nazwa folderu jest zainstalowaną platforma uniwersalna systemu Windows wersją. Na przykład na tym urządzeniu z systemem Windows 10 jest zainstalowana wersja 10.0.10240.0 platforma uniwersalna systemu Windows.

     ![Otwórz folder, aby wyświetlić zainstalowane wersje](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Można zainstalować więcej niż jedną wersję platforma uniwersalna systemu Windows. Zalecamy użycie najnowszej wersji aplikacji.

2. Otwórz rozwiązanie, które zawiera aplikację C++ uniwersalną systemu Windows. Kliknij prawym przyciskiem myszy plik Project. vcxproj, a następnie wybierz polecenie Zwolnij plik projektu. Po usunięciu projektu ponownie kliknij prawym przyciskiem myszy plik projektu i wybierz polecenie edycji.

     ![Zwolnij projekt, a następnie edytuj plik projektu](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Znajdź dowolny \<właściwości > elementy, które nie zawierają atrybutu Condition, ale zawierają element \<ApplicationTypeRevision >. Zaktualizuj wartość ApplicationTypeRevision z 8,2 do 10,0. Dodaj \<WindowsTargetPlatformVersion > i \<elementu > WindowsTargetPlatformMinVersion i ustaw ich wartości jako wartość zainstalowanej wersji platforma uniwersalna systemu Windows.

     Dodaj element \<EnableDotNetNativeCompatibleProfile > i ustaw jego wartość na true, jeśli element jeszcze nie istnieje.

     Domyślna Skala zasobów dla aplikacji uniwersalnych systemu Windows to 200. Projekty utworzone za pomocą programu Visual Studio 2015 RC obejmują zasoby skalowane na 100, należy dodać \<element > UapDefaultAssetScale z wartością 100 do tej właściwości. Dowiedz się więcej o [zasobach i skalowaniu](https://msdn.microsoft.com/library/jj679352.aspx).

     Dlatego ten \<Właściwość > element będzie teraz podobny do tego:

    ```xml
    <PropertyGroup Label="Globals">
        …
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>
        <ApplicationType>Windows Store</ApplicationType>
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
        <UapDefaultAssetScale>100</UapDefaultAssetScale>
      </PropertyGroup>

    ```

4. Dla każdego pozostałego elementu \<właściwości >, sprawdź, czy element ma atrybut Condition z konfiguracją wydania. Jeśli tak, ale nie zawiera elementu \<UseDotNetNativeToolchain >, Dodaj go. Dla elementu \<UseDotNetNativeToolchain > Ustaw wartość true, np.:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. Należy zaktualizować element \<EnableDotNetNativeCompatibleProfile > i element \<UseDotNetNativeToolchain >, aby włączyć .NET Native, ale .NET Native nie jest włączona w C++ szablonach.

     Zapisz zmiany. Następnie zamknij plik projektu.

6. Kliknij prawym przyciskiem myszy plik projektu w Eksplorator rozwiązań, a następnie wybierz polecenie Załaduj ponownie projekt z menu kontekstowego. Wszystkie pliki w projekcie powinny teraz być wyświetlane w Eksplorator rozwiązań.

7. Otwórz plik Package. appxmanifest w projekcie.

    1. Znajdź element \<Targetdevicefamily elementu >. Zmień atrybuty MinVersion i MaxVersionTested, aby odpowiadały zainstalowanej wersji platforma uniwersalna systemu Windows. Jak to:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Zapisz zmiany.

         Teraz można kod, skompilować i debugować aplikację.

         Jeśli masz projekty testów jednostkowych dla aplikacji uniwersalnych systemu Windows, musisz również wykonać [te kroki](#MigrateUnitTest).

## <a name="MigrateUnitTest"></a>Zmiany wymagane dla istniejących projektów testów jednostkowych dla aplikacji uniwersalnych systemu Windows utworzonych za pomocą programu Visual Studio 2015 RC
 Jeśli utworzono projekty testów jednostkowych dla aplikacji uniwersalnych systemu Windows 10 za pomocą programu Visual Studio 2015 RC, musisz wprowadzić te dodatkowe zmiany w plikach projektu, aby użyć tych projektów testowych z najnowszą wersją programu Visual Studio 2015. Wymagane zmiany są różne w zależności od języka użytego do utworzenia aplikacji:

- [C#Aplikacje/VB](#UnitTestRCUpdate10CSharp)

- [C++korzysta](#UnitTestRCUpdate10CPlusPlus)

### <a name="UnitTestRCUpdate10CSharp"></a>Aktualizowanie projektów C#testów jednostkowych/VB

1. W programie Visual Studio Otwórz rozwiązanie, które zawiera projekt C#testu jednostkowego/VB. Zmień wartość elementu \<OuttputType > na: AppContainerExe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Zastąp ten element \<EnableCoreRuntime > false\</EnableCoreRuntime > z następującym elementem:

   ```xml

   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>

   ```

3. Usuń następujące wiersze:

   ```xml

   <PropertyGroup>
       <AppXPackage>True</AppXPackage>
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
       <PlatformTarget>AnyCPU</PlatformTarget>
       <DebugType>pdbonly</DebugType>
       <Optimize>true</Optimize>
       <OutputPath>bin\Release\</OutputPath>
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
       <ErrorReport>prompt</ErrorReport>
       <WarningLevel>4</WarningLevel>
    </PropertyGroup>

   ```

4. Dodaj ten element \<UseDotNetNativeToolchain > true\</UseDotNetNativeToolchain > jako element podrzędny do tych grup właściwości:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Usuń następujące elementy \<Item >:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="packages.config" />
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\Default.rd.xml" />
      <Content Include="Assets\Logo.scale-240.png" />
      <Content Include="Assets\SmallLogo.scale-240.png" />
      <Content Include="Assets\SplashScreen.scale-240.png" />
      <Content Include="Assets\Square71x71Logo.scale-240.png" />
      <Content Include="Assets\StoreLogo.scale-240.png" />
      <Content Include="Assets\WideLogo.scale-240.png" />
   </ItemGroup>

   ```

    Zamień je na następujące elementy:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTestApp.xaml.cs">
         <DependentUpon>UnitTestApp.xaml</DependentUpon>
      </Compile>
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <ApplicationDefinition Include="UnitTestApp.xaml">
         <Generator>MSBuild:Compile</Generator>
         <SubType>Designer</SubType>
      </ApplicationDefinition>
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\UnitTestApp.rd.xml" />
      <Content Include="Assets\LockScreenLogo.scale-200.png" />
      <Content Include="Assets\SplashScreen.scale-200.png" />
      <Content Include="Assets\Square150x150Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
      <Content Include="Assets\StoreLogo.png" />
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />
   </ItemGroup>
   ```

6. Utwórz nowy projekt testu jednostkowego i skopiuj pliki UnitTestApp. XAML i UnitTestApp.xaml.cs z tego nowego projektu do istniejącego projektu testów jednostkowych, który aktualizujesz.

7. Skopiuj plik UnitTestApp. Rd. XML z folderu Properties (nowy projekt testu jednostkowego) do folderu właściwości istniejącego projektu testów jednostkowych, który aktualizujesz.

8. Otwórz plik Package. appxmanifest w projekcie. Następnie usuń z niego następujące elementy:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="vstest.executionengine.appcontainer.uap.exe"
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
         <uap:VisualElements
            DisplayName="UnitTestProject1"
            Square150x150Logo="Assets\Logo.png"
            Square44x44Logo="Assets\SmallLogo.png"
            Description="UnitTestProject1"
            BackgroundColor="#464646">
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClientServer" />
   </Capabilities>
   ```

    Zamień te usunięte elementy na następujące elementy. Użyj odpowiedniej wartości dla ProjectName w oparciu o nazwę projektu, a nie UnitTestProject1 w poniższych elementach:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="$targetnametoken$.exe"
            EntryPoint="UnitTestProject1.App">
         <uap:VisualElements
               DisplayName="UnitTestProject1"
               Square150x150Logo="Assets\Square150x150Logo.png"
               Square44x44Logo="Assets\Square44x44Logo.png"
               Description="UnitTestProject1"
               BackgroundColor="transparent">
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClient" />
   </Capabilities>
   ```

   Teraz można uruchomić testy jednostkowe.

### <a name="UnitTestRCUpdate10CPlusPlus"></a>Zaktualizuj swoje C++ projekty, aby użyć najnowszych platforma uniwersalna systemu Windows

1. W programie Visual Studio Otwórz rozwiązanie, które zawiera projekt C++ testu jednostkowego. Usuń następujące elementy:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Dodaj następujące \<ProjectConfiguration > elementów poniżej tego elementu \<Items Label = "ProjectConfigurations" >, jeśli nie znajdują się one jeszcze w tym wypełnieniu:

    ```xml

    <ProjectConfiguration Include="Debug|x64">
       <Configuration>Debug</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|x64">
       <Configuration>Release</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>

    ```

3. Zamień każde wystąpienie tego elementu:

    ```xml

    <ConfigurationType>DynamicLibrary</ConfigurationType>

    ```

     Na ten:

    ```xml

    <ConfigurationType>Application</ConfigurationType>

    ```

4. Dodaj te \<właściwości > elementów, jeśli nie znajdują się one jeszcze w pliku:

    ```xml

    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>true</UseDebugLibraries>
       <PlatformToolset>v140</PlatformToolset>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>false</UseDebugLibraries>
       <WholeProgramOptimization>true</WholeProgramOptimization>
       <PlatformToolset>v140</PlatformToolset>
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
    </PropertyGroup>

    ```

5. Zamień każde wystąpienie tego elementu:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
    ```

     Na ten:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>

    ```

6. Zamień każde wystąpienie tego elementu:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

     Na ten:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

7. Dodaj te \<ItemDefinitionGroup > elementów w sekcji, które zawierają już inne \<elementy >:

    ```xml

    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
    <Link>
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
    </Link>
    </ItemDefinitionGroup>
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
       <Link>
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
       </Link>
    </ItemDefinitionGroup>

    ```

8. Usuń następujący element \< Item >:

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Zastąp ją tym \<element > Item:

    ```xml

    <ItemGroup>
       <Image Include="Assets\LockScreenLogo.scale-200.png" />
       <Image Include="Assets\SplashScreen.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
       <Image Include="Assets\Square150x150Logo.scale-200.png" />
       <Image Include="Assets\StoreLogo.png" />
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />
    </ItemGroup>

    ```

9. Usuń następujący element \< Item >:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Zamień ją na następujące elementy \<Item >:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
       <ClInclude Include="UnitTestApp.xaml.h">
          <DependentUpon>UnitTestApp.xaml</DependentUpon>
       </ClInclude>
    </ItemGroup>
    <ItemGroup>
       <ApplicationDefinition Include="UnitTestApp.xaml">
          <SubType>Designer</SubType>
       </ApplicationDefinition>
    </ItemGroup>

    ```

10. Usuń następujący element:

    ```xml
    <ClCompile Include="UnitTest.cpp"/>
    ```

     Zastąp go tymi \<CICompile > elementy:

    ```xml

    <ClCompile Include="UnitTestApp.xaml.cpp">
       <DependentUpon>UnitTestApp.xaml</DependentUpon>
    </ClCompile>
    <ClCompile Include="UnitTest.cpp"/>

    ```

11. Dodaj ten element:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
    ```

     Powyżej tego elementu w pliku:

    ```xml

    <ItemGroup>
       <Xml Include="UnitTestApp.rd.xml" />
    </ItemGroup>
    ```

12. Utwórz nowy projekt testu C++ jednostkowego i skopiuj pliki UnitTestApp. XAML, UnitTestApp. XAML. cpp, UnitTestApp. XAML. h i UnitTestApp. Rd. XML z tego projektu do istniejącego projektu, który aktualizujesz.

13. Otwórz plik Package. appxmanifest w projekcie. Następnie usuń z niego następujące elementy:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
             Executable="vstest.executionengine.appcontainer.uap.exe"
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
          <uap:VisualElements
             DisplayName="UnitTestProject1"
             Square150x150Logo="Assets\Logo.png"
             Square44x44Logo="Assets\SmallLogo.png"
             Description="UnitTestProject1"
             BackgroundColor="#464646">
             <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClientServer" />
    </Capabilities>

    ```

     Zamień te usunięte elementy na następujące elementy. Użyj odpowiedniej wartości dla ProjectName w oparciu o nazwę projektu, a nie UnitTestProject1 w poniższych elementach:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
                Executable="$targetnametoken$.exe"
                EntryPoint="UnitTestProject1.App">
          <uap:VisualElements
                DisplayName="UnitTestProject1"
                Square150x150Logo="Assets\Square150x150Logo.png"
                Square44x44Logo="Assets\Square44x44Logo.png"
                Description="UnitTestProject1"
                BackgroundColor="transparent">
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
                <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClient" />
    </Capabilities>

    ```