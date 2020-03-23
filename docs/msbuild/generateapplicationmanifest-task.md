---
title: Generowaniezarządzaniezaj zadania | Dokumenty firmy Microsoft
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
ms.openlocfilehash: f77420c5ab269e1b0052ce6102c4e3196a3be52b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634100"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest — zadanie

Generuje manifest aplikacji ClickOnce lub manifest macierzysty. Manifest macierzysty opisuje składnik, definiując unikatową tożsamość składnika i identyfikując wszystkie zestawy i pliki, które tworzą składnik. Manifest aplikacji ClickOnce rozszerza manifest macierzysty, wskazując punkt wejścia aplikacji i określając poziom zabezpieczeń aplikacji.

## <a name="parameters"></a>Parametry

W poniższej tabeli `GenerateApplicationManifest` opisano parametry zadania.

| Parametr | Opis |
|---------------------------------| - |
| `AssemblyName` | Parametr `String` opcjonalny.<br /><br /> Określa `Name` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa `EntryPoint` jest `InputManifest` wywnioskowana z lub parametrów. Jeśli nie można utworzyć nazwy, zadanie zgłasza błąd. |
| `AssemblyVersion` | Parametr `String` opcjonalny.<br /><br /> Określa `Version` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, używana jest domyślna wartość "1.0.0.0". |
| `ClrVersion` | Parametr `String` opcjonalny.<br /><br /> Określa minimalną wersję środowiska wykonawczego języka wspólnego (CLR) wymaganą przez aplikację. Wartością domyślną jest wersja CLR używana przez system kompilacji. Jeśli zadanie generuje manifest macierzysty, ten parametr jest ignorowany. |
| `ConfigFile` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa, który element zawiera plik konfiguracji aplikacji. Jeśli zadanie generuje manifest macierzysty, ten parametr jest ignorowany. |
| `Dependencies` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa listę elementów, która definiuje zestaw zestawów zależnych dla wygenerowanego manifestu. Każdy element może być dalej opisane przez metadane elementu, aby wskazać dodatkowy stan wdrożenia i typ zależności. Aby uzyskać więcej informacji, zobacz [Metadane elementu](#item-metadata). |
| `Description` | Parametr `String` opcjonalny.<br /><br /> Określa opis aplikacji lub składnika. |
| `EntryPoint` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa pojedynczy element, który wskazuje punkt wejścia dla wygenerowanego zestawu manifestu.<br /><br /> W przypadku manifestu aplikacji ClickOnce ten parametr określa zestaw, który rozpoczyna się po uruchomieniu aplikacji. |
| `ErrorReportUrl` | Parametr <xref:System.String?displayProperty=fullName> opcjonalny.<br /><br /> Określa adres URL strony sieci Web, który jest wyświetlany w oknach dialogowych podczas raportów o błędach w instalacjach ClickOnce. |
| `FileAssociations` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa listę jednego lub więcej typów plików skojarzonych z manifestem wdrażania ClickOnce.<br /><br /> Skojarzenia plików są prawidłowe tylko wtedy, gdy jest ukierunkowany na programy .NET Framework 3.5 lub nowsze. |
| `Files` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Pliki do uwzględnienia w manifeście. Określ pełną ścieżkę dla każdego pliku. |
| `HostInBrowser` | Parametr <xref:System.Boolean> opcjonalny.<br /><br /> Jeśli `true`aplikacja jest hostowana w przeglądarce (podobnie jak aplikacje przeglądarki sieci Web WPF). |
| `IconFile` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Wskazuje plik ikony aplikacji. Ikona aplikacji jest wyrażona w wygenerowanym manifeście aplikacji i jest używana w oknie dialogowym **Menu Start** i **Dodaj/Usuń programy.** Jeśli to dane wejściowe nie są określone, używana jest domyślna ikona. Jeśli zadanie generuje manifest macierzysty, ten parametr jest ignorowany. |
| `InputManifest` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Wskazuje wejściowy dokument XML, który ma służyć jako podstawa generatora manifestów. Dzięki temu ustrukturyzowane dane, takie jak zabezpieczenia aplikacji lub niestandardowe definicje manifestu, które mają być odzwierciedlane w manifeście danych wyjściowych. Element główny w dokumencie XML musi być węzłem zestawu w obszarze nazw asmv1. |
| `IsolatedComReferences` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa składniki COM do wyizolowania w wygenerowanym manifeście. Ten parametr obsługuje możliwość izolowania składników COM dla wdrożenia "Rejestracja wolna COM". Działa poprzez automatyczne generowanie manifestu ze standardowymi definicjami rejestracji COM. Jednak składniki COM muszą być zarejestrowane na komputerze kompilacji, aby to działało poprawnie. |
| `ManifestType` | Parametr `String` opcjonalny.<br /><br /> Określa typ manifestu do wygenerowania. Ten parametr może mieć następujące wartości:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Jeśli ten parametr nie jest określony, `ClickOnce`zadanie domyślnie ma wartość . |
| `MaxTargetPath` | Parametr `String` opcjonalny.<br /><br /> Określa maksymalną dopuszczalną długość ścieżki pliku we wdrożeniu aplikacji ClickOnce. Jeśli ta wartość jest określona, długość każdej ścieżki pliku w aplikacji jest sprawdzana względem tego limitu. Wszystkie elementy, które przekraczają limit zostanie podnieść w ostrzeżeniu kompilacji. Jeśli to dane wejściowe nie jest określony lub wynosi zero, a następnie nie jest wykonywane sprawdzanie. Jeśli zadanie generuje manifest macierzysty, ten parametr jest ignorowany. |
| `OSVersion` | Parametr `String` opcjonalny.<br /><br /> Określa minimalną wymaganą wersję systemu operacyjnego (OS) wymaganą przez aplikację. Na przykład wartość "5.1.2600.0" wskazuje, że system operacyjny to Windows XP. Jeśli ten parametr nie jest określony, używana jest wartość "4.10.0.0", która wskazuje windows 98 Second Edition, minimalny obsługiwany system operacyjny programu .NET Framework. Jeśli zadanie generuje manifest macierzysty, to dane wejściowe są ignorowane. |
| `OutputManifest` | Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Określa nazwę wygenerowanego pliku manifestu wyjściowego. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego jest wywnioskowana z tożsamości wygenerowanego manifestu. |
| `Platform` | Parametr `String` opcjonalny.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Jeśli ten parametr nie jest określony, `AnyCPU`zadanie domyślnie ma wartość . |
| `Product` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana z tożsamości wygenerowanego manifestu. Ta nazwa jest używana dla nazwy skrótu w menu **Start** i jest częścią nazwy wyświetlanej w oknie dialogowym **Dodawanie lub usuwanie programów.** |
| `Publisher` | Parametr `String` opcjonalny.<br /><br /> Określa wydawcę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana od zarejestrowanego użytkownika lub tożsamości wygenerowanego manifestu. Ta nazwa jest używana dla nazwy folderu w menu **Start** i jest częścią nazwy wyświetlanej w oknie dialogowym **Dodawanie lub usuwanie programów.** |
| `RequiresMinimumFramework35SP1` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli true, aplikacja wymaga .NET Framework 3.5 SP1 lub nowszej wersji. |
| `TargetCulture` | Parametr `String` opcjonalny.<br /><br /> Identyfikuje kulturę aplikacji i określa `Language` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja jest niezmienna kultury. |
| `TargetFrameworkMoniker` | Parametr `String` opcjonalny.<br /><br /> Określa moniker struktury docelowej. |
| `TargetFrameworkProfile` | Parametr `String` opcjonalny.<br /><br /> Określa docelowy profil struktury. |
| `TargetFrameworkSubset` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę podzbioru programu .NET Framework do docelowego. |
| `TargetFrameworkVersion` | Parametr `String` opcjonalny.<br /><br /> Określa docelową platformę .NET Framework projektu. |
| `TrustInfoFile` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Wskazuje dokument XML określający bezpieczeństwo aplikacji. Element główny w dokumencie XML musi być węzłem zaufaniaInfo w obszarze nazw asmv2. Jeśli zadanie generuje manifest macierzysty, ten parametr jest ignorowany. |
| `UseApplicationTrust` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli true, `Product` `Publisher`, `SupportUrl` i właściwości są zapisywane w manifeście aplikacji. |

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę parametrów klasy zadań, zobacz [Klasa podstawowa zadania](../msbuild/task-base-class.md).

Aby uzyskać informacje dotyczące `GenerateDeploymentManifest` korzystania z zadania, zobacz [GenerateApplicationManifest task](../msbuild/generateapplicationmanifest-task.md).

Dane wejściowe dla zależności i plików mogą być dodatkowo ozdobione metadanymi elementu, aby określić dodatkowy stan wdrożenia dla każdego elementu.

## <a name="item-metadata"></a>Metadane elementu

|Nazwa metadanych|Opis|
|-------------------|-----------------|
|`DependencyType`|Wskazuje, czy zależność jest publikowana i instalowana z aplikacją, czy z warunkiem wstępnym. Te metadane są prawidłowe dla wszystkich zależności, ale nie są używane dla plików. Dostępne wartości dla tych metadanych to:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Install jest wartością domyślną.|
|`AssemblyType`|Wskazuje, czy zależność jest zestawem zarządzanym, czy natywnym. Te metadane są prawidłowe dla wszystkich zależności, ale nie są używane dla plików. Dostępne wartości dla tych metadanych to:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified`jest wartością domyślną, która wskazuje, że generator manifestu automatycznie określi typ złożenia.|
|`Group`|Wskazuje grupę pobierania dodatkowych plików na żądanie. Nazwa grupy jest zdefiniowana przez aplikację i może być dowolnym ciągiem. Pusty ciąg wskazuje, że plik nie jest częścią grupy pobierania, która jest domyślna. Pliki nie w grupie są częścią początkowego pobierania aplikacji. Pliki w grupie są pobierane tylko wtedy, gdy <xref:System.Deployment.Application>aplikacja wyraźnie zażąda tego za pomocą programu .<br /><br /> Te metadane są prawidłowe `false` dla wszystkich `DependencyType` plików, gdzie `IsDataFile` jest i wszystkie zależności, gdzie jest `Install`.|
|`TargetPath`|Określa sposób definiowania ścieżki w wygenerowanym manifeście. Ten atrybut jest prawidłowy dla wszystkich plików. Jeśli ten atrybut nie jest określony, używana jest specyfikacja towaru. Ten atrybut jest prawidłowy dla wszystkich `DependencyType` plików `Install`i zależności o wartości .|
|`IsDataFile`|Wartość `Boolean` metadanych, która wskazuje, czy plik jest plikiem danych. Plik danych jest specjalny, ponieważ jest migrowany między aktualizacjami aplikacji. Te metadane są prawidłowe tylko dla plików. `False`jest wartością domyślną.|

## <a name="example"></a>Przykład

W tym przykładzie `GenerateApplicationManifest` użyto zadania do wygenerowania `GenerateDeploymentManifest` manifestu aplikacji ClickOnce i zadania do wygenerowania manifestu wdrożenia dla aplikacji z jednym zestawem. Następnie używa `SignFile` zadania do podpisania manifestów.

Ilustruje to najprostszy możliwy scenariusz generowania manifestu, w którym manifesty ClickOnce są generowane dla pojedynczego programu. Domyślna nazwa i tożsamość są wnioskowane z zestawu dla manifestu.

> [!NOTE]
> W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie utworzone, aby skupić się na aspektach generowania manifestu. W tym przykładzie tworzy w pełni działające wdrożenie ClickOnce.
>
> [!NOTE]
> Aby uzyskać więcej `Thumbprint` informacji na `SignFile` temat właściwości używanej w zadaniu w tym przykładzie, zobacz [Zadanie SignFile](../msbuild/signfile-task.md).

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

W tym przykładzie użyto `GenerateApplicationManifest` i `GenerateDeploymentManifest` zadania do generowania ClickOnce aplikacji i manifestów wdrażania dla aplikacji z jednego zestawu, określając nazwę i tożsamość manifestów.

Ten przykład jest podobny do poprzedniego przykładu, z wyjątkiem nazwy i tożsamości manifestów są jawnie określone. Ponadto w tym przykładzie jest skonfigurowany jako aplikacja online zamiast zainstalowanej aplikacji.

> [!NOTE]
> W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie utworzone, aby skupić się na aspektach generowania manifestu. W tym przykładzie tworzy w pełni działające wdrożenie ClickOnce.
>
> [!NOTE]
> Aby uzyskać więcej `Thumbprint` informacji na `SignFile` temat właściwości używanej w zadaniu w tym przykładzie, zobacz [Zadanie SignFile](../msbuild/signfile-task.md).

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

W tym `GenerateApplicationManifest` przykładzie `GenerateDeploymentManifest` użyto i zadania do generowania ClickOnce aplikacji i manifestów wdrażania dla aplikacji z wielu plików i zestawów.

> [!NOTE]
> W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie utworzone, aby skupić się na aspektach generowania manifestu. W tym przykładzie tworzy w pełni działające wdrożenie ClickOnce.
>
> [!NOTE]
> Aby uzyskać więcej `Thumbprint` informacji na `SignFile` temat właściwości używanej w zadaniu w tym przykładzie, zobacz [Zadanie SignFile](../msbuild/signfile-task.md).

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

W tym `GenerateApplicationManifest` przykładzie użyto tego zadania do wygenerowania manifestu macierzystego dla aplikacji *Test.exe*, odwołując się do składnika natywnego *Alpha.dll* i izolowanego składnika COM *Bravo.dll*.

W tym przykładzie tworzy *Test.exe.manifest*, dzięki czemu aplikacja XCOPY można wdrożyć i korzystając z rejestracji wolne COM.

> [!NOTE]
> W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie utworzone, aby skupić się na aspektach generowania manifestu. W tym przykładzie tworzy w pełni działające wdrożenie ClickOnce.

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

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [GenerateDeploymentManifest zadanie](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile zadanie](../msbuild/signfile-task.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
