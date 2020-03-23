---
title: 'Porady: tworzenie typu zerowalnego (Projektant klas)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5be8b553dfead4b8c05f29bbd18c16fcef847130
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592233"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Jak: Tworzenie typu możliwego do wartości null w Projektancie klas

Niektóre typy wartości nie zawsze mają (lub potrzebują) zdefiniowanej wartości. Jest to powszechna praktyka w bazach danych, gdzie niektóre pola mogą nie być przypisane żadnej wartości. Na przykład można przypisać wartość null do pola bazy danych, aby oznaczać, że nie została jeszcze przypisana wartość.

*Typ nullable* jest typem wartości, który można rozszerzyć, tak aby zajęło typowy zakres wartości dla tego typu, a także wartość null. Na przykład nullable `Int32`, również oznaczone jako\<Nullable Int32>, można przypisać dowolną wartość od -2147483648 do 2147483647 lub może być przypisana wartość null. Nullable\<bool> można przypisać wartości `True`, `False`lub null (brak wartości w ogóle).

Typy nullable są <xref:System.Nullable%601> wystąpieniami struktury. Każde wystąpienie typu możliwego do odczytu ma `HasValue` `Value`dwie publiczne właściwości tylko do odczytu i:

- `HasValue`jest typem `bool` i wskazuje, czy zmienna zawiera zdefiniowaną wartość. `True`oznacza, że zmienna zawiera wartość niena null. Zdefiniowaną wartość można przetestować za pomocą `if (x.HasValue)` `if (y != null)`instrukcji, takiej jak lub .

- `Value`jest tego samego typu co typ podstawowy. Jeśli `HasValue` `True`jest `Value` , zawiera znaczącą wartość. Jeśli `HasValue` `False`tak, `Value` dostęp zda wyjątek nieprawidłowej operacji.

Domyślnie podczas deklarowania zmiennej jako typu możliwego domina`HasValue` `False`nie ma zdefiniowanej wartości ( jest), innej niż wartość domyślna jej typa wartości podstawowej.

Projektant klasy wyświetla typ nullable, tak jak wyświetla jego podstawowy typ.

Aby uzyskać więcej informacji na temat typów nullable w języku C#, zobacz [Typy nullable](/dotnet/csharp/programming-guide/nullable-types/index). Aby uzyskać więcej informacji na temat typów nullable w języku Visual Basic, zobacz [Typy wartości nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Aby dodać typ nullable przy użyciu Projektanta klas

1. Na diagramie klasy rozwiń istniejącą klasę lub utwórz nową klasę.

2. Aby dodać klasę do projektu, w menu **Diagram klas** kliknij polecenie **Dodaj** > **klasę**.

3. Aby rozwinąć kształt klasy, w menu **Diagram klas** kliknij polecenie **Rozwiń**.

4. Zaznacz kształt klasy. W menu **Diagram klas** kliknij polecenie **Dodaj** > **pole**. Nowe pole o domyślnej nazwie **Pole** pojawi się w kształcie klasy, a także w oknie **Szczegóły klasy.**

5. W kolumnie **Nazwa** okna **Szczegóły klasy** (lub w samym kształcie klasy) zmień nazwę nowego pola na prawidłową i znaczącą nazwę.

6. W kolumnie **Typ** okna **Szczegóły klasy** zadeklaruj typ jako typ nullable, określając następujące elementy:

    - `int?`(Visual C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Aby dodać typ nullable przy użyciu Edytora kodu

1. Dodaj klasę do projektu. Wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie w menu **Projekt** kliknij polecenie **Dodaj klasę**.

2. W pliku cs lub .vb dla nowej klasy dodaj jeden lub więcej typów nullable w nowej klasie do deklaracji klasy.

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

3. W widoku klasy przeciągnij nową ikonę klasy na powierzchnię projektu Projektanta klas. Kształt klasy pojawia się na diagramie klasy.

4. Rozwiń szczegóły kształtu klasy i przesuń wskaźnik myszy na elementy członkowskie klasy. Etykietka narzędzia wyświetla deklarację każdego elementu członkowskiego.

5. Kliknij prawym przyciskiem myszy kształt klasy i kliknij polecenie **Szczegóły klasy**. Można wyświetlić lub zmodyfikować właściwości nowego typu w oknie **Szczegóły klasy.**

## <a name="see-also"></a>Zobacz też

- <xref:System.Nullable%601>
- [Typy dopuszczające wartości null](/dotnet/csharp/programming-guide/nullable-types/index)
- [Używanie typów dopuszczających wartości null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Instrukcje: identyfikowanie typu dopuszczającego wartość null](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Typy o wartości zerowalnej](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
