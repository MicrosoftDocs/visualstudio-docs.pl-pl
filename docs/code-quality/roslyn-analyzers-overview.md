---
title: Analiza kodu za pomocą analizatorów Roslyn
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 71db8b7e7805b66c1c6213a227cc4705367ea551
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990293"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Omówienie analizatory platformie kompilatora .NET

Visual Studio 2017 zawiera zestaw wbudowanych analizatory platformie kompilatora .NET, analizujących kodu C# lub Visual Basic. Analizatory Przyjrzyj się styl kodu, jakość kodu i łatwość utrzymania, projekt kodu i inne problemy. Można zainstalować dodatkowe analizatory jako rozszerzenie programu Visual Studio lub na poszczególnych projektów jako pakiet NuGet.

Jeśli naruszeń zasady zostaną znalezione przez analizator, są zgłaszane zarówno w edytorze kodu jako *falista* kodem naruszającym, a następnie w **lista błędów**.

Wiele reguł analizatora, lub *diagnostyki*, mają co najmniej jeden skojarzone *poprawki kodu* które można zastosować, aby rozwiązać ten problem. Diagnostyka analizatora, które są wbudowane w program Visual Studio mają poprawkę skojarzonego kodu. Poprawki kodu są wyświetlane w menu ikony żarówki, wraz z innych typów *szybkie akcje*. Aby uzyskać informacji na temat tych poprawki kodu, zobacz [typowe szybkie akcje](../ide/common-quick-actions.md).

![Naruszenie analizator i poprawki kodu szybka akcja](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizatory Roslyn a statycznej analizy kodu

Platforma kompilatora .NET ("Roslyn"), analizatory ostatecznie spowoduje zastąpienie [statycznej analizy kodu](../code-quality/code-analysis-for-managed-code-overview.md) dla kodu zarządzanego. Masz wiele reguł analizy kodu statycznego został już przepisany Roslyn analizatora diagnostyki.

Podobnie jak naruszenia reguł analizy kodu statycznego Roslyn analizatora naruszeń są wyświetlane w **lista błędów**. Ponadto naruszeń analizatora Roslyn również pojawi się w edytorze kodu jako *squigglies* w kodzie powodujący problemy. Kolor falista jest zależna od [ustawienia ważność](../code-quality/use-roslyn-analyzers.md#rule-severity) reguły. Poniższy zrzut ekranu przedstawia trzy naruszenia&mdash;jeden czerwony, zielony jednego i jeden szary:

![Squigglies w edytorze kodu](media/diagnostics-severity-colors.png)

Analizatory Roslyn analizowania kodu w czasie kompilacji, takie jak statycznej analizy kodu, jeśli jest włączona, ale również na żywo podczas wpisywania! Analizatory Roslyn oferuje również analizy czasu projektowania plików kodu, które nie są otwarte w edytorze, po włączeniu [pełnej analizy rozwiązania](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Czas kompilacji błędy i ostrzeżenia z analizatorów Roslyn są wyświetlane tylko jeśli analizatorów zostanie zainstalowany jako pakiet NuGet.

Nie tylko analizatorów Roslyn dla raportu te same typy problemów, które obsługuje statycznej analizy kodu, ale ułatwiają one łatwo rozwiązać co najmniej wszystkie wystąpienia naruszenia w pliku lub projektu. Te akcje są nazywane *poprawki kodu*. Poprawki kodu są specyficzne dla środowiska IDE; w programie Visual Studio są implementowane jako [szybkie akcje](../ide/quick-actions.md). Nie wszystkie diagnostyki analizatora mają poprawkę skojarzonego kodu.

> [!NOTE]
> Opcja menu **analizy** > **Uruchom analizę kodu** ma zastosowanie tylko do statycznej analizy kodu. Ponadto na projekt **analizy kodu** strona właściwości **Włącz analizę kodu podczas kompilacji** i **Pomijaj wyniki z wygenerowanego kodu** pola wyboru dotyczą tylko programu statyczna analiza kodu. Mają one wpływu na analizatorów Roslyn.

W celu rozróżnienia naruszeń z analizatorów Roslyn i statycznej analizy kodu w **lista błędów**, Przyjrzyj się **narzędzie** kolumny. Jeśli wartość narzędzie zgodny z jednym z zestawów analizator w **Eksploratora rozwiązań**, na przykład **Microsoft.CodeQuality.Analyzers**, naruszenia pochodzi z analizatora Roslyn. W przeciwnym razie naruszenia pochodzi ze statycznej analizy kodu.

![Narzędzie kolumny listy błędów](media/code-analysis-tool-in-error-list.png)

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

- [Szybkie akcje w programie Visual Studio](../ide/quick-actions.md)
- [Napisać własny analizator Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Zestaw SDK platformy kompilatora .NET](/dotnet/csharp/roslyn-sdk/)