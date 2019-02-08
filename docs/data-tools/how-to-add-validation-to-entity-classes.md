---
title: 'Instrukcje: Dodawanie walidacji do klas jednostek'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5f4f2f5e44ea95137f53019f52de94a5389fa6d8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913499"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Instrukcje: Dodawanie walidacji do klas jednostek
*Sprawdzanie poprawności* klas jednostek jest procesem potwierdzania, że wartości wprowadzone w obiektach danych są zgodne z ograniczeniami w schemacie obiektu, a także zasadami ustanowionymi dla aplikacji. Sprawdzanie poprawności danych, aby wysłać aktualizacje do podstawowej bazy danych jest dobrą praktyką, która zmniejsza błędy. Zmniejsza to także potencjalną liczbę rund między aplikacją a bazą danych.

 [LINQ to SQL tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) dostarcza metod częściowych, które umożliwiają użytkownikom Rozszerz kod wygenerowany przez projektanta, który jest uruchamiany podczas operacji wstawiania, aktualizacji i usuwa pełną jednostek, a także podczas i po poszczególnych kolumn zmiany.

> [!NOTE]
>  Ten temat zawiera podstawowe kroki Dodawanie walidacji do klas jednostek za pomocą **O/R Designer**. Ponieważ może być trudne do tych kroków ogólny bez odwołujące się do klasy określonej jednostki, znajduje się przewodnik, który korzysta z rzeczywistych danych.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Dodawanie sprawdzania poprawności zmian do wartości w określonej kolumnie
 Ta procedura pokazuje sposób sprawdzania poprawności danych, po zmianie wartości w kolumnie. Ponieważ Weryfikacja odbywa się wewnątrz definicji klasy (zamiast interfejsu użytkownika), jest zgłaszany wyjątek, jeśli wartość powoduje, że weryfikacja nie powiedzie się. Implementuje obsługę błędów dla kodu w aplikacji, który podejmie próbę zmiany wartości w kolumnach.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Aby sprawdzić poprawność danych podczas zmiany wartości w kolumnie

1.  Otwórz lub Utwórz nowy plik LINQ to SQL klas (**dbml** pliku) w **O/R Designer**. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań**.)

2.  W **O/R Designer**, kliknij prawym przyciskiem myszy klasę, dla którego chcesz dodać sprawdzanie poprawności, a następnie kliknij przycisk **Wyświetl kod**.

     Zostanie otwarty Edytor kodu klasę częściową dla klasy wybranego obiektu.

3.  Umieść kursor w klasie częściowej.

4.  Dla projektów języka Visual Basic:

    1.  Rozwiń **nazwę metody** listy.

    2.  Znajdź **OnCOLUMNNAMEChanging** metody dla kolumny, które chcesz dodać sprawdzanie poprawności, aby.

    3.  `OnCOLUMNNAMEChanging` Metoda jest dodawana do klasy częściowej.

    4.  Dodaj następujący kod, aby najpierw sprawdź, czy wprowadzona wartość, a następnie upewnij się, że wprowadzona dla kolumny, która wartość jest dopuszczalny dla aplikacji. `value` Argument zawiera proponowana wartość, więc Dodaj logikę, aby upewnić się, że jest prawidłowa wartość:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Dla projektów C#:

    Ponieważ C# projektów nie generują automatycznie obsługi zdarzeń, korzystać z technologii IntelliSense, aby utworzyć metody częściowej zmieniającej się kolumny. Typ `partial` i następnie spację, aby uzyskać dostęp do listy dostępnych metod częściowych. Kliknij metodę zmieniającej się kolumny dla kolumny, które chcesz dodać sprawdzanie poprawności. Poniższy kod jest podobny kod, który jest generowany, gdy wybierzesz metodą częściową zmieniającej się kolumny:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Dodawanie sprawdzania poprawności dla aktualizacji do klasy jednostki
 Oprócz sprawdzania wartości podczas wprowadzania zmian, możesz również walidować dane podczas próby aktualizacji klasy całą jednostkę. Sprawdzanie poprawności podczas próby aktualizacji umożliwia porównanie wartości w wielu kolumnach, jeśli reguły biznesowe tego wymagać. Poniższa procedura pokazuje, jak sprawdzania poprawności, gdy podejmowana jest próba aktualizacja klasy całą jednostkę.

> [!NOTE]
>  Kod sprawdzania poprawności na zakończenie klas jednostek aktualizacji jest wykonywana w części <xref:System.Data.Linq.DataContext> klasy (a nie w klasie częściowej klasy określonej jednostce).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Aby sprawdzić poprawność danych podczas aktualizacji do klasy jednostki

1.  Otwórz lub Utwórz nowy plik LINQ to SQL klas (**dbml** pliku) w **O/R Designer**. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań**.)

2.  Kliknij prawym przyciskiem myszy pusty obszar **O/R Designer** i kliknij przycisk **Wyświetl kod**.

     Zostanie otwarty Edytor kodu za pomocą klasę częściową dla `DataContext`.

3.  Umieść kursor w klasie częściowej dla `DataContext`.

4.  Dla projektów języka Visual Basic:

    1.  Rozwiń **nazwę metody** listy.

    2.  Kliknij przycisk **UpdateENTITYCLASSNAME**.

    3.  `UpdateENTITYCLASSNAME` Metoda jest dodawana do klasy częściowej.

    4.  Dostęp do wartości poszczególnych kolumn przy użyciu `instance` argumentu, jak pokazano w poniższym kodzie:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Dla projektów C#:

    Ponieważ C# projektów nie generują automatycznie obsługi zdarzeń, korzystać z technologii IntelliSense, aby utworzyć częściowego `UpdateCLASSNAME` metody. Typ `partial` i następnie spację, aby uzyskać dostęp do listy dostępnych metod częściowych. Kliknij metodę aktualizacji dla klasy, na którym chcesz dodać sprawdzanie poprawności. Poniższy kod jest podobny kod, który jest generowany, gdy wybierzesz `UpdateCLASSNAME` metody częściowej:

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)