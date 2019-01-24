---
title: Modelowanie wymagań użytkowników | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03f1fe9f2cb159e4a6d6db5ded46907b5944471e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758437"
---
# <a name="model-user-requirements"></a>Wymagania modelu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio pozwala zrozumieć, omówienia i komunikują się potrzeby użytkowników, rysując diagramy dotyczące ich działania i część systemu jest odtwarzany w pozwala im to osiągnąć swoje cele. Modelu wymagań to zbiór tych diagramów, z których każdy koncentruje się na inny aspekt potrzeb użytkowników. Aby uzyskać demonstracyjne wideo – zobacz: [Modelowanie domeny biznesowej](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje każdy typ modelu, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Wymagania modelu pomoże Ci:  
  
- Skup się na zachowaniu zewnętrznego systemu, niezależnie od jego wewnętrzną konstrukcją.  
  
- Opis użytkowników i udziałowców wymaga o wiele mniej niejednoznaczności niż w języku naturalnym.  
  
- Zdefiniuj spójne słownik terminów, używane przez użytkowników, deweloperów i testerów.  
  
- Ogranicz luki i niespójności w wymaganiach.  
  
- Zmniejsz czynności niezbędne do reagowania na zmiany wymagań.  
  
- Zaplanuj kolejność, w którym będą opracowywane funkcje.  
  
