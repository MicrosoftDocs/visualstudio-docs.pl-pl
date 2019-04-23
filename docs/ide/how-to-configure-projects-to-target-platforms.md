---
title: 'Instrukcje: Konfigurowanie projektów pod kątem platform docelowych'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9f605e761380b3dc856926dff5bd1712753a8ba
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045684"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Instrukcje: Konfigurowanie projektów pod kątem platform docelowych

Program Visual Studio umożliwia ustawianie aplikacji przeznaczonych dla różnych platform, w tym platform 64-bitowych. Aby uzyskać więcej informacji na temat obsługi platform 64-bitowych w programie Visual Studio, zobacz [aplikacji 64-bitowych](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Platformy docelowe przy użyciu programu Configuration Manager

**Programu Configuration Manager** umożliwia szybko dodać nową platformę docelową z projektem. Po wybraniu jednej z platform, w programie Visual Studio, właściwości projektu są modyfikowane w celu kompilowania projektu dla wybranej platformy.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Aby skonfigurować projekt przeznaczony dla platformy 64-bitowej

1. Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**.

2. W **aktywną platformą rozwiązania** listy, wybierz platformę 64-bitowych dla rozwiązania do obiektu docelowego, a następnie wybierz **Zamknij** przycisku.

    1. Jeśli nie ma platformy, która ma **aktywną platformą rozwiązania** wybierz **New**.

         **Nowa platforma rozwiązania** pojawi się okno dialogowe.

    2. W **wpisz lub wybierz nową platformę** wybierz **x64**.

        > [!NOTE]
        >  Jeśli nadasz konfiguracji nową nazwę, może być konieczne zmodyfikować ustawienia w **projektanta projektu** pod kątem odpowiedniej platformy.

    3. Jeśli chcesz skopiować ustawienia z bieżącej konfiguracji platformy, wybierz go, a następnie wybierz **OK** przycisku.

Właściwości dla wszystkich projektów przeznaczonych dla platformy 64-bitowe są aktualizowane i następnej kompilacji projektu będzie optymalizowany dla platform 64-bitowych.

## <a name="target-platforms-in-the-project-designer"></a>Platformy docelowe w Projektancie projektu

**Projektanta projektu** również umożliwia przeznaczonych dla różnych platform za pomocą projektu. W przypadku wybrania jednej z platform uwzględnione na liście w **nowa platforma rozwiązania** okno dialogowe nie działa w przypadku rozwiązania, można utworzyć nazwy niestandardowej konfiguracji i zmodyfikować ustawienia w **Projektant projektu**  pod kątem odpowiedniej platformy.

Wykonanie tego zadania zależy od języka programowania, którego używasz. Skorzystaj z następujących linków, aby uzyskać więcej informacji:

- Aby uzyskać [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów, zobacz [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Aby uzyskać [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów, zobacz [strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Aby uzyskać [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów, zobacz [/CLR (kompilacja środowiska uruchomieniowego języka wspólnego)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="see-also"></a>Zobacz także

- [Omówienie platformy kompilacji](../ide/understanding-build-platforms.md)
- [/ platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [aplikacje 64-bitowe](/dotnet/framework/64-bit-apps)
- [Visual Studio IDE 64-bitowe systemu](../ide/visual-studio-ide-64-bit-support.md)
