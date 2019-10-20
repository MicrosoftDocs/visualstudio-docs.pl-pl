---
title: Zrozumienie modeli, klas i relacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5426c6f8e9c4a932430a0c3bd3df6d98400c3562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659560"
---
# <a name="understanding-models-classes-and-relationships"></a>Opis modeli, klas i relacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Język specyficzny dla domeny (DSL) jest zdefiniowany przez plik definicji DSL, wraz z dowolnym niestandardowym kodem programu, który można napisać. Większość kodu programu w rozwiązaniu DSL jest generowana z tego pliku.

 W tym temacie objaśniono centralne funkcje definicji DSL.

## <a name="the-dsl-definition"></a>Definicja DSL
 Po otwarciu `Dsl\DslDefinition.dsl` okno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] będzie wyglądać podobnie do poniższej ilustracji.

 ![Projektant DSL](../modeling/media/dsl-designer.png "dsl_designer")

 Najważniejsze informacje w definicji DSL są wyświetlane na diagramie definicji DSL. Dodatkowe informacje, które są również częścią DslDefinition. DSL, są wyświetlane w Eksploratorze DSL, który zwykle pojawia się po stronie diagramu. Możesz współpracować z diagramem dla najbardziej częstych zadań i z Eksploratorem DSL, aby uzyskać bardziej zaawansowane dostosowania.

 Diagram definicji DSL przedstawia klasy domeny, które definiują elementy modelu i relacje, które definiują linki między elementami modelu. Pokazuje także kształty i łączniki, które są używane do wyświetlania elementów modelu dla użytkownika.

 ![Projektant DSL z torem](../modeling/media/dsl-desinger.png "dsl_desinger")

 Po wybraniu elementu w definicji DSL na diagramie lub w Eksploratorze DSL informacje o nim zostaną wyświetlone w okno Właściwości. Dodatkowe informacje mogą być wyświetlane w oknie Szczegóły DSL.

### <a name="models-are-instances-of-dsls"></a>Modele są wystąpieniami językami DSL
 *Model* to wystąpienie DSL utworzone przez użytkownika. Model zawiera elementy modelu, które są wystąpieniami klas domeny zdefiniowanych przez użytkownika, oraz linki między elementami, które są wystąpieniami zdefiniowanych relacji domeny. Model może również zawierać kształty i łączniki, które wyświetlają elementy modelu i linki na diagramie. Definicja DSL zawiera klasy kształtu, klasy łączników i klasę dla diagramu.

 Definicja DSL jest również nazywana *modelem domeny*. Definicja DSL lub model domeny to reprezentacja języka specyficznego dla domeny w czasie projektowania, natomiast model jest wystąpieniem czasu wykonywania dla języka specyficznego dla domeny.

## <a name="domain-classes-define-model-elements"></a>Klasy domen definiują elementy modelu
 Klasy domeny są używane do tworzenia różnych elementów w domenie, a relacje domen są łączami między elementami. Są to reprezentacja elementów i linków w czasie projektowania, które zostaną utworzone przez użytkowników języka specyficznego dla projektowania podczas tworzenia modeli.

 Na tej ilustracji przedstawiono model, który został utworzony przez użytkownika biblioteki utworów muzycznych DSL. Albumy muzyczne są reprezentowane przez pola zawierające listy utworów muzycznych. Artyści są reprezentowane przez pola zaokrąglone w górę i są połączone z albumy, do których zostały utworzone.

 ![Model wystąpienia wygenerowanego DSL](../modeling/media/music-instance.png "Music_Instance")

 Definicja DSL oddziela dwa aspekty. Wygląd elementów modelu na diagramie modelu jest definiowany przy użyciu klas kształtu i klas łączników. Informacje zawarte w modelu są definiowane przy użyciu klas domen i relacji domeny.

 Na poniższej ilustracji przedstawiono klasy domeny i relacje w definicji DSL biblioteki muzycznej.

 ![Relacje osadzania i odwołania](../modeling/media/music-classes.png "Music_Classes")

 Na ilustracji przedstawiono cztery klasy domeny: muzykę, album, wykonawca i utwór. Klasy domeny definiują właściwości domeny, takie jak nazwa, tytuł i tak dalej. W modelu wystąpienia wartości niektórych z tych właściwości są wyświetlane na diagramie.

 Między klasami są relacje domen: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs i ArtistAppearedOnAlbums. Relacje mają liczebność takich jak 1.. 1, 0.. *. Na przykład każdy utwór musi być powiązany z dokładnie jednym albumem za pomocą relacji AlbumHasSongs. Każdy album może zawierać dowolną liczbę utworów.

