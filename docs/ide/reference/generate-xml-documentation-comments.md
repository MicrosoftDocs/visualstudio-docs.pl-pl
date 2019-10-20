---
title: Wstawianie komentarzy dokumentacji XML
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e9153677b833a89a236923a971b511548b064142
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668611"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Instrukcje: wstawianie komentarzy XML do generacji dokumentacji

Program Visual Studio może pomóc w udokumentowaniu elementów kodu, takich jak klasy i metody, przez automatyczne wygenerowanie standardowej struktury komentarza dokumentacji XML. W czasie kompilacji można wygenerować plik XML zawierający komentarze dokumentacji.

> [!TIP]
> Aby uzyskać informacje o konfigurowaniu nazwy i lokalizacji wygenerowanego pliku XML, zobacz [dokumentowanie kodu za pomocą komentarzy XMLC# (Przewodnik)](/dotnet/csharp/codedoc).

Plik XML wygenerowany przez kompilator może być dystrybuowany wraz z zestawem .NET, dzięki czemu program Visual Studio i inne środowisk IDE mogą używać funkcji IntelliSense do wyświetlania szybkich informacji na temat typów i elementów członkowskich. Ponadto plik XML można uruchomić za pomocą narzędzi, takich jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) , aby generować witryny sieci Web dokumentacji interfejsu API.

> [!NOTE]
> Polecenie **Wstaw komentarz** , które automatycznie wstawia komentarze dokumentacji XML, jest dostępne [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) w i [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Można jednak ręcznie wstawiać [Komentarze do dokumentacji XML w C++ ](/cpp/build/reference/xml-documentation-visual-cpp) plikach i nadal generować pliki dokumentacji XML w czasie kompilacji.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Aby wstawić Komentarze XML dla elementu kodu

1. Umieść kursor tekstu powyżej elementu, który ma być dokumentem, na przykład metodę.

1. Wykonaj jedną z następujących czynności:

   - Wpisz `///` in C#lub `'''` w Visual Basic

   - Z menu **Edycja** wybierz pozycję **IntelliSense**  > **Wstaw komentarz**

   - Z menu kontekstowego lub kliknięcia prawym przyciskiem myszy lub tuż nad elementem kodu wybierz **wstawka**  > **Wstaw komentarz**

   Szablon XML jest natychmiast generowany powyżej elementu Code. Na przykład podczas dodawania komentarza do metody generuje element **\<summary \>** , **\<param elementu \>** dla każdego parametru oraz **\<returns \>** elementu, aby udokumentować wartość zwracaną.

   ![Szablon komentarza XML —C#](media/doc-preview-cs.png)

   ![Szablon komentarza XML — Visual Basic](media/doc-preview-vb.png)

1. Wprowadź opisy dla każdego elementu XML, aby w pełni udokumentować element kodu.

   ![Ukończony komentarz](media/doc-result-cs.png)

> [!NOTE]
> Istnieje [możliwość](../../ide/reference/options-text-editor-csharp-advanced.md) przełączania komentarzy dokumentacji XML po wpisaniu `///` w programie C# lub `'''` Visual Basic. Na pasku menu wybierz polecenie **narzędzia**  > **Opcje** , aby otworzyć okno dialogowe **Opcje** . Następnie przejdź do **edytora tekstu**  > **C#** lub **Basic**  > **Advanced**. W sekcji **Pomoc edytora** Znajdź opcję **Generuj komentarze dokumentacji XML** .

## <a name="see-also"></a>Zobacz także

- [Komentarze dokumentacji XML (C# Przewodnik programowania)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarzy XML (C# przewodnik)](/dotnet/csharp/codedoc)
- [Instrukcje: tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++Komentarz](/cpp/cpp/comments-cpp)
- [Dokumentacja XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generowanie kodu](../code-generation-in-visual-studio.md)