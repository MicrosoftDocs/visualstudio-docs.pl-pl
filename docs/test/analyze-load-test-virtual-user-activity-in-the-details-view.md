---
title: Analizowanie aktywności wirtualnego użytkownika testów obciążenia
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a03096e92f2a5da98da2d1850f505c65eb5b6e27
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918621"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analizowanie aktywności wirtualnego użytkownika testów obciążenia w widoku szczegółów analizatora testu obciążenia

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Wykresu aktywności wirtualnego użytkownika**

![Wykresu aktywności wirtualnego użytkownika](../test/media/virtual_actchart.png)

**Szczegóły** wyświetlić Wyświetla **wykres aktywności wirtualnych użytkowników**, który jest używany do wizualnie Analizuj poszczególnych użytkowników wirtualnych zostało podczas testu obciążeniowego. **Wykres aktywności wirtualnych użytkowników** pozwala widać wzorce aktywności użytkowników, wzorce obciążenia, korelować testy zakończone niepowodzeniem lub wolne i zobacz żądań z innych działań wirtualnego użytkownika. **Wykres aktywności wirtualnych użytkowników** można także pomocy, możesz określić skokami użycia procesora CPU, przerwy w żądań na sekundę i co testów lub strony były uruchamiane podczas wzrostów i spadnie.

> [!NOTE]
> Przed uruchomieniem testu obciążeniowego, dla którego chcesz użyć **wykres szczegóły aktywności wirtualnych użytkowników**, należy sprawdzić, czy **przechowywanie informacji** właściwość jest ustawiona na  **AllIndividualDetails** opcji za pomocą edytora testu obciążenia wydajności.

**Legenda szczegółów — Panel**

![Legenda szczegółów — panel](../test/media/ltest_detailslegend.png)

Legenda szczegółów — panel jest widoczna w **wykres aktywności wirtualnych użytkowników**. Szczegóły legendy okienko pozwala filtrować testy, strony i transakcje na podstawie kilku różnych kryteriów. Na przykład możesz usunąć niektóre testy z widoku, lub Usuń wszystkie testy zakończone powodzeniem lub usunąć testów, których nie powiodła się z pewnych błędów. Można również usunąć wszystkie testy, które nie mają dzienniki.

Można wyróżnić testy, których nie powiodła się, powoduje wyświetlenie wszystkich testów zakończonych niepowodzeniem pokolorowane w kolorze czerwonym. Można również wyróżnić testy, które mają dzienników testu. Testy za pomocą dzienników będą kolorowane w kolorze zielonym.

**Filtrowanie wyników Panel**

![Panel wyników filtrowania](../test/media/ltest_filterresults.png)

Panel wyników filtru jest widoczny w **wykres aktywności wirtualnych użytkowników**. Panel wyników filtrowania można filtrować od następujących czynników:

- **Pokaż tylko wyniki z dziennikami** wyświetla tylko wyniki, które mają dzienniki testów skojarzonych z nimi.

- **Pokaż pomyślne wyniki** Wyświetla pomyślne wyniki.

- **Pokaż wyniki z błędami** wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Uruchom test obciążenia:** Po utworzeniu testu obciążenia i skonfigurowaniu go w celu umożliwienia zbierania danych aktywności wirtualnego użytkownika należy uruchomić test do momentu jego zakończenia, aby wyświetlić **Wykres aktywności wirtualnego użytkownika**.||
|**Wyświetl wyniki testu obciążenia zawierające dane dotyczące wirtualnego działania użytkownika:** Po utworzeniu, skonfigurowaniu i zakończeniu testu obciążenia można wyświetlić dane dotyczące aktywności wirtualnego użytkownika za pomocą **wykresu aktywności wirtualnego użytkownika**.|-   [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Jak: Analizowanie, co robią Użytkownicy wirtualną podczas testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Izolowanie problemów z wydajnością w testach obciążenia:** Za pomocą **wykresu aktywności wirtualnego użytkownika** można wyizolować problemy z wydajnością w teście obciążenia.|-   [Instruktaż Używanie wykresu aktywności wirtualnego użytkownika w celu wyizolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)