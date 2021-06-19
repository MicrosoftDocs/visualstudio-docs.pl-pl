---
title: 'Diagramy zależności: Wskazówki'
description: Dowiedz się, jak opisać architekturę aplikacji na wysokim poziomie, tworząc diagramy zależności w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46e2b774cd4da2ef9cdb9ddef7efd19f731ade7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391026"
---
# <a name="dependency-diagrams-guidelines"></a>Diagramy zależności: wskazówki

Opisz architekturę aplikacji na wysokim poziomie, tworząc *diagramy zależności w* Visual Studio. Upewnij się, że kod pozostaje zgodny z tym projektem, w celu sprawdzania poprawności kodu za pomocą diagramu zależności. W procesie kompilacji można również uwzględnić weryfikację warstwy. Zobacz [channel 9 wideo: projektowanie i weryfikowanie architektury przy użyciu diagramów zależności.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

Aby sprawdzić, które wersje usługi Visual Studio obsługują tę funkcję, zobacz Obsługa wersji dla [architektury i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

> [!NOTE]
> Diagramy zależności dla projektów .NET Core są obsługiwane od Visual Studio 2019 w wersji 16.2.

## <a name="what-is-a-dependency-diagram"></a>Co to jest diagram zależności?

Podobnie jak w przypadku tradycyjnego diagramu architektury, diagram zależności identyfikuje główne składniki lub jednostki funkcjonalne projektu i ich współzależności. Każdy węzeł na diagramie, nazywany *warstwą*, reprezentuje logiczną grupę przestrzeni nazw, projektów lub innych artefaktów. Możesz narysować zależności, które powinny istnieć w projekcie. W przeciwieństwie do tradycyjnego diagramu architektury można sprawdzić, czy rzeczywiste zależności w kodzie źródłowym są zgodne z określonymi zamierzeniami zależności. Dzięki regularnym kompilacjom walidacji w systemie można zapewnić, że kod programu będzie nadal zgodny z architekturą systemu dzięki [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] przyszłym zmianom. Zobacz [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Jak zaprojektować lub zaktualizować aplikację za pomocą diagramów zależności

Poniższe kroki zawierają omówienie sposobu używania diagramów zależności w procesie projektowania. W kolejnych sekcjach tego tematu opisano więcej szczegółów na temat każdego kroku. Jeśli opracowujesz nowy projekt, pomiń kroki odwołujące się do istniejącego kodu.

> [!NOTE]
> Te kroki są wyświetlane w przybliżonej kolejności. Prawdopodobnie będziesz chcieć nakładać zadania, zmieniać ich kolejność, aby odpowiadały Twojej sytuacji, i ponownie je wykonywać na początku każdej iteracji w projekcie.

1. [Utwórz diagram zależności](#Create) dla całej aplikacji lub dla warstwy w jej obrębie.

2. [Zdefiniuj warstwy reprezentujące podstawowe obszary funkcjonalne lub](#CreateLayers) składniki aplikacji. Nadaj tym warstwom nazwy zgodnie z ich funkcją, na przykład "Prezentacja" lub "Usługi". Jeśli masz rozwiązanie Visual Studio, możesz skojarzyć każdą warstwę z kolekcją artefaktów, takich jak projekty, przestrzenie nazw, pliki i tak dalej.

3. [Odnajdywanie istniejących zależności między](#Generate) warstwami.

4. [Edytuj warstwy i zależności,](#EditArchitecture) aby wyświetlić zaktualizowany projekt, który ma zostać odzwierciedlony w kodzie.

5. [Zaprojektuj](#NewAreas) nowe obszary aplikacji, tworząc warstwy reprezentujące główne bloki lub składniki architektury i definiując zależności, aby pokazać, jak każda warstwa używa innych.

6. [Edytuj układ i wygląd diagramu,](#EditLayout) aby ułatwić jego omawianie ze współpracownikami.

7. [Zweryfikuj kod względem diagramu zależności,](#Validate) aby wyróżnić konflikty między kodem i wymaganą architekturą.

8. [Zaktualizuj kod, aby był zgodny z nową architekturą](#UpdateCode). Iteracyjnie opracuj i refaktoryzuj kod, dopóki walidacja nie pokaże żadnych konfliktów.

9. [Uwzględnij walidację warstwy w procesie kompilacji,](#BuildValidation) aby mieć pewność, że kod będzie nadal zgodny z projektem.

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Tworzenie diagramu zależności

Diagram zależności musi zostać utworzony wewnątrz projektu modelowania. Możesz dodać nowy diagram zależności do istniejącego projektu modelowania, utworzyć nowy projekt modelowania dla diagramu zależności lub skopiować istniejący diagram zależności w ramach tego samego projektu modelowania.

> [!IMPORTANT]
> Nie należy dodawać, przeciągać ani kopiować istniejącego diagramu zależności z projektu modelowania do innego projektu modelowania lub do innej lokalizacji w rozwiązaniu. Diagram zależności, który jest kopiowany w ten sposób, będzie miał takie same odwołania jak oryginalny diagram, nawet jeśli zmodyfikuje diagram. Uniemożliwi to prawidłowe działanie walidacji warstwy i może spowodować inne problemy, takie jak brakujące elementy lub inne błędy podczas próby otwarcia diagramu.

Zobacz [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Definiowanie warstw reprezentujących obszary funkcjonalne lub składniki

Warstwy reprezentują logiczne grupy *artefaktów*, takie jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Warstwy można tworzyć z artefaktów z projektów visual C# i Visual Basic lub dołączać specyfikacje lub plany do warstwy, łącząc dokumenty, takie jak pliki programu Word lub prezentacje programu PowerPoint. Każda warstwa jest wyświetlana na diagramie jako prostokąt i pokazuje liczbę połączonych z nim artefaktów. Warstwa może zawierać warstwy zagnieżdżone, które opisują bardziej szczegółowe zadania.

Ogólną wytycznym jest nazwanie warstw zgodnie z ich funkcją, na przykład "Prezentacja" lub "Usługi". Jeśli artefakty są ściśle zależne od siebie, umieść je w tej samej warstwie. Jeśli artefakty mogą być aktualizowane oddzielnie lub używane w oddzielnych aplikacjach, umieść je w różnych warstwach. Aby dowiedzieć się więcej na temat wzorców warstw, odwiedź witrynę Patterns & Practices (Wzorce & practices) pod witrynie [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) .

> [!TIP]
> Istnieją pewne typy artefaktów, które można połączyć z warstwami, ale które nie obsługują weryfikacji względem diagramu zależności. Aby sprawdzić, czy artefakt obsługuje walidację, otwórz **Eksplorator warstwy,** aby sprawdzić właściwość **Obsługuje** walidację linku artefaktu. Zobacz [Odnajdywanie istniejących zależności między warstwami](#Generate).

Podczas aktualizowania nieznanej aplikacji można również tworzyć mapy kodu. Te diagramy mogą ułatwić odnajdywanie wzorców i zależności podczas eksplorowania kodu. Użyj Eksplorator rozwiązań, aby eksplorować przestrzenie nazw i klasy, które często dobrze odpowiadają istniejącym warstwom. Przypisz te artefakty kodu do warstw, przeciągając je Eksplorator rozwiązań do diagramów zależności. Następnie możesz użyć diagramów zależności, aby zaktualizować kod i zachować jego spójność z projektem.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Odnajdywanie istniejących zależności między warstwami

Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Istniejące zależności można odnajdywać przez ich odwrotną inżynierię.

> [!NOTE]
> Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby zobaczyć, które artefakty mają zależności, które można odwrócić, kliknij prawym przyciskiem myszy jedną lub wiele warstw, a następnie kliknij polecenie **Wyświetl linki.** W **Eksploratorze warstw** sprawdź **kolumnę Obsługuje walidację.** Zależności nie zostaną odtąd zaprojektowane dla artefaktów, dla których ta kolumna zawiera wartość **False**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Aby odwrócić istniejące zależności między warstwami

Wybierz jedną lub wiele warstw, kliknij prawym przyciskiem myszy wybraną warstwę, a następnie kliknij polecenie **Generuj zależności.**

Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Edytowanie warstw i zależności w celu pokazania zamierzonego projektu

Aby opisać zmiany, które planujesz wprowadzić w systemie lub zamierzonej architekturze, użyj następujących kroków, aby edytować diagram zależności. Możesz również rozważyć wprowadzenie pewnych zmian refaktoryzacji, aby poprawić strukturę kodu przed rozszerzeniem go. Zobacz [Improving the structure of the code (Ulepszanie struktury kodu).](#Improving)

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Usuwanie zależności, która nie powinna istnieć|Kliknij zależność, a następnie naciśnij klawisz **DELETE.**|
|Zmień lub ogranicz kierunek zależności|Ustaw jej **właściwość Direction.**|
|Tworzenie nowych zależności|Użyj narzędzi **Zależność** i **Zależność dwukierunkowa.**<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Po zakończeniu kliknij narzędzie **Wskaźnik** lub naciśnij klawisz **ESC.**|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw we właściwości Zależności niedozwolonej **przestrzeni nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw we właściwości **Zabronione przestrzenie nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw we właściwości **Wymagane przestrzenie nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Ulepszanie struktury kodu

Zmiany refaktoryzacji to ulepszenia, które nie wpływają na zachowanie aplikacji, ale ułatwiają zmianę i rozszerzenie kodu w przyszłości. Dobrze ustrukturyzowany kod ma projekt, który można łatwo wyeksstrować do diagramu zależności.

Jeśli na przykład utworzysz warstwę dla każdej przestrzeni nazw w kodzie, a następnie odtąd utworzysz zależności, między warstwami powinien być minimalny zestaw jednokierunkowych zależności. Jeśli utworzysz bardziej szczegółowy diagram przy użyciu klas lub metod jako warstw, wynik powinien również mieć te same właściwości.

Jeśli tak nie jest, kod będzie trudniejszy do zmiany w całym cyklu życia i będzie mniej odpowiedni do walidacji przy użyciu diagramów zależności.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Projektowanie nowych obszarów aplikacji

Po rozpoczęciu opracowywania nowego projektu lub nowego obszaru w nowym projekcie można narysować warstwy i zależności, aby ułatwić identyfikację głównych składników przed rozpoczęciem opracowywania kodu.

- **Pokazywanie możliwych do zidentyfikowania** wzorców architektury w diagramach zależności, jeśli jest to możliwe. Na przykład diagram zależności opisujący aplikację klasy desktop może zawierać warstwy takie jak Prezentacja, Logika domeny i Magazyn danych. Diagram zależności, który obejmuje jedną funkcję w aplikacji, może mieć warstwy, takie jak Model, Widok i Kontroler. Aby uzyskać więcej informacji na temat takich wzorców, zobacz [Patterns & Practices: Application Architecture](https://archive.codeplex.com/?p=apparch).

- **Utwórz artefakt kodu dla każdej warstwy,** takiej jak przestrzeń nazw, klasa lub składnik. Ułatwia to obserwowanie kodu i łączenie artefaktów kodu z warstwami. Po utworzeniu każdego artefaktu połącz go z odpowiednią warstwą.

- **Nie trzeba łączyć większości klas** i innych artefaktów z warstwami, ponieważ należą one do większych artefaktów, takich jak przestrzenie nazw, które zostały już połączone z warstwami.

- **Utwórz nowy diagram dla nowej funkcji**. Zazwyczaj istnieje co najmniej jeden diagram zależności opisujący całą aplikację. Jeśli projektujesz nową funkcję w aplikacji, nie dodawaj ani nie zmieniaj istniejących diagramów. Zamiast tego utwórz własny diagram, który odzwierciedla nowe części kodu. Warstwy na nowym diagramie mogą obejmować prezentację, logikę domeny i warstwy bazy danych dla nowej funkcji.

     Podczas kompilowania aplikacji kod zostanie zweryfikowany zarówno pod względem ogólnego diagramu, jak i bardziej szczegółowego diagramu funkcji.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Edytowanie układu prezentacji i dyskusji

Aby ułatwić identyfikowanie warstw i zależności lub omawiać je z członkami zespołu, edytuj wygląd i układ diagramu w następujący sposób:

- Zmień rozmiary, kształty i położenia warstw.

- Zmień kolory warstw i zależności.

  - Wybierz co najmniej jedną warstwę lub zależności, kliknij prawym przyciskiem myszy, a następnie kliknij polecenie **Właściwości**. W **oknie** Właściwości edytuj **właściwość** Color.

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Weryfikowanie kodu na diagramie

Po edytowaniu diagramu można go zweryfikować względem kodu ręcznie w dowolnym momencie lub automatycznie za każdym razem, gdy tworzysz.

Zobacz:

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

- [Uwzględnianie walidacji warstwy w procesie kompilacji](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Aktualizowanie kodu w celu zgodności z nową architekturą

Zazwyczaj błędy pojawiają się podczas pierwszej weryfikacji kodu względem zaktualizowanego diagramu zależności. Te błędy mogą mieć kilka przyczyn:

- Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

- Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zazwyczaj jest to proces iteracyjny. Aby uzyskać więcej informacji na temat tych błędów, zobacz [Validate code with dependency diagrams](../modeling/validate-code-with-layer-diagrams.md)(Weryfikowanie kodu za pomocą diagramów zależności).

> [!NOTE]
> Podczas opracowywania lub refaktoryzacji kodu mogą pojawić się nowe artefakty, które można połączyć z diagramem zależności. Może to jednak nie być konieczne, na przykład jeśli masz warstwy reprezentujące istniejące przestrzenie nazw, a nowy kod dodaje tylko więcej materiału do tych przestrzeni nazw.

Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. Po pominiesz błąd, dobrym rozwiązaniem jest rejestrowanie elementu roboczego w programie Team Foundation. Aby wykonać to zadanie, zobacz [Validate code with dependency diagrams (Weryfikowanie kodu za pomocą diagramów zależności).](../modeling/validate-code-with-layer-diagrams.md)

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Uwzględnianie walidacji warstwy w procesie kompilacji

Aby mieć pewność, że przyszłe zmiany w kodzie będą zgodne z diagramami zależności, uwzględnij weryfikację warstwy w standardowym procesie kompilacji rozwiązania. Za każdym razem, gdy inni członkowie zespołu skompilowali rozwiązanie, wszelkie różnice między zależnościami w kodzie i diagramie zależności będą zgłaszane jako błędy kompilacji. Aby uzyskać więcej informacji na temat do uwzględnienia walidacji warstwy w procesie kompilacji, zobacz [Validate code with dependency diagrams](../modeling/validate-code-with-layer-diagrams.md)(Weryfikowanie kodu za pomocą diagramów zależności).

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
