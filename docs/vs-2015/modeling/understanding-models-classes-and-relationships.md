---
title: Objaśnienie modeli, klas i relacji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d4381edb42e2aef53c00aea619eea34ee20060d5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424329"
---
# <a name="understanding-models-classes-and-relationships"></a>Opis modeli, klas i relacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Języka specyficznego dla domeny (DSL) jest definiowany przez jego pliku definicji DSL, wraz z wszelki kod niestandardowy program, który może zapisać. Większość kodu programu w rozwiązaniu DSL jest generowany na podstawie tego pliku.  
  
 W tym temacie omówiono funkcje centralnej definicji DSL.  
  
## <a name="the-dsl-definition"></a>W definicji DSL  
 Po otwarciu `Dsl\DslDefinition.dsl`, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna podobny do poniższej ilustracji.  
  
 ![Projektant DSL](../modeling/media/dsl-designer.png "dsl_designer")  
  
 Najważniejsze informacje w definicji DSL jest wyświetlany w diagramem definicji DSL. Dodatkowe informacje, które wchodzi w skład DslDefinition.dsl, jest wyświetlany w Eksplorator DSL, który zazwyczaj znajduje się na stronie diagramu. Możesz pracować z diagramem najczęstsze zadania i Eksplorator DSL dla bardziej zaawansowanych dostosowań.  
  
 Na diagramie w definicji DSL przedstawiono klasy domeny, które definiują elementy modelu i relacji, które definiują łącza między elementami modelu. Pokazuje także kształtów i łączników, które są używane do wyświetlania elementów modelu do użytkownika.  
  
 ![Projektant DSL za pomocą toru](../modeling/media/dsl-desinger.png "dsl_desinger")  
  
 Po wybraniu elementu w definicji DSL, na diagramie lub w Eksploratorze DSL informacje o nim są wyświetlane w oknie dialogowym właściwości. Dodatkowe informacje mogą być wyświetlane w oknie Szczegóły języka DSL.  
  
### <a name="models-are-instances-of-dsls"></a>Modele są wystąpieniami językami DSL  
 A *modelu* jest wystąpieniem DSL utworzone przez użytkownika. Model zawiera elementy modelu, które są wystąpieniami klasy domeny, które należy zdefiniować i łączy między elementami, które są wystąpieniami klasy relacji domeny, które definiujesz. Model może również mieć kształtów i łączników, które zawierają elementy modelu i łącza na diagramie. W definicji DSL zawiera klasy kształtów, klas łącznika i klasy dla diagramu.  
  
 Definicję DSL jest także znana jako *modelu domeny*. Model definicji DSL lub domena jest projektowania reprezentacja języka specyficznego dla domeny, model jest wystąpienia środowiska wykonawczego języka specyficznego dla domeny.  
  
## <a name="domain-classes-define-model-elements"></a>Klasy domeny definiują elementy modelu  
 Klasy domeny są używane do tworzenia różnych elementów w domenie i relacje domeny są łącza między elementami. Są one projektowania reprezentacja elementów i łącza, które będą tworzone przez użytkowników języka specyficznego dla projektu podczas tworzenia swoich modeli.  
  
 Na ilustracji przedstawiono model, który został utworzony przez użytkownika Biblioteka utworów muzycznych DSL. Utworów muzycznych albumy są reprezentowane przez pola zawierające listy utworów. Artystów są reprezentowane przez zaokrąglonych pól i są podłączone do albumów, do których one opracowali.  
  
 ![Wystąpienie modelu DSL wygenerowanego](../modeling/media/music-instance.png "Music_Instance")  
  
 W definicji DSL oddziela dwa aspekty. Wygląd elementów modelu w diagramie model jest zdefiniowana za pomocą klasy kształtów i łączników klasy. Informacje w modelu jest zdefiniowana za pomocą klasy domeny i relacje domeny.  
  
 Poniższa ilustracja przedstawia klasy domeny i relacje w definicji DSL Biblioteka utworów muzycznych.  
  
 ![Relacji osadzania i odwołania](../modeling/media/music-classes.png "Music_Classes")  
  
 Na ilustracji przedstawiono cztery klasy domeny: Muzyka, fotograficzne, wykonawcy i utworu. Klasy domeny definiują właściwości domeny, takie jak nazwy, tytułu i tak dalej. W modelu wystąpień wartości niektóre z tych właściwości są wyświetlane na diagramie.  
  
 Między klasami są relacje domeny: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs i ArtistAppearedOnAlbums. Relacje zostały Liczebność punktów, takich jak 1..1, 0.. *. Na przykład każdy utwór musi być powiązany do dokładnie jednego albumu relacji AlbumHasSongs. Każdego albumu może mieć dowolną liczbę utworów.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Ponowne rozmieszczanie diagramem definicji DSL  
 Zauważ, że klasy domeny mogą być wyświetlane kilka razy na diagramem definicji DSL, podobnie jak albumu na tym rysunku. Zawsze istnieje jeden widok główny, i może być niektóre *odwołania* widoków.  
  
 Aby zmienić kolejność diagramem definicji DSL, możesz wykonywać następujące czynności:  
  
