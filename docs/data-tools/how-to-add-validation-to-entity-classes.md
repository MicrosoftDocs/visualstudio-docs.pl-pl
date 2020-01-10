---
title: 'Instrukcje: Dodawanie walidacji do klas jednostek'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3ccd83662700794e60572eed923d10452595d726
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586565"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Instrukcje: Dodawanie walidacji do klas jednostek
*Sprawdzanie poprawności* klas jednostek jest procesem potwierdzania, że wartości wprowadzone do obiektów danych są zgodne z ograniczeniami w schemacie obiektu, a także z regułami ustanowionymi dla aplikacji. Sprawdzanie poprawności danych przed wysłaniem aktualizacji do podstawowej bazy danych jest dobrym sposobem na zmniejszenie błędów. Zmniejsza również potencjalną liczbę operacji rundy między aplikacją a bazą danych.

[Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) oferują metody częściowe, które umożliwiają użytkownikom rozbudowa kodu generowanego przez projektanta, który jest uruchamiany podczas wstawiania, aktualizacji i usuwania kompletnych jednostek, a także w czasie i po zmianach poszczególnych kolumn.

> [!NOTE]
> Ten temat zawiera podstawowe kroki umożliwiające dodawanie walidacji do klas jednostek przy użyciu **projektanta o/R**. Ze względu na to, że może być trudne przestrzeganie tych ogólnych kroków bez odwoływania się do określonej klasy jednostki, dostępne są wskazówki, które korzystają z rzeczywistych danych.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Dodawanie walidacji zmian do wartości w określonej kolumnie
Ta procedura pokazuje, jak sprawdzać poprawność danych po zmianie wartości w kolumnie. Ponieważ Walidacja jest wykonywana wewnątrz definicji klasy (zamiast w interfejsie użytkownika), zgłaszany jest wyjątek, jeśli wartość spowoduje niepowodzenie walidacji. Zaimplementuj obsługę błędów dla kodu w aplikacji, który próbuje zmienić wartości kolumn.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Aby sprawdzić poprawność danych podczas zmiany wartości kolumny

1. Otwórz lub Utwórz nowy plik klas LINQ to SQL (plik**DBML** ) w **projektancie o/R**. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań**).

2. W **projektancie o/R**kliknij prawym przyciskiem myszy klasę, dla której chcesz dodać walidację, a następnie kliknij polecenie **Wyświetl kod**.

     Zostanie otwarty Edytor kodu z klasą częściową dla wybranej klasy jednostki.

3. Umieść kursor w klasie częściowej.

4. Projekty Visual Basic:

    1. Rozwiń listę **Nazwa metody** .

    2. Znajdź metodę **OnCOLUMNNAMEChanging** dla kolumny, do której chcesz dodać walidację.

    3. Metoda `OnCOLUMNNAMEChanging` jest dodawana do klasy częściowej.

    4. Dodaj następujący kod, aby najpierw sprawdzić, czy wartość została wprowadzona, a następnie aby upewnić się, że wartość wprowadzona dla kolumny jest akceptowalna dla aplikacji. Argument `value` zawiera proponowaną wartość, więc Dodaj logikę, aby potwierdzić, że jest to prawidłowa wartość:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Dla C# projektów:

    Ponieważ C# projekty nie generują automatycznie programów obsługi zdarzeń, można użyć funkcji IntelliSense, aby utworzyć zmiany kolumn częściowych. Wpisz `partial` a następnie miejsce, aby uzyskać dostęp do listy dostępnych metod częściowych. Kliknij metodę zmiany kolumny dla kolumny, dla której chcesz dodać walidację. Poniższy kod jest podobny do kodu generowanego po wybraniu zmiany kolumny częściowej:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Dodawanie sprawdzania poprawności dla aktualizacji klasy jednostki
Oprócz sprawdzania wartości podczas zmian, można także sprawdzić poprawność danych podczas próby zaktualizowania kompletnej klasy jednostki. Walidacja podczas próby aktualizacji umożliwia porównanie wartości w wielu kolumnach, jeśli wymagają tego reguły biznesowe. Poniższa procedura pokazuje, jak sprawdzić, kiedy zostanie podjęta próba zaktualizowania kompletnej klasy jednostki.

> [!NOTE]
> Kod sprawdzania poprawności dla aktualizacji kompletnych klas jednostek jest wykonywany w klasie <xref:System.Data.Linq.DataContext> częściowej (zamiast klasy częściowej określonej klasy jednostki).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Aby sprawdzić poprawność danych podczas aktualizacji klasy jednostki

1. Otwórz lub Utwórz nowy plik klas LINQ to SQL (plik**DBML** ) w **projektancie o/R**. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań**).

2. Kliknij prawym przyciskiem myszy pusty obszar w **Projektancie O/R** i kliknij polecenie **Wyświetl kod**.

     Zostanie otwarty Edytor kodu z klasą częściową dla `DataContext`.

3. Umieść kursor w klasie częściowej dla `DataContext`.

4. Projekty Visual Basic:

    1. Rozwiń listę **Nazwa metody** .

    2. Kliknij pozycję **UpdateENTITYCLASSNAME**.

    3. Metoda `UpdateENTITYCLASSNAME` jest dodawana do klasy częściowej.

    4. Dostęp do poszczególnych wartości kolumn za pomocą argumentu `instance`, jak pokazano w poniższym kodzie:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Dla C# projektów:

    Ponieważ C# projekty nie generują automatycznie programów obsługi zdarzeń, można użyć funkcji IntelliSense do utworzenia metody `UpdateCLASSNAME` częściowej. Wpisz `partial` a następnie miejsce, aby uzyskać dostęp do listy dostępnych metod częściowych. Kliknij metodę Update dla klasy, do której chcesz dodać walidację. Poniższy kod przypomina kod generowany podczas wybierania `UpdateCLASSNAME` metodzie częściowej:

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

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
