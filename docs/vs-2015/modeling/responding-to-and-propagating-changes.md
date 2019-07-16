---
title: Odpowiadanie na zmiany i propagowanie zmian | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9838e934421e619c85f348052fbe589288391c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158842"
---
# <a name="responding-to-and-propagating-changes"></a>Odpowiadanie na zmiany i propagowanie zmian
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy element zostanie utworzony, usunięty lub zaktualizowany, można napisać kod, który propaguje zmiany z innymi częściami modelu lub zasobów zewnętrznych, takich jak pliki, bazy danych lub innych składników.  
  
## <a name="in-this-section"></a>W tej sekcji  
 Program narzędziowy należy wziąć pod uwagę te techniki w następującej kolejności:  
  
|Techniki|Scenariusze|Więcej informacji|  
|---------------|---------------|--------------------------|  
|Zdefiniuj właściwość domeny obliczeniowe.|Właściwość domeny, którego wartość jest obliczana na podstawie innych właściwości w modelu. Na przykład cena, która jest sumą ceny powiązanych elementów.|[Obliczone i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md)|  
|Zdefiniuj właściwość domeny magazynu niestandardowego.|Właściwość domeny przechowywane w innych częściach modelu lub zewnętrznie. Na przykład można przeanalizować wyrażenia ciągu w drzewie w modelu.|[Obliczone i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md)|  
|Obsługa zmian, takich jak OnValueChanging i OnDeleting zastąpienia|Synchronizuj różne elementy i Synchronizuj wartości zewnętrznej za pomocą modelu.<br /><br /> Ograniczenie wartości do zdefiniowanego zakresu.<br /><br /> Wywoływana bezpośrednio przed i po wartości właściwości i inne zmiany. Możesz zakończyć zmian przez wyrzucanie wyjątku.|[Obsługa zmian wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md)|  
|reguły|Można zdefiniować reguły, które oczekują w kolejce do wykonania bezpośrednio przed zakończeniem transakcji, w którym miało miejsce zmiany. Nie są wykonywane na cofania i ponawiania. Pozwala to zachować synchronizację z innego jednej strony Sklepu.|[Reguły propagujące zmiany w modelu](../modeling/rules-propagate-changes-within-the-model.md)|  
|Zdarzenia Store|Magazyn modelowania zawiera powiadomienia o zdarzeniach, takie jak dodawanie lub usuwanie elementu lub łączenie lub zmiana wartości właściwości. Zdarzenie jest również wykonywane na operacje Cofnij i ponów. Użyj magazynu zdarzeń, aby zaktualizować wartości, które nie znajdują się w magazynie.|[Programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|Zdarzenia platformy .NET|Kształty mają obsługi zdarzeń, które odpowiadanie na kliknięcia myszy i innych gestów. Musisz zarejestrować te zdarzenia, dla każdego obiektu. Rejestracja odbywa się zwykle w zastąpieniu obiektu InitializeInstanceResources i należy ją odtworzyć dla każdego elementu.<br /><br /> Te zdarzenia występują zwykle poza transakcją.|[Instrukcje: Przechwytywanie kliknięć w kształcie lub elemencie Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|Granice reguły|Reguła granice jest używana specjalnie w celu ograniczenia granice kształtu.|[BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|Wybór zasad|Reguły wyboru w szczególności ograniczenie, co użytkownik może wybrać.|[Instrukcje: Ograniczanie bieżącego wyboru i uzyskiwanie dostępu do niego](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Wskazuje stany elementów modelu przy użyciu funkcji kształtów i łączników, takich jak w tle, strzałek, kolor i szerokości linii i stylu.|[Aktualizowanie kształtów i łączników, aby odzwierciedlały model](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**Porównanie reguł i zdarzenia Store**  
 Zgłaszających zmiany, reguł i zdarzenia są uruchamiane po wystąpieniu zmian w modelu.  
  
 Reguły są zazwyczaj stosowane w transakcji end zostało zmienione, a zdarzenia są stosowane po zatwierdzeniu zmian w ramach transakcji.  
  
 Używać zdarzeń store można zsynchronizować modelu obiektów poza Store i reguł do zapewniania spójności w ramach Store.  
  
- **Tworzenie niestandardowych reguł** Tworzenie niestandardowej reguły jako pochodne klasy abstrakcyjnej reguły. Musi również powiadomić framework o reguły niestandardowej. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
- **Subskrybowanie zdarzeń** przed mogą subskrybować zdarzenie, utworzyć program obsługi zdarzeń i delegata. Następnie użyj <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>właściwości do subskrybowania zdarzenia. Aby uzyskać więcej informacji, zobacz [obsługi propagowanie zmian poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
- **Cofanie zmian** cofnięcie transakcji, zdarzenia są wywoływane, ale nie są stosowane zasady. Jeśli reguła zmienia wartość i Cofnij tę zmianę, wartość jest resetowany do oryginalnej wartości podczas działania cofania. Gdy zdarzenie jest wywoływane, możesz ręcznie zmienić wartość do oryginalnej wartości. Aby dowiedzieć się więcej na temat transactons i cofania, zobacz [jak: Użycie transakcji do aktualizacji modelu](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
- **Przekazywanie argumentów zdarzeń do zasad i zdarzenia** obu zdarzeń, a zasady są przekazywane `EventArgs` parametr, który zawiera informacje o tym, jak model został zmieniony.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Przechwytywanie kliknięć w kształcie lub elemencie Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
