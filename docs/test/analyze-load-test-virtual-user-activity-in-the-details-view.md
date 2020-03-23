---
title: Analizowanie aktywności wirtualnego użytkownika testu obciążenia
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
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591238"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analizowanie aktywności użytkownika wirtualnego testu obciążenia w widoku Szczegóły analizatora testów obciążenia

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Wykres aktywności użytkownika wirtualnego**

![Wykres aktywności użytkownika wirtualnego](../test/media/virtual_actchart.png)

Widok **Szczegóły** wyświetla **wykres aktywności użytkownika wirtualnego,** który służy do wizualnej analizy tego, co poszczególne użytkownicy wirtualni zrobili podczas testu obciążenia. **Wykres aktywności użytkownika wirtualnego** umożliwia wyświetlanie wzorców aktywności użytkownika, wzorców obciążenia, skorelowania nieudanych lub powolnych testów oraz wyświetlanie żądań z inną aktywnością użytkownika wirtualnego. **Wykres aktywności użytkownika wirtualnego** może również pomóc w określeniu skoków użycia procesora CPU, spadków żądań na sekundę oraz testów lub stron uruchomionych podczas skoków i upadków.

> [!NOTE]
> Przed uruchomieniem testu obciążenia, dla którego chcesz użyć **wykresu szczegółów aktywności użytkownika wirtualnego,** należy sprawdzić, czy właściwość **Magazyn szczegółów chronometrażu** jest ustawiona na opcję **AllIndividualDetails** przy użyciu Edytora testu wydajności ładowania.

**Panel Legenda szczegółów**

![Panel Legenda szczegółów](../test/media/ltest_detailslegend.png)

Panel legendy szczegółów jest widoczny na **wykresie aktywności użytkownika wirtualnego**. Okienko legendy szczegółów umożliwia odfiltrowanie testów, stron i transakcji na podstawie kilku różnych kryteriów. Na przykład można usunąć niektóre testy z widoku lub usunąć wszystkie pomyślne testy lub usunąć testy, które nie powiodły się z niektórych błędów. Można również usunąć wszystkie testy, które nie mają dzienników.

Można wyróżnić testy, które nie powiodły się, który wyświetla wszystkie testy nie powiodło się w kolorze czerwonym. Można również wyróżnić testy, które mają dzienniki testów. Testy z dziennikami będą kolorowe na zielono.

**Panel wyników filtru**

![Panel wyników filtrowania](../test/media/ltest_filterresults.png)

Panel Wyniki filtru jest widoczny na **wykresie aktywności użytkownika wirtualnego**. Panel Wyniki filtru można filtrować w następujący sposób:

- **Pokaż tylko wyniki z dziennikami** Wyświetla tylko wyniki testów, które mają dzienniki testów skojarzone z nimi.

- **Pokaż pomyślne wyniki** Wyświetla pomyślne wyniki.

- **Pokaż wyniki z błędami** Wyświetla wyniki z błędami, które mogą pomóc w debugowaniu.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Uruchom test obciążenia:** Po utworzeniu testu obciążenia i skonfigurowaniu go w taki sposób, aby umożliwić zbieranie danych o aktywności użytkownika wirtualnego, należy go uruchomić do czasu jego zakończenia, aby wyświetlić **wykres aktywności użytkownika wirtualnego**.||
|**Wyświetlanie wyników testu obciążenia, które zawierają dane aktywności użytkownika wirtualnego:** Po utworzeniu, skonfigurowaniu i uruchomieniu testu obciążenia można wyświetlić dane aktywności użytkownika wirtualnego za pomocą **wykresu aktywności użytkownika wirtualnego**.|-   [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Jak: Analizowanie, co użytkownicy wirtualni robią podczas testu obciążenia](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Izoluj problemy z wydajnością w testach obciążenia:** Wykres aktywności **użytkownika wirtualnego** służy do wyizolowania problemów z wydajnością w teście obciążenia.|-   [Instruktaż: Używanie wykresu aktywności użytkownika wirtualnego do izolowania problemów](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie wyników testów obciążenia i błędów w widoku Tabele](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
