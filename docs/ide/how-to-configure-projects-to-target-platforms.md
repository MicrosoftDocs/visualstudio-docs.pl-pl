---
title: 'Instrukcje: Skonfiguruj projekty na platformach docelowych'
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
ms.openlocfilehash: 5d31d3a4f2e42981df646f9c38e13ee9b5f21122
ms.sourcegitcommit: 9e5e8b6e9a3b6614723e71cc23bb434fe4218c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69634922"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Instrukcje: Skonfiguruj projekty na platformach docelowych

Program Visual Studio umożliwia ustawianie aplikacji przeznaczonych dla różnych platform, w tym platform 64-bitowych. Aby uzyskać więcej informacji na temat obsługi platform 64-bitowych w programie Visual Studio, zobacz [aplikacji 64-bitowych](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Docelowa platforma z Configuration Manager

**Configuration Manager** umożliwia szybkie dodanie nowej platformy, która ma być docelowa do projektu. W przypadku wybrania jednej z platform dostępnych w programie Visual Studio właściwości projektu są modyfikowane w celu skompilowania projektu dla wybranej platformy.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Aby skonfigurować projekt jako docelowy dla platformy 64-bitowej

1. Na pasku menu wybierz kolejno opcje **Kompiluj** > **Configuration Manager**.

2. Na liście **Active platformę rozwiązania** Wybierz platformę 64-bitową dla rozwiązania, które ma być celem, a następnie wybierz przycisk **Zamknij** .

    1. Jeśli żądaną platformę nie ma na liście **aktywnych platform rozwiązań** , wybierz pozycję **Nowy**.

         Zostanie wyświetlone okno dialogowe **Nowa platforma rozwiązania** .

    2. Na liście **Typ lub wybierz nową platformę** wybierz pozycję **x64**.

        > [!NOTE]
        > Jeśli podajesz konfigurację nową nazwę, może być konieczne zmodyfikowanie ustawień w **projektancie projektu** , aby wskazać odpowiednią platformę.

    3. Jeśli chcesz skopiować ustawienia z bieżącej konfiguracji platformy, wybierz ją, a następnie wybierz przycisk **OK** .

Wszystkie projekty przeznaczone dla platformy 64-bitowej są aktualizowane, a następna kompilacja projektu zostanie zoptymalizowana dla platform 64-bitowych.

## <a name="target-platforms-in-the-project-designer"></a>Platformy docelowe w projektancie projektu

**Projektant projektu** umożliwia również ukierunkowanie na różne platformy dla projektu. W przypadku wybrania jednej z platform znajdujących się na liście w **nowej platformie rozwiązania** okno dialogowe nie działa w przypadku Twojego rozwiązania, można utworzyć niestandardową nazwę konfiguracji i zmodyfikować ustawienia w **projektancie projektu** , aby wskazać odpowiednią platformę. .

Wykonywanie tego zadania różni się w zależności od języka programowania, którego używasz. Aby uzyskać więcej informacji, zobacz następujące linki:

- W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] przypadku projektów należy zapoznać się z tematem [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] przypadku projektów zobacz [stronę Kompilacja, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

- W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] przypadku projektów zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Ręczne edytowanie pliku projektu

Czasami trzeba ręcznie edytować plik projektu dla pewnej konfiguracji niestandardowej. Przykładem jest to, że warunki, których nie można określić w IDE, takie jak odwołanie, które jest inne dla dwóch różnych platform, jak w poniższym przykładzie.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Przykład: Odwołania do zestawów i bibliotek DLL x86 i x64

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

Aby uzyskać więcej informacji na temat pliku projektu, zobacz [Dokumentacja schematu pliku projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).

## <a name="see-also"></a>Zobacz także

- [Omówienie platformy kompilacji](../ide/understanding-build-platforms.md)
- [/platform (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-bitowe aplikacje](/dotnet/framework/64-bit-apps)
- [Obsługa programu Visual Studio IDE 64-bit](../ide/visual-studio-ide-64-bit-support.md)
- [Zrozumienie pliku projektu](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
