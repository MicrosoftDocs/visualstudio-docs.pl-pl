---
title: Odwołanie do diagramów zależności
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
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
ms.openlocfilehash: 1e592b6d5da908b71aa5af9bae7afe495944301a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936798"
---
# <a name="dependency-diagrams-reference"></a>Diagramy zależności: odwołanie

W programie Visual Studio, można użyć *diagram zależności* aby zwizualizować logiczną architekturę wysokiego systemu. Diagram zależności organizuje artefaktów fizycznych w systemie w logiczne, abstrakcyjne grupy o nazwie *warstwy*. Te warstwy opisania głównych zadań wykonywanych przez te artefakty pełnią lub główne składniki systemu. Każda warstwa może również zawierać zagnieżdżone warstwy opisujące bardziej szczegółowe zadania.

Aby zobaczyć, jakie wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługę wersji narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Diagramy zależności nie są obsługiwane dla projektów .NET Core w programie Visual Studio.

Można określić zamierzone lub istniejące zależności między warstwami. Te zależności, które są reprezentowane jako strzałki, wskazują, które warstwy mogą używać lub obecnie używają funkcje reprezentowane przez inne warstwy. Organizacja systemu na warstwy, które opisują różne role i funkcje, diagram zależności może ułatwić ułatwiają zrozumienie, ponowne użycie i utrzymywać kod.

Użyj diagramu, zależności, które ułatwiają wykonywanie następujących zadań:

- Komunikować się z istniejącą lub zamierzonego logiczną architekturę systemu.

- Odkryj konfliktów między istniejący kod i planowaną architekturę.

- Wizualizacja wpływu zmian na planowaną architekturę podczas refaktoryzacji, zaktualizować lub ewolucji systemu.

- Wzmocnienie planowaną architekturę podczas tworzenia i konserwacji kodu, umieszczając Weryfikacja przy użyciu zaewidencjonowania i operacji kompilacji.

W tym temacie opisano elementy, które można używać na diagram zależności. Aby uzyskać szczegółowe informacje o sposobie tworzenia i Rysowanie diagramów zależności, zobacz [diagramy zależności: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md). Aby uzyskać więcej informacji na temat wzorców warstwowe, odwiedź stronę [lokacji wzorców i praktyk](http://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-dependency-diagrams"></a>Odczytywanie diagramów zależności

![Elementy na diagramach zależności](../modeling/media/uml_layerrefreading.png)

W poniższej tabeli opisano elementy, które można używać na diagram zależności.

|**Kształt**|**Element**|**Opis**|
|-|-|-|
|1|**Warstwa**|Grupy logicznej artefaktów fizycznych w systemie. Te artefakty mogą być przestrzenie nazw, projekty, klasy, metody i tak dalej.<br /><br /> Aby zobaczyć artefakty, które są połączone z warstwą, otwórz menu skrótów dla warstwy, a następnie wybierz **Wyświetl łącza** otworzyć **Eksplorator warstw**.<br /><br /> Aby uzyskać więcej informacji, zobacz [Eksplorator warstw](#Explorer).<br /><br /> -   **Zabronione zależności Namespace** — Określa, że artefakty skojarzone z tą warstwą nie może zależeć od określonych przestrzeni nazw.<br />-   **Zabronione przestrzenie nazw** — Określa, że artefakty skojarzone z tą warstwą nie mogą należeć do określonych przestrzeni nazw.<br />-   **Wymagane przestrzenie nazw** — Określa, że artefakty skojarzone z tą warstwą muszą należeć do jednej z określonych przestrzeni nazw.|
|2|**Zależności**|Wskazuje, że jedna warstwę może korzystać z funkcji w innej warstwie, ale nie odwrotnie.<br /><br /> -   **Kierunek** -Określa kierunek zależności.|
|3|**Zależność dwukierunkowa**|Wskazuje, że jedna warstwę może korzystać z funkcji w innej warstwie i odwrotnie.<br /><br /> -   **Kierunek** -Określa kierunek zależności.|
|4|**Komentarz**|Służy do dodawania notatek do diagramu lub elementy na diagramie.|
|5|**Link komentarza**|Usługa umożliwia łączenie komentarze do elementów na diagramie.|

## <a name="Explorer"></a> Eksplorator warstw

Możesz połączyć każdą warstwę artefakty w rozwiązaniu, takich jak projekty, klasy, przestrzeni nazw, pliki projektu i innymi częściami oprogramowania. Liczba na warstwie pokazuje liczbę artefaktów, które są połączone z warstwą. Jednak podczas odczytywania liczbę artefaktów na warstwie, pamiętaj o następujących kwestiach:

- Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

- Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

Aby uzyskać więcej informacji na temat łączenia warstwami i artefaktami zobacz:

- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Sprawdź połączonych artefaktów

Na diagramie zależności, otwórz menu skrótów dla jednej lub kilku warstw, a następnie wybierz **Wyświetl łącza**.

**Eksplorator warstw** otwiera się i pokazuje artefaktów, które są połączone z wybranej warstwy. **Eksplorator warstw** zawiera kolumnę, który pokazuje poszczególne właściwości łącza artefaktu.

> [!NOTE]
> Jeśli nie widzisz wszystkie te właściwości, rozwiń **Eksplorator warstw** okna.

|**Kolumna w Eksploratorze warstw**|**Opis**|
|-|-|
|**Kategorie**|Rodzaj artefaktu, takie jak klasy, przestrzeni nazw, plik źródłowy i tak dalej|
|**Warstwa**|Warstwy, który stanowi łącze do artefaktu|
|**Obsługuje walidację**|Jeśli **True**, a następnie proces sprawdzania poprawności warstwy można sprawdzić, czy projekt jest zgodny ze zależności do lub z tego elementu.<br /><br /> Jeśli **False**, a następnie łącze nie uczestniczy w procesie walidacji warstwy.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramy zależności: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md).|
|**Identyfikator**|Odwołanie do połączonych artefaktów|

## <a name="see-also"></a>Zobacz także

- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
