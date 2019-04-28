---
title: 'Instrukcje: Zmiany zwracanego typu metody DataContext (Projektant O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 03e24c11e18f092823ad8dd8c4479b50e531b78b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402820"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Instrukcje: Zmiany zwracanego typu metody DataContext (O/R Designer)
Zwracany typ <xref:System.Data.Linq.DataContext> — metoda (utworzonym w zależności od procedury składowanej lub funkcji) różni się w zależności od tego, gdzie porzucić procedury składowanej lub funkcji w elemencie **O/R Designer**. Jeśli usuniesz element bezpośrednio na istniejącej klasy jednostki, <xref:System.Data.Linq.DataContext> metodę, która ma typ zwracany klasy jednostki jest tworzony (Jeśli schemat danych zwróconych przez procedurę składowaną lub funkcję odpowiada kształt klasy jednostek). Jeśli usuniesz element na pustym obszarem **O/R Designer**, <xref:System.Data.Linq.DataContext> metodę, która zwraca automatycznie wygenerowany typ zostanie utworzony. Możesz zmienić typ zwracany <xref:System.Data.Linq.DataContext> metoda po dodaniu do okienka metod. Aby sprawdzić lub zmienić typ zwracany <xref:System.Data.Linq.DataContext> metody, zaznacz go i kliknij **typie zwracanym** właściwość **właściwości** okna.

> [!NOTE]
> Nie można cofnąć <xref:System.Data.Linq.DataContext> metody, które mają typ zwracany po ustawieniu klasę jednostki Zwróć typ wygenerowany automatycznie za pomocą **właściwości** okna. Aby przywrócić <xref:System.Data.Linq.DataContext> metodę, aby zwracany typ wygenerowany automatycznie, należy przeciągnąć oryginalnego obiektu bazy danych na **O/R Designer** ponownie.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Zmiany zwracanego typu metody DataContext ze typu automatycznie wygenerowana klasa jednostki

1. Wybierz <xref:System.Data.Linq.DataContext> metody w okienko metod.

2. Wybierz **typie zwracanym** w **właściwości** okna, a następnie wybierz jednostki dostępne klasy w **typie zwracanym** listy. Jeśli klasa odpowiedniej jednostki nie jest na liście, dodaj go do, lub utwórz go w **O/R Designer** ją dodać do listy.

3. Zapisz *dbml* pliku.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Aby zmienić typ zwracany metody DataContext z klasy jednostki na typ wygenerowany automatycznie

1. Wybierz <xref:System.Data.Linq.DataContext> method in Class metoda **metody** okienku i usuń go.

2. Przeciągnij obiekt bazy danych z **Eksploratora serwera** lub **Eksplorator bazy danych** na pustym obszarem **O/R Designer**.

3. Zapisz *dbml* pliku.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)