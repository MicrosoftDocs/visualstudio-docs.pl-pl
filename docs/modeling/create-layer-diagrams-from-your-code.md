---
title: Tworzenie diagramów zależności z kodu
description: Dowiedz się, jak utworzyć diagram zależności w Visual Studio w celu wizualizacji architektury logicznej wysokiego poziomu systemu oprogramowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: b07af93386d5062f28f19f01ce150fba8ec45dd2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389660"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Tworzenie diagramów zależności z kodu

Aby zwizualizować architekturę logiczną wysokiego poziomu systemu oprogramowania, utwórz *diagram zależności w* Visual Studio. Aby upewnić się, że kod pozostaje zgodny z tym projektem, zweryfikuj kod za pomocą diagramu zależności. Można tworzyć diagramy zależności dla programu Visual C# i Visual Basic projektów. Aby sprawdzić, które wersje usługi Visual Studio obsługują tę funkcję, zobacz Obsługa wersji dla [architektury i narzędzi do modelowania.](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)

![Tworzenie diagramu zależności](../modeling/media/layerdiagramvisualizecode.png)

Diagram zależności umożliwia organizowanie elementów Visual Studio w logiczne, abstrakcyjne grupy nazywane *warstwami*. Można użyć warstw do opisania głównych zadań wykonywanych przez te artefakty lub główne składniki systemu. Każda warstwa może zawierać innych warstwy opisujące bardziej szczegółowe zadania. Można również określić zamierzone lub istniejące *zależności między* warstwami. Te zależności, które są reprezentowane jako strzałki, wskazują, które warstwy mogą używać lub obecnie używają funkcje reprezentowane przez inne warstwy. Aby utrzymać kontrolę architektury kodu, wyświetl zamierzone zależności na diagramie i przeprowadź walidację kodu na podstawie diagramu.

