---
title: Praca z kodem Visual C++ (Projektant klas)
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 16dbcbecece0e8ec38e3f38391ca5063e2e3d36c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975011"
---
# <a name="work-with-visual-c-code-in-class-designer"></a>Praca z kodem języka Visual C++ w Projektancie klas

**Projektant klasy** Wyświetla powierzchni projektowej o nazwie *diagram klas* zapewniający wizualnej reprezentacji elementów kodu w projekcie. Diagramy klas można użyć do projektowania i wizualizowanie klas i innych typów w projekcie.

**Projektant klasy** obsługuje następujące elementy kodu C++:

- Klasy (przypomina kształt klasy zarządzanej, z tą różnicą, że może mieć wiele relacji dziedziczenia)

- Klasa anonimowa (wyświetla wygenerowaną nazwę widoku klasy dla typu anonimowego)

- Klasa szablonu

- Struct

- Wyliczenie

- Makra (wyświetla przetworzone po widoku makro)

- Element TypeDef

> [!NOTE]
> Nie jest taka sama jak diagram klas UML, który można utworzyć w projekcie modelowania. Aby uzyskać więcej informacji, zobacz [diagramów klas UML: Odwołanie](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Rozwiązywanie problemów z rozwiązania typu i problemów z wyświetlaniem

### <a name="location-of-source-files"></a>Lokalizację plików źródłowych

**Projektant klasy** nie zachować informacje o lokalizacji plików źródłowych. W związku z tym, jeśli zmodyfikujesz do struktury projektu lub Przenieś pliki źródłowe w swoim projekcie **projektanta klas** może utracić śledzenie typ (szczególnie typ źródłowy element typedef, bazowe klasy lub typu powiązania). Może zostać wyświetlony błąd taki jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij kod źródłowy zmodyfikowany lub przenoszone do diagramu klas, aby ją wyświetlić ją ponownie.

### <a name="update-and-performance-issues"></a>Aktualizacja problemów z wydajnością

Dla projektów Visual C++ może potrwać 30 do 60 sekund, aby zmiany w pliku źródłowym, być wyświetlane na diagramie klasy. To opóźnienie może również spowodować **projektanta klas** zgłosić błąd **nie znaleziono żadnych typów w zaznaczeniu**. Jeśli zostanie wyświetlony błąd taki jak to, kliknij przycisk **anulować** komunikat o błędzie i zaczekaj, aż element kodu, które będą wyświetlane na **Widok klas**. Po wykonaniu tej czynności **projektanta klas** powinno być możliwe do wyświetlania tego typu.

Jeśli diagram klas nie aktualizuje się zmiany wprowadzone w kodzie, konieczne może być zamknij diagram i otwórz go ponownie.

### <a name="type-resolution-issues"></a>Typ rozwiązywania problemów

**Projektant klasy** może nie móc rozwiązać typów z następujących powodów:

- Typ jest w projekcie lub w zestawie, który nie odwołuje się projekt, który zawiera diagram klas. Aby rozwiązać ten problem, Dodaj odwołanie do projektu lub zestawu, który zawiera tekst. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../managing-references-in-a-project.md).

- Typ nie jest w niewłaściwym zakresie, więc **projektanta klas** nie można go zlokalizować. Upewnij się, że kod nie jest Brak `using`, `imports`, lub `#include` instrukcji. Upewnij się, że nie zostały przeniesione typu (lub powiązanego typu) z przestrzeni nazw, w którym został on pierwotnie znajduje się również.

- Typ nie istnieje lub została ujęta w komentarz. Aby rozwiązać ten problem, upewnij się, że nie oznaczone jako komentarz lub usunięty typ.

- Typ znajduje się w bibliotece odwołuje się #import — dyrektywa. Możliwym obejściem jest ręcznie dodać wygenerowanego kodu (plik .tlh) # dyrektywy include w pliku nagłówka.

