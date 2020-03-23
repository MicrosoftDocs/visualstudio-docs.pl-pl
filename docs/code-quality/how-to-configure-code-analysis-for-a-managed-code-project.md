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
ms.openlocfilehash: 98db7cda02495d207d6e9387341173ea2efe22ca
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431355"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Jak: Konfigurowanie starszej analizy dla kodu zarządzanego

W programie Visual Studio można wybrać z listy [zestawów reguł](../code-quality/rule-set-reference.md) analizy kodu, aby zastosować do projektu kodu zarządzanego. Domyślnie jest zaznaczony zestaw reguł **minimalnych zalecanych reguł** firmy Microsoft, ale w razie potrzeby można zastosować inny zestaw reguł. Zestawy reguł mogą być stosowane do jednego lub wielu projektów w rozwiązaniu.

> [!NOTE]
> Ten artykuł dotyczy starszej analizy, a nie [analizatorów kodu opartych na platformie kompilatora .NET.](use-roslyn-analyzers.md)

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurowanie zestawu reguł dla projektu programu .NET Framework

1. Otwórz kartę **Analiza kodu** na stronach właściwości projektu. Można to zrobić w jeden z następujących sposobów:

   - W **Eksploratorze rozwiązań**wybierz projekt. Na pasku menu wybierz pozycję >  **Analizuj** > **konfiguruj analizę kodu**dla** \<>projectname **.

   - Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**, a następnie wybierz kartę **Analiza kodu.**

2. Na listach **Konfiguracja** i **Platforma** wybierz konfigurację kompilacji i platformę docelową.

::: moniker range="vs-2017"

3. Aby przeprowadzić analizę kodu za każdym razem, gdy projekt jest budowany przy użyciu wybranej konfiguracji, wybierz **włącz analizę kodu na kompilacji**. Analizę kodu można również uruchomić ręcznie, wybierając **opcję Analizuj** > analizę**przebiegu analizy** > kodu**uruchamiania na \<>projectname **.

::: moniker-end

::: moniker range=">=vs-2019"

3. Aby uruchomić analizę kodu za każdym razem, gdy projekt jest zbudowany przy użyciu wybranej konfiguracji, wybierz **uruchom na kompilacji** w sekcji **Analizatory binarne.** Można również uruchomić starszą analizę kodu ręcznie, zobacz [Jak: Uruchom starszą analizę kodu ręcznie dla kodu zarządzanego, aby](how-to-run-legacy-code-analysis-manually-for-managed-code.md) uzyskać więcej informacji.

::: moniker-end

4. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, wyczyść pole wyboru **Wygaszanie wyników z wygenerowanego kodu.**

    > [!NOTE]
    > Ta opcja nie pomija błędów analizy kodu i ostrzeżeń z wygenerowanego kodu, gdy błędy i ostrzeżenia pojawiają się w formularzach i szablonach. Można zarówno wyświetlić i zachować kod źródłowy dla formularza lub szablonu i nie zostanie zastąpiony.

::: moniker range="vs-2017"

5. Na liście **Uruchom ten zestaw reguł** wykonaj jedną z następujących czynności:

::: moniker-end

::: moniker range=">=vs-2019"

5. Na liście **Aktywne reguły** wykonaj jedną z następujących czynności:

::: moniker-end

   - Wybierz zestaw reguł, którego chcesz użyć.

   - Wybierz ** \<opcję Przeglądaj>,** aby znaleźć istniejący niestandardowy zestaw reguł, których nie ma na liście.

   - Zdefiniuj [niestandardowy zestaw reguł](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Określanie zestawów reguł dla wielu projektów w rozwiązaniu

Domyślnie wszystkim zarządzanym projektom rozwiązania jest przypisywany zestaw reguł analizy kodu *minimalnych zalecanych reguł firmy Microsoft.* Można zmienić zestawy reguł, które są przypisane do projektów rozwiązania w oknie dialogowym **Właściwości** dla rozwiązania.

1. Otwórz rozwiązanie w programie Visual Studio.

2. W menu **Analiza** wybierz polecenie **Konfiguruj analizę kodu dla rozwiązania**.

3. W razie potrzeby rozwiń węzeł **Właściwości wspólne**, a następnie wybierz pozycję Ustawienia **analizy kodu**.

4. Można określić zestaw reguł dla jednego lub więcej projektów:

    - Aby określić zestaw reguł dla pojedynczego projektu, wybierz nazwę projektu.

    - Aby określić zestaw reguł dla wielu projektów, przytrzymaj naciśnięty **klawisz Ctrl** i wybierz nazwy projektów.

    - Aby określić wszystkie projekty w rozwiązaniu, przytrzymaj naciśnięty **klawisz Shift** i kliknij na liście projektów.

5. Zaznacz pole **Zestaw reguł** projektu, a następnie wybierz nazwę zestawu reguł, który chcesz zastosować.

## <a name="see-also"></a>Zobacz też

- [Odwołanie zestawu reguł analizy kodu](../code-quality/rule-set-reference.md)