### <a name="rearranging-the-dsl-definition-diagram"></a>Ponowne rozmieszczanie diagramu definicji DSL
 Należy zauważyć, że Klasa domeny może być wyświetlana kilka razy na diagramie definicji DSL, ponieważ album znajduje się na tym obrazie. Zawsze istnieje jeden widok główny, który może zawierać wiele widoków *odwołań* .

 Aby zmienić układ diagramu definicji DSL, można:

- Zastępowanie widoków głównych i referencyjnych za pomocą poleceń **Umieść Drzewo tutaj** i **Podziel polecenia drzewa** . Kliknij prawym przyciskiem myszy jedną z klas domeny, aby wyświetlić te polecenia.

- Zmień kolejność klas domen i klas kształtów, naciskając klawisze Ctrl + Strzałka w górę i Ctrl + Strzałka w dół.

- Zwijanie lub rozwijanie klas przy użyciu ikony w prawym górnym rogu każdego kształtu.

- Zwiń części drzewa, klikając znak minus (-) u dołu klasy domeny.

## <a name="inheritance"></a>Dziedziczenie
 Klasy domeny można definiować przy użyciu dziedziczenia. Aby utworzyć wyprowadzenie dziedziczenia, kliknij narzędzie dziedziczenia, kliknij klasę pochodną, a następnie kliknij klasę bazową. Element modelu ma wszystkie właściwości, które są zdefiniowane dla własnej klasy domeny, wraz ze wszystkimi właściwościami dziedziczonymi z klasy bazowej. Dziedziczy również role w relacjach.

 Dziedziczenie może być również używane między relacjami, kształtami i łącznikami. Dziedziczenie musi pozostać w tej samej grupie. Kształt nie może dziedziczyć z klasy domeny.

## <a name="domain-relationships"></a>Relacje domeny
 Elementy modelu mogą być połączone relacjami. Łącza są zawsze binarne; łączą dokładnie dwa elementy. Jednak każdy element może mieć wiele linków do innych obiektów, a nawet może zawierać więcej niż jeden link między tą samą parą elementów.

 Tak jak można definiować różne klasy elementów, można definiować różne klasy łączy. Klasa łącza jest nazywana *relacją domeny*. Relacja domeny określa klasy elementu, które mogą nawiązywać połączenia. Każdy koniec relacji nazywa się *rolą*, a relacja domeny definiuje nazwy dla obu ról, jak również dla samej relacji.

 Istnieją dwa rodzaje relacji domeny: osadzanie relacji i relacje odwołania. Na diagramie definicji DSL relacje osadzania mają pełne linie w każdej roli, a relacje odwołań mają linie kreskowane.