[Wideo: Weryfikowanie zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="create-a-dependency-diagram"></a><a name="CreateDiagram"></a> Tworzenie diagramu zależności

Przed utworzeniem diagramu zależności upewnij się, że rozwiązanie ma projekt modelowania.

> [!IMPORTANT]
> Nie dodawaj, nie przeciągaj ani nie kopiuj istniejącego diagramu zależności z projektu modelowania do innego projektu modelowania ani do innego miejsca w rozwiązaniu. Pozwala to zachować odniesienia z oryginalnego diagramu nawet po zmianie diagramu. Mogłoby to także uniemożliwić prawidłowe działanie walidacji warstwy i spowodować wystąpienie innych problemów, takich jak brakujące elementy lub inne błędy, przy próbie otwarcia diagramu.
>
> Zamiast tego dodaj nowy diagram zależności do projektu modelowania. Skopiuj elementy z diagramu źródłowego do nowego diagramu. Zapisz zarówno projekt modelowania, jak i nowy diagram zależności.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Dodawanie nowego diagramu zależności do projektu modelowania

> [!NOTE]
> Diagramy zależności dla projektów .NET Core są obsługiwane od Visual Studio 2019 w wersji 16.2.

1. W menu **Architektura** wybierz pozycję **Nowy diagram zależności.**

2. W **obszarze Szablony** wybierz diagram **zależności**.

3. Nadaj nazwę diagramowi.

4. Na **stronie Dodawanie do projektu modelowania** przejdź do istniejącego projektu modelowania w rozwiązaniu i wybierz go.

     -lub-

     Wybierz **pozycję Utwórz nowy projekt modelowania,** aby dodać nowy projekt modelowania do rozwiązania.

    > [!NOTE]
    > Diagram zależności musi istnieć wewnątrz projektu modelowania. Możesz jednak połączyć elementy w innym miejscu rozwiązania.

5. Pamiętaj, aby zapisać zarówno projekt modelowania, jak i diagram zależności.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Przeciąganie i upuszczanie lub kopiowanie i wklejanie z mapy kodu

1. Wygeneruj mapę kodu dla rozwiązania przy użyciu menu **Architektura.**

2. Rozważ zastosowanie filtru mapy kodu w celu usunięcia folderów rozwiązań i elementów "Zasoby testowe", jeśli chcesz wymusić tylko zależności w kodzie produktu.

3. Na wygenerowanej mapie kodu usuń węzeł "Zewnętrzny" lub rozwiń go, aby wyświetlić zestawy zewnętrzne, w zależności od tego, czy chcesz wymusić zależności przestrzeni nazw, i usuń nie wymagane zestawy z mapy kodu.

4. Tworzenie nowego diagramu zależności dla rozwiązania przy użyciu menu **Architektura**

5. Zaznacz wszystkie węzły na mapie kodu (użyj _klawisza Ctrl_ A lub użyj zaznaczenia gumki, naciskając klawisz Shift przed kliknięciem, przeciągnięciem  +  i  zwolnieniem.

6. Przeciągnij i upuść lub skopiuj i wklej wybrane elementy do nowego diagramu weryfikacji zależności.

7. Przedstawia bieżącą architekturę aplikacji. Zdecyduj, jaka ma być architektura, i odpowiednio zmodyfikuj diagram zależności.

![Diagram zależności wygenerowany na podstawie mapy kodu](media/dependency-validation-01.png)

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a> Tworzenie warstw z artefaktów
 Warstwy możesz tworzyć z elementów rozwiązania Visual Studio, takich jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Powoduje to automatyczne tworzenie łączy między warstwami i elementami, uwzględniając je w procesie walidacji warstwy.

 Możesz również połączyć warstwy z elementami, które nie obsługują walidacji, takimi jak dokumenty programu Word lub prezentacji programu PowerPoint, tak aby można było skojarzyć warstwy ze specyfikacjami lub planami. Możesz również połączyć warstwy z plikami projektów współużytkowanymi przez wiele aplikacji, ale proces walidacji nie uwzględni warstw wyświetlanych z nazwami rodzajowymi, takimi jak „Warstwa 1” i „Warstwa 2”.

 Aby sprawdzić, czy połączony element obsługuje walidację, otwórz **Eksploratora warstw** i sprawdź właściwość **Obsługuje** walidację elementu. Zobacz [Managing links to artifacts (Zarządzanie linkami do artefaktów).](#Managing)

|**Do**|**Wykonaj te kroki**|
|-|-|
|Utworzyć warstwę dla pojedynczego artefakt|<ol><li>Przeciągnij element na diagram zależności z tych źródeł:<br /><br /> <ul><li>**Eksplorator rozwiązań**<br /><br />         Możesz na przykład przeciągać pliki lub projekty.</li><li>Mapy kodu<br /><br />         Zobacz [Mapowanie zależności między rozwiązaniami i](../modeling/map-dependencies-across-your-solutions.md) [Używanie map kodu do debugowania aplikacji.](../modeling/use-code-maps-to-debug-your-applications.md)</li><li>**Widok klasy** lub **przeglądarka obiektów**</li></ul><br />     Warstwy jest wyświetlana na diagramie i jest połączona z artefaktem.</li><li>Zmień nazwę warstwy, aby odzwierciedlała obowiązki skojarzonego kodu lub artefaktów.</li></ol> **Ważne:**  Przeciągnięcie plików binarnych do diagramu zależności nie powoduje automatycznego dodania ich odwołań do projektu modelowania. Musisz ręcznie dodać do projektu modelowania pliki binarne, które chcesz walidować. **Aby dodać pliki binarne do projektu modelowania** <ol><li>W **Eksplorator rozwiązań** otwórz menu skrótów projektu modelowania, a następnie wybierz pozycję **Dodaj istniejący element**.</li><li>W **oknie dialogowym Dodawanie** istniejącego elementu przejdź do plików binarnych, wybierz je, a następnie wybierz przycisk **OK.**     Pliki binarne pojawią się w projekcie modelowania.</li><li>W **Eksplorator rozwiązań** wybierz dodany plik binarny, a następnie naciśnij **klawisz F4,** aby otworzyć **okno** Właściwości.</li><li>Dla każdego pliku binarnego ustaw właściwość **Akcja kompilacji** na wartość **Weryfikuj**.</li></ol>|
|Utwórz jedną warstwę dla wszystkich zaznaczonych artefaktów|Przeciągnij wszystkie artefakty do diagramu zależności w tym samym czasie.<br /><br /> Warstw pojawi się na diagramie i będzie połączona z artefaktami.|
|Tworzenie warstwy dla każdego zaznaczonego artefaktu|Naciśnij i przytrzymaj klawisz **SHIFT** podczas przeciągania wszystkich artefaktów do diagramu zależności w tym samym czasie. **Uwaga:**  Jeśli wybierasz zakres elementów za pomocą klawisza **SHIFT,** zwolnij klucz po wybraniu artefaktów. Naciśnij i przytrzymaj go ponownie podczas przeciągania artefaktów do diagramu. <br /><br /> Warstwa dla każdego artefaktu pojawia się na diagramie i jest połączona z poszczególnymi artefaktami.|
|Dodawanie artefaktu do warstwy|Przeciągnij artefakt do warstwy.|
|Tworzenie nowej niepołączonej warstwy|W **przyborniku** rozwiń **sekcję Diagram zależności,** a następnie przeciągnij **warstwę** do diagramu zależności.<br /><br /> Aby dodać wiele warstw, kliknij dwukrotnie narzędzie. Po zakończeniu wybierz narzędzie **Wskaźnik** lub naciśnij klawisz **ESC.**<br /><br /> — lub —<br /><br /> Otwórz menu skrótów diagramu zależności, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Warstwa**.|
|Tworzenie zagnieżdżonych warstw|Przeciągnij istniejącą warstwę na inną warstwę.<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla warstwy, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Warstwa**.|
|Tworzenie nowej warstwy zawierającej dwie lub więcej istniejących warstw|Wybierz warstwy, otwórz menu skrótów dla wybranego elementu, a następnie wybierz pozycję **Grupuj.**|
|Zmienianie koloru warstwy|Ustaw jego **właściwość Color** na kolor, którego potrzebujesz.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw we właściwości **Zabronione przestrzenie nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw we właściwości Zależności niedozwolonej **przestrzeni nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw we właściwości **Wymagane przestrzenie nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|

 Liczba na warstwie oznacza liczbę artefaktów, które są połączone z warstwą. Jednak odczytując tę liczbę, należy pamiętać, że:

- Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

- Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

## <a name="manage-links-between-layers-and-artifacts"></a><a name="Managing"></a> Zarządzanie połączeniami między warstwami i artefaktami

1. Na diagramie zależności otwórz menu skrótów dla warstwy, a następnie wybierz pozycję **Wyświetl linki**.

     **Eksplorator warstw** pokazuje linki artefaktów dla wybranej warstwy.

2. Wykonaj następujące zadania, aby zarządzać tymi łączami:

|**Do**|**W Eksploratorze warstw**|
|-|-|
|Usuwanie łącza między warstwą i artefaktem|Otwórz menu skrótów linku artefaktu, a następnie wybierz pozycję **Usuń**.|
|Przenoszenie łącza z jednej warstwy na drugą|Przeciągnij łącze artefaktu do istniejącej warstwy na diagramie.<br /><br /> — lub —<br /><br /> 1. Otwórz menu skrótów linku artefaktu, a następnie wybierz pozycję **Wytnij**.<br />2. Na diagramie zależności otwórz menu skrótów dla warstwy, a następnie wybierz pozycję **Wklej**.|
|Kopiowanie łącza z jednej warstwy na drugą|1. Otwórz menu skrótów linku artefaktu, a następnie wybierz pozycję **Kopiuj**.<br />2. Na diagramie zależności otwórz menu skrótów dla warstwy, a następnie wybierz pozycję **Wklej**.|
|Tworzenie nowej warstwy z istniejącego łącza artefaktu|Przeciągnij łącze artefaktu do pustego obszaru na diagramie.|
|Sprawdź, czy połączony artefakt obsługuje walidację względem diagramu zależności.|Poszukaj linku **artefaktu w** kolumnie Obsługuje walidację.|

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a> Istniejące zależności inżyniera odwrotnego
 Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Możesz odtwarzać istniejące zależności dla artefaktów, które są połączone z warstwami na diagramie.

> [!NOTE]
> Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby zobaczyć, które artefakty mają zależności, które można odwrócić, otwórz menu skrótów dla jednej lub wielu warstw, a następnie wybierz **pozycję Wyświetl linki.** W **Eksploratorze warstw** sprawdź **kolumnę Obsługuje walidację.** Zależności nie zostaną odtąd zaprojektowane dla artefaktów, dla których ta kolumna zawiera wartość **False**.

- Wybierz jedną lub wiele warstw, otwórz menu skrótów dla wybranej warstwy, a następnie wybierz pozycję **Generuj zależności.**

  Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a> Edytowanie warstw i zależności w celu pokazania zamierzonego projektu
 Aby opisać zmiany, które planujesz wprowadzić w systemie lub zamierzonej architekturze, edytuj diagram zależności:

|**Do**|**Wykonaj następujące kroki**|
|-|-|
|Zmień lub ogranicz kierunek zależności|Ustaw jego **właściwość Direction.**|
|Tworzenie nowych zależności|Użyj narzędzi **Zależności i** **Zależność dwukierunkowa.**<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Po zakończeniu wybierz narzędzie **Wskaźnik** lub naciśnij klawisz **ESC.**|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw we właściwości Zabronione zależności **przestrzeni nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw we właściwości **Zabronione przestrzenie nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw we właściwości **Wymagane przestrzenie nazw** warstwy. Użyj średnika (**;**), aby oddzielić przestrzenie nazw.|

## <a name="change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a> Zmienianie sposobu, w jaki elementy są wyświetlane na diagramie
 Możesz zmieniać rozmiar, kształt, kolor i położenie warstw lub kolor zależności, edytując ich właściwości.

## <a name="discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a> Odnajdywanie wzorców i zależności na mapie kodu
 Podczas tworzenia diagramów zależności można również utworzyć **mapy kodu**. Te diagramy mogą ułatwić odnajdywanie wzorców i zależności podczas eksplorowania kodu. Użyj Eksplorator rozwiązań, Widok klasy lub przeglądarki obiektów, aby eksplorować zestawy, przestrzenie nazw i klasy — które często dobrze odpowiadają istniejącym warstwom. Aby uzyskać więcej informacji na temat map kodu, zobacz:

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Zobacz też

- [Obsługa wersji dla architektury i narzędzi do modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [Wideo: Weryfikowanie zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)
- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
