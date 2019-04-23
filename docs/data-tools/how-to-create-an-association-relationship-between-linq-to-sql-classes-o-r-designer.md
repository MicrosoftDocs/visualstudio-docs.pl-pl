---
title: Jak utworzyć relację między klasy LINQ do SQL za pomocą Projektanta obiektów relacyjnych
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9d7bf1be05ebabcaac319cce591cf82cd2ab5f5d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112289"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Instrukcje: Tworzenie skojarzenia między LINQ to SQL klas (Projektant O/R)
Skojarzenia między klasami jednostki w [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] są analogiczne do relacji między tabelami w bazie danych. Można utworzyć skojarzenia między klasami jednostki przy użyciu **Edytor skojarzeń** okno dialogowe.

Gdy używasz należy wybrać klasy nadrzędnej i podrzędnej klasy **Edytor skojarzeń** okno dialogowe, aby utworzyć skojarzenie. Klasa nadrzędna jest klasa jednostki, który zawiera klucz podstawowy; Klasa potomna jest klasa jednostki, która zawiera klucz obcy. Na przykład, jeśli klas jednostek zostały utworzone mapowane na `Northwind Customers` i `Orders` tabel, `Customer` klasy będzie klasy nadrzędnej i `Order` klasy będzie klasy podrzędnej.

> [!NOTE]
>  Podczas przeciągania tabel z **Eksploratora serwera** lub **Eksplorator bazy danych** na **Object Relational Designer** (**O/R Designer**), skojarzenia są tworzone automatycznie w oparciu o istniejące relacje klucza obcego w bazie danych.

## <a name="association-properties"></a>Właściwości skojarzenia
Po utworzeniu skojarzenia, po wybraniu skojarzenia w **O/R Designer**, istnieje kilka właściwości możliwych do skonfigurowania w **właściwości** okna. (Skojarzenie jest wiersz między powiązanymi klasami). Poniższa tabela zawiera opis właściwości skojarzenia.

|Właściwość|Opis|
|--------------|-----------------|
|**Kardynalność**|Określa, czy skojarzenie jest jeden do wielu lub jeden do jednego.|
|**Właściwości elementu podrzędnego**|Określa, czy ma być utworzona właściwość kolekcji lub odwołanie do rekordów podrzędnych po stronie klucza obcego skojarzenia obiektu nadrzędnego. Na przykład w przypadku skojarzenia między `Customer` i `Order`, jeśli **właściwości elementu podrzędnego** ustawiono **True**, właściwość o nazwie `Orders` jest tworzona w klasie nadrzędnej.|
|**Właściwość nadrzędna**|Właściwość klasy podrzędnej, przywołującej skojarzoną klasę nadrzędną. Na przykład w przypadku skojarzenia między `Customer` i `Order`, właściwość o nazwie `Customer` odwołujący skojarzonego odbiorcy zamówienie zostanie utworzone na `Order` klasy.|
|**Właściwości uczestniczące**|Wyświetla właściwości skojarzenia oraz **wielokropka** przycisku (...), który otwiera ponownie **Edytor skojarzeń** okno dialogowe.|
|**unikatowe**|Określa, czy obce kolumny docelowe mają ograniczenie unikatowości.|

## <a name="to-create-an-association-between-entity-classes"></a>Aby utworzyć skojarzenie między klasami jednostki

1. Kliknij prawym przyciskiem myszy klasę jednostki, która reprezentuje klasa nadrzędna do skojarzenia, wskaż opcję **Dodaj**, a następnie kliknij przycisk **skojarzenie**.

2. Sprawdź, czy poprawny **klasy nadrzędnej** wybrano **Edytor skojarzeń** okno dialogowe.

3. Wybierz **klasy podrzędnej** w polu kombi.

4. Wybierz **właściwości skojarzenia** powiązanych klas. Zwykle to mapuje relacji klucza obcego w bazie danych. Na przykład w `Customers` i `Orders` skojarzenia, **właściwości skojarzenia** są `CustomerID` dla każdej klasy.

5. Kliknij przycisk **OK** utworzyć skojarzenie.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: Tworzenie zapytań LINQ do klas SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: Reprezentacja kluczy podstawowych](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)