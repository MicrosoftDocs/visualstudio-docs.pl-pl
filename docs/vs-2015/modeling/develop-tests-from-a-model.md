---
title: Opracowywanie testów na podstawie modelu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tests and requirements
ms.assetid: 40f87192-ba85-4552-8804-314a678261ae
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c0613e43816e7ef7036c5e13b7abafe90b451b81
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787188"
---
# <a name="develop-tests-from-a-model"></a>Opracowywanie testów na podstawie modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wymagania i modele architektury można użyć, aby ułatwić organizowanie testów systemu i jego składników. Praktyka ta pomaga zagwarantować, że testowania wymagań które są ważne dla użytkowników i innych zainteresowanych stron i pomaga szybko aktualizować testów, gdy zmienią się wymagania. Jeśli używasz [!INCLUDE[TCMext](../includes/tcmext-md.md)], można także utrzymać łącza między modele i testy.  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują tych funkcji, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="system-and-subsystem-testing"></a>System i testowanie podsystemu  
 *Testy systemu,* znany także jako *testy odbiorcze*, oznacza, że sprawdzenie, czy spełnione są wymagania użytkowników. Testy te są zajmującym się ochroną widocznych zewnętrznych zachowań systemu, a nie wewnętrzną konstrukcją.  
  
 Testy systemu są bardzo przydatne, gdy rozszerzenie lub przeprojektowanie systemu. Ułatwiają one należy unikać wprowadzania błędów po zmianie kodu.  
  
 Planując wszelkie zmiany lub rozszerzenie do systemu, warto zacząć od zestawu testów systemowych, korzystających z istniejącego systemu. Następnie można rozszerzyć lub dostosować testy, aby przetestować nowe wymagania, wprowadzić zmiany w kodzie i ponownie uruchom pełny zestaw testów.  
  
 Podczas tworzenia nowego systemu można rozpocząć tworzenie testów, zaraz po rozpoczęciu programowania. Definiując testów przed opracowywanie każdej funkcji, można przechwycić dyskusje wymagania w bardzo określony sposób.  
  
 Testowanie podsystemu dotyczą te same zasady główne składniki systemu. Każdy składnik jest testowane oddzielnie od innych składników. Podsystem testy skoncentrować się na zachowanie widoczne na interfejsy użytkownika składnika lub interfejsu API.  
  
 Aby uzyskać więcej informacji o sposobach uruchamiania testów, zobacz [testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).  
  
## <a name="deriving-system-tests-from-a-requirements-model"></a>Wyprowadzanie testów systemowych z modelu wymagań  
 Można tworzyć i utrzymania relacji między testy systemu i modelu wymagań. Aby ustalić tę relację, piszesz testy, które odpowiadają głównych elementów modelu wymagań. Program Visual Studio pomaga zachować tej relacji przez umożliwienie tworzenia łącza między testy i części modelu. Aby uzyskać więcej informacji na temat modeli wymagania, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
### <a name="write-tests-for-each-use-case"></a>Pisanie testów dla każdego przypadku użycia  
 Jeśli używasz [!INCLUDE[TCMext](../includes/tcmext-md.md)], można utworzyć grupę testów dla każdego przypadku użycia, zdefiniowanego w modelu wymagań. Na przykład jeśli przypadek użycia zamówienie posiłku, który zawiera, Utwórz zamówienie i Dodaj element do zamówienia, można utworzyć testy dla obu ogólnych i bardziej szczegółowe te przypadki użycia. Aby uzyskać więcej informacji dotyczących przypadków użycia, zobacz [diagramy przypadków użycia UML: wskazówki dotyczące](../modeling/uml-use-case-diagrams-guidelines.md).  
  
 Te wytyczne mogą być pomocne:  
  
-   Każdy przypadek użycia powinna mieć kilka testów, dla ścieżki głównej i wyjątkowe wyniki.  
  
