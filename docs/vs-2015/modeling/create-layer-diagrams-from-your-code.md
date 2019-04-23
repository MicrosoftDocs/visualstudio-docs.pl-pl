---
title: Tworzenie diagramów warstw z kodu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a3ff96a68d66c95d4f1302ba2f419c873e8f077d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050215"
---
# <a name="create-layer-diagrams-from-your-code"></a>Tworzenie diagramów warstw z kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zwizualizować systemu oprogramowania logiczną architekturę wysokiego, Utwórz *diagramu warstwowego* w programie Visual Studio. Aby upewnić się, że kod pozostaje zgodny z tym projektem, Przeprowadź walidację kodu z diagramu warstwowego. Możesz tworzyć diagramy warstwowe do projektów programu Visual C# .NET i Visual Basic .NET. Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Tworzenie diagramu warstwowego](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Diagram warstwowy pozwala organizować elementy rozwiązania Visual Studio w logiczne, abstrakcyjne grupy o nazwie *warstwy*. Można użyć warstw do opisania głównych zadań wykonywanych przez te artefakty lub główne składniki systemu. Każda warstwa może zawierać innych warstwy opisujące bardziej szczegółowe zadania. Można również określić zamierzone lub istniejące *zależności* między warstwami. Te zależności, które są reprezentowane jako strzałki, wskazują, które warstwy mogą używać lub obecnie używają funkcje reprezentowane przez inne warstwy. Aby utrzymać kontrolę architektury kodu, wyświetl zamierzone zależności na diagramie i przeprowadź walidację kodu na podstawie diagramu.  
  
