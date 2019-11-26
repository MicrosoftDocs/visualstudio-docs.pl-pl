---
title: 'Scenariusz: zmiana projektu przy użyciu wizualizacji i modelowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cafc4e2a87a31603e1f8cef4174d8538be768428
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296026"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upewnij się, że system oprogramowania spełnia potrzeby użytkowników, korzystając z narzędzi do wizualizacji i modelowania w programie Visual Studio. Użyj narzędzi, takich jak diagramy UML (UML), mapy kodu, Diagramy warstw i diagramy klas, aby:

 Aby sprawdzić, które wersje programu Visual Studio obsługują poszczególne narzędzia, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Wyjaśnij wymagania użytkowników i procesy biznesowe.

- Wizualizuj i Eksploruj istniejący kod.

- Opisz zmiany w istniejącym systemie.

- Sprawdź, czy system spełnia wymagania.

- Zachowaj spójność kodu z projektem.

  Ten przewodnik:

- Opisuje, jak te narzędzia mogą korzystać z projektu oprogramowania.

- Pokazuje, w jaki sposób można korzystać z tych narzędzi, niezależnie od podejścia programistycznego, z przykładowym scenariuszem.

  Aby dowiedzieć się więcej o tych narzędziach i scenariuszach, które są przez nie obsługiwane, zobacz:

- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)

## <a name="ScenarioOverview"></a>Omówienie scenariusza
 W tym scenariuszu opisano odcinki cykli rozwoju oprogramowania dwóch fikcyjnych firm: obiad teraz i publikowanie z lucerny. Zapraszamy teraz usługa dostarczania posiłków opartych na sieci Web w Seattle. Klienci mogą zamówić posiłki i uregulować je w witrynie sieci Web obiadu teraz. Zamówienia są następnie wysyłane do odpowiedniej lokalnej restauracji na potrzeby dostawy. Publikowanie Lucerny, firma w Nowym Jorku, uruchamia kilka firm zarówno w sieci Web, jak i w Internecie. Na przykład uruchamiają witrynę sieci Web, w której klienci mogą publikować przeglądy restauracji.

 Przede wszystkim uzyskano obiad i chcemy wprowadzić następujące zmiany:

- Zintegruj swoje witryny sieci Web, dodając do obiadu teraz funkcje przeglądu restauracji.

- Zastąp teraz system płatności z tytułu obiadu w systemie z systemem Lucerny.

- Rozwiń usługę z obiadem teraz w całym regionie.

  Obiad obejmuje teraz programowanie SCRUM i eXtreme. Mają bardzo duże pokrycie testów i bardzo mały nieobsługiwany kod. Minimalizują one ryzyko, tworząc małe, ale działające wersje systemu, a następnie zwiększając przyrost funkcji. Opracowują swój kod w krótkich i częstych iteracjach. Dzięki temu mogą one często polegać na zmianie, niewielkim kodzie i uniknięciu "Big Design" na początku.

  Lucerny, w której znajduje się znacznie większa i złożona kolekcja systemów, a niektóre z nich są starsze niż 40 lat. Są one bardzo ostrożne w przypadku wprowadzania zmian ze względu na złożoność i zakres starszego kodu. Są one zgodne z bardziej rygorystycznym procesem opracowywania, ale przed projektowaniem szczegółowych rozwiązań i udokumentowaniem projektu oraz zmian, które wystąpiły podczas opracowywania.

  Oba zespoły używają diagramów modelowania w programie Visual Studio, aby ułatwić im opracowywanie systemów spełniających potrzeby użytkowników. Używają Team Foundation Server wraz z innymi narzędziami, aby ułatwić im planowanie i organizowanie pracy oraz zarządzanie nimi.

  Aby uzyskać więcej informacji na temat Team Foundation Server, zobacz:

