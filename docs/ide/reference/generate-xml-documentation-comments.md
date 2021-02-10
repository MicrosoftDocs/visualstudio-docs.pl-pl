---
title: Wstawianie komentarzy dokumentacji XML
description: Dowiedz się, jak wstawiać komentarze dokumentacji XML w kodzie, którego można użyć do utworzenia pliku XML generowanego przez kompilator do dystrybucji wraz z zestawem platformy .NET.
ms.custom: SEO-VS-2020
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2c203d9a445d9426a8079801a856e20f7be82229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946569"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Instrukcje: wstawianie komentarzy XML do generacji dokumentacji

Program Visual Studio może pomóc w udokumentowaniu elementów kodu, takich jak klasy i metody, przez automatyczne wygenerowanie standardowej struktury komentarza dokumentacji XML. W czasie kompilacji można wygenerować plik XML zawierający komentarze dokumentacji.

> [!TIP]
> Aby uzyskać informacje o konfigurowaniu nazwy i lokalizacji wygenerowanego pliku XML, zobacz [dokumentowanie kodu za pomocą komentarzy XML (Przewodnik C#)](/dotnet/csharp/codedoc).

Plik XML wygenerowany przez kompilator może być dystrybuowany wraz z zestawem .NET, dzięki czemu program Visual Studio i inne środowisk IDE mogą używać funkcji IntelliSense do wyświetlania szybkich informacji na temat typów i elementów członkowskich. Ponadto plik XML można uruchomić za pomocą narzędzi, takich jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) , aby generować witryny sieci Web dokumentacji interfejsu API.

> [!NOTE]
> Polecenie **Wstaw komentarz** , które automatycznie wstawia komentarze dokumentacji XML, jest dostępne w [języku C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) i [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Można jednak ręcznie wstawiać [Komentarze dokumentacji XML w plikach języka C++](/cpp/build/reference/xml-documentation-visual-cpp) i nadal generować pliki dokumentacji XML w czasie kompilacji.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Aby wstawić Komentarze XML dla elementu kodu

1. Umieść kursor tekstu powyżej elementu, który ma być dokumentem, na przykład metodę.

2. Wykonaj jedną z następujących czynności:

   - Wpisz `///` w języku C# lub `'''` w Visual Basic

   - Z menu **Edycja** wybierz pozycję **IntelliSense**  >  **Wstaw komentarz**

   - W prawym przyciskiem myszy lub w menu kontekstowym lub tuż nad elementem **kodu wybierz Wstaw**  >  **komentarz**

   Szablon XML jest natychmiast generowany powyżej elementu Code. Na przykład podczas dodawania komentarza do metody generuje on **\<summary\>** element, **\<param\>** element dla każdego parametru i **\<returns\>** element, aby udokumentować wartość zwracaną.

   ![Szablon komentarza XML-C #](media/doc-preview-cs.png)

   ![Szablon komentarza XML — Visual Basic](media/doc-preview-vb.png)

3. Wprowadź opisy dla każdego elementu XML, aby w pełni udokumentować element kodu.

   ![Zrzut ekranu przedstawiający ukończony komentarz.](media/doc-result-cs.png)

Możesz użyć stylów w komentarzach XML, które będą renderowane w szybkich informacjach, gdy wskaźnik myszy znajduje się nad elementem. Te style obejmują: kursywę, pogrubienie, punktor i link do kliknięcia.

   ![Zrzut ekranu przedstawiający ukończony komentarz ze znacznikami stylu dla kursywy, pogrubienia, punktora i linku do kliknięcia.](media/doc-style-cs.png) 

> [!NOTE]
> Istnieje [możliwość](../../ide/reference/options-text-editor-csharp-advanced.md) przełączania komentarzy dokumentacji XML po wpisaniu kodu `///` w języku C# lub `'''` Visual Basic. Na pasku menu wybierz **Narzędzia**  >  **Opcje** , aby otworzyć okno dialogowe **Opcje** . Następnie przejdź do **edytora tekstu**  >  **C#** lub **Basic**  >  **Advanced**. W sekcji **Pomoc edytora** Znajdź opcję **Generuj komentarze dokumentacji XML** .

## <a name="see-also"></a>Zobacz też

- [Komentarze dokumentacji XML (Przewodnik programowania w języku C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarzy XML (Przewodnik C#)](/dotnet/csharp/codedoc)
- [Instrukcje: tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Komentarze języka C++](/cpp/cpp/comments-cpp)
- [Dokumentacja XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generowanie kodu](../code-generation-in-visual-studio.md)
