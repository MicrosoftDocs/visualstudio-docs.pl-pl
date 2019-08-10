---
title: Obiekty niestandardowe powiązane z danymi
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b9994d52c5ca39d744cf26dc019440e70e809ee8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925661"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Powiązywanie obiektów jako źródeł danych w programie Visual Studio

Visual Studio zapewnia narzędzia projektowania do pracy z niestandardowych obiektów jako źródło danych w aplikacji. Jeśli chcesz przechowywać dane z bazy danych w obiekcie, który możesz powiązać formanty interfejsu użytkownika, zalecanym podejściem jest używać programu Entity Framework do generowania klasy lub klas. Entity Framework automatycznie generuje cały kod standardowego śledzenia zmian, co oznacza, że wszelkie zmiany w obiektach lokalnych są automatycznie utrwalane w bazie danych po wywołaniu metody AcceptChanges w obiekcie Nieogólnymi. Aby uzyskać więcej informacji, zobacz [dokumentacja programu Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Podejścia do powiązania obiektów w tym artykule należy wziąć pod uwagę tylko wtedy, gdy aplikacja jest już oparta na zestawach danych. Możesz również użyć tych metod, jeśli znasz już zestawy danych, a dane, które będą przetwarzane, są tabelaryczne i nie są zbyt skomplikowane lub zbyt duże. Aby uzyskać przykład jeszcze prostsze, dotyczące ładowania danych bezpośrednio do obiektów przy użyciu elementu DataReader i ręczne aktualizowanie interfejsu użytkownika bez wiązania danych, zobacz [Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Wymagania dotyczące obiektu

Jedynym wymaganiem dla obiektów niestandardowych pracować z danymi narzędzia do projektowania w programie Visual Studio jest, że obiekt wymaga co najmniej jedną właściwość publiczną.

Ogólnie rzecz biorąc niestandardowe obiekty nie wymagają żadnych określonych interfejsów konstruktorów i atrybutów, które mają działać jako źródło danych dla aplikacji. Jednak jeśli chcesz przeciągnąć obiekt z **źródeł danych** okna do powierzchni projektu, aby utworzyć formant powiązany z danymi i jeśli obiekt implementuje <xref:System.ComponentModel.ITypedList> lub <xref:System.ComponentModel.IListSource> interfejsu, obiekt musi mieć domyślny Konstruktor. W przeciwnym razie program Visual Studio nie można utworzyć wystąpienia obiektu źródła danych, a następnie wyświetla komunikat o błędzie, jeśli przeciągniesz element do powierzchni projektowej.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Przykłady użycia niestandardowych obiektów jako źródła danych

Chociaż istnieją niezliczone sposoby implementacji logiki aplikacji podczas pracy z obiektami jako źródłem danych, w przypadku baz danych SQL istnieje kilka standardowych operacji, które można uprościć za pomocą obiektów TableAdapter utworzonych przez program Visual Studio. Na tej stronie wyjaśniono, jak zaimplementować te standardowe procesy przy użyciu TableAdapters. Nie jest on przeznaczony jako przewodnik tworzenia niestandardowych obiektów. Na przykład będzie zazwyczaj wykonywać następujące operacje standardowe niezależnie od konkretnej implementacji obiektów lub aplikacji logiki:

- Ładowanie danych w obiektach (zazwyczaj z bazy danych).

- Tworzenie typizowanego kolekcji obiektów.

- Dodawanie obiektów do i usuwanie obiektów z kolekcji.

- Dane obiektu są wyświetlane użytkownikom w formularzu.

- Zmienianie/edytowanie danych w obiekcie.

- Zapisywanie danych z obiektów w bazie danych.

### <a name="load-data-into-objects"></a>Ładowanie danych do obiektów

W tym przykładzie dane zostały załadowane do obiektów za pomocą adapterów TableAdapter. Domyślnie TableAdapters są tworzone za pomocą dwóch rodzajów metod, które pobierania danych z bazy danych i wypełnianie tabel danych.

- `TableAdapter.Fill` Metoda wypełni istniejącej tabeli danych z danymi zwracanymi.

- `TableAdapter.GetData` Metoda zwraca tabelę danych wypełniony danymi.

Najprostszym sposobem załadowania niestandardowych obiektów z danymi jest wywołać `TableAdapter.GetData` metody w pętli poprzez Kolekcja wierszy w tabeli zwracanych danych i wypełnić każdego obiektu z wartościami w każdym wierszu. Możesz utworzyć `GetData` metodę zwracającą tabelę danych wypełnione dla dowolnego zapytania, które dodano do TableAdapter.

> [!NOTE]
> Program Visual Studio domyślnie nazywa zapytania `Fill` `GetData` TableAdapter, ale można je zmienić na dowolną poprawną nazwę metody.

Poniższy przykład pokazuje, jak w pętli poprzez wierszy w tabeli danych w celu wypełnienia obiektu z danymi:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Tworzenie typizowanego kolekcji obiektów

Można tworzyć klasy kolekcji dla obiektów lub używać kolekcji z określonym typem, które są automatycznie dostarczane przez [Składnik BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Podczas tworzenia niestandardowej klasy kolekcji dla obiektów, zalecamy, aby dziedziczyć z <xref:System.ComponentModel.BindingList%601>. Ta klasa ogólna zapewnia funkcje do administrowania kolekcji, a także możliwość wywoływać zdarzenia, które wysyłać powiadomienia do infrastruktury powiązanie danych w formularzach Windows Forms.

Automatycznie wygenerowana kolekcja w programie <xref:System.Windows.Forms.BindingSource> <xref:System.ComponentModel.BindingList%601> używa dla swojej kolekcji z określonym typem. Jeśli aplikacja nie wymaga dodatkowych funkcji, można zachować swoją kolekcję w ramach programu <xref:System.Windows.Forms.BindingSource>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.BindingSource.List%2A> właściwość <xref:System.Windows.Forms.BindingSource> klasy.

> [!NOTE]
> Jeśli Twoja kolekcja wymaga funkcji, nie został dostarczony przez implementację podstawową <xref:System.ComponentModel.BindingList%601>, należy utworzyć kolekcję niestandardową, więc można dodać do klasy, zgodnie z potrzebami.

Poniższy kod przedstawia sposób tworzenia klasy kolekcji silnie typizowane `Order` obiektów:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Dodawanie obiektów do kolekcji

Dodać obiekty do kolekcji, wywołując `Add` metody klasy kolekcji niestandardowej lub z <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Add` Metody jest dostarczana automatycznie dla niestandardowej kolekcji, gdy dziedziczą z <xref:System.ComponentModel.BindingList%601>.

Poniższy kod przedstawia sposób dodawania obiektów do typizowaną kolekcją w <xref:System.Windows.Forms.BindingSource>:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

Poniższy kod przedstawia sposób dodawania obiektów do typizowaną kolekcją, której dziedziczy <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> W tym przykładzie `Orders` kolekcja jest właściwością `Customer` obiektu.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Usuwanie obiektów z kolekcji

Usuwanie obiektów z kolekcji, wywołując `Remove` lub `RemoveAt` metody klasy kolekcji niestandardowej lub z <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Remove` i `RemoveAt` metody automatycznie dostarczane dla niestandardowej kolekcji dziedziczą z <xref:System.ComponentModel.BindingList%601>.

Poniższy kod przedstawia sposób Znajdź i usuwanie obiektów z kontrolą typów kolekcji w <xref:System.Windows.Forms.BindingSource> z <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> metody:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Wyświetlanie danych obiektu dla użytkowników

Aby wyświetlić dane w obiekty do użytkowników, tworzenie obiektu źródła danych przy użyciu **konfiguracji źródła danych** kreatora, a następnie przeciągnij indywidualne właściwości lub cały obiekt na formularz z **źródeł danych**okna.

### <a name="modify-the-data-in-objects"></a>Modyfikowanie danych w obiektach

Aby edytować danych w obiektach niestandardowych, które są powiązane z danymi do kontrolek formularzy Windows Forms, prosto edytować dane w powiązanej kontrolki (lub bezpośrednio we właściwościach obiektu). Powiązanie danych architektury aktualizuje dane w obiekcie.

Jeśli aplikacja wymaga śledzenia zmian i stopniowe tylnej stronie proponowanych zmian do ich oryginalnych wartości, musisz zaimplementować tę funkcję w modelu obiektu. Przykłady sposobu tabel danych śledzenie pracy proponowane, zobacz <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, i <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Zapisz dane w obiektach z powrotem w bazie danych

Zapisywanie danych w bazie danych przez przekazanie wartości z obiektu do TableAdapter dbdirect — metody.

Program Visual Studio tworzy dbdirect — metody, które mogą być wykonywane bezpośrednio w bazie danych. Te metody nie wymagają obiektów DataSet lub DataTable.

|TableAdapter dbdirect — metody|Opis|
| - |-----------------|
|`TableAdapter.Insert`|Dodaje nowe rekordy w bazie danych, dzięki czemu możesz podawać wartości poszczególnych kolumn jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. Metoda aktualizacji przyjmuje wartości oryginalnego i nowych kolumn jako parametry metody. Oryginalne wartości są używane do lokalizowania oryginalnego rekordu, a nowe wartości są używane na zaktualizowanie rekordu.<br /><br /> `TableAdapter.Update` Metoda umożliwia również uzgadniają zmiany w zestawie danych w bazie danych, wykonując <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, tablica lub <xref:System.Data.DataRow>określane jako parametry metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych oparte na oryginalnych wartości kolumny przekazanych jako parametry metody.|

Aby zapisać dane z kolekcji obiektów, należy wykonać pętlę przez kolekcję obiektów (na przykład przy użyciu pętli for Next). Wyślij wartości dla każdego obiektu do bazy danych przy użyciu metod DBDirect TableAdapter.

Poniższy przykład pokazuje, jak używać `TableAdapter.Insert` dbdirect — metody w celu dodania nowego klienta bezpośrednio do bazy danych:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)