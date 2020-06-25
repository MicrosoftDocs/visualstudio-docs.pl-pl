---
title: Pomijaj ostrzeżenia kompilatora dla projektów i pakietów NuGet
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53db72495b64236441b9ce517c0eb25dc09a207c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283960"
---
# <a name="how-to-suppress-compiler-warnings"></a>Instrukcje: pomijanie ostrzeżeń kompilatora

Możesz wyrejestrować dziennik kompilacji, filtrując jeden lub więcej rodzajów ostrzeżeń kompilatora. Na przykład możesz chcieć przejrzeć tylko niektóre dane wyjściowe, które są generowane podczas ustawiania szczegółowości dziennika kompilacji na **normalne**, **szczegółowe**lub **diagnostyczne**. Aby uzyskać więcej informacji na temat szczegółowości, zobacz [jak: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Pomiń określone ostrzeżenia dla języka Visual C# lub F\#

Na stronie właściwości **kompilacja** można pominąć określone ostrzeżenia dla projektów C# i F #.

1. W **Eksplorator rozwiązań**wybierz projekt, w którym mają zostać pominięte ostrzeżenia.

1. Na pasku menu wybierz polecenie **Wyświetl**  >  **strony właściwości**.

1. Wybierz stronę **kompilacja** .

1. W polu **Pomiń ostrzeżenia** Określ kody błędów ostrzeżeń, które mają być pomijane, oddzielone średnikami.

1. Ponownie skompiluj rozwiązanie.

## <a name="suppress-specific-warnings-for-c"></a>Pomiń określone ostrzeżenia dla języka C++

Strona właściwości **Właściwości konfiguracji** służy do pomijania określonych ostrzeżeń dla projektów języka C++.

1. W **Eksplorator rozwiązań**wybierz projekt lub plik źródłowy, w którym mają zostać pominięte ostrzeżenia.

1. Na pasku menu wybierz polecenie **Wyświetl**  >  **strony właściwości**.

1. Wybierz kategorię **Właściwości konfiguracji** , wybierz kategorię **C/C++** , a następnie wybierz stronę **Zaawansowane** .

1. Wykonaj jedną z następujących czynności:

    - W polu **Wyłącz określone ostrzeżenia** Określ kody błędów ostrzeżeń, które mają zostać pominięte, oddzielone średnikami.

    - W polu **Wyłącz określone ostrzeżenia** wybierz pozycję **Edytuj** , aby wyświetlić więcej opcji.

1. Wybierz przycisk **OK** , a następnie Skompiluj ponownie rozwiązanie.

## <a name="suppress-warnings-for-visual-basic"></a>Pomiń ostrzeżenia dla Visual Basic

Można ukryć określone ostrzeżenia kompilatora dla Visual Basic, edytując plik *vbproj* dla projektu. Aby pominąć ostrzeżenia według *kategorii*, można użyć [strony właściwości kompilacji](../ide/reference/compile-page-project-designer-visual-basic.md). Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Aby pominąć określone ostrzeżenia dla Visual Basic

Ten przykład pokazuje, jak edytować plik *. vbproj* , aby pominąć określone ostrzeżenia kompilatora.

1. W **Eksplorator rozwiązań**wybierz projekt, w którym mają zostać pominięte ostrzeżenia.

1. Na pasku **menu wybierz projekt**  >  **Zwolnij**projekt.

1. W **Eksplorator rozwiązań**otwórz prawym przyciskiem myszy lub menu skrótów dla projektu, a następnie wybierz polecenie **Edytuj \<ProjectName> . vbproj**.

    Plik projektu XML zostanie otwarty w edytorze kodu.

1. Znajdź `<NoWarn>` element konfiguracji kompilacji, z którą tworzysz, i Dodaj co najmniej jedną liczbę ostrzegawczą jako wartość `<NoWarn>` elementu. Jeśli określisz wiele numerów ostrzeżeń, rozdziel je przecinkami.

     Poniższy przykład pokazuje `<NoWarn>` element konfiguracji kompilacji *debugowania* na platformie x86 z pominięciem dwóch ostrzeżeń kompilatora:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > Projekty .NET Core nie zawierają domyślnie grup właściwości konfiguracji kompilacji. Aby pominąć ostrzeżenia w projekcie .NET Core, należy ręcznie dodać sekcję Konfiguracja kompilacji do pliku. Przykład:
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. Zapisz zmiany w pliku *. vbproj* .

1. Na pasku **menu wybierz projekt**  >  **Załaduj ponownie**projekt.

1. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **Kompiluj ponownie rozwiązanie**.

    W oknie **danych wyjściowych** nie są już wyświetlane ostrzeżenia, które zostały określone przez użytkownika.

Aby uzyskać więcej informacji, zobacz [/nowarn — opcja kompilatora](/dotnet/visual-basic/reference/command-line-compiler/nowarn) dla kompilatora wiersza polecenia Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Pomijaj ostrzeżenia dla pakietów NuGet

W niektórych przypadkach może być konieczne pominięcie ostrzeżeń kompilatora NuGet dla jednego pakietu NuGet zamiast całego projektu. Ostrzeżenie służy do tego celu, więc nie trzeba go pomijać na poziomie projektu. Na przykład jedno z ostrzeżeń NuGet informuje o tym, że pakiet może nie być w pełni zgodny z projektem. W przypadku pominięcia na poziomie projektu i późniejszego dodania dodatkowego pakietu NuGet nigdy nie wiadomo, czy wystąpiło ostrzeżenie o zgodności.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Aby pominąć określone Ostrzeżenie dla pojedynczego pakietu NuGet

1. W **Eksplorator rozwiązań**wybierz pakiet NuGet, dla którego mają zostać pominięte ostrzeżenia kompilatora.

   ![Pakiet NuGet w Eksplorator rozwiązań](media/nuget-package-with-warning.png)

1. Z menu kontekstowego kliknij prawym przyciskiem myszy lub wybierz polecenie **Właściwości**.

1. W polu **nowarn** we właściwościach pakietu wprowadź numer ostrzegawczy, który ma zostać pominięty dla tego pakietu. Jeśli chcesz pominąć więcej niż jedno ostrzeżenie, użyj przecinka do oddzielenia numerów ostrzeżeń.

   ![Właściwości pakietu NuGet](media/nuget-properties-nowarn.png)

   Ostrzeżenie znika z **Eksplorator rozwiązań** i **Lista błędów**.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
- [Instrukcje: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
