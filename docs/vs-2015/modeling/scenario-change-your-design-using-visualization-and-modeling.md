---
title: 'Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4dface8e157e44aa09b271446dba68b2779d0a6b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745768"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upewnij się, że oprogramowanie systemu spełnia wymagania użytkowników przy użyciu wizualizacji i modelowania narzędzi w programie Visual Studio. Użyj narzędzi takich jak diagramy modelowania UML (Unified Language), map kodu, diagramów warstwowych i diagramów klas do:  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje każde narzędzie, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
- Wyjaśnij procesy biznesowe i wymagania użytkowników.  
  
- Wizualizacja i eksploracja istniejącego kodu.  
  
- Opisz zmiany w istniejącym systemie.  
  
- Sprawdź, czy system spełnia wymagania.  
  
- Utrzymuj spójność kodu z projektem.  
  
  W tym instruktażu:  
  
- W tym artykule opisano te narzędzia zyska projektem oprogramowania.  
  
- Pokazano, jak może użyć tych narzędzi, niezależnie od tego, daną metodę rozwoju w przykładowym scenariuszu.  
  
  Aby dowiedzieć się więcej o tych narzędziach i scenariuszach, które wspierają, zobacz:  
  
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)  
  
- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)  
  
- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)  
  
##  <a name="ScenarioOverview"></a> Omówienie scenariusza  
 W tym scenariuszu opisano odcinki z cyklu rozwoju oprogramowania dwóch fikcyjnych spółek: Dinner Now i Lucerne Publishing. Dinner Now zapewnia terenie Seattle usługę dostarczania posiłków opartą na sieci Web. Klienci mogą posiłki i zapłacić za w witrynie internetowej firmy Dinner Now. Zamówienia są następnie wysyłane do odpowiedniej lokalnej restauracji do dostarczenia. Lucerna Publishing, firma w Nowym Jorku, prowadzi kilka działalności zarówno off, jak i w sieci Web. Na przykład uruchamiają witryny sieci Web których klienci mogą ogłaszać opinie o restauracjach.  
  
 Lucerna niedawno nabyła obiad teraz i chce wprowadzić następujące zmiany:  
  
- Integrowanie ich witryn sieci Web przez dodanie możliwości przeglądu restauracji na obiad teraz.  
  
- Zamień na systemu płatności Dinner Now system firmy Lucerne.  
  
- Rozwinięcie węzła usługi Dinner Now całego regionu.  
  
  Dinner Now używa SCRUM i eXtreme Programming. Mają bardzo wysokie pokrycie testu i bardzo mało nieobsługiwanego kodu. Firma minimalizuje ryzyko tworząc małe, ale działające wersje systemu, a następnie stopniowo dodając nowe funkcje. Firma opracowuje swój kod w krótkich i częstych iteracjach. Pozwala to wykorzystać pewne zmiany, często refaktoryzować kod i unikać "na początku związanych z dużymi projektami".  
  
  Lucerna zachowuje zdecydowanie większą i bardzien złożoną kolekcję systemów, z których niektóre mają więcej niż 40 lat. Są one wyjątkową ostrożność podczas wprowadzania zmian z powodu złożoności i zakresu starszego kodu. Stosują bardziej rygorystyczny proces tworzenia oprogramowania, preferując projektowanie szczegółowych rozwiązań i dokumentowanie projektu oraz zmian, które występują podczas pracy.  
  
  Oba zespoły korzystają z diagramów modelowania w programie Visual Studio, aby ułatwić opracowanie systemów spełniających potrzeby użytkowników. Używają serwera Team Foundation Server oraz innymi narzędziami, aby pomóc im planowania, organizowania i zarządzania pracą.  
  
  Aby uzyskać więcej informacji na temat serwera Team Foundation Server zobacz:  
  
