---
title: Odpowiadanie na zmiany i propagowanie zmian
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c9f108529931fc99946e18f15492f72384e1578
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809992"
---
# <a name="respond-to-and-propagate-changes"></a>Odpowiadanie na zmiany i propagowanie zmian

Gdy element jest tworzony, usuwany lub aktualizowany, można napisać kod, który propaguje zmianę do innych części modelu lub do zasobów zewnętrznych, takich jak pliki, bazy danych lub inne składniki.

## <a name="reference"></a>Dokumentacja

W ramach wytycznych należy wziąć pod uwagę następujące techniki w następującej kolejności:

|Technika|Scenariusze|Więcej informacji|
|-|-|-|
|Zdefiniuj właściwość domeny obliczeniowej.|Właściwość domeny, której wartość jest obliczana na podstawie innych właściwości w modelu. Na przykład cena jest sumą cen powiązanych elementów.|[Obliczone i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md)|
|Zdefiniuj niestandardową właściwość domeny magazynu.|Właściwość domeny przechowywana w innych częściach modelu lub zewnętrznie. Na przykład można przeanalizować ciąg wyrażenia w drzewie w modelu.|[Obliczone i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md)|
|Przesłoń procedury obsługi zmian, takie jak OnValueChanging i onusuwania|Utrzymuj synchronizację różnych elementów i Zachowaj wartości zewnętrzne w synchronizacji z modelem.<br /><br /> Ograniczenie wartości do zdefiniowanych zakresów.<br /><br /> Wywoływana bezpośrednio przed i po wartości właściwości i innych zmian. Możesz przerwać zmianę, zgłaszając wyjątek.|[Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md)|
|Reguły|Można zdefiniować reguły, które są umieszczane w kolejce do wykonania tuż przed końcem transakcji, w której nastąpiła zmiana. Nie są wykonywane przy cofaniu ani ponawiania. Użyj ich, aby zachować synchronizację jednej części sklepu z inną.|[Reguły propagujące zmiany w modelu](../modeling/rules-propagate-changes-within-the-model.md)|
|Zdarzenia ze sklepu|Magazyn modelowania udostępnia powiadomienia o zdarzeniach, takich jak dodawanie lub usuwanie elementu lub łącza lub zmiana wartości właściwości. To zdarzenie jest również wykonywane w przypadku cofania i ponawiania. Użyj zdarzeń ze sklepu, aby zaktualizować wartości, które nie znajdują się w sklepie.|[Programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Zdarzenia platformy .NET|Kształty zawierają programy obsługi zdarzeń reagujące na kliknięcia myszą i inne gesty. Musisz zarejestrować się w celu uzyskania tych zdarzeń dla każdego obiektu. Rejestracja zwykle odbywa się w przesłonięciu InitializeInstanceResources i musi być wykonana dla każdego elementu.<br /><br /> Te zdarzenia zwykle występują poza transakcją.|[Instrukcje: Przechwytywanie kliknięć w kształcie lub elemencie Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Reguły dotyczące granic|Reguła granic jest używana w celu ograniczenia granic kształtu.|[BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu](../vs-2015/modeling/boundsrules-constrain-shape-location-and-size.md?view=vs-2015)|
|Reguły wyboru|Reguły wyboru ograniczają możliwości wybranych przez użytkownika.|[Porady: ograniczenie bieżącego wyboru i uzyskiwanie dostępu do niego](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Wskaż Stany elementów modelu przy użyciu funkcji kształtów i łączników, takich jak cień, groty strzałek, kolor i szerokość linii oraz styl.|[Aktualizowanie kształtów i łączników, aby odzwierciedlały model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Porównywanie reguł i zdarzeń ze sklepu

Powiadomienia o zmianach, reguły i zdarzenia są uruchamiane, gdy w modelu wystąpią zmiany.

Reguły są zwykle stosowane w końcowej transakcji, w której nastąpiła zmiana, a zdarzenia są stosowane po zatwierdzeniu zmian w transakcji.

Użyj zdarzeń ze sklepu, aby zsynchronizować model z obiektami spoza magazynu i regułami, aby zachować spójność w sklepie.

- **Tworzenie reguł niestandardowych** Reguła niestandardowa jest tworzona jako Klasa pochodna z reguły abstrakcyjnej. Należy również powiadomić platformę o regule niestandardowej. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

- **Subskrybowanie zdarzeń** Aby można było subskrybować zdarzenie, należy utworzyć procedurę obsługi i delegata zdarzeń. Następnie użyj <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> właściwości, aby subskrybować zdarzenie. Aby uzyskać więcej informacji, zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Cofanie zmian** Po cofnięciu transakcji są zgłaszane zdarzenia, ale nie są stosowane reguły. Jeśli reguła zmieni wartość i cofnięto tę zmianę, wartość zostanie zresetowana do oryginalnej wartości podczas akcji Cofnij. Gdy zdarzenie jest zgłaszane, należy ręcznie zmienić wartość z powrotem na oryginalną wartość. Aby dowiedzieć się więcej na temat transakcji i cofania, zobacz [How to: use Transactions to updateing model](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Przekazywanie argumentów zdarzeń do zasad i zdarzeń** Oba zdarzenia i reguły są przesyłane `EventArgs` parametrem zawierającym informacje o sposobie zmiany modelu.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Przechwytywanie kliknięć w kształcie lub elemencie Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Pisanie kodu w celu dostosowania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)