- Zamienić głównego i widoki się odwoływać za pomocą **przenieść drzewa w tym miejscu** i **Podziel drzewo** poleceń. Kliknij prawym przyciskiem myszy klasę jednej domeny, aby wyświetlić te polecenia.  
  
- Kolejność kształt klasy i klas domeny, naciskając klawisze Ctrl + Strzałka w górę i Ctrl + Strzałka w dół.  
  
- Zwinąć lub rozwinąć klas przy użyciu ikony w prawym górnym rogu każdego z kształtów.  
  
- Zwiń części drzewa, klikając znak minus (-) w dolnej części klasy domeny.  
  
## <a name="inheritance"></a>Dziedziczenie  
 Klasy domeny mogą być definiowane za pomocą dziedziczenia. Aby utworzyć pochodnym dziedziczenia, kliknij narzędzie dziedziczenia, kliknij w klasie pochodnej, a następnie kliknij klasy bazowej. Element modelu ma wszystkie właściwości, które są zdefiniowane na własnej klasy domeny wraz z wszystkich właściwości, które są dziedziczone z klasy podstawowej. Dziedziczy jej ról w relacji.  
  
 Można także dziedziczenia między relacje, kształty i łączniki. Dziedziczenie musi przechowywać w ramach tej samej grupy. Kształt nie może dziedziczyć z klasy domeny.  
  
## <a name="domain-relationships"></a>Relacje domeny  
 Elementy modelu mogą być połączone przez zastosowanie relacji. Łącza są zawsze binary; łączą się dokładnie z dwóch elementów. Jednak każdy element może mieć wiele łączy do innych obiektów, a nawet może być więcej niż jednego połączenia między tej samej pary elementów.  
  
 Tak, jak można zdefiniować różne rodzaje elementów, można zdefiniować różne rodzaje łączy. Klasa łącza jest nazywana *relacji domeny*. Relacja domeny określa, które klasy elementu można połączyć z jego wystąpienia. Każdy koniec relacji jest nazywany *roli*, a relacja domeny definiuje nazwy dwóch ról, a także samą relację.  
  
 Istnieją dwa rodzaje relacji domeny: osadzanie relacje i relacje odniesienia. Na diagramem definicji DSL relacji osadzania mieć linia ciągła w każdej roli, a relacje odniesienia mają Kreskowanie wierszy.  
  
