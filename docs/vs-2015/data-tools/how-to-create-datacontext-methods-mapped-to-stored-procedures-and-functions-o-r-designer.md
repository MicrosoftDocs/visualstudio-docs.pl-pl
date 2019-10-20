---
title: 'Instrukcje: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (Projektant O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665978"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Instrukcje: Tworzenie metod DataContext mapowanych na procedury składowane i funkcje (Projektant O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Procedury składowane i funkcje można dodać do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jako metody <xref:System.Data.Linq.DataContext>. Wywołanie metody i przekazanie w wymaganych parametrach powoduje uruchomienie procedury składowanej lub funkcji w bazie danych i zwrócenie danych w zwracanym typie metody <xref:System.Data.Linq.DataContext>. Aby uzyskać szczegółowe informacje na temat metod <xref:System.Data.Linq.DataContext>, zobacz [metody DataContext (Projektant O/R)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Procedury składowane mogą również służyć do przesłonięcia domyślnego zachowania środowiska uruchomieniowego [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)], które wykonuje operacje wstawiania, aktualizacji i usuwania, gdy zmiany są zapisywane z klas jednostek do bazy danych. Aby uzyskać więcej informacji, zobacz [How to: assignd procedur składowanych do wykonywania aktualizacji, wstawianych i usuwanych (Projektant O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>Tworzenie metod DataContext
 Metody <xref:System.Data.Linq.DataContext> można tworzyć, przeciągając procedury składowane lub funkcje z **Eksplorator serwera/Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

> [!NOTE]
> Zwracany typ wygenerowanej metody <xref:System.Data.Linq.DataContext> różni się w zależności od tego, gdzie porzucasz procedurę składowaną lub funkcję na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Upuszczanie elementów bezpośrednio do istniejącej klasy Entity tworzy metodę <xref:System.Data.Linq.DataContext> z typem zwracanym klasy Entity. Upuszczanie elementów do pustego obszaru [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tworzy metodę <xref:System.Data.Linq.DataContext>, która zwraca typ wygenerowany automatycznie. Zwracany typ metody <xref:System.Data.Linq.DataContext> można zmienić po dodaniu jej do okienka metod. Aby sprawdzić lub zmienić zwracany typ metody <xref:System.Data.Linq.DataContext>, zaznacz ją i sprawdź Właściwość **zwracanego typu** w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [How to: zmiana zwracanego typu metody DataContext (Projektant O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Aby utworzyć metody DataContext, które zwracają automatycznie generowane typy

1. W **Eksplorator serwera** /**Eksplorator bazy danych**rozwiń węzeł **procedury składowane** w bazie danych, z którą pracujesz.

2. Znajdź żądaną procedurę przechowywaną i przeciągnij ją do pustego obszaru [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Metoda <xref:System.Data.Linq.DataContext> jest tworzona z automatycznie generowanym typem zwracanym i pojawia się w okienku **metody** .

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Aby utworzyć metody DataContext, które mają zwracany typ klasy jednostki

1. W **Eksplorator serwera** /**Eksplorator bazy danych**rozwiń węzeł **procedury składowane** w bazie danych, z którą pracujesz.

2. Znajdź żądaną procedurę przechowywaną i przeciągnij ją do istniejącej klasy jednostki w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Metoda <xref:System.Data.Linq.DataContext> jest tworzona z typem zwracanym wybranej klasy jednostki i pojawia się w okienku **metody** .

> [!NOTE]
> Aby uzyskać informacje na temat zmieniania typu zwracanego istniejących metod <xref:System.Data.Linq.DataContext>, zobacz [How to: Change the return Type of DataContext, Metoda (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Zobacz też
 Wskazówki dotyczące [LINQ to SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [metody DataContext (Projektant o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) wskazówki [: tworzenie klas LINQ to SQL (projektant o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [wprowadzenie do LINQ w Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [instrukcje: zapisywanie zapytań LINQ w C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