- [Planowanie i śledzenie pracy](#PlanningTracking)  
  
- [Testowanie, sprawdzanie poprawności i ewidencjonowanie kodu zaktualizowanego](#TestValidateCheckInCode)  
  
##  <a name="ModelingDiagramsTools"></a> Role architektury i diagramów modelowania w tworzeniu oprogramowania  
 W poniższej tabeli opisano role, które mogą pełnić te narzędzia wielu i różnych etapach cyklu życia tworzenia oprogramowania:  
  
||**Modelowanie wymagań użytkowników**|**Modelowanie procesów biznesowych**|**Architektura i projektowanie**|**Kod — Wizualizacja i eksploracja**|**Weryfikacja**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Diagram przypadków użycia (UML)|√|√|||√|  
|Diagram aktywności (UML)|√|√|√||√|  
|Diagram klas (UML)|√|√|√||√|  
|Diagram składników (UML)|√|√|√||√|  
|Diagram sekwencji (UML)|√|√|√||√|  
|Diagram języka specyficznego dla domeny (DSL)|√|√|√|||  
|Diagram warstwy, sprawdzenie poprawności warstwy|||√|√|√|  
|Mapy kodu|||√|√|√|  
|Projektant klasy (oparty na kodzie)||||√||  
  
 Aby narysować diagramy UML i diagramy warstwowe, należy utworzyć projekt modelowania jako część nowego lub istniejącego rozwiązania. Te diagramy należy utworzyć w projekcie modelowania. Elementy na diagramach UML są częścią wspólnego wzoru a diagramy UML są widokami tego modelu. Elementy na diagramach znajdują się w projekcie modelowania, ale nie są one przechowywane we wspólnym modelu. Mapy kodu i diagramy klas .NET utworzone na podstawie kodu istnieje poza projektem modelowania.  
  
 Zobacz:  
  
- [Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md)  
  
- [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)  
  
- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  
  
  W celu pokazania alternatywnych widoków architektury, można ponownie użyć niektóre elementy z tego samego modelu na wielu lub w różnych diagramach. Na przykład użytkownik można przeciągnąć składnik do innego diagramu składników lub diagramu sekwencji, aby mógł działać jako Aktor. Zobacz [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
  Oba zespoły korzystają również sprawdzanie poprawności warstwy, aby upewnić się, że opracowywany kod pozostaje zgodny z projektem.  
  
  Zobacz:  
  
- [Zachowywanie kodu zgodnie z projektem](#ValidatingCode)  
  
- [Opisz logiczną architekturę: diagramy warstw](#DescribeLayers)  
  
- [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)  
  
  > [!NOTE]
  >  Niektóre wersje programu Visual Studio obsługuje sprawdzanie poprawności warstwy i wersje tylko do odczytu mapy kodu i diagramów UML do wizualizacji i modelowania. Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="UnderstandingCommunicating"></a> Opis i przekazywaniu informacji o systemie  
 Nie ma żadnej zalecanej kolejności przy użyciu programu Visual Studio, modelowanie diagramów, aby można było ich używać stosownie do potrzeb lub podejścia. Zwykle zespoły wracają do swoich modeli wielokrotnie i często w całym projekcie. Każdy diagram oferuje szczególne zalety, aby ułatwić zrozumienie, opisać i zakomunikować różne aspekty systemu w fazie projektowania.  
  
 Dinner Now i Lucerne komunikują się ze sobą i z udziałowcami projektu za pomocą diagramów oraz ich wspólnego języka. Na przykład Dinner Now używa diagramów do wykonywania następujących zadań:  
  
- Wizualizacja istniejącego kodu.  
  
- Komunikować się z usługą Lucerne o nowych lub zaktualizowanych przypadków użycia.  
  
- Zidentyfikuj zmiany, które są wymagane do obsługi nowych lub zaktualizowanych przypadków użycia.  
  
  Lucerna używa diagramów do wykonywania następujących zadań:  
  
- Więcej informacji na temat procesu biznesowego obiad teraz.  
  
- Omówienie konstrukcji systemu.  
  
- Komunikuj się z firmą Dinner Now w kwestii nowych lub uaktualnionych wymagań użytkownika.  
  
- Dokumentowanie aktualizacji systemu.  
  
  Diagramy są zintegrowane z programem Team Foundation Server, dzięki czemu zespoły mogą planowanie, zarządzanie i łatwiej śledzić ich pracę. Na przykład używają modeli do identyfikowania przypadków testowych i zadań programistycznych i do szacowania pracy. Lucerna łaczy Team Foundation Server elementy robocze z elementów modelu tak aby monitorować postęp i upewnij się, że system spełnia wymagania użytkowników. Na przykład łączą przypadki użycia z elementami roboczymi przypadków testowych można zobaczyć, że przypadki użycia są spełnione, gdy kod przechodzi wszystkie testy.  
  
  Zanim zespoły zaewidencjonują zmiany, sprawdzają poprawność kodu w stosunku do testów i projektu uruchamiając kompilacje, które obejmują sprawdzanie poprawności warstwy i zautomatyzowane testy. Dzięki temu, upewnij się, że zaktualizowany kod nie są w konflikcie z projektowaniem i przerwać wcześniej działające funkcje.  
  
  Zobacz:  
  
- [Opis roli systemu w procesie biznesowym](#UnderstandingBPMandSystemDesign)  
  
- [Opisujący nowych lub uaktualnionych wymagań użytkownika](#DescribingURM)  
  
- [Tworzenie testów z modeli](#CreatingTests)  
  
- [Identyfikowanie zmian w istniejącym systemie](#DeterminingChanges)  
  
- [Zachowywanie kodu zgodnie z projektem](#ValidatingCode)  
  
- [Ogólne porady dotyczące tworzenia i używania modeli](#GeneralTips)  
  
- [Planowanie i śledzenie pracy](#PlanningTracking)  
  
- [Testowanie, sprawdzanie poprawności i ewidencjonowanie kodu zaktualizowanego](#TestValidateCheckInCode)  
  
###  <a name="UnderstandingBPMandSystemDesign"></a> Opis roli systemu w procesie biznesowym  
 Lucerna chce dowiedzieć się więcej na temat procesu biznesowego obiad teraz. Tworzą następujące diagramy w celu jasnego przedstawienia jej z firmą Dinner Now łatwiej:  
  
|**Diagram**|**W tym artykule opisano**|  
|-----------------|-------------------|  
|*Diagram przypadków użycia (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|— Działania, które obsługuje system firmy Dinner Now<br />Osoby i systemy zewnętrzne, które wykonują działania<br />-Główne składniki systemu obsługujące każde działanie<br />Części procesu biznesowego, które są poza zakresem bieżącego systemu, na przykład dostawy żywności|  
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|Przepływ kroków, które występują, gdy klient tworzy zamówienie|  
|*Diagram klas (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|Podmioty gospodarcze i warunki, które są używane w dyskusji oraz relacje między tymi jednostkami. Na przykład zamówienie i element Menu są częścią słownictwa w tym scenariuszu.|  
  
 Na przykład Lucerne tworzy Poniższy diagram przypadków użycia, aby zrozumieć zadania, które są wykonywane w witrynie internetowej firmy Dinner Now i kto je wykonuje:  
  
 ![Diagram przypadków użycia UML](../modeling/media/uml-usecase.png "UML_UseCase")  
  
 **Diagram przypadków użycia UML**  
  
 Poniższy diagram aktywności opisuje przepływ kroków, gdy klient tworzy zamówienie witryny firmy Dinner Now w sieci Web. W tej wersji elementy komentarza określenie role i tworzą linie *torów*, które organizują etapy poprzez role:  
  
 ![Diagram aktywności UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")  
  
 **Diagram aktywności UML**  
  
 Następujący diagram klas opisuje jednostki, które uczestniczą w procesie przetwarzania zamówień:  
  
 ![Diagram klas UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")  
  
 **Diagram klas UML**  
  
###  <a name="DescribingURM"></a> Opisujący nowych lub uaktualnionych wymagań użytkownika  
 Lucerna chce, aby dodać funkcje w systemie obiad teraz tak, aby klienci mogą odczytywać opinie i dodawać opinie o restauracjach. One aktualizuje następujące diagramy, czemu może opisać i omówić ten nowy wymóg z firmą Dinner Now:  
  
|**Diagram**|**W tym artykule opisano**|  
|-----------------|-------------------|  
|*Diagram przypadków użycia (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|Nowy przypadek użycia dla "Napisz recenzję restauracji"|  
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|Kroki, które występują, gdy klient chce napisać recenzję restauracji|  
|*Diagram klas (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|Dane, które są wymagane do przechowywania przeglądu|  
  
 Na przykład poniższy diagram przypadków użycia zawiera nowy przypadek użycia "Napisz recenzję", aby przedstawić nowe wymaganie. Jest wyróżniany kolorem pomarańczowym na diagramie w celu łatwiejszej identyfikacji:  
  
 ![Diagram przypadków użycia UML](../modeling/media/uml-writerev.png "UML_WriteRev")  
  
 **Diagram przypadków użycia UML**  
  
 Poniższy diagram aktywności zawiera nowe elementy w kolorze pomarańczowym i opisuje przepływ kroków w nowy przypadek użycia:  
  
 ![Diagram aktywności UML](../modeling/media/uml-writereview.png "UML_WriteReview")  
  
 **Diagram aktywności UML**  
  
 Poniższy diagram klas zawiera nową klasę Review i jej relacje z innymi klasami, aby zespoły mogły omawiać jej szczegóły. Zwróć uwagę, że klient i restauracja mogą mieć wiele opinii:  
  
 ![Diagram klas UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")  
  
 **Diagram klas UML**  
  
###  <a name="CreatingTests"></a> Tworzenie testów z modeli  
 Oba zespoły zgadzają się, że powinni pełny zestaw testów systemu i jego składników, zanim wprowadzą jakiekolwiek zmiany. Lucerna ma wyspecjalizowany zespół wykonujący system i testowanie poziomu składnika. Ich ponowne użycie testy utworzone przez firmy Dinner Now i im strukturę za pomocą diagramów UML:  
  
- Każdy przypadek użycia jest reprezentowany przez jeden lub wiele testów. Elementy na diagramie przypadków użycia łączą się z przypadkiem testowym z elementami roboczymi na serwerze Team Foundation Server.  
  
- Każdy przepływ na diagramie aktywności lub diagramu sekwencji poziom systemu jest połączony z co najmniej jedno z badań. Zespół testowy systematycznie sprawdza, czy przetestować wszystkie możliwe ścieżki, za pomocą diagramu aktywności.  
  
- Terminy używane do opisu testów są oparte na warunkach określonych przez diagramy przypadków, klasa i działalności użycia.  
  
  Zmieniają się wymagania diagramy są aktualizowane w celu odzwierciedlenia tych zmian, testy również są aktualizowane. Wymóg jest uważany za spełniony tylko wtedy, gdy testy zostały zakończone pomyślnie. Gdy jest to możliwe lub praktyczne, badania są zdefiniowane i oparte na diagramach UML przed rozpoczęciem implementacji.  
  
  Zobacz:  
  
- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)  
  
- [Weryfikacja modelu UML](../modeling/validate-your-uml-model.md)  
  
###  <a name="DeterminingChanges"></a> Identyfikowanie zmian w istniejącym systemie  
 Dinner Now musi oszacować koszty realizacji nowego wymagania. Zależy to częściowo ile ta zmiana wpłynie na inne części systemu. Aby pomóc im to zrozumieć, jeden z deweloperów Dinner Now tworzy te mapy i diagramy z istniejącego kodu:  
  
|**Mapa lub diagramu**|**Pokazuje**|  
|------------------------|---------------|  
|*Mapy kodu*<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Przeglądanie i rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Zależności i inne relacje w kodzie.<br /><br /> Na przykład Dinner Now może rozpocząć od przejrzenia mapy kodu zestawu omówienie zestawów i ich zależności. Może przechodzić do mapy do zbadania przestrzeni nazw i klas w tych zestawach.<br /><br /> Dinner Now, można również utworzyć mapy na zbadanie szczególnych obszarów i innych rodzajów relacji w kodzie. Używają Eksploratora rozwiązań, aby znaleźć i wybrać obszary i relacje, które ich interesują.|  
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [porady: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie|  
  
 Na przykład deweloper tworzy mapę kodu. Dostosowuje jego zakres, aby skupić się na obszarach, których dotyczy nowy scenariusz. Te obszary zaznaczone i wyróżnione na mapie:  
  
 ![Wykres zależności Namespace](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")  
  
 **Mapy kodu Namespace**  
  
 Deweloper rozwija wybrane obszary nazw, aby zobaczyć ich klasy, metody i relacje:  
  
 ![Wykres zależności przestrzeni nazw rozwiniętej](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")  
  
 **Rozwinięty obszar nazw mapy kodu z widoczny aż linki międzygrupowe**  
  
 Deweloper bada kod, aby znaleźć dotyczy klasy i metody. Aby zobaczyć skutki każdej zmiany, jak wprowadzisz je, ponowne generowanie mapy kodu po każdej zmianie. Zobacz [tworzenie wizualizacji kodu](../modeling/visualize-code.md).  
  
 Aby opisać zmiany dotyczące innych części systemu, takie jak składniki lub interakcje, zespół może narysować je na tablicach. Dzięki temu szczegółowe informacje mogą być przechwytywane, zarządzane i rozpoznawane przez oba zespoły może również narysować następujące diagramy w programie Visual Studio:  
  
|**Diagramy**|**W tym artykule opisano**|  
|------------------|-------------------|  
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|Przepływ kroków, które występują, gdy system zauważa, że klient składa zamówienie z restauracji ponownie monitowania klienta o napisanie recenzji.|  
|*Diagram klas (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|Logiczne klays i ich wzajemne relacje. Na przykład dodaje się nową klasę do opisania **przeglądu** i jej relacji z innymi jednostkami, takich jak **restauracji**, **Menu**, i **klienta**.<br /><br /> Aby skojarzyć opinie z klientem, system musi przechowywać szczegóły klienta. Diagram klas UML może pomóc wyjaśnić te szczegóły.|  
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [porady: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie.|  
|*Diagram składników (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)|Części wysokiego poziomu systemu, takie jak witryna firmy Dinner Now w sieci Web oraz ich interfejsów. Niniejsze interfejsy określają, jak składniki wzajemnej interakcji za pośrednictwem metody lub usługi, które zapewniają i wykorzystują.|  
|*Diagram sekwencji (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|Sekwencja interakcji między wystąpieniami.|  
  
 Na przykład poniższy diagram składników zawiera nowy składnik, który jest częścią składnika witryny firmy Dinner Now w sieci Web. Składnik ReviewProcessing obsługuje funkcje tworzenia przeglądów i pojawia się wyróżniony kolorem pomarańczowym:  
  
 ![Diagram składników UML](../modeling/media/uml-internal.png "UML_Internal")  
  
 **Diagram składników UML**  
  
 Na poniższym diagramie sekwencji przedstawiono sekwencję wzajemnych oddziaływań zachodzących, gdy obiad teraz witryny sieci Web sprawdza, czy klient ma uporządkowane z restauracji przed. Jeśli to PRAWDA, prosi klienta o utworzenie recenzji, która jest wysyłana do restauracji i publikowane na witrynie sieci Web:  
  
 ![Diagram sekwencji UML](../modeling/media/uml-revsystem.png "UML_RevSystem")  
  
 **Diagram sekwencji UML**  
  
###  <a name="ValidatingCode"></a> Zachowywanie kodu zgodnie z projektem  
 Dinner Now, musisz upewnić się, że zaktualizowany kod pozostaje zgodny z projektem. Tworzy diagramy warstw, które opisują warstwy funkcji w systemie, określa dozwolone zależności między nimi i kojarzy artefakty rozwiązania z tymi warstwami.  
  
|**Diagram**|**W tym artykule opisano**|  
|-----------------|-------------------|  
|*Diagram warstwowy*<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|Logiczna architektura kodu.<br /><br /> Diagram warstwy organizuje i mapuje artefakty w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania grup abstrakcyjnych nazywanych *warstwy*. Te warstwy określają role, zadania lub funkcje, które te artefakty pełnią w systemie.<br /><br /> Diagramy warstwy są przydatne do opisywania zamierzonego projektu systemu i sprawdzenia poprawności zmian kodu w stosunku do projektu.<br /><br /> Aby utworzyć warstwy, przeciągnij elementy z Eksploratora rozwiązań, map kodu, widoku klas i przeglądarki obiektów. Aby narysować nowe warstwy, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu.<br /><br /> Aby wyświetlić istniejące zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu warstwy, a następnie kliknij przycisk **Wygeneruj zależności**. Aby określić zależności zamierzone, narysuj nowe.|  
  
 Na przykład poniższy diagram warstwowy opisuje zależności między warstwami i liczbą artefaktów, które są skojarzone z poszczególnymi warstwami:  
  
 ![Diagram warstwy system płatności zintegrowane](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagram warstwowy**  
  
 Aby upewnić się, że nie występują konflikty z projektem podczas programowania kodu, zespoły sprawdzają poprawność warstw w kompilacjach, które są uruchamiane na Team Foundation Build. Tworzą one równie niestandardowe zadanie MSBuild w celu wymagania sprawdzania poprawności warstwy w swoich operacjach ewidencjonowania. Używają raportów z kompilacji do zbierania błędów sprawdzania poprawności.  
  
 Zobacz:  
  
-   [Zdefiniuj proces kompilacji](http://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
-   [Korzystać z procesu kompilacji ewidencjonowanej warunkowo do sprawdzenia poprawności zmian](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
-   [Dostosowywanie szablonu procesu kompilacji](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
###  <a name="GeneralTips"></a> Ogólne porady dotyczące tworzenia i używania modeli  
  
- Większość diagramów składa się z węzłów, które są połączone liniami. Dla każdego typu diagramu Przybornik zawiera różne rodzaje węzłów i wierszy.  
  
   Aby otworzyć przybornik, na **widoku** menu, kliknij przycisk **przybornika**.  
  
- Aby utworzyć węzeł, przeciągnij je z przybornika do diagramu. Niektóre rodzaje węzłów muszą zostać przeciągnięte do istniejących węzłów. Na przykład na diagramie składników nowy port musi być dodany do istniejącego składnika.  
  
- Aby utworzyć linię lub połączenie, kliknij odpowiednie narzędzie w przyborniku, kliknij węzeł źródła, a następnie kliknij węzeł docelowy. Niektóre linie mogą być tworzone tylko między pewnymi rodzajami węzłów. Gdy przesuniesz wskaźnik nad możliwe źródło lub docelowej kursor wskazuje, czy można utworzyć połączenie.  
  
- Podczas tworzenia elementów na diagramach UML, można to również dodawane do wspólnego modelu. Diagramy UML w projekcie modelowania są widokami tego modelu. Elementy na diagramie warstwy są częścią projektu modelowania, nawet jeśli nie są one przechowywane we wspólnym modelu.  
  
   Aby wyświetlić model w **architektury** menu wskaż **Windows**, a następnie kliknij przycisk **Eksploratora modelu UML**.  
  
- W niektórych przypadkach można przeciągnąć niektóre elementy z **Eksploratora modelu UML** do diagramu UML. Niektóre elementy w ramach tego samego modelu mogą być używane w wielu lub różnych diagramach w celu wyświetlenia alternatywnych widoków architektury. Na przykład można przeciągnąć składnik do innego diagramu składników lub diagramu sekwencji do użycia jako Aktor.  
  
- Program Visual Studio obsługuje UML 2.1.2. Ten przegląd zawiera opis najważniejszych funkcji diagramów UML w tej wersji, ale istnieje wiele książek, w których omówiono UML i jego zastosowania w szczegółach.  
  
  Zobacz [tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md).  
  
###  <a name="PlanningTracking"></a> Planowanie i śledzenie pracy  
 Diagramy modelowania w usłudze Visual Studio są zintegrowane z programem Team Foundation Server, aby zaplanować, zarządzanie i łatwiej śledzić pracę. Oba zespoły używają modeli do identyfikowania przypadków testowych i zadań programistycznych i do szacowania pracy. Lucerna tworzy i łaczy Team Foundation Server elementy robocze z elementami modelu, takie jak przypadki użycia lub składniki. Pomoże im to monitorować ich postęp i śledzić ich pracę odpowiednio do wymagań użytkowników. Pomoże im to upewnić się, że ich zmiany w dalszym ciągu spełniają te wymagania.  
  
 Jako postępem prac zespoły aktualizują elementy robocze, aby odzwierciedlić czas poświęcony na ich zadań. Ponadto monitorują i raportują stan swojej pracy, korzystając z następujących funkcji serwera Team Foundation Server:  
  
- Codzienne *Raporty postępu* które pokazują, czy zostaną zakończone planowaną pracę w oczekiwanym czasie. Generują inne podobne raporty z Team Foundation Server w celu śledzenia postępu usterek.  
  
- *Arkusz iteracji* który używa programu Microsoft Excel, aby pomóc zespołowi w monitorowaniu i równoważeniu obciążenia pracą poszczególnych członków. Ten arkusz jest połączony z serwerem Team Foundation Server i dostarcza tematy do dyskusji podczas regularnie odbywanych spotkań.  
  
- A *pulpit nawigacyjny prac rozwojowych* używający Office Project do informowania zespołu o ważnych projektów.  
  
  Zobacz:  
  
- [Śledzenie pracy za pomocą programu Visual Studio Team Services lub serwera Team Foundation Server](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
- [Łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md)  
  
- [Wykresy, pulpity nawigacyjne i raporty dla programu Visual Studio ALM](http://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
- [Tworzenie zaległości i zadań za pomocą programu Project](http://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
###  <a name="TestValidateCheckInCode"></a> Testowanie, sprawdzanie poprawności i ewidencjonowanie kodu  
 Jak wykonania poszczególne zadania zespoły ewidencjonują kod do kontroli wersji serwera Team Foundation i otrzymują przypomnienia z Team Foundation Server, jeśli zapomną. Zanim Team Foundation Server zaakceptuje ewidencjonowania, zespoły uruchamiają testy jednostkowe i sprawdzanie poprawności warstwy, aby sprawdzić kod w oparciu o przypadki testowe i projekt. Używają programu Team Foundation Server do uruchamiania kompilacji, zautomatyzowanych testów jednostek i sprawdzania poprawności warstw w regularnie. Dzięki temu, upewnij się, że dany kod spełnia następujące kryteria:  
  
- To działa.  
  
- Nie zprzerywa wcześniej działającego kodu.  
  
- Nie powoduje konfliktu z projektem.  
  
  Dinner Now ma duży zbiór zautomatyzowanych testów, których może korzystać Lucerne, ponieważ prawie wszystkie nadal obowiązują. Lucerna można tworzyć na tych testach i dodać nowe na pokrycie nowej funkcje. Obie używają Visual Studio do uruchomienia testów ręcznych.  
  
  Aby upewnić się, że kod odpowiada wymaganiom projektu, zespoły konfigurują swoje kompilacje w Team Foundation Build, uwzględniając sprawdzanie poprawności warstwy. Jeśli wystąpią konflikty, raport jest generowany ze szczegółami.  
  
  Zobacz:  
  
- [Testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)  
  
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)  
  
- [Korzystanie z kontroli wersji](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
- [Kompiluj aplikację](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
##  <a name="UpdatingSystem"></a> Aktualizowanie systemu przy użyciu wizualizacji i modelowania  
 Lucerna i obiad teraz muszą zintegrować swoje systemy płatności. Poniższe sekcje pokazują, że diagramy modelowania w programie Visual Studio pomagają w wykonaniu tego zadania:  
  
- [Omówienie wymagań użytkowników: diagramy przypadków użycia](#UnderstandUseCases)  
  
- [Omówienie procesu biznesowego: diagramy aktywności](#UnderstandActivities)  
  
- [Opisz strukturę systemu: diagramy składników](#DescribeComponents)  
  
- [Opisz interakcje: diagramy sekwencji](#DescribeSequence)  
  
- [Wizualizacja istniejącego kodu: Map kodu](#VisualizeCode)  
  
- [Definiuj słownik typów: diagramy klas](#DefineClasses)  
  
- [Opisz logiczną architekturę: diagramy warstw](#DescribeLayers)  
  
  Zobacz:  
  
- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)  
  
- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)  
  
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)  
  
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)  
  
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)  
  
###  <a name="UnderstandUseCases"></a> Omówienie wymagań użytkowników: diagramy przypadków użycia  
 Diagramy przypadków użycia stanowią podsumowanie działań, że obsługuje system i osób wykonujących te działania. Lucerna używa diagramu przypadków użycia, aby dowiedzieć się, system firmy Dinner Now w kwestii:  
  
- Klienci składają zamówienia.  
  
- Restauracje otrzymują zamówienia.  
  
- Brama zewnętrznego agenta płatności procesora, który używa System płatności obiad teraz do sprawdzania poprawności płatności, jest poza zakresem dla witryny sieci Web.  
  
  Diagram pokazuje również, jak główne przypadki użycia dzielą się na mniejsze przypadki użycia. Lucerna chce korzystać z jej własnego systememu płatności. Wyróżnia przypadek użycia proces płatności innym kolorem, aby wskazać, że wymaga on zmiany:  
  
  ![Wyróżnianie przetwarzania płatności na diagramie przypadku użycia](../modeling/media/uml-processpay.png "UML_ProcessPay")  
  
  **Wyróżnianie przetwarzania płatności na diagramie przypadku użycia**  
  
  Jeśli czas tworzenia był krótki, zespół może omówić, czy chcą umożliwić klientom płacenie restauracjom bezpośrednio. Aby to pokazać, zastąpi przypadek użycia proces płatności przy użyciu jednego, który jest poza granicami system firmy Dinner Now. Następnie łączy klienta bezpośrednio z Restauracją, wskazując, że firmy Dinner Now może tylko przetwarzać zamówienia:  
  
  ![Zmiana zakresu płatności restauracji na diagramie przypadku użycia](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")  
  
  **Zmiana zakresu płatności restauracji na diagramie przypadków użycia**  
  
  Zobacz:  
  
- [Diagramy przypadków użycia UML: informacje](../modeling/uml-use-case-diagrams-reference.md)  
  
- [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="drawing-a-use-case-diagram"></a>Rysowanie diagramu przypadków użycia  
 Diagram przypadków użycia ma następujące cechy główne:  
  
- *Aktorzy* reprezentują role pełnione przez osoby, organizacje, maszyny lub systemy oprogramowania. Na przykład klient, restauracja i System płatności obiad teraz są aktorami.  
  
- *Zastosowań* reprezentują interakcje między podmiotami i systemem w fazie projektowania.  Mogą one reprezentować dowolną skalę interakcji z jednym kliknięciem myszy lub wiadomości do transakcji trwającej wiele dni.  
  
- *Skojarzenia* powiązują aktorów z przypadkami użycia.  
  
- Większy przypadek użycia może *obejmują* mniejszymi, na przykład, Utwórz zamówienie zawiera wybierz restaurację. Możesz *rozszerzyć* przypadek użycia, który dodaje cele i kroki do przypadku rozszerzonego użycia, aby wskazać, że przypadek użycia występuje jedynie w pewnych warunkach. Przypadki użycia mogą również dziedziczyć z innego.  
  
- A *podsystemu* reprezentuje system oprogramowania, które jest projektowane lub jeden z jego składników. Jest duże pole, które zawiera przypadki użycia. Diagram przypadków użycia wyjaśnia, co jest wewnątrz lub na zewnątrz granicy podsystemu. Aby wskazać, że użytkownik musi osiągnąć określone cele w inny sposób, narysuj te przypadki użycia poza granicą podsystemu.  
  
- *Artefakty* połączyć elementy na diagramie z innymi diagramami lub dokumentami.  
  
  Zobacz:  
  
- [Diagramy przypadków użycia UML: informacje](../modeling/uml-use-case-diagrams-reference.md)  
  
- [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-use-case-diagrams"></a>Podsumowanie: Zalety diagramów przypadków użycia  
 Diagramy przypadków użycia ułatwiają wizualizowanie:  
  
-   Działania, które system obsługuje lub nie obsługuje  
  
-   Osoby i systemy zewnętrzne, które wykonują te działania  
  
-   Główne składniki systemu obsługujące każde działanie, które można przedstawić jako podsystemy zagnieżdżone wewnątrz systemu nadrzędnego  
  
-   Jak przypadek użycia można podzielić na mniejsze lub na odmiany  
  
#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  
  
|**Diagram**|**W tym artykule opisano**|  
|-----------------|-------------------|  
|Diagramu aktywności|Przepływ kroków w przypadku użycia i używające, które wykonują te kroki w przypadku.<br /><br /> Nazwy przypadków użycia często odzwierciedlają kroki na diagramie aktywności. Diagramy aktywności obsługują elementy, takie jak decyzje, scalenia, dane wejściowe i wyjściowe, przepływy współbieżne i tak dalej.<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagramów sekwencji|Sekwencja interakcji między uczestnikami w przypadku użycia.<br /><br /> Zobacz:<br /><br /> -   [Diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagram klas (UML)|Jednostki lub typy, które uczestniczą w przypadku użycia.<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|  
  
###  <a name="UnderstandActivities"></a> Omówienie procesu biznesowego: diagramy aktywności  
 Diagramy aktywności opisują przepływ kroków procesu biznesowego i zapewniają prosty sposób komunikowania przepływu pracy. Projekt rozwoju może mieć wiele diagramów aktywności. Zwykle działanie obejmuje wszystkie akcje, które wynikają z jednego z działań zewnętrznych, takich jak zamawianie posiłku, aktualizowanie menu lub dodanie nowej restauracji do działalności. Działanie może również opisywać szczegóły działań złożonych.  
  
 Lucerna aktualizacje następujący diagramie aktywności, aby pokazać, że Lucerna przetwarza płatności i płaci restauracjom. System płatności obiad teraz one Zamień System płatności firmy Lucerne, jak podkreślono:  
  
 ![System płatności firmy Lucerne na diagramie aktywności](../modeling/media/uml-lucerne.png "UML_Lucerne")  
  
 **Zastępowanie System płatności obiad teraz w diagramie aktywności**  
  
 Zaktualizowany diagram pomaga firmom Lucerne i Dinner Now zwizualizować, gdzie System płatności firmy Lucerne znajdzie się w procesie biznesowym. W tym wydaniu komentarze służą do definiowania ról, które należy wykonać czynności. Wiersze są używane do tworzenia *torów*, które organizują etapy poprzez role.  
  
 Zespoły mogą też rozważyć omówienie alternatywnego scenariusza, gdy klient płaci restauracji zamiast po dostarczeniu zamówienia. To spowodowałoby różne wymagania dotyczące systemu oprogramowania.  
  
 Poprzednio obiad teraz zwrócił te diagramy na tablicy lub w programie PowerPoint. Teraz również używa programu Visual Studio do narysowania tych diagramów, tak aby oba zespoły można przechwycić, zrozumieć i zarządzać szczegółowe informacje.  
  
 Zobacz:  
  
-   [Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)  
  
-   [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="drawing-an-activity-diagram"></a>Rysowanie diagramu aktywności  
 Diagram aktywności ma następujące cechy główne:  
  
- *Węzeł początkowy* który określa pierwszą akcję działania.  
  
   Diagram zawsze powinien mieć jeden z tych węzłów.  
  
- *Akcje* opisują kroki, których użytkownik lub oprogramowanie wykonują zadanie.  
  
- *Kontrole przepływu* ukazują przepływ między działaniami.  
  
- *Węzły decyzji* reprezentujące rozgałęzienia warunkowe w przepływie.  
  
- *Węzły Rozwidlające* które dzielą pojedyncze przepływy na przepływy współbieżne.  
  
- *Węzły ostateczne działalności* które pokazują koniec działań.  
  
   Chociaż te węzły są opcjonalne, warto uwzględnić je na diagramie aby pokazać, gdzie kończy się działanie.  
  
  Zobacz:  
  
- [Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)  
  
- [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-activity-diagrams"></a>Podsumowanie: Zalety diagramów aktywności  
 Diagramy aktywności ułatwiają wizualizację i opisywanie przepływu sterowania i informacji między działaniami firmy, systemu lub programu. Jest to prosty i skuteczny sposób na odzwierciedlanie przepływu pracy podczas komunikowania się z innymi osobami.  
  
#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  
  
|**Diagram**|**Opis**|  
|-----------------|---------------------|  
|Diagramów przypadków użycia|Podsumowanie działań, które wykonuje każdy uczestnik.<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagramów składników|Umożliwia wizualizację systemu jako zbiór części wielokrotnego użytku, które zapewniają lub zużywają działanie za pomocą wyraźnie określonych interfejsów.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)|  
  
###  <a name="DescribeComponents"></a> Opisz strukturę systemu: diagramy składników  
 Diagramy składników opisują system jako kolekcję osobnych części, które zapewniają lub zużywają działanie za pomocą wyraźnie określonych interfejsów. Części mogą być w dowolnej skali i mogą być połączone w dowolny sposób.  
  
 Aby pomóc firmom Lucerne i Dinner Now wizualizować i omówić składniki systemu oraz ich interfejsów, tworzą następujące diagramy składników:  
  
 ![Składniki zewnętrzne w systemie płatności](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")  
  
 **Składniki systemu płatności Dinner Now**  
  
 Ten diagram przedstawia różne typy składników i ich *zależności*. Na przykład zarówno witrynę sieci obiad teraz, jak i System płatności firmy Lucerne wymagają brama zewnętrznego procesora płatności do sprawdzania poprawności płatności. Strzałki między składnikami przedstawiają zależności wskazujące, które składniki wymagają funkcjonalności innych składników.  
  
 Aby użyć System płatności firmy Lucerne, należy zaktualizować witrynę sieci obiad teraz do użycia interfejsów PaymentApproval i PayableInsertion w systemie płatności Lucerne.  
  
 Poniższy diagram przedstawia określoną konfigurację składników dla witryny firmy Dinner Now w sieci Web. Ta konfiguracja oznacza, że dowolne wystąpienie witryny sieci Web składa się z czterech *części*:  
  
- CustomerProcessing  
  
- OrderProcessing  
  
- ReviewProcessing  
  
- PaymentProcessing  
  
  Te części są wystąpieniami określonych typów składników i są połączone w następujący sposób:  
  
  ![Składniki wewnątrz witryny firmy Dinner Now w sieci Web](../modeling/media/uml-dinnernow.png "UML_DinnerNow")  
  
  **Składniki wewnątrz Dinner Now witrynę sieci Web**  
  
  Obiad teraz witryny sieci Web deleguje swoje zachowanie na te części, które obsługują funkcje witryny sieci Web. Strzałki między składnikiem nadrzędnym i jego składnikami Członkowskimi pokazują *delegacji* wskazujące części obsługujące komunikaty, które nadrzędny otrzymuje lub wysyła za pośrednictwem jej interfejsów.  
  
  W tej konfiguracji składnik PaymentProcessing przetwarza płatności odbiorcy. W związku z tym należy go zaktualizować w celu integracji z systemem płatności firmy Lucerne. W innych sytuacjach wiele wystąpień typu składnika może istnieć w tym samym składniku nadrzędnym.  
  
  Zobacz:  
  
- [Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)  
  
- [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="drawing-a-component-diagram"></a>Rysowanie diagramu składników  
 Diagram składników ma następujące cechy główne:  
  
- *Składniki* reprezentujące oddzielene części funkcjonalności systemu.  
  
- *Zapewnij porty interfejsu* reprezentujące grupy wiadomości lub połączeń, których składniki wdrażają i są używane przez inne składniki lub systemy zewnętrzne.  
  
- *Zapewnij porty interfejsu* reprezentujące grupy wiadomości lub połączeń, których składniki wysyłają do innych składników lub systemów zewnętrznych. Tego rodzaju port opisuje operacje, których składnik co najmniej oczekuje od innych składników lub systemów zewnętrznych.  
  
- *Części* są członkami składników i są zazwyczaj wystąpieniami innych składników. Część jest fragmentem projektu wewnętrznego składnika nadrzędnego.  
  
- *Zależności* wskazujące składniki wymagają funkcjonalności innych składników.  
  
- *Delegacji* wskazujące części składnika obsługi wiadomości wysłanych lub odebranych przez składnik nadrzędny.  
  
  Zobacz:  
  
- [Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)  
  
- [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-component-diagrams"></a>Podsumowanie: Zalety diagramów składników  
 Diagramy składników ułatwiają wizualizowanie:  
  
-   System jako kolekcja osobnych części, niezależnie od ich implementacji języka i stylu.  
  
-   Składniki z dobrze określonymi interfejsami, co ułatwia zrozumienie i aktualizację w przypadku zmiany wymagań projektu.  
  
#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  
  
|**Diagram**|**Opis**|  
|-----------------|---------------------|  
|Mapy kodu|Umożliwia wizualizację organizacji i relacjach w istniejącym kodzie.<br /><br /> Aby zidentyfikować potencjalne składniki, tworzenie kodu mapy i pogrupować elementy według ich funkcji w systemie.<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)|  
|Diagramów sekwencji|Umożliwia wizualizację sekwencji wzajemnego oddziaływania między komponentami lub częściami wewnątrz składnika.<br /><br /> Aby utworzyć linię życia na diagramie sekwencji ze składnika, kliknij prawym przyciskiem myszy składnik, a następnie kliknij przycisk **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [Diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagram klas (UML)|Definiuj interfejsy na dostarczonych lub wymaganych portach i klasy, które implementują funkcjonalność składników.<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagram warstwowy|Opisz logiczną architekturę systemu w powiązaniu ze składnikami. Użyj sprawdzania poprawności warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagramu aktywności|Umożliwia wizualizację wewnętrznego przetwarzania, które składniki wykonują w odpowiedzi na wiadomości przychodzące.<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|  
  
###  <a name="VisualizeCode"></a> Wizualizacja istniejącego kodu: Map kodu  
 Mapy kodu pokazują bieżącą organizacją i relacje w kodzie. Elementy są reprezentowane przez *węzłów* na mapie, a relacje są reprezentowane przez *łącza*. Mapy kodu może pomóc Ci realizować następujące rodzaje zadań:  
  
- Poznawanie nieznanego kodu.  
  
- Dowiedz się, gdzie i w jaki sposób proponowana zmiana może mieć wpływ na istniejący kod.  
  
- Znajdowanie obszarów złożoności, naturalnych warstw lub wzorców albo innych obszarów, które mogą skorzystać na poprawie.  
  
  Na przykład Dinner Now musi oszacować koszt aktualizacji składnika PaymentProcessing. Zależy to częściowo ile ta zmiana wpłynie na inne części systemu. Aby pomóc im to zrozumieć, jeden z deweloperów Dinner Now generuje mapy kodu z kodu i dopasowuje obszarem zakresu obszarów, które mogą mieć wpływ zmiany.  
  
  Poniższe mapy przedstawia zależności między klasą PaymentProcessing i innymi częściami systemu firmy Dinner Now, które zostaną wyświetlone jako zaznaczone:  
  
  ![Wykres zależności dla systemu płatności Dinner Now](../modeling/media/dep-dnpayment.png "Dep_DNPayment")  
  
  **Mapę kodu dla systemu płatności Dinner Now**  
  
  Deweloper bada mapy, rozwijając klasę PaymentProcessing i wybierając jej elementy członkowskie, aby zobaczyć obszary, które potencjalnie dotyczą zmiany:  
  
  ![Metody wewnątrz PaymentProcessing i zależności](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")  
  
  **Metody wewnątrz klasy PaymentProcessing i ich zależności**  
  
  Generują poniższe mapy dla systemu płatności firmy Lucerne sprawdzić jej klas, metod i zależności. Zespół widzi, że system firmy Lucerne może również wymagać pracy nad interakcją z innymi częściami firmy Dinner now:  
  
  ![Wykres zależności dla systemu płatności Lucerne](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")  
  
  **Mapy kodu dla systemu płatności Lucerne**  
  
  Oba zespoły współpracują ze sobą w celu określenia zmian, które są wymagane do zintegrowania dwóch systemów. One decyduje się o zrefaktoryzować część kodu, czemu będzie łatwiejszy do aktualizacji. Klasa PaymentApprover zostanie przeniesione do obszaru nazw DinnerNow.Business i będzie wymagać pewnych nowych metod. Klasy firmy Dinner Now, które obsługują transakcje, będą miały własny obszar nazw. Zespoły tworzą i używanie elementów roboczych do planowania, organizowania i śledzenia swojej pracy. Łączą elementy robocze z elementami modelu, gdzie jest to użyteczne.  
  
  Po reorganizacji kodu zespoły generują nowej mapy kodu, aby zobaczyć zaktualizowaną strukturę i relacje:  
  
  ![Wykres zależności z kodem zreorganizowanym](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")  
  
  **Mapy kodu z kodem zreorganizowanym**  
  
  Ta mapa pokazuje, że klasa PaymentApprover znajduje się teraz w przestrzeni nazw DinnerNow.Business i ma kilka nowych metod. Klasy transakcji firmy Dinner Now mają teraz własne obszar nazw PaymentSystem, dzięki czemu łatwiej radzenia sobie z tym kodem później.  
  
#### <a name="creating-a-code-map"></a>Tworzenie Map kodu  
  
-   Aby uzyskać szybki przegląd kodu źródłowego wykonaj następujące kroki, aby wygenerować mapę kodu:  
  
     Na **architektury** menu, kliknij przycisk **Generuj mapę kodu dla rozwiązania**.  
  
     Aby uzyskać szybki przegląd skompilowanego kodu Utwórz mapę kodów puste, a następnie przeciągnij pliki zestawu lub pliki binarne do powierzchni mapy.  
  
-   Aby poznać konkretny kod lub elementy rozwiązania, użyj Eksploratora rozwiązań, aby wybrać elementy i relacje, które mają być wyświetlane. Możesz następnie wygenerować nowej mapy lub Dodaj wybrane elementy do istniejącej mapy. Zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Aby ułatwić zrozumienie mapy, można zmienić układ, aby go do rodzaju zadań, które chcesz wykonać.  
  
     Na przykład do zwizualizowania warstw w kodzie, wybierz układ drzewa. Zobacz [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).  
  
#### <a name="summary-strengths-of-code-maps"></a>Podsumowanie: Zalety map kodu  
 Mapy kodu ułatwiają:  
  
-   Więcej informacji o organizacji i relacjach w istniejącym kodzie.  
  
-   Zidentyfikuj obszary, które mogą mieć wpływ proponowana zmiana.  
  
-   Znajdowanie obszarów złożoności, wzorów, warstwy lub innych obszarów, które można poprawić, aby ułatwić utrzymania, zmieniać i ponownego użycia kodu.  
  
#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  
  
|**Diagram**|**W tym artykule opisano**|  
|-----------------|-------------------|  
|Diagram warstwowy|Logiczna architektura systemu. Użyj sprawdzania poprawności warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Aby ułatwić identyfikację istniejących lub planowanych warstw, utwórz mapę kodu i pogrupować pokrewne elementy. Aby utworzyć diagram warstwy, zobacz:<br /><br /> -   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)|  
|Diagramów składników|Składniki, ich interfejsy oraz ich wzajemne relacje.<br /><br /> Aby pomóc w zidentyfikowaniu składników, utworzyć kod mapy i pogrupować elementy według ich funkcji w systemie.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagram klas (UML)|Klasy, ich atrybuty i operacje oraz ich wzajemne relacje.<br /><br /> Aby pomóc w zidentyfikowaniu tych elementów, należy utworzyć diagram klas UML, pokazujący te elementy.<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagram klasy (oparty na kodzie)|Istniejące klasy w kodzie dla konkretnego projektu.<br /><br /> Wizualizację i modyfikowanie istniejącej klasy w kodzie, za pomocą projektanta klas.<br /><br /> Zobacz [porady: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  
  
###  <a name="DescribeSequence"></a> Opisz interakcje: diagramy sekwencji  
 Diagramy sekwencji opisują serię interakcji między częściami systemu. Części mogą być w dowolnej skali. Na przykład mogą sięgać od poszczególnych obiektów w programie do dużych podsystemów lub podmiotów zewnętrznych. Interakcje mogą mieć dowolną skalę i typu. Na przykład mogą sięgać od pojedynczych komunikatów do rozszerzonych transakcji i mogą być wywołaniami funkcji lub komunikatami usługi sieci Web.  
  
 Aby pomóc firmom Lucerne i Dinner Now opisać i omówić czynności w przypadku użycia przetwarzanie płatności, tworzą poniższego diagramu sekwencji z diagramu składników. Są lustrzanym odbiciem witryny firmy Dinner Now w sieci Web i jej części. Komunikaty wyświetlane między liniami życia odpowiadają połączeniom na diagramach składników:  
  
 ![Diagram sekwencji dla przetwarzania płatności, przypadek użycia](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")  
  
 **Diagram sekwencji dla przetwarzania płatności, przypadek użycia**  
  
 Diagram sekwencji pokazuje, że gdy klient tworzy zamówienie, obiad teraz witryny sieci Web wywołuje metodę ProcessOrder dla wystąpienia obiektu OrderProcessing. Następnie OrderProcessing wywołuje ProcessPayment na PaymentProcessing. Ten proces jest kontynuowany, dopóki brama zewnętrznego agenta rozliczeniowego płatności nie sprawdzi poprawność płatności. Dopiero wtedy kontrola zwraca do witryny firmy Dinner Now w sieci Web.  
  
 Lucerna musi oszacować koszt aktualizacji system płatności, ich integracji z systemem obiad teraz. Aby pomóc im to zrozumieć, może być tworzą one równie map kodu, aby wizualizować kod, których to dotyczy.  
  
 Zobacz:  
  
-   [Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)  
  
-   [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)  
  
-   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)  
  
#### <a name="drawing-a-sequence-diagram"></a>Rysowanie diagramu sekwencji  
 Diagram sekwencji ma następujące cechy główne:  
  
- Pionowe *linii życia* reprezentują aktorów lub wystąpienia obiektów oprogramowania.  
  
   Aby dodać symbol aktora, co oznacza, że uczestnik jest poza systemem w fazie projektowania, kliknij przycisk linii życia. W **właściwości** oknie **aktora** do **True**. Jeśli **właściwości** okno nie jest otwarte, naciśnij **F4**.  
  
- Poziomy *wiadomości* reprezentują wywołania metod, komunikaty usług sieci Web lub niektóre inne rodzaje komunikacji. *Wystąpienia wykonania* są pionowymi cieniowanymi prostokątami, które pojawiają się na liniach życia i reprezentują okresy, podczas których obiekty odbierające przetwarzają wywołania.  
  
- Podczas *synchroniczne* komunikat obiektu nadawcy czeka na formant, aby <\<zwracają >> tak jak w regularnym wywołaniu funkcji. Podczas *asynchronicznego* wiadomości, nadawca może natychmiast kontynuować.  
  
- Użyj <\<Tworzenie >> wiadomości, które umożliwiają wskazanie konstrukcji obiektów przez inne obiekty. Powinno być pierwszą wiadomością wysłaną do obiektu.  
  
  Zobacz:  
  
- [Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)  
  
- [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-sequence-diagrams"></a>Podsumowanie: Zalety diagramów sekwencji  
 Diagramy sekwencji pozwalają zwizualizować:  
  
-   Przepływ sterowania, które przechodzi między aktorami i obiektami podczas wykonywania przypadku użycia.  
  
-   Implementacja wywołania metody lub komunikatu.  
  
#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  
  
|**Diagram**|**Opis**|  
|-----------------|---------------------|  
|Diagram klas (UML)|Definiowanie klas, które reprezentują linie życia oraz parametry i zwracane wartości, które są używane w wiadomościach przesyłanych między liniami życia.<br /><br /> Aby utworzyć klasę z linii życia, kliknij prawym przyciskiem myszy linii życia, a następnie kliknij przycisk **Utwórz klasę** lub **Utwórz interfejs**. Aby utworzyć linię życia z typu na diagramie klasy, kliknij prawym przyciskiem myszy typ, a następnie kliknij przycisk **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagramów składników|Opisz składniki, linie życia oraz interfejsy, które zapewniają i wykorzystują zachowanie reprezentowane przez wiadomości.<br /><br /> Aby utworzyć linię życia z diagramu składników, kliknij prawym przyciskiem myszy składnik, a następnie kliknij przycisk **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagramów przypadków użycia|Podsumowanie interakcji między użytkownikami i składnikami na diagramie sekwencji jako przypadek użycia, który przedstawia cel użytkownika.<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|  
  
###  <a name="DefineClasses"></a> Definiuj słownik typów: diagramy klas  
 Diagramy klas określają podmioty, terminy i pojęcia, które uczestniczą w systemie oraz ich wzajemne relacje. Na przykład służy tych diagramów podczas programowania do opisania atrybutów i operacji dla każdej klasy, niezależnie od ich implementacji języka i stylu.  
  
 Aby pomóc firmie Lucerne opisać i omówić podmioty, które uczestniczą w przypadku użycia przetwarzanie płatności, można narysować Poniższy diagram klasy:  
  
 ![Jednostki procesu płatności na diagramie klasy](../modeling/media/uml-payentities.png "UML_PayEntities")  
  
 **Jednostki procesu płatności na diagramie klasy**  
  
 Ten diagram przedstawia to, że klient może mieć wiele zamówień i płacić za zamówienia na różne sposoby. BankAccount i CreditCard dziedziczy płatności.  
  
 Podczas programowania Lucerne używa poniższego diagramu klas do opisania i omówienia szczegółów każdej klasy:  
  
 ![Szczegóły procesu płatności jednostek na diagramie klasy](../modeling/media/uml-payment.png "UML_Payment")  
  
 **Szczegóły procesu płatności na diagramie klasy**  
  
 Zobacz:  
  
-   [Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)  
  
-   [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)  
  
#### <a name="drawing-a-class-diagram"></a>Rysowanie diagramu klas  
 Diagram klas ma następujące cechy główne:  
  
- Typy takie jak klasy, interfejsy i wyliczenia:  
  
  -   A *klasy* jest definicji obiektów, które mają szczególne strukturalnych szczególnymi cechami strukturalnymi i.  
  
  -   *Interfejsu* definiuje część widocznych zewnętrznych zachowań obiektu.  
  
  -   *Wyliczenie* jest klasyfikatorem, który zawiera listę wartości literałów.  
  
- *Atrybuty* to wartości pewnego typu, opisujące każde wystąpienie *klasyfikatora*. Klasyfikator to ogólna nazwa dla typów, składników, przypadków użycia i nawet aktorów.  
  
- *Operacje* są metodami lub funkcjami, które mogą wykonywać wystąpienia klasyfikatora.  
  
- *Skojarzenia* oznacza pewnego rodzaju relację między dwoma klasyfikatorami.  
  
  - *Agregacji* jest skojarzeniem, które wskazuje wspólną własność między klasyfikatorami.  
  
  - A *kompozycji* to skojarzenie ukazujące relacje między klasyfikatorami.  
  
    Aby wyświetlić agregacje lub kompozycje, ustaw **agregacji** właściwości skojarzenia. **Udostępnione** pokazuje agregacje i **złożonego** — kompozycje.  
  
- A *zależności* wskazuje, że zmiana definicji jednego klasyfikatora może zmienić definicję innego klasyfikatora.  
  
- A *Generalizacja* wskazuje, że dany Klasyfikator dziedziczy część jego definicji od klasyfikatora ogólnego. A *realizacja* wskazuje, że klasa implementuje operacje i atrybuty oferowane przez interfejs.  
  
   Aby utworzyć te relacje, należy użyć **dziedziczenia** narzędzia. Alternatywnie, realizacja może być reprezentowana jako *interfejsu typu lizak*.  
  
- *Pakiety* są grupami klasyfikatorów, skojarzeń, linii życia, składników i innych pakietów. *Importuj* relacji wskazują, że jeden pakiet zawiera wszystkie definicje innego pakietu.  
  
  Jako punktu wyjścia do badania i omawiania istniejących klas można użyć projektanta klas do tworzenia diagramów klas z kodu.  
  
  Zobacz:  
  
- [Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)  
  
- [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)  
  
- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>Podsumowanie: Zalety diagramów klas  
 Diagramy klas pomagają określić:  
  
-   Wspólny Słownik terminów do wykorzystania podczas omawiania potrzeb użytkowników i jednostek, które uczestniczą w systemie. Zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
-   Typy, które są używane przez części systemu, takie jak składniki, niezależnie od ich implementacji. Zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).  
  
-   Relacje, takie jak zależności między typami. Na przykład można pokazać, że jeden typ może być skojarzony z wieloma wystąpieniami innego typu.  
  
#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  
  
|**Diagram**|**Opis**|  
|-----------------|---------------------|  
|Diagramów przypadków użycia|Zdefiniuj typy, które są używane do opisywania celów i etapów przypadków użycia.<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagramu aktywności|Definiowanie typów danych, które przechodzą przez węzły obiektów, PinY wejściowe, PinY wyjściowe oraz węzły parametru działania.<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagramów składników|Opisz składniki, ich interfejsy oraz ich wzajemne relacje. Klasa może również opisywać dokończyć kompletny komponent.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagram warstwowy|Definiuj logiczną architekturę systemu, w odniesieniu do klasy.<br /><br /> Użyj sprawdzania poprawności warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagramów sekwencji|Definiuj rodzaje linii życia i operacje, parametry i zwracane wartości dla wszystkich wiadomości, które linia życia może odbierać.<br /><br /> Aby utworzyć linię życia z typu na diagramie klasy, kliknij prawym przyciskiem myszy typ, a następnie kliknij przycisk **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [Diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Mapy kodu|Umożliwia wizualizację organizacji i relacjach w istniejącym kodzie.<br /><br /> Aby zidentyfikować klasy, ich relacje i ich metod, utwórz mapę kodu, pokazujący te elementy.<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)|  
  
###  <a name="DescribeLayers"></a> Opisz logiczną architekturę: diagramy warstw  
 Diagramy warstwy opisują architekturę logiczną systemu organizowania artefaktów w Twoich rozwiązaniach w abstrakcyje grupy, lub *warstwy*. Artefakty mogą być różne, takie jak przestrzenie nazw, projekty, klasy, metody i tak dalej. Warstwy przedstawiają i opisują role lub zadania, które te artefakty pełnią w systemie. Można także dodać sprawdzanie poprawności warstwy w kompilacji i ewidencjonowaniu operacji, aby upewnić się, że kod pozostaje zgodny z jego zamysłem.  
  
 Aby zachować zgodność kodu z projektem, firmy Dinner Now i Lucerne umożliwia poniższego diagramu warstwy sprawdzania poprawności kodu, jest opracowywany:  
  
 ![Diagram warstwy system płatności zintegrowane](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagram warstwy na obiad teraz zintegrowany z Lucerną**  
  
 Warstwy na tym diagramie połączyć odpowiednie artefakty rozwiązania firmy Dinner Now i Lucerne. Na przykład warstwa biznesowa łączy do nazw DinnerNow.Business i jej elementów członkowskich, które obejmują teraz klasa PaymentApprover. Linki warstwy dostępu do zasobów z obszarem nazw DinnerNow.Data. Strzałki, lub *zależności*, określić, że tylko warstwa biznesowa może używać funkcji w warstwie dostępu do zasobów. Jako że zespoły aktualizują kod, sprawdzanie poprawności warstwy odbywa się regularnie pozwala na wychwytywanie konfliktów w momencie ich wystąpienia i pomagają zespołom niezwłoczne ich rozwiązywanie.  
  
 Zespoły współpracują ze sobą nad stopniową integracją i testowaniem tych dwóch systemów. One najpierw upewnij się, że PaymentApprover i pozostała część Dinner Now dobrze ze sobą pomyślnie przed mają do czynienia PaymentProcessing.  
  
 Poniższe mapy kodu pokazuje nowe wywołania między Dinner Now a PaymentApprover:  
  
 ![Wykres zależności zaktualizowane przy użyciu zintegrowanego systemu](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")  
  
 **Mapy kodu ze zaktualizowanymi wywołaniami metod**  
  
 Po potwierdzeniu, że system działa zgodnie z oczekiwaniami, Dinner Now komentuje kod PaymentProcessing. Raporty sprawdzania poprawności warstwy są czyste, a wynikowy mapy kodu pokazuje, że istnieje nie więcej zależności klasy PaymentProcessing:  
  
 ![Wykres zależności bez PaymentProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")  
  
 **Mapy kodu bez PaymentProcessing**  
  
#### <a name="drawing-a-layer-diagram"></a>Rysowanie diagramu warstw  
 Diagram warstwy ma następujące cechy główne:  
  
- *Warstwy* opis grupy logicznej artefaktów.  
  
- A *łącze* jest skojarzeniem między warstwą i artefaktem.  
  
   Aby utworzyć warstwy z artefaktów, przeciągnij elementy z Eksploratora rozwiązań, map kodu, widoku klas lub przeglądarki obiektów. Aby narysować nowe warstwy i łączyć je w artefakty, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu, aby utworzyć warstwy, a następnie przeciągnij elementy do tych warstw.  
  
   Liczba na warstwie pokazuje liczbę artefaktów, które są połączone z warstwą. Te artefakty mogą być przestrzenie nazw, projekty, klasy, metody i tak dalej. Interpretując liczbę artefaktów na warstwie, pamiętaj o następujących kwestiach:  
  
  - Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.  
  
     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.  
  
  - Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.  
  
    Aby zobaczyć artefakty, które są połączone z warstwą, kliknij prawym przyciskiem myszy warstwę, a następnie kliknij przycisk **Wyświetl łącza** otworzyć **Eksplorator warstw**.  
  
- A *zależności* wskazuje, że jedna warstwę może korzystać z funkcji w innej warstwie, ale nie odwrotnie. A *zależność dwukierunkowa* wskazuje, że jedna warstwę może korzystać z funkcji w innej warstwie i odwrotnie.  
  
   Aby wyświetlić istniejące zależności na diagramie warstwy, kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij przycisk **Wygeneruj zależności**. Aby opisać zależności zamierzone, narysuj nowe.  
  
  Zobacz:  
  
- [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)  
  
- [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)  
  
- [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-layer-diagrams"></a>Podsumowanie: Zalety diagramów warstw  
 Diagramy warstwy pomogą Ci:  
  
-   Opisz logiczną architekturę systemu zgodnie z funkcji jego artefaktów.  
  
-   Upewnij się, że kod w opracowaniu odpowiada określonemu projektowi.  
  
#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  
  
|**Diagram**|**Opis**|  
|-----------------|---------------------|  
|Mapy kodu|Umożliwia wizualizację organizacji i relacjach w istniejącym kodzie.<br /><br /> Aby utworzyć warstwy, Generuj mapę kodu, a następnie zgrupuj elementy na mapie jako potencjalne warstwy. Przeciągnij grupy z mapy do diagramu warstwowego.<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Przeglądanie i rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)|  
|Diagramów składników|Opisz składniki, ich interfejsy oraz ich wzajemne relacje.<br /><br /> Aby zwizualizować warstwy, Utwórz diagram składników, który opisuje funkcje różnych składników w systemie.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)|  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
|**Kategoria**|**Łącza**|  
|------------------|---------------|  
|**Fora**|-   [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Zobacz też  
 [Wizualizacja kodu](../modeling/visualize-code.md)   
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)   
 [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)   
 [Używaj modeli w Agile development](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Weryfikacja systemu w czasie projektowania](../modeling/validate-your-system-during-development.md)   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)



