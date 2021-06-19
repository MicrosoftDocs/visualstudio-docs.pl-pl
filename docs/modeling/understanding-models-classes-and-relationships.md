---
title: Opis modeli, klas i relacji
description: Dowiedz się, jak język specyficzny dla domeny (DSL) jest definiowany przez jego plik definicji DSL i że większość kodu programu w rozwiązaniu DSL jest generowana na podstawie tego pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b086f21b466863c3498ce15c15f7077b358c6d39
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388623"
---
# <a name="understanding-models-classes-and-relationships"></a>Opis modeli, klas i relacji
Język specyficzny dla domeny (DSL) jest definiowany przez jego plik definicji DSL wraz z dowolnym niestandardowym kodem programu, który można napisać. Większość kodu programu w rozwiązaniu DSL jest generowana na podstawie tego pliku.

 W tym temacie wyjaśniono centralne funkcje definicji DSL.

## <a name="the-dsl-definition"></a>Definicja DSL
 Po otwarciu `Dsl\DslDefinition.dsl` okna Visual Studio podobne do poniższego.

 ![dsl designer](../modeling/media/dsl_designer.png)

 Najważniejsze informacje w definicji DSL są wyświetlane na diagramie definicji DSL. Dodatkowe informacje, które są również częścią DslDefinition.dsl, są wyświetlane w Eksploratorze DSL, który zazwyczaj jest wyświetlany na stronie diagramu. Pracujesz z diagramem dla najczęściej wykonywanych zadań i z Eksploratorem DSL w celu bardziej zaawansowanych dostosowań.

 Diagram definicji DSL przedstawia klasy domeny, które definiują elementy modelu, i relacje, które definiują łącza między elementami modelu. Pokazuje również kształty i łączniki, które są używane do wyświetlania użytkownikowi elementów modelu.

 ![dsl designer with tolane (projektant dsl z toriem)](../modeling/media/dsl_desinger.png)

 Po wybraniu elementu w definicji DSL, na diagramie lub w Eksploratorze DSL, informacje o nim są wyświetlane w okno Właściwości. Dodatkowe informacje mogą być wyświetlane w oknie Szczegóły DSL.

### <a name="models-are-instances-of-dsls"></a>Modele są wystąpieniami plików DSL
 Model *to* wystąpienie DSL utworzone przez użytkownika. Model zawiera elementy modelu, które są wystąpieniami definiowania klas domeny oraz łącza między elementami, które są wystąpieniami relacji domeny, które definiujesz. Model może również mieć kształty i łączniki, które wyświetlają elementy modelu i linki na diagramie. Definicja DSL zawiera klasy kształtów, klasy łączników i klasę dla diagramu.

 Definicja DSL jest również znana jako *model domeny*. Definicja DSL lub model domeny jest reprezentacją języka specyficznego dla domeny w czasie projektowania, natomiast model jest wystąpieniami w czasie działania języka specyficznego dla domeny.

## <a name="domain-classes-define-model-elements"></a>Klasy domen definiują elementy modelu
 Klasy domeny są używane do tworzenia różnych elementów w domenie, a relacje domeny są łączami między elementami. Są one reprezentacją elementów i linków w czasie projektowania, które będą tworzyć wystąpienia użytkowników języka specyficznego dla projektu podczas tworzenia modeli.

 Na tej ilustracji przedstawiono model, który został utworzony przez użytkownika biblioteki muzyki DSL. Muzyka jest reprezentowana przez pola zawierające listy utworów. Artystów są reprezentowane przez okrągłe narożniki i są połączone z komputerami, do których się przyczyniły.

 ![Model wystąpienia wygenerowanego DSL](../modeling/media/music_instance.png)

 Definicja DSL oddziela dwa aspekty. Wygląd elementów modelu na diagramie modelu jest definiowany przy użyciu klas kształtów i klas łączników. Informacje przeniesiene w modelu są definiowane przy użyciu klas domeny i relacji domeny.

 Na poniższej ilustracji przedstawiono klasy domen i relacje w definicji DSL biblioteki muzyki.

 ![Osadzanie i relacje odwoływać](../modeling/media/music_classes.png)

 Na ilustracji przedstawiono cztery klasy domen: Music ( Muzyka), Artist (Muzyka), Artist (Autor) i Song (Utwór). Klasy domen definiują właściwości domeny, takie jak Nazwa, Tytuł i tak dalej. W modelu wystąpienia wartości niektórych z tych właściwości są wyświetlane na diagramie.

 Między klasami są relacje domeny: MusicHasAlbums, MusicHasArtists,BonbHasSongs i ArtistAppearedOnAlbums. Relacje mają mnożenia, takie jak 1..1, 0..*. Na przykład każdy utwór musi być powiązany z dokładnie jednym Utworem za pośrednictwem relacji TheKiHasSongs. Każdy z nich może mieć dowolną liczbę utworów.

