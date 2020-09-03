---
title: 'Instrukcje: zmiana zwracanego typu metody DataContext (Projektant O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 351a2f53d8ad8c5f29821d905c292cd988390869
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658839"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Instrukcje: zmienianie zwracanego typu metody DataContext (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zwracany typ <xref:System.Data.Linq.DataContext> metody (utworzony w oparciu o procedurę składowaną lub funkcję) różni się w zależności od tego, gdzie porzucasz procedurę składowaną lub funkcję w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . W przypadku porzucenia elementu bezpośrednio do istniejącej klasy jednostki <xref:System.Data.Linq.DataContext> zostanie utworzona Metoda, która ma zwracany typ klasy jednostki (Jeśli schemat danych zwróconych przez procedurę składowaną lub funkcję dopasowuje kształt klasy jednostki). Jeśli upuszczasz element na pusty obszar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , <xref:System.Data.Linq.DataContext> zostanie utworzona Metoda zwracająca automatycznie wygenerowany typ. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu jej do okienka metod. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz ją i kliknij właściwość **Typ zwracany** w oknie **Właściwości** .

> [!NOTE]
> Nie można przywrócić <xref:System.Data.Linq.DataContext> metod, które mają ustawiony typ zwracany na klasę jednostki, aby zwracał typ wygenerowany automatycznie przy użyciu okna **Właściwości** . Aby przywrócić <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowany typ, należy ponownie przeciągnąć oryginalny obiekt bazy danych do projektanta O/R.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Aby zmienić zwracany typ metody DataContext z automatycznie generowanego typu do klasy Entity

1. Wybierz <xref:System.Data.Linq.DataContext> metodę w okienku metody.

2. W oknie **Właściwości** wybierz pozycję **Typ zwracany** , a następnie wybierz dostępną klasę jednostki na liście **Typ zwracany** . Jeśli żądana Klasa jednostki nie znajduje się na liście, Dodaj ją do lub utwórz ją w programie, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Aby dodać ją do listy.

3. Zapisz plik. dbml.

### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Aby zmienić zwracany typ metody DataContext z klasy Entity z powrotem na typ wygenerowany automatycznie

1. Wybierz <xref:System.Data.Linq.DataContext> metodę w okienku metody i usuń ją.

2. Przeciągnij obiekt bazy danych z **Eksplorator serwera** / **Eksplorator bazy danych** do pustego obszaru projektanta o/R.

3. Zapisz plik. dbml.

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [metody DataContext — projektant o/r)](../data-tools/datacontext-methods-o-r-designer.md) [instrukcje: Tworzenie metod DataContext mapowanych na procedury składowane i funkcje (Projektant o/r)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
