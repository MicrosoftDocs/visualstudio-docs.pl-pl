---
title: Analiza kodu przy użyciu analizatorów Roslyn
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
ms.openlocfilehash: 2d4a9bfca972f9c57688b19bd872b31ee5997f76
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550764"
---
# <a name="overview-of-net-compiler-platform-code-analyzers"></a>Przegląd .NET Compiler Platform analizatorów kodu

Analizatory .NET Compiler Platform ("Roslyn") analizują kod na potrzeby stylu, jakości i utrzymania, projektowania i innych problemów. Program Visual Studio zawiera wbudowany zestaw analizatorów, które analizują kod C# lub Visual Basic podczas pisania. Preferencje dla tych wbudowanych analizatorów można skonfigurować na stronie [Opcje edytora tekstu](../ide/code-styles-and-code-cleanup.md) lub w [pliku. editorconfig](../ide/editorconfig-code-style-settings-reference.md). Dodatkowe analizatory można zainstalować jako rozszerzenie programu Visual Studio lub pakiet NuGet.

Jeśli wykryto naruszenia reguł przez analizator, są one raportowane w edytorze kodu (jako zygzak w kodzie błędu) i w oknie **Lista błędów** .

Wiele reguł analizatorów lub *diagnostyki*ma jedną lub więcej skojarzonych *poprawek kodu* , które można zastosować, aby rozwiązać problem. Diagnostyka analizatora wbudowana w program Visual Studio ma skojarzoną poprawkę kodu. Poprawki kodu są wyświetlane w menu ikony żarówki wraz z innymi typami szybkich [akcji](../ide/quick-actions.md). Aby uzyskać informacje na temat tych poprawek kodu, zobacz [Common Quick Actions](../ide/common-quick-actions.md).