-   Opisywane przypadek użycia w modelu wymagań jest niezwykle ważne do definiowania jego postcondition, oznacza to, że cel zostanie osiągnięty, niż do szczegółowego opisywania, procedury użytkownik wykona w celu osiągnięcia celu. Na przykład może być postcondition zamówienia posiłek, restauracja jest przygotowywana posiłek dla klienta, a klient zapłacił. Postcondition jest kryterium, które testy należy sprawdzić.  
  
-   Podstawowy oddzielnych testów na oddzielnych klauzul postcondition. Na przykład utworzyć osobne testów do powiadamiania restauracji kolejności i do celów płatności odbiorcy. Ten rozdział ma następujące zalety:  
  
    -   Zmiany w różnych aspektów wymagania często występują, niezależnie od siebie. Dzieląc testy na różnych aspektach w ten sposób, możesz ułatwić aktualizowanie testów, gdy zmienią się wymagania.  
  
    -   Jeśli plan rozwoju implementuje jednym aspekcie przypadek użycia przed inny, możesz włączyć testy oddzielnie, w miarę postępów rozwoju.  
  
-   Podczas projektowania testy, należy oddzielić wybór danych testowych, od kodu lub skryptu, który określa, czy osiągnięte zostały postcondition. Na przykład może być testu z prostą funkcją arytmetyczne: dane wejściowe 4; Sprawdź, czy dane wyjściowe to 2. Zamiast tego należy projektować skryptu jako: Wybierz dane wejściowe mnożenia danych wyjściowych przez siebie i sprawdź, czy wynik jest oryginalne dane wejściowe. Ten styl umożliwia różne dane wejściowe testu bez wprowadzania zmian w głównej części testu.  
  
#### <a name="linking-tests-to-use-cases"></a>Łączenie testy z przypadkami użycia  
 Jeśli używasz [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] do projektowania i uruchomić testy, możesz organizować testy w ramach wymaganie, przypadek użycia lub elementów roboczych historii użytkownika. Można połączyć te elementy robocze z przypadkami użycia w modelu. Dzięki temu można szybko śledzenia zmiany do testów i przypadek użycia pomaga śledzić postęp każdego z nich.  
  
###### <a name="to-link-tests-to-a-use-case"></a>Aby połączyć testy przypadek użycia  
  
