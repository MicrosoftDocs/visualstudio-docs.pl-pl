---
title: Analiza kodu za pomocą analizatorów Roslyn
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba1529840a38a23929b9926cc4bed5cc22a058cb
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232570"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Omówienie analizatory platformie kompilatora .NET

Analizatory platformie kompilatora .NET ("Roslyn") Analizuj swój kod pod kątem stylu, jakość i łatwość utrzymania, projektowania i inne problemy. Program Visual Studio zawiera zestaw wbudowanych analizatorów, które analizują swoje C# lub kod języka Visual Basic podczas typu. Konfigurowanie preferencji dotyczących tych wbudowanych analizatory na [edytora tekstów opcje](../ide/code-styles-and-quick-actions.md) strony lub [pliku .editorconfig](../ide/editorconfig-code-style-settings-reference.md). Można zainstalować dodatkowe analizatory jako rozszerzenie programu Visual Studio lub pakietu NuGet.

Jeśli naruszeń zasady zostaną znalezione przez analizator, są one raportowane w edytorze kodu (jako *falista* kodem naruszającym) i w **lista błędów** okna.

Wiele reguł analizatora, lub *diagnostyki*, mają co najmniej jeden skojarzone *poprawki kodu* które można zastosować, aby rozwiązać ten problem. Diagnostyka analizatora, które są wbudowane w program Visual Studio mają poprawkę skojarzonego kodu. Poprawki kodu są wyświetlane w menu ikony żarówki, wraz z innych typów [szybkie akcje](../ide/quick-actions.md). Aby uzyskać informacji na temat tych poprawki kodu, zobacz [typowe szybkie akcje](../ide/common-quick-actions.md).

![Naruszenie analizator i poprawki kodu szybka akcja](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizatory Roslyn a statycznej analizy kodu

Platforma kompilatora .NET ("Roslyn"), analizatory ostatecznie spowoduje zastąpienie [statycznej analizy kodu](../code-quality/code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. Masz wiele reguł analizy kodu statycznego został już przepisany Roslyn analizatora diagnostyki.

Podobnie jak naruszenia reguł analizy kodu statycznego Roslyn analizatora naruszeń są wyświetlane w **lista błędów**. Ponadto naruszeń analizatora Roslyn również pojawi się w edytorze kodu jako *squigglies* w kodzie powodujący problemy. Kolor falista jest zależna od [ustawienia ważność](../code-quality/use-roslyn-analyzers.md#rule-severity) reguły. Poniższy zrzut ekranu przedstawia trzy naruszenia&mdash;jeden czerwony, zielony jednego i jeden szary:

![Squigglies w edytorze kodu](media/diagnostics-severity-colors.png)

Analizatory Roslyn analizowania kodu w czasie kompilacji, takie jak statycznej analizy kodu, jeśli jest włączona, ale również na żywo podczas wpisywania. Po włączeniu [pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis), analizatorów Roslyn udostępniają analizy czasu projektowania plików kodu, które nie są otwarte w edytorze.

> [!TIP]
> Czas kompilacji błędy i ostrzeżenia z analizatorów Roslyn są wyświetlane tylko jeśli analizatorów zostanie zainstalowany jako pakiet NuGet.

Nie tylko analizatorów Roslyn dla raportu te same typy problemów, które obsługuje statycznej analizy kodu, ale ułatwiają one łatwo rozwiązać co najmniej wszystkie wystąpienia naruszenia w pliku lub projektu. Te akcje są nazywane *poprawki kodu*. Poprawki kodu są specyficzne dla środowiska IDE; w programie Visual Studio są implementowane jako [szybkie akcje](../ide/quick-actions.md). Nie wszystkie diagnostyki analizatora mają poprawkę skojarzonego kodu.

> [!NOTE]
> Poniższe opcje interfejsu użytkownika są stosowane tylko do statycznej analizy kodu:
>
> - **Analizy** > **Uruchom analizę kodu** opcji menu.
> - **Włącz analizę kodu podczas kompilacji** i **Pomijaj wyniki z wygenerowanego kodu** pola wyboru na **analizy kodu** kartę strony właściwości projektu (te opcje nie mają wpływa na analizatorów Roslyn).

W celu rozróżnienia naruszeń z analizatorów Roslyn i statycznej analizy kodu w **lista błędów**, Przyjrzyj się **narzędzie** kolumny. Jeśli wartość narzędzie zgodny z jednym z zestawów analizator w **Eksploratora rozwiązań**, na przykład **Microsoft.CodeQuality.Analyzers**, naruszenia pochodzi z analizatora Roslyn. W przeciwnym razie naruszenia pochodzi ze statycznej analizy kodu.

![Narzędzie kolumny listy błędów](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> **RunCodeAnalysis** właściwość msbuild w pliku projektu jest stosowana tylko do statycznej analizy kodu. Po zainstalowaniu analizatorów, ustaw **RunCodeAnalysis** do **false** w pliku projektu, aby uniemożliwić statycznej analizy kodu po kompilacji.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pakiet NuGet, a rozszerzenie VSIX

Platforma kompilatora .NET, analizatory mogą być zainstalowane na projekcie za pośrednictwem pakietu NuGet lub całego programu Visual Studio jako rozszerzenie programu Visual Studio. Istnieją pewne różnice zachowanie klawisza, te dwie metody [instalowanie analizatorów](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Zakres

Po zainstalowaniu analizatory jako rozszerzenie programu Visual Studio, one dotyczyć na poziomie rozwiązania, wszystkie wystąpienia programu Visual Studio. Jeśli zainstalujesz analizatorów jako pakiet NuGet, który jest preferowaną metodą, dotyczą one tylko projektu, w którym zainstalowano pakiet NuGet. W środowiskach zespołu analizatory zainstalowany jako pakiety NuGet są uwzględnione w zakresie *wszystkim deweloperom* , pracować nad tym projektem.

### <a name="build-errors"></a>Błędy kompilacji

Aby reguły wymuszane w czasie kompilacji, w tym za pośrednictwem wiersza polecenia lub w ramach ciągłej integracji (CI) kompilacji, należy zainstalować analizatorów jako pakiet NuGet. Analizator ostrzeżenia i błędy nie pojawiają się w raporcie kompilacji w przypadku instalowania analizatorów jako rozszerzenie.

Poniższy zrzut ekranu przedstawia dane wyjściowe kompilacji wiersza polecenia, od tworzenia projektu, który zawiera naruszenie reguły analizatora:

![Naruszenie reguły danych wyjściowych programu MSBuild](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Ważność reguły

Nie można ustawić ważność reguły z analizatorów, które zostały zainstalowane jako rozszerzenie programu Visual Studio. Aby skonfigurować [reguły o ważności](../code-quality/use-roslyn-analyzers.md#rule-severity), instalowanie analizatorów jako pakiet NuGet.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Instalowanie analizatorów Roslyn w programie Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Używanie analizatorów Roslyn w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Napisać własny analizator Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK platformy kompilatora .NET](/dotnet/csharp/roslyn-sdk/)