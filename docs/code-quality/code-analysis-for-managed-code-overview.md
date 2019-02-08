---
title: Statyczna analiza kodu dla kodu zarządzanego
ms.date: 03/26/2018
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0da99377a6e0f5405029c0ac194484de3a3a1c90
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909144"
---
# <a name="overview-of-static-code-analysis-for-managed-code-in-visual-studio"></a>Omówienie statycznej analizy kodu dla kodu zarządzanego w programie Visual Studio

Program Visual Studio 2017 można wykonać analizy kodu dla kodu zarządzanego na dwa sposoby: za pomocą *FxCop* analizy statycznej zestawów zarządzanych, a za pomocą nowoczesnych więcej *analizatorów Roslyn*. W tym temacie omówiono FxCop statycznej analizy kodu. Aby dowiedzieć się więcej na temat analizowania kodu za pomocą analizatorów kodu, zobacz [analizatorów Przegląd Roslyn](../code-quality/roslyn-analyzers-overview.md).

Analiza kodu dla kodu zarządzanego analizuje zestawy zarządzane i raportuje informacje o zestawach, takie jak naruszenia programowania i projektowania reguły określone w wytycznych projektowych programu Microsoft .NET Framework.

Narzędzie do analizy reprezentuje kontrole wykonywane podczas analizy jako komunikaty ostrzegawcze. Komunikaty ostrzegawcze identyfikują wszystkie istotne błędy programowania i projektowania i gdy jest możliwe, dostarczają informacji na temat sposobu rozwiązania problemu.

> [!NOTE]
> Statyczna analiza kodu nie jest obsługiwana dla projektów .NET Core i .NET Standard w programie Visual Studio. Po uruchomieniu analizy kodu dla projektu .NET Core lub .NET Standard w ramach programu msbuild, zobaczysz błąd podobny do **błąd: CA0055: Nie można zidentyfikować platformy dla \<your.dll >**. Aby przeanalizować kod w projektach .NET Core lub .NET Standard, należy użyć [analizatorów Roslyn](../code-quality/roslyn-analyzers-overview.md) zamiast tego.

## <a name="ide-integrated-development-environment-integration"></a>Integracja z IDE (zintegrowanym środowiskiem programistycznym)

Możesz uruchomić analizę kodu projektu, ręcznie lub automatycznie.

Aby uruchomić analizę kodu za każdym razem, tworzysz projekt, wybierz **Włącz analizę kodu podczas kompilacji** na stronie właściwości projektu. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Aby ręczne przeprowadzanie analizy kodu dla projektu, na pasku menu wybierz **analizy** > **Uruchom analizę kodu** > **Uruchom analizę kodu dla \<projektu >**.

## <a name="rule-sets"></a>Zestawy reguł

Reguły analizy kodu dla zarządzanego kodu są grupowane w [zestawów reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Można użyć jednej standardowych zestawów reguł Microsoft lub możesz [Tworzenie niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md) aby spełnić szczególną potrzebę.

## <a name="suppress-warnings"></a>Pomijanie ostrzeżeń

Często jest to użyteczne, aby wskazać, że ostrzeżenie nie ma zastosowania. Informuje dewelopera i inne osoby, które mogą później przejrzeć kod że ostrzeżenie zostało zbadane a następnie pominięte lub ignorowane.

Pomijanie ostrzeżeń w źródłowej jest implementowane za pomocą atrybutów niestandardowych. Aby pominąć ostrzeżenie, Dodaj atrybut `SuppressMessage` do kodu źródłowego, jak pokazano w poniższym przykładzie:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Aby uzyskać więcej informacji, zobacz [pomijanie ostrzeżeń](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Jeśli migrujesz projektu programu Visual Studio 2017, nagle może być wystąpiły z dużą liczbą ostrzeżenia analizy kodu. Jeśli jesteś gotowy naprawić ostrzeżenia, a następnie od razu się w produktywności, możesz to zrobić *linii bazowej* stanu analiza projektu. Z **analizy** menu, wybierz opcję **Uruchom analizę kodu i Pomiń aktywne problemy**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Uruchamianie analizy kodu jako części zasad ewidencjonowania

Jako organizacja można wymagać, aby wszystkie zaewidencjonowania spełniały pewne zasady. W szczególności chcesz upewnić się, że spełnione są następujące zasady:

- Nie ma żadnych błędów kompilacji w kodzie, które zostały zaewidencjonowane.

- Uruchamianie analizy kodu jako część najnowszej kompilacji.

Można to zrobić poprzez określenie zasad ewidencjonowania. Aby uzyskać więcej informacji, zobacz [udoskonalanie jakości kodu za pomocą zasad zaewidencjonowania projektu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integracji kompilacji zespołu

Zintegrowane funkcje systemu kompilacji można użyć, aby uruchomić narzędzie do analizy jako część procesu kompilacji. Aby uzyskać więcej informacji, zobacz [potoki Azure](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Instrukcje: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
