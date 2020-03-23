---
title: Pomijanie ostrzeżeń kompilatora dla projektów i pakietów NuGet
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b604f6a1392353d304897a233b74c0d81fc258df
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114506"
---
# <a name="how-to-suppress-compiler-warnings"></a>Jak: Pomijanie ostrzeżeń kompilatora

Można odleskać dziennik kompilacji przez odfiltrowanie jednego lub więcej rodzajów ostrzeżenia kompilatora. Na przykład można przejrzeć tylko niektóre dane wyjściowe generowane po ustawieniu szczegółowości dziennika kompilacji na **Normalny,** **Szczegółowy**lub **Diagnostyczny**. Aby uzyskać więcej informacji na temat szczegółowości, zobacz [Jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Pomijanie określonych ostrzeżeń dla programu Visual C# lub F\#

Strona właściwości **Build** służy do pomijania określonych ostrzeżeń dla projektów języka C# i F#.

1. W **Eksploratorze rozwiązań**wybierz projekt, w którym chcesz pominąć ostrzeżenia.

1. Na pasku menu wybierz pozycję **Wyświetl** > **strony właściwości**.

1. Wybierz stronę **Kompilacja.**

1. W polu **Pomijaj ostrzeżenia** określ kody błędów ostrzeżeń, które mają zostać pominięte, oddzielone średnikami.

1. Ponownie skompiluj rozwiązanie.

## <a name="suppress-specific-warnings-for-c"></a>Pomijanie określonych ostrzeżeń dla języka C++

Strona **właściwości Właściwości konfiguracji służy** do wygaśania określonych ostrzeżeń dla projektów języka C++.

1. W **Eksploratorze rozwiązań**wybierz projekt lub plik źródłowy, w którym chcesz pominąć ostrzeżenia.

1. Na pasku menu wybierz pozycję **Wyświetl** > **strony właściwości**.

1. Wybierz **kategorię Właściwości konfiguracji,** wybierz kategorię **C/C++,** a następnie wybierz stronę **Zaawansowane.**

1. Wykonaj jedną z następujących czynności:

    - W polu **Wyłącz określone ostrzeżenia** określ kody błędów ostrzeżeń, które chcesz pominąć, oddzielone średnikiem.

    - W polu **Wyłącz określone ostrzeżenia** wybierz pozycję **Edytuj,** aby wyświetlić więcej opcji.

1. Wybierz przycisk **OK,** a następnie odbuduj rozwiązanie.

## <a name="suppress-warnings-for-visual-basic"></a>Pomijanie ostrzeżeń dla języka Visual Basic

Ostrzeżenia dotyczące kompilatora dla języka Visual Basic można ukryć, edytując plik *.vbproj* dla projektu. Aby pominąć ostrzeżenia według *kategorii,* można użyć [strony właściwości Compile](../ide/reference/compile-page-project-designer-visual-basic.md). Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Aby pominąć określone ostrzeżenia dla języka Visual Basic

W tym przykładzie pokazano, jak edytować plik *.vbproj,* aby pominąć ostrzeżenia określonego kompilatora.

1. W **Eksploratorze rozwiązań**wybierz projekt, w którym chcesz pominąć ostrzeżenia.

1. Na pasku menu wybierz pozycję **Project** > **Unload Project**.

1. W **Eksploratorze rozwiązań**otwórz menu po kliknięciu prawym przyciskiem myszy lub skróty dla projektu, a następnie wybierz polecenie **Edytuj \<nazwę projektu>.vbproj**.

    Plik projektu XML zostanie otwarty w edytorze kodu.

1. Zlokalizuj `<NoWarn>` element dla konfiguracji kompilacji, z którą tworzysz, i `<NoWarn>` dodaj jeden lub więcej numerów ostrzegawczych jako wartość elementu. Jeśli określisz wiele numerów ostrzegawczych, oddziel je przecinkiem.

     W poniższym `<NoWarn>` przykładzie przedstawiono element konfiguracji kompilacji *debugowania* na platformie x86, z dwoma ostrzeżeniami kompilatora pominiętymi:

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
   > Projekty .NET Core domyślnie nie zawierają grup właściwości konfiguracji kompilacji. Aby pominąć ostrzeżenia w projekcie .NET Core, należy ręcznie dodać sekcję konfiguracji kompilacji do pliku. Przykład:
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

1. Zapisz zmiany w pliku *.vbproj.*

1. Na pasku menu wybierz pozycję **Project** > **Reload Project**.

1. Na pasku menu wybierz pozycję **Build** > **Rebuild Solution**.

    Okno **Dane wyjściowe** nie wyświetla już ostrzeżeń, które zostały określone.

Aby uzyskać więcej informacji, zobacz [opcję kompilatora /nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) dla kompilatora wiersza polecenia języka Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Pomijanie ostrzeżeń dla pakietów NuGet

W niektórych przypadkach można pominąć ostrzeżenia kompilatora NuGet dla pojedynczego pakietu NuGet, a nie dla całego projektu. Ostrzeżenie służy celowi, więc nie chcesz pomijać go na poziomie projektu. Na przykład jeden z ostrzeżenia NuGet informuje, że pakiet może nie być w pełni zgodne z projektem. Jeśli pominąć go na poziomie projektu, a później dodać dodatkowy pakiet NuGet, nigdy nie wiadomo, czy było tworzenie ostrzeżenia zgodności.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Aby pominąć określone ostrzeżenie dla pojedynczego pakietu NuGet

1. W **Eksploratorze rozwiązań**wybierz pakiet NuGet, dla którego chcesz pominąć ostrzeżenia kompilatora.

   ![Pakiet NuGet w Eksploratorze rozwiązań](media/nuget-package-with-warning.png)

1. Z menu po kliknięciu prawym przyciskiem myszy lub w menu kontekstowym wybierz polecenie **Właściwości**.

1. W polu **NoWarn** właściwości pakietu wprowadź numer ostrzeżenia, który chcesz pominąć dla tego pakietu. Jeśli chcesz pominąć więcej niż jedno ostrzeżenie, użyj przecinka, aby oddzielić liczby ostrzeżeń.

   ![Właściwości pakietu NuGet](media/nuget-properties-nowarn.png)

   Ostrzeżenie zniknie z **Eksploratora rozwiązań** i **listy błędów**.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
- [Jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
