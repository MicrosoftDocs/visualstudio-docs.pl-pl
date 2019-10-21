---
title: 'Porady: tworzenie typu zerowalnego (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 671b2230daafbbdf92edda2ba1a671b688723796
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647856"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Instrukcje: Tworzenie typu dopuszczającego wartość null w Projektant klas

Niektóre typy wartości nie zawsze mają określoną wartość (lub potrzebują). Jest to typowa sytuacja w bazach danych, w których niektóre pola mogą nie mieć przypisanej żadnej wartości. Na przykład możesz przypisać wartość null do pola bazy danych, aby oznaczać, że nie została jeszcze przypisana wartość.

*Typ dopuszczający wartość null* jest typem wartości, który można rozciągnąć, tak aby miał typowy zakres wartości dla tego typu, a także wartość null. Na przykład wartość null dla `Int32`, również oznaczona jako wartość null \<Int32 >, może mieć przypisanych wartości od-2147483648 do 2147483647 lub może być przypisana wartość null. > @No__t_0bool dopuszczające wartość null można przypisać do wartości `True`, `False` lub null (bez wartości).

Typy dopuszczające wartości null są wystąpieniami struktury <xref:System.Nullable%601>. Każde wystąpienie typu dopuszczającego wartość null ma dwie publiczne właściwości tylko do odczytu, `HasValue` i `Value`:

- `HasValue` jest typu `bool` i wskazuje, czy zmienna zawiera zdefiniowaną wartość. `True` oznacza, że zmienna zawiera wartość różną od null. Można testować pod kątem zdefiniowanej wartości przy użyciu instrukcji, takiej jak `if (x.HasValue)` lub `if (y != null)`.

- `Value` jest tego samego typu co typ podstawowy. Jeśli `HasValue` jest `True`, `Value` zawiera wartość znaczącą. Jeśli `HasValue` jest `False`, uzyskanie dostępu do `Value` spowoduje zgłoszenie nieprawidłowego wyjątku operacji.

Domyślnie podczas deklarowania zmiennej jako typu dopuszczającego wartość null nie ma zdefiniowanej wartości (`HasValue` jest `False`), innej niż domyślna wartość jego bazowego typu wartości.

Projektant klas wyświetla typ dopuszczający wartość null, tak jak wyświetla jego typ podstawowy.

Aby uzyskać więcej informacji na temat typów C#dopuszczających wartości null w, zobacz [Typy dopuszczające wartości null](/dotnet/csharp/programming-guide/nullable-types/index). Aby uzyskać więcej informacji na temat typów dopuszczających wartości null w Visual Basic, zobacz [dopuszczanie typów wartości null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Aby dodać typ dopuszczający wartość null przy użyciu Projektant klas

1. Na diagramie klasy rozwiń istniejącą klasę lub Utwórz nową klasę.

2. Aby dodać klasę do projektu, w menu **Diagram klas** kliknij polecenie **Dodaj**  > **Dodaj klasę**.

3. Aby rozwinąć kształt klasy, w menu **Diagram klas** kliknij przycisk **Rozwiń**.

4. Wybierz kształt klasy. W menu **Diagram klas** kliknij**pole** **Dodaj**  > . Nowe pole, które ma **pole** nazwa domyślna, pojawi się w kształcie klasy, a także w oknie **Szczegóły klasy** .

5. W kolumnie **Nazwa** okna **Szczegóły klasy** (lub samego kształtu klasy) Zmień nazwę nowego pola na prawidłową i zrozumiałą nazwę.

6. W kolumnie **Typ** okna **Szczegóły klasy** Zadeklaruj typ jako typ dopuszczający wartość null, określając następujące elementy:

    - `int?` (wizualizacja C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Aby dodać typ dopuszczający wartość null przy użyciu edytora kodu

1. Dodaj klasę do projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Dodaj klasę**.

2. W pliku CS lub VB dla nowej klasy Dodaj jeden lub więcej typów wartości null w nowej klasie do deklaracji klasy.

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

3. W Widok klasy Przeciągnij nową ikonę klasy do Projektant klas powierzchni projektowej. Kształt klasy zostanie wyświetlony na diagramie klas.

4. Rozwiń szczegóły kształtu klasy i przesuń wskaźnik myszy nad składowe klasy. W etykietce narzędzia zostanie wyświetlona deklaracja każdego elementu członkowskiego.

5. Kliknij prawym przyciskiem myszy kształt klasy, a następnie kliknij pozycję **Szczegóły klasy**. Właściwości nowego typu można wyświetlić lub zmodyfikować w oknie **Szczegóły klasy** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Nullable%601>
- [Typy dopuszczające wartości null](/dotnet/csharp/programming-guide/nullable-types/index)
- [Używanie typów dopuszczających wartości null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Instrukcje: identyfikowanie typu dopuszczającego wartość null](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Typy wartości dopuszczających wartości null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
