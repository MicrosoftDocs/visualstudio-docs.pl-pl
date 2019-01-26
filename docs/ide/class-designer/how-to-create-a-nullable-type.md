---
title: 'Instrukcje: Tworzenie typu Zerowalnego (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2d21a032c100f2a76815e25a9d7c96aa4c071b62
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988340"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Instrukcje: Tworzenie typu dopuszczającego wartość null w Projektancie klas

Niektóre typy wartości nie zawsze masz (lub potrzebujesz) zdefiniowanej wartości. Jest to powszechną praktyką w bazach danych, gdzie niektóre pola nie można przypisać dowolną wartość. Na przykład może przypisać wartości null z polem bazy danych, aby oznaczają, że nie jeszcze nadano jej wartość.

A *typu dopuszczającego wartość null* jest typem wartości, które można rozszerzyć, aby przyspieszyć typowy zakres wartości dla tego typu, a także wartość null. Na przykład dopuszczający wartości null z `Int32`, są również oznaczane jako dopuszczającego wartość null\<Int32 > można przypisać dowolną wartość od -2147483648 do 2147483647 i może ona zostać przypisana wartość null. Nullable\<bool > można przypisać wartości `True`, `False`, lub wartość null (Brak wartości wszystkie).

Typy dopuszczające wartości null są wystąpieniami <xref:System.Nullable%601> struktury. Każde wystąpienie typu dopuszczającego wartość null, ma dwa publiczne właściwości tylko do odczytu, `HasValue` i `Value`:

-   `HasValue` Typ jest `bool` i wskazuje, czy zmienna zawiera wartość zdefiniowana. `True` oznacza, że zmienna zawiera wartość inną niż null. Możesz sprawdzić wartości zdefiniowanej przy użyciu instrukcji takich jak `if (x.HasValue)` lub `if (y != null)`.

-   `Value` jest taki sam typ co typ podstawowy. Jeśli `HasValue` jest `True`, `Value` zawiera odpowiednią wartość. Jeśli `HasValue` jest `False`, uzyskiwania dostępu do `Value` spowoduje zgłoszenie wyjątku dotyczącego nieprawidłowej operacji.

Domyślnie, kiedy Deklarujesz zmienną typu dopuszczającego wartość null, go nie ma zdefiniowanej wartości (`HasValue` jest `False`), inne niż domyślna wartość typu wartości podstawowej.

Projektant klas Wyświetla typ dopuszczający wartość null, tak samo, jak wyświetla jego typ podstawowy.

Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku C#, zobacz [typów dopuszczających wartości zerowe](/dotnet/csharp/programming-guide/nullable-types/index). Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku Visual Basic, zobacz [typów wartości dopuszczających wartości zerowe](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Aby dodać typ dopuszczający wartość null, za pomocą projektanta klas

1.  Na diagramie klasy należy rozwinąć istniejącej klasy, lub Utwórz nową klasę.

2.  Aby dodać klasę do projektu, na **Diagram klas** menu, kliknij przycisk **Dodaj** > **Dodaj klasę**.

3.  Aby rozwinąć kształt klasy na **Diagram klas** menu, kliknij przycisk **rozwiń**.

4.  Wybierz kształt klasy. Na **Diagram klas** menu, kliknij przycisk **Dodaj** > **pola**. Nowe pole o nazwie domyślnej **pola** pojawi się w kształt klasy, a także w **szczegóły klasy** okna.

5.  W **nazwa** kolumny **szczegóły klasy** okna (lub w klasie kształtu, sam), Zmień nazwę nowego pola do nazwy ważne i istotne.

6.  W **typu** kolumny **szczegóły klasy** oknie zadeklarowana jako typ dopuszczający wartość null, określając następujące czynności:

    - `int?` (Visual C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Aby dodać typ dopuszczający wartość null, za pomocą edytora kodu

1.  Dodaj klasę do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **Dodaj klasę**.

2.  W pliku CS lub .vb dla nowej klasy należy dodać co najmniej jeden typ dopuszczający wartość null w nowej klasie do deklaracji klasy.

    ```csharp
    // Declare a nullable type in Visual C#:
    class Test
    {
       int? building_number = 5;
    }
    ```

    ```vb
    ' Declare a nullable type in Visual Basic:
    Class Test
       Dim buildingNumber As Nullable(Of Integer) = 5
    End Class
    ```

3.  W widoku klas przeciągnij nową ikonę klasy do powierzchni projektowej projektanta klas. Kształt klasy pojawia się na diagramie klasy.

4.  Rozwiń szczegóły kształt klasy, a następnie przesuń wskaźnik myszy nad składowych klasy. Etykietka narzędzia zawiera deklarację każdego elementu członkowskiego.

5.  Kliknij prawym przyciskiem myszy kształt klasy, a następnie kliknij przycisk **szczegóły klasy**. Można wyświetlać lub modyfikować właściwości nowego typu w **szczegóły klasy** okna.

## <a name="see-also"></a>Zobacz także

- <xref:System.Nullable%601>
- [Typy dopuszczające wartości null](/dotnet/csharp/programming-guide/nullable-types/index)
- [Używanie typów dopuszczających wartości null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Instrukcje: Identyfikowanie typu dopuszczającego wartość null](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Typy wartości dopuszczających wartości null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
