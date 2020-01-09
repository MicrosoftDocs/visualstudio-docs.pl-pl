---
title: GenerateApplicationManifest — — zadanie | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 446f4728f92d5a486afea1a7c03c8d5006690bfc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589308"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest — zadanie
Generuje manifest aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lub natywny manifest. Manifest natywny opisuje składnik, definiując unikatową tożsamość dla składnika i identyfikując wszystkie zestawy i pliki tworzące składnik. Manifest aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rozszerza natywny manifest przez wskazanie punktu wejścia aplikacji i określenie poziomu zabezpieczeń aplikacji.

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry zadania `GenerateApplicationManifest`.

| Parametr | Opis |
|---------------------------------| - |
| `AssemblyName` | Opcjonalny parametr `String`.<br /><br /> Określa pole `Name` tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana na podstawie parametrów `EntryPoint` lub `InputManifest`. Jeśli nie można utworzyć nazwy, zadanie zgłosi błąd. |
| `AssemblyVersion` | Opcjonalny parametr `String`.<br /><br /> Określa pole `Version` tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zostanie użyta domyślna wartość "1.0.0.0". |
| `ClrVersion` | Opcjonalny parametr `String`.<br /><br /> Określa minimalną wersję środowiska uruchomieniowego języka wspólnego (CLR) wymaganą przez aplikację. Wartość domyślna to wersja środowiska CLR używana przez system kompilacji. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany. |
| `ConfigFile` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa, który element zawiera plik konfiguracji aplikacji. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany. |
| `Dependencies` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa listę elementów, która definiuje zestaw zestawów zależnych dla wygenerowanego manifestu. Każdy element może być dokładniej opisany przez metadane elementu, aby wskazać dodatkowy stan wdrożenia i typ zależności. Aby uzyskać więcej informacji, zobacz [metadane elementu](#item-metadata). |
| `Description` | Opcjonalny parametr `String`.<br /><br /> Określa opis aplikacji lub składnika. |
| `EntryPoint` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa pojedynczy element, który wskazuje punkt wejścia dla wygenerowanego zestawu manifestu.<br /><br /> W przypadku manifestu aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ten parametr określa zestaw, który jest uruchamiany, gdy aplikacja jest uruchamiana. |
| `ErrorReportUrl` | Opcjonalny parametr <xref:System.String?displayProperty=fullName>.<br /><br /> Określa adres URL strony sieci Web, która jest wyświetlana w oknach dialogowych podczas raportów o błędach w instalacjach technologii ClickOnce. |
| `FileAssociations` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa listę typów plików, które są skojarzone z manifestem wdrażania ClickOnce.<br /><br /> Skojarzenia plików są prawidłowe tylko wtedy, gdy jest wskazywany .NET Framework 3,5 lub nowszy. |
| `Files` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Pliki do uwzględnienia w manifeście. Określ pełną ścieżkę każdego pliku. |
| `HostInBrowser` | Opcjonalny parametr <xref:System.Boolean>.<br /><br /> Jeśli `true`, aplikacja jest hostowana w przeglądarce (w przypadku aplikacji przeglądarki sieci Web WPF). |
| `IconFile` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Wskazuje plik ikony aplikacji. Ikona aplikacji jest wyrażona w wygenerowanym manifeście aplikacji i jest używana dla **menu Start** i okna dialogowego **Dodaj/Usuń programy** . Jeśli dane wejściowe nie są określone, zostanie użyta ikona domyślna. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany. |
| `InputManifest` | Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Wskazuje wejściowy dokument XML, który ma stanowić podstawę dla generatora manifestów. Dzięki temu dane strukturalne, takie jak zabezpieczenia aplikacji lub niestandardowe definicje manifestu, są uwzględniane w manifeście danych wyjściowych. Element główny w dokumencie XML musi być węzłem zestawu w przestrzeni nazw asmv1. |
| `IsolatedComReferences` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa składniki COM do wyizolowania w wygenerowanym manifeście. Ten parametr obsługuje możliwość izolowania składników modelu COM dla wdrożenia "Rejestracja wolnego modelu COM". Działa on przez Autogenerowanie manifestu ze standardowymi definicjami rejestracji modelu COM. Jednak składniki COM muszą być zarejestrowane na maszynie kompilacji, aby zapewnić prawidłowe działanie. |
| `ManifestType` | Opcjonalny parametr `String`.<br /><br /> Określa typ manifestu do wygenerowania. Ten parametr może mieć następujące wartości:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Jeśli ten parametr nie jest określony, domyślnie zostanie `ClickOnce`. |
| `MaxTargetPath` | Opcjonalny parametr `String`.<br /><br /> Określa maksymalną dozwoloną długość ścieżki pliku w ramach wdrożenia aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Jeśli ta wartość jest określona, długość każdej ścieżki pliku w aplikacji jest sprawdzana względem tego limitu. Wszystkie elementy, które przekraczają limit, zostaną zgłoszone w ostrzeżeniu kompilacji. Jeśli nie określono tego parametru wejściowego lub wartość jest równa zero, sprawdzanie nie jest przeprowadzane. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany. |
| `OSVersion` | Opcjonalny parametr `String`.<br /><br /> Określa minimalną wymaganą wersję systemu operacyjnego (OS) wymaganą przez aplikację. Na przykład wartość "5.1.2600.0" wskazuje system operacyjny Windows XP. Jeśli ten parametr nie jest określony, zostanie użyta wartość "4.10.0.0", która wskazuje na system Windows 98 Second Edition, minimalną obsługiwaną wersję systemu operacyjnego .NET Framework. Jeśli zadanie generuje natywny manifest, dane wejściowe zostaną zignorowane. |
| `OutputManifest` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę wygenerowanego pliku manifestu wyjściowego. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego jest wywnioskowana z tożsamości wygenerowanego manifestu. |
| `Platform` | Opcjonalny parametr `String`.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Jeśli ten parametr nie jest określony, domyślnie zostanie `AnyCPU`. |
| `Product` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana z tożsamości wygenerowanego manifestu. Ta nazwa jest używana jako nazwa skrótu w menu **Start** i jest częścią nazwy, która pojawia się w oknie dialogowym **Dodaj lub usuń programy** . |
| `Publisher` | Opcjonalny parametr `String`.<br /><br /> Określa wydawcę aplikacji. Jeśli ten parametr nie jest określony, nazwa zostanie wywnioskowana z zarejestrowanego użytkownika lub tożsamość wygenerowanego manifestu. Ta nazwa jest używana jako nazwa folderu w menu **Start** i jest częścią nazwy, która pojawia się w oknie dialogowym **Dodaj lub usuń programy** . |
| `RequiresMinimumFramework35SP1` | Opcjonalny parametr `Boolean`.<br /><br /> W przypadku wartości true aplikacja wymaga .NET Framework 3,5 z dodatkiem SP1 lub nowszej wersji. |
| `TargetCulture` | Opcjonalny parametr `String`.<br /><br /> Identyfikuje kulturę aplikacji i określa pole `Language` tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja ma niezmienną kulturę. |
| `TargetFrameworkMoniker` | Opcjonalny parametr `String`.<br /><br /> Określa moniker platformy docelowej. |
| `TargetFrameworkProfile` | Opcjonalny parametr `String`.<br /><br /> Określa Profil platformy docelowej. |
| `TargetFrameworkSubset` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę podzbioru .NET Framework, który ma być obiektem docelowym. |
| `TargetFrameworkVersion` | Opcjonalny parametr `String`.<br /><br /> Określa .NET Framework docelowy projektu. |
| `TrustInfoFile` | Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Wskazuje dokument XML, który określa zabezpieczenia aplikacji. Element główny w dokumencie XML musi być węzłem trustInfo w przestrzeni nazw asmv2. Jeśli zadanie generuje natywny manifest, ten parametr jest ignorowany. |
| `UseApplicationTrust` | Opcjonalny parametr `Boolean`.<br /><br /> W przypadku wartości true właściwości `Product`, `Publisher`i `SupportUrl` są zapisywane w manifeście aplikacji. |

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.GenerateManifestBase>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą parametrów klasy Task, zobacz [Klasa bazowa zadania](../msbuild/task-base-class.md).

Aby uzyskać informacje dotyczące sposobu korzystania z zadania `GenerateDeploymentManifest`, zobacz [zadanie GenerateApplicationManifest —](../msbuild/generateapplicationmanifest-task.md).

Dane wejściowe dla zależności i plików mogą być dodatkowo uzupełnione o metadane elementu, aby określić dodatkowy stan wdrożenia dla każdego elementu.

## <a name="item-metadata"></a>Metadane elementu

|Nazwa metadanych|Opis|
|-------------------|-----------------|
|`DependencyType`|Wskazuje, czy zależność jest publikowana i instalowana z aplikacją lub wymaganiem wstępnym. Te metadane są prawidłowe dla wszystkich zależności, ale nie są używane dla plików. Dostępne wartości dla tych metadanych to:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Wartość domyślna to Install.|
|`AssemblyType`|Wskazuje, czy zależność jest zestawem zarządzanym, czy natywnym. Te metadane są prawidłowe dla wszystkich zależności, ale nie są używane dla plików. Dostępne wartości dla tych metadanych to:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` jest wartością domyślną, co oznacza, że Generator manifestu określi typ zestawu automatycznie.|
|`Group`|Wskazuje grupę do pobrania dodatkowych plików na żądanie. Nazwa grupy jest definiowana przez aplikację i może być dowolnym ciągiem. Pusty ciąg wskazuje, że plik nie jest częścią grupy pobierania, co jest ustawieniem domyślnym. Pliki, które nie znajdują się w grupie, są częścią pobierania początkowej aplikacji. Pliki w grupie są pobierane tylko wtedy, gdy aplikacja zostanie jawnie zażądana przy użyciu <xref:System.Deployment.Application>.<br /><br /> Te metadane są prawidłowe dla wszystkich plików, w których `IsDataFile` jest `false` i wszystkich zależności, w których `DependencyType` jest `Install`.|
|`TargetPath`|Określa sposób definiowania ścieżki w wygenerowanym manifeście. Ten atrybut jest prawidłowy dla wszystkich plików. Jeśli ten atrybut nie jest określony, Specyfikacja elementu jest używana. Ten atrybut jest prawidłowy dla wszystkich plików i zależności z `DependencyType` wartością `Install`.|
|`IsDataFile`|Wartość metadanych `Boolean`, która wskazuje, czy plik jest plikiem danych. Plik danych jest specjalny w tym, że jest migrowany między aktualizacjami aplikacji. Te metadane są prawidłowe tylko dla plików. `False` jest wartością domyślną.|

## <a name="example"></a>Przykład
Ten przykład używa zadania `GenerateApplicationManifest` do wygenerowania manifestu aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i zadania `GenerateDeploymentManifest` w celu wygenerowania manifestu wdrożenia dla aplikacji z pojedynczym zestawem. Następnie używa zadania `SignFile` do podpisania manifestów.

Ilustruje to najprostszy możliwy scenariusz generowania manifestu, w którym są generowane [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestów dla pojedynczego programu. Nazwa domyślna i tożsamość są wywnioskowane z zestawu dla manifestu.

> [!NOTE]
> W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie skompilowane w celu skoncentrowania się na aspektach generowania manifestu. Ten przykład powoduje utworzenie w pełni działającego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.
>
> [!NOTE]
> Aby uzyskać więcej informacji na temat właściwości `Thumbprint` używanej w zadaniu `SignFile` w tym przykładzie, zobacz [SignFile — Task](../msbuild/signfile-task.md).

```xml
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
Ten przykład używa zadań `GenerateApplicationManifest` i `GenerateDeploymentManifest` do generowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i manifestów wdrożenia dla aplikacji z pojedynczym zestawem, określając nazwę i tożsamość manifestów.

Ten przykład jest podobny do poprzedniego przykładu, z wyjątkiem tego, że nazwa i tożsamość manifestów są jawnie określone. Ponadto ten przykład jest konfigurowany jako aplikacja online zamiast zainstalowanej aplikacji.

> [!NOTE]
> W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie skompilowane w celu skoncentrowania się na aspektach generowania manifestu. Ten przykład powoduje utworzenie w pełni działającego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.
>
> [!NOTE]
> Aby uzyskać więcej informacji na temat właściwości `Thumbprint` używanej w zadaniu `SignFile` w tym przykładzie, zobacz [SignFile — Task](../msbuild/signfile-task.md).

```xml
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
Ten przykład używa `GenerateApplicationManifest` i `GenerateDeploymentManifest` zadań do generowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i manifestów wdrożenia dla aplikacji z wieloma plikami i zestawami.

> [!NOTE]
> W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie skompilowane w celu skoncentrowania się na aspektach generowania manifestu. Ten przykład powoduje utworzenie w pełni działającego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.
>
> [!NOTE]
> Aby uzyskać więcej informacji na temat właściwości `Thumbprint` używanej w zadaniu `SignFile` w tym przykładzie, zobacz [SignFile — Task](../msbuild/signfile-task.md).

```xml
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
Ten przykład używa zadania `GenerateApplicationManifest`, aby wygenerować natywny manifest dla aplikacji *test. exe*, który odwołuje się do natywnego składnika *alfa. dll* i izolowanego składnika com *Bravo. dll*.

W tym przykładzie jest tworzony *test. exe. manifest*, dzięki czemu aplikacja xcopy jest wdrażana i korzysta z bezpłatnej rejestracji com.

> [!NOTE]
> W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie skompilowane w celu skoncentrowania się na aspektach generowania manifestu. Ten przykład powoduje utworzenie w pełni działającego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.

```xml
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

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [GenerateDeploymentManifest —, zadanie](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile —, zadanie](../msbuild/signfile-task.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
