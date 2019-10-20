---
title: 'Instrukcje: Konfigurowanie dziedziczenia przy użyciu projektanta O-R | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f8c08546fdf96c755b3adb80021ab7269509739
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654705"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Instrukcje: Konfigurowanie dziedziczenia przy użyciu projektanta O/R
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) obsługuje koncepcję dziedziczenia pojedynczej tabeli, ponieważ jest ona często zaimplementowana w systemach relacyjnych. W przypadku dziedziczenia z jedną tabelą istnieje pojedyncza tabela bazy danych zawierająca pola dla informacji nadrzędnych i podrzędnych. W przypadku danych relacyjnych kolumna rozróżniacza zawiera wartość określającą, do której klasy należy każdy rekord.

 Rozważmy na przykład tabelę osób, która zawiera wszystkich zatrudnionych przez firmę. Niektóre osoby to pracownicy i niektórzy ludzie są kierownikami. Tabela osoby zawiera kolumnę o nazwie `EmployeeType`, która ma wartość 1 dla menedżerów i wartość 2 dla pracowników; jest to kolumna rozróżniacza. W tym scenariuszu można utworzyć podklasę pracowników i wypełnić klasę tylko rekordami mającymi `EmployeeType` wartość 2. Można również usunąć kolumny, które nie dotyczą poszczególnych klas.

 Tworzenie modelu obiektów, który używa dziedziczenia (i odpowiada danych relacyjnych) może być nieco mylące. Poniższa procedura zawiera opis czynności wymaganych do skonfigurowania dziedziczenia przy użyciu projektanta O/R. Następujące czynności ogólne nie odwołujące się do istniejącej tabeli i kolumn mogą być trudne, dlatego podano przewodnik, który używa danych. Aby uzyskać szczegółowe instrukcje krok po kroku dotyczące konfigurowania dziedziczenia przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], zobacz [Przewodnik: tworzenie LINQ to SQL klas przy użyciu dziedziczenia pojedynczej tabeli (Projektant O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

### <a name="to-create-inherited-data-classes"></a>Aby utworzyć dziedziczone klasy danych

1. Otwórz [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], dodając element **klasy LINQ to SQL** do istniejącego Visual Basic lub C# projektu.

2. Przeciągnij tabelę, która ma być używana jako klasa bazowa na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

3. Przeciągnij drugą kopię tabeli na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] i zmień jej nazwę. Jest to Klasa pochodna lub podklasa.

4. Kliknij przycisk **dziedziczenie** na karcie **Object Relational Designer** **przybornika**, a następnie kliknij podklasę (nazwę tabeli) i połącz ją z klasą bazową.

    > [!NOTE]
    > Kliknij element **dziedziczenia** w **przyborniku** i zwolnij przycisk myszy, kliknij drugą kopię klasy utworzonej w kroku 3, a następnie kliknij pierwszą klasę utworzoną w kroku 2. Strzałka w linii dziedziczenia wskaże pierwszą klasę.

5. W każdej klasie Usuń wszystkie właściwości obiektu, które nie mają być wyświetlane i które nie są używane do skojarzenia. Wystąpił błąd podczas próby usunięcia właściwości obiektu używanych dla skojarzeń: [nie można usunąć właściwości \<property nazwy >, ponieważ uczestniczy ona w > \<association nazw skojarzenia](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Ponieważ Klasa pochodna dziedziczy właściwości zdefiniowane w klasie bazowej, w każdej klasie nie można definiować tych samych kolumn. (Kolumny są implementowane jako właściwości.) Można włączyć tworzenie kolumn w klasie pochodnej przez ustawienie modyfikatora dziedziczenia dla właściwości w klasie bazowej. Aby uzyskać więcej informacji, zobacz [nie w kompilacji: Zastępowanie właściwości i metod](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213).

6. Wybierz linię dziedziczenia w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

7. W oknie **Właściwości** Ustaw **Właściwość rozróżniacz** na nazwę kolumny, która jest używana do rozróżniania rekordów w klasach.

8. Ustaw właściwość **wartość rozróżniacza klasy pochodnej** na wartość w bazie danych, która określa rekord jako typ dziedziczony. (Jest to wartość, która jest przechowywana w kolumnie dyskryminatora i używana do wyznaczania dziedziczonej klasy).

9. Ustaw właściwość **wartość rozróżniacza klasy bazowej** na wartość, która określa rekord jako typ podstawowy. (Jest to wartość, która jest przechowywana w kolumnie dyskryminatora i używana do wyznaczania klasy bazowej).

10. Opcjonalnie można również ustawić **domyślną właściwość dziedziczenia** , aby wyznaczyć typ w hierarchii dziedziczenia, który jest używany podczas ładowania wierszy, które nie pasują do żadnego zdefiniowanego kodu dziedziczenia. Innymi słowy, jeśli rekord ma wartość w swojej kolumnie rozróżniacza, która nie pasuje do wartości w **klasie pochodnej wartości rozróżniacza** lub właściwości **wartości rozróżniacza klasy bazowej** , rekord zostanie załadowany do typu wyznaczonego jako  **Domyślne dziedziczenie**.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w](../data-tools/linq-to-sql-tools-in-visual-studio2.md) przewodniku po programie Visual Studio [: tworzenie klas LINQ to SQL (Projektant O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [Pave Nowości dotyczące tworzenia aplikacji dla danych w programie Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [dostęp do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [ Wskazówki: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (Projektant O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [nie w kompilacji: dziedziczenie w Visual Basic](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [dziedziczenia](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)
