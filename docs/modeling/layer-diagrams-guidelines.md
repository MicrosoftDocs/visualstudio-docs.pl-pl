---
title: 'Diagramy zależności: Wytyczne dotyczące'
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8f4a09950de9480604d922b0d3dd5cefda17256
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908793"
---
# <a name="dependency-diagrams-guidelines"></a>Diagramy zależności: wskazówki

Opis architektury aplikacji na wysokim poziomie, tworząc *diagramów zależności* w programie Visual Studio. Upewnij się, że kod pozostaje zgodny z tym projektem, sprawdzanie poprawności kodu za pomocą diagram zależności. Można także dodać sprawdzanie poprawności warstwy w procesie kompilacji. Zobacz [wideo Channel 9: Projektowanie i Walidacja architektury za pomocą diagramów zależności](http://go.microsoft.com/fwlink/?LinkID=252073).

Aby zobaczyć, jakie wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługę wersji narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Diagramy zależności nie są obsługiwane dla projektów .NET Core w programie Visual Studio 2017.

## <a name="what-is-a-dependency-diagram"></a>Co to jest diagram zależności?

Przykład diagramu tradycyjna architektura diagram zależności identyfikuje główne składniki lub jednostki organizacyjne projektu i ich współzależności. Wywołuje się, każdy węzeł na diagramie *warstwy*, reprezentuje grupę logiczną przestrzenie nazw, projekty lub inne artefakty. Aby narysować zależności, które powinny istnieć w projekcie. W przeciwieństwie do diagramu tradycyjna architektura można zweryfikować, że rzeczywiste zależności w kodzie źródłowym są zgodne z zależności zamierzone, które zostały określone przez. Dokonując weryfikacji część regularnych kompilacji na [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], można upewnić się, że kod programu nadal stosować się do architektury systemu poprzez przyszłe zmiany. Zobacz [diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Jak zaprojektować lub zaktualizuj aplikację przy użyciu diagramów zależności

W poniższych krokach przedstawiono omówienie sposobu używania diagramów zależności w ramach procesu tworzenia. Kolejnych sekcjach, w tym temacie opisano bardziej szczegółowo o każdym kroku. Jeśli tworzysz nowy projekt, należy pominąć kroki, które odwołują się do istniejącego kodu.

> [!NOTE]
> Te kroki są wyświetlane w kolejności przybliżone. Prawdopodobnie warto nakładać się na zadaniach, zmienić kolejność je do potrzeb swojej własnej sytuacji i ich ponowne przeanalizowanie wraz na początku każdej iteracji w projekcie.

1.  [Utwórz diagram zależności](#Create) dla całej aplikacji lub dla warstwy znajdujący się w nim.

2.  [Zdefiniuj warstwy do reprezentowania podstawowych obszarów funkcjonalnych lub składniki](#CreateLayers) aplikacji. Nazwy tych warstw, zgodnie z ich funkcji, na przykład "Prezentacji" lub "Usługi". Jeśli masz rozwiązanie programu Visual Studio, każda warstwa można skojarzyć z kolekcją *artefaktów*, takich jak projekty, przestrzenie nazw, pliki i tak dalej.

3.  [Odkryj istniejące zależności](#Generate) między warstwami.

4.  [Edytowanie warstw i zależności](#EditArchitecture) Aby wyświetlić zaktualizowany projekt ma kod, aby odzwierciedlić.

5.  [Projektowanie nowych obszarów aplikacji](#NewAreas) , tworząc warstwy do reprezentowania bloków architektury podmiotu zabezpieczeń lub składniki i definiowanie zależności, aby pokazać, jak każda warstwa używa innych.

6.  [Edytuj układ i wygląd diagramu](#EditLayout) ułatwiające omówić go współpracownikom.

7.  [Walidować kod dla diagram zależności](#Validate) do wyróżnienia konfliktów między kodem i architektura potrzebujesz.

8.  [Aktualizowanie kodu do nowej architektury](#UpdateCode). Wielokrotnie tworzenie i refaktoryzacji kodu, aż sprawdzanie poprawności pokazuje żadne konflikty.

9. [Uwzględniając sprawdzanie poprawności warstwy w procesie kompilacji](#BuildValidation) aby upewnić się, że kod nadal stosować się do projektu.

## <a name="Create"></a> Tworzenie diagramów zależności

Diagram zależności, należy utworzyć w projekcie modelowania. Możesz Dodaj nowy diagram zależności do istniejącego projektu modelowania, Utwórz nowy projekt modelowania diagram zależności lub Kopiuj istniejącego diagramu zależności w obrębie tego samego projektu modelowania.

> [!IMPORTANT]
> Nie dodawać, przeciągnij lub skopiuj istniejący diagram zależności z projektu modelowania do innego projektu modelowania lub w innej lokalizacji w rozwiązaniu. Diagram zależności, które są kopiowane w ten sposób mają te same odwołania jako oryginalnego diagramu nawet wtedy, gdy modyfikować diagram. To uniemożliwi uniemożliwić prawidłowe działanie walidacji warstwy i spowodować innych problemów, takich jak brakujące elementy lub inne błędy podczas próby otwarcia diagramu.

Zobacz [tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Zdefiniuj warstwy do reprezentowania obszarów funkcjonalnych i składników

Warstwy reprezentują logiczne grupy *artefaktów*, takich jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Możesz utworzyć warstwy z artefaktów w projektach Visual C# i Visual Basic lub do warstwy można dołączyć specyfikacje lub plany, łącząc dokumenty, takie jak pliki programu Word lub prezentacje programu PowerPoint. Każda warstwa jest wyświetlana jako prostokąt na diagramie i pokazuje liczbę artefaktów, które są połączone. Warstwa może zawierać zagnieżdżone warstwy opisujące bardziej szczegółowe zadania.

Ogólną wytyczną, nazwa warstwy zgodnie z ich funkcji, na przykład "Prezentacji" lub "Usługi". Jeśli artefakty są ściśle wzajemnie, należy je umieścić w tej samej warstwie. Jeśli artefakty mogą być aktualizowane oddzielnie lub używany w aplikacjach w oddzielnych, umieść je w różnych warstwach. Aby dowiedzieć się więcej na temat wzorców warstwowe, znaleźć wzorce i praktyki [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Brak niektórych rodzajów artefaktów, które można połączyć z warstwy, ale które nie obsługują weryfikacji względem diagram zależności. Aby sprawdzić, czy artefakt obsługuje walidację, otwórz **Eksplorator warstw** zbadanie **obsługuje walidację** właściwości łącza artefaktu. Zobacz [odnajdywanie istniejące zależności między warstwami](#Generate).

Podczas aktualizowania nieznanych aplikacji, można również tworzyć mapy kodu. Te diagramy ułatwia odnajdowanie wzorców i zależności, chociaż możesz zapoznać się z kodu. Aby zapoznać się z przestrzeni nazw i klasy, które często dobrze odpowiadają istniejącym warstwom jednak używać Eksploratora rozwiązań. Przypisz te artefakty kodu do warstwy, przeciągając je w Eksploratorze rozwiązań do diagramów zależności. Można następnie użyć diagramów zależności, aby ułatwić aktualizowanie kodu i Utrzymaj spójne z projektu.

Zobacz:

-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Odkryj istniejące zależności między warstwami

Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Można sprawdzić istniejące zależności, odtwarzania je.

> [!NOTE]
> Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby zobaczyć, które artefakty mają zależności, które można odtwarzać, kliknij prawym przyciskiem myszy jednego lub wielu warstw, a następnie kliknij przycisk **Wyświetl łącza**. W **Eksplorator warstw**, sprawdź **obsługuje walidację** kolumny. Zależności nie będą odtwarzane dla artefaktów, dla których ta kolumna zawiera **False**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Aby odtwarzać istniejące zależności między warstwami

Wybierz warstwę jednego lub wielu warstw, kliknij prawym przyciskiem myszy zaznaczonej warstwy, a następnie kliknij **Wygeneruj zależności**.

Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.

## <a name="EditArchitecture"></a> Edytowanie warstw i zależności w celu przedstawienia zamierzonego projektu

Aby opisać zmiany, które planujesz wprowadzić do systemu lub zamierzonej architektury, umożliwia edytowanie diagram zależności następujące kroki. Można też rozważyć wprowadzamy zmiany refaktoryzacji w celu struktury kodu przed jej rozszerzeniem. Zobacz [poprawy struktury kodu](#Improving).

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Usuń zależności, które nie powinny istnieć|Kliknij zależności, a następnie naciśnij klawisz **Usuń**.|
|Zmień lub ogranicz kierunek zależności|Ustaw jego **kierunek** właściwości.|
|Tworzenie nowych zależności|Użyj **zależności** i **zależność dwukierunkowa** narzędzia.<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Gdy skończysz, kliknij przycisk **wskaźnik** narzędzi lub naciśnij klawisz **ESC** klucza.|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw w warstwie **zabronione zależności Namespace** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw w warstwie **zabronione przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw w warstwie **wymagane przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|

### <a name="Improving"></a> Zwiększanie struktury kodu

Refaktoryzacji zmiany dotyczą poprawy nie wpływają na sposób działania aplikacji, które ułatwia kodu do zmiany i rozszerzać w przyszłości. Kod dobrze jest projekt, który jest łatwy do abstrakcyjnej diagram zależności.

Na przykład jeśli tworzysz warstwę dla każdej przestrzeni nazw w kodzie i następnie odtwarzanie zależności, należy to minimalny zestaw jednokierunkowe zależności między warstwami. Jeśli tworzysz bardziej szczegółowego diagramu przy użyciu klasy lub metody jako warstw, w wyniku powinni również mieć takie same charakterystyki.

Jeśli nie jest to możliwe, kod będzie trudniejsze do zmieniają się przez cały jej użytkowania i będzie mniej odpowiednia do weryfikacji przy użyciu diagramów zależności.

## <a name="NewAreas"></a> Nowe obszary projektowania aplikacji

Po uruchomieniu rozwoju nowy projekt lub nowy obszar w nowym projekcie można narysować warstw i zależności w celu identyfikowania głównych składników przed przystąpieniem do tworzenia kodu.

-   **Pokaż do zidentyfikowania wzorców architektonicznych** diagramy zależność, jeśli jest to możliwe. Na przykład diagram zależności, opisujący aplikacji pulpitu może obejmować warstw, takich jak prezentacja, logika domeny i Data Store. Diagram zależności, który obejmuje pojedynczej funkcji w aplikacji może być warstw, takich jak Model, widok i kontroler. Aby uzyskać więcej informacji o tych wzorcach, zobacz [wzorce i rozwiązania: Architektura aplikacji](http://go.microsoft.com/fwlink/?LinkId=145794).

-   **Tworzenie artefaktu kodu, dla każdej warstwy** takich jak przestrzeń nazw, klasy lub składnika. Ułatwia podążają za kodem i łączenie artefaktów kodu do warstw. Zaraz po utworzeniu każdego artefaktu, połącz go do odpowiedniej warstwy.

-   **Nie masz połączyć większość klas i innych artefaktów do warstw** ponieważ mieści się w ramach większych artefaktów, takich jak przestrzenie nazw, które zostały już połączone z warstwami.

-   **Utwórz nowy diagram na nową funkcję**. Zazwyczaj będzie istnieć jeden lub więcej diagramów zależności opisujące całej aplikacji. W przypadku projektowania nowych funkcji w aplikacji, nie dodać do lub zmiana istniejących diagramów. Zamiast tego Utwórz własną diagram, który odzwierciedla nowej części kodu. Nowy diagram warstwy mogą obejmować prezentacja, logika domeny i warstwy bazy danych dla nowych funkcji.

     W przypadku tworzenia aplikacji, kodu zostanie zweryfikowana, zarówno przed ogólny diagram i bardziej szczegółowe diagramu funkcji.

## <a name="EditLayout"></a> Edytuj układ prezentacji i dyskusji

Aby pomóc Ci zidentyfikować warstw i zależności lub wdasz z członkami zespołu, należy zmodyfikować wygląd i układ diagramu w następujący sposób:

-   Zmień rozmiary, kształty i położenie warstw.

-   Zmień kolory warstw i zależności.

    -   Wybierz jeden lub więcej warstw i zależności, kliknij prawym przyciskiem myszy, a następnie kliknij **właściwości**. W **właściwości** oknie edycji **kolor** właściwości.

## <a name="Validate"></a> Sprawdź poprawność kodu na podstawie diagramu

Po zakończeniu edycji diagramu, użytkownik może sprawdzić jego poprawność kodu ręcznie w dowolnym momencie lub automatycznie każdym razem, gdy kompilujesz.

Zobacz:

-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

-   [Uwzględniając sprawdzanie poprawności warstwy w procesie kompilacji](#BuildValidation)

## <a name="UpdateCode"></a> Aktualizowanie kodu do nowej architektury

Zazwyczaj błędy pojawią się sprawdzanie poprawności kodu na podstawie diagramu zaktualizowane zależności po raz pierwszy. Te błędy mogą mieć kilka przyczyn:

-   Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

-   Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zazwyczaj jest procesem iteracyjnym. Aby uzyskać więcej informacji na temat tych błędów, zobacz [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Tworzenie lub refaktoryzować kod, Niewykluczone, że nowe artefaktów, aby połączyć diagram zależności. Jednak może to nie być konieczne, na przykład w przypadku warstwy, które reprezentują istniejącej przestrzeni nazw, a nowy kod dodaje więcej materiału tylko z tymi przestrzeniami nazw.

Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. Gdy błąd zostanie pominięty, jest dobrym rozwiązaniem do dziennika element roboczy w programie Team Foundation. Aby wykonać to zadanie, zobacz [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Uwzględniając sprawdzanie poprawności warstwy w procesie kompilacji

Aby upewnić się, że przyszłe zmiany w kodzie są zgodne z diagramów zależności, obejmują sprawdzanie poprawności warstwy do swojego rozwiązania standardowym procesem kompilacji. Zawsze, gdy inni członkowie zespołu Skompiluj rozwiązanie, różnice między zależności w kodzie i diagram zależności, będzie zgłaszane jako błędy kompilacji. Aby uzyskać więcej informacji o tym sprawdzania poprawności warstwy w procesie kompilacji, zobacz [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Zobacz także

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)