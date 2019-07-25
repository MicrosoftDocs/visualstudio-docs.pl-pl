---
title: 'Instrukcje: Skonfiguruj projekty na platformach docelowych'
ms.date: 11/04/2016
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
ms.openlocfilehash: faef9f55a88385953a121574f761193cc8c11ea9
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416823"
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

## <a name="see-also"></a>Zobacz także

- [Omówienie platformy kompilacji](../ide/understanding-build-platforms.md)
- [/platform (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64-bitowe aplikacje](/dotnet/framework/64-bit-apps)
- [Obsługa programu Visual Studio IDE 64-bit](../ide/visual-studio-ide-64-bit-support.md)
