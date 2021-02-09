---
title: Korzystanie z zasad zaewidencjonowania analizy kodu
ms.date: 11/04/2016
description: Dowiedz się, jak używać zasad zaewidencjonowania analizy kodu, aby sprawdzić, czy kod jest zgodny z dziedziczeniem, sprzęgiem klas, łatwość konserwacji i standardami złożoności.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f061d9d10d66857a0b2506d13d6d6671f7df401
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860048"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Instrukcje: wymuszanie kodu utrzymującego za pomocą zasad ewidencjonowania analizy kodu

Deweloperzy mogą używać narzędzia metryki kodu do mierzenia złożoności i utrzymania kodu, ale nie można wywoływać metryk kodu jako części zasad ewidencjonowania. Można jednak włączyć reguły analizy kodu, które weryfikują zgodność kodu za pomocą standardów metryk kodu i wymuszać reguły przy użyciu zasad ewidencjonowania. Aby uzyskać więcej informacji o metrykach kodu, zobacz [wartości metryk kodu](../code-quality/code-metrics-values.md).

Możesz włączyć głębokość dziedziczenia, sprzęgania klas, indeks utrzymania i reguły złożoności, aby wymusić obsługę kodu za pomocą zasad ewidencjonowania analizy kodu. Wszystkie cztery te reguły są dostępne w kategorii "reguły utrzymania" w edytorze zasad analizy kodu.

Administratorzy kontroli wersji programu Team Foundation mogą dodać reguły utrzymania analizy kodu do wymagań zasad ewidencjonowania. Te zasady ewidencjonowania wymagają od deweloperów uruchomienia analizy kodu na podstawie tych zmian reguł przed zainicjowaniem zaewidencjonowania.

## <a name="to-open-the-code-analysis-policy-editor"></a>Aby otworzyć Edytor zasad analizy kodu

1. W **Team Explorer** kliknij prawym przyciskiem myszy projekt, kliknij pozycję **Ustawienia projektu**, a następnie kliknij pozycję **Kontrola źródła**.

     Zostanie wyświetlone okno dialogowe **Kontrola źródła** .

2. Na karcie **zasady ewidencjonowania** i kliknij przycisk **Dodaj**.

     Zostanie wyświetlone okno dialogowe **Dodawanie zasad ewidencjonowania** .

3. Na liście **zasad ewidencjonowania** zaznacz pole wyboru **Analiza kodu** , a następnie kliknij przycisk **OK**.

     Zostanie wyświetlone okno dialogowe **Edytor zasad analizy kodu** .

## <a name="to-enable-code-analysis-maintainability-rules"></a>Aby włączyć reguły utrzymania analizy kodu

1. W oknie dialogowym **Edytor zasad analizy kodu** w obszarze **Ustawienia reguły** rozwiń węzeł **reguły utrzymania** .

2. Zaznacz pola wyboru dla następujących reguł:

   - Głębokość dziedziczenia: **CA1501 AvoidExcessiveInheritance** — próg: ostrzeżenie na ponad 5 poziomach głębokości

   - Złożoność: **CA1502 AvoidExcessiveComplexity** — próg: Ostrzeżenie o więcej niż 25

   - Indeks utrzymania: **CA1505 AvoidUnmaintainableCode** — próg: ostrzeżenie przy mniej niż 20

   - Sprzęganie klas: **CA1506 AvoidExcessiveClassCoupling** -Threshold: Ostrzeżenie o więcej niż 80 dla klasy i ponad 30 dla metody

     Ponadto, jeśli chcesz, aby naruszenie zasad nie powodowało pomyślnej kompilacji, zaznacz pole wyboru **Traktuj ostrzeżenie jako błąd** obok opisu reguły.

3. Kliknij przycisk **OK**. Nowe zasady ewidencjonowania mają teraz zastosowanie do przyszłych zaewidencjonowania.

## <a name="see-also"></a>Zobacz też

- [Wartości metryk kodu](../code-quality/code-metrics-values.md)
- [Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
