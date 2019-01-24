---
title: Praca z kodem Visual C++ (Projektant klas) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90f0c73abb33a2da9c2735bcbc16b5559437bc65
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54765015"
---
# <a name="working-with-visual-c-code-class-designer"></a>Praca z kodem Visual C++ (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klasy Wyświetla powierzchni projektowej o nazwie *diagram klas* zapewniający wizualnej reprezentacji elementów kodu w projekcie. Diagramy klas można użyć do projektowania i wizualizowanie klas i innych typów w projekcie.  
  
 Projektant klas obsługuje następujące elementy kodu C++:  
  
-   Klasy (przypomina kształt klasy zarządzanej, z tą różnicą, że może mieć wiele relacji dziedziczenia)  
  
-   Klasa anonimowa (wyświetla wygenerowaną nazwę widoku klasy dla typu anonimowego)  
  
-   Klasa szablonu  
  
-   Struct  
  
-   Wyliczenie  
  
-   Makra (wyświetla przetworzone po widoku makro)  
  
-   Element TypeDef  
  
> [!NOTE]
>  Nie jest taka sama jak diagram klas UML, który można utworzyć w projekcie modelowania. Aby uzyskać więcej informacji, zobacz [diagramów klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md).  
  
## <a name="troubleshooting-type-resolution-and-display-issues"></a>Rozpoznawanie typu do rozwiązywania problemów i problemów z wyświetlaniem  
  
### <a name="location-of-source-files"></a>Lokalizację plików źródłowych  
 Projektant klas nie zachować informacje o lokalizacji plików źródłowych. W związku z tym jeśli modyfikujesz do struktury projektu, lub przenoszenia plików źródłowych w projekcie, Projektant klas może spowodować utratę śledzenie typ (szczególnie typ źródłowy element typedef, bazowe klasy lub typu powiązania). Może zostać wyświetlony błąd taki jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij kod źródłowy zmodyfikowany lub przenoszone do diagramu klas, aby ją wyświetlić ją ponownie.  
  
### <a name="update-and-performance-issues"></a>Aktualizacja i problemy z wydajnością  
 Dla projektów Visual C++ może potrwać 30 do 60 sekund, aby zmiany w pliku źródłowym, być wyświetlane na diagramie klasy. To opóźnienie może również spowodować projektanta klas wygenerować błąd **nie znaleziono żadnych typów w zaznaczeniu**. Jeśli zostanie wyświetlony błąd taki jak to, kliknij przycisk **anulować** komunikat o błędzie i zaczekaj, aż element kodu, które pojawią się w widoku klas. Po wykonaniu tej czynności, Projektant klas powinien móc wyświetlić tego typu.  
  
 Jeśli diagram klas nie aktualizuje się zmiany wprowadzone w kodzie, konieczne może być zamknij diagram i otwórz go ponownie.  
  
### <a name="type-resolution-issues"></a>Typ rozwiązywania problemów  
 Projektant klas może nie być w stanie rozpoznać typów z następujących powodów:  
  
