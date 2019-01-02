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
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 484c80e474fdce799bc10787bddf157a19f46740
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902922"
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

-   **Pokaż tylko wyniki z dziennikami** wyświetla tylko wyniki, które mają dzienniki testów skojarzonych z nimi.

-   **Pokaż pomyślne wyniki** Wyświetla pomyślne wyniki.

-   **Pokaż wyniki z błędami** wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Uruchom test obciążenia:** Po utworzeniu testu obciążenia i skonfigurować go, aby włączyć zbieranie danych aktywności wirtualnego użytkownika, należy uruchomić test do czasu jego zakończenia w celu wyświetlenia **wykres aktywności wirtualnych użytkowników**.||
|**Wyświetl wyniki testu obciążenia, które zawierają dane o aktywności użytkownika wirtualnego:** Po testu obciążenia zostało utworzone, skonfigurowane i zakończy działanie, można wyświetlić dane o aktywności wirtualnego użytkownika za pomocą **wykres aktywności wirtualnych użytkowników**.|-   [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Jak: Analizowanie, co robią użytkownicy wirtualni podczas testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Wyizolować problemy z wydajnością w testach obciążenia:** Możesz użyć **wykres aktywności wirtualnych użytkowników** Aby wyizolować problemy z wydajnością w teście obciążenia.|-   [Wskazówki: Za pomocą wykresu aktywności wirtualnego użytkownika umożliwiającego Wyizolowanie problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)