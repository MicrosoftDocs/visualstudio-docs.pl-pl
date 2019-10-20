---
title: 'Instrukcje: Dodawanie walidacji do klas jednostek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a68b0314f3c64ce9196b8d48a78844bc81990a92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665992"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Instrukcje: Dodawanie walidacji do klas jednostek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Sprawdzanie poprawności* klas jednostek jest procesem potwierdzania, że wartości wprowadzone do obiektów danych są zgodne z ograniczeniami w schemacie obiektu, a także z regułami ustanowionymi dla aplikacji. Sprawdzanie poprawności danych przed wysłaniem aktualizacji do podstawowej bazy danych jest dobrym sposobem na zmniejszenie błędów. Zmniejsza również potencjalną liczbę operacji rundy między aplikacją a bazą danych.

 [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) oferują metody częściowe, które umożliwiają użytkownikom rozbudowa kodu generowanego przez projektanta, który jest uruchamiany podczas wstawiania, aktualizacji i usuwania kompletnych jednostek, a także w czasie i po zmianach poszczególnych kolumn.

> [!NOTE]
> Ten temat zawiera podstawowe kroki umożliwiające dodawanie walidacji do klas jednostek przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Ze względu na to, że może być trudne przestrzeganie tych ogólnych kroków bez odwoływania się do określonej klasy jednostki, podano przewodnik, który używa rzeczywistych danych.

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Dodawanie walidacji zmian do wartości w określonej kolumnie
 Ta procedura pokazuje, jak sprawdzać poprawność danych po zmianie wartości w kolumnie. Ponieważ Walidacja jest wykonywana wewnątrz definicji klasy (zamiast w interfejsie użytkownika), zgłaszany jest wyjątek, jeśli wartość spowoduje niepowodzenie walidacji. Zaimplementuj obsługę błędów dla kodu w aplikacji, który próbuje zmienić wartości kolumn.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>Aby sprawdzić poprawność danych podczas zmiany wartości kolumny

1. Otwórz lub Utwórz nowy plik klas LINQ to SQL (plik**DBML** ) w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań**).

2. W Projektancie O/R kliknij prawym przyciskiem myszy klasę, dla której chcesz dodać walidację, a następnie kliknij polecenie **Wyświetl kod**.

    Zostanie otwarty Edytor kodu z klasą częściową dla wybranej klasy jednostki.

3. Umieść kursor w klasie częściowej.

4. Projekty Visual Basic:

   1. Rozwiń listę **Nazwa metody** .

   2. Znajdź metodę**zmiany** **na serwerze**_ColumnName_dla kolumny, do której ma zostać dodana Walidacja.

   3. Metoda `On`*columnname* `Changing` jest dodawana do klasy częściowej.

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

   5. Ponieważ C# projekty nie generują automatycznie programów obsługi zdarzeń, można użyć funkcji IntelliSense do tworzenia zmiennych metod częściowych.

       Wpisz `partial` a następnie miejsce, aby uzyskać dostęp do listy dostępnych metod częściowych. Kliknij metodę zmiany kolumny dla kolumny, dla której chcesz dodać walidację. Następujący kod jest podobny do kodu generowanego po wybraniu zmiany metody częściowej przez kolumnę:

      ```csharp
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
          {
             throw new System.NotImplementedException();
          }

      ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>Dodawanie weryfikacji dla aktualizacji klasy jednostki
 Oprócz sprawdzania wartości podczas zmian, można także sprawdzić poprawność danych podczas próby zaktualizowania kompletnej klasy jednostki. Walidacja podczas próby aktualizacji umożliwia porównanie wartości w wielu kolumnach, jeśli wymagają tego reguły biznesowe. Poniższa procedura pokazuje, jak sprawdzić, kiedy zostanie podjęta próba zaktualizowania kompletnej klasy jednostki.

> [!NOTE]
> Kod sprawdzania poprawności dla aktualizacji kompletnych klas jednostek jest wykonywany w klasie <xref:System.Data.Linq.DataContext> częściowej (zamiast klasy częściowej określonej klasy jednostki).

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Aby sprawdzić poprawność danych podczas aktualizacji klasy jednostki

1. Otwórz lub Utwórz nowy plik klas LINQ to SQL (plik**DBML** ) w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie plik **. dbml** w **Eksplorator rozwiązań**).

2. Kliknij prawym przyciskiem myszy pusty obszar w Projektancie O/R i kliknij polecenie **Wyświetl kod**.

    Zostanie otwarty Edytor kodu z klasą częściową dla `DataContext`.

3. Umieść kursor w klasie częściowej dla `DataContext`.

4. Projekty Visual Basic:

   1. Rozwiń listę **Nazwa metody** .

   2. Kliknij pozycję **Aktualizuj**_ENTITYCLASSNAME_.

   3. @No__t_0 Metoda*ENTITYCLASSNAME* jest dodawana do klasy częściowej.

   4. Dostęp do poszczególnych wartości kolumn za pomocą argumentu `instance`, jak pokazano w poniższym kodzie:

      ```vb
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
          Dim ErrorMessage As String = "Invalid data!"
          Throw New Exception(ErrorMessage)
      End If
      ```

      Dla C# projektów:

   5. Ponieważ C# projekty nie generują automatycznie programów obsługi zdarzeń, można użyć funkcji IntelliSense do utworzenia częściowej metody `Update`*CLASSNAME* .

   6. Wpisz `partial` a następnie miejsce, aby uzyskać dostęp do listy dostępnych metod częściowych. Kliknij metodę Update dla klasy, dla której chcesz dodać sprawdzanie poprawności. Poniższy kod przypomina kod, który jest generowany po wybraniu metody `Update`*CLASSNAME* częściowej:

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

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [sprawdzania poprawności danych](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
