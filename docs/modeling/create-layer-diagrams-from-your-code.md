---
title: Tworzenie diagramów zależności z kodu
ms.date: 11/04/2016
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
ms.openlocfilehash: b9822dda92a096e3c497d468865d3ed9fd56e16d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421189"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Tworzenie diagramów zależności z kodu

Aby zwizualizować systemu oprogramowania logiczną architekturę wysokiego, Utwórz *diagram zależności* w programie Visual Studio. Aby upewnić się, że kod pozostaje zgodny z tym projektem, Przeprowadź walidację kodu z diagramów zależności. Możesz tworzyć diagramy zależności dla projektów języka Visual C# i Visual Basic. Aby zobaczyć, jakie wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługę wersji narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools).

![Tworzenie diagramów zależności](../modeling/media/layerdiagramvisualizecode.png)

Diagram zależności pozwala organizować elementy rozwiązania Visual Studio w logiczne, abstrakcyjne grupy o nazwie *warstwy*. Można użyć warstw do opisania głównych zadań wykonywanych przez te artefakty lub główne składniki systemu. Każda warstwa może zawierać innych warstwy opisujące bardziej szczegółowe zadania. Można również określić zamierzone lub istniejące *zależności* między warstwami. Te zależności, które są reprezentowane jako strzałki, wskazują, które warstwy mogą używać lub obecnie używają funkcje reprezentowane przez inne warstwy. Aby utrzymać kontrolę architektury kodu, wyświetl zamierzone zależności na diagramie i przeprowadź walidację kodu na podstawie diagramu.

[Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="CreateDiagram"></a> Tworzenie diagramów zależności

Przed utworzeniem diagram zależności, upewnij się, że rozwiązanie ma projektu modelowania.

> [!IMPORTANT]
> Nie Dodawanie, przeciągnij lub skopiuj istniejący diagram zależności z projektu modelowania do innego projektu modelowania lub w inne miejsce w rozwiązaniu. Pozwala to zachować odniesienia z oryginalnego diagramu nawet po zmianie diagramu. Mogłoby to także uniemożliwić prawidłowe działanie walidacji warstwy i spowodować wystąpienie innych problemów, takich jak brakujące elementy lub inne błędy, przy próbie otwarcia diagramu.
>
> Zamiast tego Dodaj nowy diagram zależności do projektu modelowania. Skopiuj elementy z diagramu źródłowego do nowego diagramu. Zapisz zarówno projekt modelowania, jak i nowy diagram zależności.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Dodaj nowy diagram zależności do projektu modelowania

> [!NOTE]
> Diagramy zależności nie są obsługiwane dla projektów .NET Core w programie Visual Studio.

1. Na **architektury** menu, wybierz **nowy Diagram zależności**.

2. W obszarze **szablony**, wybierz **diagram zależności**.

3. Nadaj nazwę diagramowi.

4. W **Dodaj do projektu modelowania**, wyszukaj i wybierz istniejący projekt modelowania w rozwiązaniu.

     —lub—

     Wybierz **Utwórz nowy projekt modelowania** Aby dodać nowy projekt modelowania w rozwiązaniu.

    > [!NOTE]
    > Diagram zależności musi istnieć w projekcie modelowania. Możesz jednak połączyć elementy w innym miejscu rozwiązania.

5. Upewnij się zapisać zarówno projekt modelowania i diagram zależności.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Przeciągnij i upuść, lub skopiuj i Wklej, z mapy kodu

1. Generuj mapę kodu dla rozwiązania za pomocą **architektury** menu.

2. Należy rozważyć stosowanie filtru mapy kodu, aby usunąć foldery rozwiązania i "Test zasoby", jeśli chcesz wymusić zależności w kodzie produktu.

3. Na mapie kodu wygenerowanego Usuń węzeł "External", lub rozwinąć, aby wyświetlić zestawy zewnętrzne w zależności od tego, czy chcesz wymusić zależności przestrzeni nazw i Usuń-wymagane zestawy z mapy kodu.

4. Utwórz nowy Diagram zależności za pomocą rozwiązania **architektury** menu

5. Zaznacz wszystkie węzły na mapie kodu (Użyj _Ctrl_ + _A_, lub Użyj zaznaczenia gumki, naciskając klawisz _Shift_ klucza przed kliknij przycisk, przeciągnij i wersji.

6. Przeciągnij i upuść lub kopiowania i wklejania, wybrane elementy do nowego diagramu weryfikacji zależności.

7. Wskazuje bieżący architektury aplikacji. Zdecydować, co architektura za oraz odpowiednio zmodyfikować diagram zależności.

![Diagram zależności wygenerowany na podstawie mapy kodu](media/dependency-validation-01.png)

## <a name="CreateLayers"></a> Tworzenie warstw z artefaktów
 Warstwy możesz tworzyć z elementów rozwiązania Visual Studio, takich jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Powoduje to automatyczne tworzenie łączy między warstwami i elementami, uwzględniając je w procesie walidacji warstwy.

 Możesz również połączyć warstwy z elementami, które nie obsługują walidacji, takimi jak dokumenty programu Word lub prezentacji programu PowerPoint, tak aby można było skojarzyć warstwy ze specyfikacjami lub planami. Możesz również połączyć warstwy z plikami projektów współużytkowanymi przez wiele aplikacji, ale proces walidacji nie uwzględni warstw wyświetlanych z nazwami rodzajowymi, takimi jak „Warstwa 1” i „Warstwa 2”.

 Aby sprawdzić, czy połączony element obsługuje walidację, otwórz **Eksplorator warstw** i zbadaj **obsługuje walidację** właściwości elementu. Zobacz [Zarządzanie łączami do artefaktów](#Managing).

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Utworzyć warstwę dla pojedynczego artefakt|<ol><li>Przeciągnij element na diagram zależności z tych źródeł:<br /><br /> <ul><li>**Eksplorator rozwiązań**<br /><br />         Możesz na przykład przeciągać pliki lub projekty.</li><li>Mapy kodu<br /><br />         Zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) i [mapy Użyj kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Widok klas** lub **przeglądarka obiektów**</li></ul><br />     Warstwy jest wyświetlana na diagramie i jest połączona z artefaktem.</li><li>Zmień nazwę warstwy, aby odzwierciedlała obowiązki skojarzonego kodu lub artefaktów.</li></ol> **Ważne:**  Przeciąganie plików binarnych do diagramu zależności nie powoduje automatycznego dodania odniesień do nich do projektu modelowania. Musisz ręcznie dodać do projektu modelowania pliki binarne, które chcesz walidować. **Aby dodać pliki binarne do projektu modelowania** <ol><li>W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu modelowania, a następnie wybierz **Dodaj istniejący element**.</li><li>W **Dodaj istniejący element** okno dialogowe, przejdź do plików binarnych, zaznacz je, a następnie wybierz **OK**.     Pliki binarne pojawią się w projekcie modelowania.</li><li>W **Eksploratora rozwiązań**, wybierz plik binarny, który zostanie dodany, a następnie naciśnij **F4** otworzyć **właściwości** okna.</li><li>Dla każdego pliku binarnego ustaw **Build Action** właściwości **weryfikacji**.</li></ol>|
|Utwórz jedną warstwę dla wszystkich zaznaczonych artefaktów|Przeciągnij wszystkie artefakty do diagramu zależności, w tym samym czasie.<br /><br /> Warstw pojawi się na diagramie i będzie połączona z artefaktami.|
|Tworzenie warstwy dla każdego zaznaczonego artefaktu|Naciśnij i przytrzymaj klawisz **SHIFT** klucza podczas przeciągania wszystkich artefaktów na diagram zależności w tym samym czasie. **Uwaga:**  Jeśli używasz **SHIFT** klawisz, aby wybrać zakres elementów, zwolnij klawisz po zaznaczeniu artefaktów. Naciśnij i przytrzymaj go ponownie podczas przeciągania artefaktów do diagramu. <br /><br /> Warstwa dla każdego artefaktu pojawia się na diagramie i jest połączona z poszczególnymi artefaktami.|
|Dodawanie artefaktu do warstwy|Przeciągnij artefakt do warstwy.|
|Tworzenie nowej niepołączonej warstwy|W **przybornika**, rozwiń węzeł **Diagram zależności** sekcji, a następnie przeciągnij **warstwy** diagram zależności.<br /><br /> Aby dodać wiele warstw, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz pozycję **wskaźnik** narzędzi lub naciśnij klawisz **ESC** klucza.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów dla diagramu zależność, wybierz polecenie **Dodaj**, a następnie wybierz **warstwy**.|
|Tworzenie zagnieżdżonych warstw|Przeciągnij istniejącą warstwę na inną warstwę.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów dla warstwy, wybierz polecenie **Dodaj**, a następnie wybierz **warstwy**.|
|Tworzenie nowej warstwy zawierającej dwie lub więcej istniejących warstw|Zaznacz warstwy, otwórz menu skrótów dla zaznaczenia, a następnie wybierz **grupy**.|
|Zmienianie koloru warstwy|Ustaw jego **kolor** właściwość kolor, który chcesz.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw w warstwie **zabronione przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw w warstwie **zabronione zależności Namespace** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw w warstwie **wymagane przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|

 Liczba na warstwie oznacza liczbę artefaktów, które są połączone z warstwą. Jednak odczytując tę liczbę, należy pamiętać, że:

- Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

- Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

## <a name="Managing"></a> Zarządzanie połączeniami między warstwami i artefaktami

1. Na diagramie zależności, otwórz menu skrótów dla warstwy, a następnie wybierz **Wyświetl łącza**.

     **Eksplorator warstw** Wyświetla łącza artefaktów dla zaznaczonej warstwy.

2. Wykonaj następujące zadania, aby zarządzać tymi łączami:

|**To**|**W Eksploratorze warstw**|
|-|-|
|Usuwanie łącza między warstwą i artefaktem|Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz **Usuń**.|
|Przenoszenie łącza z jednej warstwy na drugą|Przeciągnij łącze artefaktu do istniejącej warstwy na diagramie.<br /><br /> - lub -<br /><br /> 1.  Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz **Wytnij**.<br />2.  Na diagramie zależności, otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|
|Kopiowanie łącza z jednej warstwy na drugą|1.  Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz **kopiowania**.<br />2.  Na diagramie zależności, otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|
|Tworzenie nowej warstwy z istniejącego łącza artefaktu|Przeciągnij łącze artefaktu do pustego obszaru na diagramie.|
|Sprawdź, czy połączony artefakt obsługuje walidację na podstawie diagram zależności.|Przyjrzyj się **obsługuje walidację** kolumny dla łącza artefaktu.|

## <a name="Discovering"></a> Odtwarzanie istniejących zależności
 Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Możesz odtwarzać istniejące zależności dla artefaktów, które są połączone z warstwami na diagramie.

> [!NOTE]
> Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby zobaczyć, które artefakty mają zależności można odtworzyć, otwórz menu skrótów dla jednej lub wielu warstw, a następnie wybierz **Wyświetl łącza**. W **Eksplorator warstw**, sprawdź **obsługuje walidację** kolumny. Zależności nie będą odtwarzane dla artefaktów, dla których ta kolumna zawiera **False**.

- Zaznacz jedną lub wiele warstw, otwórz menu skrótów dla zaznaczonej warstwy, a następnie wybierz **Wygeneruj zależności**.

  Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.

## <a name="EditDependencies"></a> Edytowanie warstw i zależności w celu przedstawienia zamierzonego projektu
 Aby opisać zmiany, które planujesz wprowadzić do systemu lub zamierzonej architektury, należy edytować diagram zależności:

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Zmień lub ogranicz kierunek zależności|Ustaw jego **kierunek** właściwości.|
|Tworzenie nowych zależności|Użyj **zależności** i **zależność dwukierunkowa** narzędzia.<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz pozycję **wskaźnik** narzędzi lub naciśnij klawisz **ESC** klucza.|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw w warstwie **zabronione zależności Namespace** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw w warstwie **zabronione przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw w warstwie **wymagane przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|

## <a name="EditLayout"></a> Zmienianie sposobu wyświetlania elementów na diagramie
 Możesz zmieniać rozmiar, kształt, kolor i położenie warstw lub kolor zależności, edytując ich właściwości.

## <a name="Codemaps"></a> Odnajdowanie wzorców i zależności na mapie kodu
 Podczas tworzenia diagramów zależności, można również tworzyć **map kodu**. Te diagramy ułatwia odnajdowanie wzorców i zależności, chociaż możesz zapoznać się z kodu. Użyj Eksploratora rozwiązań, widoku klas lub przeglądarki obiektów, aby zapoznać się z zestawów, przestrzeni nazw i klas — które często dobrze odpowiadają istniejącym warstwom. Aby uzyskać więcej informacji na temat map kodu zobacz:

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Zobacz też

- [Obsługa wersji narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Diagramy zależności: informacje](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)
- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