- Upewnij się, że **projektanta klas** obsługuje typ wprowadzony. Zobacz [ograniczenia dla elementów kodu w języku C++](#limitations-for-c-code-elements).

Ten błąd jest najbardziej prawdopodobne zobaczyć problemu rozpoznawania typu jest **nie można odnaleźć kodu dla jednego lub więcej kształtów na diagramie klasy "\<element >"**. Ten komunikat o błędzie nie musi oznaczać, że Twój kod jest błąd. Wskazuje on, że tego projektanta klas nie może wyświetlić kodu. Spróbuj wykonać następujące działania:

- Upewnij się, że typ istnieje. Upewnij się, że nie przypadkowo oznaczone jako komentarz lub usunięty kodu źródłowego.

- Spróbuj rozwiązać tego typu. Typ może być w projekcie lub w zestawie, który nie odwołuje się projekt, który zawiera diagram klas. Aby rozwiązać ten problem, Dodaj odwołanie do projektu lub zestawu, który zawiera tekst. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../managing-references-in-a-project.md).

- Upewnij się, że typ jest w niewłaściwym zakresie tak, aby zlokalizować projektanta klas. Upewnij się, że kod nie jest Brak `using`, `imports`, lub `#include` instrukcji. Upewnij się, że nie zostały przeniesione typu (lub powiązanego typu) z przestrzeni nazw, w którym został on pierwotnie znajduje się również.

### <a name="troubleshoot-other-error-messages"></a>Rozwiązywanie problemów z inne komunikaty o błędach

Pomoc dotyczącą rozwiązywania problemów z błędów i ostrzeżeń można znaleźć w publiczne fora Microsoft Developer Network (MSDN). Zobacz [Forum projektanta klas programu Visual Studio](http://go.microsoft.com/fwlink/?linkid=160754).

## <a name="limitations-for-c-code-elements"></a>Ograniczenia dotyczące elementów kodu C++

- Podczas ładowania projektu Visual C++ **projektanta klas** funkcje w sposób tylko do odczytu. Można zmienić na diagramie klasy, ale nie można zapisać zmian z diagramu klasy do kodu źródłowego.

- **Projektant klasy** obsługuje tylko natywny semantyki C++. W przypadku projektów Visual C++, które są kompilowane do kodu zarządzanego **projektanta klas** tylko wizualizacji elementy kodu, które są typami natywnymi. W związku z tym, można dodać diagram klas do projektu, ale **projektanta klas** nie zezwoli na wizualizowanie elementów, w którym `IsManaged` właściwość jest ustawiona na `true` (oznacza to typy wartości i typy referencyjne).

- Dla projektów Visual C++ **projektanta klas** odczytuje tylko definicji typu. Załóżmy na przykład, możesz zdefiniować typu w pliku nagłówka (.h) i zdefiniować jej elementów członkowskich w pliku implementacji (.cpp). Jeśli wywołujesz "Pokaż Diagram klas" w pliku implementacji (.cpp) **projektanta klas** powoduje wyświetlenia żadnych danych. Inny przykład, jeśli wywołujesz "Pokaż Diagram klas" w pliku .cpp, który używa `#include` instrukcję, aby dołączyć inne pliki, ale nie zawiera żadnych definicji rzeczywista klasa **projektanta klas** ponownie powoduje wyświetlenia żadnych danych.

- Pliki IDL (.idl), które definiowanie interfejsów COM i bibliotek typów, nie są wyświetlane na diagramach, chyba że są one kompilowane do kodu natywnego języka C++.

- **Projektant klasy** nie obsługuje funkcje i zmienne globalne.

- **Projektant klasy** nie obsługuje Unii. Jest to specjalny typ klasy, w którym pamięci przydzielonej jest niezbędne dla Unii zajmuje największy element członkowski danych kwoty.

- **Projektant klasy** nie wyświetla typy danych podstawowych takich jak `int` i `char`.

- **Projektant klasy** nie wyświetla typy, które są zdefiniowane poza bieżącym projekcie, jeśli projekt nie ma poprawne odwołania do tych typów.

- **Projektant klasy** można wyświetlić typy zagnieżdżone, ale nie relacje między typem zagnieżdżonym i innych typów.

- **Projektant klasy** nie może wyświetlić typy, które są nieważne lub który pochodzi od typu void.

## <a name="see-also"></a>Zobacz także

- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
- [Dodatkowe informacje na temat błędów Projektanta klas](additional-information-about-errors.md)
- [Klasy Visual C++ w Projektancie klas](visual-cpp-classes.md)
- [Struktury Visual C++ w Projektancie klas](visual-cpp-structures.md)
- [Wyliczenia Visual C++ w Projektancie klas](visual-cpp-enumerations.md)
- [Definicje typów języka Visual C++ w Projektancie klas](visual-cpp-typedefs.md)
