---
title: Model aplikacji&#39;architektura s | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9e5de52fbe15049f4acb3dacf236bfe9f4ecc92
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823263"
---
# <a name="model-your-app39s-architecture"></a>Model aplikacji&#39;architektury s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby mieć pewność, że z oprogramowania systemu lub aplikacji spełnia użytkowników potrzebuje, możesz tworzyć modele w programie Visual Studio, jako część opisie ogólną strukturę i zachowanie systemu oprogramowania lub aplikacji. Przy użyciu modeli, może również opisywać wzorców, które są używane w całym projekcie. Modele te ułatwiają zrozumienie istniejącej architektury, omówiono zmiany i wyraźnie komunikacji zamiaru.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Cel modelu jest zmniejszenie niejasności, występujących w opisach języka naturalnego, ułatwienie Ty i Twoi współpracownicy wizualizacji projektu i w celu omówienia alternatywnych projektów. Model powinien być używany razem z innych dokumentów lub dyskusji. Przez siebie model nie reprezentuje pełną specyfikację architektury.  
  
> [!NOTE]
> W tym temacie "system" oznacza, że oprogramowanie, które tworzysz. Może być duży zbiór wielu składników oprogramowania i sprzętu, lub pojedynczej aplikacji lub jej część aplikacji.  
  
 Architektura systemu można podzielić na dwóch obszarach:  
  