## <a name="CreateDiagram"></a> Tworzenie diagramu warstwowego  
 Przed utworzeniem diagramu warstwowego upewnij się, że rozwiązanie ma projektu modelowania. Zobacz [UML tworzenie projektów i diagramów modelowania](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
> [!IMPORTANT]
>  Nie dodawaj, nie przeciągaj ani nie kopiuj istniejącego diagramu warstwowego z projektu modelowania do innego projektu modelowania ani do innej lokalizacji w rozwiązaniu. Pozwala to zachować odniesienia z oryginalnego diagramu nawet po zmianie diagramu. Mogłoby to także uniemożliwić prawidłowe działanie walidacji warstwy i spowodować wystąpienie innych problemów, takich jak brakujące elementy lub inne błędy, przy próbie otwarcia diagramu.  
>   
>  Zamiast tego dodaj nowy diagram warstwowy do projektu modelowania. Skopiuj elementy z diagramu źródłowego do nowego diagramu. Zapisz zarówno projekt modelowania, jak i nowy diagram warstwowy.  
  
#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Aby dodać nowy diagram warstwowy do projektu modelowania  
  
1. Na **architektury** menu, wybierz **nowe UML lub diagramu warstwowego**.  
  
2. W obszarze **szablony**, wybierz **diagramu warstwowego**.  
  
3. Nadaj nazwę diagramowi.  
  
4. W **Dodaj do projektu modelowania**, wyszukaj i wybierz istniejący projekt modelowania w rozwiązaniu.  
  
     —lub—  
  
     Wybierz **Utwórz nowy projekt modelowania** Aby dodać nowy projekt modelowania w rozwiązaniu.  
  
    > [!NOTE]
    >  Diagram warstwowy musi istnieć w projekcie modelowania. Możesz jednak połączyć elementy w innym miejscu rozwiązania.  
  
5. Pamiętaj, aby zapisać zarówno projekt modelowania, jak i diagram warstwowy.  
  
## <a name="CreateLayers"></a> Tworzenie warstw z artefaktów  
 Warstwy możesz tworzyć z elementów rozwiązania Visual Studio, takich jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Powoduje to automatyczne tworzenie łączy między warstwami i elementami, uwzględniając je w procesie walidacji warstwy.  
  
 Możesz również połączyć warstwy z elementami, które nie obsługują walidacji, takimi jak dokumenty programu Word lub prezentacji programu PowerPoint, tak aby można było skojarzyć warstwy ze specyfikacjami lub planami. Możesz również połączyć warstwy z plikami projektów współużytkowanymi przez wiele aplikacji, ale proces walidacji nie uwzględni warstw wyświetlanych z nazwami rodzajowymi, takimi jak „Warstwa 1” i „Warstwa 2”.  
  
 Aby sprawdzić, czy połączony element obsługuje walidację, otwórz **Eksplorator warstw** i zbadaj **obsługuje walidację** właściwości elementu. Zobacz [Zarządzanie łączami do artefaktów](#Managing).  
  
|**To**|**Wykonaj następujące kroki**|  
|------------|----------------------------|  
|Utworzyć warstwę dla pojedynczego artefakt|<ol><li>Przeciągnij element do diagramu warstwowego z tych źródeł:<br /><br /> <ul><li>**Eksplorator rozwiązań**<br /><br />         Możesz na przykład przeciągać pliki lub projekty.</li><li>Mapy kodu<br /><br />         Zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) i [mapy Użyj kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Widok klas** lub **przeglądarka obiektów**</li></ul><br />     Warstwy jest wyświetlana na diagramie i jest połączona z artefaktem.</li><li>Zmień nazwę warstwy, aby odzwierciedlała obowiązki skojarzonego kodu lub artefaktów.</li></ol> **Ważne:**  Przeciąganie plików binarnych do diagramu warstwowego nie powoduje automatycznego dodania odniesień do nich do projektu modelowania. Musisz ręcznie dodać do projektu modelowania pliki binarne, które chcesz walidować. **Aby dodać pliki binarne do projektu modelowania** <ol><li>W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu modelowania, a następnie wybierz **Dodaj istniejący element**.</li><li>W **Dodaj istniejący element** okno dialogowe, przejdź do plików binarnych, zaznacz je, a następnie wybierz **OK**.     Pliki binarne pojawią się w projekcie modelowania.</li><li>W **Eksploratora rozwiązań**, wybierz plik binarny, który zostanie dodany, a następnie naciśnij **F4** otworzyć **właściwości** okna.</li><li>Dla każdego pliku binarnego ustaw **Build Action** właściwości **weryfikacji**.</li></ol>|  
|Utwórz jedną warstwę dla wszystkich zaznaczonych artefaktów|Przeciągnij wszystkie artefakty do diagramu warstwowego w tym samym czasie.<br /><br /> Warstw pojawi się na diagramie i będzie połączona z artefaktami.|  
|Tworzenie warstwy dla każdego zaznaczonego artefaktu|Naciśnij i przytrzymaj klawisz **SHIFT** klucza podczas przeciągania wszystkich artefaktów do diagramu warstwowego w tym samym czasie. **Uwaga:**  Jeśli używasz **SHIFT** klawisz, aby wybrać zakres elementów, zwolnij klawisz po zaznaczeniu artefaktów. Naciśnij i przytrzymaj go ponownie podczas przeciągania artefaktów do diagramu. <br /><br /> Warstwa dla każdego artefaktu pojawia się na diagramie i jest połączona z poszczególnymi artefaktami.|  
|Dodawanie artefaktu do warstwy|Przeciągnij artefakt do warstwy.|  
|Tworzenie nowej niepołączonej warstwy|W **przybornika**, rozwiń węzeł **diagramu warstwowego** sekcji, a następnie przeciągnij **warstwy** do diagramu warstwowego.<br /><br /> Aby dodać wiele warstw, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz pozycję **wskaźnik** narzędzi lub naciśnij klawisz **ESC** klucza.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów dla diagramu warstwowego, wybierz polecenie **Dodaj**, a następnie wybierz **warstwy**.|  
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
  
1. Na diagramie warstwowym Otwórz menu skrótów dla warstwy, a następnie wybierz **Wyświetl łącza**.  
  
     **Eksplorator warstw** Wyświetla łącza artefaktów dla zaznaczonej warstwy.  
  
2. Wykonaj następujące zadania, aby zarządzać tymi łączami:  
  
|**To**|**W Eksploratorze warstw**|  
|------------|---------------------------|  
|Usuwanie łącza między warstwą i artefaktem|Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz **Usuń**.|  
|Przenoszenie łącza z jednej warstwy na drugą|Przeciągnij łącze artefaktu do istniejącej warstwy na diagramie.<br /><br /> - lub -<br /><br /> 1.  Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz **Wytnij**.<br />2.  Na diagramie warstwowym Otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|  
|Kopiowanie łącza z jednej warstwy na drugą|1.  Otwórz menu skrótów dla łącza artefaktu, a następnie wybierz **kopiowania**.<br />2.  Na diagramie warstwowym Otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|  
|Tworzenie nowej warstwy z istniejącego łącza artefaktu|Przeciągnij łącze artefaktu do pustego obszaru na diagramie.|  
|Sprawdź, czy połączony artefakt obsługuje walidację na podstawie diagramu warstwowego.|Przyjrzyj się **obsługuje walidację** kolumny dla łącza artefaktu.|  
  
## <a name="Discovering"></a> Odtwarzanie istniejących zależności  
 Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Możesz odtwarzać istniejące zależności dla artefaktów, które są połączone z warstwami na diagramie.  
  
> [!NOTE]
>  Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby zobaczyć, które artefakty mają zależności można odtworzyć, otwórz menu skrótów dla jednej lub wielu warstw, a następnie wybierz **Wyświetl łącza**. W **Eksplorator warstw**, sprawdź **obsługuje walidację** kolumny. Zależności nie będą odtwarzane dla artefaktów, dla których ta kolumna zawiera **False**.  
  
- Zaznacz jedną lub wiele warstw, otwórz menu skrótów dla zaznaczonej warstwy, a następnie wybierz **Wygeneruj zależności**.  
  
  Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.  
  
## <a name="EditDependencies"></a> Edytowanie warstw i zależności w celu przedstawienia zamierzonego projektu  
 Do opisania zmian, które planujesz wprowadzić do systemu lub zamierzonej architektury, przeprowadź edycję diagramu warstwowego:  
  
|**To**|**Wykonaj następujące kroki**|  
|------------|-----------------------------|  
|Zmień lub ogranicz kierunek zależności|Ustaw jego **kierunek** właściwości.|  
|Tworzenie nowych zależności|Użyj **zależności** i **zależność dwukierunkowa** narzędzia.<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz pozycję **wskaźnik** narzędzi lub naciśnij klawisz **ESC** klucza.|  
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Wpisz przestrzenie nazw w warstwie **zabronione zależności Namespace** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|  
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Wpisz przestrzenie nazw w warstwie **zabronione przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|  
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Wpisz przestrzeń nazw w warstwie **wymagane przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielenia przestrzeni nazw.|  
  
## <a name="EditLayout"></a> Zmienianie sposobu wyświetlania elementów na diagramie  
 Możesz zmieniać rozmiar, kształt, kolor i położenie warstw lub kolor zależności, edytując ich właściwości.  
  
## <a name="Codemaps"></a> Odnajdowanie wzorców i zależności na mapie kodu  
 Podczas tworzenia diagramów warstwowych, mogą również utworzyć **map kodu**. Te diagramy ułatwia odnajdowanie wzorców i zależności, chociaż możesz zapoznać się z kodu. Użyj Eksploratora rozwiązań, widoku klas lub przeglądarki obiektów, aby zapoznać się z zestawów, przestrzeni nazw i klas — które często dobrze odpowiadają istniejącym warstwom. Aby uzyskać więcej informacji na temat map kodu zobacz:  
  
- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)  
  
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)  
  
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wideo Channel 9: Projektowanie i Walidacja architektury za pomocą diagramów warstwowych](http://go.microsoft.com/fwlink/?LinkID=252073)   
 [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)   
 [Diagramy warstw: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md)   
 [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)   
 [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)