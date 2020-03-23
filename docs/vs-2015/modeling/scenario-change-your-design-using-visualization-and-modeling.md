---
title: 'Scenariusz: zmienianie projektu przy użyciu wizualizacji i modelowania | Dokumenty firmy Microsoft'
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
ms.openlocfilehash: 70cc3c81c426ec55d0afb36360155786ec97d937
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302316"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upewnij się, że system oprogramowania spełnia potrzeby użytkowników przy użyciu narzędzi do wizualizacji i modelowania w programie Visual Studio. Użyj narzędzi, takich jak diagramy języka UML (Unified Modeling Language), mapy kodu, diagramy warstw i diagramy klas, aby:

 Aby zobaczyć, które wersje programu Visual Studio obsługują każde narzędzie, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Wyjaśnij wymagania użytkowników i procesy biznesowe.

- Wizualizuj i eksploruj istniejący kod.

- Opis zmian w istniejącym systemie.

- Sprawdź, czy system spełnia jego wymagania.

- Zachowaj kod zgodny z projektem.

  Ten przewodnik:

- W tym artykule opisano, jak te narzędzia mogą przynieść korzyści projektowi oprogramowania.

- Pokazuje, jak można użyć tych narzędzi, niezależnie od podejścia do programowania, z przykładowym scenariuszem.

  Aby dowiedzieć się więcej o tych narzędziach i scenariuszach, które obsługują, zobacz:

- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)

## <a name="scenario-overview"></a><a name="ScenarioOverview"></a>Omówienie scenariusza
 W tym scenariuszu opisano epizody z cyklu życia tworzenia oprogramowania dwóch fikcyjnych firm: Dinner Now i Lucerne Publishing. Dinner Now zapewnia usługę dostarczania posiłków w Seattle w sieci Web. Klienci mogą zamawiać posiłki i płacić za nie w witrynie sieci Web Dinner Now. Zamówienia są następnie wysyłane do odpowiedniej lokalnej restauracji w celu dostarczenia. Lucerne Publishing, firma z Nowego Jorku, prowadzi kilka firm zarówno poza siecią, jak i w internecie. Na przykład uruchamiają witrynę sieci Web, w której klienci mogą publikować recenzje restauracji.

 Lucerna niedawno nabyte Obiad teraz i chce wprowadzić następujące zmiany:

- Zintegruj swoje witryny sieci Web, dodając funkcje przeglądu restauracji do obiadu teraz.

- Zamień system płatności Dinner Now na system Lucerny.

- Rozwiń usługę Obiad teraz w całym regionie.

  Kolacja Teraz używa SCRUM i eXtreme Programming. Mają bardzo wysoki zasięg testu i bardzo mało nieobsługiwał kod. Minimalizują one ryzyko, tworząc małe, ale działające wersje systemu, a następnie dodając funkcje przyrostowo. Rozwijają swój kod za jący krótkie i częste iteracje. Dzięki temu mogą ogarniać zmiany pewnie, refaktoryzuje kod często i uniknąć "duży projekt z góry".

  Lucerna utrzymuje znacznie większy i złożony zbiór systemów, z których niektóre mają ponad 40 lat. Są one bardzo ostrożne w wprowadzaniu zmian ze względu na złożoność i zakres starszego kodu. Postępują zgodnie z bardziej rygorystycznym procesem rozwoju, preferując projektowanie szczegółowych rozwiązań i dokumentowanie projektu i zmian, które zachodzą podczas opracowywania.

  Oba zespoły używają diagramów modelowania w programie Visual Studio, aby pomóc im w opracowywaniu systemów spełniających potrzeby użytkowników. Używają team foundation server wraz z innymi narzędziami, aby pomóc im planować, organizować i zarządzać swoją pracą.

  Aby uzyskać więcej informacji na temat programu Team Foundation Server, zobacz:

