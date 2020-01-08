---
title: Konfigurowanie analizy kodu
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe144e8de67264c9d89f6a240ef815afac9a4655
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587566"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Instrukcje: Konfigurowanie starszej analizy dla kodu zarządzanego

W programie Visual Studio można wybrać spośród listy [zestawów reguł](../code-quality/rule-set-reference.md) analizy kodu, które mają zostać zastosowane do projektu kodu zarządzanego. Domyślnie **reguł zalecanych Minimum Microsoft** zestaw reguł jest zaznaczone, ale można zastosować inną regułę, ustaw, jeśli to konieczne. Zestawy reguł można zastosować do jednego lub wielu projektów w rozwiązaniu.

> [!NOTE]
> Ten artykuł ma zastosowanie do starszej analizy, a nie do [.NET compiler platform analizatorów kodu](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurowanie zestawu reguł dla projektu .NET Framework

1. Otwórz **analizy kodu** kartę na stronach właściwości projektu. Można to zrobić w jeden z następujących sposobów:

   - W **Eksploratora rozwiązań**, wybierz projekt. Na pasku menu wybierz **analizy** > **Konfigurowanie analizy kodu** > **dla \<nazwa_projektu >** .

   - Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**, a następnie wybierz pozycję **analizy kodu** kartę.

2. W **konfiguracji** i **platformy** listy, wybierz platformę konfiguracji i docelowej kompilacji.

::: moniker range="vs-2017"

3. Aby uruchomić analizę kodu za każdym razem, gdy projekt zostanie skompilowany przy użyciu wybranej konfiguracji, wybierz pozycję **Włącz analizę kodu podczas kompilacji**. Można również uruchomić analizę kodu ręcznie, wybierając **analizy** > **Uruchom analizę kodu** > **Uruchom analizę kodu dla \<nazwa_projektu >** .

::: moniker-end

::: moniker range=">=vs-2019"

3. Aby uruchomić analizę kodu za każdym razem, gdy projekt został skompilowany przy użyciu wybranej konfiguracji, wybierz pozycję **Uruchom przy kompilacji** w sekcji **analizatory binarne** . Można również uruchomić analizę kodu ręcznie, wybierając **analizy** > **Uruchom analizę kodu** > **Uruchom analizę kodu dla \<nazwa_projektu >** .

::: moniker-end

4. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, należy wyczyścić **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.

    > [!NOTE]
    > Ta opcja nie pomija błędy analizy kodu i ostrzeżenia z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Możesz wyświetlić i zachować kod źródłowy formularza lub szablonu i nie zostanie on zastąpiony.

::: moniker range="vs-2017"

5. W **Uruchom ten zestaw reguł** listy, wykonaj jedną z następujących czynności:

::: moniker-end

::: moniker range=">=vs-2019"

5. Na liście **aktywne reguły** wykonaj jedną z następujących czynności:

::: moniker-end

   - Wybierz zestaw reguł, który chcesz użyć.

   - Wybierz pozycję **\<przeglądaj >** , aby znaleźć istniejący niestandardowy zestaw reguł, którego nie ma na liście.

   - Zdefiniuj [niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Określanie zestawów reguł dla wielu projektów w rozwiązaniu

Domyślnie są przypisywane projektów zarządzanych rozwiązania *reguł zalecanych Minimum Microsoft* zestaw reguł analizy kodu. Można zmienić zestawów reguł, które są przypisane do projektów rozwiązania w **właściwości** okno dialogowe dla rozwiązania.

1. Otwórz rozwiązanie w programie Visual Studio.

2. Na **analizy** menu, wybierz opcję **Konfigurowanie analizy kodu dla rozwiązania**.

3. Jeśli to konieczne, rozwiń węzeł **wspólne właściwości**, a następnie wybierz pozycję **ustawienia analizy kodu**.

4. Można określić zestaw reguł dla jednego lub więcej projektów:

    - Aby określić zestaw reguł dla pojedynczego projektu, wybierz nazwę projektu.

    - Aby określić zestaw reguł dla wielu projektów, przytrzymaj wciśnięty **Ctrl** i wybrać nazwy projektu.

    - Aby określić wszystkie projekty w rozwiązaniu, przytrzymaj wciśnięty **Shift** i kliknij pozycję na liście projektu.

5. Wybierz **zestaw reguł** pole projektu, a następnie wybierz nazwę reguły, ustaw chcesz zastosować.

## <a name="see-also"></a>Zobacz także

- [Informacje o zestawie reguł analizy kodu](../code-quality/rule-set-reference.md)
