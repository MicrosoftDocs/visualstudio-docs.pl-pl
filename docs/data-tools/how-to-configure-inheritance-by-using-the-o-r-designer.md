---
title: Konfigurowanie dziedziczenia przy użyciu projektanta O-R
description: Informacje o konfigurowaniu dziedziczenia przy użyciu Object Relational Designer (Projektant O/R), który obsługuje dziedziczenie pojedynczej tabeli. Utworzono dziedziczone klasy danych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4bc36bca3cc5bd13b3dcfad5ebed66eca7eeb019
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436336"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Instrukcje: konfigurowanie dziedziczenia za pomocą narzędzia Object Relational Designer
**Object Relational Designer** ( **Projektant O/R** ) wspiera koncepcję dziedziczenia pojedynczej tabeli, ponieważ jest ona często zaimplementowana w systemach relacyjnych. W przypadku dziedziczenia z jedną tabelą istnieje pojedyncza tabela bazy danych zawierająca pola dla informacji nadrzędnych i podrzędnych. W przypadku danych relacyjnych kolumna rozróżniacza zawiera wartość określającą, do której klasy należy każdy rekord.

Rozważmy na przykład `Persons` tabelę zawierającą wszystkie osoby zaangażowane przez firmę. Niektóre osoby to pracownicy i niektórzy ludzie są kierownikami. `Persons`Tabela zawiera kolumnę o nazwie `EmployeeType` , która ma wartość 1 dla menedżerów i wartość 2 dla pracowników; jest to kolumna rozróżniacza. W tym scenariuszu można utworzyć podklasę pracowników i wypełnić klasę tylko rekordami o `EmployeeType` wartości 2. Można również usunąć kolumny, które nie dotyczą poszczególnych klas.

Tworzenie modelu obiektów, który używa dziedziczenia (i odpowiada danych relacyjnych) może być nieco mylące. Poniższa procedura zawiera opis czynności wymaganych do skonfigurowania dziedziczenia przy użyciu **projektanta o/R**. Następujące kroki ogólne nie odwołujące się do istniejącej tabeli i kolumn mogą być trudne, dlatego należy zapewnić Przewodnik korzystający z danych. Aby uzyskać szczegółowe instrukcje krok po kroku dotyczące konfigurowania dziedziczenia przy użyciu **projektanta o/r** , zobacz [Przewodnik: tworzenie klas LINQ to SQL za pomocą dziedziczenia z jedną tabelą (Projektant o/r)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Aby utworzyć dziedziczone klasy danych

1. Otwórz **projektanta o/R** przez dodanie elementu **LINQ to SQL klas** do istniejącego Visual Basic lub projektu C#.

2. Przeciągnij tabelę, która ma być używana jako klasa bazowa do **projektanta O/R**.

3. Przeciągnij drugą kopię tabeli do **projektanta o/R** i zmień jej nazwę. Jest to Klasa pochodna lub podklasa.

4. Kliknij przycisk **dziedziczenie** na karcie **Object Relational Designer** **przybornika** , a następnie kliknij podklasę (nazwę tabeli) i połącz ją z klasą bazową.

    > [!NOTE]
    > Kliknij element **dziedziczenia** w **przyborniku** i zwolnij przycisk myszy, kliknij drugą kopię klasy utworzonej w kroku 3, a następnie kliknij pierwszą klasę utworzoną w kroku 2. Strzałka w linii dziedziczenia wskazuje na pierwszą klasę.

5. W każdej klasie Usuń wszystkie właściwości obiektu, które nie mają być wyświetlane i które nie są używane do skojarzenia. Wystąpił błąd podczas próby usunięcia właściwości obiektu używanych dla skojarzeń: [ \<property name> nie można usunąć właściwości, ponieważ uczestniczy ona w skojarzeniu \<association name> ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Ponieważ Klasa pochodna dziedziczy właściwości zdefiniowane w klasie bazowej, w każdej klasie nie można definiować tych samych kolumn. (Kolumny są implementowane jako właściwości.) Można włączyć tworzenie kolumn w klasie pochodnej przez ustawienie modyfikatora dziedziczenia dla właściwości w klasie bazowej. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [dziedziczeniu (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. Wybierz linię dziedziczenia w **projektancie o/R**.

7. W oknie **Właściwości** Ustaw **Właściwość rozróżniacz** na nazwę kolumny, która odróżnia rekordy w klasach.

8. Ustaw właściwość **wartość rozróżniacza klasy pochodnej** na wartość w bazie danych, która określa rekord jako typ dziedziczony. (Jest to wartość, która jest przechowywana w kolumnie rozróżniacz i służy do wyznaczania klasy dziedziczonej).

9. Ustaw właściwość **wartość rozróżniacza klasy bazowej** na wartość, która określa rekord jako typ podstawowy. (Jest to wartość, która jest przechowywana w kolumnie rozróżniacz i jest używana do wyznaczania klasy bazowej).

10. Opcjonalnie można również ustawić **domyślną właściwość dziedziczenia** , aby wyznaczyć typ w hierarchii dziedziczenia, który jest używany podczas ładowania wierszy, które nie pasują do żadnego zdefiniowanego kodu dziedziczenia. Innymi słowy, jeśli rekord ma wartość w swojej kolumnie rozróżniacza, która nie pasuje do wartości w **klasie pochodnej wartości rozróżniacza** lub właściwości **wartości rozróżniacza klasy bazowej** , rekord jest ładowany do typu wyznaczonego jako **domyślne dziedziczenie**.

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Przewodnik: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (Projektant O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Podstawowe informacje o dziedziczeniu (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Dziedziczenie](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