### <a name="embedding-relationships"></a>Relacje osadzania
 Każdy element w modelu, z wyjątkiem jego elementu głównego, jest celem jednego łącza osadzania. W związku z tym cały model tworzy pojedyncze drzewo łączy. Relacja osadzania reprezentuje lub ma własność. Dwa elementy modelu, które są powiązane w ten sposób, są również znane jako nadrzędne i podrzędne. Element podrzędny jest określany jako osadzony w elemencie nadrzędnym.

 Linki osadzania nie są zwykle wyświetlane jawnie jako łączniki na diagramie. Zamiast tego są zwykle reprezentowane przez zawieranie. Katalog główny modelu jest reprezentowany przez diagram, a elementy osadzone w nim są wyświetlane jako kształty na diagramie.

 W tym przykładzie muzyka klasy głównej zawiera relację osadzania MusicHasAlbums do albumu, która ma AlbumHasSongs do piosenki. Utwory są wyświetlane jako elementy na liście wewnątrz każdego albumu. Muzyka ma także osadzenie MusicHasArtists do klasy wykonawcy, której wystąpienia również są wyświetlane jako kształty na diagramie.

 Domyślnie osadzone elementy są automatycznie usuwane po usunięciu ich elementów nadrzędnych.

 Gdy model jest zapisywany w pliku w formacie XML, osadzone elementy są zagnieżdżane wewnątrz ich rodziców, o ile nie dostosowano serializacji.

> [!NOTE]
> Osadzanie nie jest takie samo jak dziedziczenie. Elementy podrzędne w relacji osadzania nie dziedziczą właściwości elementu nadrzędnego. Osadzanie jest typem łącza między elementami modelu. Dziedziczenie jest relacją między klasami i nie tworzy linków między elementami modelu.

### <a name="embedding-rules"></a>Reguły osadzania
 Każdy element w modelu wystąpienia musi być elementem docelowym dokładnie jednego łącza osadzania, z wyjątkiem katalogu głównego modelu.

 W związku z tym każda nieabstrakcyjna Klasa domeny, z wyjątkiem klasy głównej, musi być elementem docelowym co najmniej jednej relacji osadzania lub musi dziedziczyć osadzenie z klasy bazowej. Klasa może być elementem docelowym co najmniej dwóch operacji osadzania, ale jego elementy modelu wystąpienia mogą mieć tylko jeden element nadrzędny jednocześnie. Liczebność z elementu docelowego do źródła musi wynosić 0.. 1 lub 1.. 1.

### <a name="the-explorer-displays-the-embedding-tree"></a>Eksplorator Wyświetla drzewo osadzania
 Definicja DSL również tworzy Eksploratora, który użytkownicy widzą obok ich diagramu modelu.

 ![Wygenerowany Eksplorator DSL](../modeling/media/music-explorer.png "Music_Explorer")

 Eksplorator pokazuje wszystkie elementy w modelu, nawet te, dla których nie zdefiniowano żadnych kształtów. Pokazuje elementy i relacje osadzania, ale nie odwołują się do relacji.

 Aby wyświetlić wartości właściwości domeny elementu, użytkownik wybiera element w diagramie modelu lub w Eksploratorze modelu, a następnie otwiera okno Właściwości. Wyświetla wszystkie właściwości domeny, w tym te, które nie są wyświetlane na diagramie. W przykładzie każdy utwór ma tytuł i gatunek, ale tylko wartość tytułu jest pokazywana na diagramie.

## <a name="reference-relationships"></a>Relacje odwołań
 Relacja odwołania reprezentuje dowolny rodzaj relacji, które nie są osadzane.

 Relacje odwołań są zwykle wyświetlane na diagramie jako łączniki między kształtami.

 W reprezentacji XML modelu łącze odwołania między dwoma elementami jest reprezentowane przy użyciu *monikerów.* Oznacza to, że monikery są nazwami, które jednoznacznie identyfikują każdy element w modelu. Węzeł XML dla każdego elementu modelu zawiera węzeł, który określa nazwę relacji i moniker drugiego elementu.

