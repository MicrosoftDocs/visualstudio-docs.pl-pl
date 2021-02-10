---
title: 'Instrukcje: Konfigurowanie projektów na platformach docelowych'
description: Dowiedz się, w jaki sposób program Visual Studio umożliwia konfigurowanie aplikacji przeznaczonych do użycia na różnych platformach, w tym na platformach 64-bitowych.
ms.custom: SEO-VS-2020
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8a298f19f247c45740e87074804755f6ca691ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969870"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Instrukcje: Konfigurowanie projektów na platformach docelowych

Program Visual Studio umożliwia konfigurowanie aplikacji przeznaczonych dla różnych platform, w tym na platformach 64-bitowych. Aby uzyskać więcej informacji o obsłudze platformy 64-bitowego w programie Visual Studio, zobacz [64-bitowe aplikacje](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Docelowa platforma z Configuration Manager

**Configuration Manager** umożliwia szybkie dodanie nowej platformy, która ma być docelowa do projektu. W przypadku wybrania jednej z platform dostępnych w programie Visual Studio właściwości projektu są modyfikowane w celu skompilowania projektu dla wybranej platformy.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Aby skonfigurować projekt jako docelowy dla platformy 64-bitowej

1. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **Configuration Manager**.

2. Na liście **Active platformę rozwiązania** Wybierz platformę 64-bitową dla rozwiązania, które ma być celem, a następnie wybierz przycisk **Zamknij** .

    1. Jeśli żądaną platformę nie ma na liście **aktywnych platform rozwiązań** , wybierz pozycję **Nowy**.

         Zostanie wyświetlone okno dialogowe **Nowa platforma rozwiązania** .

    2. Na liście **Typ lub wybierz nową platformę** wybierz pozycję **x64**.

        > [!NOTE]
        > Jeśli podajesz konfigurację nową nazwę, może być konieczne zmodyfikowanie ustawień w **projektancie projektu** , aby wskazać odpowiednią platformę.

    3. Jeśli chcesz skopiować ustawienia z bieżącej konfiguracji platformy, wybierz ją, a następnie wybierz przycisk **OK** .

Wszystkie projekty przeznaczone dla platformy 64-bitowej są aktualizowane, a następna kompilacja projektu zostanie zoptymalizowana dla platform 64-bitowych.

> [!NOTE]
> Nazwa platformy **Win32** jest używana na potrzeby projektów języka C++ i oznacza **x86**. Program Visual Studio traktuje zarówno platformy na poziomie projektu, jak i platformy na poziomie rozwiązań, a platformy projektu pochodzą z systemów projektów specyficznych dla języka. Projekty języka C++ używają **Win32** i **x64**, ale platformy rozwiązań używają **procesorów x86** i **x64**. W przypadku wybrania opcji **x86** jako konfiguracji rozwiązania program Visual Studio wybiera platformę **Win32** dla projektów języka C++. Aby wyświetlić ustawienia platformy na poziomie projektu i na poziomie rozwiązania, Otwórz **Configuration Manager** i zanotuj ustawienia dwóch platform. Platforma na poziomie rozwiązania jest wyświetlana na liście rozwijanej **aktywne rozwiązanie platformy** , a w tabeli przedstawiono platformę na poziomie projektu dla każdego projektu.
> ![Zrzut ekranu przedstawiający platformę rozwiązania i platformę projektu](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Platformy docelowe w projektancie projektu

**Projektant projektu** umożliwia również ukierunkowanie na różne platformy dla projektu. W przypadku wybrania jednej z platform znajdujących się na liście w **nowej platformie rozwiązania** okno dialogowe nie działa dla danego rozwiązania, można utworzyć niestandardową nazwę konfiguracji i zmodyfikować ustawienia w **projektancie projektu** , aby wskazać odpowiednią platformę.

Wykonywanie tego zadania różni się w zależności od języka programowania, którego używasz. Aby uzyskać więcej informacji, zobacz następujące linki:

- W przypadku [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów należy zapoznać się z tematem [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- W przypadku [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów zobacz [stronę Kompilacja, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

- W przypadku [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Ręczne edytowanie pliku projektu

Czasami trzeba ręcznie edytować plik projektu dla pewnej konfiguracji niestandardowej. Przykładem jest to, że warunki, których nie można określić w IDE, takie jak odwołanie, które jest inne dla dwóch różnych platform, jak w poniższym przykładzie.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Przykład: odwołanie do zestawów i bibliotek DLL x86 i x64

Może istnieć zestaw lub biblioteka DLL platformy .NET, która ma zarówno wersje x86, jak i x64. Aby skonfigurować projekt do korzystania z tych odwołań, najpierw Dodaj odwołanie, a następnie otwórz plik projektu i zmodyfikuj go, aby dodać `ItemGroup` warunek, który odwołuje się zarówno do konfiguracji, jak i na platformie docelowej.  Załóżmy na przykład, że dane binarne, do których odwołuje się odwołanie, to ClassLibrary1, a istnieją różne ścieżki do konfiguracji debugowania i wydania, a także wersje x86 i x64.  Następnie użyj czterech `ItemGroup` elementów ze wszystkimi kombinacjami ustawień w następujący sposób:

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
> W programie Visual Studio 2017 musisz zwolnić projekt, aby można było edytować plik projektu. Aby zwolnić projekt, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Zwolnij projekt**. Po zakończeniu edycji Zapisz zmiany i Załaduj ponownie projekt, klikając prawym przyciskiem myszy węzeł projektu i wybierając polecenie **Załaduj ponownie projekt**.
::: moniker-end

Aby uzyskać więcej informacji na temat pliku projektu, zobacz [Dokumentacja schematu pliku projektu MSBuild](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>Zobacz też

- [Opis platform kompilacji](../ide/understanding-build-platforms.md)
- [/platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-bitowe aplikacje](/dotnet/framework/64-bit-apps)
- [Obsługa programu Visual Studio IDE 64-bit](../ide/visual-studio-ide-64-bit-support.md)
- [Zrozumienie pliku projektu](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
