---
title: 'Diagramy składników UML: wytyczne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297158"
---
# <a name="uml-component-diagrams-guidelines"></a>Diagramy składników UML: Zalecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można narysować *diagram składników* , aby pokazać strukturę systemu oprogramowania. Aby zapoznać się z pokazem wideo, zobacz [Projektowanie struktury fizycznej za pomocą diagramów składników](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Aby utworzyć diagram składników UML, w menu **Architektura** kliknij **Nowy UML lub diagram warstwowy**.

 Składnik jest jednostką modularną wymienną w jego środowisku. Jego elementy wewnętrzne są ukryte, ale zawiera co najmniej jeden poprawnie zdefiniowany *interfejs* , za poorednictwem którego można uzyskać dostęp do jego funkcji. Składnik może również mieć *wymagane interfejsy*. Interfejs wymagany określa, których funkcji lub usług wymaga od innych składników. Łącząc interfejsy dostarczane i wymagane z kilku składników można konstruować większe składniki. Kompletny system oprogramowania może być rozumiany jako składnik.

 Rysowanie diagramów składników ma kilka zalet:

- Myślenie o projekcie w odniesieniu do głównych bloków ułatwia zespołowi deweloperów zrozumienie istniejącego projektu i utworzenie nowego.

- Myślenie o systemie jako o zbiorze składników z dobrze zdefiniowanymi interfejsami dostarczanymi i wymaganymi poprawia rozdzielenie składników. To z kolei sprawia, że projekt łatwiej zrozumieć i łatwiej go zmienić, gdy zmienią się wymagania.

  Można użyć diagramu składników do reprezentowania projektu niezależnie od tego, jaki język lub platforma projektowania są lub będą używane.

## <a name="OtherDiagrams"></a>Relacje z innymi diagramami
 Diagramów składników możesz używać w połączeniu z innymi diagramami.

|Inny diagram|Pomaga w omawianiu i komunikowaniu tych aspektów projektu|
|-------------------|--------------------------------------------------------------------|
|Diagram sekwencji UML|Interakcje między składnikami systemu<br />-Interakcje i między częściami wewnątrz składnika.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md).|
|Diagram klas UML|— Interfejsy składnika. Diagram klas pozwala wymienić metody interfejsu.<br />— Dane wysyłane w ramach interfejsów składników.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md).|
|Diagramy aktywności|— Przetwarzanie wewnętrzne wykonywane przez składnik w odpowiedzi na komunikaty przychodzące.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md).|
|Diagramy warstw|— Logiczne warstwy architektury dla składników.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramy warstwowe: odwołanie](../modeling/layer-diagrams-reference.md).|

## <a name="Basics"></a>Podstawowe kroki do rysowania diagramów składników
 Informacje referencyjne dotyczące elementów na diagramach składników można znaleźć w temacie [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md).

 Aby uzyskać więcej informacji o sposobach używania diagramów składników w procesie projektowania, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

