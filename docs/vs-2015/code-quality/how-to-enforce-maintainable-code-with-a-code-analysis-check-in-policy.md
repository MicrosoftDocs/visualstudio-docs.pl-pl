---
title: 'Instrukcje: wymuszanie kodu utrzymującego za pomocą zasad ewidencjonowania analizy kodu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660218"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Porady: wymuszanie kodu za pomocą zasad ewidencjonowania analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deweloperzy mogą używać narzędzia metryki kodu do mierzenia stopnia złożoności i utrzymania kodu, ale nie mogą wywoływać metryk kodu w ramach zasad ewidencjonowania. Jednak zespół może włączyć reguły analizy kodu, które weryfikują zgodność kodu z wzorcem metryk kodu i wymuszają reguły przy użyciu zasad ewidencjonowania. Aby uzyskać więcej informacji o metrykach kodu, zobacz [wartości metryk kodu](../code-quality/code-metrics-values.md).

 Deweloperzy mogą włączać głębokość dziedziczenia, sprzęgania klas, indeks utrzymania i reguły złożoności, aby wymusić obsługę kodu za pomocą zasad ewidencjonowania analizy kodu. Wszystkie cztery te reguły są dostępne w kategorii "reguły utrzymania" w edytorze zasad analizy kodu.

 Administratorzy kontroli wersji dla [!INCLUDE[esprfound](../includes/esprfound-md.md)] mogą dodać reguły utrzymania analizy kodu do wymagań zasad ewidencjonowania. Te zasady ewidencjonowania wymagają od deweloperów uruchomienia analizy kodu na podstawie tych zmian reguł przed zainicjowaniem zaewidencjonowania.

### <a name="to-open-the-code-analysis-policy-editor"></a>Aby otworzyć Edytor zasad analizy kodu

1. W **Team Explorer**kliknij prawym przyciskiem myszy projekt zespołowy, kliknij pozycję **Ustawienia projektu zespołowego**, a następnie kliknij pozycję **Kontrola źródła**.

     Zostanie wyświetlone okno dialogowe **Kontrola źródła** .

2. Na karcie **zasady ewidencjonowania** i kliknij przycisk **Dodaj**.

     Zostanie wyświetlone okno dialogowe **Dodawanie zasad ewidencjonowania** .

3. Na liście **zasad ewidencjonowania** zaznacz pole wyboru **Analiza kodu** , a następnie kliknij przycisk **OK**.

     Zostanie wyświetlone okno dialogowe **Edytor zasad analizy kodu** .

### <a name="to-enable-code-analysis-maintainability-rules"></a>Aby włączyć reguły utrzymania analizy kodu

1. W oknie dialogowym **Edytor zasad analizy kodu** w obszarze **Ustawienia reguły**rozwiń węzeł **reguły utrzymania** .

2. Zaznacz pola wyboru dla następujących reguł:

    - Głębokość dziedziczenia: **CA1501 AvoidExcessiveInheritance** — próg: ostrzeżenie na ponad 5 poziomach głębokości

    - Złożoność: **CA1502 AvoidExcessiveComplexity** — próg: Ostrzeżenie o więcej niż 25

    - Indeks utrzymania: **CA1505 AvoidUnmaintainableCode** — próg: ostrzeżenie przy mniej niż 20

    - Sprzęganie klas: **CA1506 AvoidExcessiveClassCoupling** -Threshold: Ostrzeżenie o więcej niż 80 dla klasy i ponad 30 dla metody

    - Ponadto, jeśli chcesz, aby naruszenie reguły uniemożliwiło kompilację, zaznacz pole wyboru **Traktuj ostrzeżenie jako błąd** obok opisu reguły.

3. Kliknij przycisk **OK**. Nowe zasady ewidencjonowania mają teraz zastosowanie do przyszłych zaewidencjonowania.

## <a name="see-also"></a>Zobacz też
 [Wartości metryk kodu](../code-quality/code-metrics-values.md) [tworzenia i używania zasad zaewidencjonowania analizy kodu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
