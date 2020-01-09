---
title: Tworzenie diagramów zależności z kodu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51e33d5f9b20230b056c017c9067bb4b2acafce6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597194"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Tworzenie diagramów zależności z kodu

Aby wizualizować architekturę logiczną wysokiego poziomu systemu oprogramowania, Utwórz *Diagram zależności* w programie Visual Studio. Aby upewnić się, że kod pozostaje spójny z tym projektem, zweryfikuj swój kod przy użyciu diagramu zależności. Można tworzyć diagramy zależności dla projektów C# wizualizacji i Visual Basic. Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools).

![Tworzenie diagramu zależności](../modeling/media/layerdiagramvisualizecode.png)

Diagram zależności umożliwia organizowanie elementów rozwiązania programu Visual Studio w logiczne, abstrakcyjne grupy o nazwie *warstwy*. Można użyć warstw do opisania głównych zadań wykonywanych przez te artefakty lub główne składniki systemu. Każda warstwa może zawierać innych warstwy opisujące bardziej szczegółowe zadania. Można również określić zamierzone lub istniejące *zależności* między warstwami. Te zależności, które są reprezentowane jako strzałki, wskazują, które warstwy mogą używać lub obecnie używają funkcje reprezentowane przez inne warstwy. Aby utrzymać kontrolę architektury kodu, wyświetl zamierzone zależności na diagramie i przeprowadź walidację kodu na podstawie diagramu.

