---
title: 'Diagramy aktywności UML: Odwołanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2dcfa13a7ac97a5afd3e315fcef13a706c5f4bce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810471"
---
# <a name="uml-activity-diagrams-reference"></a>Diagramy aktywności UML: Odnośnik
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Diagram aktywności* przedstawia proces biznesowy lub procesu oprogramowania jako przepływ pracy za pomocą szeregu akcji. Osoby, składniki oprogramowania lub komputerów, można wykonywać te akcje.  
  
 Diagram aktywności służy do opisywania procesów kilka typów, takich jak następujące przykłady:  
  
- Proces biznesowy lub przepływ pracy między użytkownikami i systemu. Aby uzyskać więcej informacji, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
- Kroki wykonywane w przypadku użycia. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: wskazówki dotyczące](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Protokół oprogramowania, oznacza to, że dozwolone sekwencje interakcje pomiędzy składnikami.  
  
- Algorytm oprogramowania.  
  
  W tym temacie opisano elementy, które można użyć w diagramach aktywności. Aby uzyskać bardziej szczegółowe uzyskać informacje na temat działania rysowania diagramów zobacz [diagramy aktywności UML: wskazówki dotyczące](../modeling/uml-activity-diagrams-guidelines.md). Aby utworzyć diagram aktywności UML na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**. Aby uzyskać więcej informacji na temat narysować diagramy modelowania ogólnie rzecz biorąc, zobacz [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-activity-diagrams"></a>Odczytywanie diagramów aktywności  
 W tabelach w poniższych sekcjach opisano elementy, które można używać na diagramie aktywności i ich właściwości głównego. Aby uzyskać pełną listę właściwości elementów, zobacz [właściwości elementów w diagramach aktywności UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).  
  
 Akcje i inne elementy, które są wyświetlane na diagramie aktywności stanowią jedno działanie. Możesz zobaczyć tę aktywność w Eksploratorze modelu UML. Jest on tworzony podczas dodawania pierwszego elementu na diagram.  
  
 Do odczytu na diagramie, załóżmy, że tokenu lub wątek kontroli, przekazuje wzdłuż łączniki z jedną akcję do następnego.  
  
### <a name="simple-control-flows"></a>Prosty formant przepływów  
 Możesz wyświetlić sekwencję akcji przy użyciu gałęzi i pętli. Aby uzyskać więcej informacji o sposobie używania elementy opisane w tym miejscu, w sekcji opisujący przepływ sterowania tematu [diagramy aktywności UML: wskazówki dotyczące](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Prosty przepływ sterowania](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")  
  
||||  
|-|-|-|  
|**Kształt**|**Element**|**Opis i właściwości głównego**|  
|1|**Akcja**|Krok w działaniu, w których użytkowników lub oprogramowania wykonać jakieś zadanie.<br /><br /> Akcję można uruchomić, gdy token jest już dostępna na wszystkich przychodzących przepływów. Po jej zakończeniu, wysyłane są tokeny na wszystkie wychodzące przepływy.<br /><br /> -   **Treść** -Określa akcję szczegółowo.<br />-   **Język** — język wyrażeń w treści.<br />-   **Lokalne warunków końcowych** — ograniczenia, które muszą zostać spełnione, po zakończeniu wykonywania. Celem osiągnięte przez akcję.<br />-   **Warunki wstępne lokalnego** — ograniczenia, które muszą zostać spełnione przed rozpoczęciem wykonywania.|  
|2|**Przepływ sterowania**|Łącznik, który przedstawia przepływ sterowania między akcjami. Interpretowanie diagramu, Wyobraź sobie token przepływy do następnego w ramach jednej akcji.<br /><br /> Aby utworzyć przepływ sterowania, użyj **łącznika** narzędzia.|  
|3|**Węzeł początkowy**|Wskazuje pierwszej akcji lub akcji w ramach działania. Po uruchomieniu działania token przepływów z poziomu początkowej węzła.|  
|4|**Ostatni węzeł działania**|Zakończenie działania. Po odebraniu tokenu kończy działanie.|  
|5|**Węzeł decyzji**|Gałąź warunkowa w przepływie. Ma jedne dane wejściowe i wyjściowe dwóch lub więcej. Przychodzący token wynika, na co najmniej jeden dane wyjściowe.|  
|6|**Ochrona**|Warunek, który określa, czy token może przepływać wzdłuż łącznika. Najczęściej używane na wychodzące przepływy węzła decyzji.<br /><br /> Aby ustawić zabezpieczenia, kliknij prawym przyciskiem myszy przepływu, kliknij przycisk **właściwości** , a następnie ustaw **je przed nieprzewidzianymi** właściwości.|  
|7|**Scal węzła**|Wymagane do scalenia przepływów, które zostały podziału z węzłem decyzji. Ma dwa lub więcej danych wejściowych i jeden danych wyjściowych. Wynika tokenu na wszystkie dane wejściowe dla danych wyjściowych.|  
|8|**Komentarz**|Zawiera dodatkowe informacje na temat elementów, z którymi jest połączony.|  
|9|**Wywołaj akcję zachowania**|Akcja, która jest zdefiniowana w bardziej szczegółowo w innym diagramie aktywności.<br /><br /> -   **IsSynchronous** — Jeśli to ustawienie ma wartość true, akcja czeka, aż do zakończenia działania.<br />-   **Zachowanie** -wywołane działanie.|  
|(niewyświetlany)|**Wywołanie operacji**|Akcja wywołująca operację na wystąpienie klasy.|  
||**Aktywność**|Przepływ pracy, który jest przedstawiony za diagramie aktywności. Aby wyświetlić właściwości działania, należy wybrać w **Eksploratora modelu UML**.<br /><br /> -   **Jest tylko do odczytu** — Jeśli to ustawienie ma wartość true, działanie nie należy zmieniać stan każdego obiektu.<br />-   **Wykonanie jednej** — w przypadku wartości true, co najwyżej jednego wykonania tego diagramu w danym momencie.|  
||**Diagram aktywności UML**|Diagram, który wyświetla działania. Aby wyświetlić jego właściwości, kliknij pustą część diagramu. **Uwaga:** nazw Diagram aktywności, plik, który zawiera diagram i działania wyświetlane przez diagram można wszystkie się różnić.|  
  
### <a name="concurrent-flows"></a>Przepływy współbieżne  
 Możesz opisać sekwencji akcji, które są wykonywane w tym samym czasie. Aby uzyskać więcej informacji zobacz rysunek przepływy współbieżne.  
  
 ![Diagram działania pokazujący przepływ współbieżny](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")  
  
||||  
|-|-|-|  
|**Kształt**|**Element**|**Opis**|  
|11|**Węzeł rozwidlenia repozytorium**|Dzieli pojedynczego przepływu na przepływy współbieżne. Każdy przychodzący token tworzy token w każdym łączniku wychodzących.|  
|12|**Dołącz do węzła**|Łączy przepływy współbieżne do pojedynczego przepływu. Jeśli każdy przychodzący przepływ ma tokenu oczekiwania, token jest generowany dla danych wyjściowych.|  
|13|**Wysłanie sygnału**|Akcja, która wysyła wiadomości lub sygnał do kolejnego działania lub współbieżnych wątków w ramach tego samego działania. Typ i treść wiadomości jest implikowane według tytułu akcji albo określony w dodatkowe uwagi.<br /><br /> Akcję można wysłać danych sygnał, który może być przekazywany do akcji w usłudze flow obiektu lub wprowadzania numeru pin (16).|  
|14|**Zaakceptuj akcję zdarzenia**|Akcja, która czeka na komunikat lub sygnał, zanim będzie można kontynuować działania. Typ komunikatu, które mogą odbierać akcji jest implikowana przez tytuł lub określone dodatkowe uwagi.<br /><br /> Jeśli akcja nie przychodzącego przepływu sterowania, tworzy token po każdym odebraniu komunikatu.<br /><br /> Działania mogą odbierać dane w sygnał, który mogą być przekazany obiekt przepływ danych wyjściowych lub numer PIN (17).<br /><br /> -   **IsUnmarshall** — Jeśli to ustawienie ma wartość true, może istnieć kilka PinY wyjściowe wpisane, a dane są unmarshalled na nich. Jeśli wartość to false, wszystkie dane jest wyświetlany na jeden kod pin.|  
  
###  <a name="DataFlow"></a> Przepływ danych  
 Możesz opisać przepływu danych w ramach jednej akcji. Aby uzyskać więcej informacji na temat elementów używanych w tej sekcji zamieszczono Rysowanie diagramu aktywności sekcji rysowania dane przepływają w temacie wytycznych.  
  
 ![Diagram działania pokazujący przepływ danych](../modeling/media/uml-actovdata.png "UML_ActOvData")  
  
||||  
|-|-|-|  
|**Kształt**|**Element**|**Opis**|  
|15|**Węzeł obiektu**|Reprezentuje dane, które są przekazywane wraz z przepływu.<br /><br /> -   **Kolejność** — w jaki sposób są przechowywane w wielu tokenów.<br />-   **Wybór** -wywołuje proces, który może być zdefiniowany w innym diagramie, który filtruje dane.<br />-   **Górna granica** -0 wskazuje, że dane muszą przekazują bezpośrednio przepływ; \* wskazuje, że dane mogą być przechowywane w przepływie.<br />-   **Typ** — typ obiektów, przechowywane i przekazywane.|  
|16|**Wejściowy kod Pin**|Reprezentuje dane, które mogą odbierać akcji, podczas wykonywania.<br /><br /> -   **Typ** — typ obiektów przekazywane.|  
|17|**Dane wyjściowe numeru Pin**|Reprezentuje dane, które tworzy akcję, podczas wykonywania.<br /><br /> -   **Typ** — typ obiektów przekazywane.|  
|18|**Węzeł parametru działania**|Węzeł obiektu za pomocą którego dane mogą być odbierane lub generowane przez działanie.<br /><br /> Używany podczas działania reprezentowanego przez diagram jest wywoływana z innego działania lub na diagramie przedstawiono operacji lub funkcji.<br /><br /> -   **Typ** — typ obiektów przekazywane.|  
|(niewyświetlany)|**Obiekt przepływu**|Łącznik, który przedstawia przepływ danych między działaniami i węzły obiektów.<br /><br /> Aby utworzyć przepływ obiektu, należy użyć **łącznika** narzędzie do łączenia danych wejściowych lub numeru pin w danych wyjściowych lub węzeł obiektu do innego elementu.<br /><br /> -   **Wybór** -wywołuje proces, który może być zdefiniowany w innym diagramie, który filtruje dane.<br />-   **Przekształcenie** -wywołuje proces, który może być zdefiniowany w innym diagramie, który przekształca dane.<br />-   **IsMulticast** — wskazuje, że może być kilka obiektów adresatów lub składniki.<br />-   **IsMultiReceive** — wskazuje, że dane wejściowe mogą być odbierane z kilka obiektów lub składniki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)



