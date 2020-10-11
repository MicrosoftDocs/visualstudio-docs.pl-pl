---
title: Starsza analiza dla kodu zarządzanego
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b6ab8171d2317549beabe2d8e552eeeefccd02cf
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91927994"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Przegląd starszej analizy kodu zarządzanego w programie Visual Studio

Program Visual Studio może przeanalizować kod zarządzany na dwa sposoby: ze [starszą analizą](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), znaną również jako FxCop statycznej analizy zestawów zarządzanych i bardziej nowoczesnymi [analizatorami kodu](../code-quality/roslyn-analyzers-overview.md)opartymi na .NET compiler platform. Ten temat obejmuje starszą analizę. Aby dowiedzieć się więcej na temat analizy kodu na podstawie .NET Compiler Platform, zobacz [Omówienie analizatorów opartych na .NET compiler platform](../code-quality/roslyn-analyzers-overview.md).

Analiza kodu dla kodu zarządzanego analizuje zestawy zarządzane i raportuje informacje o zestawach, takie jak naruszenia reguł programowania i projektowania określonych w [wytycznych dotyczących projektowania platformy .NET](/dotnet/standard/design-guidelines/).

Narzędzie do analizy reprezentuje kontrole wykonywane podczas analizy jako komunikaty ostrzegawcze. Komunikaty ostrzegawcze identyfikują wszelkie istotne problemy związane z programowaniem i projektowaniem oraz, gdy jest to możliwe, dostarczają informacji na temat sposobu rozwiązania problemu.

> [!NOTE]
> Starsza analiza (analiza kodu statycznego) nie jest obsługiwana w przypadku projektów .NET Core i .NET Standard w programie Visual Studio. Jeśli uruchamiasz analizę kodu w projekcie .NET Core lub .NET Standard w ramach programu MSBuild, zobaczysz błąd podobny do **błędu: CA0055: nie można zidentyfikować platformy dla \<your.dll> **. Aby analizować kod w projektach .NET Core lub .NET Standard, należy zamiast tego użyć [analizatorów kodu](../code-quality/roslyn-analyzers-overview.md) .

## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)

Możesz uruchomić analizę kodu dla projektu ręcznie lub automatycznie.

Aby uruchomić analizę kodu przy każdej kompilacji projektu, wybierz opcję na stronie właściwości **Analiza kodu** projektu. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Aby ręcznie uruchomić analizę kodu w projekcie, na pasku menu wybierz pozycję **Analizuj**Przeprowadź  >  **analizę kodu**  >  **Uruchom analizę kodu na \<project> **.

## <a name="rule-sets"></a>Zestawy reguł

Reguły analizy kodu dla kodu zarządzanego są pogrupowane w [zestawy reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Można użyć jednego z standardowych zestawów reguł firmy Microsoft lub można [utworzyć niestandardowy zestaw reguł](../code-quality/how-to-create-a-custom-rule-set.md) , aby spełnić konkretne potrzeby.

## <a name="suppress-warnings"></a>Pomijanie ostrzeżeń

Często warto wskazać, że ostrzeżenie nie ma zastosowania. Informuje dewelopera i inne osoby, które mogą później przejrzeć kod, że ostrzeżenie zostało zbadane, a następnie pominięte lub zignorowane.

Pomijanie ostrzeżeń w źródle jest implementowane za poorednictwem atrybutów niestandardowych. Aby pominąć ostrzeżenie, Dodaj atrybut `SuppressMessage` do kodu źródłowego, jak pokazano w następującym przykładzie:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Aby uzyskać więcej informacji, zobacz [pomijanie ostrzeżeń](../code-quality/in-source-suppression-overview.md).

::: moniker range="vs-2017"

> [!NOTE]
> W przypadku migrowania projektu do programu Visual Studio 2017 może wystąpić nagłe zaistnienie dużej liczby ostrzeżeń dotyczących analizy kodu. Jeśli nie możesz naprawić ostrzeżeń, możesz pominąć wszystkie z nich, wybierając pozycję **Analizuj**  >  **analizę kodu i pominąć aktywne problemy**.
>
> ![Uruchom analizę kodu i Pomiń problemy w programie Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> W przypadku migrowania projektu do programu Visual Studio 2019 może wystąpić nagłe zaistnienie dużej liczby ostrzeżeń dotyczących analizy kodu. Jeśli nie możesz naprawić ostrzeżeń, możesz pominąć wszystkie z nich, wybierając pozycję **Analizuj**  >  **kompilację i pominąć aktywne problemy**.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Uruchom analizę kodu w ramach zasad ewidencjonowania

Jako organizacja można wymagać, aby wszystkie zaewidencjonowania spełniały określone zasady. W szczególności chcesz upewnić się, że przestrzegasz następujących zasad:

- Brak błędów kompilacji w kodzie, który został zaewidencjonowany.

- Analiza kodu jest uruchamiana w ramach najnowszej kompilacji.

Można to osiągnąć przez określenie zasad ewidencjonowania. Aby uzyskać więcej informacji, zobacz [rozszerzanie jakości kodu za pomocą zasad ewidencjonowania projektu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integracja kompilacji zespołowej

Możesz użyć zintegrowanych funkcji systemu kompilacji, aby uruchomić Narzędzie analizy jako część procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="see-also"></a>Zobacz też

- [Omówienie analizatorów opartych na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
- [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Porady: włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