[Wideo: Weryfikuj zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="CreateDiagram"></a>Tworzenie diagramu zależności

Przed utworzeniem diagramu zależności upewnij się, że rozwiązanie ma projekt modelowania.

> [!IMPORTANT]
> Nie dodawaj, nie przeciągaj ani nie Kopiuj istniejącego diagramu zależności z projektu modelowania do innego projektu modelowania lub w innym miejscu w rozwiązaniu. Pozwala to zachować odniesienia z oryginalnego diagramu nawet po zmianie diagramu. Mogłoby to także uniemożliwić prawidłowe działanie walidacji warstwy i spowodować wystąpienie innych problemów, takich jak brakujące elementy lub inne błędy, przy próbie otwarcia diagramu.
>
> Zamiast tego Dodaj nowy diagram zależności do projektu modelowania. Skopiuj elementy z diagramu źródłowego do nowego diagramu. Zapisz projekt modelowania i nowy diagram zależności.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Dodawanie nowego diagramu zależności do projektu modelowania

> [!NOTE]
> Diagramy zależności dla projektów .NET Core są obsługiwane począwszy od programu Visual Studio 2019 w wersji 16,2.

1. W menu **Architektura** wybierz polecenie **Nowy diagram zależności**.

2. W obszarze **Szablony**wybierz pozycję **Diagram zależności**.

3. Nadaj nazwę diagramowi.

4. W obszarze **Dodaj do projektu modelowania**przejdź do i wybierz istniejący projekt modelowania w rozwiązaniu.

     lub

     Wybierz pozycję **Utwórz nowy projekt modelowania** , aby dodać nowy projekt modelowania do rozwiązania.

    > [!NOTE]
    > Diagram zależności musi znajdować się w projekcie modelowania. Możesz jednak połączyć elementy w innym miejscu rozwiązania.

5. Upewnij się, że zapisywany jest projekt modelowania i diagram zależności.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Przeciąganie i upuszczanie, kopiowanie i wklejanie z mapy kodu

1. Wygeneruj mapę kodu dla rozwiązania przy użyciu menu **Architektura** .

2. Rozważ zastosowanie filtru mapy kodu w celu usunięcia folderów rozwiązań i "testów zasobów", jeśli chcesz tylko wymusić zależności w kodzie produktu.

3. Na wygenerowanej mapie kodu Usuń węzeł "zewnętrzny" lub rozwiń go, aby wyświetlić zestawy zewnętrzne, w zależności od tego, czy chcesz wymusić zależności przestrzeni nazw, i Usuń niewymagane zestawy z mapy kodu.

4. Utwórz nowy diagram zależności dla rozwiązania przy użyciu menu **Architektura**

5. Zaznacz wszystkie węzły na mapie kodu (Użyj _klawisza Ctrl_ + _A_lub Skorzystaj z opcji wyboru przedziału, naciskając klawisz _SHIFT_ przed kliknięciem, przeciągnięciem i wydaniem.

6. Przeciągnij i upuść, lub skopiuj i wklej wybrane elementy do nowego diagramu walidacji zależności.

7. Zostanie wyświetlona bieżąca architektura aplikacji. Zdecyduj, co ma być architektura, i odpowiednio zmodyfikuj diagram zależności.

![Diagram zależności wygenerowany na podstawie mapy kodu](media/dependency-validation-01.png)

## <a name="CreateLayers"></a>Tworzenie warstw na podstawie artefaktów
 Warstwy możesz tworzyć z elementów rozwiązania Visual Studio, takich jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Powoduje to automatyczne tworzenie łączy między warstwami i elementami, uwzględniając je w procesie walidacji warstwy.

 Możesz również połączyć warstwy z elementami, które nie obsługują walidacji, takimi jak dokumenty programu Word lub prezentacji programu PowerPoint, tak aby można było skojarzyć warstwy ze specyfikacjami lub planami. Możesz również połączyć warstwy z plikami projektów współużytkowanymi przez wiele aplikacji, ale proces walidacji nie uwzględni warstw wyświetlanych z nazwami rodzajowymi, takimi jak „Warstwa 1” i „Warstwa 2”.

 Aby sprawdzić, czy połączony element obsługuje walidację, Otwórz **Eksploratora warstw** i sprawdź Właściwość **obsługuje walidację** elementu. Zobacz [Zarządzanie łączami do artefaktów](#Managing).

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Utworzyć warstwę dla pojedynczego artefakt|<ol><li>Przeciągnij element na diagram zależności z następujących źródeł:<br /><br /> <ul><li>**Eksplorator rozwiązań**<br /><br />         Możesz na przykład przeciągać pliki lub projekty.</li><li>Mapy kodu<br /><br />         Zapoznaj się z [zależnościami mapy w swoich rozwiązaniach](../modeling/map-dependencies-across-your-solutions.md) i [korzystaj z map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Widok klasy** lub **Przeglądarka obiektów**</li></ul><br />     Warstwy jest wyświetlana na diagramie i jest połączona z artefaktem.</li><li>Zmień nazwę warstwy, aby odzwierciedlała obowiązki skojarzonego kodu lub artefaktów.</li></ol> **Ważne:**  Przeciąganie plików binarnych do diagramu zależności nie powoduje automatycznego dodania odwołań do projektu modelowania. Musisz ręcznie dodać do projektu modelowania pliki binarne, które chcesz walidować. **Aby dodać pliki binarne do projektu modelowania** <ol><li>W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu modelowania, a następnie wybierz **Dodaj istniejący element**.</li><li>W oknie dialogowym **Dodaj istniejący element** przejdź do plików binarnych, zaznacz je, a następnie wybierz **przycisk OK**.     Pliki binarne pojawią się w projekcie modelowania.</li><li>W **Eksplorator rozwiązań**wybierz plik binarny, który został dodany, a następnie naciśnij klawisz **F4** , aby otworzyć okno **Właściwości** .</li><li>Dla każdego pliku binarnego ustaw właściwość **Akcja kompilacji** na **Sprawdź poprawność**.</li></ol>|
|Utwórz jedną warstwę dla wszystkich zaznaczonych artefaktów|Przeciągnij wszystkie artefakty do diagramu zależności w tym samym czasie.<br /><br /> Warstw pojawi się na diagramie i będzie połączona z artefaktami.|
|Tworzenie warstwy dla każdego zaznaczonego artefaktu|Naciśnij i przytrzymaj klawisz **SHIFT** podczas przeciągania wszystkich artefaktów do diagramu zależności w tym samym czasie. **Uwaga:**  Jeśli używasz klawisza **SHIFT** , aby wybrać zakres elementów, po wybraniu artefaktów zwolnij klawisz. Naciśnij i przytrzymaj go ponownie podczas przeciągania artefaktów do diagramu. <br /><br /> Warstwa dla każdego artefaktu pojawia się na diagramie i jest połączona z poszczególnymi artefaktami.|
|Dodawanie artefaktu do warstwy|Przeciągnij artefakt do warstwy.|
|Tworzenie nowej niepołączonej warstwy|W **przyborniku**rozwiń sekcję **Diagram zależności** , a następnie przeciągnij **warstwę** do diagramu zależności.<br /><br /> Aby dodać wiele warstw, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz narzędzie **wskaźnik** lub naciśnij klawisz **ESC** .<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla diagramu zależności, wybierz polecenie **Dodaj**, a następnie wybierz **warstwa**.|
|Tworzenie zagnieżdżonych warstw|Przeciągnij istniejącą warstwę na inną warstwę.<br /><br /> — lub —<br /><br /> Otwórz menu skrótów dla warstwy, wybierz polecenie **Dodaj**, a następnie wybierz **warstwa**.|
|Tworzenie nowej warstwy zawierającej dwie lub więcej istniejących warstw|Zaznacz warstwy, otwórz menu skrótów dla zaznaczenia, a następnie wybierz **grupę**.|
|Zmienianie koloru warstwy|Ustaw jej właściwość **Color** na odpowiedni kolor.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw w właściwości **zabronione przestrzenie nazw** warstwy. Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw w właściwości **niedozwolone zależności przestrzeni nazw** . Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw we właściwości **wymagane przestrzenie nazw** warstwy. Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|

 Liczba na warstwie oznacza liczbę artefaktów, które są połączone z warstwą. Jednak odczytując tę liczbę, należy pamiętać, że:

- Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

- Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

## <a name="Managing"></a>Zarządzanie łączami między warstwami i artefaktami

1. Na diagramie zależności Otwórz menu skrótów dla warstwy, a następnie wybierz polecenie **Wyświetl linki**.

     **Eksplorator warstwy** pokazuje linki artefaktu dla wybranej warstwy.

2. Wykonaj następujące zadania, aby zarządzać tymi łączami:

|**To**|**W Eksploratorze warstwy**|
|-|-|
|Usuwanie łącza między warstwą i artefaktem|Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz polecenie **Usuń**.|
|Przenoszenie łącza z jednej warstwy na drugą|Przeciągnij łącze artefaktu do istniejącej warstwy na diagramie.<br /><br /> — lub —<br /><br /> 1. Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz polecenie **Wytnij**.<br />2. na diagramie zależności Otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|
|Kopiowanie łącza z jednej warstwy na drugą|1. Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz **Kopiuj**.<br />2. na diagramie zależności Otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|
|Tworzenie nowej warstwy z istniejącego łącza artefaktu|Przeciągnij łącze artefaktu do pustego obszaru na diagramie.|
|Sprawdź, czy połączony artefakt obsługuje walidację względem diagramu zależności.|Przyjrzyj się kolumnie **obsługuje walidację** dla linku artefaktu.|

## <a name="Discovering"></a>Odtwarzanie istniejących zależności
 Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Możesz odtwarzać istniejące zależności dla artefaktów, które są połączone z warstwami na diagramie.

> [!NOTE]
> Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby sprawdzić, które artefakty mają zależności, które można odtworzyć, otwórz menu skrótów dla jednej lub wielu warstw, a następnie wybierz polecenie **Wyświetl linki**. W **Eksploratorze warstwy**zapoznaj się z kolumną **Obsługa walidacji** . Zależności nie będą odtwarzane w przypadku artefaktów, dla których ta kolumna pokazuje **wartość false**.

- Wybierz jedną lub wiele warstw, otwórz menu skrótów dla wybranej warstwy, a następnie wybierz polecenie **Generuj zależności**.

  Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.

## <a name="EditDependencies"></a>Edycja warstw i zależności w celu pokazania zamierzonego projektu
 Aby opisać zmiany, które planujesz wprowadzić do systemu lub zamierzonej architektury, Edytuj diagram zależności:

|**To**|**Wykonaj następujące kroki**|
|-|-|
|Zmień lub ogranicz kierunek zależności|Ustaw jej właściwość **Direction** .|
|Tworzenie nowych zależności|Użyj **zależności** i **dwukierunkowych narzędzi zależności** .<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz narzędzie **wskaźnik** lub naciśnij klawisz **ESC** .|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw w właściwości **niedozwolone zależności przestrzeni nazw** . Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw w właściwości **zabronione przestrzenie nazw** warstwy. Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw we właściwości **wymagane przestrzenie nazw** warstwy. Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|

## <a name="EditLayout"></a>Zmień sposób wyświetlania elementów na diagramie
 Możesz zmieniać rozmiar, kształt, kolor i położenie warstw lub kolor zależności, edytując ich właściwości.

## <a name="Codemaps"></a>Odnajdywanie wzorców i zależności na mapie kodu
 Podczas tworzenia diagramów zależności można także tworzyć **mapy kodu**. Te diagramy mogą pomóc w znalezieniu wzorców i zależności podczas eksplorowania kodu. Użyj Eksplorator rozwiązań, Widok klasy lub Przeglądarka obiektów do eksplorowania zestawów, przestrzeni nazw i klas, które często są dobrze zgodne z istniejącymi warstwami. Aby uzyskać więcej informacji na temat map kodu, zobacz:

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Zobacz także

- [Obsługa wersji dla architektury i narzędzi modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [Wideo: Weryfikuj zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)
- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