- [Projektowania wysokiego poziomu](#Structure). Opisuje główne składniki i jak współdziałają ze sobą w celu spełnienia poszczególnych wymagań. Jeśli system jest duża, każdy składnik może mieć własną projektowania wysokiego poziomu, który pokazuje, jak jest zbudowany z mniejszych składników.  
  
- [Wzorce projektowe](#Patterns) i Konwencji używanych w całym projekty składników. Wzorzec opisuje sposób postępowania w osiąganiu celu programowania. Za pomocą tych samych wzorców w całym projekcie, Twój zespół może zmniejszyć kosztów wprowadzania zmian i tworzenie nowego oprogramowania.  
  
## <a name="Structure"></a> Projektowania wysokiego poziomu  
 Projektowania wysokiego poziomu w tym artykule opisano główne składniki systemu i jak współdziałają ze sobą w celu osiągnięcia celów projektowania. Działania na poniższej liście są zaangażowane w opracowywaniu projektowania wysokiego poziomu, ale niekoniecznie w określonej kolejności.  
  
 Jeśli aktualizujesz istniejący kod może zacząć poprzez opisanie główne składniki. Upewnij się, zrozumieć wszelkie zmiany wymagań użytkowników i następnie dodać lub zmodyfikować interakcje między składnikami. Jeśli tworzysz nowy system begin przez opis najważniejszych funkcji potrzeb użytkowników. Następnie zapoznaj się z sekwencji interakcji dla przypadków użycia głównego i następnie konsolidowanie sekwencji do projektu składnika.  
  
 W każdym przypadku jest przydatne do tworzenia różnych działań równoległych i tworzenie kodu i testów na wczesnym etapie. Należy unikać próby wykonaj jedną z tych aspektów, przed rozpoczęciem korzystania z innej. Zazwyczaj wymagania i zrozumieć, najlepszym sposobem na projektowanie systemu zmieni się podczas pisania i testowania kodu. W związku z tym należy rozpocząć poprzez zrozumienie i kodowania najważniejszych funkcji, wymagań i projektu. Wypełnij szczegóły w późniejszej iteracji projektu.  
  
- [Opis wymagań](#Requirements). Punkt początkowy dowolnego projektu jest jasne zrozumienie potrzeb użytkowników.  
  
- [Wzorce architektury](#BigDecisions). Opcje wprowadzone o podstawowych technologii i architektury elementów systemu.  
  
- [Składniki oraz ich interfejsów](#Components). Rysowanie diagramów składników, aby pokazać główne części systemu i pokazanie interfejsów, które współdziałają ze sobą. Interfejsy, które poszczególnych składników zawierają wszystkie komunikaty, które można zidentyfikowane na diagramach sekwencji.  
  
- [Interakcje pomiędzy składnikami](#Interactions). Dla każdego przypadku użycia, zdarzenia lub komunikatu przychodzącego można narysować diagram sekwencji pokazujący sposób interakcji główne składniki systemu do osiągnięcia wymaganą reakcję.  
  
- [Model danych składników i interfejsy](#Data). Możesz narysować diagramy klas do opisania informacje, które jest przekazywane między składnikami, a następnie przechowywane wewnątrz składników.  
  
## <a name="Requirements"></a> Omówienie wymagań  
 Ogólny projekt kompletnej aplikacji jest najbardziej efektywne opracowany wraz z modelem wymagania lub innych opis potrzeb użytkowników. Aby uzyskać więcej informacji na temat modeli wymagania, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
 Jeśli system, który tworzysz składnik w systemie większe, część lub całość wymagań może zostać zawarte w interfejsów programistycznych.  
  
 Model wymagań zapewnia tych podstawowych rodzajów informacji:  
  
- Interfejs dostarczany. Interfejs dostarczany zawiera listę usług lub operacji, które system lub składnika, musisz podać swoim użytkownikom, czy są one ludzi użytkowników ani innych składników oprogramowania.  
  
- Wymagane interfejsy. Interfejs wymagany zawiera listę usług lub operacji, które można użyć systemu lub składnika. W niektórych przypadkach można zaprojektować wszystkie te usługi w ramach własnego systemu. W innych przypadkach zwłaszcza wtedy, gdy projektujesz składnik, który może być łączone z innymi składnikami w wielu konfiguracjach wymaganego interfejsu zostaną ustawione przez zewnętrzne zagadnienia.  
  
- Jakość wymagań dotyczących usług. Wydajności, bezpieczeństwa, niezawodności, a inne cele i ograniczenia, które muszą spełniać system.  
  
  Modelu wymagań są zapisywane z punktu widzenia użytkowników w systemie, czy są one osób lub innymi składnikami oprogramowania. Nie wiedzą niczego wewnętrzne działanie systemu. Z drugiej strony w modelu architektury jest do opisywania wewnętrzne działanie i pokazują, jak spełniają użytkowników potrzebuje.  
  
  Oddzieleniu wymagań i modeli architektury jest przydatne, ponieważ ułatwia celu omówienia ich wymagań z użytkownikami. Pomaga również Refaktoryzuj projektu i należy wziąć pod uwagę alternatywnych architektury podczas przechowywania wymagania bez zmian.  
  
  W dwie alternatywne metody, można oddzielić wymagania i modele architektury:  
  
- Zachować je w tym samym rozwiązaniu, ale różnych projektach. Będą one występować jako osobne modele w Eksploratorze modelu UML. Różni członkowie zespołu mogą działać równolegle w modelach. Ograniczone rodzaje śledzenia mogą być tworzone między modelami.  
  
- Umieść je w tym samym modelu UML, ale w różnych pakietach. Ułatwia to Śledzenie zależności między modelami, ale uniemożliwia więcej niż jedną osobę w czasie pracy na podstawie modelu. Ponadto bardzo dużych modeli będzie trwać dłużej obciążenia do programu Visual Studio. To podejście w związku z tym jest mniej odpowiednia w przypadku dużych projektów.  
  
  Ilość szczegółów, które należy umieścić w wymagania lub architektury model zależy od tego, skali projektu oraz wielkość i stopień rozproszenia zespołu. Małego zespołu nad projektem krótki mogą zostać przekazane żadne dodatkowe niż powstawać diagramu klas koncepcji biznesowych i niektórych wzorców projektowych; duży projekt rozproszone na więcej niż jeden region należałoby znacznie bardziej szczegółowo.  
  
## <a name="BigDecisions"></a> Wzorce architektury  
 Na wczesnym etapie projektowania należy wybrać technologie główne i elementów, od których zależy od projektu. Obszary, w których należy te opcje są następujące:  
  
- Podstawowa Wybór technologii, takich jak wybrać między bazą danych i systemu plików i wybór między aplikację sieciową i klienta sieci Web i tak dalej.  
  
- Opcje struktury, takie jak wybór między Windows Workflow Foundation lub ADO.NET Entity Framework.  
  
- Wybór metody integracji na przykład między usługi enterprise service bus lub kanał point-to-point.  
  
  Te opcje są często określane przez jakości wymagań, takie jak skalowalność i elastyczność i wprowadzenia szczegółowe wymagania są znane. W dużym systemie konfiguracji sprzętu i oprogramowania są silnie powiązane ze sobą.  
  
  Wybrane opcje, które wpływają na sposób używania i interpretować architektury model. Na przykład w systemie, który korzysta z bazy danych, skojarzenia na diagramie klasy może reprezentować relacji lub klucze obce w bazie danych, natomiast w systemie, który jest oparty na plikach XML, skojarzenia może wskazywać odsyłaczy, które używają języka XPath. W rozproszonym systemie wiadomości w diagramie sekwencji może reprezentować komunikatów o komunikacji sieciowej; w przypadku aplikacji niezależna reprezentują wywołania funkcji.  
  
## <a name="Components"></a> Składniki oraz ich interfejsów  
 Główne zalecenia przedstawione w tej sekcji są następujące:  
  
- Tworzenie diagramów składników, aby pokazać główne części systemu.  
  
- Rysuj zależności między składnikami lub ich interfejsy, aby wyświetlić strukturę systemu.  
  
- Umożliwia interfejsy na składnikach usługi pokazują, że każdy składnik udostępnia lub wymaga.  
  
- W dużych projektów możesz narysować diagramy oddzielnych do rozkładania każdy składnik na mniejsze części.  
  
  Te punkty są opracowane w dalszej części tej sekcji.  
  
### <a name="components"></a>Składniki  
 Centralna widoków architektura modelu są diagramów składników, które pokazują głównych składników systemu i jak są one zależne od siebie nawzajem. Aby uzyskać więcej informacji na temat diagramów składników zobacz [diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md).  
  
 ![Diagram składników UML przedstawiający części](../modeling/media/uml-barecomponent.png "UML_BareComponent")  
  
 Diagram składników typowym dla dużych systemu mogą być następujące składniki, takie jak te:  
  
- Prezentacji. Składnik, który zapewnia dostęp do użytkownika, zwykle działających w przeglądarce sieci Web.  
  
- Składniki usługi sieci Web. Zapewnia połączenie między klientami a serwerami.  
  
- Użyj przypadków kontrolerów. Prowadzi użytkownika przez kroki poszczególnych scenariuszy.  
  
- Podstawowa biznesowych. Zawiera klasy, które są oparte na klasach w modelu wymagań, implementuje kluczowe operacje i nakłada ograniczeń biznesowych.  
  
- Baza danych. Przechowuje obiektów biznesowych.  
  
- Rejestrowanie i składniki obsługi błędów.  
  
### <a name="dependencies-between-components"></a>Zależności między składnikami  
 Oprócz samych elementów można wyświetlić zależności między nimi. Kształt strzałki zależności między składnikami dwóch pokazuje, że zmiany w projekcie jednego mogą mieć wpływ na projekt z drugiej strony. Zwykle dzieje się tak, ponieważ jeden składnik używa usług lub funkcji, które są dostarczane przez inny składnik, bezpośrednio lub pośrednio.  
  
 Dobrze architektura ma wyczyść rozmieszczenie zależności, w których te warunki są spełnione:  
  
- Nie istnieją żadne pętle na mapie kodu.  
  
- Składniki mogą być ułożone w warstwach, w których każdy zależności przechodzi z składnika w jednej warstwy do składnika w ciągu następnych. Wszystkie zależności między dwóch warstw go w tym samym kierunku.  
  
  Można wyświetlić zależności między składnikami lub można wyświetlić zależności między wymagane i podano interfejsów, które są dołączone do składników. Korzystając z interfejsów, można określić, jakie operacje są używane w poszczególnych zależności. Zazwyczaj przedstawiono zależności między składnikami, gdy diagramy są rysowane najpierw, a następnie zastępuje zależności między interfejsami, po dodaniu więcej informacji. Obie wersje są poprawne opisy oprogramowania, ale wersja z interfejsami zapewnia więcej szczegółów niż starszej wersji.  
  
  Zarządzanie zależnościami jest najważniejsze dla środowiska produkcyjnego, łatwego w utrzymaniu oprogramowania. Diagramy składników powinny odzwierciedlać wszystkich zależności w kodzie. Jeśli kod już istnieje, upewnij się, że wszystkie zależności są wyświetlane na diagramach. Jeśli kod jest opracowywany, upewnij się, że nie zawiera zależności, które nie są planowane na diagramie składników. Państwu pomóc odkryć zależności w kodzie, można wygenerować diagramów warstwowych. Ułatwiające upewnij się, czy spełniono swoje ograniczenia planowane zależności, możesz walidować kod diagramów warstwy. Aby uzyskać więcej informacji, zobacz [diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md).  
  
### <a name="interfaces"></a>Interfejsy  
 Umieszczając interfejsy na składniki, można oddzielić i nazwy główne grupy operacji, które są dostarczane przez poszczególne składniki. Na przykład składników opartych na sieci web systemu sprzedaży może mieć interfejs, za pomocą którego klienci kupić towarów, interfejs, za pomocą którego zaktualizować ich katalogów dostawców, a trzeciego interfejsu, przez który system jest zarządzany.  
  
 Składnik może mieć dowolną liczbę interfejsów dostarczany i wymagany. Interfejs dostarczany usługi show, dostępne dla innych składników używać składnika. Wymagane interfejsy Pokaż usług używanych przez składnik w innych składników.  
  
 Jeśli zdefiniujesz oba dostarczone i wymagane interfejsy, dzięki temu można oddzielić składnika nie pozostawia żadnych śladów od pozostałej części projektu, tak, aby można było używać tych metod:  
  
- Umieść ten składnik w kontroler testu, w którym otaczającego składniki są symulowane przez kontroler testów.  
  
- Tworzenie składnika niezależnie od innych składników.  
  
- Ponowne użycie składnika w innych kontekstach przez sprzężenia interfejsy do różnych składników.  
  
  Jeśli chcesz zdefiniować listę operacji w interfejsie, można utworzyć inny widok interfejsu na diagramie klas UML. Aby to zrobić, zlokalizuj interfejsu w Eksploratorze modelu UML, a następnie przeciągnij go do diagramu klas. Następnie można dodać operacje do interfejsu.  
  
  Operacja w interfejsie UML może reprezentować dowolny sposób, w którym może być wywoływany zachowanie składnika. Może on reprezentuje żądanie usługi sieci Web, sygnał lub interakcji z innego typu lub wywołania funkcji zwykłego programu.  
  
  Aby ustalić, jakie operacje można dodać, należy utworzyć diagramy sekwencji, aby pokazać, jak składniki współdziałają ze sobą. Zobacz [interakcje pomiędzy składnikami](#Interactions). Każda z tych diagramów sekwencji pokazuje interakcje występujące w przypadku użycia innego. W ten sposób można stopniowo dodajesz do listy operacji w interfejsie każdego składnika, gdy eksplorujesz przypadków użycia.  
  
### <a name="decomposing-a-component-into-parts"></a>Podzielenie składnika na części  
 Można użyć procedury opisanej w poprzedniej sekcji, aby każdy składnik.  
  
 W ramach każdego składnika można wyświetlić jego składniki podrzędne jako części. Część jest skutecznie atrybut jej składnika nadrzędnego, który jest rodzajem klasy. Każda część ma swój własny typ, który może być składnika. Możesz umieścić ten składnik na diagramie i wyświetl jego części. Aby uzyskać więcej informacji, zobacz [diagramy składników UML: Wytyczne dotyczące](../modeling/uml-component-diagrams-guidelines.md).  
  
 Jest to przydatne do zastosowania tej techniki do całego systemu. Narysuj jako samodzielny składnik i wyświetl jego głównych składnikach, jako części. Dzięki temu można jednoznacznie interfejsów systemu ze światem zewnętrznych.  
  
 Gdy projekt dla składnika wykorzystuje inny składnik, często należy dokonać wyboru o tym, czy w ramach lub jako oddzielny składnik, które są dostępne za pośrednictwem interfejsu wymaga go reprezentuje.  
  
 Użyj części w następujących sytuacjach:  
  
- Projekt składnika nadrzędnego, należy zawsze używać typu składnika części. Dlatego projekt części jest integralną częścią projektu składnika nadrzędnego.  
  
- Składnik nadrzędny nie ma żadnych konkretnych istnienie swój własny. Na przykład można mieć koncepcyjny składnik o nazwie Warstwa prezentacji, który reprezentuje kolekcję rzeczywistych składników, które obsługi widoków i interakcje użytkownika.  
  
  Użyj oddzielnych składników dostępne za pośrednictwem interfejsów wymagane w następujących sytuacjach:  
  
- Wymaganie składnika mogą zostać dołączone przez swoje interfejsy do różnych składników dostarczanie w czasie wykonywania.  
  
- Projekt jest taka, że będzie można łatwo zastąpić inną jednego dostawcę.  
  
  Korzystanie z interfejsów wymagane zwykle lepiej jest użycie części. Mimo, że projekt może trwać dłużej, wynikowy system jest bardziej elastyczna. Jest również łatwiejsze testowanie składników oddzielnie. Dzięki temu mniej sprzężenia w swoich planach rozwoju.  
  
## <a name="Interactions"></a> Interakcje pomiędzy składnikami  
 Główne zalecenia przedstawione w tej sekcji są następujące:  
  
- Zidentyfikować przypadki użycia systemu.  
  
- Dla każdego przypadku użycia narysuj jeden lub więcej diagramów, aby pokazać, jak osiągnąć składnikami systemu wymagany wynik współpracując ze sobą i z użytkownikami. Zazwyczaj są to diagramów sekwencji i diagramy aktywności.  
  
- Użyj interfejsów, aby określić komunikaty odbierane przez poszczególne składniki.  
  
- Opisz skutków operacji w interfejsach.  
  
- Powtórz procedurę dla każdego składnika, przedstawiający sposób interakcji części.  
  
  Na przykład w sieci web systemu sprzedaży, modelu wymagań zdefiniować zakupu przez klienta jako przypadek użycia. Można utworzyć diagramu sekwencji do wyświetlenia interakcji, że klient ma ze składnikami w warstwie prezentacji oraz interakcji, do których mają z magazynu i składników ewidencjonowania aktywności.  
  
### <a name="identifying-the-initiating-events"></a>Identyfikowanie inicjujący zdarzenia  
 Pracy wykonanej przez większość systemów oprogramowania może wygodnie podzielone przez odpowiedzi, które zapewnia inne dane wejściowe lub zdarzeń. Zainicjować zdarzenie może być jednym z następujących zdarzeń:  
  
- Pierwszą akcją w przypadku użycia. Modelu wymagań może pojawiać się jako krok w przypadku użycia lub akcji w diagramie aktywności. Aby uzyskać więcej informacji [diagramy przypadków użycia UML: Wytyczne dotyczące](../modeling/uml-use-case-diagrams-guidelines.md) i [diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md).  
  
- Komunikat o interfejs programistyczny. Jeśli system, który tworzysz składnik w systemie większe, powinny być opisane jako operacji w jeden z interfejsów składnika. Zobacz [składników oraz ich interfejsów](#Components).  
  
- Określony warunek, który jest monitorowany przez system lub regularne zdarzeń, takich jak porze dnia.  
  
### <a name="describe-the-computations"></a>Opisz obliczeń  
 Narysuj diagramy sekwencji, aby pokazać, jak składniki odpowiadać na zdarzenie początkowe.  
  
 Rysuj linię życia dla każdego wystąpienia składnika, który bierze udział w typowej sekwencji. W niektórych przypadkach może być więcej niż jedno wystąpienie każdego typu. Jeśli zostały opisane całego systemu jako samodzielny składnik, powinna to być jedna linia życia dla każdej części, które zawiera.  
  
 Aby uzyskać więcej informacji, zobacz [UML Sequence Diagrams: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Diagramy aktywności są przydatne także w niektórych przypadkach. Na przykład jeśli składniki ciągłego strumienia danych, można go opisać jako przepływ obiektu. Jeśli składnik ma złożonych algorytmów, można go opisać jako przepływ sterowania. Upewnij się, wprowadź jasne, który składnik wykonuje każde działanie, na przykład za pomocą komentarzy. Aby uzyskać więcej informacji, zobacz [diagramy aktywności UML: Wytyczne dotyczące](../modeling/uml-activity-diagrams-guidelines.md).  
  
### <a name="specify-the-operations"></a>Określ czynności  
 Choć te diagramy przedstawiają operacje wykonywane przez każdy składnik to reprezentowana jako komunikaty na diagramie sekwencji lub działania w diagramie aktywności.  
  
 Zbieraj te operacje razem dla każdego składnika. Twórz interfejsy dostarczane w składniku i dodać operacje do interfejsów. Zwykle oddzielny interfejs jest używany dla każdego typu klienta. Operacje najłatwiej są dodawane do interfejsów w **Eksploratora modelu UML**. W ten sam sposób zbierania operacji, które korzysta z każdego składnika od innych składników i umieścić je w wymagane interfejsy dołączone do składnika.  
  
 Jest to przydatne w celu dodawania komentarzy do diagramów aktywności lub sekwencji, należy pamiętać, zdobyła po zakończeniu każdej operacji. Można także napisać efekt każdej operacji w jego **lokalnego Postcondition** właściwości.  
  
### <a name="Data"></a> Model danych składników i interfejsów  
 Określ parametry i zwracane wartości każdej operacji w interfejsach składnika. Gdzie operacje reprezentują wywołania, takie jak żądania usługi sieci Web, parametry są tych rodzajów informacji, które są wysyłane jako część żądania. W przypadku, gdy kilka wartości są zwracane z operacją, można użyć parametrów za pomocą **kierunek** właściwością **się**.  
  
 Każdy parametr i wartość zwracana ma typ. Można zdefiniować tymi typami za pomocą diagramów klas UML. Nie masz do reprezentowania szczegółów implementacji w tych diagramów. Na przykład jeśli są opisującego dane, które są przesyłane w formacie XML, można użyć asocjacji do reprezentacji dowolnego rodzaju porównania między węzłami, XML i używanie klas do reprezentowania węzłów.  
  
 Komentarze służą do opisywania ograniczeń biznesowych skojarzenia i atrybutów. Na przykład jeśli wszystkie elementy w kolejności klienta muszą pochodzić z tego samego dostawcy, możesz opisać to przez odwołanie do skojarzenia między elementami kolejność i elementy w katalogu produktów oraz między elementami katalogu i jego dostawcy.  
  
## <a name="Patterns"></a> Wzorce projektowe  
 Wzorzec projektowy jest konspektu sposobu projektowania danego aspekt tego oprogramowania, zwłaszcza taki, który występuje w różnych częściach systemu. Przyjmując jednolite podejście w projekcie, można zmniejszyć koszt projektu, zapewnienia spójności interfejsu użytkownika i zmniejszyć koszt zrozumienie i zmieniania kodu.  
  
 Niektóre wzorce projektowe ogólnych, takich jak obserwatora są dobrze znane i powszechnie stosowane. Ponadto są wzorce, które mają zastosowanie tylko do projektu. Na przykład w sieci Web system sprzedaży, nastąpi kilka operacji w kodzie gdzie zmian zamówienia klienta. W celu zapewnienia, że był wyświetlany stan zamówienia na każdym etapie, wszystkie czynności należy wykonać konkretnego protokołu aktualizacji bazy danych.  
  
 Część pracy architektury oprogramowania ma na celu określenie, jakie wzorce powinny być przyjęte przez projekt. Jest to zazwyczaj bieżące zadanie, ponieważ nowe wzorce i ulepszenia istniejących wzorców zostaną odnalezione w miarę postępów projektu. Jest to przydatne do organizowania plan rozwoju, tak aby wykonywania wszystkich Twoich wzorców projektowania główne na wczesnym etapie.  
  
 Większość wzorców projektowych może częściowo zawarte w kodzie framework. Część wzorca można zmniejszyć żądania dla deweloperów do użycia z określonymi klasami lub składniki, takie jak warstwa dostępu do bazy danych, które zapewnia, że baza danych odbywa się poprawnie.  
  
 Wzorzec projektowy jest opisane w dokumencie i zwykle obejmuje następujące elementy:  
  
- Nazwa.  
  
- Opis kontekst, w której ma zastosowanie. Jakie kryteria należy upewnić się deweloperem, należy rozważyć stosowanie tego wzorca?  
  
- Krótki opis problemów, które ona rozwiązuje.  
  
- Model głównych składników oraz ich wzajemne relacje. Może to być klasy lub składniki i interfejsy, za pomocą skojarzeń i zależności między nimi. Elementy zazwyczaj można podzielić na dwie kategorie:  
  
  - Elementy, które muszą być replikowane przez dewelopera w każdej części kodu, w których wzorzec jest używany. Typy szablonów służy do opisywania tych. Aby uzyskać więcej informacji, zobacz [diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md).  

  - Elementy opisujące klasy framework, które należy używać projektanta.  
  
- Model interakcji między częściami, za pomocą diagramów sekwencji lub działania.  
  
- Konwencje nazewnictwa.  
  
- Opis sposobu wzorzec rozwiązuje problem.  
  
- Opis zmian, które deweloperzy mogą mieć możliwość przyjęcia.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Wizualizacja kodu](../modeling/visualize-code.md)   
 [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)   
 [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)   
 [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
