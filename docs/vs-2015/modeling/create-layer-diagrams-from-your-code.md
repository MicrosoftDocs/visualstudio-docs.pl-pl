---
title: Tworzenie diagramów warstwy na podstawie kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 138f818eab34b0b1860c7daa85f1b6814888fc9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652847"
---
# <a name="create-layer-diagrams-from-your-code"></a>Tworzenie diagramów warstw z kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wizualizować architekturę logiczną wysokiego poziomu systemu oprogramowania, Utwórz *Diagram warstwowy* w programie Visual Studio. Aby upewnić się, że kod pozostaje spójny z tym projektem, zweryfikuj swój kod przy użyciu diagramu warstwowego. Możesz tworzyć diagramy warstwowe do projektów programu Visual C# .NET i Visual Basic .NET. Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektura i modelowanie](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

 ![Tworzenie diagramu warstwowego](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 Diagram warstwowy umożliwia organizowanie elementów rozwiązania programu Visual Studio w logiczne, abstrakcyjne grupy o nazwie *warstwy*. Można użyć warstw do opisania głównych zadań wykonywanych przez te artefakty lub główne składniki systemu. Każda warstwa może zawierać innych warstwy opisujące bardziej szczegółowe zadania. Można również określić zamierzone lub istniejące *zależności* między warstwami. Te zależności, które są reprezentowane jako strzałki, wskazują, które warstwy mogą używać lub obecnie używają funkcje reprezentowane przez inne warstwy. Aby utrzymać kontrolę architektury kodu, wyświetl zamierzone zależności na diagramie i przeprowadź walidację kodu na podstawie diagramu.

## <a name="CreateDiagram"></a>Tworzenie diagramu warstwowego
 Przed utworzeniem diagramu warstwowego upewnij się, że rozwiązanie ma projektu modelowania. Zobacz [Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> Nie dodawaj, nie przeciągaj ani nie kopiuj istniejącego diagramu warstwowego z projektu modelowania do innego projektu modelowania ani do innej lokalizacji w rozwiązaniu. Pozwala to zachować odniesienia z oryginalnego diagramu nawet po zmianie diagramu. Mogłoby to także uniemożliwić prawidłowe działanie walidacji warstwy i spowodować wystąpienie innych problemów, takich jak brakujące elementy lub inne błędy, przy próbie otwarcia diagramu.
>
> Zamiast tego dodaj nowy diagram warstwowy do projektu modelowania. Skopiuj elementy z diagramu źródłowego do nowego diagramu. Zapisz zarówno projekt modelowania, jak i nowy diagram warstwowy.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Aby dodać nowy diagram warstwowy do projektu modelowania

1. W menu **Architektura** wybierz kolejno pozycje **Nowy UML lub diagram warstwowy**.

2. W obszarze **Szablony**wybierz pozycję **Diagram warstwowy**.

3. Nadaj nazwę diagramowi.

4. W obszarze **Dodaj do projektu modelowania**przejdź do i wybierz istniejący projekt modelowania w rozwiązaniu.

     —lub—

     Wybierz pozycję **Utwórz nowy projekt modelowania** , aby dodać nowy projekt modelowania do rozwiązania.

    > [!NOTE]
    > Diagram warstwowy musi istnieć w projekcie modelowania. Możesz jednak połączyć elementy w innym miejscu rozwiązania.

5. Pamiętaj, aby zapisać zarówno projekt modelowania, jak i diagram warstwowy.

## <a name="CreateLayers"></a>Tworzenie warstw na podstawie artefaktów
 Warstwy możesz tworzyć z elementów rozwiązania Visual Studio, takich jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Powoduje to automatyczne tworzenie łączy między warstwami i elementami, uwzględniając je w procesie walidacji warstwy.

 Możesz również połączyć warstwy z elementami, które nie obsługują walidacji, takimi jak dokumenty programu Word lub prezentacji programu PowerPoint, tak aby można było skojarzyć warstwy ze specyfikacjami lub planami. Możesz również połączyć warstwy z plikami projektów współużytkowanymi przez wiele aplikacji, ale proces walidacji nie uwzględni warstw wyświetlanych z nazwami rodzajowymi, takimi jak „Warstwa 1” i „Warstwa 2”.

 Aby sprawdzić, czy połączony element obsługuje walidację, Otwórz **Eksploratora warstw** i sprawdź Właściwość **obsługuje walidację** elementu. Zobacz [Zarządzanie łączami do artefaktów](#Managing).

|**Do**|**Wykonaj następujące kroki**|
|------------|----------------------------|
|Utworzyć warstwę dla pojedynczego artefakt|<ol><li>Przeciągnij element na diagram warstwy z następujących źródeł:<br /><br /> <ul><li>**Eksplorator rozwiązań**<br /><br />         Możesz na przykład przeciągać pliki lub projekty.</li><li>Mapy kodu<br /><br />         Zapoznaj się z [zależnościami mapy w swoich rozwiązaniach](../modeling/map-dependencies-across-your-solutions.md) i [korzystaj z map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Widok klasy** lub **Przeglądarka obiektów**</li></ul><br />     Warstwy jest wyświetlana na diagramie i jest połączona z artefaktem.</li><li>Zmień nazwę warstwy, aby odzwierciedlała obowiązki skojarzonego kodu lub artefaktów.</li></ol> **Ważne:**  Przeciąganie plików binarnych do diagramu warstwowego nie powoduje automatycznego dodania odwołań do projektu modelowania. Musisz ręcznie dodać do projektu modelowania pliki binarne, które chcesz walidować. **Aby dodać pliki binarne do projektu modelowania** <ol><li>W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu modelowania, a następnie wybierz **Dodaj istniejący element**.</li><li>W oknie dialogowym **Dodaj istniejący element** przejdź do plików binarnych, zaznacz je, a następnie wybierz **przycisk OK**.     Pliki binarne pojawią się w projekcie modelowania.</li><li>W **Eksplorator rozwiązań**wybierz plik binarny, który został dodany, a następnie naciśnij klawisz **F4** , aby otworzyć okno **Właściwości** .</li><li>Dla każdego pliku binarnego ustaw właściwość **Akcja kompilacji** na **Sprawdź poprawność**.</li></ol>|
|Utwórz jedną warstwę dla wszystkich zaznaczonych artefaktów|Przeciągnij wszystkie artefakty do diagramu warstwowego w tym samym czasie.<br /><br /> Warstw pojawi się na diagramie i będzie połączona z artefaktami.|
|Tworzenie warstwy dla każdego zaznaczonego artefaktu|Naciśnij i przytrzymaj klawisz **SHIFT** podczas przeciągania wszystkich artefaktów do diagramu warstwy w tym samym czasie. **Uwaga:**  Jeśli używasz klawisza **SHIFT** , aby wybrać zakres elementów, po wybraniu artefaktów zwolnij klawisz. Naciśnij i przytrzymaj go ponownie podczas przeciągania artefaktów do diagramu. <br /><br /> Warstwa dla każdego artefaktu pojawia się na diagramie i jest połączona z poszczególnymi artefaktami.|
|Dodawanie artefaktu do warstwy|Przeciągnij artefakt do warstwy.|
|Tworzenie nowej niepołączonej warstwy|W **przyborniku**rozwiń sekcję **Diagram warstwowy** , a następnie przeciągnij **warstwę** do diagramu warstwowego.<br /><br /> Aby dodać wiele warstw, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz narzędzie **wskaźnik** lub naciśnij klawisz **ESC** .<br /><br /> oraz<br /><br /> Otwórz menu skrótów dla diagramu warstwy, wybierz polecenie **Dodaj**, a następnie wybierz **warstwa**.|
|Tworzenie zagnieżdżonych warstw|Przeciągnij istniejącą warstwę na inną warstwę.<br /><br /> oraz<br /><br /> Otwórz menu skrótów dla warstwy, wybierz polecenie **Dodaj**, a następnie wybierz **warstwa**.|
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

1. Na diagramie warstwowym Otwórz menu skrótów dla warstwy, a następnie wybierz polecenie **Wyświetl linki**.

     **Eksplorator warstwy** pokazuje linki artefaktu dla wybranej warstwy.

2. Wykonaj następujące zadania, aby zarządzać tymi łączami:

|**Do**|**W Eksploratorze warstwy**|
|------------|---------------------------|
|Usuwanie łącza między warstwą i artefaktem|Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz polecenie **Usuń**.|
|Przenoszenie łącza z jednej warstwy na drugą|Przeciągnij łącze artefaktu do istniejącej warstwy na diagramie.<br /><br /> oraz<br /><br /> 1. Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz polecenie **Wytnij**.<br />2. na diagramie warstwowym Otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|
|Kopiowanie łącza z jednej warstwy na drugą|1. Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz **Kopiuj**.<br />2. na diagramie warstwowym Otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|
|Tworzenie nowej warstwy z istniejącego łącza artefaktu|Przeciągnij łącze artefaktu do pustego obszaru na diagramie.|
|Sprawdź, czy połączony artefakt obsługuje walidację na podstawie diagramu warstwowego.|Przyjrzyj się kolumnie **obsługuje walidację** dla linku artefaktu.|

## <a name="Discovering"></a>Odtwarzanie istniejących zależności
 Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Możesz odtwarzać istniejące zależności dla artefaktów, które są połączone z warstwami na diagramie.

> [!NOTE]
> Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby sprawdzić, które artefakty mają zależności, które można odtworzyć, otwórz menu skrótów dla jednej lub wielu warstw, a następnie wybierz polecenie **Wyświetl linki**. W **Eksploratorze warstwy**zapoznaj się z kolumną **Obsługa walidacji** . Zależności nie będą odtwarzane w przypadku artefaktów, dla których ta kolumna pokazuje **wartość false**.

- Wybierz jedną lub wiele warstw, otwórz menu skrótów dla wybranej warstwy, a następnie wybierz polecenie **Generuj zależności**.

  Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.

## <a name="EditDependencies"></a>Edycja warstw i zależności w celu pokazania zamierzonego projektu
 Do opisania zmian, które planujesz wprowadzić do systemu lub zamierzonej architektury, przeprowadź edycję diagramu warstwowego:

|**Do**|**Wykonaj następujące kroki**|
|------------|-----------------------------|
|Zmień lub ogranicz kierunek zależności|Ustaw jej właściwość **Direction** .|
|Tworzenie nowych zależności|Użyj **zależności** i **dwukierunkowych narzędzi zależności** .<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz narzędzie **wskaźnik** lub naciśnij klawisz **ESC** .|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw w właściwości **niedozwolone zależności przestrzeni nazw** . Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw w właściwości **zabronione przestrzenie nazw** warstwy. Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw we właściwości **wymagane przestrzenie nazw** warstwy. Użyj średnika ( **;** ), aby oddzielić przestrzenie nazw.|

## <a name="EditLayout"></a>Zmień sposób wyświetlania elementów na diagramie
 Możesz zmieniać rozmiar, kształt, kolor i położenie warstw lub kolor zależności, edytując ich właściwości.

## <a name="Codemaps"></a>Odnajdywanie wzorców i zależności na mapie kodu
 Podczas tworzenia diagramów warstw można także tworzyć **mapy kodu**. Te diagramy mogą pomóc w znalezieniu wzorców i zależności podczas eksplorowania kodu. Użyj Eksplorator rozwiązań, Widok klasy lub Przeglądarka obiektów do eksplorowania zestawów, przestrzeni nazw i klas, które często są dobrze zgodne z istniejącymi warstwami. Aby uzyskać więcej informacji na temat map kodu, zobacz:

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Zobacz też
 [Wideo Channel 9: projektowanie i weryfikowanie architektury przy użyciu](http://go.microsoft.com/fwlink/?LinkID=252073) diagramów warstwowych diagramy: Diagramy warstw [referencyjnych](../modeling/layer-diagrams-reference.md) [: wskazówki](../modeling/layer-diagrams-guidelines.md) [Weryfikuj kod przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md) [Wizualizacja kodu](../modeling/visualize-code.md)