- [Planowanie i śledzenie pracy](#PlanningTracking)

- [Testowanie, sprawdzanie poprawności i sprawdzanie zaktualizowanego kodu](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a>Role architektury i diagramy modelowania w programowaniu oprogramowania
 W poniższej tabeli opisano role, które te narzędzia mogą odtwarzać na różnych etapach cyklu tworzenia oprogramowania:

||**Modelowanie wymagań użytkownika**|**Modelowanie procesów firmy**|**Projekt architektury systemowej &**|**Wizualizacja kodu & Eksploracja**|**Zgodności**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Diagram przypadków użycia (UML)|√|√|||√|
|Diagram aktywności (UML)|√|√|√||√|
|Diagram klas (UML)|√|√|√||√|
|Diagram składników (UML)|√|√|√||√|
|Diagram sekwencji (UML)|√|√|√||√|
|Diagram języka specyficznego dla domeny (DSL)|√|√|√|||
|Diagram warstwowy, walidacja warstwy|||√|√|√|
|Mapa kodu|||√|√|√|
|Projektant klas (oparty na kodzie)||||√||

 Aby rysować diagramy UML i Diagramy warstw, należy utworzyć projekt modelowania jako część istniejącego rozwiązania lub nowego. Te diagramy muszą zostać utworzone w projekcie modelowania. Elementy na diagramach UML są częścią wspólnego modelu, a diagramy UML są widokami tego modelu. Elementy na diagramach warstw znajdują się w projekcie modelowania, ale nie są one przechowywane we wspólnym modelu. Mapy kodu i diagramy klas .NET utworzone na podstawie kodu istnieją poza projektem modelowania.

 Zobacz:

- [Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Aby wyświetlić alternatywne widoki architektury, można użyć niektórych elementów z tego samego modelu na wielu lub różnych diagramach. Na przykład można przeciągnąć składnik do innego diagramu składników lub diagramu sekwencji, aby mógł działać jako aktor. Zobacz [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

  Oba zespoły również używają walidacji warstwy, aby upewnić się, że kod w trakcie tworzenia nadal jest zgodny z projektem.

  Zobacz:

- [Zachowywanie spójności kodu w projekcie](#ValidatingCode)

- [Opisywanie architektury logicznej: diagramy warstwowe](#DescribeLayers)

- [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Niektóre wersje programu Visual Studio obsługują sprawdzanie poprawności warstwy i wersje tylko do odczytu na potrzeby wizualizacji i modelowania. Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="UnderstandingCommunicating"></a>Zrozumienie i przekazywanie informacji o systemie
 Nie ma określonej kolejności na potrzeby używania diagramów modelowania programu Visual Studio, dzięki czemu można ich używać w zależności od potrzeb lub podejścia. Zwykle zespoły ponownie odwiedzają swoje modele iteracyjnie i często w całym projekcie. Każdy diagram oferuje szczególne zalety, które ułatwiają zrozumienie, opisywanie i komunikowanie różnych aspektów systemu w trakcie opracowywania.

 Obiady teraz i lucerny komunikują się ze sobą i ze swoimi uczestnikami projektu, korzystając ze diagramów jako ich wspólnego języka. Na przykład obiad używa teraz diagramów do wykonywania następujących zadań:

- Wizualizuj istniejący kod.

- Komunikuj się z usługami w ramach platformy Lucerny, aby poznać nowe lub zaktualizowane historie użytkownika.

- Zidentyfikuj zmiany, które są wymagane do obsługi nowych lub zaktualizowanych historii użytkownika.

  W przypadku korzystania z diagramów z wykresów:

- Poznaj proces biznesowy obiadu teraz.

- Zapoznaj się z projektowaniem systemu.

- Skontaktuj się z obiadem teraz o nowych lub zaktualizowanych wymaganiach użytkownika.

- Aktualizacje dokumentów do systemu.

  Diagramy są zintegrowane z Team Foundation Server, dzięki czemu zespoły mogą łatwiej planować i śledzić swoją służbę oraz zarządzać nią. Na przykład używają modeli do identyfikowania przypadków testowych i zadań programistycznych i szacowania ich pracy. Linki lucerny Team Foundation Server elementy robocze do elementów modelu, dzięki czemu mogą monitorować postęp i upewnić się, że system spełnia wymagania użytkowników. Na przykład łączą przypadki użycia z elementami roboczymi przypadku testowego, dzięki czemu mogą zobaczyć, że przypadki użycia są spełnione, gdy wszystkie testy zostały zakończone pomyślnie.

  Zanim zespoły zaewidencjonują zmiany, sprawdzają poprawność kodu względem testów i projektu, uruchamiając kompilacje, które obejmują sprawdzanie poprawności warstwy i testy automatyczne. Pomaga to upewnić się, że zaktualizowany kod nie powoduje konfliktu z projektem i przerwaniem wcześniej działającej funkcjonalności.

  Zobacz:

- [Zrozumienie roli systemu w procesie biznesowym](#UnderstandingBPMandSystemDesign)

- [Opisywanie nowych lub zaktualizowanych wymagań użytkowników](#DescribingURM)

- [Tworzenie testów z modeli](#CreatingTests)

- [Identyfikowanie zmian w istniejącym systemie](#DeterminingChanges)

- [Zachowywanie spójności kodu w projekcie](#ValidatingCode)

- [Ogólne porady dotyczące tworzenia i używania modeli](#GeneralTips)

- [Planowanie i śledzenie pracy](#PlanningTracking)

- [Testowanie, sprawdzanie poprawności i sprawdzanie zaktualizowanego kodu](#TestValidateCheckInCode)

### <a name="UnderstandingBPMandSystemDesign"></a>Zrozumienie roli systemu w procesie biznesowym
 Lucerny, która chce dowiedzieć się więcej na temat procesu biznesowego obiadu teraz. Tworzą one następujące diagramy w celu łatwiejszego wyjaśnienia z obiadem:

|**4b**|**Szczegół**|
|-----------------|-------------------|
|*Diagram przypadków użycia (UML)*<br /><br /> Zobacz:<br /><br /> -   [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramy przypadków użycia -   UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md)|— Działania obsługiwane przez system obiady teraz<br />— Osoby i systemy zewnętrzne, które wykonują działania<br />— Główne składniki systemu, które obsługują poszczególne działania<br />— Części procesu biznesowego, które są poza zakresem bieżącego systemu, na przykład dostarczanie żywności|
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> [diagramy działań -   UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />[diagramy aktywności UML -   : wytyczne](../modeling/uml-activity-diagrams-guidelines.md)|Przepływ kroków, które występują, gdy klient tworzy zamówienie|
|*Diagram klas (UML)*<br /><br /> Zobacz:<br /><br /> -   [diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />[diagramy klas UML -   : wytyczne](../modeling/uml-class-diagrams-guidelines.md)|Jednostki biznesowe i warunki, które są używane w dyskusjach i relacje między tymi jednostkami. Na przykład element Order i menu jest częścią słownika w tym scenariuszu.|

 Na przykład w przypadku programu lucerny tworzy się następujący diagram przypadków użycia, aby zrozumieć zadania wykonywane w witrynie sieci Web obiady teraz i wykonujące te czynności:

 ![Diagram przypadków użycia UML](../modeling/media/uml-usecase.png "UML_UseCase")

 **Diagram przypadków użycia UML**

 Poniższy diagram aktywności zawiera opis przepływu kroków, gdy klient tworzy zamówienie w witrynie sieci Web obiady teraz. W tej wersji elementy komentarzy identyfikują role i tworzą *tory*, które organizują kroki według roli:

 ![Diagram aktywności UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **Diagram aktywności UML**

 Na poniższym diagramie klas opisano jednostki, które uczestniczą w procesie zamawiania:

 ![Diagram klas UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **Diagram klas UML**

### <a name="DescribingURM"></a>Opisywanie nowych lub zaktualizowanych wymagań użytkowników
 W związku z tym klienci mogą dodawać funkcje do systemu obiady teraz, aby umożliwić klientom odczytywanie i tworzenie przeglądów restauracji. Aktualizują one następujące diagramy, aby umożliwić im opisywanie i omawianie nowego wymagania z obiadem:

|**4b**|**Szczegół**|
|-----------------|-------------------|
|*Diagram przypadków użycia (UML)*<br /><br /> Zobacz:<br /><br /> -   [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramy przypadków użycia -   UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md)|Nowy przypadek użycia dla "Napisz recenzję restauracji"|
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> [diagramy działań -   UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />[diagramy aktywności UML -   : wytyczne](../modeling/uml-activity-diagrams-guidelines.md)|Kroki, które należy wykonać, gdy klient chce napisać przegląd restauracji|
|*Diagram klas (UML)*<br /><br /> Zobacz:<br /><br /> -   [diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />[diagramy klas UML -   : wytyczne](../modeling/uml-class-diagrams-guidelines.md)|Dane wymagane do przechowania przeglądu|

 Na przykład poniższy diagram przypadków użycia obejmuje nowy przypadek użycia "Write Recenzja", który reprezentuje nowe wymaganie. Jest on wyróżniony w kolorze pomarańczowym na diagramie, aby ułatwić identyfikację:

 ![Diagram przypadków użycia UML](../modeling/media/uml-writerev.png "UML_WriteRev")

 **Diagram przypadków użycia UML**

 Poniższy diagram aktywności zawiera nowe elementy w kolorze pomarańczowym do opisania przepływu kroków w nowym przypadku użycia:

 ![Diagram aktywności UML](../modeling/media/uml-writereview.png "UML_WriteReview")

 **Diagram aktywności UML**

 Poniższy diagram klas zawiera nową klasę przeglądu i jej relacje z innymi klasami, dzięki czemu zespoły mogą omawiać szczegóły. Zwróć uwagę, że klient i restauracji mogą mieć wiele recenzji:

 ![Diagram klas UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **Diagram klas UML**

### <a name="CreatingTests"></a>Tworzenie testów z modeli
 Oba zespoły zgadzają się, że potrzebują pełnego zestawu testów dla systemu i jego składników przed wprowadzeniem jakichkolwiek zmian. Lucerny z wyspecjalizowanym zespołem, który przeprowadza testowanie na poziomie składników. Ponownie korzystają z testów utworzonych w ramach obiadu teraz i struktury tych testów przy użyciu diagramów UML:

- Każdy przypadek użycia jest reprezentowany przez jeden lub kilka testów. Elementy na diagramie przypadków użycia łączą się z elementami roboczymi przypadek testowy w Team Foundation Server.

- Każdy przepływ na diagramie aktywności lub diagramie sekwencji na poziomie systemu jest połączony z jednym testem co najmniej. Zespół testowy systematycznie sprawdza, czy wszystkie możliwe ścieżki są testowane za pomocą diagramu aktywności.

- Terminy używane do opisywania testów są oparte na warunkach zdefiniowanych przez diagramy przypadków użycia, klas i działań.

  Wraz ze zmianą wymagań i diagramy są aktualizowane w celu odzwierciedlenia tych zmian, testy również są aktualizowane. Wymaganie jest uznawane za spełnione tylko wtedy, gdy testy zostały zakończone pomyślnie. Gdy jest to możliwe lub praktyczne, testy są definiowane i oparte na diagramach UML przed rozpoczęciem implementacji.

  Zobacz:

- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)

- [Weryfikacja modelu UML](../modeling/validate-your-uml-model.md)

### <a name="DeterminingChanges"></a>Identyfikowanie zmian w istniejącym systemie
 Kolacja teraz musi oszacować koszt zaspokajania nowego wymagania. Jest to zależne od tego, jak bardzo zmiana wpłynie na inne części systemu. Aby ułatwić im zrozumienie, jeden z obiadów teraz tworzy te mapy i diagramy z istniejącego kodu:

|**Mapa lub diagram**|**Pokazując**|
|------------------------|---------------|
|*Mapa kodu*<br /><br /> Zobacz:<br /><br /> -   [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [przeglądać i zmieniać rozmieszczenie map kodu](../modeling/browse-and-rearrange-code-maps.md)<br />-   [dostosować mapy kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Zależności i inne relacje w kodzie.<br /><br /> Na przykład możesz zacząć od obiadu, przeglądając mapy kodu zestawu, aby zapoznać się z omówieniem zestawów i ich zależnościami. Mogą przechodzić do szczegółów map, aby eksplorować przestrzenie nazw i klasy w tych zestawach.<br /><br /> Na obiad teraz można również tworzyć mapy umożliwiające Eksplorowanie określonych obszarów i innych rodzajów relacji w kodzie. Używają oni Eksplorator rozwiązań, aby znajdować i wybierać obszary i relacje, które je interesują.|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie|

 Na przykład deweloper tworzy mapę kodu. Dostosowuje swój zakres, aby skoncentrować się na obszarach, na które wpłynie nowy scenariusz. Obszary te są wybrane i wyróżnione na mapie:

 ![Wykres zależności przestrzeni nazw](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Mapa kodu przestrzeni nazw**

 Deweloper rozszerza wybrane przestrzenie nazw, aby zobaczyć ich klasy, metody i relacje:

 ![Wykres zależności rozwiniętej przestrzeni nazw](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Rozwinięta Mapa kodu przestrzeni nazw z widocznymi łączami między grupami**

 Deweloper bada kod w celu znalezienia odpowiednich klas i metod. Aby zobaczyć efekty każdej zmiany w miarę ich tworzenia, należy ponownie wygenerować mapy kodu po każdej zmianie. Zobacz [wizualizowanie kodu](../modeling/visualize-code.md).

 Aby opisać zmiany w innych częściach systemu, takich jak składniki lub interakcje, zespół może narysować te elementy w tablicach. Mogą również narysować następujące diagramy w programie Visual Studio, aby szczegóły mogły być przechwytywane, zarządzane i zrozumiałe dla obu zespołów:

|**Schematów**|**Szczegół**|
|------------------|-------------------|
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> [diagramy działań -   UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />[diagramy aktywności UML -   : wytyczne](../modeling/uml-activity-diagrams-guidelines.md)|Przepływ kroków, które występują, gdy system wykryje, że klient ponownie umieści zamówienie z restauracji, monitując klienta o napisanie przeglądu.|
|*Diagram klas (UML)*<br /><br /> Zobacz:<br /><br /> -   [diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />[diagramy klas UML -   : wytyczne](../modeling/uml-class-diagrams-guidelines.md)|Klasy logiczne i ich relacje. Na przykład nowa klasa jest dodawana do opisywania **przeglądu** i jego relacji z innymi jednostkami, takimi jak **restauracja**, **menu**i **Klient**.<br /><br /> Aby skojarzyć przeglądy z klientem, system musi przechowywać szczegóły klienta. Diagram klas UML może pomóc w wyjaśnieniu tych szczegółów.|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie.|
|*Diagram składników (UML)*<br /><br /> Zobacz:<br /><br /> -   [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />[diagramy składników UML -   : wytyczne](../modeling/uml-component-diagrams-guidelines.md)|Części wysokiego poziomu systemu, takie jak witryna obiadu teraz i ich interfejsy. Te interfejsy definiują, jak składniki współdziałają ze sobą za pomocą metod lub usług, które zapewniają i wykorzystują.|
|*Diagram sekwencji (UML)*<br /><br /> Zobacz:<br /><br /> [diagramy sekwencji -   UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />[diagramy sekwencji -   UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md)|Sekwencja interakcji między wystąpieniami.|

 Na przykład poniższy diagram składników przedstawia nowy składnik, który jest częścią składnika witryny sieci Web obiad teraz. Składnik ReviewProcessing obsługuje funkcje tworzenia przeglądów i pojawia się w kolorze pomarańczowym:

 ![Diagram składników UML](../modeling/media/uml-internal.png "UML_Internal")

 **Diagram składników UML**

 Poniższy diagram sekwencji przedstawia sekwencję interakcji występujących, gdy witryna sieci Web obiady teraz sprawdzi, czy klient zamówił z restauracji przed. Jeśli ta wartość jest równa true, prosi klienta o utworzenie przeglądu, który jest wysyłany do restauracji i publikowany przez witrynę sieci Web:

 ![Diagram sekwencji UML](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **Diagram sekwencji UML**

### <a name="ValidatingCode"></a>Zachowywanie spójności kodu w projekcie
 Teraz należy upewnić się, że zaktualizowany kod pozostaje zgodny z projektem. Tworzą diagramy warstwowe opisujące warstwy funkcji w systemie, określają dozwolone zależności między nimi i kojarzą artefakty rozwiązań z tymi warstwami.

|**4b**|**Szczegół**|
|-----------------|-------------------|
|*Diagram warstwowy*<br /><br /> Zobacz:<br /><br /> -   [tworzenia diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy warstwowe: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [diagramy warstwowe: wytyczne](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikuj kod przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|Logiczna architektura kodu.<br /><br /> Diagram warstwowy organizuje i mapuje artefakty w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie do grup abstrakcyjnych o nazwie *warstwy*. Te warstwy identyfikują role, zadania lub funkcje, które te artefakty pełnią w systemie.<br /><br /> Diagramy warstw są przydatne do opisywania zamierzonego projektu systemu i weryfikowania rozwoju kodu względem tego projektu.<br /><br /> Aby utworzyć warstwy, przeciągnij elementy z Eksplorator rozwiązań, map kodu, Widok klasy i Przeglądarka obiektów. Aby narysować nowe warstwy, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu.<br /><br /> Aby wyświetlić istniejące zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu warstwy, a następnie kliknij polecenie **Generuj zależności**. Aby określić zamierzone zależności, narysuj nowe zależności.|

 Na przykład poniższy diagram warstwowy opisuje zależności między warstwami i liczbą artefaktów, które są skojarzone z poszczególnymi warstwami:

 ![Diagram warstwowy zintegrowanego systemu płatności](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagram warstwowy**

 Aby upewnić się, że konflikty z projektem nie wystąpią podczas tworzenia kodu, zespoły korzystają z walidacji warstwy w kompilacjach, które są uruchamiane w programie Team Foundation Build. Tworzy również niestandardowe zadanie programu MSBuild, aby wymagać weryfikacji warstwy w ramach operacji zaewidencjonowania. Wykorzystują one raporty kompilacji do zbierania błędów walidacji.

 Zobacz:

- [Zdefiniuj proces kompilacji](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Użyj procesu kompilacji ewidencjonowania warunkowego do walidacji zmian](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Dostosuj szablon procesu kompilacji](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="GeneralTips"></a>Ogólne porady dotyczące tworzenia i używania modeli

- Większość diagramów składa się z węzłów, które są połączone liniami. Dla każdego typu diagramu Przybornik zawiera różne rodzaje węzłów i linii.

   Aby otworzyć przybornik, w menu **Widok** kliknij polecenie **Przybornik**.

- Aby utworzyć węzeł, przeciągnij go z przybornika do diagramu. Niektóre rodzaje węzłów muszą być przeciągane do istniejących węzłów. Na przykład na diagramie składników należy dodać nowy port do istniejącego składnika.

- Aby utworzyć wiersz lub połączenie, kliknij odpowiednie narzędzie w przyborniku, kliknij węzeł źródłowy, a następnie kliknij węzeł docelowy. Niektóre linie mogą być tworzone tylko między pewnymi rodzajami węzłów. Gdy przesuwasz wskaźnik nad możliwym źródłem lub obiektem docelowym, wskaźnik wskazuje, czy można utworzyć połączenie.

- Podczas tworzenia elementów na diagramach UML są one również dodawane do wspólnego modelu. Diagramy UML w projekcie modelowania są widokami tego modelu. Elementy na diagramie warstwy są częścią projektu modelowania, nawet jeśli nie są one przechowywane we wspólnym modelu.

   Aby wyświetlić model, w menu **Architektura** wskaż pozycję **Windows**, a następnie kliknij pozycję **Eksplorator modelu UML**.

- W niektórych przypadkach można przeciągnąć niektóre elementy z **Eksploratora modelu UML** do diagramu UML. Niektóre elementy w ramach tego samego modelu mogą być używane na wielu lub różnych diagramach w celu wyświetlenia alternatywnych widoków architektury. Na przykład można przeciągnąć składnik do innego diagramu składników lub do diagramu sekwencji, który ma być używany jako aktor.

- Program Visual Studio obsługuje język UML 2.1.2. To omówienie zawiera opis głównych funkcji diagramów UML w tej wersji, ale istnieje wiele książek, które szczegółowo omawiają UML i jego użycie.

  Zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md).

### <a name="PlanningTracking"></a>Planowanie i śledzenie pracy
 Diagramy modelowania programu Visual Studio są zintegrowane z Team Foundation Server, dzięki czemu można łatwiej planować i zarządzać nimi. Oba zespoły używają modeli do identyfikowania przypadków testowych i zadań programistycznych oraz szacowania ich pracy. Lucerny tworzy i łączy Team Foundation Server elementów roboczych z elementami modelu, takimi jak przypadki użycia lub składniki. Ułatwia to monitorowanie postępów i śledzenie ich pracy z powrotem do wymagań użytkowników. Dzięki temu można upewnić się, że ich zmiany będą nadal spełniały te wymagania.

 W miarę postępów prac zespoły aktualizują swoje elementy robocze, aby odzwierciedlały czas spędzony na wykonywaniu zadań. Umożliwiają również monitorowanie i zgłaszanie stanu pracy przy użyciu następujących funkcji Team Foundation Server:

- Codzienne *raporty postępu* pokazujące, czy ukończyją planowaną pracę w oczekiwanym czasie. Generują one inne podobne raporty z Team Foundation Server, aby śledzić postęp błędów.

- *Arkusz iteracji* , który używa programu Microsoft Excel, aby pomóc zespołowi monitorować i zrównoważyć obciążenie między jego członkami. Ten arkusz jest połączony z Team Foundation Server i umożliwia skoncentrowanie się na dyskusjach podczas zwykłych spotkań z postępem.

- *Pulpit nawigacyjny programistyczny* , który używa programu Office Project do informowania zespołu o ważnych informacjach o projekcie.

  Zobacz:

- [Śledzenie pracy przy użyciu Visual Studio Team Services lub Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md)

- [Wykresy, pulpity nawigacyjne i raporty dla programu Visual Studio ALM](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Tworzenie zaległości i zadań przy użyciu projektu](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="TestValidateCheckInCode"></a>Testowanie, sprawdzanie poprawności i ewidencjonowanie kodu
 Gdy zespoły ukończyją każde zadanie, sprawdzają swój kod w kontroli wersji programu Team Foundation i odbierają przypomnienia z Team Foundation Server, jeśli zapomnieć. Zanim Team Foundation Server zaakceptuje ich zaewidencjonowania, zespoły uruchamiają testy jednostkowe i sprawdzanie poprawności warstwy w celu zweryfikowania kodu względem ich przypadków testowych i projektu. Używają Team Foundation Server do uruchamiania kompilacji, zautomatyzowanych testów jednostkowych i regularnego sprawdzania poprawności warstwy. Pomaga to upewnić się, że kod spełnia następujące kryteria:

- Działa.

- Nie powoduje przerwania działania kodu.

- Nie powoduje konfliktu z projektem.

  Obiad ma teraz dużą kolekcję zautomatyzowanych testów, które mogą być ponownie używane przez Lucerny, ponieważ niemal wszystkie nadal mają zastosowanie. W ramach tych testów można także skompilować te testy i dodać nowe, aby uwzględnić nowe funkcje. Oba te programy również używają programu Visual Studio do uruchamiania testów ręcznych.

  Aby upewnić się, że kod jest zgodny z projektem, zespoły konfigurują kompilacje w programie Team Foundation Build, aby uwzględnić walidację warstwy. Jeśli wystąpią konflikty, raport zostanie wygenerowany ze szczegółowymi informacjami.

  Zobacz:

- [Testowanie aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)

- [Użyj kontroli wersji](https://go.microsoft.com/fwlink/?LinkID=525605)

- [Kompilowanie aplikacji](/azure/devops/pipelines/index)

## <a name="UpdatingSystem"></a>Aktualizowanie systemu przy użyciu wizualizacji i modelowania
 Lucerny i obiady teraz muszą zintegrować swoje systemy płatności. W poniższych sekcjach przedstawiono diagramy modelowania w programie Visual Studio, które ułatwiają wykonywanie tego zadania:

- [Informacje o wymaganiach użytkownika: diagramy przypadków użycia](#UnderstandUseCases)

- [Poznaj proces biznesowy: diagramy aktywności](#UnderstandActivities)

- [Opisz strukturę systemu: diagramy składników](#DescribeComponents)

- [Opisywanie interakcji: diagramy sekwencji](#DescribeSequence)

- [Wizualizowanie istniejącego kodu: mapy kodu](#VisualizeCode)

- [Definiowanie słownika typów: diagramy klas](#DefineClasses)

- [Opisywanie architektury logicznej: diagramy warstwowe](#DescribeLayers)

  Zobacz:

- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)

- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)

### <a name="UnderstandUseCases"></a>Informacje o wymaganiach użytkownika: diagramy przypadków użycia
 Diagramy przypadków użycia podsumowują działania obsługiwane przez system i wykonujących te działania. Lucerny z użyciem diagramu przypadków użycia, aby poznać następujące informacje o systemie obiad teraz:

- Klienci tworzą zamówienia.

- Restauracje otrzymują zamówienia.

- Brama zewnętrznego agenta rozliczeniowego płatności, której system płatności jest używany do sprawdzania poprawności płatności, jest poza zakresem dla witryny sieci Web.

  Diagram pokazuje również, jak niektóre główne przypadki użycia są podzielone na mniejsze przypadki użycia. Lucerny, która chce korzystać z własnego systemu płatności. Wyróżniają one przypadek użycia płatności procesu w innym kolorze, aby wskazać, że wymaga wprowadzenia zmian:

  ![Wyróżnianie procesu płatności na diagramie przypadku użycia](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Wyróżnianie procesu płatności na diagramie przypadków użycia**

  Jeśli czas projektowania był krótki, zespół może omówić, czy chcą, aby klienci płaciły Restauracje bezpośrednio. Aby to pokazać, zastąpi przypadek użycia płatności procesu, który jest poza granicą systemu na obiad teraz. Następnie mogą połączyć klienta bezpośrednio z restauracji, wskazując na to, że obiad będzie teraz przetwarzał tylko zamówienia:

  ![Przeznaczanie zakresu w restauracji w ramach diagramu przypadków użycia](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Przeznaczanie zakresu w restauracji w ramach diagramu przypadków użycia**

  Zobacz:

- [Diagramy przypadków użycia UML: informacje](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Rysowanie diagramu przypadków użycia
 Diagram przypadków użycia ma następujące główne funkcje:

- *Aktory* reprezentują role odgrywane przez osoby, organizacje, maszyny lub systemy oprogramowania. Na przykład klient, restauracji i obiad teraz system płatności są uczestnikami.

- *Przypadki użycia* reprezentują interakcje między aktorami a systemem w trakcie opracowywania.  Mogą one reprezentować dowolną skalę interakcji z pojedynczego kliknięcia myszą lub komunikatem do przedłużonej liczby dni.

- *Skojarzenia* łączy aktorów z przypadkami użycia.

- Większy przypadek użycia może *zawierać* mniejsze, na przykład Utwórz zamówienie obejmuje wybór restauracji. Możesz *rozszerzyć* przypadek użycia, który dodaje cele i kroki do rozszerzonego przypadku użycia, aby wskazać, że przypadek użycia występuje tylko w określonych warunkach. Przypadki użycia mogą również dziedziczyć od siebie nawzajem.

- *Podsystem* reprezentuje system oprogramowania, który jest opracowywany lub jeden z jego składników. Jest to duże pole, które zawiera przypadki użycia. Diagram przypadków użycia wyjaśnia, co znajduje się wewnątrz lub na zewnątrz granicy podsystemu. Aby wskazać, że użytkownik musi wykonać określone cele w inny sposób, narysuj te przypadki użycia poza granicą podsystemu.

- *Artefakty* umożliwiają łączenie elementów na diagramie z innymi diagramami lub dokumentami.

  Zobacz:

- [Diagramy przypadków użycia UML: informacje](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Podsumowanie: zalety diagramów przypadków użycia
 Diagramy przypadków użycia ułatwiają wizualizację:

- Działania obsługiwane przez system lub nie obsługują

- Osoby i systemy zewnętrzne, które wykonują te działania

- Główne składniki systemu, które obsługują poszczególne działania, które można reprezentować jako podsystemy zagnieżdżone w systemie nadrzędnym

- Jak przypadek użycia może być podzielony na mniejsze lub Wariacje

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Szczegół**|
|-----------------|-------------------|
|Diagramu aktywności|Przepływ kroków w przypadku użycia i tych, którzy wykonują te kroki w tym przypadku użycia.<br /><br /> Nazwy przypadków użycia często duplikują kroki na diagramie aktywności. Diagramy aktywności obsługują elementy, takie jak decyzje, scalenia, dane wejściowe i wyjściowe, przepływy współbieżne i tak dalej.<br /><br /> Zobacz:<br /><br /> [diagramy działań -   UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />[diagramy aktywności UML -   : wytyczne](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagramów sekwencji|Sekwencja interakcji między uczestnikami w przypadku użycia.<br /><br /> Zobacz:<br /><br /> [diagramy sekwencji -   UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />[diagramy sekwencji -   UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagram klas (UML)|Jednostki lub typy, które uczestniczą w przypadku użycia.<br /><br /> Zobacz:<br /><br /> -   [diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />[diagramy klas UML -   : wytyczne](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="UnderstandActivities"></a>Poznaj proces biznesowy: diagramy aktywności
 Diagramy aktywności opisują przepływ kroków w procesie biznesowym i zapewniają prosty sposób komunikowania się z przepływem pracy. Projekt programistyczny może mieć wiele diagramów aktywności. Zwykle działanie obejmuje wszystkie akcje wynikające z jednej akcji zewnętrznej, takie jak porządkowanie posiłku, aktualizowanie menu lub Dodawanie nowej restauracji do firmy. Działanie może również opisywać szczegóły złożonej akcji.

 Program lucerny aktualizuje Poniższy diagram aktywności, aby pokazać, że w ramach procesu płatności w ramach restauracji zostanie wyświetlona płatność i napłacina restauracja Zastępują one system płatności z tytułu obiadu teraz z systemem płatności z lucerny, jako wyróżniony:

 ![System płatności z lucerny na diagramie aktywności](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Zastępowanie systemu płatności na obiad teraz na diagramie aktywności**

 Zaktualizowany diagram ułatwia prezentowanie i obiad, a teraz przedstawia wizualizację, w której system płatności z lucerny mieści się w procesie biznesowym. W tej wersji Komentarze są używane do identyfikowania ról, które wykonują kroki. Wiersze są używane do tworzenia *torów*, które organizują kroki według roli.

 Zespoły mogą również rozważyć przedyskutowanie alternatywnej historii, w której klient płaci restauracji, a nie po ich dostarczeniu. Spowoduje to utworzenie różnych wymagań dla systemu oprogramowania.

 Wcześniej obiad teraz przyniesieł te diagramy do tablicy lub w programie PowerPoint. Teraz używają one również programu Visual Studio do rysowania tych diagramów, aby oba zespoły mogły przechwytywać i zrozumieć szczegóły oraz zarządzać nimi.

 Zobacz:

- [Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)

- [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Rysowanie diagramu aktywności
 Diagram aktywności ma następujące główne funkcje:

- *Początkowy węzeł* , który wskazuje na pierwszą akcję działania.

   Diagram powinien zawsze mieć jeden z tych węzłów.

- *Akcje* opisujące kroki, w których użytkownik lub oprogramowanie wykonuje zadanie.

- *Przepływy sterowania* , które pokazują przepływ między akcjami.

- *Węzły decyzyjne* , które reprezentują gałęzie warunkowe w przepływie.

- *Węzły rozwidlenia* dzielące pojedyncze przepływy na współbieżne przepływy.

- *Końcowe węzły działania* , które pokazują koniec działania.

   Chociaż te węzły są opcjonalne, warto uwzględnić je na diagramie, aby pokazać, gdzie działa działanie.

  Zobacz:

- [Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)

- [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Podsumowanie: zalety diagramów aktywności
 Diagramy aktywności ułatwiają wizualizowanie i opisywanie przepływu sterowania i informacji między działaniami firmy, systemu lub programu. Jest to prosty i przydatny sposób opisywania przepływu pracy podczas komunikowania się z innymi osobami.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Opis**|
|-----------------|---------------------|
|Diagramów przypadków użycia|Podsumuj działania wykonywane przez poszczególne aktorów.<br /><br /> Zobacz:<br /><br /> -   [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramy przypadków użycia -   UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagramów składników|Wizualizuj system jako kolekcję części wielokrotnego użytku, które zapewniają lub zużywają zachowanie za pomocą dobrze zdefiniowanego zestawu interfejsów.<br /><br /> Zobacz:<br /><br /> -   [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />[diagramy składników UML -   : wytyczne](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="DescribeComponents"></a>Opisz strukturę systemu: diagramy składników
 Diagramy składników opisują system jako zbiór wyodrębnionych części, które udostępniają lub zużywają działanie za pomocą dobrze zdefiniowanego zestawu interfejsów. Części mogą być w dowolnej skali i mogą łączyć się w dowolny sposób.

 Aby ułatwić podlucerny i obiad, teraz Wizualizuj i omawiać składniki systemu oraz ich interfejsy, tworzy następujące diagramy składników:

 ![Składniki zewnętrzne w systemie płatności](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Składniki systemu płatności na obiad teraz**

 Ten diagram przedstawia różne typy składników i ich *zależności*. Na przykład zarówno witryna sieci Web obiadu teraz, jak i system płatności z lucerny, wymagają od bramy zewnętrznego agenta rozliczeniowego płatności do sprawdzania poprawności płatności. Strzałki między składnikami reprezentują zależności wskazujące, które składniki wymagają funkcjonalności innych składników.

 Aby można było korzystać z systemu płatności z lucerny, należy zaktualizować witrynę sieci Web obiad teraz, aby używać interfejsów PaymentApproval i PayableInsertion w systemie płatności z lucerny.

 Na poniższym diagramie przedstawiono określoną konfigurację składników dla witryny sieci Web obiadu teraz. Ta konfiguracja wskazuje, że każde wystąpienie witryny sieci Web składa się z czterech *części*:

- CustomerProcessing

- OrderProcessing

- ReviewProcessing

- PaymentProcessing

  Te części są wystąpieniami określonych typów składników i są połączone w następujący sposób:

  ![Składniki w ramach obiadu teraz witryny sieci Web](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Składniki w witrynie obiad teraz w sieci Web**

  Witryna sieci Web obiady teraz deleguje jej zachowanie do tych części, które obsługują funkcje witryny sieci Web. Strzałki między składnikiem nadrzędnym i jego składnikami członkowskimi pokazują *delegowania* wskazujące, które części obsługują komunikaty, które element nadrzędny odbiera lub wysyła za pomocą jego interfejsów.

  W tej konfiguracji składnik PaymentProcessing przetwarza płatności klientów. W związku z tym należy je zaktualizować w celu integracji z systemem płatności z lucerny. W innych scenariuszach wiele wystąpień typu składnika może istnieć w tym samym składniku nadrzędnym.

  Zobacz:

- [Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)

- [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Rysowanie diagramu składników
 Diagram składników ma następujące główne funkcje:

- *Składniki* reprezentujące wyodrębnione fragmenty funkcji systemu.

- *Podane porty interfejsu* reprezentujące grupy komunikatów lub wywołania, które składniki implementują i są używane przez inne składniki lub systemy zewnętrzne.

- *Wymagane porty interfejsu* reprezentujące grupy komunikatów lub wywołania, które składniki wysyłają do innych składników lub systemów zewnętrznych. Ten rodzaj portu opisuje operacje, których składnik nie oczekuje od innych składników lub systemów zewnętrznych.

- *Części* są członkami składników i są zwykle wystąpieniami innych składników. Część jest częścią wewnętrznego projektu składnika nadrzędnego.

- *Zależności* wskazujące składniki wymagają funkcjonalności innych składników programu.

- *Delegacje* wskazujące części składnika obsługują komunikaty wysyłane z lub odbierane przez składnik nadrzędny.

  Zobacz:

- [Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)

- [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Podsumowanie: zalety diagramów składników
 Diagramy składników ułatwiają wizualizację:

- System jako zbiór wyodrębnionych części niezależnie od ich języka lub stylu implementacji.

- Składniki ze dobrze zdefiniowanymi interfejsami, dzięki czemu projekt jest łatwiejszy do zrozumienia i zaktualizowania, gdy wymagania zmieniają się.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Opis**|
|-----------------|---------------------|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby zidentyfikować kandydatów dla składników, Utwórz mapę kodu i pogrupuj elementy według ich funkcji w systemie.<br /><br /> Zobacz:<br /><br /> -   [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)|
|Diagramów sekwencji|Wizualizuj sekwencję interakcji między składnikami lub częściami wewnątrz składnika.<br /><br /> Aby utworzyć linię życia na diagramie sekwencji z poziomu składnika, kliknij prawym przyciskiem myszy składnik, a następnie kliknij polecenie **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> [diagramy sekwencji -   UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />[diagramy sekwencji -   UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagram klas (UML)|Zdefiniuj interfejsy dla dostarczonych lub wymaganych portów oraz klasy, które implementują funkcje składników programu.<br /><br /> Zobacz:<br /><br /> -   [diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />[diagramy klas UML -   : wytyczne](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram warstwowy|Opisz logiczną architekturę systemu, która odnosi się do składników. Użyj walidacji warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> -   [tworzenia diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy warstwowe: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [diagramy warstwowe: wytyczne](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikuj kod przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|
|Diagramu aktywności|Wizualizuj wewnętrzne przetwarzanie wykonywane przez składniki w odpowiedzi na komunikaty przychodzące.<br /><br /> Zobacz:<br /><br /> [diagramy działań -   UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />[diagramy aktywności UML -   : wytyczne](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="VisualizeCode"></a>Wizualizowanie istniejącego kodu: mapy kodu
 Mapy kodu pokazują bieżącą organizację i relacje w kodzie. Elementy są reprezentowane przez *węzły* na mapie, a relacje są reprezentowane przez *linki*. Mapy kodu mogą pomóc w wykonywaniu następujących rodzajów zadań:

- Eksploruj nieznany kod.

- Zapoznaj się z miejscem i sposobem, w jaki proponowana zmiana może mieć wpływ na istniejący kod.

- Znajdź obszary złożoności, naturalnych warstw lub wzorców lub inne obszary, które mogą korzystać z poprawy.

  Na przykład obiad będzie teraz musiał oszacować koszt aktualizowania składnika PaymentProcessing. Jest to zależne od tego, jak bardzo zmiana wpłynie na inne części systemu. Aby ułatwić im zrozumienie tego, jeden z obiadów obecnie deweloperów generuje mapy kodu z kodu i dostosowuje fokus zakresu w obszarach, na które mogą mieć wpływ zmiany.

  Poniższa mapa przedstawia zależności między klasą PaymentProcessing i innymi częściami systemu obiadu teraz, które zostały wyświetlone:

  ![Wykres zależności dla systemu płatności z obiadem teraz](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Mapa kodu dla systemu płatności z obiadem teraz**

  Deweloper eksploruje mapę przez rozwijanie klasy PaymentProcessing i wybieranie jej elementów członkowskich, aby zobaczyć obszary, które mogą mieć wpływ:

  ![Metody wewnątrz PaymentProcessing i zależności](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **Metody wewnątrz klasy PaymentProcessing i ich zależności**

  Generują następujące mapy dla systemu płatności z lucerny, aby sprawdzić jej klasy, metody i zależności. Zespół widzi, że system lucerny, może również wymagać pracy w celu współdziałania z innymi częściami obiadu:

  ![Wykres zależności dla systemu płatności z lucerny](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Mapa kodu dla systemu płatności z lucerny**

  Oba zespoły współpracują ze sobą, aby określić zmiany, które są wymagane do integracji dwóch systemów. Użytkownik zdecyduje się na refaktoryzację pewnego kodu, aby ułatwić jego aktualizację. Klasa PaymentApprover zostanie przeniesiona do przestrzeni nazw DinnerNow. Business i będzie wymagała nowych metod. Klasy obiadu teraz, które obsługują transakcje, będą miały własny obszar nazw. Zespoły tworzą i wykorzystują elementy robocze do planowania, organizowania i śledzenia pracy. Łączą elementy robocze z elementami modelu, w których są użyteczne.

  Po rozpoczęciu restrukturyzacji kodu zespoły generują nową mapę kodu, aby wyświetlić zaktualizowaną strukturę i relacje:

  ![Wykres zależności z rezorganizowanym kodem](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **Mapa kodu z rezorganizowanym kodem**

  Ta mapa pokazuje, że Klasa PaymentApprover znajduje się teraz w przestrzeni nazw DinnerNow. Business i ma kilka nowych metod. Klasy transakcji obiadu teraz mają swoją własną przestrzeń nazw PaymentSystem, co ułatwia objęcie tego kodu w późniejszym czasie.

#### <a name="creating-a-code-map"></a>Tworzenie mapy kodu

- Aby uzyskać szybki przegląd kodu źródłowego, wykonaj następujące kroki, aby wygenerować mapę kodu:

     W menu **Architektura** kliknij polecenie **Generuj mapę kodu dla rozwiązania**.

     Aby zapoznać się z krótkim omówieniem skompilowanego kodu, Utwórz pustą mapę kodu, a następnie przeciągnij pliki zestawu lub pliki binarne na powierzchnię mapy.

- Aby poznać określony kod lub elementy rozwiązania, użyj Eksplorator rozwiązań, aby zaznaczyć elementy i relacje, które chcesz wizualizować. Następnie można wygenerować nową mapę lub dodać wybrane elementy do istniejącej mapy. Zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

- Aby ułatwić Eksplorowanie mapy, należy zmienić układ tak, aby odpowiadał rodzajom zadań, które chcesz wykonać.

     Na przykład w celu wizualizowania warstw w kodzie wybierz układ drzewa. Zobacz [przeglądanie i zmiana kolejności map kodu](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Podsumowanie: zalety map kodu
 Mapy kodu pomagają Ci:

- Poznaj organizację i relacje w istniejącym kodzie.

- Zidentyfikuj obszary, na które może mieć wpływ proponowana zmiana.

- Znajdź obszary złożoności, wzorce, warstwy lub inne obszary, które można ulepszyć, aby ułatwić przechowywanie, zmianę i ponowne użycie kodu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Szczegół**|
|-----------------|-------------------|
|Diagram warstwowy|Logiczna architektura systemu. Użyj walidacji warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Aby ułatwić identyfikację istniejących warstw lub zamierzonych warstw, Utwórz mapę kodu i pogrupuj powiązane elementy. Aby utworzyć diagram warstwowy, zobacz:<br /><br /> -   [tworzenia diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy warstwowe: wytyczne](../modeling/layer-diagrams-guidelines.md)|
|Diagramów składników|Składniki, ich interfejsy i ich relacje.<br /><br /> Aby ułatwić identyfikację składników, należy utworzyć mapę kodu i zgrupować elementy według ich funkcji w systemie.<br /><br /> Zobacz:<br /><br /> -   [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />[diagramy składników UML -   : wytyczne](../modeling/uml-component-diagrams-guidelines.md)|
|Diagram klas (UML)|Klasy, ich atrybuty i operacje oraz ich relacje.<br /><br /> Aby ułatwić identyfikację tych elementów, należy utworzyć diagram klas UML, który pokazuje te elementy.<br /><br /> Zobacz:<br /><br /> -   [diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />[diagramy klas UML -   : wytyczne](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram klas (oparty na kodzie)|Istniejące klasy w kodzie dla określonego projektu.<br /><br /> Aby wizualizować i modyfikować istniejącą klasę w kodzie, użyj Projektant klas.<br /><br /> Zobacz [jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="DescribeSequence"></a>Opisywanie interakcji: diagramy sekwencji
 Diagramy sekwencji opisują serię interakcji między częściami systemu. Części mogą być w dowolnej skali. Na przykład mogą przedziały od poszczególnych obiektów w programie do dużych podsystemów lub aktorów zewnętrznych. Interakcje mogą mieć dowolną skalę i typ. Na przykład mogą one obejmować zakres od poszczególnych komunikatów do rozszerzonych transakcji i mogą być wywołaniami funkcji lub komunikatami usługi sieci Web.

 Aby pomóc z lucerny i obiadem, teraz opiszemy i omawiamy kroki w przypadku użycia płatności procesu, tworzą Poniższy diagram sekwencji na podstawie diagramu składników. Linie życia odzwierciedlają składnik witryny sieci Web obiadu teraz i jej części. Komunikaty wyświetlane między liniami życia są zgodne z połączeniami na diagramach składników:

 ![Diagram sekwencji dla przypadku użycia płatności procesu](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Diagram sekwencji dla przypadku użycia płatności procesu**

 Diagram sekwencji pokazuje, że gdy klient tworzy zamówienie, witryna sieci Web obiad teraz wywołuje ProcessOrder na wystąpieniu OrderProcessing. Następnie OrderProcessing wywołuje ProcessPayment na PaymentProcessing. Ten proces jest kontynuowany do momentu potwierdzenia płatności przez bramę zewnętrznego procesora płatności. Dopiero po wykonaniu tej kontroli powrócisz do witryny sieci Web obiad teraz.

 W ramach tego okresu należy oszacować koszt aktualizacji systemu płatności w celu integracji z systemem z obiadem teraz. Aby ułatwić im zrozumienie tego, mogą również tworzyć mapy kodu w celu wizualizacji kodu, którego to dotyczy.

 Zobacz:

- [Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)

- [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Rysowanie diagramu sekwencji
 Diagram sekwencji ma następujące główne funkcje:

- Pionowe *linie życia* reprezentują aktorów lub wystąpienia obiektów oprogramowania.

   Aby dodać symbol aktora, który wskazuje, że uczestnik jest spoza systemu w trakcie opracowywania, kliknij linię życia. W oknie **Właściwości** Ustaw **aktor** na **wartość true**. Jeśli okno **Właściwości** nie jest otwarte, naciśnij klawisz **F4**.

- *Komunikaty* poziome reprezentują wywołania metod, wiadomości usługi sieci Web lub inną komunikację. *Wystąpienia wykonywania* to prostokąty cieniowane w pionie, które są wyświetlane na liniach życia i reprezentują okresy, w których obiekty odbierają wywołania.

- Podczas *synchronicznego* komunikatu obiekt nadawcy czeka na kontrolkę, która <\<zwracać > > tak jak w przypadku zwykłego wywołania funkcji. W komunikacie *asynchronicznym* nadawca może natychmiast kontynuować pracę.

- Użyj <\<utworzyć > > komunikatów, aby wskazać konstrukcję obiektów przez inne obiekty. Powinien to być pierwszy komunikat wysyłany do obiektu.

  Zobacz:

- [Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)

- [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Podsumowanie: zalety diagramów sekwencji
 Diagramy sekwencji ułatwiają wizualizację:

- Przepływ sterowania, który przesyła między aktorami lub obiektami podczas wykonywania przypadku użycia.

- Implementacja wywołania metody lub komunikatu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Opis**|
|-----------------|---------------------|
|Diagram klas (UML)|Zdefiniuj klasy reprezentowane przez linie życia oraz parametry i wartości zwracane, które są używane w komunikatach przesyłanych między liniami życia.<br /><br /> Aby utworzyć klasę z linii życia, kliknij prawym przyciskiem myszy linię życia, a następnie kliknij pozycję **Utwórz klasę** lub **Utwórz interfejs**. Aby utworzyć linię życia na podstawie typu na diagramie klasy, kliknij prawym przyciskiem myszy typ, a następnie kliknij polecenie **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)<br />[diagramy klas UML -   : wytyczne](../modeling/uml-class-diagrams-guidelines.md)|
|Diagramów składników|Opisz składniki reprezentowane przez linie życia oraz interfejsy, które zapewniają i wykorzystują zachowanie reprezentowane przez komunikaty.<br /><br /> Aby utworzyć linię życia na podstawie diagramu składnika, kliknij prawym przyciskiem myszy składnik, a następnie kliknij polecenie **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />[diagramy składników UML -   : wytyczne](../modeling/uml-component-diagrams-guidelines.md)|
|Diagramów przypadków użycia|Podsumuj interakcje między użytkownikami i składnikami na diagramie sekwencji jako przypadek użycia, który reprezentuje cel użytkownika.<br /><br /> Zobacz:<br /><br /> -   [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramy przypadków użycia -   UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="DefineClasses"></a>Definiowanie słownika typów: diagramy klas
 Diagramy klas definiują jednostki, terminy lub koncepcje, które uczestniczą w systemie i ich relacji ze sobą. Na przykład można użyć tych diagramów podczas programowania, aby opisać atrybuty i operacje dla każdej klasy, niezależnie od ich języka lub stylu implementacji.

 Aby pomóc lucerny opisać i omówić jednostki, które uczestniczą w przypadku użycia w procesie płatności, narysujemy następujący Diagram klas:

 ![Przetwarzanie jednostek płatności na diagramie klas](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Przetwarzanie jednostek płatności na diagramie klas**

 Ten diagram pokazuje, że klient może mieć wiele zamówień i różne sposoby płacenia za zamówienia. BankAccount i CreditCard są dziedziczone z płatności.

 Podczas opracowywania, w przypadku korzystania z poniższych diagramów klas, w celu opisania szczegółów poszczególnych klas i omówienia ich:

 ![Przetwarzanie szczegółów jednostki płatniczej na diagramie klas](../modeling/media/uml-payment.png "UML_Payment")

 **Przetwarzanie szczegółów płatności na diagramie klas**

 Zobacz:

- [Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)

- [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>Rysowanie diagramu klas
 Diagram klas ma następujące główne funkcje:

- Typy takie jak klasy, interfejsy i wyliczenia:

  - *Klasa* jest definicją obiektów, które mają określone charakterystyki strukturalne lub behawioralne.

  - *Interfejs* definiuje część widocznego na zewnątrz zachowania obiektu.

  - *Wyliczenie* jest klasyfikatorem zawierającym listę wartości literału.

- *Atrybuty* są wartościami określonego typu, które opisują każde wystąpienie *klasyfikatora*. Klasyfikator to ogólna nazwa dla typów, składników, przypadków użycia, a nawet aktorów.

- *Operacje* to metody lub funkcje, które mogą wykonywać wystąpienia klasyfikatora.

- *Skojarzenie* wskazuje rodzaj relacji między dwoma klasyfikatorami.

  - *Agregacja* to skojarzenie wskazujące wspólną własność między klasyfikatorami.

  - *Kompozycja* to skojarzenie, które wskazuje całość relacji między klasyfikatorami.

    Aby wyświetlić agregacje lub kompozycje, należy ustawić właściwość **agregacji** skojarzenia. W obszarze **udostępnione** są wyświetlane agregacje i **złożone** kompozycje.

- *Zależność* wskazuje, że zmiana definicji jednego klasyfikatora może zmienić definicję innego klasyfikatora.

- *Generalizacja* wskazuje, że określony klasyfikator dziedziczy część swojej definicji z klasyfikatora ogólnego. *Realizacja* wskazuje, że klasa implementuje operacje i atrybuty oferowane przez interfejs.

   Aby utworzyć te relacje, użyj narzędzia **dziedziczenie** . Alternatywnie realizacja może być reprezentowana jako *lizak*.

- *Pakiety* są grupami klasyfikatora, skojarzeniami, liniami życia, składnikami i innymi pakietami. Relacje *importu* wskazują, że jeden pakiet zawiera wszystkie definicje innego pakietu.

  Jako punkt początkowy do eksplorowania i omawiania istniejących klas można użyć Projektant klas do tworzenia diagramów klas na podstawie kodu.

  Zobacz:

- [Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)

- [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Podsumowanie: zalety diagramów klas
 Diagramy klas ułatwiają Definiowanie:

- Typowy słownik terminów do użycia podczas omawiania potrzeb użytkowników i jednostek, które uczestniczą w systemie. Zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

- Typy, które są używane przez części systemu, takie jak składniki, niezależnie od ich implementacji. Zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

- Relacje, takie jak zależności, między typami. Można na przykład pokazać, że jeden typ może być skojarzony z wieloma wystąpieniami innego typu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Opis**|
|-----------------|---------------------|
|Diagramów przypadków użycia|Zdefiniuj typy, które są używane do opisywania celów i kroków w przypadku użycia.<br /><br /> Zobacz:<br /><br /> -   [diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />[diagramy przypadków użycia -   UML: wytyczne](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagramu aktywności|Zdefiniuj typy danych przekazywane przez węzły obiektów, numery PIN wejścia, PIN wyjściowe i węzły parametrów działania.<br /><br /> Zobacz:<br /><br /> [diagramy działań -   UML: odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />[diagramy aktywności UML -   : wytyczne](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagramów składników|Opisz składniki, ich interfejsy i ich relacje. Klasa może również opisywać kompletny składnik.<br /><br /> Zobacz:<br /><br /> -   [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />[diagramy składników UML -   : wytyczne](../modeling/uml-component-diagrams-guidelines.md)|
|Diagram warstwowy|Zdefiniuj architekturę logiczną systemu, która odnosi się do klas.<br /><br /> Użyj walidacji warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> -   [tworzenia diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy warstwowe: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [diagramy warstwowe: wytyczne](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikuj kod przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|
|Diagramów sekwencji|Zdefiniuj typy linii życia oraz operacje, parametry i wartości zwracane dla wszystkich komunikatów, które mogą być odbierane przez linię życia.<br /><br /> Aby utworzyć linię życia na podstawie typu na diagramie klasy, kliknij prawym przyciskiem myszy typ, a następnie kliknij polecenie **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> [diagramy sekwencji -   UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />[diagramy sekwencji -   UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md)|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby zidentyfikować klasy, ich relacje i ich metody, Utwórz mapę kodu, która pokazuje te elementy.<br /><br /> Zobacz:<br /><br /> -   [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="DescribeLayers"></a>Opisywanie architektury logicznej: diagramy warstwowe
 Diagramy warstw opisują architekturę logiczną systemu przez organizowanie artefaktów w rozwiązaniu do grup abstrakcyjnych lub *warstw*. Artefakty mogą mieć wiele rzeczy, takich jak przestrzenie nazw, projekty, klasy, metody i tak dalej. Warstwy reprezentują i opisują role lub zadania wykonywane przez artefakty w systemie. Możesz również uwzględnić walidację warstwy w operacjach kompilacji i zaewidencjonowania, aby upewnić się, że kod pozostaje zgodny z projektem.

 Aby zachować kod spójny z projektem, obiad teraz i Lucerny, użyj poniższego diagramu warstwowego, aby zweryfikować swój kod w miarę rozwoju:

 ![Diagram warstwowy zintegrowanego systemu płatności](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagram warstwowy dla obiadu teraz zintegrowany z lucerny**

 Warstwy na tym diagramie łączą się z odpowiednimi artefaktami rozwiązań na obiad teraz i Lucerny. Na przykład warstwa biznesowa łączy się z przestrzenią nazw DinnerNow. Business i jej członkami, która teraz zawiera klasę PaymentApprover. Warstwa dostępu do zasobów łączy się z przestrzenią nazw DinnerNow. Data. Strzałki lub *zależności*określają, że tylko warstwa biznesowa może korzystać z funkcji w warstwie dostępu do zasobów. Gdy zespoły aktualizują swój kod, sprawdzanie poprawności warstwy jest wykonywane regularnie, aby przechwytywać konflikty w miarę ich występowania, a także ułatwić zespołom ich natychmiastowe rozwiązanie.

 Zespoły współpracują ze sobą w celu przyrostowego integrowania i testowania dwóch systemów. Najpierw należy upewnić się, że PaymentApprover i pozostała część obiadu teraz współpracują ze sobą, zanim zadbają o PaymentProcessing.

 Poniższa mapa kodu przedstawia nowe wywołania między obiadem teraz i PaymentApprover:

 ![Zaktualizowany wykres zależności z systemem zintegrowanym](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Mapa kodu ze zaktualizowanymi wywołaniami metod**

 Po upewnieniu się, że system działa zgodnie z oczekiwaniami, obiad teraz oznacza kod PaymentProcessing. Raporty sprawdzania poprawności warstwy są czyste, a powstająca Mapa kodu wskazuje, że nie ma więcej zależności PaymentProcessing:

 ![Wykres zależności bez PaymentProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **Mapa kodu bez PaymentProcessing**

#### <a name="drawing-a-layer-diagram"></a>Rysowanie diagramu warstwowego
 Diagram warstwowy ma następujące główne funkcje:

- *Warstwy* opisują logiczne grupy artefaktów.

- *Łącze* jest skojarzeniem między warstwą a artefaktem.

   Aby utworzyć warstwy na podstawie artefaktów, przeciągnij elementy z Eksplorator rozwiązań, mapy kodu Widok klasy lub Przeglądarka obiektów. Aby narysować nowe warstwy, a następnie połączyć je z artefaktami, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu, aby utworzyć warstwy, a następnie przeciągnij elementy do tych warstw.

   Liczba na warstwie pokazuje liczbę artefaktów, które są połączone z warstwą. Te artefakty mogą być przestrzeniami nazw, projektami, klasami, metodami i tak dalej. Podczas interpretacji liczby artefaktów na warstwie należy pamiętać o następujących kwestiach:

  - Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

  - Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

    Aby wyświetlić artefakty, które są połączone z warstwą, kliknij prawym przyciskiem myszy warstwę, a następnie kliknij przycisk **Wyświetl linki** , aby otworzyć **Eksploratora warstw**.

- *Zależność* wskazuje, że jedna warstwa może korzystać z funkcjonalności w innej warstwie, ale nie odwrotnie. *Zależność dwukierunkowa* wskazuje, że jedna warstwa może korzystać z funkcjonalności w innej warstwie i odwrotnie.

   Aby wyświetlić istniejące zależności na diagramie warstwy, kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij polecenie **Generuj zależności**. Aby opisać zamierzone zależności, narysuj nowe.

  Zobacz:

- [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)

- [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Podsumowanie: zalety diagramów warstw
 Diagramy warstw pomagają:

- Opisz logiczną architekturę systemu w zależności od funkcjonalności jego artefaktów.

- Upewnij się, że kod w obszarze programowanie jest zgodny z określonym projektem.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Opis**|
|-----------------|---------------------|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby utworzyć warstwy, wygeneruj mapę kodu, a następnie Grupuj elementy na mapie jako potencjalną warstwę. Przeciągnij grupy z mapy do diagramu warstwowego.<br /><br /> Zobacz:<br /><br /> -   [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [przeglądać i zmieniać rozmieszczenie map kodu](../modeling/browse-and-rearrange-code-maps.md)|
|Diagramów składników|Opisz składniki, ich interfejsy i ich relacje.<br /><br /> Aby wizualizować warstwy, Utwórz diagram składników, który opisuje funkcje różnych składników w systemie.<br /><br /> Zobacz:<br /><br /> -   [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)<br />[diagramy składników UML -   : wytyczne](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategorii**|**Linki**|
|------------------|---------------|
|**Dotyczące**|-   [Wizualizacja programu Visual Studio & narzędzia do modelowania](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [wizualizacji programu Visual Studio & Modeling SDK (narzędzia DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Zobacz też
 [Wizualizowanie kodu](../modeling/visualize-code.md) [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md) [Używanie modeli w procesie programistycznym](../modeling/use-models-in-your-development-process.md) [Korzystanie z modeli w programowaniu Agile](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) [weryfikacja systemu podczas programowania](../modeling/validate-your-system-during-development.md) [](../modeling/extend-uml-models-and-diagrams.md)
