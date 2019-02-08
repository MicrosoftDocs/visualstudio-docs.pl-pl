---
title: Pomijanie ostrzeżeń kompilatora dla projektów i pakiety NuGet
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7e9f995c8fc1107da7bc90b230eddc265e6082b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913135"
---
# <a name="how-to-suppress-compiler-warnings"></a>Instrukcje: Pomijanie ostrzeżeń kompilatora

W dzienniku kompilacji mogą declutter przez filtrowanie jednego lub więcej rodzajów ostrzeżeń kompilatora. Na przykład możesz chcieć przejrzeć tylko niektóre z danych wyjściowych, który jest generowany, gdy poziom szczegółowości dziennika kompilacji jest ustawiona na **normalny**, **szczegółowe**, lub **diagnostycznych**. Aby uzyskać więcej informacji na temat poziomu szczegółowości, zobacz [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Pomiń określone ostrzeżenia dla wizualizacji C# lubF# #

Użyj **kompilacji** stronę właściwości i pomijanie określonych ostrzeżeń dla C# i F# projektów.

1. W **Eksploratora rozwiązań**, wybierz projekt, w którym chcesz pominąć ostrzeżenia.

1. Na pasku menu wybierz **widoku** > **stron właściwości**.

1. Wybierz **kompilacji** strony.

1. W **pomijanie ostrzeżeń** Określ kody błędów, ostrzeżeń, które chcesz pominąć, oddzielając je średnikami.

1. Ponownie skompiluj rozwiązanie.

## <a name="suppress-specific-warnings-for-visual-c"></a>Pomiń określone ostrzeżenia dla języka Visual C++

Użyj **właściwości konfiguracji** stronę właściwości i pomijanie określonych ostrzeżeń dla projektów w języku C++.

1. W **Eksploratora rozwiązań**, wybierz projekt lub pliku, w którym chcesz pominąć ostrzeżenia źródła.

1. Na pasku menu wybierz **widoku** > **stron właściwości**.

1. Wybierz **właściwości konfiguracji** kategorii, wybierz **C/C++** kategorii, a następnie wybierz **zaawansowane** strony.

1. Wykonaj jedną z następujących czynności:

    - W **Wyłącz określone ostrzeżenia** Określ kody błędów, ostrzeżeń, które chcesz pominąć, rozdzielając je średnikiem.

    - W **Wyłącz określone ostrzeżenia** wybierz **Edytuj** Aby wyświetlić więcej opcji.

1. Wybierz **OK** przycisk, a następnie ponownie skompiluj rozwiązanie.

## <a name="suppress-warnings-for-visual-basic"></a>Pomijanie ostrzeżeń dla języka Visual Basic

Można ukryć określone ostrzeżenia kompilatora dla języka Visual Basic, edytując *.vbproj* plik projektu. Aby pominąć ostrzeżenia, *kategorii*, możesz użyć [stronie właściwości kompilacji](../ide/reference/compile-page-project-designer-visual-basic.md). Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Pomija określone ostrzeżenia dla języka Visual Basic

W tym przykładzie pokazano, jak edytować *.vbproj* pliku pomija określone ostrzeżenia kompilatora.

1. W **Eksploratora rozwiązań**, wybierz projekt, w którym chcesz pominąć ostrzeżenia.

1. Na pasku menu wybierz **projektu** > **Zwolnij projekt**.

1. W **Eksploratora rozwiązań**, otwórz menu skrótu lub kliknij prawym przyciskiem myszy dla projektu, a następnie wybierz **Edytuj <ProjectName>.vbproj**.

    XML pliku projektu zostanie otwarty w edytorze kodu.

1. Znajdź `<NoWarn>` elementu dla konfiguracji kompilacji możesz usłudze i Dodaj co najmniej jeden numery ostrzeżeń jako wartość `<NoWarn>` elementu. Jeśli określisz wiele numerów ostrzeżeń, rozdziel je przecinkami.

     W poniższym przykładzie przedstawiono `<NoWarn>` elementu *debugowania* kompilacji konfiguracji x86 platformy przy użyciu dwóch ostrzeżenia kompilatora pominięte:

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
   > Projekty .NET core zawierają domyślnie grupy właściwości konfiguracji kompilacji. Aby pominąć ostrzeżenia w projekcie platformy .NET Core, ręcznie Dodaj sekcję konfiguracji kompilacji do pliku. Na przykład:
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

1. Czy zapisać zmiany *.vbproj* pliku.

1. Na pasku menu wybierz **projektu** > **Załaduj ponownie projekt**.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

    **Dane wyjściowe** okna nie powoduje już zgłaszania ostrzeżeń, określonych przez użytkownika.

Aby uzyskać więcej informacji, zobacz [/nowarn — opcja kompilatora](/dotnet/visual-basic/reference/command-line-compiler/nowarn) dla wiersza polecenia kompilatora języka Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Pomijanie ostrzeżeń dla pakietów NuGet

W niektórych przypadkach można pominąć ostrzeżenia kompilatora NuGet dla jednego pakietu NuGet, a nie dla całego projektu. Ostrzeżenie służy cel, dzięki czemu użytkownik nie chce pomijanie go na poziomie projektu. Na przykład jeden z ostrzeżeniami NuGet informuje, że pakiet może nie być w pełni zgodne z projektem. Jeśli pomijanie go na poziomie projektu, a później dodać dodatkowe pakietu NuGet może nigdy nie wiadomo, jeśli został on produkujących ostrzeżenie dotyczące zgodności.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Określone ostrzeżenia dla jednego pakietu NuGet

1. W **Eksploratora rozwiązań**, wybierz pakiet NuGet, aby pominąć ostrzeżenia kompilatora dla.

   ![Pakiet NuGet w Eksploratorze rozwiązań](media/nuget-package-with-warning.png)

1. Wybierz z menu kliknij prawym przyciskiem myszy lub kontekst **właściwości**.

1. W **NoWarn** okno właściwości pakietu, wprowadź numer ostrzeżenia mają być pominięte dla tego pakietu. Jeśli chcesz więcej niż jeden ostrzeżenia, należy użyć przecinka do oddzielania numery ostrzeżeń.

   ![Właściwości pakietu NuGet](media/nuget-properties-nowarn.png)

   Ostrzeżenie znika z **Eksploratora rozwiązań** i **lista błędów**.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md)
- [Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)