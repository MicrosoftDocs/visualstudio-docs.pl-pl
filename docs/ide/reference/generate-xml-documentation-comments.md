---
title: Wstawianie komentarzy do dokumentacji XML
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77706400"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Jak: Wstawianie komentarzy XML do generowania dokumentacji

Visual Studio może pomóc w dokumentowaniu elementów kodu, takich jak klasy i metody, automatycznie generując standardową strukturę komentarzy dokumentacji XML. W czasie kompilacji można wygenerować plik XML, który zawiera komentarze dokumentacji.

> [!TIP]
> Aby uzyskać informacje dotyczące konfigurowania nazwy i lokalizacji wygenerowanego pliku XML, zobacz [Dokumentowanie kodu za pomocą komentarzy XML (Przewodnik języka C#).](/dotnet/csharp/codedoc)

Wygenerowany przez kompilator plik XML może być dystrybuowany wraz z zestawem platformy .NET, dzięki czemu program Visual Studio i inne identyfikatory mogą używać technologii IntelliSense do pokazania szybkich informacji o typach i członkach. Ponadto plik XML można uruchomić za pomocą narzędzi, takich jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) do generowania stron internetowych odniesienia interfejsu API.

> [!NOTE]
> Polecenie **Wstaw komentarz,** które automatycznie wstawia komentarze do dokumentacji XML, jest dostępne w [językach C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) i [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Można jednak ręcznie [wstawić komentarze dokumentacji XML w](/cpp/build/reference/xml-documentation-visual-cpp) plikach języka C++ i nadal generować pliki dokumentacji XML w czasie kompilacji.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Aby wstawić komentarze XML dla elementu kodu

1. Umieść kursor tekstowy nad elementem, który chcesz udokumentować, na przykład metodą.

2. Wykonaj jedną z następujących czynności:

   - Wpisz `///` w języku `'''` C#lub visual basic

   - Z menu **Edycja** wybierz polecenie **IntelliSense** > **Insert Comment**

   - Z menu po kliknięciu prawym przyciskiem myszy lub w menu kontekstowym na elemencie kodu lub tuż nad nim wybierz pozycję > **Urywek Wstaw komentarz** **Snippet**

   Szablon XML jest natychmiast generowany powyżej elementu kodu. Na przykład podczas komentowania metody generuje element ** \<podsumowania,\> ** element ** \<param\> ** dla każdego parametru ** \<\> ** i zwraca element do dokumentu wartości zwracanej.

   ![Szablon komentarza XML - C #](media/doc-preview-cs.png)

   ![Szablon komentarza XML — Visual Basic](media/doc-preview-vb.png)

3. Wprowadź opisy dla każdego elementu XML, aby w pełni udokumentować element kodu.

   ![Wypełniony komentarz](media/doc-result-cs.png)

Style w komentarzach XML, które będą renderowane w szybkich informacjach po najechaniu kursorem na element. Style te obejmują: kursywę, pogrubienie, punktory i klikalne łącze.

   ![Wypełniony komentarz](media/doc-style-cs.png) 

> [!NOTE]
> Istnieje [opcja](../../ide/reference/options-text-editor-csharp-advanced.md) przełączania komentarzy dokumentacji XML `///` po wpisaniu `'''` w języku C# lub Visual Basic. Na pasku menu wybierz pozycję**Opcje** **narzędzi,** > aby otworzyć okno dialogowe **Opcje.** Następnie przejdź do **edytora** > tekstu**C#** lub **Basic** > **Advanced**. W sekcji **Pomoc edytora** poszukaj opcji **Generuj komentarze do dokumentacji XML.**

## <a name="see-also"></a>Zobacz też

- [Komentarze do dokumentacji XML (Przewodnik programowania języka C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarzy XML (Przewodnik języka C#)](/dotnet/csharp/codedoc)
- [Jak: Tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Komentarze do języka C++](/cpp/cpp/comments-cpp)
- [Dokumentacja XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generowanie kodu](../code-generation-in-visual-studio.md)