### <a name="embedding-relationships"></a>Osadzanie relacji  
 Każdy element w modelu, z wyjątkiem jego główny jest celem jeden link osadzania. W związku z tym cały model stanowi jedno drzewo osadzania łącza. Relacja osadzania reprezentuje zawierania lub własności. Dwa elementy modelu, które są powiązane w ten sposób są nazywane także nadrzędnymi i podrzędnymi. Element podrzędny jest nazywany można osadzić w obiekcie nadrzędnym.  
  
 Osadzanie łącza nie są zwykle wyświetlane jawnie jako łączniki, na diagramie. Zazwyczaj są one jednak reprezentowane przez zawierania. Korzeń modelu reprezentowanego przez diagram i osadzone w nim elementy są wyświetlane jako kształtów na diagramie.  
  
 W tym przykładzie Klasa główna utworów muzycznych ma relację osadzania MusicHasAlbums do albumów, mającej AlbumHasSongs osadzania do utworu. Utwory są wyświetlane jako elementy na liście wewnątrz każdego albumu. Muzyka ma również MusicHasArtists osadzania do klasy wykonawcy, w których wystąpienia są również wyświetlane jako kształtów na diagramie.  
  
 Domyślnie osadzone elementy są automatycznie usuwane po usunięciu nadrzędnych.  
  
 Po zapisaniu modelu do pliku w postaci XML, osadzone elementy są zagnieżdżone wewnątrz nadrzędnych, chyba że dostosowano serializacji.  
  
> [!NOTE]
> Osadzanie nie jest taka sama jak dziedziczenie. Elementy podrzędne w relacji osadzania dziedziczy właściwości elementu nadrzędnego. Osadzanie jest typu łącza między elementami modelu. Dziedziczenie jest relacja między klasami i nie tworzyć łącza między elementami modelu.  
  
### <a name="embedding-rules"></a>Osadzanie reguły  
 Każdy element w modelu wystąpień musi być elementem docelowym dokładnie jeden link osadzania, z wyjątkiem korzeń modelu.  
  
 W związku z tym każda klasa nieabstrakcyjna domeny, z wyjątkiem Klasa główna musi być elementem docelowym co najmniej jedna relacja osadzania lub ten typ musi dziedziczyć z klasy bazowej osadzania. Klasa może być elementem docelowym co najmniej dwóch osadzenia, ale jego wystąpienia elementów modelu w danym momencie może mieć tylko jedną jednostkę nadrzędną. Liczebność z docelowym źródłem musi być od 0 do 1 lub 1.. 1.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>Eksplorator Wyświetla drzewo osadzania  
 Definicji DSL tworzy również Eksploratora, który użytkownicy widzą wraz z ich diagramu modelu.  
  
 ![Wygenerowany Eksploratorze DSL](../modeling/media/music-explorer.png "Music_Explorer")  
  
 Eksplorator pokazuje wszystkie elementy w modelu, nawet te, dla których nie zdefiniowano kształtów. Pokazuje elementów i relacji osadzania, ale odwołuje się do relacji.  
  
 Aby wyświetlić wartości właściwości domeny elementu, użytkownik wybierze element diagramu modelu lub w Eksploratorze modelu i spowoduje otwarcie okna właściwości. Wyświetla wszystkie właściwości domeny, łącznie z tymi, które nie są wyświetlane na diagramie. W tym przykładzie każdy utwór ma tytuł i określonego rodzaju, ale tylko wartość tytuł jest wyświetlany na diagramie.  
  
## <a name="reference-relationships"></a>Relacje odniesienia  
 Relacja odwołania reprezentuje dowolny rodzaj relacji, który nie jest osadzania.  
  
 Relacje odniesienia zazwyczaj są wyświetlane na diagramie jako łączniki między kształtów.  
  
 W modelu reprezentację XML łącza między dwoma elementami jest reprezentowane za pomocą *monikerów.* Oznacza to monikerów są nazwami, które jednoznacznie identyfikują każdego elementu w modelu. Węzeł XML dla każdego elementu modelu, zawiera węzeł, który określa nazwę relacji i moniker innego elementu.  
  
