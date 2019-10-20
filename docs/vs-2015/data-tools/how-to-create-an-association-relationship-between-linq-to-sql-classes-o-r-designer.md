---
title: 'Instrukcje: Tworzenie skojarzenia (relacji) między klasami LINQ to SQL (Projektant O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c2f6f6f65410336eacf72967c8360a56e8fa5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610002"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Instrukcje: Tworzenie skojarzenia (relacji) między klasami LINQ to SQL (Projektant O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Skojarzenia klas jednostek w [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] są analogiczne do relacji między tabelami w bazie danych. Skojarzenia klas jednostek można utworzyć przy użyciu okna dialogowego **Edytor skojarzeń** .

 Należy wybrać klasę nadrzędną i klasę podrzędną podczas korzystania z okna dialogowego **Edytor skojarzeń** w celu utworzenia skojarzenia. Klasa nadrzędna jest klasą jednostki, która zawiera klucz podstawowy; Klasa podrzędna jest klasą jednostki, która zawiera klucz obcy. Na przykład jeśli utworzono klasy jednostki, które mapują do tabel klienci i zamówienia Northwind, Klasa klienta byłaby klasą nadrzędną, a Klasa Order będzie klasą podrzędną.

> [!NOTE]
> Gdy przeciągniesz tabele z **Eksplorator serwera** /**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), skojarzenia są tworzone automatycznie na podstawie istniejących relacji klucza obcego w bazie danych.

 Po utworzeniu skojarzenia, gdy wybierzesz skojarzenie w Projektancie O/R, w oknie **Właściwości** znajdują się pewne konfigurowalne właściwości. (Skojarzenie jest linią między powiązanymi klasami). Poniższa tabela zawiera opisy właściwości skojarzenia.

|Właściwość|Opis|
|--------------|-----------------|
|**Kardynalności**|Określa, czy skojarzenie jest jedno-do-wielu, czy jeden-do-jednego.|
|**Właściwość podrzędna**|Określa, czy ma zostać utworzona właściwość obiektu nadrzędnego, który jest kolekcją lub odwołaniem do rekordów podrzędnych po stronie klucza obcego skojarzenia. Na przykład w skojarzeniu między klientem i kolejności, jeśli **Właściwość podrzędna** ma wartość **true**, w klasie nadrzędnej jest tworzona właściwość o nazwie Orders.|
|**Właściwość nadrzędna**|Właściwość klasy podrzędnej, która odwołuje się do skojarzonej klasy nadrzędnej. Na przykład w skojarzeniu między klientem i kolejnością właściwość o nazwie klient odwołująca się do skojarzonego klienta dla zamówienia jest tworzona w klasie Order.|
|**Właściwości uczestniczące**|Wyświetla właściwości skojarzenia i zawiera przycisk **wielokropka** (...), który powoduje ponowne otwarcie okna dialogowego **Edytor skojarzeń** .|
|**Unikatowy**|Określa, czy obce kolumny docelowe mają ograniczenie unikatowości.|

### <a name="to-create-an-association-between-entity-classes"></a>Aby utworzyć skojarzenie między klasami jednostek

1. Kliknij prawym przyciskiem myszy klasę jednostki, która reprezentuje klasę nadrzędną w skojarzeniu, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **skojarzenie**.

2. Sprawdź, czy w oknie dialogowym **Edytor skojarzeń** została wybrana prawidłowa **Klasa nadrzędna** .

3. Wybierz **klasę podrzędną** w polu kombi.

4. Wybierz **właściwości skojarzenia** , które wiążą klasy. Zwykle jest to mapowanie do relacji klucza obcego zdefiniowanej w bazie danych. Na przykład w skojarzeniu klienci i zamówienia **właściwości skojarzenia** są IDKlienta dla każdej klasy.

5. Kliknij przycisk **OK** , aby utworzyć skojarzenie.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w](../data-tools/linq-to-sql-tools-in-visual-studio2.md) przewodniku po programie Visual Studio [: tworzenie klas LINQ to SQL (Projektant o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [metod DataContext (Projektant o/r)](../data-tools/datacontext-methods-o-r-designer.md) [instrukcje: Reprezentowanie kluczy podstawowych](https://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)
