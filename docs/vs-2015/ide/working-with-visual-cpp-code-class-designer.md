---
title: Praca z kodem C++ wizualizacji (Projektant klas) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 020535ac73c48be74e56100c7b6f9c49b69e50dc
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851312"
---
# <a name="working-with-visual-c-code-class-designer"></a>Praca z kodem Visual C++ (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klas wyświetla wizualną powierzchnię projektową o nazwie *Diagram klas* , który zapewnia wizualną reprezentację elementów kodu w projekcie. Diagramów klas można używać do projektowania i wizualizacji klas i innych typów w projekcie.

 Projektant klas obsługuje następujące C++ elementy kodu:

- Klasa (przypomina kształt klasy zarządzanej, z tą różnicą, że może mieć wiele relacji dziedziczenia)

- Klasa anonimowa (wyświetla nazwę wygenerowaną Widok klasy dla typu anonimowego)

- Klasa szablonu

- Struct

- Wyliczenie

- Makro (wyświetla widok po przetworzeniu makra)

- Własne

> [!NOTE]
> To nie jest taka sama jak Diagram klas UML, który można utworzyć w projekcie modelowania. Aby uzyskać więcej informacji, zobacz [diagramy klas UML: Reference](../modeling/uml-class-diagrams-reference.md).

## <a name="troubleshooting-type-resolution-and-display-issues"></a>Rozwiązywanie problemów z rozpoznawaniem i wyświetlaniem typów

### <a name="location-of-source-files"></a>Lokalizacja plików źródłowych
 Projektant klas nie śledzi lokalizacji plików źródłowych. W związku z tym, jeśli zmodyfikujesz strukturę projektu lub przeniesiesz pliki źródłowe w projekcie, Projektant klas może utracić śledzenie typu (szczególnie typ źródłowy typedef, klasy bazowe lub typy skojarzeń). Może zostać wyświetlony błąd, taki jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij ponownie zmodyfikowany lub zlokalizowany kod źródłowy do diagramu klas, aby go wyświetlić.

### <a name="update-and-performance-issues"></a>Problemy z aktualizacją i wydajnością
 W przypadku C++ projektów wizualnych może upłynąć od 30 do 60 sekund, aby zmiana w pliku źródłowym była wyświetlana na diagramie klas. To opóźnienie może być również przyczyną Projektant klas zgłoszenia błędu **nie znaleziono żadnych typów w zaznaczeniu**. Jeśli wystąpi błąd, na przykład, kliknij przycisk **Anuluj** w komunikacie o błędzie i poczekaj na wyświetlenie elementu kodu w widok klasy. Po wykonaniu tej czynności Projektant klas powinna być w stanie wyświetlić typ.

 Jeśli Diagram klas nie jest aktualizowany ze zmianami wprowadzonymi w kodzie, może być konieczne zamknięcie diagramu i otwarcie go ponownie.

### <a name="type-resolution-issues"></a>Problemy z rozpoznawaniem typów
 Projektant klas może nie być w stanie rozpoznać typów z następujących powodów:

