---
title: Odpowiadanie na zmiany i propagowanie zmian
description: Dowiedz się, że po utworzeniu, usunięciu lub zaktualizowaniu elementu możesz napisać kod, który propaguje zmianę do innych części modelu lub do zasobów zewnętrznych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6fc8345ca90414f410dde9a089d9529ed19536b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387583"
---
# <a name="respond-to-and-propagate-changes"></a>Odpowiadanie na zmiany i propagowanie ich

Gdy element jest tworzony, usuwany lub aktualizowany, można napisać kod, który propaguje zmianę do innych części modelu lub do zasobów zewnętrznych, takich jak pliki, bazy danych lub inne składniki.

## <a name="reference"></a>Odwołanie

Jako wskazówki rozważ te techniki w następującej kolejności:

|Technika|Scenariusze|Więcej informacji|
|-|-|-|
|Definiowanie właściwości domeny obliczeniowej.|Właściwość domeny, której wartość jest obliczana na podstawie innych właściwości w modelu. Na przykład cena, która jest sumą cen powiązanych elementów.|[Obliczone i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md)|
|Zdefiniuj właściwość domeny magazynu niestandardowego.|Właściwość domeny przechowywana w innych częściach modelu lub na zewnątrz. Na przykład ciąg wyrażenia można ująć w drzewo w modelu.|[Obliczone i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md)|
|Przesłanianie programów obsługi zmian, takich jak OnValueChanging i OnDeleting|Synchronizuj różne elementy i synchronizuj wartości zewnętrzne z modelem.<br /><br /> Ogranicz wartości do zdefiniowanych zakresów.<br /><br /> Wywoływana bezpośrednio przed wartością właściwości i po jej zakończeniu oraz innymi zmianami. Zmianę można zakończyć, zgłaszając wyjątek.|[Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md)|
|Reguły|Można zdefiniować reguły, które są w kolejce do wykonania tuż przed końcem transakcji, w której miała miejsce zmiana. Nie są one wykonywane w przypadku cofania ani ponownego wykonania. Użyj ich, aby zachować jedną część magazynu w zsynchronizowaniu z inną.|[Reguły propagujące zmiany w modelu](../modeling/rules-propagate-changes-within-the-model.md)|
|Przechowywanie zdarzeń|Magazyn modelowania udostępnia powiadomienia o zdarzeniach, takich jak dodawanie lub usuwanie elementu lub linku albo zmienianie wartości właściwości. Zdarzenie jest również wykonywane w przypadku cofania i ponownego wykonania. Użyj zdarzeń magazynu, aby zaktualizować wartości, które nie znajdują się w magazynie.|[Programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Zdarzenia .NET|Kształty mają procedury obsługi zdarzeń, które reagują na kliknięcia myszą i inne gesty. Należy zarejestrować te zdarzenia dla każdego obiektu. Rejestracja jest zwykle wykonywana w zastąpień elementu InitializeInstanceResources i musi być wykonywana dla każdego elementu.<br /><br /> Te zdarzenia zwykle występują poza transakcją.|[Instrukcje: Przechwytywanie kliknięć w kształcie lub elemencie Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Reguły granic|Reguła granic jest używana specjalnie w celu ograniczenia granic kształtu.|[BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Reguły wyboru|Reguły wyboru ograniczają w szczególności to, co użytkownik może wybrać.|[Porady: ograniczenie bieżącego wyboru i uzyskiwanie dostępu do niego](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Wskazywanie stanów elementów modelu przy użyciu funkcji kształtów i łączników, takich jak cienie, strzałki, kolor i szerokość linii oraz styl.|[Aktualizowanie kształtów i łączników, aby odzwierciedlały model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Porównywanie reguł i przechowywanie zdarzeń

Powiadomienia o zmianach, reguły i zdarzenia są uruchamiane, gdy w modelu wystąpią zmiany.

Reguły są zwykle stosowane w transakcji końcowej, w której nastąpiła zmiana, a zdarzenia są stosowane po zatwierdzone zmiany w transakcji.

Użyj zdarzeń magazynu, aby zsynchronizować model z obiektami spoza magazynu, oraz reguł w celu zachowania spójności w ramach magazynu.

- **Tworzenie reguł niestandardowych** Regułę niestandardową tworzy się jako klasę pochodną na podstawie reguły abstrakcyjnej. Należy również powiadomić platformę o regułę niestandardową. Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

- **Subskrybowanie zdarzeń** Zanim będzie można zasubskrybować zdarzenie, utwórz program obsługi zdarzeń i deleguj. Następnie użyj właściwości <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> , aby zasubskrybować zdarzenie. Aby uzyskać więcej informacji, zobacz [Programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Cofanie zmian** Po cofnięcie transakcji są wywoływane zdarzenia, ale reguły nie są stosowane. Jeśli reguła zmieni wartość i cofniesz zmianę, wartość zostanie zresetowana do oryginalnej wartości podczas akcji cofania. Po zdarzeniu należy ręcznie zmienić wartość z powrotem na jej oryginalną wartość. Aby dowiedzieć się więcej na temat transakcji i cofania, zobacz [Jak: używać transakcji do aktualizowania modelu](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Przekazywanie argumentów zdarzeń do reguł i zdarzeń** Zarówno zdarzenia, jak i reguły są przekazywane `EventArgs` jako parametr, który zawiera informacje o tym, jak zmienił się model.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Przechwytywanie kliknięć w kształcie lub elemencie Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Pisanie kodu w celu dostosowania Domain-Specific językowego](../modeling/writing-code-to-customise-a-domain-specific-language.md)