### <a name="rearranging-the-dsl-definition-diagram"></a>Zmiana rozmieszczania diagramu definicji DSL
 Zwróć uwagę, że klasa domeny może pojawić się kilka razy na diagramie definicji DSL, tak jak Na tej ilustracji. Zawsze istnieje jeden widok główny, a niektóre widoki referencyjne mogą *być* dostępne.

 Aby zmienić rozmieszczenie diagramu definicji DSL, można:

- Zamień widoki główne i widoki referencyjne za pomocą poleceń **Bring Tree Here (Przynieź drzewo tutaj)** **i Split Tree (Podziel** drzewo). Kliknij prawym przyciskiem myszy pojedynczą klasę domeny, aby wyświetlić te polecenia.

- Aby ponownie uporządkować klasy domen i klasy kształtów, naciśnij klawisze Ctrl+W górę i Ctrl+W dół.

- Zwiń lub rozwiń klasy przy użyciu ikony w prawym górnym rogu każdego kształtu.

- Zwiń części drzewa, klikając znak minus (-) w dolnej części klasy domeny.

## <a name="inheritance"></a>Dziedziczenie
 Klasy domen można zdefiniować za pomocą dziedziczenia. Aby utworzyć dziedziczenie pochodne, kliknij narzędzie Dziedziczenie, kliknij klasę pochodną, a następnie kliknij klasę bazową. Element modelu ma wszystkie właściwości, które są zdefiniowane we własnej klasie domeny, wraz ze wszystkimi właściwościami dziedziczoną z klasy bazowej. Dziedziczy również swoje role w relacjach.

 Dziedziczenie może być również używane między relacjami, kształtami i łącznikami. Dziedziczenie musi znajdować się w tej samej grupie. Kształt nie może dziedziczyć z klasy domeny.

## <a name="domain-relationships"></a>Relacje między domenami
 Elementy modelu można połączyć za pomocą relacji. Linki są zawsze binarne; Łączy dokładnie dwa elementy. Jednak każdy element może mieć wiele linków do innych obiektów, a nawet może być więcej niż jedno łącze między tymi samymi dwiema elementami.

 Tak jak można zdefiniować różne klasy elementów, można zdefiniować różne klasy linków. Klasa łącza jest nazywana *relacją domeny*. Relacja domeny określa, jakie klasy elementu mogą łączyć się jego wystąpienia. Każdy koniec relacji jest nazywany *rolą*, a relacja domeny definiuje nazwy dla dwóch ról, a także dla samej relacji.

 Istnieją dwa rodzaje relacji domeny: osadzanie relacji i relacje odwoływać. Na diagramie definicji DSL relacje osadzania mają linie ciągłe w każdej roli, a relacje odwoływać się mają linie przerywane.

