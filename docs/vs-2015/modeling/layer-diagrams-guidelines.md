---
title: 'Diagramy warstw: wskazówki | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21376668eef88d3d8ce42ff73785b972be045cb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850633"
---
# <a name="layer-diagrams-guidelines"></a>Diagramy warstw: Zalecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opisz architekturę aplikacji na wysokim poziomie, tworząc *diagramy warstwowe* w programie Visual Studio. Upewnij się, że kod pozostaje spójny z tym projektem, sprawdzając poprawność kodu przy użyciu diagramu warstwowego. Możesz również uwzględnić walidację warstwy w procesie kompilacji. Zobacz [wideo Channel 9: projektowanie i weryfikowanie architektury przy użyciu diagramów warstwowych](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-layer-diagram"></a>Co to jest diagram warstwowy?
 Podobnie jak w przypadku tradycyjnego diagramu architektury, diagram warstwowy identyfikuje główne składniki lub jednostki funkcjonalne projektu i ich współzależności. Każdy węzeł na diagramie o nazwie *warstwa*reprezentuje logiczną grupę przestrzeni nazw, projektów lub innych artefaktów. Możesz narysować zależności, które powinny istnieć w projekcie. W przeciwieństwie do tradycyjnego diagramu architektury można sprawdzić, czy rzeczywiste zależności w kodzie źródłowym są zgodne z zamierzonymi zależnościami określonymi przez użytkownika. Dzięki wprowadzeniu częściowej walidacji regularnej kompilacji w [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] programie można upewnić się, że kod programu będzie nadal przestrzegać architektury systemu przy użyciu przyszłych zmian. Zobacz [diagramy warstwowe: odwołanie](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-layer-diagrams"></a><a name="Update"></a> Jak projektować lub aktualizować aplikację przy użyciu diagramów warstw
 Poniższe kroki zawierają omówienie sposobu używania diagramów warstwowych w ramach procesu tworzenia oprogramowania. W kolejnych sekcjach tego tematu opisano więcej szczegółów na temat każdego kroku. Jeśli tworzysz nowy projekt, Pomiń procedurę odwołującą się do istniejącego kodu.

> [!NOTE]
> Te kroki są wyświetlane w przybliżonej kolejności. Prawdopodobnie chcesz nakładać się na zadania, zmienić ich kolejność, aby dostosować je do własnych sytuacji i ponownie je odwiedzać na początku każdej iteracji w projekcie.

1. [Utwórz diagram warstwy](#Create) dla całej aplikacji lub dla warstwy w niej.

2. [Zdefiniuj warstwy, aby reprezentować podstawowe obszary funkcjonalne lub składniki](#CreateLayers) aplikacji. Nazwij te warstwy według ich funkcji, na przykład "prezentacja" lub "usługi". Jeśli masz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, możesz skojarzyć każdą warstwę z kolekcją *artefaktów*, takimi jak projekty, przestrzenie nazw, pliki i tak dalej.

3. [Odkryj istniejące zależności](#Generate) między warstwami.

4. [Edytuj warstwy i zależności](#EditArchitecture) , aby wyświetlić zaktualizowany projekt, który ma być odzwierciedlany przez kod.

5. [Zaprojektuj nowe obszary aplikacji](#NewAreas) przez utworzenie warstw do reprezentowania głównych bloków architektury lub składników i zdefiniowanie zależności, aby pokazać, w jaki sposób każda warstwa używa innych.

6. [Edytuj układ i wygląd diagramu](#EditLayout) , aby pomóc w omówieniu go współpracownikom.

7. [Sprawdź poprawność kodu względem diagramu warstwowego](#Validate) , aby wyróżnić konflikty między kodem a wymaganą architekturą.

8. [Zaktualizuj kod, aby był zgodny z nową architekturą](#UpdateCode). Iteracyjnie opracowuje i refaktoryzacji kodu do momentu, gdy Walidacja nie wyświetli żadnych konfliktów.

9. [Uwzględnij walidację warstwy w procesie kompilacji](#BuildValidation) , aby upewnić się, że kod będzie nadal zgodny z projektem.

## <a name="create-a-layer-diagram"></a><a name="Create"></a> Tworzenie diagramu warstwowego
 Diagram warstwowy musi być utworzony w projekcie modelowania. Można dodać nowy diagram warstwowy do istniejącego projektu modelowania, utworzyć nowy projekt modelowania dla diagramu warstwy lub skopiować istniejący diagram warstwowy w ramach tego samego projektu modelowania.

> [!IMPORTANT]
> Nie dodawaj, nie przeciągaj ani nie Kopiuj istniejącego diagramu warstwowego z projektu modelowania do innego projektu modelowania lub do innej lokalizacji w rozwiązaniu. Diagram warstwowy, który jest kopiowany w ten sposób, będzie miał takie same odwołania jak oryginalny diagram, nawet w przypadku zmodyfikowania diagramu. Uniemożliwi to prawidłowe działanie walidacji warstwy i może spowodować inne problemy, takie jak brakujące elementy lub inne błędy podczas próby otwarcia diagramu.

 Zobacz [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Definiowanie warstw do reprezentowania obszarów funkcjonalnych lub składników
 Warstwy reprezentują logiczne grupy *artefaktów*, takie jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Można tworzyć warstwy na podstawie artefaktów z Visual C# .NET i Visual Basic projektów .NET. można również dołączać specyfikacje lub plany do warstwy, łącząc dokumenty, takie jak pliki programu Word lub prezentacje programu PowerPoint. Każda warstwa jest wyświetlana jako prostokąt na diagramie i pokazuje liczbę artefaktów, które są z nią połączone. Warstwa może zawierać zagnieżdżone warstwy, które opisują bardziej szczegółowe zadania.

 Ogólną wytyczną jest nazwa warstw, zgodnie z ich funkcją, na przykład "prezentacja" lub "usługi". Jeśli artefakty są blisko siebie zależne, umieść je w tej samej warstwie. Jeśli artefakty mogą być aktualizowane oddzielnie lub używane w oddzielnych aplikacjach, umieść je w różnych warstwach. Aby dowiedzieć się więcej o wzorcach warstwowych, odwiedź witrynę & Practices w temacie [http://go.microsoft.com/fwlink/?LinkId=145794](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home) .

> [!TIP]
> Istnieją pewne typy artefaktów, które można połączyć z warstwami, ale nie obsługują walidacji na diagramie warstwowym. Aby sprawdzić, czy artefakt obsługuje walidację, Otwórz **Eksploratora warstw** , aby sprawdzić Właściwość **obsługuje walidację** łącza artefaktu. Zobacz sekcję [odnajdywanie istniejących zależności między warstwami](#Generate).

 Podczas aktualizowania nieznanej aplikacji można również utworzyć mapy kodu. Te diagramy mogą pomóc w znalezieniu wzorców i zależności podczas eksplorowania kodu. Użyj Eksplorator rozwiązań, aby eksplorować przestrzenie nazw i klasy, które często są dobrze zgodne z istniejącymi warstwami. Przypisz te artefakty kodu do warstw, przeciągając je z Eksplorator rozwiązań do diagramów warstwowych. Następnie można użyć diagramów warstwowych, aby pomóc zaktualizować kod i zachować spójność z projektem.

 Zobacz:

- [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Odkryj istniejące zależności między warstwami
 Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Istniejące zależności można wykrywać przez odbudowane.

> [!NOTE]
> Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby sprawdzić, które artefakty mają zależności, które można odtworzyć, kliknij prawym przyciskiem myszy jedną lub wiele warstw, a następnie kliknij pozycję **Wyświetl linki**. W **Eksploratorze warstwy**zapoznaj się z kolumną **Obsługa walidacji** . Zależności nie będą odtwarzane w przypadku artefaktów, dla których ta kolumna pokazuje **wartość false**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Aby odtworzyć istniejące zależności między warstwami

- Wybierz jedną warstwę lub wiele warstw, kliknij prawym przyciskiem myszy wybraną warstwę, a następnie kliknij polecenie **Generuj zależności**.

  Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Edycja warstw i zależności w celu pokazania zamierzonego projektu
 Aby opisać zmiany, które planujesz wprowadzić do systemu lub zamierzonej architektury, wykonaj następujące kroki, aby edytować diagram warstwy. Można również rozważyć wprowadzenie zmian refaktoryzacji w celu poprawy struktury kodu przed jego rozszerzeniem. Zobacz [ulepszanie struktury kodu](#Improving).

|**Działanie**|**Wykonaj następujące kroki**|
|------------|-----------------------------|
|Usuń zależność, która nie powinna istnieć|Kliknij zależność, a następnie naciśnij klawisz **delete**.|
|Zmień lub ogranicz kierunek zależności|Ustaw jej właściwość **Direction** .|
|Tworzenie nowych zależności|Użyj **zależności** i **dwukierunkowych narzędzi zależności** .<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Gdy skończysz, kliknij narzędzie **wskaźnik** lub naciśnij klawisz **ESC** .|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw w właściwości **niedozwolone zależności przestrzeni nazw** . Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw w właściwości **zabronione przestrzenie nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw we właściwości **wymagane przestrzenie nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Ulepszanie struktury kodu
 Zmiany refaktoryzacji są ulepszeniami, które nie wpływają na zachowanie aplikacji, ale ułatwiają zmianę i zwiększenie ich w przyszłości. Kod dobrze skonstruowany ma projekt łatwy do abstrakcyjny dla diagramu warstwowego.

 Na przykład w przypadku utworzenia warstwy dla każdej przestrzeni nazw w kodzie, a następnie odtworzenia zależności między warstwami powinien istnieć minimalny zestaw współzależności jednokierunkowych między warstwy. Jeśli utworzysz bardziej szczegółowy diagram przy użyciu klas lub metod jako warstw, wynik powinien również mieć te same cechy.

 Jeśli tak się nie dzieje, kod będzie trudniejszy do zmiany w całym życiu i będzie mniej odpowiedni do walidacji przy użyciu diagramów warstwowych.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Projektuj nowe obszary aplikacji
 Po rozpoczęciu opracowywania nowego projektu lub nowego obszaru w nowym projekcie można rysować warstwy i zależności, aby pomóc w zidentyfikowaniu głównych składników przed rozpoczęciem opracowywania kodu.

- **Pokaż możliwe do zidentyfikowania wzorce architektury** na diagramach warstw, jeśli to możliwe. Na przykład diagram warstwowy opisujący aplikację klasyczną może obejmować takie warstwy jak prezentacja, Logika domeny i magazyn danych. Diagram warstwowy, który obejmuje pojedynczą funkcję w aplikacji, może mieć takie warstwy, jak model, widok i kontroler. Aby uzyskać więcej informacji na temat takich wzorców, zobacz [wzorce & praktyki: Architektura aplikacji](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home).

     Jeśli często tworzysz podobne wzorce, Utwórz niestandardowe narzędzie. Zobacz [Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md).

- **Utwórz artefakt kodu dla każdej warstwy** , takiej jak przestrzeń nazw, Klasa lub składnik. Dzięki temu można łatwiej stosować kod i łączyć artefakty kodu z warstwami. Zaraz po utworzeniu każdego artefaktu należy połączyć go z odpowiednią warstwą.

- **Nie ma potrzeby łączenia większości klas i innych artefaktów z warstwami** , ponieważ należą one do większych artefaktów, takich jak przestrzenie nazw, które zostały już połączone z warstwami.

- **Utwórz nowy diagram dla nowej funkcji**. Zwykle istnieje co najmniej jeden diagram warstwowy opisujący całą aplikację. Jeśli projektujesz nową funkcję w aplikacji, nie dodawaj ani nie zmieniaj istniejących diagramów. Zamiast tego należy utworzyć własny diagram, który odzwierciedla nowe części kodu. Warstwy na nowym diagramie mogą obejmować prezentację, logikę domeny i warstwy bazy danych dla nowej funkcji.

     Podczas kompilowania aplikacji kod zostanie zweryfikowany zarówno na ogólnym diagramie, jak i na bardziej szczegółowym diagramie funkcji.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Edytuj układ prezentacji i dyskusji
 Aby ułatwić identyfikację warstw i zależności lub omawianie ich członkom zespołu, Edytuj wygląd i układ diagramu w następujący sposób:

- Zmiana rozmiarów, kształtów i pozycji warstw.

- Zmień kolory warstw i zależności.

  - Wybierz co najmniej jedną warstwę lub zależności, kliknij prawym przyciskiem myszy, a następnie kliknij polecenie **Właściwości**. W oknie **Właściwości** Edytuj Właściwość **Color** .

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Sprawdzanie poprawności kodu względem diagramu
 Po edytowaniu diagramu można sprawdzić jego poprawność ręcznie w dowolnym momencie lub automatycznie za każdym razem, gdy uruchamiana jest lokalna kompilacja lub [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] .

 Zobacz:

- [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)

- [Uwzględnij walidację warstwy w procesie kompilacji](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Zaktualizuj kod, aby był zgodny z nową architekturą
 Zwykle błędy pojawią się podczas pierwszego sprawdzania poprawności kodu na zaktualizowanym diagramie warstwowym. Te błędy mogą mieć kilka przyczyn:

- Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

- Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

  Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Jest to zazwyczaj proces iteracyjny. Aby uzyskać więcej informacji o tych błędach, zobacz [Weryfikowanie kodu przy użyciu diagramów warstwowych](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Podczas opracowywania lub refaktoryzacji kodu, możesz mieć nowe artefakty do łączenia się z diagramem warstwowym. Jednak może to nie być konieczne, na przykład w przypadku warstw, które reprezentują istniejące przestrzenie nazw, a nowy kod dodaje więcej materiału do tych przestrzeni nazw.

 Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. W przypadku pominięcia błędu dobrym sposobem jest zarejestrowanie elementu pracy w [!INCLUDE[esprfound](../includes/esprfound-md.md)] . Aby wykonać to zadanie, zobacz [Walidacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md).

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Uwzględnij walidację warstwy w procesie kompilacji
 Aby zapewnić, że przyszłe zmiany w kodzie są zgodne z diagramami warstw, należy uwzględnić walidację warstwy w standardowym procesie kompilacji rozwiązania. Za każdym razem, gdy inny członek zespołu kompiluje rozwiązanie, wszelkie różnice między zależnościami w kodzie a diagramem warstwowym będą raportowane jako błędy kompilacji. Aby uzyskać więcej informacji na temat sprawdzania poprawności warstwy w procesie kompilacji, zobacz [Sprawdzanie poprawności kodu przy użyciu diagramów warstwowych](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Zobacz też
 [Diagramy warstw: dokumentacja](../modeling/layer-diagrams-reference.md) [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)