- Typ jest w projekcie lub w zestawie, który nie odwołuje się projekt, który zawiera diagram klas. Aby rozwiązać ten problem, Dodaj odwołanie do projektu lub zestawu, który zawiera tekst. Aby uzyskać więcej informacji, zobacz [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](http://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
- Typ nie jest w niewłaściwym zakresie, więc Projektant klas nie może go zlokalizować. Upewnij się, że kod nie jest Brak `using`, `imports`, lub `#include` instrukcji. Upewnij się, że nie zostały przeniesione typu (lub powiązanego typu) z przestrzeni nazw, w którym został on pierwotnie znajduje się również.  
  
- Typ nie istnieje lub została ujęta w komentarz. Aby rozwiązać ten problem, upewnij się, że nie oznaczone jako komentarz lub usunięty typ.  
  
- Typ znajduje się w bibliotece odwołuje się #import — dyrektywa. Możliwym obejściem jest ręcznie dodać wygenerowanego kodu (plik .tlh) # dyrektywy include w pliku nagłówka.  
  
  Ten błąd jest najbardziej prawdopodobne zobaczyć problemu rozpoznawania typu jest **nie można odnaleźć kodu dla jednego lub więcej kształtów na diagramie klasy "\<element >"**. Ten komunikat o błędzie nie musi oznaczać, że Twój kod jest błąd. Wskazuje on, że tego projektanta klas nie może wyświetlić kodu. Spróbuj wykonać następujące działania.  
  
- Upewnij się, że typ istnieje. Upewnij się, że nie przypadkowo oznaczone jako komentarz lub usunięty kodu źródłowego.  
  
- Upewnij się, że Projektant klasy obsługuje typ, który wprowadzono. Zobacz [ograniczenia dla elementów kodu w języku C++](#limitations).  
  
- Spróbuj rozwiązać tego typu. Typ może być w projekcie lub w zestawie, który nie odwołuje się projekt, który zawiera diagram klas. Aby rozwiązać ten problem, Dodaj odwołanie do projektu lub zestawu, który zawiera tekst. Aby uzyskać więcej informacji, zobacz [NIB jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](http://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
- Upewnij się, że typ jest w niewłaściwym zakresie tak, aby zlokalizować projektanta klas. Upewnij się, że kod nie jest Brak `using`, `imports`, lub `#include` instrukcji. Upewnij się, że nie zostały przeniesione typu (lub powiązanego typu) z przestrzeni nazw, w którym został on pierwotnie znajduje się również.  
  
### <a name="troubleshooting-other-error-messages"></a>Rozwiązywanie problemów z inne komunikaty o błędach  
 Pomoc dotyczącą rozwiązywania problemów z błędów i ostrzeżeń można znaleźć w publiczne fora Microsoft Developer Network (MSDN). Zobacz [Forum projektanta klas programu Visual Studio](http://go.microsoft.com/fwlink/?linkid=160754).  
  
##  <a name="limitations"></a> Ograniczenia dotyczące elementów kodu w języku C++  
  
-   Gdy projekt Visual C++ jest ładowany, funkcje projektanta klas w sposób tylko do odczytu. Można zmienić na diagramie klasy, ale nie można zapisać zmian z diagramu klasy do kodu źródłowego.  
  
-   Projektant klasy obsługuje tylko natywny semantyki C++. Dla projektów Visual C++, które są kompilowane do kodu zarządzanego Projektant klas tylko wizualizować elementy kodu, które są typami natywnymi. W związku z tym, można dodać diagram klas do projektu, ale Projektant klas nie zezwoli na wizualizowanie elementów, w którym `IsManaged` właściwość jest ustawiona na `true` (oznacza to typy wartości i typy referencyjne).  
  
-   Dla projektów Visual C++ Projektant klas odczytuje tylko definicji typu. Załóżmy na przykład, możesz zdefiniować typu w pliku nagłówka (.h) i zdefiniować jej elementów członkowskich w pliku implementacji (.cpp). Jeśli wywołujesz "Pokaż Diagram klas" w pliku implementacji (.cpp), Projektant klas nie powoduje wyświetlenia żadnych danych Inny przykład, jeśli wywołujesz "Pokaż Diagram klas" w pliku .cpp, który używa `#include` instrukcję, aby dołączyć inne pliki, ale nie zawiera żadnych definicji klas rzeczywiste, nic nie wyświetla ponownie projektanta klas.  
  
-   Pliki IDL (.idl), które definiowanie interfejsów COM i bibliotek typów, nie są wyświetlane na diagramach, chyba że są one kompilowane do kodu natywnego języka C++.  
  
-   Projektant klas nie obsługuje funkcje i zmienne globalne.  
  
-   Projektant klas nie obsługuje Unii. Jest to specjalny typ klasy, w którym pamięci przydzielonej jest niezbędne dla Unii zajmuje największy element członkowski danych kwoty.  
  
-   Projektant klas nie są wyświetlane typy danych podstawowych takich jak `int` i `char`.  
  
-   Projektant klas nie są wyświetlane typy, które są zdefiniowane poza bieżącym projekcie, jeśli projekt nie ma poprawne odwołania do tych typów.  
  
-   Projektant klas umożliwia wyświetlanie typów zagnieżdżonych, ale nie relacje między typem zagnieżdżonym i innych typów.  
  
-   Projektant klas nie może wyświetlić typy, które są nieważne lub który pochodzi od typu void.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie i wyświetlanie klas i typów](../ide/designing-and-viewing-classes-and-types.md)   
 [Praca z klasami i innymi typami (Projektant klas)](../ide/working-with-classes-and-other-types-class-designer.md)   
 [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md)   
 [Projektowanie klas i typów (Projektant klas)](../ide/designing-classes-and-types-class-designer.md)   
 [Dodatkowe informacje na temat błędów projektanta klas](../ide/additional-information-about-class-designer-errors.md)   
 [Klasy Visual C++ w Projektancie klas](../ide/visual-cpp-classes-in-class-designer.md)   
 [Struktury Visual C++ w Projektancie klas](../ide/visual-cpp-structures-in-class-designer.md)   
 [Wyliczenia Visual C++ w Projektancie klas](../ide/visual-cpp-enumerations-in-class-designer.md)   
 [Definicje typów języka Visual C++ w Projektancie klas](../ide/visual-cpp-typedefs-in-class-designer.md)
