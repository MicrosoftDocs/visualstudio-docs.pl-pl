---
title: Migrowanie aplikacji na platformie Universal Windows (UWP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8d4bc5d8e8a24483c30ac813d3253626e58dd353
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791751"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migracja aplikacji na platformę uniwersalną systemu Windows
Wprowadź potrzebne zmiany ręcznej w istniejących plików projektu dla aplikacji Windows Store 8.1, aplikacje systemu Windows Phone 8.1 lub Windows Universal apps utworzonych za pomocą programu Visual Studio 2015 RC, dzięki czemu mogą być używane za pomocą programu Visual Studio 2015 RTM. (W przypadku aplikacji uniwersalnej Windows 8.1, za pomocą projektu aplikacji Windows i Windows Phone projektu, należy wykonać kroki do każdego projektu migracji.)  
  
 Na platformie Universal Windows możesz teraz wskazać swoją aplikację do co najmniej jeden urządzenia z rodzin. Jeśli chcesz, aby dowiedzieć się więcej o aplikacji Windows Universal apps, zapoznaj się z tym [Przewodnik po platformie](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
- [Migrowanie istniejących C# /VB Windows Store 8.1 lub Windows Phone 8.1 aplikacji](#MigrateCSharp) używać uniwersalnej platformy Windows.  
  
- [Migrowanie istniejących aplikacji C++ Windows Store 8.1 lub Windows Phone 8.1](#MigrateCPlusPlus) używać uniwersalnej platformy Windows.  
  
- [Zmiany wymagane w przypadku istniejących aplikacji Universal Windows utworzonych za pomocą programu Visual Studio 2015 RC](#PreviousVersions).  
  
- [Zmiany wymagane do istniejących projektów testów jednostkowych dla aplikacji Universal Windows utworzonych za pomocą programu Visual Studio 2015 RC](#MigrateUnitTest).  
  
  Jeśli nie chcesz wprowadzić te zmiany, Dowiedz się, jak [portu istniejących aplikacji](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) do nowego projektu Universal Windows.  
  
##  <a name="MigrateCSharp"></a> Migrowanie C# /VB Windows Store 8.1 lub Windows Phone 8.1 aplikacjach opcję użycia platformy uniwersalnej Windows  
  
#### <a name="migrate-your-cvb-project-files"></a>Migrowanie plików projektu C# /VB  
  
1.  Aby znaleźć której uniwersalnej platformy Windows został zainstalowany, otwórz ten folder: **\Windows Kits\10\Platforms\UAP pliki (x86) \Program**. Zawiera listę folderów dla każdej platformy uniwersalnej Windows, który jest zainstalowany. Nazwa folderu jest wersja Universal Windows Platform, która została zainstalowana. Na przykład to urządzenie z systemem Windows 10 ma 10.0.10240.0 uniwersalnej platformy Windows zainstalowaną wersję.  
  
     ![Otwórz folder, aby wyświetlić wersje zainstalowane](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Można zainstalować więcej niż jedna wersja platformy uniwersalnej Windows. Zaleca się, że używasz najnowszej wersji dla aplikacji.  
  
2.  W Eksploratorze plików przejdź do folderu, w której jest przechowywany projekt platformy uniwersalnej systemu Windows. Utwórz plik JSON, w tym folderze. Nazwij plik: plik project.json, a następnie dodaj następującą zawartość do tego pliku:  
  
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
  
3.  Utwórz plik o nazwie default.rd.xml z następującą zawartością. Jeśli masz projektu VB, Dodaj ten plik do katalogu mój projekt do projektu. Jeśli masz projekt C#, należy dodać ten plik do katalogu właściwości projektu.  
  
    ```xml  
    <?xml version="1.0"?>  
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>  
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->  
    <Assembly Dynamic="Required All" Name="*Application*"/>  
    <!-- Add your application specific runtime directives here. -->  
    </Application></Directives>  
    ```  
  
4.  Otwórz swoje rozwiązanie, który zawiera Twojej istniejącej aplikacji Windows Store 8.1 lub Windows Phone 8.1 w programie Visual Studio.  
  
5.  Kliknij prawym przyciskiem myszy istniejącego projektu dla aplikacji w Eksploratorze rozwiązań, a następnie wybierz **Zwolnij projekt**. Gdy projekt jest zwolniony, ponownie kliknij prawym przyciskiem myszy plik projektu i wybierz opcję edytować plik .csproj lub .vbproj.  
  
     ![Kliknij prawym przyciskiem myszy projekt i wybierz pozycję Edytuj](../misc/media/uap-editproject.png "UAP_EditProject")  
  
6.  Znajdź \<PropertyGroup > element, który zawiera \<TargetPlatformVersion > element z wartością 8.1. Wykonaj następujące czynności w tym \<PropertyGroup > element:  
  
    1.  Ustaw wartość \<platformy > element: **x86**.  
  
    2.  Dodaj \<TargetPlatformIdentifier > element i ustaw dla niego wartość: **UAP**.  
  
    3.  Zmiana wartości istniejącego \<TargetPlatformVersion > element staje się ona wartością wersji Universal Windows Platform, który został zainstalowany. Również dodać \<TargetPlatformMinVersion > element i nadaj mu taką samą wartość.  
  
    4.  Zmień wartość właściwości \<MinimumVisualStudioVersion > element: **14**.  
  
    5.  Zastąp \<ProjectTypeGuids > elementu, jak pokazano poniżej:  
  
         Dla języka C#:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        ```  
  
         Dla języka VB:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        ```  
  
    6.  Dodaj \<EnableDotNetNativeCompatibleProfile > element i ustaw dla niego wartość: **true**.  
  
    7.  Domyślna Skala zasobów dla aplikacji Universal Windows apps to 200. Jeśli projekt zawiera zasoby, które nie są skalowane o wartości 200, należy dodać \<UapDefaultAssetScale > element z wartością zasoby do tego PropertyGroup skali. Dowiedz się więcej o [zasobów i skaluje się](http://msdn.microsoft.com/library/jj679352.aspx).  
  
         Teraz Twoja \<PropertyGroup > element zawartość okna powinna wyglądać następująco:  
  
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
  
7.  Zastąp wszystkie wystąpienia 12.0 14.0 w celu uwzględnienia wersji programu Visual Studio, którego obecnie używasz. Podobnie jak tych wystąpień:  
  
    ```xml  
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
    ```  
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">  
        <VisualStudioVersion>14.0</VisualStudioVersion>  
    ```  
  
8.  Znajdź \<PropertyGroup > elementy, które są skonfigurowane dla platformy AnyCPU jako część atrybutu warunku. Usunąć te elementy i wszystkie jego elementy podrzędne. AnyCPU nie jest obsługiwana dla aplikacji systemu Windows 10 w programie Visual Studio 2015. Na przykład, należy usunąć \<PropertyGroup > elementów, takich jak te z nich:  
  
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
  
9. Dla każdego pozostałe \<PropertyGroup > element, sprawdź, czy element ma atrybut warunku, przy użyciu konfiguracji wydania. Jeśli tak jest, ale nie zawiera \<UseDotNetNativeToolchain > element, dodać go. Ustaw wartość \<UseDotNetNativeToolchain > element na wartość true, następująco:  
  
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
  
10. Windows Phone projekty tylko usunąć \<PropertyGroup > element, który zawiera \<TargetPlatformIdentifier > element z wartością WindowsPhoneApp. Także usunąć wszystkie elementy podrzędne tego elementu:  
  
    ```xml  
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">  
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>  
    </PropertyGroup>  
    ```  
  
11. Znajdź \<ItemGroup > element, który zawiera \<AppxManifest > element. Dodaj następujący kod \<Brak > element jako element podrzędny elementu \<ItemGroup > element:  
  
    ```xml  
    <None Include="project.json" />  
    ```  
  
12. Znajdź \<ItemGroup > element, który zawiera inne zasoby, które są dodawane do projektu, takich jak pliki PNG logo (\<zawartości Include="Assets\Logo.scale-100.png" / >). Dodaj następujący kod \<zawartości > element podrzędny tej \<ItemGroup > element:  
  
     **Dla języka C#:**  
  
    ```xml  
    <Content Include="Properties\default.rd.xml" />  
    ```  
  
     **Dla języka VB:**  
  
    ```xml  
    <Content Include="My Project\default.rd.xml" />  
    ```  
  
13. Znajdź \<ItemGroup > element, który zawiera \<odwołanie > elementy podrzędne do pakietów NuGet. Zwróć uwagę na pakiety NuGet, których używasz, ponieważ będą potrzebne je pobrać za pomocą Menedżera pakietów NuGet, po ponownym załadowaniu projektu. Usuń ten element \<ItemGroup > wraz z jego elementów podrzędnych. Na przykład projekt platformy uniwersalnej systemu Windows może mieć następujące pakiety NuGet, które muszą zostać usunięte:  
  
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
  
15. Zamknij plik .csproj lub .vbproj.  
  
16. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie z menu kontekstowego wybierz pozycję Załaduj ponownie projekt. Wszystkie pliki w projekcie powinna być teraz wyświetlana w Eksploratorze rozwiązań.  
  
17. Użyj Menedżera NuGet, aby dodać z powrotem pakiety, które usunięto w poprzednim kroku.  
  
     Teraz należy wykonać kroki, aby [Zaktualizuj pliki manifestu w pakiecie](#PackageManifest) dla wszystkich projektów Windows Store 8.1 lub Windows Phone 8.1.  
  
##  <a name="MigrateCPlusPlus"></a> Migrowanie aplikacji C++ Windows Store 8.1 lub Windows Phone 8.1 do użycia platformy uniwersalnej Windows  
  
#### <a name="migrate-your-c-project-files"></a>Migrowanie plików projektu C++  
  
1.  Aby znaleźć której uniwersalnej platformy Windows został zainstalowany, otwórz ten folder: **\Windows Kits\10\Platforms\UAP pliki (x86) \Program**. Zawiera listę folderów dla każdej platformy uniwersalnej Windows, który jest zainstalowany. Nazwa folderu jest wersja Universal Windows Platform, która została zainstalowana. Na przykład to urządzenie z systemem Windows 10 ma 10.0.10240.0 uniwersalnej platformy Windows zainstalowaną wersję.  
  
     ![Otwórz folder, aby wyświetlić wersje zainstalowane](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Można zainstalować więcej niż jedna wersja platformy uniwersalnej Windows. Zaleca się, że używasz najnowszej wersji dla aplikacji.  
  
2.  Otwórz swoje rozwiązanie, który zawiera istniejących aplikacji C++ Windows Store 8.1 lub aplikacji Windows Phone 8.1 w programie Visual Studio.  
  
     Kliknij prawym przyciskiem myszy istniejący projekt w Eksploratorze rozwiązań, a następnie wybierz **Zwolnij projekt**. Gdy projekt jest zwolniony, ponownie kliknij prawym przyciskiem myszy plik projektu, a następnie wybrać opcję Edytuj plik .vcxproj.  
  
     ![Po prawej stronie&#45;kliknij plik projektu, a następnie wybrać opcję Edytuj](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")  
  
3.  Znajdź \<PropertyGroup > element, który zawiera \<ApplicationTypeRevision > element z wartością 8.1. Wykonaj następujące czynności w tym \<PropertyGroup > element:  
  
    1.  Dodaj \<WindowsTargetPlatformVersion > element i \<WindowsTargetPlatformMinVersion > element i podaj wartość wersji Universal Windows Platform, który został zainstalowany.  
  
    2.  Zaktualizuj wartość elementu ApplicationTypeRevision 8.1 10.0.  
  
    3.  Zmień wartość właściwości \<MinimumVisualStudioVersion > element: 14.  
  
    4.  Dodaj \<EnableDotNetNativeCompatibleProfile > element i ustaw dla niego wartość: PRAWDA.  
  
    5.  Domyślna Skala zasobów dla aplikacji Universal Windows apps to 200. Jeśli projekt zawiera zasoby, które nie są skalowane o wartości 200, należy dodać \<UapDefaultAssetScale > element z wartością zasoby do tego PropertyGroup skali. Dowiedz się więcej o [zasobów i skaluje się](http://msdn.microsoft.com/library/jj679352.aspx).  
  
    6.  Dla Windows Phone projektów, zmień wartość \<ApplicationType > od Windows Phone do Windows Store.  
  
         Teraz Twoja \<PropertyGroup > element zawartość okna powinna wyglądać następująco:  
  
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
  
4.  Należy zastąpić wszystkie wystąpienia \<PlatformToolset > elemencie muszą mieć wartość w wersji 140. Na przykład:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
5.  Dla każdego pozostałe \<PropertyGroup > element, sprawdź, czy element ma atrybut warunku, przy użyciu konfiguracji wydania. Jeśli tak jest, ale nie zawiera \<UseDotNetNativeToolchain > element, dodać go. Ustaw wartość \<UseDotNetNativeToolchain > element na wartość true, następująco:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
6.  Zapisz zmiany. Zamknij plik projektu.  
  
7.  Kliknij prawym przyciskiem myszy plik projektu w Eksploratorze rozwiązań, a następnie z menu kontekstowego wybierz pozycję Załaduj ponownie projekt. Wszystkie pliki w projekcie powinna być teraz wyświetlana w Eksploratorze rozwiązań.  
  
     Teraz należy wykonać kroki, aby [Zaktualizuj pliki manifestu w pakiecie](#PackageManifest) dla wszystkich projektów Windows Store 8.1 lub Windows Phone 8.1.  
  
##  <a name="PackageManifest"></a> Zaktualizuj plik manifestu pakietu dla projektów Windows Store 8.1 lub Windows Phone 8.1  
 Należy zaktualizować plik manifestu pakietu dla każdego projektu w rozwiązaniu.  
  
#### <a name="update-your-package-manifest-file"></a>Zaktualizuj plik manifestu pakietu  
  
1. Otwórz plik manifestu Package.appx w projekcie. Należy edytować plik manifestu Package.appx dla poszczególnych projektów Windows Store i Windows Phone.  
  
2. Należy zaktualizować \<pakietu > elementu za pomocą nowego schematów na podstawie Twojego istniejącego projektu typu. Najpierw usuń poniżej schematów na podstawie tego, czy mają projektów Windows Store lub Windows Phone.  
  
    **STARA dla projektów Windows Store:** swoje \<pakietu > element będzie wyglądać podobnie do następującego.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">  
  
   ```  
  
    **STARY dla projektu Windows Phone:** swoje \<pakietu > element będzie wyglądać podobnie do następującego.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"  
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"  
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">  
   ```  
  
    **NOWE platformy Windows Universal:** schematów poniżej, aby dodać swoje \<pakietu > element. Usuń wszelkie prefiksy identyfikator skojarzonego przestrzeni nazw z elementów dla schematów, które zostały usunięte. Aktualizowanie właściwości IgnorableNamespaces: uap mp. Nowy \<pakietu > element powinien wyglądać podobnie do następującego.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"  
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"  
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"  
      IgnorableNamespaces= "uap mp">  
  
   ```  
  
3. Dodaj \<zależności > element podrzędny do \<pakietu > element. Następnie dodaj \<TargetDeviceFamily > element podrzędny tej \<zależności > elementu z atrybutami nazwę, MinVersion i MaxVersionTested. Zwraca wartość atrybutu Name: zależności targetdevicefamily elementu. Zapewniają MinVersion i MaxVersionTested wartość wersji Universal Windows Platform, którą instalujesz. Ten element powinien wyglądać mniej więcej tak:  
  
   ```xml  
   <Dependencies>  
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />  
   </Dependencies>  
   ```  
  
4. **Dla Windows Store tylko:** należy dodać \<mp:PhoneIdentity > element podrzędny do \<pakietu > element. Dodaj atrybut PhoneProductId i atrybut PhonePublisherId. Ustaw PhoneProductId można mieć taką samą wartość jak w atrybucie nazwy w \<tożsamości > element. Ustaw wartość PhonePublishedId: 00000000-0000-0000-0000-000000000000. Jak to:  
  
   ```xml  
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />   
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>  
   ```  
  
5. Znajdź \<wymagania wstępne > element i usunąć ten element i wszystkie elementy podrzędne, które przedstawiono w nim.  
  
6. Dodaj **uap** przestrzeni nazw dla następujących \<zasobu > elementy: DXFeatureLevel, skali. Na przykład:  
  
   ```xml  
   <Resources>  
     <Resource Language="en-us"/>  
    <Resource uap:Scale="180"/>  
    <Resource uap:DXFeatureLevel="dx11"/>  
   </Resources>  
  
   ```  
  
7. Dodaj **uap** przestrzeni nazw dla następujących \<możliwości > elementy: documentsLibrary, picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, terminy i kontakty. Na przykład:  
  
   ```xml  
   <Capabilities>  
     <uap:Capability Name="documentsLibrary"/>  
     <uap:Capability Name="removableStorage"/>  
   </Capabilities>  
  
   ```  
  
8. Dodaj **uap** przestrzeń nazw \<VisualElements > elementu i wszelkich jego elementy podrzędne. Na przykład:  
  
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
  
    **Dotyczy tylko Windows Store:** zostały zmienione nazwy Rozmiar kafelka. Zmienianie atrybutów w \<VisualElements > element, aby odzwierciedlić nowe zbieżności rozmiarów kafelka. 70 x 70 staje się 71 x 71 i 30 x 30 staje się 44 x 44.  
  
    **Stary:** nazwy rozmiarów kafelka  
  
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
  
    **Nowość:** nazwy rozmiarów kafelka  
  
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
  
9. Dodaj **uap** przestrzeń nazw \<ApplicationContentUriRules > i jego elementy podrzędne. Na przykład:  
  
    ```xml  
    <uap:ApplicationContentUriRules>  
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>  
      <uap:Rule Type="exclude" Match="*.pdf"/>  
    </uap:ApplicationContentUriRules>  
  
    ```  
  
10. Dodaj **uap** przestrzeni nazw dla następujących \<rozszerzenia > elementy i wszystkie jego elementy podrzędne: windows.accountPictureProvide, windows.alarm windows.appointmentsProvider windows.autoPlayContent  windows.autoPlayDevice windows.cachedFileUpdate, windows.cameraSettings, windows.fileOpenPicker, windows.fileTypeAssociation, windows.fileSavePicke, windows.lockScreenCall, windows.printTaskSettings, windows.protocol, windows.search, windows.shareTarget. Na przykład:  
  
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
  
11. Dodaj **uap** przestrzeń nazw do zadania w tle chatMessageNotification typu. Na przykład:  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
     <BackgroundTasks ServerName="MyBackgroundTasks">  
        <uap:Task Type="chatMessageNotification"/>  
      </BackgroundTasks>  
    </Extension>  
  
    ```  
  
12. Zmień zależności struktury. Dodaj nazwę wydawcy do wszystkich \<PackageDependency > elementy, a następnie określ MinVersion, jeśli jeszcze nie określono.  
  
     **Stary:** \<PackageDependency > element  
  
    ```xml  
    <Dependencies>  
     <PackageDependency Name="Microsoft.VCLibs.120.00" />  
    </Dependencies>  
  
    ```  
  
     **Nowość:** \<PackageDependency > element  
  
    ```xml  
    <Dependencies>  
     <PackageDependency  
          Name="Microsoft.VCLibs.120.00"  
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"  
          MinVersion="12.0.30113.0" />  
    </Dependencies>  
  
    ```  
  
     Odpowiednie wartości wydawcy i MinVersion na użytek framework rzeczywiste, którego używasz. Należy pamiętać, że te nazwy mogą ulec zmianie w systemie Windows 10.  
  
13. Zastąp gattCharacteristicNotification i rfcommConnection typu zadania w tle zadanie typu połączenia Bluetooth. Na przykład:  
  
     **STARY:**  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
                <Task Type="rfcommConnection"/>  
               <Task Type="gattCharacteristicNotification"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
     **Nowość:** przy użyciu połączenia Bluetooth typu zadań.  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
               <Task Type="bluetooth"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
14. Zamień bluetooth.rfcomm możliwości urządzenia Bluetooth i bluetooth.genericAttributeProfile ogólnych funkcji Bluetooth. Na przykład:  
  
     **STARY:**  
  
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
  
     **Nowość:** zastąpione ogólnych funkcji Bluetooth.  
  
    ```xml  
    <Capabilities>  
      <uap:DeviceCapability Name="bluetooth"/>  
    </Capabilities>  
  
    ```  
  
15. Usuń wszelkie przestarzałe elementy.  
  
    1. Te atrybuty \<VisualElements > są przestarzałe i powinny zostać usunięte:  
  
       - \<VisualElements > atrybuty: ForegroundText, ToastCapable  
  
       - \<DefaultTile > atrybut DefaultSize  
  
       - \<ApplicationView > element  
  
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
  
    2. Usuń Windows.contact i rozszerzenia windows.contactPicker i wszystkie elementy w ramach tych rozszerzeń.  
  
16. Zapisz plik manifestu Package.appx. Następnie zamknij program Visual Studio.  
  
17. Należy usunąć niektóre pliki ukryte, przed ponownym otwarciu rozwiązania.  
  
    1.  Otwórz Eksploratora plików, kliknij pozycję **widoku** w pasku narzędzi i wybierz **ukryte elementy** i **rozszerzenia nazw plików**. Otwórz ten folder na komputerze: \<ścieżkę do lokalizacji rozwiązania >\\.vs\\\v14 {Nazwa projektu}. W przypadku plików z rozszerzeniem pliku .suo, usuń go.  
  
    2.  Teraz wróć do folderu, w którym znajduje się rozwiązania. Otwórz wszystkie foldery dla projektów, które istnieją w rozwiązaniu. Jeśli plik w obrębie żadnego z tych projektów folderów. csproj.user lub. rozszerzenie vbproj.user, usuń go.  
  
         Możesz teraz ponownie otworzyć rozwiązania w programie Visual Studio. Jesteś gotowy do kodu, kompilowanie i debugowanie aplikacji przy użyciu platformy uniwersalnej Windows.  
  
         Dowiedz się, jak [dostosować swój kod](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) z zalet co nowego na platformie Windows Universal.  
  
##  <a name="PreviousVersions"></a> Zmiany wymagane w przypadku istniejących aplikacji Universal Windows utworzonych za pomocą programu Visual Studio 2015 RC  
 Aplikacje uniwersalne systemu Windows 10 jest utworzony w programie Visual Studio 2015 RC, należy przekierować projekt do wersji platformy Windows uniwersalnej zainstalowana najnowsza wersja programu Visual Studio 2015. Wszelkie wcześniejsze wersje nie jest obsługiwane. Zmiany wymagane są różne w zależności od języka, który został użyty do utworzenia aplikacji:  
  
-   [C# /VB aplikacji](#RCUpdate10CSharp)  
  
-   [Aplikacje C++](#RCUpdate10CPlusPlus)  
  
###  <a name="RCUpdate10CSharp"></a> Aktualizowanie projektów C# /VB, aby używać najnowszej wersji uniwersalnej platformy Windows  
 Po otwarciu rozwiązania dla istniejącej aplikacji zobaczysz, że aplikacja wymaga aktualizacji:  
  
 ![Wyświetl projekt w Eksploratorze rozwiązań](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")  
  
 Jeśli chcesz załadować ponownie ten projekt w Eksploratorze rozwiązań, zobaczysz to okno dialogowe:  
  
 ![Przekierować aplikację do używania poprawny zestaw SDK](../misc/media/missingsdkforuap.png "MissingSDKforUAP")  
  
 Ponieważ Universal Windows Platform SDK do projektu jest teraz obsługiwane, nie można go zainstalować. Po prostu kliknij przycisk OK, a następnie wykonaj poniższe kroki.  
  
##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Aktualizowanie projektów C# /VB, aby używać najnowszej wersji uniwersalnej platformy Windows  
  
1. Aby znaleźć której uniwersalnej platformy Windows został zainstalowany, otwórz ten folder: **\Windows Kits\10\Platforms\UAP pliki (x86) \Program**. Zawiera listę folderów dla każdej platformy uniwersalnej Windows, który jest zainstalowany. Nazwa folderu jest wersja Universal Windows Platform, która została zainstalowana. Na przykład to urządzenie z systemem Windows 10 ma 10.0.10240.0 uniwersalnej platformy Windows zainstalowaną wersję.  
  
    ![Otwórz folder, aby wyświetlić wersje zainstalowane](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
    Można zainstalować więcej niż jedna wersja platformy uniwersalnej Windows. Zaleca się, że używasz najnowszej wersji dla aplikacji.  
  
2. W Eksploratorze plików przejdź do folderu, w której jest przechowywany projekt platformy uniwersalnej systemu Windows. Usuń packages.config pliku, a następnie utwórz nowy plik JSON, w tym folderze. Nazwij plik: plik project.json, a następnie dodaj następującą zawartość do tego pliku:  
  
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
  
3. Za pomocą programu Visual Studio Otwórz swoje rozwiązanie, który zawiera aplikację Windows Universal C# /VB. Zobaczysz, że konieczne jest zaktualizowanie pliku projektu (plik .csproj lub .vbproj). Kliknij prawym przyciskiem myszy plik projektu, a następnie wybierz opcję edytować ten plik.  
  
    ![Kliknij prawym przyciskiem myszy projekt i wybierz pozycję Edytuj](../misc/media/uap-editproject.png "UAP_EditProject")  
  
4. Znajdź \<PropertyGroup > element, który zawiera \<TargetPlatformVersion > i \<TargetPlatformMinVersion > elementy. Zmiana wartości istniejącego \<TargetPlatformVersion > i \<TargetPlatformMinVersion > elementy, aby mieć taką samą wersję platformy Windows uniwersalnej, który został zainstalowany.  
  
    Domyślna Skala zasobów dla aplikacji Universal Windows apps to 200. Projekty utworzone za pomocą programu Visual Studio 2015 RC dołączone zasoby skalowane w 100, należy dodać \<UapDefaultAssetScale > element o wartości 100, aby ta PropertyGroup. Dowiedz się więcej o [zasobów i skaluje się](http://msdn.microsoft.com/library/jj679352.aspx).  
  
5. Jeśli dodano wszelkie odwołania do zestawów SDK rozszerzeń platformy uniwersalnej systemu Windows (na przykład: zestaw SDK usługi Mobile Windows), musisz zaktualizować wersję zestawu SDK. Na przykład to \<SDKReference > element:  
  
   ```xml  
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">  
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
   </SDKReference>  
  
   ```  
  
    Należy je zmienić to:  
  
   ```xml  
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">  
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
   </SDKReference>  
  
   ```  
  
6. Znajdź \<docelowy > element z atrybutem nazwy, który ma wartość: EnsureNuGetPackageBuildImports. Usuń ten element i jego elementów podrzędnych.  
  
   ```xml  
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">  
       <PropertyGroup>  
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>  
       </PropertyGroup>  
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />  
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />  
   </Target>  
   ```  
  
7. Znajdowanie i usuwanie \<Import > elementy za pomocą atrybutów projektu i warunków, które odwołują się Microsoft.Diagnostics.Tracing.EventSource i Microsoft.ApplicationInsights, podobnie do następującego:  
  
   ```xml  
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />  
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />  
  
   ```  
  
8. Znajdź \<ItemGroup > zawierający \<odwołanie > elementy podrzędne do pakietów NuGet. Zwróć uwagę na pakiety NuGet, do których istnieją odwołania, ponieważ te informacje będą potrzebne w przyszłości kroku. Jedną istotną różnicą między formatu projektu systemu Windows 10 między Visual Studio 2015 RC i Visual Studio 2015 RTM jest, że używa formatu RTM [NuGet](http://docs.nuget.org/) w wersji 3.  
  
    Usuń \<ItemGroup > i wszystkich jego obiektów podrzędnych. Na przykład projekt platformy uniwersalnej systemu Windows utworzonych za pomocą programu Visual Studio RC mają następujące pakiety NuGet, które muszą zostać usunięte:  
  
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
  
9. Znajdź \<ItemGroup > element, który zawiera \<AppxManifest > element. W przypadku \<Brak > element z atrybutem Include równa: packages.config, usuń go. Ponadto Dodaj \<Brak > elementu z pliku dołączania atrybut i ustawić jej wartość na: pliku project.json.  
  
10. Zapisz zmiany. Zamknij plik projektu.  
  
11. Kliknij prawym przyciskiem myszy plik projektu w Eksploratorze rozwiązań, a następnie z menu kontekstowego wybierz pozycję Załaduj ponownie projekt. Wszystkie pliki w projekcie powinna być teraz wyświetlana w Eksploratorze rozwiązań.  
  
12. Wybierz plik ApplicationInsights.config w Eksploratorze rozwiązań i otwórz jej właściwości. Ustaw właściwość akcji kompilacji "Treści", a następnie skopiuj do katalogu wyjściowego właściwości na wartość "Kopiuj Jeśli nowszy".  
  
13. Otwórz plik manifestu Package.appx w projekcie.  
  
    1.  Znajdź \<TargetDeviceFamily > element. Zmień jego atrybuty MinVersion i MaxVersionTested, aby odpowiadać wersji Universal Windows Platform, która została zainstalowana. Jak to:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Zapisz zmiany.  
  
14. Użyj Menedżera NuGet, aby dodać pakiety, które usunięto w poprzednim kroku. Jedną istotną różnicą między formatu projektu systemu Windows 10 między Visual Studio 2015 RC i Visual Studio 2015 RTM jest, że używa formatu RTM [NuGet](http://docs.nuget.org/) w wersji 3.  
  
    Można teraz kodu, kompilacji i debugowania aplikacji.  
  
    W przypadku projektów testów jednostkowych dla aplikacji Universal Windows, należy również wykonać [te kroki](#MigrateUnitTest).  
  
###  <a name="RCUpdate10CPlusPlus"></a> Aktualizowanie projektów C++, aby używać najnowszej wersji uniwersalnej platformy Windows  
  
1.  Aby znaleźć której uniwersalnej platformy Windows został zainstalowany, otwórz ten folder: **\Windows Kits\10\Platforms\UAP pliki (x86) \Program**. Zawiera listę folderów dla każdej platformy uniwersalnej Windows, który jest zainstalowany. Nazwa folderu jest wersja Universal Windows Platform, która została zainstalowana. Na przykład to urządzenie z systemem Windows 10 ma 10.0.10240.0 uniwersalnej platformy Windows zainstalowaną wersję.  
  
     ![Otwórz folder, aby wyświetlić wersje zainstalowane](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Można zainstalować więcej niż jedna wersja platformy uniwersalnej Windows. Zaleca się, że używasz najnowszej wersji dla aplikacji.  
  
2.  Otwórz swoje rozwiązanie, zawierającego Universal Windows w języku C++ aplikacji. Kliknij prawym przyciskiem myszy plik .vcxproj projektu, a następnie wybrać opcję zwalnianie pliku projektu. Po projektu został zwolniony, ponownie kliknij prawym przyciskiem myszy plik projektu i wybierz go edytować.  
  
     ![Zwolnij projekt, a następnie edytuj plik projektu](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")  
  
3.  Znajdzie \<PropertyGroup > elementy, które nie zawiera atrybutu warunku, ale zawierają \<ApplicationTypeRevision > element. Zaktualizuj wartość ApplicationTypeRevision od 8.2 do 10.0. Dodaj \<WindowsTargetPlatformVersion > i \<WindowsTargetPlatformMinVersion > element i ustaw ich wartości, wartość wersji Universal Windows Platform, który został zainstalowany.  
  
     Dodaj \<EnableDotNetNativeCompatibleProfile > element i ustaw jej wartość na wartość true, jeśli element nie istnieje.  
  
     Domyślna Skala zasobów dla aplikacji Universal Windows apps to 200. Projekty utworzone za pomocą programu Visual Studio 2015 RC dołączone zasoby skalowane w 100, należy dodać \<UapDefaultAssetScale > element o wartości 100, aby ta PropertyGroup. Dowiedz się więcej o [zasobów i skaluje się](http://msdn.microsoft.com/library/jj679352.aspx).  
  
     Dlatego ta \<PropertyGroup > element teraz wyglądać podobnie jak poniżej:  
  
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
  
4.  Dla każdego pozostałe \<PropertyGroup > element, sprawdź, czy element ma atrybut warunku, przy użyciu konfiguracji wydania. Jeśli tak jest, ale nie zawiera \<UseDotNetNativeToolchain > element, dodać go. Ustaw wartość \<UseDotNetNativeToolchain > element na wartość true, następująco:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
5.  Należy zaktualizować \<EnableDotNetNativeCompatibleProfile > element i \<UseDotNetNativeToolchain > element, aby włączyć .NET Native, ale .NET Native nie jest włączone w szablonów języka C++.  
  
     Zapisz zmiany. Zamknij plik projektu.  
  
6.  Kliknij prawym przyciskiem myszy plik projektu w Eksploratorze rozwiązań, a następnie z menu kontekstowego wybierz pozycję Załaduj ponownie projekt. Wszystkie pliki w projekcie powinna być teraz wyświetlana w Eksploratorze rozwiązań.  
  
7.  Otwórz plik manifestu Package.appx w projekcie.  
  
    1.  Znajdź \<TargetDeviceFamily > element. Zmień jego atrybuty MinVersion i MaxVersionTested, aby odpowiadać wersji Universal Windows Platform, która została zainstalowana. Jak to:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Zapisz zmiany.  
  
         Można teraz kodu, kompilacji i debugowania aplikacji.  
  
         W przypadku projektów testów jednostkowych dla aplikacji Universal Windows, należy również wykonać [te kroki](#MigrateUnitTest).  
  
##  <a name="MigrateUnitTest"></a> Zmiany wymagane do istniejących projektów testów jednostkowych dla aplikacji Universal Windows utworzonych za pomocą programu Visual Studio 2015 RC  
 Jeśli utworzono jednostkę projektów testów dla aplikacji uniwersalnych systemu Windows 10 za pomocą programu Visual Studio 2015 RC, musisz wprowadzić te dodatkowe zmiany do projektu pliki w celu korzystania z tych testów projektów za pomocą najnowszej wersji programu Visual Studio 2015. Zmiany wymagane są różne w zależności od języka, który został użyty do utworzenia aplikacji:  
  
-   [C# /VB aplikacji](#UnitTestRCUpdate10CSharp)  
  
-   [Aplikacje C++](#UnitTestRCUpdate10CPlusPlus)  
  
###  <a name="UnitTestRCUpdate10CSharp"></a> Aktualizowanie projektów testów jednostkowych języka C# /VB  
  
1. Za pomocą programu Visual Studio Otwórz swoje rozwiązanie, który zawiera projektu testu jednostkowego języka C# /VB. Zmień wartość właściwości \<OuttputType > element: AppContainerExe.  
  
   ```xml  
  
   <OutputType>AppContainerExe</OutputType>  
  
   ```  
  
2. Zamień ten element \<EnableCoreRuntime > false\</EnableCoreRuntime > za pomocą następującego elementu:  
  
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
  
4. Dodaj ten element \<UseDotNetNativeToolchain > wartość true,\</UseDotNetNativeToolchain > jako element podrzędny do tych grup właściwości:  
  
   ```xml  
  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">  
  
   ```  
  
5. Usuń następujące \<ItemGroup > elementy:  
  
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
  
    Zastąp je z następującymi elementami:  
  
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
  
6. Utwórz nowy projekt testów jednostkowych, a następnie skopiuj pliki UnitTestApp.xaml i UnitTestApp.xaml.cs z tego nowego projektu do Twojego istniejącego projektu testu jednostkowego, która jest aktualizowana.  
  
7. Skopiuj plik UnitTestApp.rd.xml z folderu właściwości nowy projekt testów jednostkowych w folderze właściwości Twojego istniejącego projektu testu jednostkowego, która jest aktualizowana.  
  
8. Otwórz plik manifestu Package.appx w projekcie. Następnie należy usunąć te elementy z niego:  
  
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
  
    Zastąp te elementy usunięte następujące elementy. Użyj wartości odpowiednich dla ProjectName na podstawie nazwy projektu, zamiast UnitTestProject1 w poniższych elementach:  
  
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
  
   Teraz możesz uruchomić testy jednostkowe.  
  
###  <a name="UnitTestRCUpdate10CPlusPlus"></a> Aktualizowanie projektów C++, aby używać najnowszej wersji uniwersalnej platformy Windows  
  
1.  Za pomocą programu Visual Studio Otwórz swoje rozwiązanie, który zawiera projektu testu jednostkowego języka C++. Usuń następujące elementy:  
  
    ```xml  
  
    <TestApplication>true</TestApplication>  
    <AppxPackage>True</AppxPackage>  
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>  
    <EnableCoreRuntime>false</EnableCoreRuntime>  
  
    ```  
  
2.  Dodaj następujący kod \<ProjectConfiguration > elementy poniżej tego elementu \<ItemGroup Label = "ProjectConfigurations" > Jeśli nie są już w tym fille:  
  
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
  
3.  Zastąp każde wystąpienie tego elementu:  
  
    ```xml  
  
    <ConfigurationType>DynamicLibrary</ConfigurationType>  
  
    ```  
  
     Na ten:  
  
    ```xml  
  
    <ConfigurationType>Application</ConfigurationType>  
  
    ```  
  
4.  Dodaj następujące \<PropertyGroup > elementy, jeśli nie są już w pliku:  
  
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
  
5.  Zastąp każde wystąpienie tego elementu:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
    ```  
  
     Na ten:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
  
    ```  
  
6.  Zastąp każde wystąpienie tego elementu:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
     Na ten:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
7.  Dodaj następujące \<ItemDefinitionGroup — > elementy w sekcji zawierającej już inne \<ItemDefinitionGroup — > elementy:  
  
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
  
8.  Usuń następujące \< ItemGroup > element:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\Logo.scale-100.png" />  
       <Image Include="Assets\SmallLogo.scale-100.png" />  
       <Image Include="Assets\StoreLogo.scale-100.png" />  
       <Image Include="Assets\SplashScreen.scale-100.png" />  
       <Image Include="Assets\WideLogo.scale-100.png" />  
    </ItemGroup>  
  
    ```  
  
     Zastąp go to \<ItemGroup > element:  
  
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
  
9. Usuń następujące \< ItemGroup > element:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
    </ItemGroup>  
    ```  
  
     Zastąp go te \<ItemGroup > elementy:  
  
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
  
10. Aby usunąć następującego elementu:  
  
    ```xml  
    <ClCompile Include="UnitTest.cpp"/>  
    ```  
  
     Zastąp go te \<CICompile > elementy:  
  
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
  
     Nad tym elementem w pliku:  
  
    ```xml  
  
    <ItemGroup>  
       <Xml Include="UnitTestApp.rd.xml" />  
    </ItemGroup>  
    ```  
  
12. Utwórz nowy projekt testu jednostki w języku C++, a następnie skopiuj pliki UnitTestApp.xaml, UnitTestApp.xaml.cpp, UnitTestApp.xaml.h i UnitTestApp.rd.xml z tego projektu do istniejącego projektu, która jest aktualizowana.  
  
13. Otwórz plik manifestu Package.appx w projekcie. Następnie należy usunąć te elementy z niego:  
  
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
  
     Zastąp te elementy usunięte następujące elementy. Użyj wartości odpowiednich dla ProjectName na podstawie nazwy projektu, zamiast UnitTestProject1 w poniższych elementach:  
  
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