---
title: 'Diagramy składników UML: Wytyczne dotyczące | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ef8a152293ef5e1cf9137540abb5590eb43c057a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424450"
---
# <a name="uml-component-diagrams-guidelines"></a>Diagramy składników UML: Wytyczne dotyczące
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio, można narysować *diagram składników* Aby wyświetlić strukturę systemu oprogramowania. Aby obejrzeć wideo demonstracyjne, zobacz [Projektowanie struktury fizycznej za pomocą diagramów składników](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Aby utworzyć diagram składników UML na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**.  
  
 Składnik jest jednostką modularną wymienną w jego środowisku. Jego szczegóły wewnętrzne są ukryte, ale ma co najmniej jeden dobrze zdefiniowany *interfejs dostarczany* za pośrednictwem której możliwy jego funkcji. Składnik może mieć też *wymagane interfejsy*. Interfejs wymagany określa, których funkcji lub usług wymaga od innych składników. Łącząc interfejsy dostarczane i wymagane z kilku składników można konstruować większe składniki. Kompletny system oprogramowania może być rozumiany jako składnik.  
  
 Rysowanie diagramów składników ma kilka zalet:  
  
- Myślenie o projekcie w odniesieniu do głównych bloków ułatwia zespołowi deweloperów zrozumienie istniejącego projektu i utworzenie nowego.  
  
- Myślenie o systemie jako o zbiorze składników z dobrze zdefiniowanymi interfejsami dostarczanymi i wymaganymi poprawia rozdzielenie składników. To z kolei sprawia, że projekt łatwiej zrozumieć i łatwiej go zmienić, gdy zmienią się wymagania.  
  
  Można użyć diagramu składników do reprezentowania projektu niezależnie od tego, jaki język lub platforma projektowania są lub będą używane.  
  
## <a name="OtherDiagrams"></a> Relacja z innymi diagramami  
 Diagramów składników możesz używać w połączeniu z innymi diagramami.  
  
|Inny diagram|Pomaga w omawianiu i komunikowaniu tych aspektów projektu|  
|-------------------|--------------------------------------------------------------------|  
|Diagram sekwencji UML|-Interakcje między składnikami systemu<br />-Interakcje między częściami wewnątrz składnika.<br /><br /> Aby uzyskać więcej informacji, zobacz [UML Sequence Diagrams: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).|  
|Diagram klas UML|-Interfejsy składnika. Diagram klas pozwala wymienić metody interfejsu.<br />-Dane przesyłane w parametrach przez interfejsy składników.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramów klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md).|  
|Diagramy aktywności|-Przetwarzanie wewnętrzne wykonywane przez składnik w odpowiedzi na wiadomości przychodzące.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md).|  
|Diagramy warstw|-Logiczne warstw architektury dla składników.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md).|  
  
## <a name="Basics"></a> Podstawowe kroki rysowania diagramów składników  
 Aby uzyskać informacje na temat elementów na diagramach składników, zobacz [diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md).  
  
 Aby uzyskać więcej informacji o sposobie używania diagramów składników w procesie projektowania, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).  
  
