---
title: Wstaw komentarze dokumentacji XML
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 085e2fe029daf246f6883e6856ddff6a9bacccdc
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929144"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Instrukcje: Wstawianie komentarzy XML do generowania dokumentacji

Program Visual Studio może pomóc dokumentów elementów kodu, takich jak klasy i metody, przez automatyczne generowanie standardowych strukturę komentarzy dokumentacji XML. W czasie kompilacji można wygenerować pliku XML, który zawiera komentarze dokumentacji.

> [!TIP]
> Aby uzyskać informacji o konfigurowaniu nazwę i lokalizację w wygenerowanym pliku XML, zobacz [dokumentowanie kodu przy użyciu komentarzy XML (C# przewodnik)](/dotnet/csharp/codedoc).

Plik XML generowanych przez kompilator mogą być dystrybuowane wraz z Twojego zestawu platformy .NET tak, aby program Visual Studio i innych środowisk IDE umożliwia IntelliSense pokazywanie szybkich informacji na temat typów i elementów członkowskich. Ponadto plik XML mogą być uruchamiane za pomocą takich narzędzi [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) do generowania dokumentacja interfejsu API witryn sieci Web.

> [!NOTE]
> **Wstaw komentarz** polecenia, które automatycznie wstawia komentarze dokumentacji XML jest dostępna w [ C# ](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) i [języka Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Jednak można wstawiać ręcznie [komentarze dokumentacji XML w języku C++](/cpp/ide/xml-documentation-visual-cpp) pliki i nadal Generuj pliki dokumentacji XML w czasie kompilacji.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Aby wstawić komentarze XML dla elementu kodu

1. Umieść kursor nad elementem, aby dokumentu, na przykład metoda tekstu.

1. Wykonaj jedną z następujących czynności:

   - Typ `///` w C#, lub `'''` w języku Visual Basic

   - Z **Edytuj** menu, wybierz **IntelliSense** > **Wstaw komentarz**

   - Kliknij prawym przyciskiem myszy lub kontekst menu lub po prostu nad element kodu, wybierz **fragment** > **Wstaw komentarz**

   Szablon XML natychmiast jest generowany powyżej elementu kodu. Na przykład, gdy Dodawanie komentarza do metody, generuje ona **\<podsumowania\>** elementu **\<param\>** element dla każdego parametru i **\<zwraca\>** element do dokumentu wartość zwracaną.

   ![Szablon komentarza XML-C#](media/doc-preview-cs.png)

   ![Szablon komentarza XML - Visual Basic](media/doc-preview-vb.png)

1. Wprowadź opis każdego elementu XML do dokumentów w pełni element kodu.

   ![Komentarz ukończone](media/doc-result-cs.png)

> [!NOTE]
> Brak [opcji](../../ide/reference/options-text-editor-csharp-advanced.md) do komentarzy dokumentacji XML Przełącz po wpisaniu `///` w C# lub `'''` języka Visual Basic. Na pasku menu wybierz **narzędzia** > **opcje** otworzyć **opcje** okno dialogowe. Następnie przejdź do **edytora tekstów**  >  **C#** lub **podstawowe** > **zaawansowane**. W **pomocy edytora** sekcji, poszukaj **Generuj komentarze dokumentacji XML** opcji.

## <a name="see-also"></a>Zobacz także

- [Komentarze dokumentacji XML (C# Programming Guide)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu przy użyciu komentarzy XML (C# przewodnik)](/dotnet/csharp/codedoc)
- [Instrukcje: Tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Komentarze języka C++](/cpp/cpp/comments-cpp)
- [Dokumentacja XML (C++)](/cpp/ide/xml-documentation-visual-cpp)
- [Generowanie kodu](../code-generation-in-visual-studio.md)