## <a name="roles"></a>Role  
 Każda relacja domeny ma dwie role, do roli źródłowej i roli docelowej.  
  
 Na poniższej ilustracji, wiersz między **wydawcy** klasy domeny i **PublisherCatalog** relacji domeny jest roli źródłowej. Wiersz między relacji domeny i **albumu** klasy domeny jest roli docelowej.  
  
 ![Role i właściwości. ](../modeling/media/propertycode.png "PropertyCode")  
  
 Nazwy skojarzone z relacji są szczególnie ważne podczas pisania kodu programu, który przechodzi przez model. Na przykład podczas kompilowania rozwiązania DSL wygenerowanej klasy Publisher ma właściwość katalogu, który jest kolekcją albumów. Klasa albumu ma właściwość wydawcy, który jest pojedynczym wystąpieniem klasy wydawcy.  
  
 Po utworzeniu relacji w definicji DSL nazwy właściwości i relacji są podane wartości domyślne. Można jednak zmienić je.  
  
## <a name="multiplicities"></a>Liczebność punktów  
 Liczebność punktów Określ, ile elementów może mieć tę samą rolę w relacji domeny. W tym przykładzie zero do wielu (0..\*) ustawienia liczebności na **katalogu** roli Określa, że dowolne wystąpienie **wydawcy** klasa domeny może mieć tyle  **PublisherCatalog** relacji łączy, jaką chcesz nadać mu.  
  
 Konfigurowanie Liczebność roli, wpisując na diagramie lub modyfikując `Multiplicity` właściwość **właściwości** okna. W poniższej tabeli opisano ustawienia dla tej właściwości.  
  
|Typ liczebność|Opis|  
|-----------------------|-----------------|  
|0.. * (zero do wielu)|Każde wystąpienie klasy domeny może mieć wiele wystąpień tej relacji lub nie wystąpienia relacji.|  
|Od 0 do 1 (zero do jednego)|Każde wystąpienie klasy domeny może mieć nie więcej niż jedno wystąpienie relacji lub nie wystąpienia relacji.|  
|1..1 (po jednym)|Każde wystąpienie klasy domeny może mieć jedno wystąpienie relacji. Nie można utworzyć więcej niż jedno wystąpienie tej relacji z dowolnej instancji klasy roli. Jeśli włączono weryfikację błąd sprawdzania poprawności pojawi się, gdy dowolne wystąpienie klasy roli ma żadne wystąpienie relacji.|  
|1.. * (jeden do wielu)|Każde wystąpienie klasy na roli, która ma liczebność to może mieć wiele wystąpień tej relacji, a każde wystąpienie musi mieć co najmniej jedno wystąpienie relacji. Jeśli włączono weryfikację błąd sprawdzania poprawności pojawi się, gdy dowolne wystąpienie klasy roli ma żadne wystąpienie relacji.|  
  
## <a name="domain-relationships-as-classes"></a>Relacje domeny jako klasy  
 Łącze jest reprezentowana w Store jako wystąpienie LinkElement, czyli klasę pochodną ModelElement. Te właściwości można zdefiniować diagramu modelu domeny na relacji domeny.  
  
 Można również ustawić relację źródłowych lub docelowych relacje. Na diagramie modelu domeny, kliknij prawym przyciskiem myszy relacji domeny, a następnie kliknij przycisk **Pokaż jako klasę**. Zostanie wyświetlone okno dodatkowe klasy. Można następnie nawiązywanie relacji.  
  
 Podobnie jak w przypadku klas domeny, częściowo poprzez dziedziczenie, można zdefiniować relację. Wybierz pochodnej relacji i ustaw **relacji podstawowej** w oknie dialogowym właściwości.  
  
 Pochodnej relacji specjalizuje się jej relacją podstawową. Domeny klas, które dział it, który łączy powinny pochodzić z lub taka sama jak klasy połączone relacji bazowej. Po utworzeniu łącza pochodnej relacji w modelu jest wystąpieniem pochodnej i relacji podstawowych. W kodzie programu możesz przejść do przeciwległym końcu łącza za pomocą właściwości generowane przez podstawę lub w klasie pochodnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Relacje domeny w generowanego interfejsu API](../misc/domain-relationships-in-the-generated-api.md)   
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
