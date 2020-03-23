---
title: 'Jak: Konfigurowanie projektów do platform docelowych'
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cbe4bc3f982ae18b9f85fe8bf5c21495c98beee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112539"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Jak: Konfigurowanie projektów do platform docelowych

Visual Studio umożliwia skonfigurowanie aplikacji do kierowania na różne platformy, w tym platformy 64-bitowe. Aby uzyskać więcej informacji na temat obsługi platformy 64-bitowej w programie Visual Studio, zobacz [aplikacje 64-bitowe](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Platformy docelowe z menedżerem konfiguracji

Menedżer **konfiguracji** umożliwia szybkie dodawanie nowej platformy do docelowego działania projektu. Jeśli wybierzesz jedną z platform dołączonych do programu Visual Studio, właściwości projektu są modyfikowane do tworzenia projektu dla wybranej platformy.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Aby skonfigurować projekt do kierowania na platformę 64-bitową

1. Na pasku menu wybierz pozycję **Build** > **Configuration Manager**.

2. Na liście **Active Solution Platform** wybierz platformę 64-bitową dla rozwiązania docelowego, a następnie wybierz przycisk **Zamknij.**

    1. Jeśli żądana platforma nie jest wyświetlana na liście **Platforma aktywnego rozwiązania,** wybierz pozycję **Nowy**.

         Zostanie wyświetlone okno dialogowe **Nowa platforma rozwiązania.**

    2. Na liście **Typ lub Wybierz nową platformę** wybierz **x64**.

        > [!NOTE]
        > Jeśli nadasz konfiguracji nową nazwę, może być trzeba zmodyfikować ustawienia w **Projektancie projektu,** aby kierować na właściwą platformę.

    3. Jeśli chcesz skopiować ustawienia z bieżącej konfiguracji platformy, wybierz ją, a następnie wybierz przycisk **OK.**

Właściwości dla wszystkich projektów, które są przeznaczone dla platformy 64-bitowej są aktualizowane, a następna kompilacja projektu zostanie zoptymalizowana dla platform 64-bitowych.

## <a name="target-platforms-in-the-project-designer"></a>Platformy docelowe w projektancie projektu

**Projektant projektu** zapewnia również sposób kierowania różnych platform z projektu. Jeśli wybranie jednej z platform uwzględnionych na liście w oknie dialogowym **Nowa platforma rozwiązania** nie działa dla rozwiązania, można utworzyć niestandardową nazwę konfiguracji i zmodyfikować ustawienia w **Projektancie projektu,** aby kierować reklamy na właściwą platformę.

Wykonanie tego zadania różni się w zależności od używanego języka programowania. Aby uzyskać więcej informacji, zobacz następujące łącza:

- Zobacz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] [też/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] przypadku projektów zobacz [Tworzenie strony, Projektant projektów (C#)](../ide/reference/build-page-project-designer-csharp.md).

- W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] przypadku projektów zobacz [/clr (kompilacja wspólnego środowiska wykonawczego języka).](/cpp/build/reference/clr-common-language-runtime-compilation)

## <a name="manually-editing-the-project-file"></a>Ręczna edycja pliku projektu

Czasami musisz ręcznie edytować plik projektu dla jakiejś konfiguracji niestandardowej. Przykładem jest, gdy masz warunki, które nie mogą być określone w IDE, takie jak odwołanie, które jest różne dla dwóch różnych platform, jak w poniższym przykładzie.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Przykład: Odwoływanie się do zestawów x86 i x64 oraz bibliotek DLL

Może mieć .NET zestawu lub biblioteki DLL, który ma zarówno x86 i x64 wersje. Aby skonfigurować projekt do używania tych odwołań, najpierw dodaj odwołanie, a następnie `ItemGroup` otwórz plik projektu i edytuj go, aby dodać warunek, który odwołuje się zarówno do konfiguracji, jak i do platformy docelowej.  Załóżmy na przykład, że plik binarny, do którego się odwołujesz, to ClassLibrary1 i istnieją różne ścieżki dla konfiguracji debugowania i wydania, a także wersje x86 i x64.  Następnie użyj `ItemGroup` czterech elementów ze wszystkimi kombinacjami ustawień, w następujący sposób:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> W programie Visual Studio 2017 należy zwolnić projekt, zanim będzie można edytować plik projektu. Aby zwolnić projekt, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zwolnij projekt**. Po zakończeniu edycji zapisz zmiany i przeładuj projekt, klikając prawym przyciskiem myszy węzeł projektu i wybierając polecenie **Przeładowanie projektu**.
::: moniker-end

Aby uzyskać więcej informacji na temat pliku projektu, zobacz [odwołanie do schematu pliku projektu MSBuild](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>Zobacz też

- [Opis platform kompilacji](../ide/understanding-build-platforms.md)
- [/platform (opcje kompilatora języka C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [Aplikacje 64-bitowe](/dotnet/framework/64-bit-apps)
- [Obsługa 64-bitowej wersji programu Visual Studio IDE](../ide/visual-studio-ide-64-bit-support.md)
- [Opis pliku projektu](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
