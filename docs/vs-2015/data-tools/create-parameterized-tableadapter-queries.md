---
title: Tworzenie sparametryzowanych zapytań adaptera TableAdapter
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 560587e70365a485c3391a0623b959f88d417698
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671059"
---
# <a name="create-parameterized-tableadapter-queries"></a>Tworzenie sparametryzowanych zapytań adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapytanie sparametryzowane zwraca dane, które spełniają warunki klauzuli WHERE w zapytaniach. Na przykład możesz Sparametryzuj listę klientów, aby wyświetlić tylko klientów w określonym mieście, dodając `WHERE City = @City` na końcu instrukcji SQL, która zwraca listę klientów.

W Projektant obiektów Dataset można tworzyć sparametryzowane zapytania TableAdapter. Można je również utworzyć w aplikacji systemu Windows za pomocą polecenia **Sparametryzuj źródło danych** w menu **dane** . Polecenie **Sparametryzuj Data Source** tworzy kontrolki w formularzu, gdzie można wprowadzać wartości parametrów i uruchamiać zapytanie.

> [!NOTE]
> Podczas konstruowania zapytania parametrycznego należy użyć notacji parametru, która jest specyficzna dla bazy danych, względem której jest używane kodowanie. Na przykład źródła danych dostępu i OleDb używają znaku zapytania "?" do określenia parametrów, więc klauzula WHERE będzie wyglądać następująco: `WHERE City = ?`.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub używanej wersji. Aby zmienić ustawienia, przejdź do menu **Narzędzia** , a następnie wybierz pozycję **Importuj i Eksportuj ustawienia**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-parameterized-tableadapter-query"></a>Tworzenie sparametryzowanych zapytań TableAdapter

- Utwórz nowy TableAdapter, dodając klauzulę WHERE z odpowiednimi parametrami do instrukcji SQL. Aby uzyskać więcej informacji, zobacz [Tworzenie i Konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     —lub—

- Dodaj zapytanie do istniejącego TableAdapter, dodając klauzulę WHERE z odpowiednimi parametrami do instrukcji SQL.

### <a name="create-a-parameterized-query-while-designing-a-data-bound-form"></a>Utwórz zapytanie parametryczne podczas projektowania formularza powiązanego z danymi

1. Wybierz kontrolkę w formularzu, która jest już powiązana z zestawem danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. W menu **dane** wybierz polecenie**Dodaj zapytanie**.

3. Wypełnij okno dialogowe **Konstruktor kryteriów wyszukiwania** , dodając klauzulę WHERE z odpowiednimi parametrami do instrukcji SQL.

### <a name="add-a-query-to-an-existing-data-bound-form"></a>Dodawanie zapytania do istniejącego formularza powiązanego z danymi

1. Otwórz formularz w **Projektant formularzy systemu Windows**.

2. W menu **dane** wybierz pozycję **Dodaj zapytanie** lub **Tagi inteligentne danych**.

   > [!NOTE]
   > Jeśli polecenie **Dodaj zapytanie** nie jest dostępne w menu **dane** , zaznacz kontrolkę w formularzu wyświetlającym źródło danych, do którego chcesz dodać parametryzacja. Na przykład, jeśli formularz wyświetla dane w kontrolce <xref:System.Windows.Forms.DataGridView>, zaznacz ją. Jeśli formularz wyświetla dane w poszczególnych kontrolkach, wybierz dowolny formant powiązany z danymi.

3. W obszarze **Wybierz tabelę źródła danych** wybierz tablethat, do którego chcesz dodać parametryzacja.

4. Wpisz nazwę w polu **Nowa nazwa zapytania** , jeśli tworzysz nowe zapytanie.

    —lub—

    W polu **Nazwa istniejącej kwerendy** wybierz zapytanie.

5. W polu **tekstowym zapytanie** Wpisz zapytanie, które pobiera parametry.

6. Wybierz **przycisk OK**.

    Kontrolka do wprowadzania parametru i przycisk **ładowania** są dodawane do formularza w kontrolce <xref:System.Windows.Forms.ToolStrip>.

   Parametry TableAdapter mogą mieć przypisane wartości null, jeśli chcesz wysyłać zapytania o rekordy, które nie mają bieżącej wartości. Rozważmy na przykład następujące zapytanie, które ma `ShippedDate` parametr w jego klauzuli `WHERE`:

   ```sql
   SELECT CustomerID, OrderDate, ShippedDate
   FROM Orders
   WHERE (ShippedDate = @ShippedDate) OR
   (ShippedDate IS NULL)
   ```

Jeśli było to zapytanie w TableAdapter, można wykonać zapytanie o wszystkie zamówienia, które nie zostały dostarczone z następującym kodem:

   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]

### <a name="enable-a-query-to-accept-null-values"></a>Włącz zapytanie, aby akceptowało wartości null

1. W **Projektant obiektów DataSet**wybierz zapytanie TableAdapter, które wymaga zaakceptowania wartości parametrów null.

2. W oknie **Właściwości** wybierz pozycję **Parametry**. Następnie naciśnij przycisk wielokropka ( **...** ), aby otworzyć **Edytor kolekcji parametrów**.

3. Wybierz parametr, który dopuszcza wartości null i ustaw właściwość **AllowDBNull** na `true`.

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)