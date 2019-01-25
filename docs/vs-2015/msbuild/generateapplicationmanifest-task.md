---
title: Generateapplicationmanifest — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 570f4d7ec459a961f2608557ce692029128ce4b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756587"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikacji lub manifest macierzysty. Manifest natywny zawiera opis składnika poprzez określenie unikatowej tożsamości składnika i identyfikację wszystkich zestawów i plików, które tworzą składnik. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikacji rozszerza manifest natywny przez wskazanie punktu wejścia aplikacji i określenie poziomu zabezpieczeń aplikacji.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GenerateApplicationManifest` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssemblyName`|Opcjonalnie `String` parametru.<br /><br /> Określa `Name` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa wynika z `EntryPoint` lub `InputManifest` parametrów. Jeśli nazwa nie można utworzyć, zadanie wyrzuca błąd.|  
|`AssemblyVersion`|Opcjonalnie `String` parametru.<br /><br /> Określa `Version` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, jest używana wartość domyślna "1.0.0.0".|  
|`ClrVersion`|Opcjonalnie `String` parametru.<br /><br /> Określa minimalną wersję z języka wspólnego środowiska uruchomieniowego (CLR) wymaganą przez aplikację. Wartość domyślna to wersja środowiska CLR używana przez system kompilacji. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany.|  
|`ConfigFile`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa, który element zawiera plik konfiguracji aplikacji. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany.|  
|`Dependencies`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa elementu listy, który definiuje zestaw zestawów zależnych dla wygenerowanego manifestu. Każdy element może być opisane przez metadane elementu, aby wskazać dodatkowy stan wdrożenia i typ zależności. Aby uzyskać więcej informacji zobacz sekcję "Element Metadnych" poniżej.|  
|`Description`|Opcjonalnie `String` parametru.<br /><br /> Określa opis dla aplikacji lub składnika.|  
|`EntryPoint`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa pojedynczy element, który wskazuje punkt wejścia dla wygenerowanego zestawu manifestu.<br /><br /> Aby uzyskać [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikacji, ten parametr określa zestaw, który rozpoczyna się, gdy aplikacja jest uruchomiona.|  
|`ErrorReportUrl`|Opcjonalne [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametr.<br /><br /> Określa adres URL strony sieci Web, która jest wyświetlana w oknach dialogowych podczas raportów błędu instalacji ClickOnce.|  
|`FileAssociations`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa listę typu pliku, które są skojarzone z manifestem wdrażania ClickOnce.<br /><br /> Skojarzenia plików poprawne tylko, tylko wtedy, gdy architekturą docelową jest .NET Framework 3.5 lub nowszy.|  
|`Files`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Pliki do dołączenia w manifeście. Określ pełną ścieżkę do każdego pliku.|  
|`HostInBrowser`|Opcjonalne [Boolean] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) parametr.<br /><br /> Jeśli `true`, aplikacja jest obsługiwana w przeglądarce (tak jak aplikacje przeglądarki sieci Web dla WPF).|  
|`IconFile`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Wskazuje plik ikony aplikacji. Ikona aplikacji jest wyrażona w manifeście aplikacji wygenerowanym i jest używany dla okna dialogowego Start Menu i Dodaj/Usuń programy. Jeśli wejście to nie jest określony, ikona domyślna jest używana. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany.|  
|`InputManifest`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Wskazuje dokument danych wejściowych XML, która będzie służyć jako podstawa do generatora manifestu. Dzięki temu dane strukturalnych, takie jak zabezpieczenia aplikacji lub niestandardowe definicje manifestu są odzwierciedlane w manifeście danych wyjściowych. Element główny dokumentu XML musi być zbiorem węzła trustinfo w obszarze nazw asmv1.|  
|`IsolatedComReferences`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa składniki COM do izolowania w manifeście. Ten parametr obsługuje możliwość izolowania składników COM wdrażania "Wolna rejestracja COM". Działa polega na automatycznym generowaniu manifestu ze standardowymi definicjami rejestracji com. Jednak składniki COM musi być zarejestrowana na komputerze kompilacji, aby działać prawidłowo.|  
|`ManifestType`|Opcjonalnie `String` parametru.<br /><br /> Określa, jakiego typu manifest wygenerować. Ten parametr może mieć następujące wartości:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Jeśli ten parametr nie jest określony, domyślnym zadaniem `ClickOnce`.|  
|`MaxTargetPath`|Opcjonalnie `String` parametru.<br /><br /> Określa dozwoloną maksymalną długość ścieżki pliku w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia aplikacji. Jeśli ta wartość jest określona, długość każdej ścieżki pliku w aplikacji jest sprawdzana względem tego limitu. Wszystkie elementy, które przekraczają limit wywołają ostrzeżenia kompilacji. Jeśli wejście to nie jest określona lub jest równe zeru, żadne sprawdzanie nie jest przeprowadzane. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany.|  
|`OSVersion`|Opcjonalnie `String` parametru.<br /><br /> Określa wersję minimalną wymaganego systemu operacyjnego (OS) wymagane przez aplikację. Na przykład wartość "5.1.2600.0" wskazuje, że system operacyjny Windows XP. Jeśli ten parametr nie jest określony, zostanie użyta wartość "4.10.0.0", która wskazuje Windows 98 Wydanie drugie, minimum obsługiwany system operacyjny programu .NET Framework. Jeśli zadanie generuje natywny manifest, ta wejściowa jest ignorowana.|  
|`OutputManifest`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę utworzonego wyjściowego pliku manifestu. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego wynika z tożsamości wygenerowanego manifestu.|  
|`Platform`|Opcjonalnie `String` parametru.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Jeśli ten parametr nie jest określony, domyślnym zadaniem `AnyCPU`.|  
|`Product`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa wynika z tożsamości wygenerowanego manifestu. Nazwa ta jest używaną nazwą skrótu w Start menu i jest częścią nazwy, która pojawia się w oknie dialogowym Dodaj lub usuń programy.|  
|`Publisher`|Opcjonalnie `String` parametru.<br /><br /> Określa wydawcę aplikacji. Jeśli ten parametr nie jest określony, nazwa wynika z zarejestrowanego użytkownika lub tożsamości wygenerowanego manifestu. Nazwa ta jest używaną nazwą folderu, w Start menu i jest częścią nazwy, która pojawia się w oknie dialogowym Dodaj lub usuń programy.|  
|`RequiresMinimumFramework35SP1`|Opcjonalnie `Boolean` parametru.<br /><br /> W przypadku opcji true, aplikacja wymaga .NET Framework 3.5 z dodatkiem SP1 lub nowsza wersja.|  
|`TargetCulture`|Opcjonalnie `String` parametru.<br /><br /> Identyfikuje kulturę aplikacji i określa `Language` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja jest kulturowo niezmienna.|  
|`TargetFrameworkMoniker`|Opcjonalnie <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Określa krótką nazwę platformy docelowej.|  
|`TargetFrameworkProfile`|Opcjonalnie <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Określa profil platformy docelowej.|  
|`TargetFrameworkSubset`|Opcjonalnie <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Określa nazwę podzbioru .NET Framework do obiektu docelowego.|  
|`TargetFrameworkVersion`|Opcjonalnie <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Określa docelową aplikację .NET Framework projektu.|  
|`TrustInfoFile`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Wskazuje dokument XML, który określa zabezpieczenia aplikacji. Element główny dokumentu XML musi być węzłem trustInfo w obszarze nazw asmv2. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany.|  
|`UseApplicationTrust`|Opcjonalnie <!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> W przypadku opcji true `Product`, `Publisher`, i `SupportUrl` właściwości są zapisywane w manifeście aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę parametrów klasy zadanie, zobacz [klasa podstawowa zadania](../msbuild/task-base-class.md).  
  
 Aby uzyskać informacje o sposobie używania `GenerateDeploymentManifest` zadań, zobacz [generateapplicationmanifest — zadanie](../msbuild/generateapplicationmanifest-task.md).  
  
 Dane wejściowe dla zależności i pliki mogą być dalej ozdobione metadanymi elementu, aby określić dodatkowy stan wdrożenia dla każdego elementu.  
  
## <a name="item-metadata"></a>Metadane elementu  
  
|Nazwa metadanych|Opis|  
|-------------------|-----------------|  
|`DependencyType`|Wskazuje, czy zależność jest opublikowana i zainstalowana z aplikacją lub warunkiem wstępnym. Te metadane obowiązuje w przypadku wszystkich zależności, ale nie jest używany do plików. Dostępne wartości dla tych metadanych są następujące:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Wartością domyślną jest instalacja.|  
|`AssemblyType`|Wskazuje, czy zależność jest zarządzany lub natywny zestaw. Te metadane obowiązuje w przypadku wszystkich zależności, ale nie jest używany do plików. Dostępne wartości dla tych metadanych są następujące:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` jest to wartość domyślna, co oznacza, że generator manifestu automatycznie określi typ zespołu.|  
|`Group`|Wskazuje grupę do pobierania dodatkowych plików na żądanie. Nazwa grupy jest zdefiniowany przez aplikację i może być dowolnym ciągiem. Pusty ciąg wskazuje, że plik nie jest częścią grupy pobrania, co jest ustawieniem domyślnym. Pliki nie w grupie są częścią pierwszego pobrania aplikacji. Pliki w grupie są pobierane tylko wtedy, gdy wyraźnie żąda tego aplikacja za pomocą <xref:System.Deployment.Application>.<br /><br /> Te metadane obowiązuje dla wszystkich plików gdzie `IsDataFile` jest `false` i wszystkie zależności gdzie `DependencyType` jest `Install`.|  
|`TargetPath`|Określa, jak ścieżka powinna być zdefiniowana w manifeście. Ten atrybut jest ważny dla wszystkich plików. Jeśli ten atrybut nie jest określony, Specyfikacja elementu jest używana. Ten atrybut jest ważny dla wszystkich plików i współzależności z `DependencyType` wartość `Install`.|  
|`IsDataFile`|A `Boolean` wartość metadanych, która wskazuje, czy plik jest plikiem danych. Plik danych jest wyjątkowy, w tym, że jest on przenoszony między aktualizacjami aplikacji. Te metadane obowiązuje tylko dla plików. `False` jest to wartość domyślna.|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `GenerateApplicationManifest` zadania do wygenerowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikacji i `GenerateDeploymentManifest` zadania do wygenerowania wdrażania manifestu dla aplikacji z pojedynczym zestawem. Następnie używa `SignFile` zadania do podpisania manifestów.  
  
 Obrazuje to najprostszy scenariusz możliwości generowania manifestu gdzie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] w jednym programie są generowane manifesty. Domyślna nazwa i tożsamość są dedukowane z zestawu dla manifestu.  
  
> [!NOTE]
>  W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie zbudowaną w celu skupiania się na aspektach generacji manifestu. Ten przykład generuje w pełni pracujące [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat `Thumbprint` właściwości używane w `SignFile` zadań w tym przykładzie, zobacz [signfile — zadanie](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `GenerateApplicationManifest` i `GenerateDeploymentManifest` do wygenerowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] stosowania i wdrażania manifestów aplikacji z jednego zestawu, określając nazwę tożsamości manifestów.  
  
 Ten przykład jest podobny do poprzedniego przykładu, z wyjątkiem jawnie określonej nazwy i tożsamości manifestów. Ponadto ten przykład jest konfigurowany jako aplikacja online zamiast zainstalowanej aplikacji.  
  
> [!NOTE]
>  W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie zbudowaną w celu skupiania się na aspektach generacji manifestu. Ten przykład generuje w pełni pracujące [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat `Thumbprint` właściwości używane w `SignFile` zadań w tym przykładzie, zobacz [signfile — zadanie](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `GenerateApplicationManifest` i `GenerateDeploymentManifest` do wygenerowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] stosowania i wdrażania manifestów aplikacji z wielu plików i zestawów.  
  
> [!NOTE]
>  W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie zbudowaną w celu skupiania się na aspektach generacji manifestu. Ten przykład generuje w pełni pracujące [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat `Thumbprint` właściwości używane w `SignFile` zadań w tym przykładzie, zobacz [signfile — zadanie](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `GenerateApplicationManifest` zadania, aby wygenerować macierzysty manifest aplikacji Test.exe, odwołuje się do macierzystych Alpha.dll i wyizolowanego modelu COM składnika Bravo.dll.  
  
 Ten przykład generuje Test.exe.manifest, dzięki czemu aplikacja XCOPY możliwych do wdrożenia, korzystając z rejestracji wolnego modelu COM.  
  
> [!NOTE]
>  W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie zbudowaną w celu skupiania się na aspektach generacji manifestu. Ten przykład generuje w pełni pracujące [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia.  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)   
 [Signfile — zadanie](../msbuild/signfile-task.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