## <a name="roles"></a>Pełnione
 Każda relacja domeny ma dwie role, rolę źródłową i rolę docelową.

 Na poniższej ilustracji wiersz między klasą domeny **wydawcy** a relacją domeny **PublisherCatalog** jest rolą źródłową. Wiersz między relacją domeny a klasą domeny **albumu** jest rolą docelową.

 ![Role i właściwości.](../modeling/media/propertycode.png "PropertyCode")

 Nazwy skojarzone z relacją są szczególnie ważne podczas pisania kodu programu, który przechodzi przez model. Na przykład podczas kompilowania rozwiązania DSL wygenerowanego wydawcy klasy ma wykaz właściwości, który jest kolekcją albumów. Album klasy ma wydawcę właściwości, który jest pojedynczym wystąpieniem wydawcy klasy.

 Podczas tworzenia relacji w definicji DSL, nazwy właściwości i relacji są określone wartościami domyślnymi. Można jednak je zmienić.

## <a name="multiplicities"></a>Liczebnościami
 Liczebność określają, ile elementów może mieć tę samą rolę w relacji domeny. W tym przykładzie ustawienie liczebności zero-do-wielu (0.. \*) w roli **katalogu** określa, że każde wystąpienie klasy domeny **wydawcy** może mieć dowolną liczbę linków relacji **PublisherCatalog** , które chcesz nadać.

 Skonfiguruj liczebność roli, wpisując ją na diagramie lub modyfikując właściwość `Multiplicity` w oknie **Właściwości** . W poniższej tabeli opisano ustawienia dla tej właściwości.

|Typ mnożenia|Opis|
|-----------------------|-----------------|
|0.. * (od zera do wielu)|Każde wystąpienie klasy domeny może mieć wiele wystąpień relacji lub nie ma wystąpień relacji.|
|0.. 1 (zero do jednego)|Każde wystąpienie klasy domeny nie może mieć więcej niż jednego wystąpienia relacji lub nie ma wystąpień relacji.|
|1.. 1 (jeden)|Każde wystąpienie klasy domeny może mieć jedno wystąpienie relacji. Nie można utworzyć więcej niż jednego wystąpienia tej relacji z dowolnego wystąpienia klasy roli. Jeśli sprawdzanie poprawności jest włączone, pojawi się błąd walidacji, gdy dowolne wystąpienie klasy roli nie ma wystąpienia relacji.|
|1.. * (jeden do wielu)|Każde wystąpienie klasy w roli, która ma tę liczebność, może mieć wiele wystąpień relacji, a każde wystąpienie musi mieć co najmniej jedno wystąpienie relacji. Jeśli sprawdzanie poprawności jest włączone, pojawi się błąd walidacji, gdy dowolne wystąpienie klasy roli nie ma wystąpienia relacji.|

## <a name="domain-relationships-as-classes"></a>Relacje domeny jako klasy
 Łącze jest reprezentowane w sklepie jako wystąpienie elementu LinkElement, który jest klasą pochodną ModelElement. Te właściwości można zdefiniować na diagramie modelu domeny dla relacji domeny.

 Można również utworzyć relację źródłową lub docelową innych relacji. Na diagramie modelu domeny kliknij prawym przyciskiem myszy relację domeny, a następnie kliknij polecenie **Pokaż jako klasę**. Zostanie wyświetlone dodatkowe pole klasy. Następnie można połączyć z nim relacje.

 Istnieje możliwość zdefiniowania relacji częściowo przez dziedziczenie, podobnie jak w przypadku klas domeny. Wybierz relację pochodną i ustaw **podstawową relację** w okno właściwości.

 Relacja pochodna określa swoją relację podstawową. Klasy domeny, z którymi łączy się, powinny pochodzić lub takie same, jak klasy połączone przez relację podstawową. Gdy w modelu tworzony jest link do relacji pochodnej, jest to wystąpienie zarówno pochodne, jak i podstawowych relacji. W kodzie programu można przejść do przeciwległego końca łącza przy użyciu właściwości generowanych przez bazę lub klasę pochodną.

## <a name="see-also"></a>Zobacz też
 [Relacje domeny w wygenerowanym interfejsie API](../misc/domain-relationships-in-the-generated-api.md) [Narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
