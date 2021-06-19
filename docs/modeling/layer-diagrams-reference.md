---
title: Informacje o diagramach zależności
description: Dowiedz się, Visual Studio diagram zależności umożliwia wizualizację architektury logicznej wysokiego poziomu systemu.
ms.custom: SEO-VS-2020
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb138164cfab44778c932a4bcb93572a3053a70
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391039"
---
# <a name="dependency-diagrams-reference"></a>Diagramy zależności: informacje

W Visual Studio można użyć *diagramu zależności,* aby zwizualizować architekturę logiczną wysokiego poziomu systemu. Diagram zależności organizuje artefakty fizyczne w systemie w logiczne, abstrakcyjne grupy nazywane *warstwami*. Warstwy te opisują główne zadania wykonywane przez artefakty lub główne składniki systemu. Każda warstwa może również zawierać zagnieżdżone warstwy, które opisują bardziej szczegółowe zadania.

Aby sprawdzić, które wersje Visual Studio tej funkcji, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

> [!NOTE]
> Diagramy zależności dla projektów .NET Core są obsługiwane od Visual Studio 2019 w wersji 16.2.

Między warstwami można określić zamierzone lub istniejące zależności. Zależności te, które są reprezentowane jako strzałki, wskazują, które warstwy mogą korzystać z funkcji reprezentowanych przez inne warstwy lub aktualnie z nich korzystać. Dzięki zorganizowaniu systemu w warstwy opisujące różne role i funkcje diagram zależności może ułatwić zrozumienie, ponowne użycie i utrzymanie kodu.

Użyj diagramu zależności, aby ułatwić wykonywanie następujących zadań:

- Przekaż istniejącą lub zamierzony architekturę logiczną systemu.

- Wykrywanie konfliktów między istniejącym kodem a zamierzony architekturą.

- Wizualizowanie wpływu zmian na zamierzoną architekturę podczas refaktoryzacji, aktualizowania lub rozwoju systemu.

- Zatęchlij zamierzony projekt architektury podczas opracowywania i konserwacji kodu, uwzględniając walidację zaewidencji i operacje kompilacji.

W tym temacie opisano elementy, których można użyć na diagramie zależności. Aby uzyskać bardziej szczegółowe informacje na temat tworzenia i rysowania diagramów zależności, zobacz [Diagramy zależności: Wskazówki.](../modeling/layer-diagrams-guidelines.md) Aby uzyskać więcej informacji na temat wzorców warstw, odwiedź witrynę [Patterns & Practices](https://archive.codeplex.com/?p=apparch)(Wzorce i praktyki).

## <a name="reading-dependency-diagrams"></a>Odczytywanie diagramów zależności

![Elementy diagramów zależności](../modeling/media/uml_layerrefreading.png)

W poniższej tabeli opisano elementy, których można użyć na diagramie zależności.

|**Kształt**|**Element**|**Opis**|
|-|-|-|
|1|**Warstwa**|Logiczna grupa fizycznych artefaktów w systemie. Te artefakty mogą być przestrzeniami nazw, projektami, klasami, metodami itp.<br /><br /> Aby wyświetlić artefakty połączone z warstwą, otwórz menu skrótów dla warstwy, a następnie wybierz pozycję **Wyświetl** linki, aby otworzyć **Eksploratora warstwy.**<br /><br /> Aby uzyskać więcej informacji, zobacz [Eksplorator warstw](#Explorer).<br /><br /> -   **Zabronione zależności przestrzeni nazw** — określa, że artefakty skojarzone z tą warstwą nie mogą zależeć od określonych przestrzeni nazw.<br />-   **Zabronione przestrzenie nazw** — określa, że artefakty skojarzone z tą warstwą nie mogą należeć do określonych przestrzeni nazw.<br />-   **Wymagane przestrzenie nazw** — określa, że artefakty skojarzone z tą warstwą muszą należeć do jednej z określonych przestrzeni nazw.|
|2|**Zależność**|Wskazuje, że jedna warstwa może korzystać z funkcji w innej warstwie, ale nie odwrotnie.<br /><br /> -   **Kierunek** — określa kierunek zależności.|
|3|**Zależność dwukierunkowa**|Wskazuje, że jedna warstwa może korzystać z funkcji w innej warstwie i na odwrót.<br /><br /> -   **Kierunek** — określa kierunek zależności.|
|4|**Komentarz**|Użyj , aby dodać ogólne uwagi do diagramu lub elementów na diagramie.|
|5|**Link komentarza**|Użyj , aby połączyć komentarze z elementami na diagramie.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Eksplorator warstw

Każdą warstwę można połączyć z artefaktami w rozwiązaniu, takimi jak projekty, klasy, przestrzenie nazw, pliki projektu i inne części oprogramowania. Liczba w warstwie pokazuje liczbę artefaktów połączonych z warstwą. Jednak podczas odczytywania liczby artefaktów w warstwie należy pamiętać o następujących elementy:

- Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

- Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

Aby uzyskać więcej informacji na temat łączenia warstw i artefaktów, zobacz:

- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Badanie połączonych artefaktów

Na diagramie zależności otwórz menu skrótów dla co najmniej jednej warstwy, a następnie wybierz pozycję **Wyświetl linki**.

**Zostanie otwarty Eksplorator** warstw z artefaktami połączonymi z wybranymi warstwami. **Eksplorator warstw** zawiera kolumnę, która pokazuje wszystkie właściwości linków artefaktu.

> [!NOTE]
> Jeśli nie widzisz wszystkich tych właściwości, rozwiń okno **Eksplorator warstw.**

|**Kolumna w Eksploratorze warstw**|**Opis**|
|-|-|
|**Kategorie**|Rodzaj artefaktu, taki jak klasa, przestrzeń nazw, plik źródłowy i tak dalej|
|**Warstwa**|Warstwa, która łączy się z artefaktem|
|**Obsługuje walidację**|W **przypadku wartości True** proces walidacji warstwy może sprawdzić, czy projekt jest zgodny z zależnościami tego elementu lub z tego elementu.<br /><br /> Jeśli **ma wartość False,** link nie uczestniczy w procesie walidacji warstwy.<br /><br /> Aby uzyskać więcej informacji, zobacz [Diagramy zależności: Wskazówki.](../modeling/layer-diagrams-guidelines.md)|
|**Identyfikator**|Odwołanie do połączonego artefaktu|

## <a name="see-also"></a>Zobacz też

- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