### <a name="embedding-relationships"></a>Osadzanie relacji
 Każdy element w modelu, z wyjątkiem jego elementu głównego, jest elementem docelowym jednego linku osadzania. W związku z tym cały model tworzy pojedyncze drzewo linków osadzania. Relacja osadzania reprezentuje zawieranie lub własność. Dwa elementy modelu, które są powiązane w ten sposób, są również nazywane elementami nadrzędnymi i podrzędnymi. Mówi się, że element podrzędny jest osadzony w nadrzędnym.

 Linki osadzania nie są zwykle wyświetlane jawnie jako łączniki na diagramie. Zamiast tego są one zwykle reprezentowane przez zawieranie. Katalog główny modelu jest reprezentowany przez diagram, a osadzone w nim elementy są wyświetlane jako kształty na diagramie.

 W tym przykładzie główna klasa Music ma relację osadzania MusicHasAlbums z negocją Użytkownika MusicHasAlbums z Elementem, który ma osadzenie w aplikacji MusicHasSongs z utworem. Utwory są wyświetlane jako elementy na liście w każdym z nich. W klasie Artist znajduje się również element MusicHasArtists, którego wystąpienia są również wyświetlane jako kształty na diagramie.

 Domyślnie osadzone elementy są automatycznie usuwane, gdy ich elementy główne są usuwane.

 Gdy model jest zapisywany w pliku w formacie XML, osadzone elementy są zagnieżdżone wewnątrz ich elementówliśmy, chyba że dostosowano serializacji.

> [!NOTE]
> Osadzanie to nie to samo co dziedziczenie. Elementy podrzędny w relacji osadzania nie dziedziczą właściwości elementu nadrzędnego. Osadzanie to typ połączenia między elementami modelu. Dziedziczenie jest relacją między klasami i nie tworzy połączeń między elementami modelu.

### <a name="embedding-rules"></a>Reguły osadzania
 Każdy element w modelu wystąpienia musi być elementem docelowym dokładnie jednego linku osadzania, z wyjątkiem elementu głównego modelu.

 W związku z tym każda nie abstrakcyjna klasa domeny, z wyjątkiem klasy głównej, musi być obiektem docelowym co najmniej jednej relacji osadzania lub musi dziedziczyć osadzanie z klasy bazowej. Klasa może być celem co najmniej dwóch osadzeń, ale jej elementy modelu wystąpienia mogą mieć tylko jeden element nadrzędny na raz. Liczebność między elementami docelowymi i źródłowymi musi mieć wartość 0..1 lub 1..1.

### <a name="the-explorer-displays-the-embedding-tree"></a>Eksplorator wyświetla drzewo osadzania
 Definicja DSL tworzy również eksploratora, który użytkownicy widzą obok diagramu modelu.

 ![Wygenerowany eksplorator DSL](../modeling/media/music_explorer.png)

 Eksplorator pokazuje wszystkie elementy w modelu, nawet te, dla których nie zdefiniowano żadnych kształtów. Pokazuje elementy i relacje osadzania, ale nie odwołują się do relacji.

 Aby wyświetlić wartości właściwości domeny elementu, użytkownik wybiera element na diagramie modelu lub w eksploratorze modelu i otwiera okno Właściwości. Wyświetla wszystkie właściwości domeny, w tym te, które nie są wyświetlane na diagramie. W tym przykładzie każdy utwór ma tytuł i gatunek, ale na diagramie jest wyświetlana tylko wartość tytułu.

## <a name="reference-relationships"></a>Relacje odwołuj się
 Relacja odwołania reprezentuje dowolny rodzaj relacji, która nie jest osadzana.

 Relacje odwołuj się zwykle są wyświetlane na diagramie jako łączniki między kształtami.

 W reprezentacji XML modelu połączenie odwołania między dwoma elementami jest reprezentowane przy *użyciu monikerów.* To oznacza, że monikery to nazwy, które jednoznacznie identyfikują każdy element w modelu. Węzeł XML dla każdego elementu modelu zawiera węzeł, który określa nazwę relacji i monikera innego elementu.

