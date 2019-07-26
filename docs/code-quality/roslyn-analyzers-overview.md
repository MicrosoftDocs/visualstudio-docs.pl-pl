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
ms.openlocfilehash: cae7a02c774773d08c287dde7df59ff62fdbec58
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68533344"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Omówienie analizatorów .NET Compiler Platform

Analizatory .NET Compiler Platform ("Roslyn") analizują kod na potrzeby stylu, jakości i utrzymania, projektowania i innych problemów. Program Visual Studio zawiera wbudowany zestaw analizatorów, które analizują kod C# lub Visual Basic podczas pisania. Preferencje dla tych wbudowanych analizatorów można skonfigurować na stronie [Opcje edytora tekstu](../ide/code-styles-and-code-cleanup.md) lub w [pliku. editorconfig](../ide/editorconfig-code-style-settings-reference.md). Dodatkowe analizatory można zainstalować jako rozszerzenie programu Visual Studio lub pakiet NuGet.

Jeśli wykryto naruszenia reguł przez analizator, są one raportowane w edytorze kodu (jako zygzak w  kodzie błędu) i w oknie **Lista błędów** .

Wiele reguł analizatorów lub *diagnostyki*ma jedną lub więcej skojarzonych *poprawek kodu* , które można zastosować, aby rozwiązać problem. Diagnostyka analizatora wbudowana w program Visual Studio ma skojarzoną poprawkę kodu. Poprawki kodu są wyświetlane w menu ikony żarówki wraz z innymi typami szybkich [akcji](../ide/quick-actions.md). Aby uzyskać informacje na temat tych poprawek kodu, zobacz [Common Quick Actions](../ide/common-quick-actions.md).

![Naruszenie analizatora i szybka czynność usuwania kodu](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizatory Roslyn a statyczna analiza kodu

Analizatory .NET Compiler Platform ("Roslyn") mogą ostatecznie zastąpić [statyczną analizę kodu](../code-quality/code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. Wiele reguł statycznej analizy kodu zostało już zapisaną jako Diagnostyka analizatora Roslyn.

Podobnie jak w przypadku naruszeń reguł analizy kodu statycznego, naruszenia analizatora Roslyn są wyświetlane w **Lista błędów**. Ponadto naruszenia analizatora Roslyn są również wyświetlane w edytorze *kodu jako* zygzaky w kodzie błędu. Kolor zygzaka zależy od [Ustawienia ważności](../code-quality/use-roslyn-analyzers.md#rule-severity) reguły. Poniższy zrzut ekranu przedstawia trzy naruszenia&mdash;jednej czerwieni, jedną zieloną i jedną szarą:

![Zygzaky w edytorze kodu](media/diagnostics-severity-colors.png)

Analizatory Roslyn analizują kod w czasie kompilacji, na przykład statycznej analizy kodu, jeśli jest włączona, ale również na żywo podczas pisania. Po włączeniu [pełnej analizy rozwiązań](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)analizatory Roslyn zapewniają również analizę czasu projektowania plików kodu, które nie są otwarte w edytorze.

> [!TIP]
> Błędy i ostrzeżenia czasu kompilacji z analizatorów Roslyn są wyświetlane tylko wtedy, gdy analizatory są zainstalowani jako pakiet NuGet.

Tylko analizatory Roslyn raportują te same typy problemów, które przeprowadzają analizy kodu statycznego, ale ułatwiają naprawianie jednego lub wszystkich wystąpień naruszenia w pliku lub projekcie. Te akcje są nazywane *poprawkami kodu*. Poprawki kodu są specyficzne dla środowiska IDE; w programie Visual Studio są one implementowane jako [szybkie akcje](../ide/quick-actions.md). Nie cała Diagnostyka analizatora ma skojarzoną poprawkę kodu.

> [!NOTE]
> Następujące opcje interfejsu użytkownika mają zastosowanie tylko do analizy kodu statycznego:
>
> - Opcja **Przeanalizuj** > **analizę kodu uruchomieniowego** .
> - Pola wyboru **Włącz analizę kodu podczas kompilacji** i **Pomijaj wyniki z wygenerowanego kodu** na karcie **Analiza kodu** na stronach właściwości projektu (te opcje nie mają wpływu na analizatory Roslyn).

Aby rozróżnić naruszenia od analizatorów Roslyn i statycznej analizy kodu w **Lista błędów**, należy zapoznać się z kolumną **Narzędzia** . Jeśli wartość narzędzia pasuje do jednego z zestawów analizatorów w **Eksplorator rozwiązań**, na przykład **Microsoft. CodeQuality. analizatory**, naruszenie pochodzi z analizatora Roslyn. W przeciwnym razie naruszenie pochodzi z analizy kodu statycznego.

![Kolumna narzędzia w Lista błędów](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Właściwość **RunCodeAnalysis** MSBuild w pliku projektu ma zastosowanie tylko do statycznej analizy kodu. Jeśli instalujesz analizatory, ustaw **RunCodeAnalysis** na **false** w pliku projektu, aby zapobiec uruchamianiu statycznej analizy kodu po kompilacji.
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
> [Zainstaluj analizatory Roslyn w programie Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Korzystanie z analizatorów Roslyn w programie Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Analizatory — często zadawane pytania](analyzers-faq.md)
- [Napisz własną Roslyn Analizator](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