- Typ znajduje się w projekcie lub zestawie, do którego nie odwołuje się projekt, który zawiera Diagram klas. Aby naprawić ten błąd, Dodaj odwołanie do projektu lub zestawu, który zawiera typ. Aby uzyskać więcej informacji, zobacz [NIB How to: Dodawanie lub usuwanie odwołań za pomocą okna dialogowego Dodawanie odwołania](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Typ nie znajduje się w poprawnym zakresie, więc nie można go zlokalizować Projektant klas. Upewnij się, że w kodzie nie brakuje instrukcji `using`, `imports`lub `#include`. Upewnij się również, że typ (lub powiązany Typ) nie został przeniesiony poza przestrzeń nazw, w której pierwotnie znajdowały się.

- Typ nie istnieje (lub został oznaczony jako komentarz). Aby naprawić ten błąd, upewnij się, że nie ma komentarza lub nie został usunięty.

- Typ znajduje się w bibliotece, do której odwołuje się dyrektywa #import. Możliwe obejście to ręczne dodanie wygenerowanego kodu (plik. tlh) do dyrektywy #include do pliku nagłówkowego.

  Błąd, który najprawdopodobniej widzisz w przypadku problemu z rozpoznawaniem typów, **nie można znaleźć kodu dla co najmniej jednego kształtu na diagramie klas "\<elementu >"** . Ten komunikat o błędzie nie musi wskazywać, że kod jest w błędzie. Wskazuje tylko, że Projektant klas nie może wyświetlić Twojego kodu. Wypróbuj następujące miary.

- Upewnij się, że typ istnieje. Upewnij się, że nie przypadkowo usunięto komentarz do kodu źródłowego lub został on usunięty.

- Upewnij się, że Projektant klas obsługuje wprowadzony typ. Zobacz [ograniczenia dotyczące C++ elementów kodu](#limitations).

- Spróbuj rozpoznać typ. Typ może należeć do projektu lub zestawu, który nie jest przywoływany z projektu, który zawiera Diagram klas. Aby naprawić ten błąd, Dodaj odwołanie do projektu lub zestawu, który zawiera typ. Aby uzyskać więcej informacji, zobacz [NIB How to: Dodawanie lub usuwanie odwołań za pomocą okna dialogowego Dodawanie odwołania](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Upewnij się, że typ znajduje się w poprawnym zakresie, aby można było go zlokalizować Projektant klas. Upewnij się, że w kodzie nie brakuje instrukcji `using`, `imports`lub `#include`. Upewnij się również, że typ (lub powiązany Typ) nie został przeniesiony poza przestrzeń nazw, w której pierwotnie znajdowały się.

### <a name="troubleshooting-other-error-messages"></a>Rozwiązywanie problemów z innymi komunikatami o błędach
 Pomoc dotyczącą rozwiązywania problemów i ostrzeżeń można znaleźć w publicznych forach Microsoft Developer Network (MSDN). Zobacz [Forum programu Visual Studio Projektant klas](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1).

## <a name="limitations"></a>Ograniczenia dotyczące C++ elementów kodu

- Po załadowaniu C++ projektu Visual Projektant klas funkcje w trybie tylko do odczytu. Można zmienić Diagram klas, ale nie można zapisać zmian z diagramu klas z powrotem do kodu źródłowego.

- Projektant klas obsługuje tylko semantykę natywną C++ . W przypadku C++ projektów wizualnych, które są kompilowane w kodzie zarządzanym, Projektant klas będzie wizualizować tylko elementy kodu, które są typami natywnymi. W związku z tym, można dodać Diagram klas do projektu, ale Projektant klas nie pozwoli na wizualizację elementów, w których właściwość `IsManaged` jest ustawiona na `true` (to jest, typy wartości i typy odwołań).

- W przypadku C++ projektów wizualnych Projektant klas odczytuje tylko definicję typu. Załóżmy na przykład, że zdefiniujesz typ w pliku nagłówka (. h) i zdefiniujesz jego składowe w pliku implementacji (. cpp). Jeśli wywołasz polecenie "Wyświetl Diagram klas" w pliku implementacji (. cpp), Projektant klas nie wyświetla niczego. W innym przykładzie, jeśli wywołasz "Widok diagramu klas" w pliku. cpp, który używa instrukcji `#include`, aby uwzględnić inne pliki, ale nie zawiera żadnych rzeczywistych definicji klas, Projektant klas ponownie wyświetli niczego.

- Pliki IDL (. idl), które definiują interfejsy COM i biblioteki typów, nie są wyświetlane w diagramach, chyba że są C++ kompilowane do kodu natywnego.

- Projektant klas nie obsługuje globalnych funkcji i zmiennych.

- Projektant klas nie obsługuje Unii. Jest to specjalny typ klasy, w której przydzielono pamięć jest tylko ilością niezbędną dla największego elementu członkowskiego danych Unii.

- W Projektant klas nie są wyświetlane podstawowe typy danych, takie jak `int` i `char`.

- Projektant klas nie wyświetla typów, które są zdefiniowane poza bieżącym projektem, jeśli projekt nie ma poprawnych odwołań do tych typów.

- Projektant klas mogą wyświetlać typy zagnieżdżone, ale nie relacje między typem zagnieżdżonym i innymi typami.

- Projektant klas nie może wyświetlić typów, które są puste lub które pochodzą od typu void.

## <a name="see-also"></a>Zobacz też
 [Projektowanie i wyświetlanie klas i typów](../ide/designing-and-viewing-classes-and-types.md) [pracujących z klasami i innymi typami (Projektant klas)](../ide/working-with-classes-and-other-types-class-designer.md) [pracujących z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md) [projektowanie klas i typów (Projektant klas)](../ide/designing-classes-and-types-class-designer.md) [dodatkowe informacje na temat błędów Projektant klas](../ide/additional-information-about-class-designer-errors.md) [ C++ klas wizualnych w](../ide/visual-cpp-classes-in-class-designer.md) Projektant klas [ C++ strukturach](../ide/visual-cpp-structures-in-class-designer.md) [ C++ ](../ide/visual-cpp-enumerations-in-class-designer.md) wizualizacji w programie Projektant klas [Visual C++ Typedefs](../ide/visual-cpp-typedefs-in-class-designer.md) w Projektant klas