![Naruszenie analizatora i szybka czynność usuwania kodu](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="net-compiler-platform-based-analysis-versus-legacy-analysis"></a>Analiza oparta na .NET Compiler Platform i analiza starszej wersji

Analiza kodu .NET Compiler Platform ("Roslyn") ostatecznie zastąpi [starszą analizę](../code-quality/code-analysis-for-managed-code-overview.md) kodu zarządzanego. Wiele starszych reguł analizy zostało już zapisaną jako analizatory kodu oparte na .NET Compiler Platform.

Podobnie jak w przypadku starszych naruszeń reguł analizy, .NET Compiler Platform w oknie Lista błędów w programie Visual Studio są wyświetlane naruszenia analizy kodu. Ponadto naruszenia analizy kodu opartego na .NET Compiler Platform są również wyświetlane w edytorze kodu jako zygzaky w kodzie, którego kod jest nieprawidłowy. Kolor zygzaka zależy od [Ustawienia ważności](../code-quality/use-roslyn-analyzers.md#rule-severity) reguły. Poniższy zrzut ekranu przedstawia trzy naruszenia&mdash;jednej czerwieni, jedną zieloną i jedną szarą:

![Zygzaky w edytorze kodu](media/diagnostics-severity-colors.png)

Analizatory kodu oparte na .NET Compiler Platform analizują kod w czasie kompilacji, na przykład Starsza analiza, jeśli jest włączona, ale również na żywo podczas pisania. Po włączeniu [pełnej analizy rozwiązań](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)analizatory kodu zapewniają również analizę czasu projektowania plików kodu, które nie są otwarte w edytorze.

> [!TIP]
> Błędy i ostrzeżenia czasu kompilacji są wyświetlane tylko wtedy, gdy analizatory są zainstalowani jako pakiet NuGet.

Nie tylko .NET Compiler Platform analizatorów kodu opartych na programie są raportowane te same typy problemów, które są używane w ramach starszej analizy, ale ułatwiają naprawianie jednego lub wszystkich wystąpień naruszenia w pliku lub projekcie. Te akcje są nazywane *poprawkami kodu*. Poprawki kodu są specyficzne dla środowiska IDE; w programie Visual Studio są one implementowane jako [szybkie akcje](../ide/quick-actions.md). Nie cała Diagnostyka analizatora ma skojarzoną poprawkę kodu.

> [!NOTE]
> Następujące opcje interfejsu użytkownika mają zastosowanie tylko do starszej analizy:
>
> - Opcja **Przeanalizuj** > **analizę kodu uruchomieniowego** .
> - Pola wyboru **Włącz analizę kodu podczas kompilacji** i **Pomijaj wyniki z wygenerowanego kodu** na karcie **Analiza kodu** na stronach właściwości projektu.

Aby rozróżnić naruszenia od analizatorów kodu i starszej analizy w oknie Lista błędów, zapoznaj się z kolumną **Narzędzia** . Jeśli wartość narzędzia pasuje do jednego z zestawów analizatorów w **Eksplorator rozwiązań**, na przykład **Microsoft. CodeQuality. analizatory**, naruszenie pochodzi z analizatora kodu. W przeciwnym razie naruszenie pochodzi ze starszej wersji analizy.

![Kolumna narzędzia w Lista błędów](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Właściwość **RunCodeAnalysis** MSBuild w pliku projektu ma zastosowanie tylko do starszej analizy. Jeśli instalujesz analizatory, ustaw **RunCodeAnalysis** na **false** w pliku projektu, aby zapobiec uruchamianiu starszej analizy po kompilacji.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Pakiet NuGet a rozszerzenie VSIX

Analizatory .NET Compiler Platform można instalować dla poszczególnych projektów za pośrednictwem pakietu NuGet lub programu Visual Studio jako rozszerzenia programu Visual Studio. Istnieją pewne kluczowe różnice między tymi dwiema metodami [instalacji analizatorów](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Scope

Jeśli instalujesz analizatory jako rozszerzenie programu Visual Studio, są one stosowane na poziomie rozwiązania do wszystkich wystąpień programu Visual Studio. Jeśli instalujesz analizatory jako pakiet NuGet, który jest preferowaną metodą, są one stosowane tylko do projektu, w którym zainstalowano pakiet NuGet. W środowiskach zespołu analizatory zainstalowane jako pakiety NuGet są w zakresie dla *wszystkich deweloperów* , którzy pracują nad tym projektem.

### <a name="build-errors"></a>Błędy kompilacji

Aby reguły były wymuszane w czasie kompilacji, w tym za pomocą wiersza polecenia lub w ramach kompilacji ciągłej integracji (CI), należy zainstalować analizatory jako pakiet NuGet. Ostrzeżenia i błędy analizatora nie są wyświetlane w raporcie kompilacji, jeśli analizatory są instalowane jako rozszerzenie.

Poniższy zrzut ekranu przedstawia dane wyjściowe kompilacji wiersza polecenia z kompilowania projektu, który zawiera naruszenie reguły analizatora:

![Dane wyjściowe MSBuild z naruszeniem reguły](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Ważność reguły

Nie można ustawić ważności reguł z analizatorów, które zostały zainstalowane jako rozszerzenie programu Visual Studio. Aby skonfigurować [ważność reguły](../code-quality/use-roslyn-analyzers.md#rule-severity), zainstaluj analizatory jako pakiet NuGet.

## <a name="categories"></a>Kategorie

Poniżej przedstawiono różne typy analizatorów, które pomagają analizować kod:

- Zalecane analizatory firmy Microsoft: [Analizatory FxCop](../code-quality/fxcop-analyzers.yml)
- Analizatory środowiska IDE programu Visual Studio: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- Analizatory stron trzecich: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), analizatory [XUnit](https://www.nuget.org/packages/xunit.analyzers/), [analizatorze Sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Instalowanie analizatorów kodu w programie Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Korzystanie z analizatorów kodu w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Napisz własny analizator kodu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