1. W [!INCLUDE[TCMlong](../includes/tcmlong-md.md)], Utwórz wymagania i podstawą zestaw testów. Aby dowiedzieć się, jak to zrobić, zobacz [testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).  
  
    Wymagania, którą tworzysz jest element roboczy w [!INCLUDE[vstsTfsShort](../includes/vststfsshort-md.md)]. Może być elementem pracy scenariusza użycia, wymagania lub przypadek użycia, w zależności od szablonu procesu, który projekt korzysta z [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Aby uzyskać więcej informacji, zobacz [śledzenie pracy za pomocą programu Visual Studio Team Services lub serwera Team Foundation Server](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2. Elementem roboczym należy połączyć jeden lub więcej przypadków użycia w modelu.  
  
    Na diagramie przypadków użycia, kliknij prawym przyciskiem myszy przypadek użycia, a następnie kliknij przycisk **łącze do elementu roboczego**. Aby uzyskać więcej informacji, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).  
  
3. Dodaj do zestawu testów, przypadki testowe, które Sprawdź przypadki użycia.  
  
   Zwykle każdy element roboczy użytkownika, jak użycia lub wymagania połączy się z kilku przypadków użycia w modelu i każdego przypadku użycia połączy się z kilku przypadków użycia lub wymagań. Jest to spowodowane każdego przypadku użycia lub wymagania obejmuje zestaw zadań, które opracowywanie kilka przypadków użycia. Na przykład w wczesnych iteracji projektu, możesz tworzyć historii użytkownika podstawowego, w którym klient może wybierz elementy z wykazu i zostały one dostarczone. W późniejszej iteracji może ona brzmieć, że użytkownik płaci podczas realizacji zamówienia i dostawca otrzymuje pieniądze, po wysłaniu towarów.  Każdy wątek dodaje klauzulę postcondition w przypadku użycia towarów zamówienia.  
  
   Można utworzyć osobne linki od wymagań dla klauzul postcondition, pisząc tych klauzul w oddzielnych komentarze na diagramie przypadków użycia. Każdy komentarz łącza z elementem roboczym wymagania i komentarz łącza do przypadku użycia na diagramie.  
  
### <a name="base-tests-on-the-requirements-types"></a>Podstawowy testy na typy wymagań  
 Typy, które jest, klasy, interfejsy i wyliczenia modelu wymagania opisano pojęcia i relacje pod względem sposobu użytkowników reakcji i komunikacji dotyczących firmy. Wyklucza typy danych tylko z wewnętrzną konstrukcją systemu.  
  
 Projektowanie testów pod względem typów te wymagania. Praktyka ta pomaga zagwarantować, że podczas zmiany z wymaganiami omówiono, łatwo jest dotyczą zmiany niezbędne zmiany w testach. Go umożliwia omówienia testów i ich zamierzonych wyniki bezpośrednio z dla użytkowników końcowych i innych zainteresowanych stron. Oznacza to, musi być obsługiwane poza procesem tworzenia użytkowników i pozwala uniknąć przypadkowego projekt testów wokół możliwe luki w projekcie.  
  
 W przypadku ręcznych testów tej praktyką polega na dostosowanie się do słownictwa używanego w modelu wymagań w skryptach testowych. Dla testów automatycznych tej praktyką obejmuje przy użyciu diagramów klas wymagania jako podstawy dla kodu testów i tworzenie dostępu i updater funkcje połączyć modelu wymagań w kodzie.  
  
 Na przykład wymagania, które mogą obejmować modelu typy Menu, element Menu, zamówienie i skojarzenia między nimi. Ten model reprezentuje informacje są przechowywane omawiają posiłku system zamawiania, ale nie reprezentuje komplikacje związane z jego wykonania. W działającym systemie może być kilka różnych realizations każdego typu, w przypadku baz danych w interfejsie użytkownika i interfejsów API. W rozproszonym systemie może być kilka wariantów każde wystąpienie, przechowywane w różnych częściach systemu, w tym samym czasie.  
  
 Aby przetestować przypadek użycia, takie jak dodawanie elementu do zamówienia, metody testowej może zawierać kod podobny do następującego:  
  
```  
Order order = … ; // set up an order  
// Store prior state:  
int countBefore = order.MenuItems.Count;   
// Perform use case:  
MenuItem chosenItem = …; // choose an item  
AddItemToOrder (chosenItem, order);   
// Verify part of postcondition:  
int countAfter = order.MenuItems.Count;  
Assert (countAfter == countBefore = 1);   
```  
  
 Należy zauważyć, że ta metoda używa klasy modelu wymagań. Skojarzenia i atrybuty są realizowane jako właściwości .NET.  
  
 Aby wprowadzić tę pracę, właściwości klasy musi być zdefiniowany jako tylko do odczytu funkcje lub metody dostępu, których dostęp do systemu, aby pobrać informacje o bieżącym stanie. Przypadki użycia metod, które symulują, takie jak AddItemToOrder musi dysku systemu za pośrednictwem jej interfejsu API lub warstwy poniżej interfejs użytkownika. Konstruktory testu obiektów, takich jak zamówienie i element MenuItem musi także zwiększać wykorzystanie systemu, aby utworzyć odpowiednie elementy w systemie.  
  
 Wiele metod dostępu i metod aktualizowania już będą dostępne za pośrednictwem interfejsu API normalne aplikacji. Ale niektóre dodatkowe funkcje mogą mieć do zapisania w celu umożliwienia badania. Te dodatkowe metody dostępu i metod aktualizowania czasami są nazywane "Instrumentacji testów". Ponieważ są one zależne od wewnętrznego projektu systemu, spoczywa deweloperów systemu zapewnić im, natomiast testerów pisanie kodu testów pod względem modelu wymagań.  
  
 Podczas pisania testów automatycznych, można użyć podczas testów generycznych do opakowania metody dostępu i metod aktualizowania. Aby uzyskać więcej informacji, zobacz [tworzenia automatycznych, testów plik wykonywalny przy użyciu testów ogólnych](http://msdn.microsoft.com/library/b8dadaf4-4473-49c5-a0d9-46eca9e65d52).  
  
### <a name="tests-for-business-rules"></a>Testy dla reguły biznesowe  
 Niektóre wymagania nie są bezpośrednio związane z dowolnego przypadku użycia jednej. Na przykład firma DinnerNow umożliwia klientom wybrać z menu wiele, ale wymaga, aby w każdej kolejności, wszystkie wybrane elementy powinny pochodzić z pojedynczym Menu. Tę regułę biznesową, może być wyrażona jako niezmiennej dotyczących skojarzeń zamówienia, menu i elementy w modelu klasy wymagań.  
  
 Regułę niezmiennej, tego rodzaju decyduje, nie tylko wszystkie przypadki użycia, które są obecnie zdefiniowane, ale również wszelkich innych przypadków użycia, które będą zdefiniowane później. Dlatego jest przydatne do zapisu w oddzielnie od wszelkich przypadków użycia i przetestować go oddzielnie z przypadkami użycia.  
  
 Reguła biznesowa niezmiennej można napisać jako komentarz na diagramie klasy. Aby uzyskać więcej informacji, zobacz [UML Class Diagrams: wskazówki dotyczące](../modeling/uml-class-diagrams-guidelines.md).  
  
 Testy można połączyć reguły biznesowej, łącząc komentarz do wymagań lub użytkownika historii elementu roboczego, którą można połączyć do zestawu testów w [!INCLUDE[TCMlong](../includes/tcmlong-md.md)]. Aby uzyskać więcej informacji, zobacz [dołączanie przypadków testowych z elementami modelu](#Attaching).  
  
 Wydajności i jakości inne wymagania dotyczące usługi można zauważyć w komentarzach, w przypadku użycia, działania lub diagramów sekwencji. Możesz połączyć je także do wymaganych elementów roboczych i ich zestawy testów.  
  
### <a name="sequence-and-activity-diagrams-for-tests"></a>Sekwencji i diagramy aktywności testów  
 Jeśli Twoje wymagania lub modele architektury obejmują sekwencji i diagramy aktywności, można napisać testy, które należy wykonać diagramy bezpośrednio.  
  
 Czasami jest przydatny do projektowania testy, które są dynamicznie wybierz różnych ścieżek za pośrednictwem gałęzie i pętle w diagramie.  
  
 Spróbuj sprawdzić stan systemu po każdej wiadomości lub akcji. Może to wymagać dodatkowych instrumentacji.  
  
## <a name="deriving-subsystem-tests-from-models"></a>Wyprowadzanie podsystemu testów z modeli  
 W projektowania wysokiego poziomu w dużym systemie można zidentyfikować, składniki i podsystemy. Reprezentują one części, które mogą być oddzielnie projektowane, znajdują się na różnych komputerach lub to moduły wielokrotnego użytku, które mogą być odtwarzane na wiele sposobów. Aby uzyskać więcej informacji, zobacz [diagramy składników UML: wskazówki dotyczące](../modeling/uml-component-diagrams-guidelines.md).  
  
 Można zastosować do poszczególnych głównych składników te same zasady używania dla całego systemu. W dużym projekcie każdy składnik może mieć własny model wymagania. W projektach mniejszych aby pokazać główne składniki i ich interakcje można utworzyć architektury model lub projektowania wysokiego poziomu. Aby uzyskać więcej informacji, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).  
  
 W obu przypadkach można ustanowić relacji między elementami modelu i testy podsystemu w taki sam sposób jak w przypadku między modelem wymagań i testów systemowych.  
  
### <a name="isolate-components-with-provided-and-required-interfaces"></a>Izolowania składników za pomocą interfejsy dostarczany i wymagany  
 Jest to przydatne, aby zidentyfikować wszystkie zależności, które składnik ma inne części systemu lub usług zewnętrznych, a także do reprezentowania je jako wymagane interfejsy. To ćwiczenie zwykle prowadzi do niektórych przeprojektowywania powodują, że składnik znacznie bardziej odłączony i łatwo mogą być oddzielone od pozostałej części projektu.  
  
 To oddzielenie zaletą jest to, że składnika mogą być wykonywane dla testowanego przez zastąpienie obiektami makiety usług, które są zwykle używane. Są to składniki, które są skonfigurowane na potrzeby testowania. Makiety składnik udostępnia interfejs, który wymaga składnika, odpowiada na zapytania z symulowanymi danymi. Składniki makiety częścią kontroler ukończenia testowej, które można podłączyć wszystkie interfejsy składnika.  
  
 Zaletą makiety testowania jest opracowanie składnika podczas inne składniki, których usługi, które będą przez niego używane są nadal w fazie projektowania.  
  
## <a name="maintain-the-relationships-between-tests-and-model"></a>Obsługa relacji między testy i Model  
 W typowym projekcie, który wykonuje iterację co kilka tygodni Przejrzyj wymagania dotyczące jest utrzymywana na początku każdej iteracji. Spotkanie w tym artykule omówiono funkcje, które mają zostać dostarczone w następnej iteracji. Modelu wymagań może służyć do pomoc w omówieniu pojęcia, scenariuszy i sekwencji akcji, które będą rozwijane. Zainteresowane strony biznesowe ustawiane priorytety, deweloperzy mogą stosować oszacowania i testerów upewnij się, że oczekiwane zachowanie każdej funkcji jest przechwytywana poprawnie.  
  
 Pisanie testów jest najbardziej skutecznym sposobem definiowania wymagane i jest również efektywny sposób upewnić się, że osoby zapoznanie co jest wymagane. Jednakże natomiast pisania testów trwa zbyt długo, podczas warsztatów specyfikacji, tworzenie modeli może odbywać się znacznie szybciej.  
  
 Z testowania punktu widzenia modelu wymagań może być traktowany jako skrót do testów. W związku z tym jest ważne, aby zachować relacji między testy i modelu w całym projekcie.  
  
##  <a name="Attaching"></a> Dołączanie przypadki testowe do elementów modelu  
 Jeśli projekt używa [!INCLUDE[TCMlong](../includes/tcmlong-md.md)], testy można połączyć elementy w modelu. Umożliwia szybkie znajdowanie testów wpływ zmiany w wymaganiach i pomaga śledzić, do którego zostały zrealizowane wymagania w zakresie.  
  
 Testy można połączyć wszelkiego rodzaju elementu. Oto kilka przykładów:  
  
-   Łączenie przypadków użycia, aby testy, które jego wykonywania.  
  
-   Zapis klauzule postcondition przypadków użycia lub celem na komentarze, które są połączone z przypadkiem użycia, a następnie połącz testy każdy komentarz.  
  
-   Napisz zasad niezmiennej komentarze na diagramach klas lub diagramów aktywności, a następnie połączyć testy.  
  
-   Połącz testy w diagramie aktywności lub poszczególne działania.  
  
-   Zestaw testów połączyć składnik lub podsystem, który sprawdza.  
  
#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Aby połączyć testy elementu modelu lub relacji  
  
1.  W [!INCLUDE[TCMlong](../includes/tcmlong-md.md)], Utwórz wymagania i podstawą zestaw testów. Aby dowiedzieć się, jak to zrobić, zobacz [testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).  
  
     Wymagania, którą tworzysz jest element roboczy w [!INCLUDE[vstsTfsShort](../includes/vststfsshort-md.md)]. Może być elementem pracy scenariusza użycia, wymagania lub przypadek użycia, w zależności od szablonu procesu, który projekt korzysta z [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Aby uzyskać więcej informacji, zobacz [śledzenie pracy za pomocą programu Visual Studio Team Services lub serwera Team Foundation Server](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Elementem roboczym należy połączyć jeden lub więcej elementów w modelu.  
  
     Na diagramie modelowania, kliknij prawym przyciskiem myszy element, komentarz lub relacji, a następnie kliknij przycisk **łącze do elementu roboczego**. Aby uzyskać więcej informacji, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).  
  
3.  Dodaj do zestawu testów, przypadki testowe, które Sprawdź wymagań wyrażony w elemencie modelu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)   
 [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)   
 [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)   
 [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)