> [!NOTE]
> Szczegółowe instrukcje tworzenia dowolnego diagramu modelowania są opisane w sekcji [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-component-diagram"></a>Aby utworzyć diagram składników

1. W menu **Architektura** kliknij kolejno pozycje **Nowy UML lub diagram warstwowy**.

2. W obszarze **Szablony**kliknij pozycję **diagram składników UML**.

3. Nadaj nazwę diagramowi.

4. W obszarze **Dodaj do projektu modelowania**wybierz istniejący projekt modelowania w rozwiązaniu lub **Utwórz nowy projekt modelowania**, a następnie kliknij przycisk **OK**.

     Nowy diagram składników pojawia się z przybornikiem **diagram składników** UML. Przybornik zawiera wymagane elementy i relacje.

### <a name="drawing-components"></a>Rysowanie składników
 ![Składniki z interfejsami](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 Utwórz *składnik* (1) dla każdej głównej jednostki funkcjonalnej w systemie lub aplikacji.

 Przykłady obejmują aplikację, urządzenie sprzętowe, usługę sieci Web, zestaw .NET, klasę program lub grupę klas, lub dowolny dający się wydzielić segment programu.

##### <a name="to-create-components"></a>Aby utworzyć składniki

1. Kliknij pozycję **składnik** w przyborniku, a następnie kliknij pustą część diagramu.

     \- lub-

     Skopiuj i wklej istniejący składnik.

    1. Znajdź istniejący składnik na diagramie lub w **Eksploratorze modelu UML**.

    2. Kliknij prawym przyciskiem myszy składnik, a następnie kliknij polecenie **Kopiuj**.

    3. Otwórz diagram, w którym ma się pojawić skopiowany składnik.

    4. Kliknij prawym przyciskiem myszy pustą część diagramu, a następnie kliknij przycisk **Wklej**.

         Kopia składnika pojawi się z nową nazwą.

2. Kliknij nazwę składnika, aby ją zmienić.

3. Jeśli chcesz zobaczyć tylko nagłówek składnika, kliknij podwójną strzałkę (5).

### <a name="showing-the-ports-of-a-component"></a>Wyświetlanie portów składnika
 *Port* (2, 3) reprezentuje grupę komunikatów lub wywołań operacji, które przechodzą do lub z składnika. Grupa jest opisana przez interfejs, który definiuje typ portu. Port może dostarczać interfejs lub wymagać interfejsu.

 Port z *interfejsem udostępnionym* (2) dostarcza operacje, które są implementowane przez składnik, i mogą być używane przez inne składniki.

 Przykłady obejmują interfejs użytkownika, usługę sieci Web, interfejs .NET lub kolekcję funkcji w dowolnym języku programowania.

 Port z *interfejsem wymaganym* (3) reprezentuje wymóg składnika dla grupy operacji lub usług dostarczanych przez inne składniki lub systemy zewnętrzne.

 Na przykład przeglądarka sieci Web wymaga serwerów sieci Web lub dodatek aplikacji wymaga usług od aplikacji.

 Składnik może mieć dowolną liczbę portów.

##### <a name="to-add-ports-to-a-component"></a>Aby dodać porty do składnika

1. W przyborniku kliknij pozycję **udostępniony interfejs** lub **wymagany interfejs**.

2. Kliknij składnik, który chcesz do niego dodać.

    Port pojawia się na granicy składnika.

    Nowy interfejs jest tworzony jako typ portu. Ten interfejs jest wyświetlany w **Eksploratorze modelu UML**.

3. Przeciągnij port wokół granicy składnika, aby go umieścić w odpowiednim miejscu.

4. Przeciągnij etykietę portu, aby dopasować jej położenie.

5. Kliknij etykietę, aby ją zmienić. Etykieta zawiera nazwę interfejsu. Jeśli ją zmienisz, zmienisz nazwę interfejsu.

   Jeśli chcesz wyświetlić listę atrybutów i operacji interfejsu, możesz to zrobić dodając je do interfejsu w Eksploratorze modelu UML. Możesz też przeciągnąć interfejs z Eksploratora modelu UML do diagramu klasy i dodać operacje i atrybuty.

### <a name="linking-between-components"></a>Tworzenie powiązań między składnikami
 Użyj zależność (4), aby pokazać, że wymaganie jednego składnika może być spełnione przez operacje lub usługi zapewniane przez inny składnik.

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Aby pokazać, że interfejs dostarczany może spełnić interfejs wymagany

1. W przyborniku kliknij pozycję **zależność**.

2. Kliknij port, z interfejsem wymaganym jednego ze składników, a następnie kliknij port z interfejsem dostarczanym w innym składniku.

   Należy unikać projektowania pętli zależności, w których każdy składnik w grupie zależy od wszystkich innych składników.

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Aby dodać port dla istniejącego interfejsu do składnika

- Znajdź interfejs w **Eksploratorze modelu UML** , a następnie przeciągnij go z tego miejsca na składnik.

     lub

- Skopiuj i wklej odwołanie do interfejsu z diagramu.

    1. Na diagramie klasy lub diagramie składników kliknij prawym przyciskiem myszy interfejs, a następnie kliknij polecenie **Kopiuj**.

    2. Na diagramie składników kliknij prawym przyciskiem myszy składnik, a następnie kliknij polecenie **Wklej odwołanie**.

         Podany interfejs pojawi się w składniku. W pobliżu pojawi się Tag akcji.

        > [!NOTE]
        > Jeśli używasz **wklejania** zamiast **odwołania wklejania**, zostanie utworzony nowy interfejs, który ma nową nazwę.

    3. Jeśli chcesz utworzyć wymagany interfejs, kliknij tag akcji, a następnie kliknij przycisk **Konwertuj na wymagany interfejs**.

## <a name="Parts"></a>Wyświetlanie wewnętrznych części składnika
 ![Diagram składników przedstawiający części wewnętrzne](../modeling/media/uml-compshowing.png "UML_CompShowing")

 Części (3) możesz umieścić w składniku (1), aby pokazać, jak jest zbudowany z mniejszych składników współdziałających ze sobą.

 Z diagramu na ilustracji wynika, że każde wystąpienie usługi sieci Web typu Dinner Now zawiera jedno wystąpienie serwera klienta i jedno wystąpienie serwera kuchni.

 Część jest właściwością jej składnika nadrzędnego, podobnie jak atrybut należy do zwykłej klasy. Część ma własny typ, który zazwyczaj jest również składnikiem. Etykieta części ma tę samą postać co zwykły atrybut:

 `+ partName : TypeName`

 Wewnątrz składnika nadrzędnego każda część pokazuje interfejs dostarczany i wymagany zdefiniowane dla jego typu (4, 5). Operacje lub usługi wymagane przez jedną część mogą być zapewniane przez inną. Łączników **zestawów części** można użyć, aby pokazać, jak części są połączone ze sobą (6).

 Można również pokazać, że interfejs składnika nadrzędnego jest faktycznie dostarczany lub wymagany przez jedną z jego części. Port elementu nadrzędnego można połączyć z portem części wewnętrznej przy użyciu relacji **delegowania** (9). Dwa porty muszą być tego samego rodzaju (dostarczane lub wymagane) i typy ich interfejsów powinny być zgodne.

 Możesz utworzyć nową część nowego typu lub z istniejącego typu.

#### <a name="to-add-parts-to-a-component"></a>Aby dodać części do składnika

1. Utwórz część dla wszystkich głównych jednostek funkcjonalnych, które uważasz za część składnika nadrzędnego.

    1. Kliknij pozycję **składnik** w przyborniku, a następnie kliknij wewnątrz składnika nadrzędnego (1).

         Nowa część (3) pojawia się wewnątrz składnika nadrzędnego.

         Nowy składnik jest tworzony w **Eksploratorze modelu UML**. Jest to typ nowej części.

         \- lub-

         Przeciągnij istniejący składnik z Eksploratora modelu UML na składnik nadrzędny.

         Nowa część (3) pojawia się wewnątrz składnika nadrzędnego. Jego typem jest składnik przeciągnięty z Eksploratora modelu UML.

         \- lub-

         Kliknij prawym przyciskiem myszy składnik, w diagramie lub w Eksploratorze modelu UML, a następnie kliknij polecenie **Kopiuj**.

         Kliknij prawym przyciskiem myszy składnik nadrzędny, a następnie kliknij polecenie **Wklej odwołanie**.

         Nowa część (3) pojawia się wewnątrz składnika nadrzędnego. Jego typem jest składnik, który został skopiowany.

    2. Kliknij nazwę nowej części, aby ją zmienić. Nie możesz zmienić jego typu.

    3. Do nowej części możesz dodać interfejsy dostarczany i wymagany (4, 5). Kliknij wybrany **interfejs** lub narzędzie **interfejsu wymagane** , a następnie kliknij w części.

         \- lub-

         Przeciągnij istniejący interfejs z **Eksploratora modelu UML** na część.

         Interfejsy są dodawane do typu części i pojawiają się w samej części. Składnik nadrzędny dostosowuje jego rozmiar w razie potrzeby.

2. Połącz części ze sobą.

    - Użyj narzędzia **zależność** , aby połączyć porty różnych części (6).

3. Połącz części z portami składnika nadrzędnego:

    1. Utwórz co najmniej jeden port (7) w składniku nadrzędnym. W przyborniku kliknij pozycję **wymagany interfejs** lub **udostępniony interfejs** , a następnie kliknij składnik nadrzędny.

    2. Oddeleguj (9) port do jednej lub kilku części (9). Kliknij narzędzie **delegowanie** , a następnie port w składniku nadrzędnym, a następnie port w części. W taki sam sposób możesz połączyć porty, które dostarczają interfejsy lub wymagają interfejsów.

### <a name="showing-the-parts-of-a-part"></a>Wyświetlanie części części
 Po rozłożeniu składnika na części, możesz rozłożyć części każdego typu na wewnętrzne części.

 Najłatwiej przeprowadzić dekompozycji poszczególnych warstw na oddzielnych diagramach składników. Najpierw musisz zlokalizować typ części. Na przykład, na ilustracji, jedna z części ma nazwę `DNCustomerServer`, a jej typem jest składnik o nazwie `CustomerServer`. Można znaleźć ten typ w Eksploratorze modelu UML i umieścić go na innym diagramie. Następnie możesz utworzyć jej własne części wewnętrzne.

##### <a name="to-place-a-parts-type-on-a-diagram"></a>Aby umieścić typ części na diagramie

1. Określ w pełni kwalifikowaną nazwę typu części.

     Kliknij prawym przyciskiem myszy część, a następnie kliknij pozycję **Właściwości**.

     Nazwa typu pojawia się w polu **typ** okno właściwości.

2. Znajdź typ części w **Eksploratorze modelu UML**.

     Kliknij pozycję **Widok**, wskaż polecenie **inne okna**, a następnie kliknij pozycję **Eksplorator modelu UML**.

     Rozwiń ten projekt i, jeśli to konieczne, dowolny pakiet, do którego należy typ.

     Typ będzie wyświetlany jako **składnik**.

     Jeśli chcesz, możesz tutaj zmienić jego nazwę.

3. Otwórz lub utwórz inny diagram składników.

4. Przeciągnij typ z Eksploratora modelu UML do diagramu.

     Widok typu pojawi się jako składnik na diagramie.

     Ma te same interfejsy, które zostały zdefiniowane dla części.

     Możesz teraz dodać części wewnątrz niego.

## <a name="Designing"></a>Projektowanie składnika

### <a name="describing-how-the-parts-collaborate"></a>Opisywanie, jak współpracują części
 Możesz narysować diagram sekwencji, aby pokazać, jak części współpracują ze sobą w odpowiedzi na komunikat docierający do składnika nadrzędnego.

 Możesz użyć tych diagramów zarówno do objaśnienia istniejącego składnika, jak i do projektowania nowego składnika.

 Jeśli nadal projektujesz składnik, możesz narysować diagramy sekwencji, zanim postanowisz, jakie części będzie mieć. Możesz użyć diagramów sekwencji do eksperymentowania z różnymi częściami, interfejsami wymaganymi i sekwencjami wiadomości. Narysuj diagramy sekwencji dla najczęściej używanych i najważniejszych przychodzących wiadomości. Następnie możesz utworzyć części w składniku odpowiadające liniom życia, co do których podejmiesz decyzję.

 Użyj diagramów sekwencji do oceny, jak praca systemu jest rozłożona się między różnymi składnikami.

- Jeśli zbyt wiele znajduje się z jednej strony, zaktualizowanie aplikacji prawdopodobnie będzie trudniejsze, niż gdy praca jest rozłożona równomiernie.

- Jeżeli praca jest za bardzo rozłożona i ma wiele interakcji, system może działać źle i być trudny do zrozumienia.

  ![Diagram sekwencji przedstawiający wspólne części współpracy](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Aby narysować diagram sekwencji pokazujący współpracę pomiędzy częściami

1. Utwórz nowy diagram sekwencji.

     Aby uzyskać więcej informacji, zobacz [diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md).

2. Utwórz linię życia dla zewnętrznego składnika, użytkownika, urządzenia lub innego aktora (1), który wysyła wiadomości do tego składnika.

     Właściwość **aktora** tej linii życia można ustawić na wartość true, aby wskazać, że jest ona zewnętrzna wobec rozważanego składnika. Nad linią życia pojawi się kreska.

3. Utwórz linię życia dla interfejsu dostarczanego (2) tego składnika, do której wybrany aktor wysyła wiadomości.

4. Utwórz linię życia dla każdej części (3) składnika.

5. Utwórz linię życia dla każdego interfejsu wymaganego (4) składnika.

6. Narysuj wiadomości od zewnętrznego aktora (5). Pokaż, jak wiadomości są przekazywane do części i jak części współpracują w odpowiedzieć na wiadomość.

7. Gdy jest to konieczne, pokaż wiadomości wysyłane do wymaganego interfejsu [6]. Nie pokazuj żadnych szczegółów w ramach przetwarzania wiadomości.

### <a name="is-the-component-more-than-its-parts"></a>Czy składnik jest czymś więcej niż częścią?
 W niektórych przypadkach składnik nie jest niczym więcej niż nazwą nadaną kolekcji części. Wszystkie prace wykonywane przez części, a w czasie wykonywania nie ma kodu ani innego artefaktu reprezentującego składnik.

 Możesz wskazać ten element w modelu, ustawiając właściwość **jest pośrednio skonkretyzowanym** składnika. W takim przypadku wszystkie interfejsy składnika powinny znaleźć się na portach z delegacją do wewnętrznych części.

### <a name="describing-the-process-inside-each-part"></a>Opisywanie procesu wewnątrz każdej części
 Możesz użyć diagramów aktywności, aby pokazać, jak składnik przetwarza każdą przychodzącą wiadomość. Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: wytyczne](../modeling/uml-activity-diagrams-guidelines.md).

 ![Diagram aktywności z buforem danych](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 Użyj opcji Zaakceptuj akcję zdarzenia (1), aby pokazać, że wiadomości przychodzące rozpoczynają nowy wątek.

 Użyj węzłów obiektów i pinów wejścia/wyjścia, aby pokazać przepływ informacji oraz, gdzie są zapisywane informacje. W przykładzie węzeł obiektu (2) służy do pokazywania buforowanych wiadomości między jednym wątkiem i innym.

### <a name="defining-data-and-classes"></a>Definiowanie klas i danych
 Możesz użyć diagramu klas UML do opisania szczegółowej treści:

- Interfejsów składnika. Podczas dodawania portu dostarczania lub wymagania do składnika, w Eksploratorze modelu UML pojawia się interfejs. Możesz je przeciągać lub kopiować to do diagramu klas UML, aby pokazać jego atrybuty i operacje, i relacje z innymi interfejsami.

- Dane przekazywane w parametrach operacji w interfejsach.

- Dane przechowywane w składnikach, na przykład, jak pokazano w przepływach obiektu w diagramie aktywności.

### <a name="general-dependencies-between-components"></a>Ogólne zależności między składnikami
 Możesz użyć diagramu składników tylko po to, by pokazać główne części projektu i ich współzależności.

 ![Zależność między składnikami](../modeling/media/uml-compdepend.png "UML_CompDepend")

 Użyj narzędzia **zależność** , aby narysować zależność. Oznacza to, że projekt jednego składnika opiera się na innym.

 Typowe rodzaje zależności obejmują:

- Jeden składnik wywołuje kod w drugim.

- Jeden składnik tworzy wystąpienia klasy, która jest zdefiniowana w innej klasie.

- Jeden składnik używa informacji utworzonych przez inny składnik.

  Możesz użyć nazwy strzałki zależności do oznaczenia szczególnego rodzaju użycia. Aby ustawić nazwę, kliknij prawym przyciskiem myszy strzałkę, a następnie kliknij pozycję **Właściwości**, a następnie ustaw pole **Nazwa** w oknie właściwości.

## <a name="see-also"></a>Zobacz też
 [Edytuj modele UML i diagramy](../modeling/edit-uml-models-and-diagrams.md) [składników UML diagramy: odniesienia](../modeling/uml-component-diagrams-reference.md) diagramy [sekwencji UML](../modeling/uml-sequence-diagrams-reference.md) : referencyjne diagramy [przypadków użycia UML](../modeling/uml-use-case-diagrams-reference.md) : referencyjne diagramy [klas UML: referencyjne](../modeling/uml-class-diagrams-reference.md) [diagramy składników UML: film referencyjny](../modeling/uml-component-diagrams-reference.md) [: Projektowanie struktury fizycznej za pomocą diagramów składników](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
