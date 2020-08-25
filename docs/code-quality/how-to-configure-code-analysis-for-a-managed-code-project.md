---
title: Konfiguruj analizę kodu
ms.date: 04/04/2018
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
- vs.codeanalysis.propertypages.asp
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c94742b452bfd665dc35c59ef831bca2cdacf1f5
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801051"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Instrukcje: Konfigurowanie starszej analizy dla kodu zarządzanego

W programie Visual Studio można wybrać spośród listy [zestawów reguł](../code-quality/rule-set-reference.md) analizy kodu, które mają zostać zastosowane do projektu kodu zarządzanego. Domyślnie jest wybierany **minimalny zalecany zestaw reguł firmy Microsoft** , ale w razie potrzeby można zastosować inny zestaw reguł. Zestawy reguł można stosować do jednego lub wielu projektów w rozwiązaniu.

> [!NOTE]
> Ten artykuł ma zastosowanie do starszej analizy, a nie do [.NET compiler platform analizatorów kodu](use-roslyn-analyzers.md).

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurowanie zestawu reguł dla projektu .NET Framework

1. Otwórz kartę **Analiza kodu** na stronach właściwości projektu. Można to zrobić w jeden z następujących sposobów:

   - W **Eksplorator rozwiązań**wybierz projekt. Na pasku menu wybierz pozycję **Analizuj**  >  **Skonfiguruj analizę kodu**  >  **dla \<projectname> **.

   - Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**, a następnie wybierz kartę **Analiza kodu** .

2. Na listach **Konfiguracja** i **platforma** wybierz konfigurację kompilacji i platformę docelową.

::: moniker range="vs-2017"

3. Aby uruchomić analizę kodu za każdym razem, gdy projekt zostanie skompilowany przy użyciu wybranej konfiguracji, wybierz pozycję **Włącz analizę kodu podczas kompilacji**. Możesz również ręcznie uruchomić analizę kodu, wybierając pozycję **Analizuj**Przeprowadź analizę kodu  >  **Run Code Analysis**  >  **Uruchom analizę kodu \<projectname> na **.

::: moniker-end

::: moniker range=">=vs-2019"

3. Aby uruchomić analizę kodu za każdym razem, gdy projekt został skompilowany przy użyciu wybranej konfiguracji, wybierz pozycję **Uruchom przy kompilacji** w sekcji **analizatory binarne** . Możesz również ręcznie uruchomić starszą analizę kodu, zobacz [jak: uruchamianie starszej analizy kodu ręcznie dla kodu zarządzanego](how-to-run-legacy-code-analysis-manually-for-managed-code.md) , aby uzyskać więcej szczegółów.

::: moniker-end

4. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, wyczyść pole wyboru **Pomiń wyniki z wygenerowanego kodu** .

    > [!NOTE]
    > Ta opcja nie powoduje pomijania błędów analizy kodu i ostrzeżeń z wygenerowanego kodu, gdy błędy i ostrzeżenia pojawiają się w formularzach i szablonach. Możesz wyświetlić i zachować kod źródłowy formularza lub szablonu i nie zostanie on zastąpiony.

::: moniker range="vs-2017"

5. Na liście **Uruchom ten zestaw reguł** wykonaj jedną z następujących czynności:

::: moniker-end

::: moniker range=">=vs-2019"

5. Na liście **aktywne reguły** wykonaj jedną z następujących czynności:

::: moniker-end

   - Wybierz zestaw reguł, którego chcesz użyć.

   - Wybierz **\<Browse>** , aby znaleźć istniejący niestandardowy zestaw reguł, którego nie ma na liście.

   - Zdefiniuj [niestandardowy zestaw reguł](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Określanie zestawów reguł dla wielu projektów w rozwiązaniu

Domyślnie wszystkie zarządzane projekty rozwiązania są przypisane do zestawu reguł analizy kodów *minimalnych zalecanych reguł firmy Microsoft* . Zestawy reguł, które są przypisane do projektów rozwiązania, można zmienić w oknie dialogowym **Właściwości** rozwiązania.

1. Otwórz rozwiązanie w programie Visual Studio.

2. W menu **Analizuj** wybierz pozycję **Konfiguruj analizę kodu dla rozwiązania**.

3. W razie potrzeby rozwiń węzeł **wspólne właściwości**, a następnie wybierz pozycję **Ustawienia analizy kodu**.

4. Można określić zestaw reguł dla jednego lub kilku projektów:

    - Aby określić zestaw reguł dla danego projektu, wybierz nazwę projektu.

    - Aby określić zestaw reguł dla wielu projektów, wybierz pozycję **Ctrl** i nazwy projektów.

    - Aby określić wszystkie projekty w rozwiązaniu, wybierz pozycję **przesunięcia** i listę projektu.

5. Zaznacz pole **zestaw reguł** projektu, a następnie wybierz nazwę zestawu reguł, który ma zostać zastosowany.

## <a name="see-also"></a>Zobacz też

- [Odwołanie zestawu reguł analizy kodu](../code-quality/rule-set-reference.md)