> [!NOTE]
> Szczegółowe kroki tworzenia dowolnego diagramu modelowania zawiera są opisane w [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-component-diagram"></a>Aby utworzyć diagram składników  
  
1. Na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**.  
  
2. W obszarze **szablony**, kliknij przycisk **Diagram składników UML**.  
  
3. Nadaj nazwę diagramowi.  
  
4. W **Dodaj do projektu modelowania**, wybierz istniejący projekt modelowania w rozwiązaniu, lub **Utwórz nowy projekt modelowania**, a następnie kliknij przycisk **OK**...  
  
     Pojawi się nowy diagram składników z UML **Diagram składników** przybornika. Przybornik zawiera wymagane elementy i relacje.  
  
### <a name="drawing-components"></a>Rysowanie składników  
 ![Składniki z interfejsami](../modeling/media/uml-compdrawing.png "UML_CompDrawing")  
  
 Tworzenie *składnika* (1) dla poszczególnych głównych jednostek funkcjonalnych w systemie lub w aplikacji.  
  
 Przykłady obejmują aplikację, urządzenie sprzętowe, usługę sieci Web, zestaw .NET, klasę program lub grupę klas, lub dowolny dający się wydzielić segment programu.  
  
##### <a name="to-create-components"></a>Aby utworzyć składniki  
  
1. Kliknij przycisk **składnika** w przyborniku, a następnie kliknij pustą część diagramu.  
  
     \- lub —  
  
     Skopiuj i wklej istniejący składnik.  
  
    1. Znajdź istniejący składnik na diagramie lub w **Eksploratora modelu UML**.  
  
    2. Kliknij prawym przyciskiem myszy składnik, a następnie kliknij przycisk **kopiowania**.  
  
    3. Otwórz diagram, w którym ma się pojawić skopiowany składnik.  
  
    4. Kliknij prawym przyciskiem myszy pustą część diagramu, a następnie kliknij przycisk **Wklej**.  
  
         Kopia składnika pojawi się z nową nazwą.  
  
2. Kliknij nazwę składnika, aby ją zmienić.  
  
3. Jeśli chcesz zobaczyć tylko nagłówek składnika, kliknij podwójną strzałkę (5).  
  
### <a name="showing-the-ports-of-a-component"></a>Wyświetlanie portów składnika  
 A *portu* (2, 3) reprezentuje grupę wiadomości lub wywołania operacji, które przekazać do lub z składnika. Grupa jest opisana przez interfejs, który definiuje typ portu. Port może dostarczać interfejs lub wymagać interfejsu.  
  
 Port o *interfejsem dostarczanym* (2) dostarcza operacje implementowane przez składnik, a które mogą być używane przez inne składniki.  
  
 Przykłady obejmują interfejs użytkownika, usługę sieci Web, interfejs .NET lub kolekcję funkcji w dowolnym języku programowania.  
  
 Port o *wymaganego interfejsu* (3) reprezentuje wymagania składnika dla grupy operacji lub usług dostarczanych przez inne składniki lub systemy zewnętrzne.  
  
 Na przykład przeglądarka sieci Web wymaga serwerów sieci Web lub dodatek aplikacji wymaga usług od aplikacji.  
  
 Składnik może mieć dowolną liczbę portów.  
  
##### <a name="to-add-ports-to-a-component"></a>Aby dodać porty do składnika  
  
1. W przyborniku kliknij **interfejs dostarczany** lub **interfejs wymagany**.  
  
2. Kliknij składnik, który chcesz do niego dodać.  
  
    Port pojawia się na granicy składnika.  
  
    Nowy interfejs jest tworzony jako typ portu. Ten interfejs jest wyświetlany w **Eksploratora modelu UML**.  
  
3. Przeciągnij port wokół granicy składnika, aby go umieścić w odpowiednim miejscu.  
  
4. Przeciągnij etykietę portu, aby dopasować jej położenie.  
  
5. Kliknij etykietę, aby ją zmienić. Etykieta zawiera nazwę interfejsu. Jeśli ją zmienisz, zmienisz nazwę interfejsu.  
  
   Jeśli chcesz wyświetlić listę atrybutów i operacji interfejsu, możesz to zrobić dodając je do interfejsu w Eksploratorze modelu UML. Możesz też przeciągnąć interfejs z Eksploratora modelu UML do diagramu klasy i dodać operacje i atrybuty.  
  
### <a name="linking-between-components"></a>Tworzenie powiązań między składnikami  
 Użyj zależność (4), aby pokazać, że wymaganie jednego składnika może być spełnione przez operacje lub usługi zapewniane przez inny składnik.  
  
##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Aby pokazać, że interfejs dostarczany może spełnić interfejs wymagany  
  
1. W przyborniku kliknij **zależności**.  
  
2. Kliknij port, z interfejsem wymaganym jednego ze składników, a następnie kliknij port z interfejsem dostarczanym w innym składniku.  
  
   Należy unikać projektowania pętli zależności, w których każdy składnik w grupie zależy od wszystkich innych składników.  
  
##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Aby dodać port dla istniejącego interfejsu do składnika  
  
- Znajdź interfejs w **Eksploratora modelu UML** i przeciągnij go stamtąd do składnika.  
  
     —lub—  
  
- Skopiuj i wklej odwołanie do interfejsu z diagramu.  
  
    1. Na diagramie klasy lub diagramie składników kliknij prawym przyciskiem myszy interfejs, a następnie kliknij przycisk **kopiowania**.  
  
    2. Na diagramie składników kliknij prawym przyciskiem myszy składnik, a następnie kliknij przycisk **Wklej odwołanie**.  
  
         Podany interfejs pojawi się w składniku. W pobliżu pojawi się Tag akcji.  
  
        > [!NOTE]
        > Jeśli używasz **Wklej** zamiast **Wklej odwołanie**, zostanie utworzony nowy interfejs z nową nazwą.  
  
    3. Jeśli chcesz utworzyć interfejs wymagany, kliknij tag akcja, a następnie kliknij przycisk **przekonwertuj na interfejs wymagany**.  
  
## <a name="Parts"></a> Wyświetlanie wewnętrznych części składnika  
 ![Diagram składników wyświetlanie wewnętrznych części](../modeling/media/uml-compshowing.png "UML_CompShowing")  
  
 Części (3) możesz umieścić w składniku (1), aby pokazać, jak jest zbudowany z mniejszych składników współdziałających ze sobą.  
  
 Z diagramu na ilustracji wynika, że każde wystąpienie usługi sieci Web typu Dinner Now zawiera jedno wystąpienie serwera klienta i jedno wystąpienie serwera kuchni.  
  
 Część jest właściwością jej składnika nadrzędnego, podobnie jak atrybut należy do zwykłej klasy. Część ma własny typ, który zazwyczaj jest również składnikiem. Etykieta części ma tę samą postać co zwykły atrybut:  
  
 `+ partName : TypeName`  
  
 Wewnątrz składnika nadrzędnego każda część pokazuje interfejs dostarczany i wymagany zdefiniowane dla jego typu (4, 5). Operacje lub usługi wymagane przez jedną część mogą być zapewniane przez inną. Możesz użyć **zestaw części** łączników, aby pokazać, jak części są połączone ze sobą (6).  
  
 Można również pokazać, że interfejs składnika nadrzędnego jest faktycznie dostarczany lub wymagany przez jedną z jego części. Port nadrzędny można połączyć do portu wewnętrznej części za pomocą **delegowania** relacji (9). Dwa porty muszą być tego samego rodzaju (dostarczane lub wymagane) i typy ich interfejsów powinny być zgodne.  
  
 Możesz utworzyć nową część nowego typu lub z istniejącego typu.  
  
#### <a name="to-add-parts-to-a-component"></a>Aby dodać części do składnika  
  
1. Utwórz część dla wszystkich głównych jednostek funkcjonalnych, które uważasz za część składnika nadrzędnego.  
  
    1. Kliknij przycisk **składnika** w przyborniku, a następnie kliknij wewnątrz składnika nadrzędnego (1).  
  
         Nowa część (3) pojawia się wewnątrz składnika nadrzędnego.  
  
         Nowy składnik jest tworzony w **Eksploratora modelu UML**. Jest to typ nowej części.  
  
         \- lub —  
  
         Przeciągnij istniejący składnik z Eksploratora modelu UML na składnik nadrzędny.  
  
         Nowa część (3) pojawia się wewnątrz składnika nadrzędnego. Jego typem jest składnik przeciągnięty z Eksploratora modelu UML.  
  
         \- lub —  
  
         Kliknij prawym przyciskiem myszy składnik w diagramie lub w Eksploratorze modelu UML, a następnie kliknij przycisk **kopiowania**.  
  
         Kliknij prawym przyciskiem myszy w składniku nadrzędnym, a następnie kliknij przycisk **Wklej odwołanie**.  
  
         Nowa część (3) pojawia się wewnątrz składnika nadrzędnego. Jego typem jest składnik, który został skopiowany.  
  
    2. Kliknij nazwę nowej części, aby ją zmienić. Nie możesz zmienić jego typu.  
  
    3. Do nowej części możesz dodać interfejsy dostarczany i wymagany (4, 5). Kliknij przycisk **interfejs dostarczany** lub **interfejs wymagany** narzędzia, a następnie kliknij przycisk w części.  
  
         \- lub —  
  
         Przeciągnij istniejący interfejs z **Eksploratora modelu UML** na część.  
  
         Interfejsy są dodawane do typu części i pojawiają się w samej części. Składnik nadrzędny dostosowuje jego rozmiar w razie potrzeby.  
  
2. Połącz części ze sobą.  
  
    - Użyj **zależności** narzędzie, aby połączyć porty różnych części (6).  
  
3. Połącz części z portami składnika nadrzędnego:  
  
    1. Utwórz co najmniej jeden port (7) w składniku nadrzędnym. Kliknij przycisk **interfejs wymagany** lub **interfejs dostarczany** w przyborniku, a następnie kliknij składnik nadrzędny.  
  
    2. Oddeleguj (9) port do jednej lub kilku części (9). Kliknij przycisk **delegowania** narzędzia, a następnie port w składniku nadrzędnym, a następnie port w części. W taki sam sposób możesz połączyć porty, które dostarczają interfejsy lub wymagają interfejsów.  
  
### <a name="showing-the-parts-of-a-part"></a>Wyświetlanie części części  
 Po rozłożeniu składnika na części, możesz rozłożyć części każdego typu na wewnętrzne części.  
  
 Najłatwiej przeprowadzić dekompozycji poszczególnych warstw na oddzielnych diagramach składników. Najpierw musisz zlokalizować typ części. Na przykład na ilustracji, jedna z części nosi `DNCustomerServer`, a jej typ jest składnik o nazwie `CustomerServer`. Można znaleźć ten typ w Eksploratorze modelu UML i umieścić go na innym diagramie. Następnie możesz utworzyć jej własne części wewnętrzne.  
  
##### <a name="to-place-a-parts-type-on-a-diagram"></a>Aby umieścić typ części na diagramie  
  
1. Określ w pełni kwalifikowaną nazwę typu części.  
  
     Kliknij część prawym przyciskiem myszy, a następnie kliknij przycisk **właściwości**.  
  
     Nazwa typu jest wyświetlana w **typu** pola w oknie właściwości.  
  
2. Zlokalizuj typ części w **Eksploratora modelu UML**.  
  
     Kliknij przycisk **widoku**, wskaż polecenie **Windows inne**, a następnie kliknij przycisk **Eksploratora modelu UML**.  
  
     Rozwiń ten projekt i, jeśli to konieczne, dowolny pakiet, do którego należy typ.  
  
     Typ będzie wymieniony jako **składnika**.  
  
     Jeśli chcesz, możesz tutaj zmienić jego nazwę.  
  
3. Otwórz lub utwórz inny diagram składników.  
  
4. Przeciągnij typ z Eksploratora modelu UML do diagramu.  
  
     Widok typu pojawi się jako składnik na diagramie.  
  
     Ma te same interfejsy, które zostały zdefiniowane dla części.  
  
     Możesz teraz dodać części wewnątrz niego.  
  
## <a name="Designing"></a> Projektowanie składnika  
  
### <a name="describing-how-the-parts-collaborate"></a>Opisywanie, jak współpracują części  
 Możesz narysować diagram sekwencji, aby pokazać, jak części współpracują ze sobą w odpowiedzi na komunikat docierający do składnika nadrzędnego.  
  
 Możesz użyć tych diagramów zarówno do objaśnienia istniejącego składnika, jak i do projektowania nowego składnika.  
  
 Jeśli nadal projektujesz składnik, możesz narysować diagramy sekwencji, zanim postanowisz, jakie części będzie mieć. Możesz użyć diagramów sekwencji do eksperymentowania z różnymi częściami, interfejsami wymaganymi i sekwencjami wiadomości. Narysuj diagramy sekwencji dla najczęściej używanych i najważniejszych przychodzących wiadomości. Następnie możesz utworzyć części w składniku odpowiadające liniom życia, co do których podejmiesz decyzję.  
  
 Użyj diagramów sekwencji do oceny, jak praca systemu jest rozłożona się między różnymi składnikami.  
  
- Jeśli zbyt wiele znajduje się z jednej strony, zaktualizowanie aplikacji prawdopodobnie będzie trudniejsze, niż gdy praca jest rozłożona równomiernie.  
  
- Jeżeli praca jest za bardzo rozłożona i ma wiele interakcji, system może działać źle i być trudny do zrozumienia.  
  
  ![Diagram przedstawiający współpracujących części sekwencji](../modeling/media/uml-compdescparts.png "UML_CompDescParts")  
  
##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Aby narysować diagram sekwencji pokazujący współpracę pomiędzy częściami  
  
1. Utwórz nowy diagram sekwencji.  
  
     Aby uzyskać więcej informacji, zobacz [UML Sequence Diagrams: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).  
  
2. Utwórz linię życia dla zewnętrznego składnika, użytkownika, urządzenia lub innego aktora (1), który wysyła wiadomości do tego składnika.  
  
     Możesz ustawić **aktora** właściwości tej linii życia na wartość true, aby wskazać, że jest zewnętrzna dla rozważanego. Nad linią życia pojawi się kreska.  
  
3. Utwórz linię życia dla interfejsu dostarczanego (2) tego składnika, do której wybrany aktor wysyła wiadomości.  
  
4. Utwórz linię życia dla każdej części (3) składnika.  
  
5. Utwórz linię życia dla każdego interfejsu wymaganego (4) składnika.  
  
6. Narysuj wiadomości od zewnętrznego aktora (5). Pokaż, jak wiadomości są przekazywane do części i jak części współpracują w odpowiedzieć na wiadomość.  
  
7. Gdy jest to konieczne, pokaż wiadomości wysyłane do wymaganego interfejsu [6]. Nie pokazuj żadnych szczegółów w ramach przetwarzania wiadomości.  
  
### <a name="is-the-component-more-than-its-parts"></a>Czy składnik jest czymś więcej niż częścią?  
 W niektórych przypadkach składnik nie jest niczym więcej niż nazwą nadaną kolekcji części. Wszystkie prace wykonywane przez części, a w czasie wykonywania nie ma kodu ani innego artefaktu reprezentującego składnik.  
  
 Możesz to zasygnalizować w modelu, ustawiając **czy wystąpienie utworzono pośrednio** właściwości składnika. W takim przypadku wszystkie interfejsy składnika powinny znaleźć się na portach z delegacją do wewnętrznych części.  
  
### <a name="describing-the-process-inside-each-part"></a>Opisywanie procesu wewnątrz każdej części  
 Możesz użyć diagramów aktywności, aby pokazać, jak składnik przetwarza każdą przychodzącą wiadomość. Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Diagram aktywności z buforu danych](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")  
  
 Użyj opcji Zaakceptuj akcję zdarzenia (1), aby pokazać, że wiadomości przychodzące rozpoczynają nowy wątek.  
  
 Użyj węzłów obiektów i pinów wejścia/wyjścia, aby pokazać przepływ informacji oraz, gdzie są zapisywane informacje. W przykładzie węzeł obiektu (2) służy do pokazywania buforowanych wiadomości między jednym wątkiem i innym.  
  
### <a name="defining-data-and-classes"></a>Definiowanie klas i danych  
 Możesz użyć diagramu klas UML do opisania szczegółowej treści:  
  
- Interfejsów składnika. Podczas dodawania portu dostarczania lub wymagania do składnika, w Eksploratorze modelu UML pojawia się interfejs. Możesz je przeciągać lub kopiować to do diagramu klas UML, aby pokazać jego atrybuty i operacje, i relacje z innymi interfejsami.  
  
- Dane przekazywane w parametrach operacji w interfejsach.  
  
- Dane przechowywane w składnikach, na przykład, jak pokazano w przepływach obiektu w diagramie aktywności.  
  
### <a name="general-dependencies-between-components"></a>Ogólne zależności między składnikami  
 Możesz użyć diagramu składników tylko po to, by pokazać główne części projektu i ich współzależności.  
  
 ![Zależności między składnikami](../modeling/media/uml-compdepend.png "UML_CompDepend")  
  
 Użyj **zależności** narzędzie, aby narysować zależność. Oznacza to, że projekt jednego składnika opiera się na innym.  
  
 Typowe rodzaje zależności obejmują:  
  
- Jeden składnik wywołuje kod w drugim.  
  
- Jeden składnik tworzy wystąpienia klasy, która jest zdefiniowana w innej klasie.  
  
- Jeden składnik używa informacji utworzonych przez inny składnik.  
  
  Możesz użyć nazwy strzałki zależności do oznaczenia szczególnego rodzaju użycia. Aby ustawić nazwę, kliknij prawym przyciskiem myszy strzałkę, a następnie kliknij przycisk **właściwości**i ustaw **nazwa** pola w oknie dialogowym właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Wideo: Projektowanie struktury fizycznej za pomocą diagramów składników](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)
