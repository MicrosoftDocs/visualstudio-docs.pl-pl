---
title: Relacje między klasami LINQ to SQL (Projektant O/R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fb81cf17de86a11d2373f6a545b3efc78e65ada9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586474"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Instrukcje: Tworzenie skojarzenia między klasami LINQ to SQL (Projektant O/R)
Skojarzenia klas jednostek w [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] są analogiczne do relacji między tabelami w bazie danych. Skojarzenia klas jednostek można utworzyć przy użyciu okna dialogowego **Edytor skojarzeń** .

Należy wybrać klasę nadrzędną i klasę podrzędną podczas korzystania z okna dialogowego **Edytor skojarzeń** w celu utworzenia skojarzenia. Klasa nadrzędna jest klasą jednostki, która zawiera klucz podstawowy; Klasa podrzędna jest klasą jednostki, która zawiera klucz obcy. Na przykład jeśli utworzono klasy jednostki, które mapują do `Northwind Customers` i `Orders` tabelach, Klasa `Customer` byłaby klasą nadrzędną, a Klasa `Order` byłaby klasą podrzędną.

> [!NOTE]
> Podczas przeciągania tabel z **Eksplorator serwera** lub **Eksplorator bazy danych** do **Object Relational Designer** (**Projektant O/R**) skojarzenia są tworzone automatycznie na podstawie istniejących relacji klucza obcego w bazie danych.

## <a name="association-properties"></a>Właściwości skojarzenia
Po utworzeniu skojarzenia, gdy wybierzesz skojarzenie w **Projektancie O/R**, w oknie **Właściwości** znajdują się pewne konfigurowalne właściwości. (Skojarzenie jest linią między powiązanymi klasami). Poniższa tabela zawiera opisy właściwości skojarzenia.

|Właściwość|Opis|
|--------------|-----------------|
|**Kardynalności**|Określa, czy skojarzenie jest jedno-do-wielu, czy jeden-do-jednego.|
|**Właściwość podrzędna**|Określa, czy ma zostać utworzona właściwość obiektu nadrzędnego, który jest kolekcją lub odwołaniem do rekordów podrzędnych po stronie klucza obcego skojarzenia. Na przykład w skojarzeniu między `Customer` i `Order`, jeśli **Właściwość podrzędna** ma wartość **true**, właściwość o nazwie `Orders` jest tworzona w klasie nadrzędnej.|
|**Właściwość nadrzędna**|Właściwość klasy podrzędnej, która odwołuje się do skojarzonej klasy nadrzędnej. Na przykład w skojarzeniu między `Customer` i `Order`właściwość o nazwie `Customer` odwołująca się do skojarzonego klienta dla zamówienia jest tworzona na klasie `Order`.|
|**Właściwości uczestniczące**|Wyświetla właściwości skojarzenia i zawiera przycisk **wielokropka** (...), który powoduje ponowne otwarcie okna dialogowego **Edytor skojarzeń** .|
|**Unikatowy**|Określa, czy obce kolumny docelowe mają ograniczenie unikatowości.|

## <a name="to-create-an-association-between-entity-classes"></a>Aby utworzyć skojarzenie między klasami jednostek

1. Kliknij prawym przyciskiem myszy klasę jednostki, która reprezentuje klasę nadrzędną w skojarzeniu, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **skojarzenie**.

2. Sprawdź, czy w oknie dialogowym **Edytor skojarzeń** została wybrana prawidłowa **Klasa nadrzędna** .

3. Wybierz **klasę podrzędną** w polu kombi.

4. Wybierz **właściwości skojarzenia** , które wiążą klasy. Zwykle jest to mapowanie do relacji klucza obcego zdefiniowanej w bazie danych. Na przykład w skojarzeniu `Customers` i `Orders` **właściwości skojarzenia** są `CustomerID` dla każdej klasy.

5. Kliknij przycisk **OK** , aby utworzyć skojarzenie.

## <a name="see-also"></a>Zobacz także

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: tworzenie klas LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Jak reprezentować klucze podstawowe](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