- [Planowanie i śledzenie prac](#PlanningTracking)

- [Testowanie, sprawdzanie poprawności i sprawdzanie zaktualizowanego kodu](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Role diagramów architektury i modelowania w tworzeniu oprogramowania
 W poniższej tabeli opisano role, które te narzędzia mogą odgrywać na wielu i różnych etapach cyklu życia tworzenia oprogramowania:

||**Modelowanie wymagań użytkownika**|**Modelowanie procesów biznesowych**|**Architektura systemu & projektowanie**|**Wizualizacja kodu & eksploracji**|**Weryfikacja**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Diagram przypadków użycia (UML)|√|√|||√|
|Diagram aktywności (UML)|√|√|√||√|
|Diagram klasy (UML)|√|√|√||√|
|Diagram składników (UML)|√|√|√||√|
|Diagram sekwencji (UML)|√|√|√||√|
|Diagram języka specyficznego dla domeny (DSL)|√|√|√|||
|Diagram warstw, sprawdzanie poprawności warstwy|||√|√|√|
|Mapa kodu|||√|√|√|
|Projektant klas (oparty na kodzie)||||√||

 Aby narysować diagramy UML i diagramy warstwowe, należy utworzyć projekt modelowania jako część istniejącego rozwiązania lub nowego. Te diagramy muszą być tworzone w projekcie modelowania. Elementy na diagramach UML są częścią wspólnego modelu, a diagramy UML są widokami tego modelu. Elementy na diagramach warstwowych znajdują się w projekcie modelowania, ale nie są przechowywane we wspólnym modelu. Mapy kodu i diagramy klas .NET utworzone na podstawie kodu istnieją poza projektem modelowania.

 Zobacz:

- [Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Aby wyświetlić alternatywne widoki architektury, można ponownie użyć niektórych elementów z tego samego modelu na wielu diagramach lub różnych. Na przykład można przeciągnąć składnik do innego diagramu składników lub do diagramu sekwencji, tak aby mógł działać jako aktor. Zobacz [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md).

  Oba zespoły również użyć sprawdzania poprawności warstwy, aby upewnić się, że kod w trakcie opracowywania pozostaje zgodne z projektem.

  Zobacz:

- [Utrzymywanie kodu zgodnego z projektem](#ValidatingCode)

- [Opis architektury logicznej: diagramy warstw](#DescribeLayers)

- [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Niektóre wersje programu Visual Studio obsługują sprawdzanie poprawności warstw i tylko do odczytu map kodu i diagramów UML do wizualizacji i modelowania. Aby zobaczyć, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understanding-and-communicating-information-about-the-system"></a><a name="UnderstandingCommunicating"></a>Opis i przekazywanie informacji o systemie
 Nie ma żadnych wymaganych kolejności przy użyciu diagramów modelowania programu Visual Studio, dzięki czemu można ich używać, ponieważ pasują one do twoich potrzeb lub podejścia. Zazwyczaj zespoły ponownie ich modele iteratively i często w całym projekcie. Każdy diagram oferuje szczególne mocne strony, które pomogą Ci zrozumieć, opisać i przekazać różne aspekty systemu w fazie opracowywania.

 Dinner Now i Lucerna komunikują się ze sobą i z zainteresowanymi stronami projektu przy użyciu diagramów jako wspólnego języka. Na przykład obiad teraz używa diagramów do wykonywania tych zadań:

- Wizualizuj istniejący kod.

- Komunikuj się z Lucerny o nowych lub zaktualizowanych historiach użytkowników.

- Identyfikowanie zmian, które są wymagane do obsługi nowych lub zaktualizowanych wątków użytkownika.

  Lucerna używa diagramów do wykonywania tych zadań:

- Dowiedz się więcej o procesie biznesowym Obiad teraz.

- Zrozumieć projekt systemu.

- Komunikuj się z obiadem teraz o nowych lub zaktualizowanych wymaganiach użytkownika.

- Aktualizacja dokumentu systemu.

  Diagramy są zintegrowane z team foundation server, dzięki czemu zespoły mogą łatwiej planować, zarządzać i śledzić swoją pracę. Na przykład używają modeli do identyfikowania przypadków testowych i zadań programistycznych oraz do szacowania ich pracy. Lucerna łączy elementy robocze programu Team Foundation Server z elementami modelu, dzięki czemu mogą monitorować postęp i upewnić się, że system spełnia wymagania użytkowników. Na przykład łączą przypadki użycia do elementów roboczych sprawy testowej, dzięki czemu mogą zobaczyć, że przypadki użycia są spełnione, gdy wszystkie testy przechodzą.

  Zanim zespoły zaewidencjonują swoje zmiany, sprawdzają poprawność kodu przed testami i projektem, uruchamiając kompilacje, które obejmują sprawdzanie poprawności warstw i testy automatyczne. Pomaga to upewnić się, że zaktualizowany kod nie powoduje konfliktu z projektem i przerywa wcześniej działające funkcje.

  Zobacz:

- [Zrozumienie roli systemu w procesie biznesowym](#UnderstandingBPMandSystemDesign)

- [Opisywanie nowych lub zaktualizowanych wymagań użytkownika](#DescribingURM)

- [Tworzenie testów z modeli](#CreatingTests)

- [Identyfikowanie zmian w istniejącym systemie](#DeterminingChanges)

- [Utrzymywanie kodu zgodnego z projektem](#ValidatingCode)

- [Ogólne wskazówki dotyczące tworzenia i używania modeli](#GeneralTips)

- [Planowanie i śledzenie prac](#PlanningTracking)

- [Testowanie, sprawdzanie poprawności i sprawdzanie zaktualizowanego kodu](#TestValidateCheckInCode)

### <a name="understanding-the-role-of-the-system-in-the-business-process"></a><a name="UnderstandingBPMandSystemDesign"></a>Zrozumienie roli systemu w procesie biznesowym
 Lucerna chce dowiedzieć się więcej o procesie biznesowym Dinner Now. Tworzą one następujące diagramy, aby łatwiej wyjaśnić ich zrozumienie z Obiad teraz łatwiej:

|**Diagram**|**Opisuje**|
|-----------------|-------------------|
|*Diagram przypadków użycia (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: Wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|- Działania, które obsługuje system Dinner Now<br />- Ludzie i systemy zewnętrzne, które wykonują działania<br />- Główne elementy systemu, które wspierają każde działanie<br />- Części procesu biznesowego, które nie są objęte zakresem obecnego systemu, na przykład dostawy żywności|
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: Wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|Przepływ kroków, które występują, gdy klient tworzy zamówienie|
|*Diagram klasy (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: Wskazówki](../modeling/uml-class-diagrams-guidelines.md)|Jednostki biznesowe i terminy używane w dyskusji i relacje między tymi jednostkami. Na przykład Kolejność i element menu są częścią słownictwa w tym scenariuszu.|

 Na przykład Lucerna tworzy następujący diagram przypadków użycia, aby zrozumieć zadania, które są wykonywane w witrynie sieci Web Obiad teraz i kto je wykonuje:

 ![Diagram przypadków użycia UML](../modeling/media/uml-usecase.png "UML_UseCase")

 **Diagram przypadków użycia UML**

 Na poniższym diagramie działania opisano przepływ kroków, gdy klient tworzy zamówienie w witrynie sieci Web Obiad teraz. W tej wersji elementy komentarza identyfikują role, a linie tworzą *tor,* które organizują kroki według roli:

 ![Diagram aktywności UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **Diagram aktywności UML**

 Na poniższym diagramie klasy opisano jednostki uczestniczące w procesie zamawiania:

 ![Diagram klas UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **Diagram klas UML**

### <a name="describing-new-or-updated-user-requirements"></a><a name="DescribingURM"></a>Opisywanie nowych lub zaktualizowanych wymagań użytkownika
 Lucerna chce dodać funkcjonalność do systemu Obiad teraz, dzięki czemu klienci mogą czytać i współtworzyć opinie restauracji. Aktualizują następujące diagramy, aby mogli opisać i omówić to nowe wymaganie z Obiad teraz:

|**Diagram**|**Opisuje**|
|-----------------|-------------------|
|*Diagram przypadków użycia (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: Wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|Nowy przypadek użycia dla "Napisz recenzję restauracji"|
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: Wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|Kroki, które występują, gdy klient chce napisać recenzję restauracji|
|*Diagram klasy (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: Wskazówki](../modeling/uml-class-diagrams-guidelines.md)|Dane wymagane do przechowywania recenzji|

 Na przykład poniższy diagram przypadków użycia zawiera nowy przypadek użycia "Write Review" do reprezentowania nowego wymagania. Jest podświetlony na pomarańczowo na schemacie w celu łatwiejszej identyfikacji:

 ![Diagram przypadków użycia UML](../modeling/media/uml-writerev.png "UML_WriteRev")

 **Diagram przypadków użycia UML**

 Poniższy diagram aktywności zawiera nowe elementy na pomarańczowo, aby opisać przepływ kroków w nowym przypadku użycia:

 ![Diagram aktywności UML](../modeling/media/uml-writereview.png "UML_WriteReview")

 **Diagram aktywności UML**

 Poniższy diagram klasy zawiera nową klasę Review i jej relacje z innymi klasami, dzięki czemu zespoły mogą omawiać jego szczegóły. Zauważ, że klient i restauracja mogą mieć wiele recenzji:

 ![Diagram klas UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **Diagram klasy UML**

### <a name="creating-tests-from-models"></a><a name="CreatingTests"></a>Tworzenie testów z modeli
 Oba zespoły zgadzają się, że potrzebują pełnego zestawu testów dla systemu i jego składników, zanim wejdą w jakiekolwiek zmiany. Lucerna ma wyspecjalizowany zespół, który wykonuje testy na poziomie systemu i komponentu. Ponownie używają testów utworzonych przez Obiad teraz i struktury tych testów przy użyciu diagramów UML:

- Każdy przypadek użycia jest reprezentowany przez jeden lub wiele testów. Elementy na diagramie przypadków użycia łącza do elementów roboczych przypadku testowego w team foundation server.

- Każdy przepływ na diagramie aktywności lub diagramie sekwencji na poziomie systemu jest połączony z co najmniej jednym testem. Zespół testowy systematycznie upewnia się, że testuje każdą możliwą ścieżkę za pośrednictwem diagramu aktywności.

- Terminy używane do opisywania testów są oparte na terminach zdefiniowanych przez diagramy przypadków użycia, klasy i aktywności.

  Ponieważ wymagania zmieniają się, a diagramy są aktualizowane w celu odzwierciedlenia tych zmian, testy są również aktualizowane. Wymóg uznaje się za spełniony tylko wtedy, gdy testy zdają. Gdy jest to możliwe lub praktyczne, testy są definiowane i oparte na diagramach UML przed rozpoczęciem implementacji.

  Zobacz:

- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)

- [Weryfikacja modelu UML](../modeling/validate-your-uml-model.md)

### <a name="identifying-changes-to-the-existing-system"></a><a name="DeterminingChanges"></a>Identyfikowanie zmian w istniejącym systemie
 Obiad teraz musi oszacować koszt spełnienia nowego wymogu. Zależy to częściowo od tego, jak bardzo ta zmiana wpłynie na inne części systemu. Aby pomóc im to zrozumieć, jeden z deweloperów obiad teraz tworzy te mapy i diagramy z istniejącego kodu:

|**Mapa lub diagram**|**Seriale**|
|------------------------|---------------|
|*Mapa kodu*<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Przeglądanie i zmienianie rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Dostosowywanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Zależności i inne relacje w kodzie.<br /><br /> Na przykład obiad teraz można rozpocząć od przeglądu map kodu zestawu dla przeglądu zestawów i ich zależności. Mogą one drążyć na mapach, aby eksplorować przestrzenie nazw i klasy w tych zestawach.<br /><br /> Obiad teraz można również utworzyć mapy do eksplorowania poszczególnych obszarów i innych rodzajów relacji w kodzie. Używają Eksploratora rozwiązań, aby znaleźć i wybrać obszary i relacje, które ich interesują.|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [Jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie|

 Na przykład deweloper tworzy mapę kodu. Dostosowuje swój zakres, aby skupić się na obszarach, które będą miały wpływ na nowy scenariusz. Te obszary są zaznaczone i wyróżnione na mapie:

 ![Wykres zależności obszaru nazw](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Mapa kodu obszaru nazw**

 Deweloper rozszerza wybrane przestrzenie nazw, aby wyświetlić ich klasy, metody i relacje:

 ![Wykres zależności rozwiniętego obszaru nazw](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Mapa kodu rozszerzonej przestrzeni nazw z widocznymi łączami między grupami**

 Deweloper sprawdza kod, aby znaleźć których dotyczy problem klas i metod. Aby zobaczyć efekty każdej zmiany w miarę ich wprowadzania, ponownie wygeneruj mapy kodu po każdej zmianie. Zobacz [Wizualizuj kod](../modeling/visualize-code.md).

 Aby opisać zmiany w innych częściach systemu, takich jak składniki lub interakcje, zespół może narysować te elementy na tablicach. Mogą również rysować następujące diagramy w programie Visual Studio, dzięki czemu szczegóły mogą być przechwytywane, zarządzane i zrozumiałe dla obu zespołów:

|**Diagramy**|**Opisuje**|
|------------------|-------------------|
|*Diagram aktywności (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: Wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|Przepływ kroków, które występują, gdy system zauważy, że klient ponownie składa zamówienie z restauracji, monitując klienta o napisanie recenzji.|
|*Diagram klasy (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: Wskazówki](../modeling/uml-class-diagrams-guidelines.md)|Klasy logiczne i ich relacje. Na przykład nowa klasa jest dodawana do opisywania **przeglądu** i jego relacji z innymi encjami, takimi jak **Restauracja,** **Menu**i **Klient**.<br /><br /> Aby skojarzyć opinie z klientem, system musi przechowywać dane klienta. Diagram klasy UML może pomóc w wyjaśnieniu tych szczegółów.|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [Jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie.|
|*Diagram składników (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: Wskazówki](../modeling/uml-component-diagrams-guidelines.md)|Części wysokiego poziomu systemu, takie jak witryna sieci Web Obiad teraz i ich interfejsy. Te interfejsy definiują sposób interakcji składników ze sobą za pośrednictwem metod lub usług, które zapewniają i zużywają.|
|*Diagram sekwencji (UML)*<br /><br /> Zobacz:<br /><br /> -   [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramy sekwencji UML: Wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|Sekwencja interakcji między wystąpieniami.|

 Na przykład na poniższym diagramie składnika przedstawiono nowy składnik, który jest częścią składnika Witryna sieci Web obiad teraz. Komponent ReviewProcessing obsługuje funkcjonalność tworzenia recenzji i pojawia się podświetlony na pomarańczowo:

 ![Diagram składników UML](../modeling/media/uml-internal.png "UML_Internal")

 **Diagram składników UML**

 Na poniższym diagramie sekwencji przedstawiono sekwencję interakcji, które występują, gdy witryna sieci Web Obiad teraz sprawdza, czy klient zamówił wcześniej w restauracji. Jeśli to prawda, to prosi klienta o utworzenie recenzji, która jest wysyłana do restauracji i publikowana przez witrynę sieci Web:

 ![Diagram sekwencji UML](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **Diagram sekwencji UML**

### <a name="keeping-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Utrzymywanie kodu zgodnego z projektem
 Obiad teraz należy upewnić się, że zaktualizowany kod pozostaje zgodny z projektem. Tworzą diagramy warstwowe, które opisują warstwy funkcjonalności w systemie, określają dozwolone zależności między nimi i kojarzą artefakty rozwiązań z tymi warstwami.

|**Diagram**|**Opisuje**|
|-----------------|-------------------|
|*Diagram warstw*<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów warstw na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy warstw: Wskazówki](../modeling/layer-diagrams-guidelines.md)<br />-   [Sprawdzanie poprawności kodu za pomocą diagramów warstwowych](../modeling/validate-code-with-layer-diagrams.md)|Logiczna architektura kodu.<br /><br /> Diagram warstwowy organizuje i mapuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] artefakty w rozwiązaniu do grup abstrakcyjnych zwanych *warstwami*. Warstwy te identyfikują role, zadania lub funkcje, które te artefakty wykonują w systemie.<br /><br /> Diagramy warstwowe są przydatne do opisywania zamierzonego projektu systemu i sprawdzania poprawności rozwijającego się kodu względem tego projektu.<br /><br /> Aby utworzyć warstwy, przeciągnij elementy z Eksploratora rozwiązań, map kodu, widoku klasy i przeglądarki obiektów. Aby narysować nowe warstwy, użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu.<br /><br /> Aby wyświetlić istniejące zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu warstwowego, a następnie kliknij polecenie **Generuj zależności**. Aby określić zamierzone zależności, narysuj nowe zależności.|

 Na przykład na poniższym diagramie warstwowym opisano zależności między warstwami i liczbę artefaktów skojarzonych z każdą warstwą:

 ![Schemat warstwowy zintegrowanego systemu płatności](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagram warstw**

 Aby upewnić się, że konflikty z projektem nie występują podczas tworzenia kodu, zespoły używa sprawdzania poprawności warstwy na kompilacji, które są uruchamiane w team foundation build. Tworzą również niestandardowe zadanie MSBuild, aby wymagać sprawdzania poprawności warstwy w swoich operacjach ewidencjonowania. Używają raportów kompilacji do zbierania błędów sprawdzania poprawności.

 Zobacz:

- [Definiowanie procesu kompilacji](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Sprawdzanie poprawności zmian za pomocą procesu kompilacji ewidencjonowania z bramką](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Dostosowywanie szablonu procesu kompilacji](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="general-tips-for-creating-and-using-models"></a><a name="GeneralTips"></a>Ogólne wskazówki dotyczące tworzenia i używania modeli

- Większość diagramów składa się z węzłów połączonych liniami. Dla każdego typu diagramu przybornik zawiera różne rodzaje węzłów i linii.

   Aby otworzyć przybornik, w menu **Widok** kliknij polecenie **Przybornik**.

- Aby utworzyć węzeł, przeciągnij go z przybornika do diagramu. Niektóre rodzaje węzłów muszą być przeciągane do istniejących węzłów. Na przykład na diagramie składników nowy port musi zostać dodany do istniejącego składnika.

- Aby utworzyć linię lub połączenie, kliknij odpowiednie narzędzie w przyborniku, kliknij węzeł źródłowy, a następnie kliknij węzeł docelowy. Niektóre wiersze mogą być tworzone tylko między określonymi rodzajami węzłów. Po przesunięciu wskaźnika nad możliwym źródłem lub obiektem docelowym wskaźnik wskazuje, czy można utworzyć połączenie.

- Podczas tworzenia elementów na diagramach UML, są również dodawanie ich do wspólnego modelu. Diagramy UML w projekcie modelowania są widokami tego modelu. Elementy na diagramie warstwowym są częścią projektu modelowania, nawet jeśli nie są przechowywane we wspólnym modelu.

   Aby wyświetlić model, w menu **Architektura** wskaż polecenie **Windows**, a następnie kliknij polecenie **Eksplorator modelu UML**.

- W niektórych przypadkach można przeciągnąć niektóre elementy z **Eksploratora modelu UML** do diagramu UML. Niektóre elementy w tym samym modelu mogą być używane na wielu diagramach lub różnych, aby wyświetlić alternatywne widoki architektury. Na przykład można przeciągnąć składnik do innego diagramu składników lub do diagramu sekwencji, aby użyć go jako aktora.

- Visual Studio obsługuje UML 2.1.2. W tym przeglądzie opisano tylko główne funkcje diagramów UML w tej wersji, ale istnieje wiele książek, które omawiają UML i jego użycie szczegółowo.

  Zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md).

### <a name="planning-and-tracking-work"></a><a name="PlanningTracking"></a>Planowanie i śledzenie pracy
 Diagramy modelowania programu Visual Studio są zintegrowane z programem Team Foundation Server, dzięki czemu można łatwiej planować, zarządzać i śledzić pracę. Oba zespoły używają modeli do identyfikowania przypadków testowych i zadań programistycznych oraz do szacowania ich pracy. Lucerna tworzy i łączy elementy robocze programu Team Foundation Server z elementami modelu, takimi jak przypadki użycia lub składniki. Pomaga im to monitorować ich postępy i śledzić ich pracę z powrotem do wymagań użytkowników. Pomaga im to upewnić się, że ich zmiany nadal spełniają te wymagania.

 W miarę postępu pracy zespoły aktualizują swoje elementy robocze, aby odzwierciedlić czas spędzony na swoich zadaniach. Monitorują również i zgłaszają stan swojej pracy przy użyciu następujących funkcji team foundation server:

- Codzienne *raporty wypalenia,* które pokazują, czy zakończą planowane prace w oczekiwanym czasie. Generują inne podobne raporty z Team Foundation Server do śledzenia postępu błędów.

- *Arkusz iteracji,* który używa programu Microsoft Excel, aby pomóc zespołowi monitorować i równoważyć obciążenie między jego członkami. Ten arkusz jest połączony z team foundation server i zapewnia fokus do dyskusji podczas regularnych spotkań postępu.

- *Pulpit nawigacyjny rozwoju,* który używa pakietu Office Project, aby informować zespół o ważnych informacjach o projekcie.

  Zobacz:

- [Śledzenie pracy przy użyciu usług zespołu visual studio lub programu Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md)

- [Wykresy, pulpity nawigacyjne i raporty dla programu Visual Studio ALM](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Tworzenie zaległości i zadań przy użyciu programu Project](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="testing-validating-and-checking-in-code"></a><a name="TestValidateCheckInCode"></a>Testowanie, sprawdzanie poprawności i sprawdzanie kodu
 Gdy zespoły wykonają każde zadanie, sprawdzają swój kod w kontroli wersji programu Team Foundation i otrzymują przypomnienia z team foundation server, jeśli zapomną. Zanim team Foundation Server zaakceptuje ich zaewidencjonowania, zespoły uruchamiają testy jednostkowe i sprawdzanie poprawności warstwy, aby zweryfikować kod w ich przypadkach testowych i projekcie. Używają Team Foundation Server do regularnego uruchamiania kompilacji, automatycznych testów jednostkowych i sprawdzania poprawności warstw. Pomaga to upewnić się, że kod spełnia następujące kryteria:

- To działa.

- Nie łamie wcześniej działającego kodu.

- Nie jest to sprzeczne z projektem.

  Obiad teraz ma duży zbiór zautomatyzowanych testów, które Lucerna może ponownie użyć, ponieważ prawie wszystkie nadal mają zastosowanie. Lucerna może również opierać się na tych testach i dodawać nowe, aby objąć nowe funkcje. Oba również używać programu Visual Studio do uruchamiania testów ręcznych.

  Aby upewnić się, że kod jest zgodny z projektem, zespoły skonfigurować swoje kompilacje w Team Foundation Build do uwzględnienia sprawdzania poprawności warstwy. Jeśli wystąpią konflikty, raport jest generowany ze szczegółami.

  Zobacz:

- [Testowanie aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)

- [Korzystanie z kontroli wersji](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Tworzenie aplikacji](/azure/devops/pipelines/index)

## <a name="updating-the-system-using-visualization-and-modeling"></a><a name="UpdatingSystem"></a>Aktualizowanie systemu za pomocą wizualizacji i modelowania
 Lucerna i Obiad Teraz muszą zintegrować swoje systemy płatności. W poniższych sekcjach przedstawiono diagramy modelowania w programie Visual Studio, aby ułatwić wykonanie tego zadania:

- [Zrozumienie wymagań użytkownika: Diagramy przypadków użycia](#UnderstandUseCases)

- [Zrozumienie procesu biznesowego: diagramy aktywności](#UnderstandActivities)

- [Opis struktury systemu: diagramy komponentów](#DescribeComponents)

- [Opis interakcji: Diagramy sekwencji](#DescribeSequence)

- [Wizualizuj istniejący kod: Mapy kodu](#VisualizeCode)

- [Definiowanie glosariusza typów: diagramy klas](#DefineClasses)

- [Opis architektury logicznej: diagramy warstw](#DescribeLayers)

  Zobacz:

- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)

- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)

### <a name="understand-the-user-requirements-use-case-diagrams"></a><a name="UnderstandUseCases"></a>Zrozumienie wymagań użytkownika: Diagramy przypadków użycia
 Diagramy przypadków użycia podsumowują działania, które obsługuje system i kto wykonuje te działania. Lucerna używa diagramu przypadków użycia, aby dowiedzieć się więcej o systemie Obiad teraz:

- Klienci tworzą zamówienia.

- Restauracje otrzymują zamówienia.

- Brama zewnętrznego procesora płatności, której system płatności obiad teraz używa do sprawdzania poprawności płatności, jest poza zakresem witryny sieci Web.

  Diagram pokazuje również, jak niektóre z głównych przypadków użycia podzielić na mniejsze przypadki użycia. Lucerna chce korzystać z własnego systemu płatności. Wyróżniają przypadek użycia płatności procesowego w innym kolorze, aby wskazać, że wymaga zmian:

  ![Wyróżnianie płatności procesowej na diagramie przypadków użycia](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Wyróżnianie płatności procesowej na diagramie przypadków użycia**

  Jeśli czas rozwoju był krótki, zespół może dyskutować, czy chcą pozwolić klientom płacić restauracje bezpośrednio. Aby to pokazać, zastąpią przypadek użycia płatności procesowego na taki, który znajduje się poza granicą systemu obiad teraz. Następnie połączyliby Klienta bezpośrednio z restauracją, wskazując, że Obiad Teraz będzie przetwarzać tylko zamówienia:

  ![Przeskuwanie płatnej restauracji na diagramie przypadków użycia](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Przeskuwanie płatnej restauracji na diagramie przypadków użycia**

  Zobacz:

- [Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Rysowanie diagramu przypadków użycia
 Diagram przypadków użycia ma następujące główne cechy:

- *Aktorzy* reprezentują role odgrywane przez osoby, organizacje, maszyny lub systemy oprogramowania. Na przykład klient, restauracja i system płatności obiad teraz są aktorami.

- *Przypadki użycia* reprezentują interakcje między podmiotami a systemem w fazie opracowywania.  Mogą one reprezentować dowolną skalę interakcji od pojedynczego kliknięcia myszą lub wiadomości do transakcji przedłużonej przez wiele dni.

- *Skojarzenia* łączą podmioty z przypadkami użycia.

- Większy przypadek użycia może *zawierać* mniejsze, na przykład Utwórz zamówienie zawiera wybierz restaurację. Można *rozszerzyć* przypadek użycia, który dodaje cele i kroki do rozszerzonego przypadku użycia, aby wskazać, że przypadek użycia występuje tylko pod pewnymi warunkami. Przypadki użycia mogą również dziedziczyć od siebie nawzajem.

- *Podsystem* reprezentuje system oprogramowania, który jest w fazie rozwoju lub jeden z jego składników. Jest to duże pole, które zawiera przypadki użycia. Diagram przypadków użycia wyjaśnia, co znajduje się wewnątrz lub na zewnątrz granicy podsystemu. Aby wskazać, że użytkownik musi osiągnąć określone cele w inny sposób, należy narysować te przypadki użycia poza granicą podsystemu.

- *Artefakty* łączą elementy na diagramie z innymi diagramami lub dokumentami.

  Zobacz:

- [Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Krótki opis: Mocne strony diagramów przypadków użycia
 Diagramy przypadków użycia pomagają wizualizować:

- Działania, które system obsługuje lub nie obsługuje

- Osoby i systemy zewnętrzne, które wykonują te działania

- Główne składniki systemu obsługujące każde działanie, które można przedstawić jako podsystemy zagnieżdżone wewnątrz systemu nadrzędnego

- Jak przypadek użycia może podzielić się na mniejsze lub odmiany

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opisuje**|
|-----------------|-------------------|
|Diagramu aktywności|Przepływ kroków w przypadku użycia i tych, którzy wykonują te kroki w tym przypadku użycia.<br /><br /> Nazwy przypadków użycia często dublują kroki na diagramie aktywności. Diagramy aktywności obsługują elementy, takie jak decyzje, scalanie, dane wejściowe i wyjściowe, równoczesne przepływy i tak dalej.<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: Wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagramów sekwencji|Sekwencja interakcji między uczestnikami w przypadku użycia.<br /><br /> Zobacz:<br /><br /> -   [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramy sekwencji UML: Wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagram klasy (UML)|Jednostki lub typy, które uczestniczą w przypadku użycia.<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: Wskazówki](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="understand-the-business-process-activity-diagrams"></a><a name="UnderstandActivities"></a>Zrozumienie procesu biznesowego: diagramy aktywności
 Diagramy aktywności opisują przepływ kroków w procesie biznesowym i zapewniają prosty sposób komunikowania się z przepływem pracy. Projekt deweloperski może mieć wiele diagramów aktywności. Zazwyczaj działanie obejmuje wszystkie akcje, które wynikają z jednej akcji zewnętrznej, takie jak zamawianie posiłku, aktualizowanie menu lub dodawanie nowej restauracji do firmy. Działanie może również opisywać szczegóły złożonej akcji.

 Lucerna aktualizuje poniższy diagram aktywności, aby pokazać, że Lucerna przetwarza płatności i płaci restauracji. Zastępują one system płatności Obiad teraz z Lucerny System płatności, jak podkreślono:

 ![System płatności Lucerna na diagramie aktywności](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Zastąpienie systemu płatności obiad teraz na diagramie aktywności**

 Zaktualizowany diagram pomaga Lucernie i obiad teraz wizualizować, gdzie Lucerna System płatności pasuje do procesu biznesowego. W tej wersji komentarze są używane do identyfikowania ról, które wykonują kroki. Linie są używane do tworzenia *torów,* które organizują kroki według roli.

 Zespoły mogą również rozważyć omówienie alternatywnej historii, w której klient płaci restauracji zamiast po dostarczeniu zamówienia. Stworzyłoby to różne wymagania dla systemu oprogramowania.

 Wcześniej obiad teraz narysował te diagramy na tablicy lub w programie PowerPoint. Teraz również za pomocą programu Visual Studio do rysowania tych diagramów, dzięki czemu oba zespoły mogą przechwytywać, rozumieć i zarządzać szczegółami.

 Zobacz:

- [Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)

- [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Rysowanie diagramu aktywności
 Diagram aktywności ma następujące główne cechy:

- *Węzeł początkowy,* który wskazuje pierwszą akcję działania.

   Diagram powinien zawsze mieć jeden z tych węzłów.

- *Akcje* opisujące kroki, w których użytkownik lub oprogramowanie wykonuje zadanie.

- *Przepływy sterujące,* które pokazują przepływ między akcjami.

- *Węzły decyzji,* które reprezentują gałęzie warunkowe w przepływie.

- *Węzły rozwidlenia,* które dzielą pojedyncze przepływy do równoczesnych przepływów.

- *Węzły końcowe działania,* które pokazują końce działania.

   Mimo że te węzły są opcjonalne, warto dołączyć je na diagramie, aby pokazać, gdzie kończy się działanie.

  Zobacz:

- [Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)

- [Diagramy aktywności UML: wskazówki](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Krótki opis: Mocne strony diagramów aktywności
 Diagramy aktywności ułatwiają wizualizację i opisanie przepływu kontroli i informacji między działaniami firmy, systemu lub programu. Jest to prosty i przydatny sposób opisywania przepływu pracy podczas komunikowania się z innymi osobami.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-----------------|---------------------|
|Diagramów przypadków użycia|Podsumuj działania wykonywane przez każdego aktora.<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: Wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagramów składników|Wizualizuj system jako zbiór części wielokrotnego użycia, które zapewniają lub zużywają zachowanie za pośrednictwem dobrze zdefiniowanego zestawu interfejsów.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: Wskazówki](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="describe-the-system-structure-component-diagrams"></a><a name="DescribeComponents"></a>Opis struktury systemu: diagramy komponentów
 Diagramy składników opisują system jako zbiór rozdzielnych części, które zapewniają lub zużywają zachowanie za pośrednictwem dobrze zdefiniowanego zestawu interfejsów. Części mogą być na dowolną skalę i mogą łączyć się w dowolny sposób.

 Aby pomóc Lucerna i Obiad teraz wizualizować i omówić składniki systemu i ich interfejsy, tworzą następujące diagramy składników:

 ![Komponenty zewnętrzne w systemie płatności](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Składniki systemu płatności Kolacja Teraz**

 Ten diagram przedstawia różne typy składników i ich *zależności*. Na przykład zarówno witryna sieci Web Obiad teraz, jak i system płatności w Lucernie wymagają bramy zewnętrznego procesora płatności do sprawdzania poprawności płatności. Strzałki między składnikami reprezentują zależności, które wskazują, które składniki wymagają funkcjonalności innych składników.

 Aby korzystać z systemu płatności Lucerna, witryna internetowa obiad teraz musi zostać zaktualizowana, aby korzystać z interfejsów PaymentApproval i PayableInsertion w systemie płatności Lucerna.

 Na poniższym diagramie przedstawiono określoną konfigurację składników witryny sieci Web Obiad teraz. Ta konfiguracja wskazuje, że każde wystąpienie witryny sieci Web składa się z czterech *części:*

- Proces obsługi klienta

- Proces zamówień

- PrzeglądProcessing

- Paymentprocessing

  Te części są wystąpieniami określonych typów komponentów i są połączone w następujący sposób:

  ![Składniki wewnątrz witryny sieci Web Dinner now](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Składniki wewnątrz witryny sieci Web Obiad teraz**

  Witryna sieci Web Obiad teraz deleguje swoje zachowanie do tych części, które obsługują funkcje witryny sieci Web. Strzałki między komponentem nadrzędnym a jego składnikami członkowskimi pokazują *delegacje,* które wskazują, które części obsługują wiadomości odbierane lub wysyłane przez rodzica za pośrednictwem interfejsów.

  W tej konfiguracji składnik PaymentProcessing przetwarza płatności odbiorcy. W związku z tym musi zostać zaktualizowany w celu integracji z systemem płatności Lucerny. W innych scenariuszach wiele wystąpień typu składnika może istnieć w tym samym składniku nadrzędnym.

  Zobacz:

- [Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)

- [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Rysowanie diagramu komponentów
 Diagram składników ma następujące główne cechy:

- *Składniki,* które reprezentują rozdzielalne elementy funkcjonalności systemu.

- *Pod warunkiem portów interfejsu,* które reprezentują grupy komunikatów lub wywołań, które składniki implementują i są używane przez inne składniki lub systemy zewnętrzne.

- *Wymagane porty interfejsu* reprezentujące grupy komunikatów lub wywołań, które składniki wysyłają do innych składników lub systemów zewnętrznych. Ten rodzaj portu opisuje operacje, których składnik przynajmniej oczekuje od innych składników lub systemów zewnętrznych.

- *Części* są elementami składowymi i są zazwyczaj wystąpieniami innych komponentów. Część jest elementem wewnętrznego projektu komponentu nadrzędnego.

- *Zależności,* które wskazują składniki wymagają funkcji innych składników.

- *Delegacje wskazujące* części składnika obsługują wiadomości wysyłane lub odbierane przez składnik nadrzędny.

  Zobacz:

- [Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)

- [Diagramy składników UML: wskazówki](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Krótki opis: Mocne strony diagramów komponentów
 Diagramy składników ułatwiają wizualizację:

- System jako zbiór rozdzielnych części, niezależnie od ich języka implementacji lub stylu.

- Składniki z dobrze zdefiniowanymi interfejsami, dzięki czemu projekt jest łatwiejszy do zrozumienia i aktualizacji po zmianie wymagań.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-----------------|---------------------|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby zidentyfikować kandydatów do składników, utwórz mapę kodu i zgrupuj elementy według ich funkcji w systemie.<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)|
|Diagramów sekwencji|Wizualizuj sekwencję interakcji między komponentami lub częściami wewnątrz komponentu.<br /><br /> Aby utworzyć linię życia na diagramie sekwencji na podstawie komponentu, kliknij go prawym przyciskiem myszy, a następnie kliknij polecenie **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramy sekwencji UML: Wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagram klasy (UML)|Zdefiniuj interfejsy na dostarczonych lub wymaganych portach i klasach, które implementują funkcjonalność składników.<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: Wskazówki](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram warstw|Opisz logiczną architekturę systemu, ponieważ odnosi się do składników. Użyj sprawdzania poprawności warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów warstw na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy warstw: Wskazówki](../modeling/layer-diagrams-guidelines.md)<br />-   [Sprawdzanie poprawności kodu za pomocą diagramów warstwowych](../modeling/validate-code-with-layer-diagrams.md)|
|Diagramu aktywności|Wizualizuj wewnętrzne przetwarzanie, które składniki wykonują w odpowiedzi na przychodzące wiadomości.<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: Wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Wizualizuj istniejący kod: Mapy kodu
 Mapy kodu pokazują bieżącą organizację i relacje w kodzie. Elementy są reprezentowane przez *węzły* na mapie, a relacje są reprezentowane przez *łącza*. Mapy kodu mogą pomóc w wykonaniu następujących rodzajów zadań:

- Zapoznaj się z nieznanym kodem.

- Dowiedz się, gdzie i jak proponowana zmiana może wpłynąć na istniejący kod.

- Znajdź obszary złożoności, naturalne warstwy lub wzory lub inne obszary, które mogą korzystać z ulepszeń.

  Na przykład obiad teraz należy oszacować koszt aktualizacji PaymentProcessing składnika. Zależy to częściowo od tego, jak bardzo ta zmiana wpłynie na inne części systemu. Aby pomóc im to zrozumieć, jeden z deweloperów obiad teraz generuje mapy kodu z kodu i dostosowuje zakres fokus na obszarach, które mogą mieć wpływ zmiany.

  Na poniższej mapie przedstawiono zależności między PaymentProcessing klasy i innych części systemu Obiad teraz, które pojawiają się wybrane:

  ![Wykres zależności dla systemu płatności Obiad teraz](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Mapa kodu dla systemu płatności Obiad Teraz**

  Deweloper eksploruje mapę, rozszerzając klasę PaymentProcessing i wybierając jej członków, aby zobaczyć obszary, których może dotyczyć:

  ![Metody wewnątrz PaymentProcessing i zależności](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **Metody wewnątrz klasy PaymentProcesssing i ich zależności**

  Generują następującą mapę dla systemu płatności Lucerna, aby sprawdzić jego klasy, metody i zależności. Zespół widzi, że system Lucerny może również wymagać pracy do interakcji z innymi częściami Obiad teraz:

  ![Wykres zależności dla systemu płatności Lucerny](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Mapa kodów dla systemu płatności Lucerna**

  Oba zespoły współpracują ze sobą w celu określenia zmian, które są wymagane do integracji dwóch systemów. Decydują się na refaktoryzacji niektórych kodu, tak aby łatwiej będzie zaktualizować. PaymentApprover Klasa zostanie przeniesione do obszaru nazw DinnerNow.Business i będzie wymagać nowych metod. Dinner Now klasy, które obsługują transakcje będą miały własne obszaru nazw. Zespoły tworzą i używają elementów roboczych do planowania, organizowania i śledzenia ich pracy. Łączą elementy robocze z elementami modelu, gdzie jest to przydatne.

  Po reorganizacji kodu zespoły generują nową mapę kodu, aby zobaczyć zaktualizowaną strukturę i relacje:

  ![Wykres zależności z zreorganizowanym kodem](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **Mapa kodu z zreorganizowanym kodem**

  Ta mapa pokazuje, że PaymentApprover klasa jest teraz w DinnerNow.Business obszaru nazw i ma kilka nowych metod. Klasy transakcji Obiad teraz mają teraz własną przestrzeń nazw PaymentSystem, co ułatwia radzenie sobie z tym kodem później.

#### <a name="creating-a-code-map"></a>Tworzenie mapy kodu

- Aby uzyskać szybki przegląd kodu źródłowego, wykonaj następujące kroki, aby wygenerować mapę kodu:

     W menu **Architektura** kliknij polecenie **Generuj mapę kodu dla rozwiązania**.

     Aby uzyskać szybki przegląd skompilowanego kodu, utwórz pustą mapę kodu, a następnie przeciągnij pliki zestawu lub pliki binarne na powierzchnię mapy.

- Aby eksplorować określone elementy kodu lub rozwiązania, użyj Eksploratora rozwiązań, aby wybrać elementy i relacje, które chcesz wizualizować. Następnie można wygenerować nową mapę lub dodać wybrane elementy do istniejącej mapy. Zobacz [Zależności mapowe między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md).

- Aby ułatwić eksplorowanie mapy, zmień układ tak, aby odpowiadał rodzajom zadań, które chcesz wykonać.

     Na przykład, aby wizualizować warstwy w kodzie, wybierz układ drzewa. Zobacz [Przeglądanie i zmienianie rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Krótki opis: Mocne strony Map Kodowych
 Mapy kodu pomogą Ci:

- Dowiedz się więcej o organizacji i relacjach w istniejącym kodzie.

- Określ obszary, na które może mieć wpływ proponowana zmiana.

- Znajdź obszary złożoności, wzorce, warstwy lub inne obszary, które można poprawić, aby ułatwić jego konserwację, zmianę i ponowne użycie.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opisuje**|
|-----------------|-------------------|
|Diagram warstw|Logiczna architektura systemu. Użyj sprawdzania poprawności warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Aby ułatwić identyfikację istniejących warstw lub zamierzonych warstw, utwórz mapę kodu i zgrupuj powiązane elementy. Aby utworzyć diagram warstwowy, zobacz:<br /><br /> -   [Tworzenie diagramów warstw na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: Wskazówki](../modeling/layer-diagrams-guidelines.md)|
|Diagramów składników|Składniki, ich interfejsy i ich relacje.<br /><br /> Aby ułatwić identyfikację składników, należy utworzyć mapę kodu i grupować elementy według ich funkcji w systemie.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: Wskazówki](../modeling/uml-component-diagrams-guidelines.md)|
|Diagram klasy (UML)|Klasy, ich atrybuty i operacje oraz ich relacje.<br /><br /> Aby ułatwić identyfikowanie tych elementów, należy utworzyć diagram klasy UML, który pokazuje te elementy.<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: Wskazówki](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram klas (oparty na kodzie)|Istniejące klasy w kodzie dla określonego projektu.<br /><br /> Aby wizualizować i modyfikować istniejącą klasę w kodzie, użyj Projektanta klas.<br /><br /> Zobacz [Jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="describe-the-interactions-sequence-diagrams"></a><a name="DescribeSequence"></a>Opis interakcji: Diagramy sekwencji
 Diagramy sekwencji opisują serię interakcji między częściami systemu. Części mogą mieć dowolną skalę. Na przykład mogą one wahać się od poszczególnych obiektów w programie do dużych podsystemów lub podmiotów zewnętrznych. Interakcje mogą być dowolnej skali i typu. Na przykład mogą one wahać się od poszczególnych wiadomości do transakcji rozszerzonych i mogą być wywołania funkcji lub wiadomości usługi sieci Web.

 Aby pomóc Lucerna i obiad teraz opisać i omówić kroki w przypadku użycia płatności procesu, tworzą one następujący diagram sekwencji na diagramie składników. Linie życia odzwierciedlają składnik Witryny sieci Web Obiad teraz i jego części. Komunikaty wyświetlane między liniami życia są zgodne z połączeniami na diagramach składników:

 ![Diagram sekwencji dla przypadku użycia płatności procesowego](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Diagram sekwencji dla przypadku użycia płatności procesu**

 Diagram sekwencji pokazuje, że gdy klient tworzy zamówienie, obiad teraz witryny sieci Web wywołuje ProcessOrder na wystąpienie OrderProcessing. Następnie ZamówienieProcessing wywołuje ProcessPayment na PaymentProcessing. Jest to kontynuowane do momentu, gdy brama zewnętrznego procesora płatności weryfikuje płatność. Tylko wtedy kontrola powraca do witryny sieci Web Obiad teraz.

 Lucerna musi oszacować koszt aktualizacji systemu płatności, aby zintegrować się z systemem Dinner Now. Aby pomóc im to zrozumieć, mogą również utworzyć mapy kodu do wizualizacji kodu, którego dotyczy problem.

 Zobacz:

- [Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)

- [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Rysowanie diagramu sekwencji
 Diagram sekwencji ma następujące główne cechy:

- Pionowe *linie życia* reprezentują aktorów lub wystąpienia obiektów oprogramowania.

   Aby dodać symbol aktora, który wskazuje, że uczestnik znajduje się poza systemem w fazie opracowywania, kliknij linię życia. W oknie **Właściwości** ustaw **pozycję Aktor** na Wartość **True**. Jeśli okno **Właściwości** nie jest otwarte, naciśnij klawisz **F4**.

- *Wiadomości* poziome reprezentują wywołania metody, komunikaty usługi sieci Web lub inną komunikację. Wystąpienia wykonywania są *pionowe* cieniowane prostokąty, które pojawiają się na liniach życia i reprezentują okresy, podczas których odbieranie obiektów proces wywołań.

- Podczas *komunikatu synchroniczowego* obiekt nadawcy czeka na formant, aby <\<zwrócić>> jak w zwykłym wywołaniu funkcji. Podczas wiadomości *asynchronicznego* nadawca może natychmiast kontynuować.

- Użyj <\<tworzenia>> komunikatów, aby wskazać konstrukcję obiektów przez inne obiekty. Powinna to być pierwsza wiadomość wysłana do obiektu.

  Zobacz:

- [Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)

- [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Krótki opis: Mocne strony diagramów sekwencji
 Diagramy sekwencji ułatwiają wizualizację:

- Przepływ kontroli, który przenosi między aktorami lub obiektami podczas wykonywania przypadku użycia.

- Implementacja wywołania metody lub wiadomości.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-----------------|---------------------|
|Diagram klasy (UML)|Zdefiniuj klasy, które reprezentują linie życia oraz parametry i zwracane wartości, które są używane w wiadomościach wysyłanych między liniami życia.<br /><br /> Aby utworzyć klasę z linii życia, kliknij prawym przyciskiem myszy linię życia, a następnie kliknij polecenie **Utwórz klasę** lub **Utwórz interfejs**. Aby utworzyć linię życia z tekstu na diagramie klasy, kliknij go prawym przyciskiem myszy, a następnie kliknij polecenie **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy klas UML: Wskazówki](../modeling/uml-class-diagrams-guidelines.md)|
|Diagramów składników|Opis składników, które reprezentują linie życia i interfejsów, które zapewniają i zużywają zachowanie reprezentowane przez wiadomości.<br /><br /> Aby utworzyć linię życia na diagramie komponentów, kliknij go prawym przyciskiem myszy, a następnie kliknij polecenie **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: Wskazówki](../modeling/uml-component-diagrams-guidelines.md)|
|Diagramów przypadków użycia|Podsumuj interakcje między użytkownikami i składników na diagramie sekwencji jako przypadek użycia, który reprezentuje cel użytkownika.<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: Wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Definiowanie glosariusza typów: diagramy klas
 Diagramy klas definiują jednostki, terminy lub pojęcia, które uczestniczą w systemie i ich relacje ze sobą. Na przykład można użyć tych diagramów podczas tworzenia do opisania atrybutów i operacji dla każdej klasy, niezależnie od ich języka implementacji lub stylu.

 Aby pomóc Lucernie opisać i omówić jednostki, które uczestniczą w przypadku użycia płatności procesu, rysują następujący diagram klasy:

 ![Przetwarzanie jednostek płatności na diagramie klas](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Przetwarzanie encji płatności na diagramie klas**

 Ten diagram pokazuje, że klient może mieć wiele zamówień i różne sposoby płacenia za zamówienia. BankAccount i CreditCard dziedziczą po płatności.

 Podczas opracowywania Lucerna używa następującego diagramu klasy, aby opisać i omówić szczegóły każdej klasy:

 ![Szczegóły jednostki płatności procesowych na diagramie klas](../modeling/media/uml-payment.png "UML_Payment")

 **Szczegóły płatności procesu na diagramie klasy**

 Zobacz:

- [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)

- [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>Rysowanie diagramu klas
 Diagram klasy ma następujące główne cechy:

- Typy, takie jak klasy, interfejsy i wyliczenia:

  - *Klasa* jest definicją obiektów, które mają określone cechy strukturalne lub behawioralne.

  - *Interfejs* definiuje część zewnętrznie widoczne zachowanie obiektu.

  - *Wyliczenie* jest klasyfikatorem, który zawiera listę wartości literału.

- *Atrybuty* są wartościami określonego typu, które opisują każde *wystąpienie klasyfikatora*. Klasyfikator jest ogólną nazwą dla typów, składników, przypadków użycia, a nawet podmiotów.

- *Operacje* są metody lub funkcje, które mogą wykonywać wystąpienia klasyfikatora.

- *Skojarzenie* wskazuje pewnego rodzaju relacji między dwoma klasyfikatorami.

  - *Agregacja* jest skojarzeniem, które wskazuje współwłasność między klasyfikatorami.

  - *Kompozycja* jest skojarzeniem, które wskazuje relację całej części między klasyfikatorami.

    Aby wyświetlić agregacje lub kompozycje, ustaw właściwość **Agregacja** na skojarzeniu. **Udostępnione** pokazuje agregacje i **Composite** pokazuje kompozycje.

- *Zależność* wskazuje, że zmiana definicji jednego klasyfikatora może zmienić definicję innego klasyfikatora.

- *Uogólnienie* wskazuje, że określony klasyfikator dziedziczy część swojej definicji z klasyfikatora ogólnego. *Realizacja* wskazuje, że klasa implementuje operacje i atrybuty oferowane przez interfejs.

   Aby utworzyć te relacje, użyj narzędzia **Dziedziczenie.** Alternatywnie, realizacja może być reprezentowana jako *lizak*.

- *Pakiety* są grupami klasyfikatorów, skojarzeń, linii życia, składników i innych pakietów. *Relacje importu* wskazują, że jeden pakiet zawiera wszystkie definicje innego pakietu.

  Jako punkt wyjścia do eksplorowania i omówienia istniejących klas, można użyć Projektanta klas do tworzenia diagramów klas z kodu.

  Zobacz:

- [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)

- [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Krótki opis: Mocne strony diagramów klasowych
 Diagramy klas ułatwią zdefiniowanie:

- Wspólny glosariusz terminów do użycia podczas omawiania potrzeb użytkowników i jednostek, które uczestniczą w systemie. Zobacz [Wymagania użytkownika modelu](../modeling/model-user-requirements.md).

- Typy, które są używane przez części systemu, takie jak składniki, niezależnie od ich implementacji. Zobacz [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

- Relacje, takie jak zależności, między typami. Na przykład można pokazać, że jeden typ może być skojarzony z wieloma wystąpieniami innego typu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-----------------|---------------------|
|Diagramów przypadków użycia|Zdefiniuj typy, które są używane do opisywania celów i kroków w przypadkach użycia.<br /><br /> Zobacz:<br /><br /> -   [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy przypadków użycia UML: Wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagramu aktywności|Zdefiniuj typy danych, które przechodzą przez węzły obiektów, piny wejściowe, piny wyjściowe i węzły parametrów aktywności.<br /><br /> Zobacz:<br /><br /> -   [Diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktywności UML: Wskazówki](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagramów składników|Opisz składniki, ich interfejsy i ich relacje. Klasa może również opisać kompletny składnik.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: Wskazówki](../modeling/uml-component-diagrams-guidelines.md)|
|Diagram warstw|Zdefiniuj logiczną architekturę systemu, ponieważ odnosi się do klas.<br /><br /> Użyj sprawdzania poprawności warstwy, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów warstw na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy warstw: Wskazówki](../modeling/layer-diagrams-guidelines.md)<br />-   [Sprawdzanie poprawności kodu za pomocą diagramów warstwowych](../modeling/validate-code-with-layer-diagrams.md)|
|Diagramów sekwencji|Zdefiniuj typy linii życia oraz operacje, parametry i wartości zwracane dla wszystkich wiadomości, które mogą odbierać linie życia.<br /><br /> Aby utworzyć linię życia z tekstu na diagramie klasy, kliknij go prawym przyciskiem myszy, a następnie kliknij polecenie **Utwórz linię życia**.<br /><br /> Zobacz:<br /><br /> -   [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Diagramy sekwencji UML: Wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby zidentyfikować klasy, ich relacje i ich metody, należy utworzyć mapę kodu, która pokazuje te elementy.<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-layer-diagrams"></a><a name="DescribeLayers"></a>Opis architektury logicznej: diagramy warstw
 Diagramy warstw opisują logiczną architekturę systemu, organizując artefakty w rozwiązaniu w abstrakcyjne grupy lub *warstwy*. Artefakty mogą być wiele rzeczy, takich jak przestrzenie nazw, projekty, klasy, metody i tak dalej. Warstwy reprezentują i opisują role lub zadania, które artefakty wykonują w systemie. Można również uwzględnić sprawdzanie poprawności warstwy w operacji kompilacji i zaewidencjonowania, aby upewnić się, że kod pozostaje zgodny z jego projektem.

 Aby zachować kod zgodne z projektem, Obiad teraz i Lucerna użyj następującego diagramu warstwy, aby sprawdzić poprawność ich kodu w miarę jego ewolucji:

 ![Schemat warstwowy zintegrowanego systemu płatności](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagram warstwowy na kolację teraz zintegrowany z Lucerną**

 Warstwy na tym diagramie łącze do odpowiednich artefaktów rozwiązania obiad teraz i Lucerny. Na przykład warstwy biznesowej łączy się z DinnerNow.Business namespace i jego członków, które teraz obejmują PaymentApprover klasy. Warstwa dostępu do zasobów łączy się z obszarem nazw DinnerNow.Data. Strzałki lub *zależności*określają, że tylko warstwa Biznesowa może korzystać z funkcji w warstwie Dostęp do zasobów. Gdy zespoły aktualizują swój kod, sprawdzanie poprawności warstwy jest wykonywane regularnie, aby przechwytywać konflikty w miarę ich występowania i pomagać zespołom w ich szybkim rozwiązywaniu.

 Zespoły współpracują ze sobą, aby stopniowo integrować i testować oba systemy. Najpierw upewnij się, że PaymentApprover i reszta Obiad Teraz pracować ze sobą pomyślnie, zanim zajmą się PaymentProcessing.

 Poniższa mapa kodu pokazuje nowe połączenia między obiad teraz i PaymentApprover:

 ![Zaktualizowany wykres zależności ze zintegrowanym systemem](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Mapa kodu ze zaktualizowanymi wywołaniami metod**

 Po potwierdzeniu, że system działa zgodnie z oczekiwaniami, Obiad teraz komentuje paymentprocessing kod. Raporty sprawdzania poprawności warstwy są czyste, a wynikowa mapa kodu pokazuje, że nie istnieje więcej zależności PaymentProcessing:

 ![Wykres zależności bez płatnościProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **Mapa kodu bez płatnościProcessing**

#### <a name="drawing-a-layer-diagram"></a>Rysowanie diagramu warstwowego
 Diagram warstwowy ma następujące główne cechy:

- *Warstwy* opisują logiczne grupy artefaktów.

- *Łącze* jest skojarzeniem między warstwą a artefaktem.

   Aby utworzyć warstwy z artefaktów, przeciągnij elementy z Eksploratora rozwiązań, map kodu, widoku klasy lub przeglądarki obiektów. Aby narysować nowe warstwy, a następnie połączyć je z artefaktami, użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu, aby utworzyć warstwy, a następnie przeciągnij elementy do tych warstw.

   Liczba na warstwie pokazuje liczbę artefaktów połączonych z warstwą. Te artefakty mogą być przestrzeniami nazw, projektami, klasami, metodami i tak dalej. Podczas interpretacji liczby artefaktów na warstwie należy pamiętać o następujących kwestiach:

  - Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

  - Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

    Aby wyświetlić artefakty połączone z warstwą, kliknij ją prawym przyciskiem myszy, a następnie kliknij polecenie **Wyświetl łącza,** aby otworzyć **Eksploratora warstw**.

- Zależność wskazuje, że jedna *warstwa* może korzystać z funkcji w innej warstwie, ale nie odwrotnie. *Zależność dwukierunkowa* wskazuje, że jedna warstwa może korzystać z funkcji w innej warstwie i na odwrót.

   Aby wyświetlić istniejące zależności na diagramie warstwowym, kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij polecenie **Generuj zależności**. Aby opisać zamierzone zależności, narysuj nowe.

  Zobacz:

- [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)

- [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Krótki opis: Mocne strony diagramów warstwowych
 Diagramy warstwowe pomagają:

- Opisz logiczną architekturę systemu zgodnie z funkcjonalnością jego artefaktów.

- Upewnij się, że kod w fazie rozwoju jest zgodny z określonym projektem.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-----------------|---------------------|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby utworzyć warstwy, wygeneruj mapę kodu, a następnie pogrupuj elementy na mapie jako potencjalne warstwy. Przeciągnij grupy z mapy na diagram warstwowy.<br /><br /> Zobacz:<br /><br /> -   [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Przeglądanie i zmienianie rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md)|
|Diagramów składników|Opisz składniki, ich interfejsy i ich relacje.<br /><br /> Aby wizualizować warstwy, należy utworzyć diagram komponentów opisujący funkcjonalność różnych komponentów w systemie.<br /><br /> Zobacz:<br /><br /> -   [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy składników UML: Wskazówki](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|------------------|---------------|
|**Fora**|-   [Narzędzia do modelowania & wizualizacji programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modelowanie SDK (NARZĘDZIA DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Zobacz też
 [Wizualizuj kod](../modeling/visualize-code.md) [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md) Korzystanie z modeli w procesie [programowania](../modeling/use-models-in-your-development-process.md) Użyj modeli w [rozwoju Agile Development](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) Sprawdź [poprawność systemu podczas opracowywania](../modeling/validate-your-system-during-development.md) [Rozszerzaj modele I diagramy UML](../modeling/extend-uml-models-and-diagrams.md)