- Na użytek modele jako podstawa testy systemu, co wyczyść relację między testy i wymagania. Gdy zmienią się wymagania tę relację pomaga poprawnie zaktualizować testy. To sprawia, że się, że system spełnia nowe wymagania.  
  
  Modelu wymagań zapewnia największe korzyści, jeśli go użyć do dyskusji fokus z użytkowników lub ich przedstawicieli, a go ponownie na początku każdej iteracji. Nie masz Oznacz go jako ukończony szczegółowo przed napisaniem kodu. Częściowo działającą aplikację, nawet wtedy, gdy znacznie uproszczone, zazwyczaj są podstawą najbardziej pobudzania dyskusję na temat wymagań użytkowników. Model jest efektywny sposób podsumowywania wyniki tych dyskusji. Aby uzyskać więcej informacji, zobacz [używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
>  W tych tematach "system" oznacza system lub aplikację, którą tworzysz. Może być duży zbiór wielu składniki sprzętu i oprogramowania; lub pojedynczej aplikacji; lub składnik oprogramowania w systemie większe. W każdym przypadku modelu wymagań w tym artykule opisano zachowanie, które nie jest widoczny spoza systemu, czy za pośrednictwem interfejsu użytkownika lub interfejsu API.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Można utworzyć kilka różnych widoków wymagań użytkowników.  Każdy widok zawiera określonego typu informacji.  Podczas tworzenia tych widoków, najlepiej jest często przenieść z jednego do drugiego. Można uruchomić w dowolnym widoku.  
  
|Diagram lub dokumentu|Znaczenie w modelu wymagań|Sekcja|  
|-------------------------|-----------------------------------------------|-------------|  
|Diagramów przypadków użycia|Kto korzysta z systemu i co robią z nim.|[Opisujący sposób użycia systemu](#UseCases)|  
|Diagram koncepcyjny klas|Słownik typów, które są używane do opisywania wymagania dotyczące programu typy widoczne w interfejsie systemu.|[Definiowanie terminy używane do opisu wymagań](#RequirementsClasses)|  
|Diagramu aktywności|Przepływ pracy i informacji między działania wykonywane przez użytkowników i system lub jej części.|[Przepływ pracy przedstawiający między użytkownikami a systemem](#Workflow)|  
|Diagramów sekwencji|Sekwencja interakcji między użytkownikami i systemu lub jego części. Alternatywny widok na diagramie aktywności.|[Wyświetlanie interakcje między użytkownikami a systemem](#Sequences)|  
|Dodatkowe dokumenty lub elementy robocze|Kryteria wydajności, bezpieczeństwa, użyteczność i niezawodność.|[Opisujące jakości wymagań](#QoSRequirements)|  
|Dodatkowe dokumenty lub elementy robocze|Ograniczenia i reguły nie jest specyficzne dla danego przypadku użycia|[Wyświetlanie reguły biznesowe](#BusinessRules)|  
  
 Należy zauważyć, że większość typów diagram może służyć do innych celów. Omówienie typów na diagramie, zobacz [tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md). Aby uzyskać podstawowe informacje na temat rysowania diagramów zobacz [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
##  <a name="UseCases"></a> Opisujący sposób użycia systemu  
 Utwórz diagramy przypadków użycia do opisywania, który korzysta z systemu i rzeczywiste użycie go do. Przypadek użycia przedstawia cel użytkownika systemu i procedury działają do osiągnięcia celu.  
  
 Na przykład online posiłku sprzedaży systemu muszą zezwalać na klienci mogą wybierać elementy menu i muszą zezwalać na udostępnianie restauracji na aktualizowanie menu. Umożliwia to podsumowanie na diagramie przypadków użycia:  
  
 ![Zastosowań klient i restauracja](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")  
  
 Można również pokazać, jak przypadek użycia składa się z mniejszych przypadków. Na przykład zamawianie posiłku jest częścią kupowania posiłek, która obejmuje też płatności i dostawy:  
  
 ![System uczestniczy w płatności, ale nie dostarczania. ](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")  
  
 Można również pokazać, które przypadki użycia znajdują się w zakresie systemu, który tworzysz. Na przykład system na ilustracji nie uczestniczy w przypadku użycia posiłku dostarczania. Dzięki temu, Ustaw kontekst prace deweloperskie. (Na diagramie przypadków użycia podsystemu kontenerów może służyć do reprezentowania systemu lub jego składniki.)  
  
 Pomaga również zespołowi omówiono, jakie zostaną uwzględnione w kolejnych wersjach. Na przykład, można omawiać czy w wersji początkowej systemu płatności dla posiłku są rozmieszczone bezpośrednio między restauracji i klienta, zamiast przechodzenia przez system. W takim przypadku można przenieść płacisz posiłku poza prostokąt System firmy Dinner Now we wstępnym wydaniu.  
  
 Diagram przypadków użycia zawiera jedynie podsumowanie przypadków użycia. Aby zapewnić bardziej szczegółowy opis, można połączyć przypadki użycia na diagramie aby oddzielić dokumentów i z innymi diagramami. Aby dowiedzieć się, jak to zrobić, zobacz [łączenie wariantów użycia z dokumentami i diagramami](../modeling/link-a-use-case-to-documents-and-diagrams.md).  
  
 Rysowanie diagramu przypadków użycia, pomaga Twojemu zespołowi:  
  
- Skup się na Użytkownicy oczekują sposób korzystania z systemu, bez trwa efektów, szczegóły implementacji.  
  
- Omówiono w zakresie systemu lub konkretnej wersji systemu.  
  
  Więcej informacji można znaleźć w następujących tematach:  
  
|Aby dowiedzieć się więcej o|Odczyt|  
|--------------------|----------|  
|Bardziej szczegółowe informacje o sposobie tworzenia przypadków użycia|[Diagramy przypadków użycia UML: Wytyczne dotyczące](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Elementy na diagramie przypadków użycia|[Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)|  
|Jak tworzyć kod z przypadków użycia|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="RequirementsClasses"></a> Definiowanie terminy używane do opisu wymagań  
 Diagramów klas UML można użyć, które pomogą Ci tworzyć spójne słownictwa koncepcji biznesowych używanych do następujących celów:  
  
- Przez samych użytkowników w celu omówienia ich firm, w którym działa system.  
  
- Do opisania potrzeb użytkowników, na przykład w opisach przypadki użycia, reguł biznesowych i przypadki użycia.  
  
- Typy informacji wymieniane na interfejs API systemu lub za pomocą interfejsu użytkownika.  
  
- Opisy testy systemu, czy akceptacji.  
  
  Gdy są one używane w tym celu, zawartość diagramu klas UML jest wywoływana diagram koncepcyjny klasy. (Nazywane również jest *modelu domeny* lub *modelu klasy analizy*.)  
  
  Na diagramie klasy pojęć możesz wyświetlić tylko te klasy potrzebne w opisach wymagań, bez wyświetlania dowolne szczegółowych informacji na temat wewnętrzną konstrukcją systemu. Diagram nie wyświetla szczegółów wewnętrzną konstrukcją systemu. Użytkownik nie zwykle pokazywałaby operacji lub interfejsów w klasach pojęć.  
  
  Na przykład można narysować tych pojęciach klas systemu firmy Dinner Now:  
  
  ![Classes Menu, Order, Menu Item, Order Item.](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")  
  
  Diagram koncepcyjny klasy zawiera słownik terminów używanych w całym modelu wymagań. Na przykład w szczegółowy opis użycia przypadek zamówienie posiłku, można napisać:  
  
  Klient wybierze *Menu* z którego można skonstruować *kolejności*, a następnie tworzy *kolejność elementów* w *kolejności* , wybierając  *Elementy menu* z *Menu*.  
  
  Zwróć uwagę, jak terminy używane w tym opisie są nazwy klasy w modelu. Diagram usuwa niejednoznaczności z relacji między tymi klasami. Na przykład jego wykazują, że każde zamówienie jest skojarzony z tylko jednym Menu.  
  
  Nieporozumień o wymaganiach użytkowników często można powiązać z nieporozumień o szczegółowe znaczenie słowa. Na przykład większość restauracji będzie wiedzę na temat udostępnionych warunków, Menu i kolejność, ale różnią się element na zamówienie i element menu jest mniej jasne. Wymagania są przedmiotem z zainteresowane strony biznesowe, jest ważne, aby udostępnić te różnice. Diagram klas jest przydatne narzędzie, aby pomóc w określeniu warunków i ich wzajemne relacje.  
  
  Model koncepcyjny klasy można tworzyć podstawowe słownictwo, za pomocą którego można opisać logikę biznesową w systemie. Jednak klasy w oprogramowaniu będzie zazwyczaj znacznie bardziej skomplikowane niż modelu koncepcyjnego, ponieważ implementacji należy wziąć pod uwagę problemów, takich jak wydajność, dystrybucji, elastyczność i innych czynników. Kilka różnych implementacji klasy koncepcyjny często znajdują się w jednym systemie.  
  
  Na przykład zamówień, mogą być reprezentowane w XML, SQL, HTML i języka C# w różnych częściach systemu, w różne interfejsy między częściami. Skojarzenie między zamówienie i Menu mogą być reprezentowane na wiele różnych sposobów, takich jak odwołania w kodzie języka C#, relacje w bazie danych lub zaktualizowana w informacjach odsyłaczy identyfikatory w formacie XML. Jednak mimo tych zmian, model koncepcyjny zawiera ważne informacje, które ma wartość true w każdej części oprogramowania. Diagram klas w przykładzie informuje, że w każdym wykonaniu będą istnieć tylko jeden Menu skojarzone z każdego zamówienia.  
  
  Rysowanie diagramu klas wymagania, pomaga Twojemu zespołowi:  
  
- Zdefiniowanie i ujednolicenie podstawowych pojęć używanych w dyskusji potrzeb użytkowników.  
  
- Wyjaśnienie relacji między tymi terminami.  
  
  Więcej informacji można znaleźć w następujących tematach:  
  
|Aby dowiedzieć się więcej o|Odczyt|  
|--------------------|----------|  
|Bardziej szczegółowe informacje dotyczące znajdowania wymagania dotyczące klas|[Diagramy klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md)|  
|Elementy na diagramie klasy koncepcyjne|[Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)|  
|Jak tworzyć kod z klasy koncepcyjne|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|  
  
 Na diagramie klasy koncepcyjny zwykle nie jest przydatne do umieszczenia strzałki na skojarzenia znacząca. Jest to spowodowane diagramu nie reprezentuje implementację. Asocjacje reprezentują relacje między obiektami w świecie rzeczywistym. Następujące [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia Ustaw strzałki niekierunkowa jako domyślny: [Przykład: Modelowanie domeny UML funkcji](http://go.microsoft.com/fwlink/?LinkId=213849).  
  
##  <a name="BusinessRules"></a> Wyświetlanie reguły biznesowe  
 Reguły biznesowej jest wymagana, która nie jest skojarzony z konkretnego przypadku użycia, należy przestrzegać w całym systemie.  
  
 Wiele reguł biznesowych są ograniczenia relacje klas pojęć. Można napisać te *reguły biznesowe statyczne* jako komentarze skojarzone z odpowiednich klas na diagramie klasy pojęć. Na przykład:  
  
 ![Reguła w komentarzu dołączona do klasy zamówienia. ](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")  
  
 *Reguły biznesowe dynamiczne* ograniczyć dozwolone sekwencja zdarzeń. Na przykład używasz diagramie sekwencji lub działania, aby pokazać, że użytkownik musi zalogować się przed przystąpieniem do wykonywania innych operacji w systemie.  
  
 Jednak wiele dynamiczne reguły może być bardziej efektywne i objęty wyrażona przez zamianę statyczne reguły. Na przykład można dodać atrybutu logicznego rejestrowane w do klasy w model koncepcyjny klasy. Czy dodatek rejestrowane jako postcondition dziennika w przypadku użycia, a następnie dodaj go jako warunek wstępny do większości innych przypadków użycia. Takie podejście umożliwia Unikaj definiowania wszystkich możliwych kombinacji sekwencja zdarzeń. Jest również bardziej elastyczne, gdy trzeba dodać nowych przypadków użycia w modelu.  
  
 Należy zauważyć, że w tym miejscu to o sposób definiowania wymagań i jest niezależne od sposobu implementacji wymagania w kodzie programu.  
  
 Więcej informacji można znaleźć w następujących tematach:  
  
|Aby dowiedzieć się więcej o|Odczyt|  
|--------------------|----------|  
|Bardziej szczegółowe informacje dotyczące znajdowania i rejestrowania reguły biznesowe statyczne|[Diagramy klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md)|  
|Elementy na diagramie klasy koncepcyjne|[Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)|  
|Jak tworzyć kod, który działa zgodnie z regułami biznesowymi|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="QoSRequirements"></a> Opisujące jakości wymagań  
 Istnieje kilka kategorii wymagań dotyczących jakości usługi. Ulepszenia obejmują następujące czynności:  
  
- Wydajność  
  
- Zabezpieczenia  
  
- Użyteczność  
  
- Niezawodność  
  
- Niezawodność  
  
  Niektóre z tych wymagań można uwzględnić w opisach przypadki użycia określonego. Inne wymagania nie są specyficzne dla przypadków użycia i najbardziej efektywne są zapisywane w osobnym dokumencie. Możliwe, to warto stosować się do słownictwa zdefiniowane za pomocą modelu wymagań. W poniższym przykładzie należy zauważyć, że głównym słowa używane wymaganie są tytuły aktorów, przypadki użycia i klas w poprzedniej ilustracji:  
  
  Jeśli restauracji usunie element Menu, gdy klient jest zamawianie posiłku, dowolny element zamówienia, który odwołuje się do tego elementu Menu będą wyświetlane w kolorze czerwonym.  
  
  Więcej informacji można znaleźć w następujących tematach:  
  
|Aby dowiedzieć się więcej o|Odczyt|  
|--------------------|----------|  
|Więcej szczegółowych informacji dotyczących jakości wymagań usługi nagrywania|[Wskazówki dotyczące definiowania jakości wymagań](http://msdn.microsoft.com/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|Dołączanie dodatkowych dokumentów z przypadkami użycia|[Łączenie przypadków użycia z dokumentami i diagramami](../modeling/link-a-use-case-to-documents-and-diagrams.md)|  
|Jak tworzyć kod, który działa zgodnie z jakości wymagań|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Workflow"></a> Przepływ pracy przedstawiający między użytkownikami a systemem  
 Diagram aktywności można użyć, aby pokazać przepływ pracy między różnych przypadków użycia. Jest często przydatny rozpocząć modelu wymagań za pomocą rysowania na diagramie aktywności przedstawiający głównych zadań, które użytkownicy wykonują — zarówno w systemie, jak i poza nim.  
  
 Na przykład:  
  
 ![Działanie z trzech akcji i pętli. ](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")  
  
 Możesz narysować diagramy przypadków użycia i diagramy aktywności, aby wyświetlić różne widoki te same informacje.  Diagram przypadków użycia jest bardziej efektywne, pokazujące zagnieżdżanie mniejszych działań wewnątrz działania większy, ale nie uwzględnia przepływ pracy. Na przykład:  
  
 ![Przypadki użycia dla poprzedniej akcji](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")  
  
 Zwróć uwagę, można również użyć diagramów aktywności opisujący algorytmów w oprogramowaniu, ale w przypadku użycia diagramy dla procesu biznesowego, skupić się na akcjach, które są widoczne poza systemem.  
  
 Więcej informacji można znaleźć w następujących tematach:  
  
|Aby dowiedzieć się więcej o|Odczyt|  
|--------------------|----------|  
|Więcej informacji na temat sposobu definiowania przepływów pracy firmy|[Diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md)|  
|Elementy na diagramie aktywności|[Diagramy aktywności UML: Odwołanie](../modeling/uml-activity-diagrams-reference.md)|  
|Jak tworzyć kodu z diagramów aktywności|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Sequences"></a> Wyświetlanie interakcje między użytkownikami a systemem  
 Diagram sekwencji służy do pokazywania wymiana wiadomości między systemem i aktorów lub między częściami systemu. Dzięki temu widok czynności w przypadku użycia, które wykazują, bardzo sekwencja interakcji. Diagramy sekwencji są szczególnie przydatne w przypadku, gdy istnieją interakcję na kilka stron w przypadku użycia, której system ma również interfejs API.  
  
 Na przykład:  
  
 ![Diagram sekwencji z systemu i aktorów. ](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")  
  
 Jedną z zalet diagramy sekwencji jest łatwo sprawdzić, jakie komunikaty są dostępne w systemie, który jest konstruowanie. Aby zaprojektować systemu, Zamień pojedynczej linii życia systemu oddzielne linię życia dla każdego z jego składników i następnie następuje wyświetlenie interakcje między nimi w odpowiedzi na każdy przychodzący komunikat.  
  
 Więcej informacji można znaleźć w następujących tematach:  
  
|Aby dowiedzieć się więcej o|Odczyt|  
|--------------------|----------|  
|Więcej informacji na temat sposobu definiowania interakcje|[Diagramy sekwencji UML: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Elementy na diagramie sekwencji|[Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)|  
|Jak tworzyć kodu z diagramów sekwencji|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="using-a-model-to-reduce-inconsistencies"></a>Przy użyciu modelu w celu zmniejszenia niespójności  
 Tworzenie modelu zwykle powoduje znaczny spadek niespójności i niejasności w wymaganiach użytkowników. Różne osoby zainteresowane działaniem mają często różne ustalenia świata firm, w którym działa system. W związku z tym pierwsze zadanie jest aby rozwiązać te różnice między dla klientów.  
  
 Można zauważyć, że wiele pytań dotyczących domeny biznesowej naturalnie wystąpić podczas tworzenia modelu. Umieszczając te pytania dla użytkowników, co wpłynie na zredukowanie potrzeby zmiany na późniejszym etapie w projekcie. Poniżej przedstawiono niektóre konkretne pytania, spróbuj odpowiedzieć sobie na początku, a następnie poprosić zainteresowane strony biznesowe czy jasne odpowiedzi:  
  
- Dla każdej klasy modelu wymagań poproś "co przypadek użycia tworzy wystąpienia tej klasy?" Na przykład w zamawianie posiłku usług online, możesz zadawać, "co przypadek użycia tworzy wystąpienia klasy Menu restauracji?" Może to prowadzić do dyskusję na temat sposobu nowej restauracji jest zarejestrowana w usłudze i wspiera jego menu. Możesz zadawać pytania podobne informacje co tworzy lub zmienia atrybuty i asocjacje.  
  
- Dla każdego przypadku użycia w modelu wymagań spróbuj opisu wynik lub postcondition każdego przypadku użycia w słowach dostarczone przez diagramy klas. Jest często przydatny pokazać efekt przypadek użycia przez powstawać wystąpienia klas, przed i po wystąpieniu przypadek użycia. Na przykład jeśli postcondition przypadków użycia jest "element menu jest dodawany do zamówienia klienta", szkic wystąpień klas zamówienie i element Menu. Pokaż skutki przypadek użycia, takie jak nowe łącze lub nowy obiekt w innym kolorze lub nowe rysunku. Prowadzi to często dyskusje na temat jakie informacje są niezbędne w modelu. Mimo że wymagania dotyczące klas bezpośrednio nie dotyczą one z implementacją opisują one systemu będzie potrzebnych do przechowywania i przesyłania informacji.  
  
- Poproś o ograniczenia dotyczące atrybuty i asocjacje, szczególnie ograniczenia obejmujące więcej niż jeden atrybut lub skojarzenia.  
  
- Poproś o prawidłowe i nieprawidłowe sekwencje przypadki użycia, rysowania diagramów sekwencji lub działania w celu przedstawienia ich.  
  
  Dzięki badanie relacje między widokami, które udostępniają różne diagramy, może szybko zrozumieć główne pojęcia, z którymi użytkownicy korzystają, oraz pomóc je, aby zrozumieć, czego potrzebują, z systemu. Można również osiągnąć lepiej zrozumieć, jakie wymagania zainteresowane strony są co najmniej pewne informacje. Możesz zaplanować tworzenie tych funkcji, co najmniej w formie uproszczonej na wczesnym etapie projektu, aby użytkownicy mogli eksperymentować z nimi.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)   
 [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)   
 [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)   
 [Przykładowe rozszerzenie programu VS: Funkcje modelowanie domeny UML](http://go.microsoft.com/fwlink/?LinkId=213849)   
 [Przykładowe rozszerzenie programu VS: Kolor elementów UML przez stereotyp](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Przykładowe rozszerzenie programu VS: Link elementów UML, diagramy, pliki i inne elementy](http://go.microsoft.com/fwlink/?LinkID=213813)   
 [Przykładowe rozszerzenie programu VS: Połączenia kształtów w diagramie UML](http://go.microsoft.com/fwlink/?LinkID=213809)   
 [Wideo: Modelowanie domeny biznesowej](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)
