---
title: Tworzenie sparametryzowanych zapytań adaptera TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d521e621436d02329b21e37a2ebfc47eef65f0b8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931029"
---
# <a name="create-parameterized-tableadapter-queries"></a>Tworzenie sparametryzowanych zapytań adaptera TableAdapter

Uruchamianie zapytania parametrycznego zwraca dane spełniające warunki klauzuli WHERE w ramach zapytania. Na przykład można zdefiniować parametry listę klientów, aby wyświetlić tylko klienci niektóre miasta, dodając `WHERE City = @City` do końca instrukcji SQL, które zwraca listę klientów.

Tworzenie sparametryzowanych zapytań adaptera TableAdapter w **Projektanta obiektów Dataset**. Można też utworzyć w aplikacji Windows, za pomocą **parametryzacja źródła danych** polecenie **danych** menu. **Parametryzacja źródła danych** polecenie tworzy formantów w formularzu, gdzie wartości parametrów wejściowych i uruchom zapytanie.

> [!NOTE]
> Podczas tworzenia zapytania parametrycznego, użyj notacji parametru, które są specyficzne dla bazy danych, która jest kodowania dla. Na przykład źródła danych programu Access i OleDb użyć znaku zapytania '?' do oznaczania parametrów, dlatego klauzuli WHERE będzie wyglądać następująco: `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Tworzenie sparametryzowanych zapytań TableAdapter

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Aby utworzyć zapytanie parametryczne w Projektancie obiektów Dataset

-   Utwórz nowy obiekt TableAdapter, dodając klauzulę WHERE z odpowiednie parametry do instrukcji SQL. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).

     —lub—

-   Dodaj zapytanie na istniejący obiekt TableAdapter, dodając klauzulę WHERE z odpowiednie parametry do instrukcji SQL.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Aby utworzyć zapytanie parametryczne podczas projektowania formularza powiązanych z danymi

1.  Wybierz kontrolkę w formularzu, która jest już powiązany z zestawem danych. Aby uzyskać więcej informacji, zobacz [formanty powiązania formularzy Windows do danych w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  Na **danych** menu, wybierz opcję **Dodaj zapytanie**.

3.  Wykonaj **Konstruktor kryteriów wyszukiwania** okno dialogowe, dodając klauzulę WHERE z odpowiednie parametry do instrukcji SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Aby dodać zapytanie do istniejącego formularza powiązanych z danymi

1.  Otwórz formularz w **Windows Forms Designer**.

2.  Na **danych** menu, wybierz opcję **Dodaj zapytanie** lub **tagów inteligentnych danych**.

    > [!NOTE]
    > Jeśli **Dodaj zapytanie** nie jest dostępny na **danych** menu, wybierz formant w formularzu, wyświetla źródła danych, możesz chcesz dodać parametry do. Na przykład, jeśli w formularzu są wyświetlane dane w <xref:System.Windows.Forms.DataGridView> sterowania, wybierz ją. Jeśli w formularzu wyświetlane dane w poszczególnych formantów, wybierz dowolny formant powiązany z danymi.

3.  W **tabeli źródła danych wybierz** obszaru, wybierz tabelę, do której chcesz dodać parametryzacji.

4.  Wpisz nazwę w **Nowa nazwa zapytania** pole, jeśli tworzysz nową kwerendę.

     —lub—

     Wybierz zapytanie w **Ejąca nazwa zapytania** pole.

5.  W **tekst zapytania** wpisz kwerendę, która przyjmuje parametry.

6.  Kliknij przycisk **OK**.

     Co formantu, aby parametr wejściowy, a co **obciążenia** przycisk są dodawane do formularza w <xref:System.Windows.Forms.ToolStrip> kontroli.

### <a name="query-for-null-values"></a>Zapytanie o wartości null

Parametry TableAdapter można przypisać wartości null wyszukiwać rekordy, które nie mają żadnej wartości bieżącej. Na przykład, należy wziąć pod uwagę następujące zapytanie, które ma `ShippedDate` parametru w jego `WHERE` klauzuli:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Gdyby to zapytanie w metodzie TableAdapter, wysłać zapytanie o wszystkie zamówienia, które nie zostały wydane z następującym kodem:

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Aby włączyć zapytanie, aby akceptować wartości null:

1.  W **Projektanta obiektów Dataset**, wybierz zapytanie TableAdapter, które wymaga, aby zaakceptować wartości parametru o wartości null.

2.  W **właściwości** wybierz **parametry**, następnie kliknij przycisk wielokropka (**...** ) przycisk, aby otworzyć **Edytor kolekcji parametrów**.

3.  Wybierz parametr, który dopuszcza wartości null i ustaw **AllowDbNull** właściwość `true`.

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)