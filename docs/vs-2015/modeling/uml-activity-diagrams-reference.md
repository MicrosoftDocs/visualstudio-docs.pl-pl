---
title: 'Diagramy aktywności UML: odwołanie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 960e9469290bca42abd252d497c2ce72e62e41a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531537"
---
# <a name="uml-activity-diagrams-reference"></a>Diagramy aktywności UML: Odnośnik
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Diagram aktywności* pokazuje proces biznesowy lub proces programowy jako przepływ pracy przez serię akcji. Te akcje mogą wykonać osoby, składniki oprogramowania lub komputery.

 Możesz użyć diagramu aktywności do opisywania procesów kilku typów, takich jak następujące przykłady:

- Proces biznesowy lub przepływ pracy między użytkownikami i systemem. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

- Kroki wykonywane w przypadku użycia. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md).

- Protokół programowy, czyli dozwolone sekwencje interakcji między składnikami.

- Algorytm oprogramowania.

  W tym temacie opisano elementy, których można użyć na diagramach aktywności. Aby uzyskać bardziej szczegółowe informacje na temat diagramów aktywności rysowania, zobacz [diagramy aktywności UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md). Aby utworzyć diagram aktywności UML, w menu **Architektura** kliknij **Nowy UML lub diagram warstwowy**. Aby uzyskać więcej informacji na temat ogólnego rysowania diagramów modelowania, zobacz [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-activity-diagrams"></a>Odczytywanie diagramów aktywności
 W tabelach w poniższych sekcjach opisano elementy, których można użyć na diagramie aktywności i ich właściwości główne. Aby uzyskać pełną listę właściwości elementów, zobacz [właściwości elementów na diagramach aktywności UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).

 Akcje i inne elementy, które pojawiają się w diagramie aktywności, tworzą jedno działanie. Działanie można zobaczyć w Eksploratorze modelu UML. Jest tworzony po dodaniu pierwszego elementu do diagramu.

 Aby odczytywać diagram, Załóżmy, że token lub wątek kontrolki są przekazywane do łączników z jednej akcji do następnego.

### <a name="simple-control-flows"></a>Proste przepływy sterowania
 Można wyświetlić sekwencję akcji z gałęziami i pętlami. Więcej informacji o sposobach używania elementów opisanych w tym miejscu znajduje się w sekcji opisywanie przepływu sterowania w temacie [diagramy działań UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md).

 ![Prosty przepływ sterowania](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")

|**Kształt**|**Element**|**Opis i główne właściwości**|
|-|-|-|
|1|**Akcja**|Krok działania, w którym użytkownicy lub oprogramowanie wykonują pewne zadania.<br /><br /> Akcja może rozpocząć się, gdy token dotarł do wszystkich przepływów przychodzących. Po jego zakończeniu tokeny są wysyłane na wszystkie przepływy wychodzące.<br /><br /> -   **Treść** — określa akcję szczegółowo.<br />-   **Język** — język wyrażenia w treści.<br />-   **Lokalne warunki końcowe** — ograniczenia, które muszą być spełnione po zakończeniu wykonywania. Cel osiągnięty przez akcję.<br />-   **Lokalne warunki** wstępne — ograniczenia, które muszą zostać spełnione przed rozpoczęciem wykonywania.|
|2|**Przepływ sterowania**|Łącznik, który pokazuje przepływ sterowania między akcjami. Aby interpretować diagram, Załóżmy, że token przepływa z jednej akcji do następnego.<br /><br /> Aby utworzyć przepływ sterowania, użyj narzędzia **Łącznik** .|
|3|**Węzeł początkowy**|Wskazuje pierwszą akcję lub akcje w działaniu. Po rozpoczęciu działania token jest przepływem z węzła początkowego.|
|4|**Węzeł końcowy działania**|Koniec do działania. Po nadejściu tokenu działanie kończy się.|
|5|**Węzeł decyzyjny**|Gałąź warunkowa w przepływie. Ma jedno wejście i dwa lub więcej danych wyjściowych. W przypadku tokenu przychodzącego wystąpi tylko jeden z danych wyjściowych.|
|6|**Chroni**|Warunek określający, czy token może przepływać na łączniku. Najczęściej używane w przepływach wychodzących węzła decyzyjnego.<br /><br /> Aby ustawić ochronę, kliknij prawym przyciskiem myszy przepływ, kliknij polecenie **Właściwości** , a następnie ustaw właściwość **Guard** .|
|7|**Węzeł scalenia**|Wymagane do scalenia przepływów, które zostały podzielone z węzłem decyzyjnym. Zawiera co najmniej dwa dane wejściowe i jedno wyjście. Token na wszelkich danych wejściowych jest niezależny od danych wyjściowych.|
|8|**Komentarz**|Zawiera dodatkowe informacje o elementach, z którymi są połączone.|
|9|**Akcja zachowania wywołania**|Akcja zdefiniowana bardziej szczegółowo na innym diagramie aktywności.<br /><br /> -   **Issynchroniczne** — w przypadku wartości true akcja czeka na zakończenie działania.<br />-   **Zachowanie** — wywołano działanie.|
|(niepokazywany)|**Akcja operacji wywołania**|Akcja, która wywołuje operację w wystąpieniu klasy.|
||**Działanie**|Przepływ pracy, który jest przedstawiony przez diagram aktywności. Aby wyświetlić właściwości działania, należy wybrać je w **Eksploratorze modelu UML**.<br /><br /> -   **Jest tylko do odczytu** — w przypadku wartości true aktywność nie powinna zmieniać stanu żadnego obiektu.<br />-   **Jest pojedynczym wykonaniem** — Jeśli prawda, jednocześnie istnieje co najwyżej jedno wykonanie tego diagramu.|
||**Diagram aktywności UML**|Diagram przedstawiający działanie. Aby wyświetlić właściwości, kliknij pustą część diagramu. **Uwaga:**  Nazwy diagramu aktywności, plik, który zawiera diagram, a działanie wyświetlane przez diagram może się różnić.|

### <a name="concurrent-flows"></a>Współbieżne przepływy
 Można opisać sekwencje akcji, które są wykonywane w tym samym czasie. Aby uzyskać więcej informacji, Zobacz Rysowanie współbieżnych przepływów.

 ![Diagram aktywności pokazujący współbieżny przepływ](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")

|**Kształt**|**Element**|**Opis**|
|-|-|-|
|11|**Węzeł rozwidlenia**|Dzieli pojedynczy przepływ na współbieżne przepływy. Każdy przychodzący token tworzy token dla każdego łącznika wychodzącego.|
|12|**Węzeł sprzężenia**|Łączy współbieżne przepływy w jeden przepływ. Gdy każdy przepływ przychodzący ma token oczekujący, token jest generowany w danych wyjściowych.|
|13|**Akcja wysyłania sygnału**|Akcja, która wysyła komunikat lub sygnał do innego działania lub do współbieżnego wątku w tym samym działaniu. Typ i zawartość komunikatu są implikowane przez tytuł akcji lub określone w dodatkowych komentarzach.<br /><br /> Akcja może wysyłać dane w sygnale, które mogą być przekazane do akcji w przepływie obiektów lub wejściowym numerze PIN (16).|
|14|**Akcja akceptowania zdarzenia**|Akcja, która czeka na komunikat lub sygnał przed kontynuowaniem akcji. Typ komunikatu, które może otrzymywać akcja, jest implikowany przez tytuł lub określony w dodatkowych komentarzach.<br /><br /> Jeśli akcja nie ma przepływu sterowania przychodzącego, generuje token za każdym razem, gdy odbierze komunikat.<br /><br /> Akcja może odbierać dane w sygnale, które mogą być przekazywane do przepływu obiektów lub numeru PIN wyjściowego (17).<br /><br /> -   **IsUnmarshall** — Jeśli prawda, może istnieć kilka wpisanych kodów wyjściowych, a dane nie są przekazywane do nich. W przypadku wartości false wszystkie dane są wyświetlane na jednym numerze PIN.|

### <a name="data-flows"></a><a name="DataFlow"></a> Przepływy danych
 Można opisać przepływ danych z jednej akcji do innej. Aby uzyskać więcej informacji na temat elementów użytych w tej sekcji, zobacz sekcję rysowanie przepływów danych tematu wskazówki dotyczące rysowania diagramu aktywności.

 ![Diagram aktywności przedstawiający przepływ danych](../modeling/media/uml-actovdata.png "UML_ActOvData")

|**Kształt**|**Element**|**Opis**|
|-|-|-|
|15|**Węzeł obiektu**|Reprezentuje dane, które są przekazywane wraz z przepływem.<br /><br /> -   **Porządkowanie** — jak są przechowywane wiele tokenów.<br />-   **Wybór** — wywołuje proces, który można zdefiniować w innym diagramie, który filtruje dane.<br />-   **Górna granica** -0 wskazuje, że dane muszą być przekazywane bezpośrednio wzdłuż przepływu; \* wskazuje, że dane mogą być przechowywane w przepływie.<br />-   **Typ** — typ obiektów, które są przechowywane i przesyłane.|
|16|**Wejściowy numer PIN**|Reprezentuje dane, które akcja może otrzymać po jej wykonaniu.<br /><br /> -   **Typ** — typ przesyłanych obiektów.|
|17|**Wyjściowy numer PIN**|Reprezentuje dane, które tworzy akcja, gdy zostanie ona wykonana.<br /><br /> -   **Typ** — typ przesyłanych obiektów.|
|18|**Węzeł parametru działania**|Węzeł obiektu, za pomocą którego dane mogą być odbierane lub generowane przez działanie.<br /><br /> Używany, gdy działanie reprezentowane przez diagram jest wywoływane z innego działania lub gdy diagram opisuje operację lub funkcję.<br /><br /> -   **Typ** — typ przesyłanych obiektów.|
|(niepokazywany)|**Przepływ obiektów**|Łącznik, który pokazuje przepływ danych między akcjami a węzłami obiektów.<br /><br /> Aby utworzyć przepływ obiektów, użyj narzędzia **łącznika** , aby połączyć numer PIN wejścia lub wyjścia lub węzeł obiektu z innym elementem.<br /><br /> -   **Wybór** — wywołuje proces, który można zdefiniować w innym diagramie, który filtruje dane.<br />-   **Transformacja** — wywołuje proces, który można zdefiniować w innym diagramie, który przekształca dane.<br />-   **IsMulticast** — wskazuje, że może istnieć kilka obiektów lub elementów odbiorcy.<br />-   **IsMultiReceive** — wskazuje, że dane wejściowe mogą być odbierane z kilku obiektów lub składników.|

## <a name="see-also"></a>Zobacz też
 [Edycja modeli UML i](../modeling/edit-uml-models-and-diagrams.md) diagramów [diagramów aktywności UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md)
