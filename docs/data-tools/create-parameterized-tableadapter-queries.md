---
title: Tworzenie sparametryzowanych zapytań adaptera TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a2b94e10dd09d26a17a7574db97880567f7725cd
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282608"
---
# <a name="create-parameterized-tableadapter-queries"></a>Tworzenie sparametryzowanych zapytań adaptera TableAdapter

Zapytanie sparametryzowane zwraca dane, które spełniają warunki klauzuli WHERE w zapytaniach. Na przykład możesz Sparametryzuj listę klientów, aby wyświetlić tylko klientów w określonym mieście przez dodanie `WHERE City = @City` do końca instrukcji SQL, która zwraca listę klientów.

W **Projektant obiektów DataSet**można tworzyć sparametryzowane zapytania TableAdapter. Można je również utworzyć w aplikacji systemu Windows za pomocą polecenia **Sparametryzuj źródło danych** w menu **dane** . Polecenie **Sparametryzuj Data Source** tworzy kontrolki w formularzu, gdzie można wprowadzać wartości parametrów i uruchamiać zapytanie.

> [!NOTE]
> Podczas konstruowania zapytania parametrycznego należy użyć notacji parametru, która jest specyficzna dla bazy danych, względem której jest używane kodowanie. Na przykład źródła danych dostępu i OleDb używają znaku zapytania "?" do określenia parametrów, więc klauzula WHERE będzie wyglądać następująco: `WHERE City = ?` .

## <a name="create-a-parameterized-tableadapter-query"></a>Tworzenie sparametryzowanych zapytań TableAdapter

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Aby utworzyć zapytanie sparametryzowane w Projektant obiektów Dataset

- Utwórz nowy TableAdapter, dodając klauzulę WHERE z odpowiednimi parametrami do instrukcji SQL. Aby uzyskać więcej informacji, zobacz [Tworzenie i Konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     -lub-

- Dodaj zapytanie do istniejącego TableAdapter, dodając klauzulę WHERE z odpowiednimi parametrami do instrukcji SQL.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Aby utworzyć zapytanie parametryczne podczas projektowania formularza powiązanego z danymi

1. Wybierz kontrolkę w formularzu, która jest już powiązana z zestawem danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. W menu **dane** wybierz polecenie **Dodaj zapytanie**.

3. Wypełnij okno dialogowe **Konstruktor kryteriów wyszukiwania** , dodając klauzulę WHERE z odpowiednimi parametrami do instrukcji SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Aby dodać zapytanie do istniejącego formularza powiązanego z danymi

1. Otwórz formularz w **Projektant formularzy systemu Windows**.

2. W menu **dane** wybierz pozycję **Dodaj zapytanie** lub **Tagi inteligentne danych**.

    > [!NOTE]
    > Jeśli polecenie **Dodaj zapytanie** nie jest dostępne w menu **dane** , zaznacz kontrolkę w formularzu wyświetlającym źródło danych, do którego chcesz dodać parametryzacja. Na przykład, jeśli formularz wyświetla dane w <xref:System.Windows.Forms.DataGridView> kontrolce, zaznacz ją. Jeśli formularz wyświetla dane w poszczególnych kontrolkach, wybierz dowolny formant powiązany z danymi.

3. W obszarze **Wybierz tabelę źródła danych** wybierz tabelę, do której chcesz dodać parametryzacja.

4. Wpisz nazwę w polu **Nowa nazwa zapytania** , jeśli tworzysz nowe zapytanie.

     -lub-

     W polu **Nazwa istniejącej kwerendy** wybierz zapytanie.

5. W polu **tekstowym zapytanie** Wpisz zapytanie, które pobiera parametry.

6. Wybierz przycisk **OK**.

     Kontrolka do wprowadzania parametru i przycisk **ładowania** są dodawane do formularza w <xref:System.Windows.Forms.ToolStrip> kontrolce.

### <a name="query-for-null-values"></a>Zapytanie o wartości null

Parametry TableAdapter mogą mieć przypisane wartości null, jeśli chcesz wysyłać zapytania o rekordy, które nie mają bieżącej wartości. Rozważmy na przykład następujące zapytanie, które ma `ShippedDate` parametr w jego `WHERE` klauzuli:

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Jeśli było to zapytanie w TableAdapter, można wykonać zapytanie o wszystkie zamówienia, które nie zostały dostarczone z następującym kodem:

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Aby włączyć akceptowanie przez zapytanie wartości null:

1. W **Projektant obiektów DataSet**wybierz zapytanie TableAdapter, które wymaga zaakceptowania wartości parametrów null.

2. W oknie **Właściwości** wybierz opcję **Parametry**, a następnie kliknij przycisk wielokropka (**...**), aby otworzyć **Edytor kolekcji parametrów**.

3. Wybierz parametr, który dopuszcza wartości null i ustaw właściwość **AllowDBNull** na `true` .

## <a name="see-also"></a>Zobacz też

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
