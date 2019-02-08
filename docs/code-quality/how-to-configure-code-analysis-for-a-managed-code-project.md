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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 466178015c725242b6bc4a28da1da6ded19b421f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916795"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Instrukcje: Konfigurowanie analizy kodu dla projektu kodu zarządzanego

W programie Visual Studio, można wybrać z listy analizy kodu [zestawów reguł](../code-quality/rule-set-reference.md)) do zastosowania do projektu kodu zarządzanego. Domyślnie **reguł zalecanych Minimum Microsoft** zestaw reguł jest zaznaczone, ale można zastosować inną regułę, ustaw, jeśli to konieczne. Zestawy reguł można zastosować do jednego lub wielu projektów w rozwiązaniu.

> [!TIP]
> Aby uzyskać informacje o sposobie konfigurowania zestawu reguł dla aplikacji sieci web ASP.NET, zobacz [jak: Konfigurowanie analizy kodu dla sieci web platformy ASP.NET w aplikacji](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Aby skonfigurować zestaw reguł dla projektu .NET Framework

1. Otwórz **analizy kodu** kartę na stronach właściwości projektu. Można to zrobić na następujące sposoby:

   - W **Eksploratora rozwiązań**, wybierz projekt. Na pasku menu wybierz **analizy** > **Konfigurowanie analizy kodu** > **dla \<nazwa_projektu >**.

   - Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**, a następnie wybierz pozycję **analizy kodu** kartę.

1. W **konfiguracji** i **platformy** listy, wybierz platformę konfiguracji i docelowej kompilacji.

1. Aby uruchomić analizę kodu, za każdym razem, gdy projekt jest kompilowany przy użyciu wybranej konfiguracji, zaznacz **Włącz analizę kodu podczas kompilacji** pole wyboru. Można również uruchomić analizę kodu ręcznie, wybierając **analizy** > **Uruchom analizę kodu** > **Uruchom analizę kodu dla \<nazwa_projektu >**.

1. Domyślnie program analizy kodu nie raportuje ostrzeżenia z kodu, który jest generowany automatycznie przez narzędzia zewnętrzne. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, należy wyczyścić **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.

    > [!NOTE]
    > Ta opcja nie pomija błędy analizy kodu i ostrzeżenia z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Zarówno można przeglądać i zachować kod źródłowy dla formularza lub szablon, bez konieczności on zastąpiony.

1. W **Uruchom ten zestaw reguł** listy, wykonaj jedną z następujących czynności:

    - Wybierz zestaw reguł, który chcesz użyć.

    - Wybierz  **\<Przeglądaj … >** można znaleźć, ustaw istniejącej reguły niestandardowe, który nie jest na liście.

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
- [Instrukcje: Konfigurowanie analizy kodu dla sieci web platformy ASP.NET w aplikacji](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)