## <a name="roles"></a>Role
 Każda relacja domeny ma dwie role: rolę źródłową i rolę docelową.

 Na poniższej ilustracji wiersz między klasą **domeny Publisher** i relacją domeny **PublisherCatalog** jest rolą źródłową. Wiersz między relacją domeny i klasą **domeny OS** jest rolą docelową.

 ![Role i właściwości.](../modeling/media/propertycode.png)

 Nazwy skojarzone z relacją są szczególnie ważne podczas pisania kodu programu, który przechodzi przez model. Na przykład podczas kompilowania rozwiązania DSL wygenerowana klasa Publisher ma właściwość Catalog, która jest kolekcją Rozwiązania. Klasa Ma właściwość Publisher, która jest pojedynczym wystąpieniem klasy Publisher.

 Podczas tworzenia relacji w definicji DSL nazwy właściwości i relacji są nadawać wartości domyślne. Można je jednak zmienić.

## <a name="multiplicities"></a>Mnożenia
 Mnożenia określają, ile elementów może mieć tę samą rolę w relacji domeny. W tym przykładzie ustawienie liczebności zero-do-wielu (0.. ) w roli katalogu określa, że dowolne wystąpienie klasy domeny Wydawca może mieć tyle linków relacji \* **publishercatalog,**  ile chcesz nadać. 

 Skonfiguruj liczebność roli, wpisując na diagramie lub modyfikując `Multiplicity` właściwość w **oknie** Właściwości. W poniższej tabeli opisano ustawienia tej właściwości.

|Typ liczebności|Opis|
|-|-|
|0..* (zero do wielu)|Każde wystąpienie klasy domeny może mieć wiele wystąpień relacji lub nie może mieć żadnych wystąpień relacji.|
|0..1 (zero do jednego)|Każde wystąpienie klasy domeny może mieć nie więcej niż jedno wystąpienie relacji lub nie może mieć żadnych wystąpień relacji.|
|1..1 (jeden)|Każde wystąpienie klasy domeny może mieć jedno wystąpienie relacji. Nie można utworzyć więcej niż jednego wystąpienia tej relacji z żadnego wystąpienia klasy roli. Jeśli weryfikacja jest włączona, zostanie wyświetlony błąd walidacji, gdy dowolne wystąpienie klasy roli nie ma wystąpienia relacji.|
|1..* (jeden do wielu)|Każde wystąpienie klasy w roli, która ma tę liczebność, może mieć wiele wystąpień relacji, a każde wystąpienie musi mieć co najmniej jedno wystąpienie relacji. Jeśli weryfikacja jest włączona, zostanie wyświetlony błąd walidacji, gdy dowolne wystąpienie klasy roli nie ma wystąpienia relacji.|

## <a name="domain-relationships-as-classes"></a>Relacje domeny jako klasy
 Link jest reprezentowany w magazynie jako wystąpienie elementu LinkElement, który jest klasą pochodną elementu ModelElement. Te właściwości można zdefiniować w diagramie modelu domeny w relacjach domeny.

 Można również ustawić relację jako źródło lub obiekt docelowy innych relacji. Na diagramie modelu domeny kliknij prawym przyciskiem myszy relację domeny, a następnie kliknij polecenie **Pokaż jako klasę**. Zostanie wyświetlone dodatkowe pole klasy. Następnie możesz połączyć z nim relacje.

 Relację można zdefiniować częściowo przez dziedziczenie, podobnie jak w przypadku klas domeny. Wybierz relację pochodną i ustaw **pozycję Relacja podstawowa** w okno Właściwości.

 Relacja pochodna specjalizuje się w jej podstawowej relacji. Klasy domen, które łączy, powinny pochodzić z klasy połączonej relacją podstawową lub być takie same. Gdy w modelu jest tworzony link relacji pochodnej, jest to wystąpienie zarówno relacji pochodnej, jak i podstawowej. W kodzie programu możesz przejść do przeciwległego końca linku przy użyciu właściwości wygenerowanych przez bazę lub klasę pochodną.

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))