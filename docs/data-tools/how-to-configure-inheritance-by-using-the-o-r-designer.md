---
title: 'Instrukcje: Skonfigurować dziedziczenie za pomocą projektanta O R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c57df245e897452d0bb8f3ae32d6490af9ee91fa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063013"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Instrukcje: Konfigurowanie dziedziczenia za pomocą narzędzia Object Relational Designer
**Object Relational Designer** (**O/R Designer**) obsługuje dziedziczenia pojedynczej tabeli, co jest często stosowana w systemach relacyjnych. Dziedziczenie pojedynczej tabeli Brak tabeli pojedynczej bazy danych, która zawiera pola zarówno informacje nadrzędnego, jak i podrzędnych. Z danymi relacyjnymi kolumna dyskryminatora zawiera wartość, która określa, która klasa dowolnego rekordu, o których należy.

Na przykład, rozważmy `Persons` tabelę, która zawiera wszystkich stosowanych przez firmę. Niektórzy użytkownicy są pracownicy i niektóre osoby menedżerów. `Persons` Tabela zawiera kolumnę o nazwie `EmployeeType` , ma wartość 1 dla menedżerów i wartość 2 dla pracowników; jest to kolumna dyskryminatora. W tym scenariuszu możesz utworzyć podklasę pracowników i wypełnić klasy za pomocą tylko te rekordy, które mają `EmployeeType` wartość 2. Z każdą z klas, można również usunąć kolumny, które nie mają zastosowania.

Tworzenie modelu obiektu, która korzysta z dziedziczenia (odpowiada relacyjnej bazie danych) może być nieco mylące. Poniższa procedura zawiera opis kroków wymaganych do konfigurowania dziedziczenia z **O/R Designer**. Następujące ogólne kroki bez odwołujące się do istniejącej tabeli i kolumn może być trudne, dlatego podano wskazówki, która korzysta z danych. Aby uzyskać szczegółowe informacje krok po kroku dotyczące konfigurowania dziedziczenie za pomocą **O/R Designer**, zobacz [instruktażu: Tworzenie zapytań LINQ do klas SQL za pomocą pojedynczej tabeli dziedziczenia (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Do tworzenia klas danych dziedziczonych

1. Otwórz **O/R Designer** , dodając **klasy LINQ do SQL** element do istniejących projektach Visual Basic lub C# projektu.

2. Przeciągnij tabelę, której chcesz użyć jako klasa bazowa na **O/R Designer**.

3. Przeciągnij drugiej kopii tabeli do **O/R Designer** i zmień jego nazwę. Jest to klasa pochodna, lub podklasę.

4. Kliknij przycisk **dziedziczenia** w **Object Relational Designer** karcie **przybornika**, a następnie kliknij podklasy (tabela, nazwa została zmieniona) i połącz go z klasy bazowej.

    > [!NOTE]
    >  Kliknij przycisk **dziedziczenia** pozycja **przybornika** i zwolnij przycisk myszy, kliknij drugą kopię klasy utworzonego w kroku 3, a następnie kliknij pierwszą klasą utworzony w kroku 2. Strzałka na linię dziedziczenia wskazuje na pierwszą klasą.

5. W każdej klasy należy usunąć wszystkie właściwości obiektu, które nie mają być wyświetlane i które nie są używane do skojarzenia. Otrzymasz komunikat o błędzie, jeśli użytkownik podejmie próbę usunięcia właściwości obiektu, używany do skojarzenia: [Właściwość \<nazwa właściwości > nie można usunąć, ponieważ uczestniczy w skojarzeniu \<Nazwa skojarzenia >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    >  Ponieważ klasa pochodna dziedziczy właściwości zdefiniowane w swojej klasie bazowej, te same kolumny nie można zdefiniować w każdej klasie. (Kolumny są implementowane jako właściwości). Tworzenie kolumny w klasie pochodnej można włączyć, ustawiając modyfikator dziedziczenia we właściwości w klasie bazowej. Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. Zaznacz wiersz dziedziczenia w **O/R Designer**.

7. W **właściwości** oknie **właściwość rozróżniacza** na nazwę kolumny, która odróżnia rekordów w Twoich zajęciach.

8. Ustaw **wartość dyskryminatora klasy pochodnej** właściwości do wartości w bazie danych, która określa rekord jako typ dziedziczone. (Jest to wartość, która jest przechowywana w kolumna dyskryminatora i służy do oznaczania odziedziczoną klasę).

9. Ustaw **wartości dyskryminator klasy bazowej** właściwości wartość, która określa rekord jako typu podstawowego. (Jest to wartość, która jest przechowywana w kolumna dyskryminatora i służy do oznaczania klasy podstawowej).

10. Opcjonalnie możesz również ustawić **domyślne dziedziczenie** właściwość, aby wskazać typ w hierarchii dziedziczenia, która jest używana podczas ładowania wierszy, które nie pasują zdefiniowany kod dziedziczenia. Innymi słowy, jeśli rekord ma wartość w jej kolumna dyskryminatora, odpowiada wartości w jednym **wartość dyskryminatora klasy pochodnej** lub **wartość dyskryminatora klasy podstawowej** właściwości, rekord Ładuje do typu wyznaczony jako **domyślne dziedziczenie**.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: Tworzenie zapytań LINQ do klas SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Przewodnik: Tworzenie zapytań LINQ do klas SQL za pomocą pojedynczej tabeli dziedziczenia (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Podstawowe informacje o dziedziczeniu (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Dziedziczenie](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)