---
title: Praca z kodem języka C++ (projektant klasy)
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- C++, Class Designer
- Class Designer, C++ support
- Class Designer, limitations
- Class Designer, tasks in C++
- C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 54087a719b0079ba32ff08ff1e08ad01f5e64ed0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596752"
---
# <a name="work-with-c-code-in-class-designer"></a>Praca z kodem języka C++ w Projektancie klas

**Projektant klas** wyświetla powierzchnię projektu wizualnego o nazwie *diagram klasy,* który zapewnia wizualną reprezentację elementów kodu w projekcie. Diagramy klas można używać do projektowania i wizualizacji klas i innych typów w projekcie.

**Projektant klas** obsługuje następujące elementy kodu języka C++:

- Klasa (przypomina kształt klasy zarządzanej, z tą różnicą, że może mieć wiele relacji dziedziczenia)

- Klasa anonimowa (wyświetla nazwę wygenerowaną widoku klasy dla typu anonimowego)

- Klasa szablonu

- Struct

- Wyliczenie

- Makro (wyświetla post-przetworzony widok makra)

- Typedef

> [!NOTE]
> To nie jest taka sama jak diagram klasy UML, który można utworzyć w projekcie modelowania. Aby uzyskać więcej informacji, zobacz [Diagramy klas UML: Odwołanie](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Rozwiązywanie problemów z rozpoznawaniem i wyświetlaniem typów

### <a name="location-of-source-files"></a>Lokalizacja plików źródłowych

**Projektant klas** nie śledzi lokalizacji plików źródłowych. W związku z tym jeśli zmodyfikujesz strukturę projektu lub przenieść pliki źródłowe w projekcie, **Projektant klas** może utracić śledzenie typu (zwłaszcza typ źródłowy typedef, klas podstawowych lub typów skojarzeń). Może pojawić się błąd, taki jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij zmodyfikowany lub przeniesiony kod źródłowy do diagramu klasy ponownie, aby ponownie go wyświetlić.

### <a name="update-and-performance-issues"></a>Problemy z aktualizacją i wydajnością

W przypadku projektów języka C++ może upłynąć od 30 do 60 sekund, aby zmiana w pliku źródłowym pojawiła się na diagramie klasy. To opóźnienie może również **spowodować, że Projektant klas** zrzuci błąd **Nie znaleziono typów w zaznaczeniu**. Jeśli pojawi się taki błąd, kliknij przycisk **Anuluj** w komunikacie o błędzie i poczekaj, aż element kodu pojawi się w **widoku klasy**. Po tym, **jak** to zrobić, Projektant klas powinien być w stanie wyświetlić typ.

Jeśli diagram klasy nie aktualizuje się ze zmianami wprowadzonymi w kodzie, może być konieczne zamknięcie diagramu i ponowne otwarcie go.

### <a name="type-resolution-issues"></a>Problemy z rozwiązywaniem typów

**Projektant klas** może nie być w stanie rozpoznać typów z następujących powodów:

- Typ znajduje się w projekcie lub zestawie, do którego nie odwołuje się projekt zawierający diagram klas. Aby rozwiązać ten błąd, należy dodać odwołanie do projektu lub zestawu, który zawiera typ. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../managing-references-in-a-project.md).

- Typ nie znajduje się w odpowiednim zakresie, więc **projektant klas** nie może go zlokalizować. Upewnij się, że w `using` `imports`kodzie `#include` nie brakuje , lub instrukcji. Upewnij się również, że typ (lub typ pokrewny) nie został przeniesiony z obszaru nazw, w którym pierwotnie znajdował się.

- Typ nie istnieje (lub został skomentowany). Aby rozwiązać ten błąd, upewnij się, że typ nie został skomentowany ani usunięty.

- Typ znajduje się w bibliotece, do których odwołuje się dyrektywa #import. Możliwym obejściem jest ręczne dodanie wygenerowanego kodu (pliku tlh) do dyrektywy #include do pliku nagłówka.

