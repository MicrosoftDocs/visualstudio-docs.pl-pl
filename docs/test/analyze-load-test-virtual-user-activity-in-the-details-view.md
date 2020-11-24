---
title: Analizowanie aktywności wirtualnego użytkownika testu obciążenia
description: Dowiedz się więcej o widoku szczegółów, który wyświetla wykres aktywności wirtualnego użytkownika. Przeanalizuj zawartość poszczególnych użytkowników wirtualnych podczas testu obciążenia.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c05a907bf75ffcdff5bb579ec2624e0dc8a7df9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441901"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analizowanie aktywności wirtualnego użytkownika testu obciążenia w widoku szczegółów analizatora testu obciążenia

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Wykres aktywności wirtualnego użytkownika**

![Wykres aktywności wirtualnego użytkownika](../test/media/virtual_actchart.png)

W widoku **szczegółów** zostanie wyświetlony **Wykres aktywności wirtualnego użytkownika**, który służy do wizualnego analizowania poszczególnych użytkowników wirtualnych podczas testu obciążenia. **Wykres aktywności wirtualnego użytkownika** umożliwia wyświetlenie wzorców aktywności użytkownika, wzorców obciążenia, skorelowanie nieudanych lub powolnych testów oraz wyświetlanie żądań z innymi wirtualnymi działaniami użytkowników. **Wykres aktywności wirtualnego użytkownika** może również pomóc w ustaleniu szczytów użycia procesora, spadku żądań na sekundę oraz testów lub stron, które zostały uruchomione podczas skoków i porzucania.

> [!NOTE]
> Przed uruchomieniem testu obciążenia, dla którego chcesz użyć **wykresu szczegółów aktywności wirtualnego użytkownika**, należy sprawdzić, czy właściwość **przechowywanie szczegółów czasu** jest ustawiona na opcję **AllIndividualDetails** za pomocą edytora testu wydajności obciążenia.

**Panel legendy szczegółów**

![Panel legendy szczegółów](../test/media/ltest_detailslegend.png)

Panel legenda szczegółów jest widoczny na **wykresie aktywności wirtualnego użytkownika**. Okienko legenda szczegółów umożliwia filtrowanie testów, stron i transakcji na podstawie różnych kryteriów. Na przykład można usunąć niektóre testy z widoku lub usunąć wszystkie testy zakończone powodzeniem lub usunąć testy, które zakończyły się niepowodzeniem z pewnymi błędami. Można również usunąć wszystkie testy, które nie mają dzienników.

Można wyróżnić testy, które nie powiodły się, co spowoduje wyświetlenie wszystkich testów zakończonych niepowodzeniem w kolorze czerwonym. Możesz również wyróżnić testy, które mają dzienniki testowe. Testy z dziennikami będą kolorowe w kolorze zielonym.

**Panel wyników filtrowania**

![Panel wyników filtrowania](../test/media/ltest_filterresults.png)

Panel wyniki filtrowania jest widoczny na **wykresie aktywności wirtualnego użytkownika**. Panel wyniki filtrowania może odfiltrować następujące elementy:

- **Pokaż tylko wyniki z dziennikami** Wyświetla tylko wyniki testów, które mają skojarzone dzienniki testowe.

- **Pokaż pomyślne wyniki** Wyświetla wyniki zakończone powodzeniem.

- **Pokaż wyniki z błędami** Wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Uruchom test obciążenia:** Po utworzeniu testu obciążenia i skonfigurowaniu go w celu umożliwienia zbierania danych aktywności wirtualnego użytkownika należy uruchomić test do momentu jego zakończenia, aby wyświetlić **Wykres aktywności wirtualnego użytkownika**.||
|**Wyświetl wyniki testu obciążenia zawierające dane dotyczące wirtualnego działania użytkownika:** Po utworzeniu, skonfigurowaniu i zakończeniu testu obciążenia można wyświetlić dane dotyczące aktywności wirtualnego użytkownika za pomocą **wykresu aktywności wirtualnego użytkownika**.|-   [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Instrukcje: analizowanie, co robią Użytkownicy wirtualną podczas testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Izolowanie problemów z wydajnością w testach obciążenia:** Za pomocą **wykresu aktywności wirtualnego użytkownika** można wyizolować problemy z wydajnością w teście obciążenia.|-   [Przewodnik: używanie wykresu aktywności wirtualnego użytkownika w celu wyizolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia i błędów w widoku tabel](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
