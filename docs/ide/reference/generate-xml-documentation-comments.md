---
title: Wstaw komentarze dokumentacji XML
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706400"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Porady: wstawianie komentarzy XML do generowania dokumentacji

Program Visual Studio może pomóc dokumentów elementów kodu, takich jak klasy i metody, przez automatyczne generowanie standardowych strukturę komentarzy dokumentacji XML. W czasie kompilacji można wygenerować pliku XML, który zawiera komentarze dokumentacji.

> [!TIP]
> Aby uzyskać informacje o konfigurowaniu nazwy i lokalizacji wygenerowanego pliku XML, zobacz [dokumentowanie kodu za pomocą komentarzy XMLC# (Przewodnik)](/dotnet/csharp/codedoc).

Plik XML generowanych przez kompilator mogą być dystrybuowane wraz z Twojego zestawu platformy .NET tak, aby program Visual Studio i innych środowisk IDE umożliwia IntelliSense pokazywanie szybkich informacji na temat typów i elementów członkowskich. Ponadto plik XML można uruchomić za pomocą narzędzi, takich jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) , aby generować witryny sieci Web dokumentacji interfejsu API.

> [!NOTE]
> Polecenie **Wstaw komentarz** , które automatycznie wstawia komentarze dokumentacji XML, jest dostępne [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) w i [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Można jednak ręcznie wstawiać [Komentarze do dokumentacji XML w C++ ](/cpp/build/reference/xml-documentation-visual-cpp) plikach i nadal generować pliki dokumentacji XML w czasie kompilacji.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Aby wstawić komentarze XML dla elementu kodu

1. Umieść kursor nad elementem, aby dokumentu, na przykład metoda tekstu.

2. Wykonaj jedną z następujących czynności:

   - Wpisz `///` in C#lub `'''` w Visual Basic

   - Z menu **Edycja** wybierz pozycję **IntelliSense** > **Wstaw komentarz**

   - Z menu kontekstowego lub kliknięcia prawym przyciskiem myszy lub tuż nad elementem kodu wybierz **wstawka** > **Wstaw komentarz**

   Szablon XML natychmiast jest generowany powyżej elementu kodu. Na przykład podczas dodawania komentarza do metody generuje element **\<summary\>** , element **\<param\>** dla każdego parametru, a **\<zwraca element\>** , aby udokumentować wartość zwracaną.

   ![Szablon komentarza XML-C#](media/doc-preview-cs.png)

   ![Szablon komentarza XML - Visual Basic](media/doc-preview-vb.png)

3. Wprowadź opis każdego elementu XML do dokumentów w pełni element kodu.

   ![Komentarz ukończone](media/doc-result-cs.png)

Możesz użyć stylów w komentarzach XML, które będą renderowane w szybkich informacjach, gdy wskaźnik myszy znajduje się nad elementem. Te style obejmują: kursywę, pogrubienie, punktor i link do kliknięcia.

   ![Komentarz ukończone](media/doc-style-cs.png) 

> [!NOTE]
> Istnieje [możliwość](../../ide/reference/options-text-editor-csharp-advanced.md) przełączania komentarzy dokumentacji XML po wpisaniu `///` w programie C# lub `'''` Visual Basic. Na pasku menu wybierz polecenie **narzędzia** > **Opcje** , aby otworzyć okno dialogowe **Opcje** . Następnie przejdź do **edytora tekstu** > **C#** lub **Basic** > **Advanced**. W sekcji **Pomoc edytora** Znajdź opcję **Generuj komentarze dokumentacji XML** .

## <a name="see-also"></a>Zobacz też

- [Komentarze dokumentacji XML (C# Przewodnik programowania)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarzy XML (C# przewodnik)](/dotnet/csharp/codedoc)
- [Instrukcje: tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++Komentarz](/cpp/cpp/comments-cpp)
- [Dokumentacja XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generowanie kodu](../code-generation-in-visual-studio.md)