- Upewnij się, że **projektant klas** obsługuje wprowadzony typ. Zobacz [Ograniczenia dla elementów kodu języka C++](#limitations-for-c-code-elements).

Błąd, który jest najbardziej prawdopodobne, aby zobaczyć dla problemu z rozpoznawaniem typów jest **Kod nie można znaleźć dla jednego lub więcej kształtów na diagramie klasy "element\<>"**. Ten komunikat o błędzie nie musi oznaczać, że kod jest w błędzie. Wskazuje tylko, że projektant klas nie mógł wyświetlić kodu. Wypróbuj następujące środki:

- Upewnij się, że typ istnieje. Upewnij się, że kod źródłowy nie został przypadkowo skomentowany lub usunięty.

- Spróbuj rozwiązać ten typ. Typ może znajdować się w projekcie lub zestawie, do którego nie odwołuje się projekt zawierający diagram klas. Aby rozwiązać ten błąd, należy dodać odwołanie do projektu lub zestawu, który zawiera typ. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../managing-references-in-a-project.md).

- Upewnij się, że typ znajduje się w odpowiednim zakresie, aby projektant klas mógł go zlokalizować. Upewnij się, że w `using`kodzie nie brakuje instrukcji , `imports`lub `#include` instrukcji. Upewnij się również, że typ (lub typ pokrewny) nie został przeniesiony z obszaru nazw, w którym pierwotnie znajdował się.

### <a name="troubleshoot-other-error-messages"></a>Rozwiązywanie problemów z innymi komunikatami o błędach

Pomoc dotyczącą rozwiązywania problemów z błędami i ostrzeżeniami można znaleźć na forach publicznych usługi Microsoft Developer Network (MSDN). Zobacz [forum projektanta klas programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner).

## <a name="limitations-for-c-code-elements"></a>Ograniczenia dla elementów kodu języka C++

- Po załadowaniu projektu C++ **projektant klasy** działa w sposób tylko do odczytu. Można zmienić diagram klasy, ale nie można zapisać zmiany z diagramu klasy z powrotem do kodu źródłowego.

- **Projektant klas** obsługuje tylko natywną semantykę języka C++. Dla projektów języka C++, które są kompilowane do kodu zarządzanego, **Projektant klas** będzie wizualizować tylko elementy kodu, które są typami macierzystymi. W związku z tym można dodać diagram klasy do projektu, ale **Projektant klas** `IsManaged` nie pozwoli `true` na wizualizację elementów, w których właściwość jest ustawiona na (czyli typy wartości i typy odwołań).

- W przypadku projektów języka C++ **Projektant klas** odczytuje tylko definicję typu. Załóżmy na przykład, że typ w pliku nagłówka (.h) i zdefiniować jego członków w pliku implementacji (.cpp). Jeśli wywołasz "Wyświetl diagram klas" w pliku implementacji (.cpp), **Projektant klas** nie wyświetla niczego. Innym przykładem, jeśli wywołasz "Zobacz diagram klas" w pliku `#include` .cpp, który używa instrukcji do dołączania innych plików, ale nie zawiera żadnych rzeczywistych definicji klas, **Projektant klas** ponownie nic nie wyświetla.

- Pliki IDL (idl), które definiują interfejsy COM i biblioteki typów, nie są wyświetlane na diagramach, chyba że są kompilowane do natywnego kodu C++.

- **Projektant klas** nie obsługuje globalnych funkcji i zmiennych.

- **Projektant klas** nie obsługuje związków. Jest to specjalny typ klasy, w którym przydzielona pamięć jest tylko ilość niezbędna dla największego elementu członkowskiego danych unii.

- **Projektant klas** nie wyświetla podstawowych `int` `char`typów danych, takich jak i .

- **Projektant klas** nie wyświetla typów, które są zdefiniowane poza bieżącym projektem, jeśli projekt nie ma poprawnych odwołań do tych typów.

- **Projektant klas** może wyświetlać typy zagnieżdżone, ale nie relacje między typem zagnieżdżonego a innymi typami.

- **Projektant klas** nie może wyświetlać typów, które są nieważne lub które wynikają z typu void.

## <a name="see-also"></a>Zobacz też

- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
- [Dodatkowe informacje na temat błędów Projektanta klas](additional-information-about-errors.md)
- [Klasy języka C++ w projektancie klas](visual-cpp-classes.md)
- [Struktury języka C++ w projektancie klas](visual-cpp-structures.md)
- [Wyliczenia języka C++ w projektancie klas](visual-cpp-enumerations.md)
- [Definicje c++ w projektancie klas](visual-cpp-typedefs.md)
