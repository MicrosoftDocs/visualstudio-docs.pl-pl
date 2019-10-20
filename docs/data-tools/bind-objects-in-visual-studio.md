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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2b046eaa4244d08c9fff9e2412471d018203de42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648799"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Powiązywanie obiektów jako źródeł danych w programie Visual Studio

Program Visual Studio oferuje narzędzia czasu projektowania umożliwiające pracę z obiektami niestandardowymi jako źródło danych w aplikacji. Aby można było przechowywać dane z bazy danych w obiekcie, który można powiązać z kontrolkami interfejsu użytkownika, Zalecanym podejściem jest użycie Entity Framework do wygenerowania klasy lub klas. Entity Framework automatycznie generuje cały kod standardowego śledzenia zmian, co oznacza, że wszelkie zmiany w obiektach lokalnych są automatycznie utrwalane w bazie danych po wywołaniu metody AcceptChanges w obiekcie Nieogólnymi. Aby uzyskać więcej informacji, zobacz [dokumentację Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Podejścia do powiązania obiektów w tym artykule należy wziąć pod uwagę tylko wtedy, gdy aplikacja jest już oparta na zestawach danych. Możesz również użyć tych metod, jeśli znasz już zestawy danych, a dane, które będą przetwarzane, są tabelaryczne i nie są zbyt skomplikowane lub zbyt duże. Aby uzyskać jeszcze uproszczony przykład obejmujący ładowanie danych bezpośrednio do obiektów przy użyciu elementu DataReader i ręczne aktualizowanie interfejsu użytkownika bez wiązania z danymi, zobacz [Tworzenie prostej aplikacji danych za pomocą ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Wymagania dotyczące obiektów

Jedynym wymaganiem dla obiektów niestandardowych do pracy z narzędziami do projektowania danych w programie Visual Studio jest to, że obiekt potrzebuje co najmniej jednej właściwości publicznej.

Ogólnie rzecz biorąc, obiekty niestandardowe nie wymagają żadnych określonych interfejsów, konstruktorów ani atrybutów do działania jako źródło danych aplikacji. Jeśli jednak chcesz przeciągnąć obiekt z okna **źródła danych** na powierzchnię projektu, aby utworzyć kontrolkę powiązaną z danymi, a jeśli obiekt implementuje interfejs <xref:System.ComponentModel.ITypedList> lub <xref:System.ComponentModel.IListSource>, obiekt musi mieć domyślny Konstruktor. W przeciwnym razie program Visual Studio nie może utworzyć wystąpienia obiektu źródła danych i po przeciągnięciu elementu na powierzchnię projektu zostanie wyświetlony komunikat o błędzie.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Przykłady użycia obiektów niestandardowych jako źródeł danych

Chociaż istnieją niezliczone sposoby implementacji logiki aplikacji podczas pracy z obiektami jako źródłem danych, w przypadku baz danych SQL istnieje kilka standardowych operacji, które można uprościć za pomocą obiektów TableAdapter utworzonych przez program Visual Studio. Na tej stronie wyjaśniono, jak zaimplementować te standardowe procesy przy użyciu TableAdapters. Nie jest on przeznaczony jako przewodnik tworzenia niestandardowych obiektów. Na przykład zwykle wykonywane są następujące operacje standardowe, niezależnie od określonej implementacji obiektów lub logiki aplikacji:

- Ładowanie danych do obiektów (zazwyczaj z bazy danych).

- Tworzenie kolekcji obiektów o określonym typie.

- Dodawanie obiektów do i usuwanie obiektów z kolekcji.

- Wyświetlanie danych obiektu dla użytkowników w formularzu.

- Zmiana/edytowanie danych w obiekcie.

- Zapisywanie danych z obiektów z powrotem w bazie danych.

### <a name="load-data-into-objects"></a>Ładowanie danych do obiektów

Na potrzeby tego przykładu dane są ładowane do obiektów przy użyciu TableAdapters. Domyślnie TableAdapters są tworzone z dwoma rodzajami metod, które pobierają dane z bazy danych i wypełniają tabele danych.

- Metoda `TableAdapter.Fill` wypełnia istniejącą tabelę danych z zwróconymi danymi.

- Metoda `TableAdapter.GetData` zwraca nową tabelę danych wypełnioną danymi.

Najprostszym sposobem ładowania obiektów niestandardowych za pomocą danych jest wywołanie metody `TableAdapter.GetData`, pętla w kolekcji wierszy w zwróconej tabeli danych i wypełnienie każdego obiektu wartościami w każdym wierszu. Można utworzyć metodę `GetData`, która zwraca wypełnioną tabelę danych dla dowolnego zapytania dodanego do TableAdapter.

> [!NOTE]
> Program Visual Studio domyślnie nazywa `Fill` i `GetData`e zapytania TableAdapter, ale można je zmienić na dowolną poprawną nazwę metody.

Poniższy przykład pokazuje, jak przechodzić przez wiersze w tabeli danych i wypełnić obiekt danymi:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Tworzenie kolekcji obiektów o określonym typie

Można tworzyć klasy kolekcji dla obiektów lub używać kolekcji z określonym typem, które są automatycznie dostarczane przez [Składnik BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Podczas tworzenia niestandardowej klasy kolekcji dla obiektów, sugerujemy, aby dziedziczyć z <xref:System.ComponentModel.BindingList%601>. Ta Klasa ogólna zapewnia funkcje do administrowania kolekcją oraz możliwość zgłaszania zdarzeń wysyłających powiadomienia do infrastruktury powiązań danych w Windows Forms.

Automatycznie wygenerowana kolekcja w <xref:System.Windows.Forms.BindingSource> używa <xref:System.ComponentModel.BindingList%601> dla swojej kolekcji z określonym typem. Jeśli aplikacja nie wymaga dodatkowych funkcji, możesz zachować swoją kolekcję w <xref:System.Windows.Forms.BindingSource>. Aby uzyskać więcej informacji, zobacz Właściwość <xref:System.Windows.Forms.BindingSource.List%2A> klasy <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Jeśli kolekcja wymaga funkcjonalności niedostarczonej przez podstawową implementację <xref:System.ComponentModel.BindingList%601>, należy utworzyć kolekcję niestandardową, tak aby można ją było dodać do klasy zgodnie z potrzebami.

Poniższy kod przedstawia sposób tworzenia klasy dla kolekcji o jednoznacznie określonym typie `Order` obiektów:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Dodawanie obiektów do kolekcji

Aby dodać obiekty do kolekcji, należy wywołać metodę `Add` niestandardowej klasy kolekcji lub <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Metoda `Add` jest udostępniana automatycznie dla kolekcji niestandardowej podczas dziedziczenia z <xref:System.ComponentModel.BindingList%601>.

Poniższy kod przedstawia sposób dodawania obiektów do kolekcji z określonym typem w <xref:System.Windows.Forms.BindingSource>:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

Poniższy kod przedstawia sposób dodawania obiektów do kolekcji z określonym typem, która dziedziczy po <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> W tym przykładzie kolekcja `Orders` jest właściwością obiektu `Customer`.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Usuwanie obiektów z kolekcji

Obiekty z kolekcji są usuwane przez wywołanie metody `Remove` lub `RemoveAt` niestandardowej klasy kolekcji lub <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Metody `Remove` i `RemoveAt` są automatycznie udostępniane dla kolekcji niestandardowej podczas dziedziczenia po <xref:System.ComponentModel.BindingList%601>.

Poniższy kod przedstawia sposób lokalizowania i usuwania obiektów z kolekcji z określonym typem w <xref:System.Windows.Forms.BindingSource> przy użyciu metody <xref:System.Windows.Forms.BindingSource.RemoveAt%2A>:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Wyświetlanie danych obiektu dla użytkowników

Aby wyświetlić dane w obiektach dla użytkowników, Utwórz źródło danych obiektu za pomocą kreatora **konfiguracji źródła danych** , a następnie przeciągnij cały obiekt lub poszczególne właściwości do formularza z okna **źródła danych** .

### <a name="modify-the-data-in-objects"></a>Modyfikowanie danych w obiektach

Aby edytować dane w obiektach niestandardowych, które są powiązane danymi z kontrolkami Windows Forms, wystarczy edytować dane w formancie powiązanym (lub bezpośrednio we właściwościach obiektu). Architektura powiązania danych aktualizuje dane w obiekcie.

Jeśli aplikacja wymaga śledzenia zmian i wycofywania proponowanych zmian do ich oryginalnych wartości, należy zaimplementować tę funkcję w modelu obiektów. Aby zapoznać się z przykładami, jak tabele danych śledzą proponowane zmiany, zobacz <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> i <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Zapisz dane w obiektach z powrotem w bazie danych

Zapisz dane z powrotem w bazie danych, przekazując wartości z obiektu do metod DBDirect TableAdapter.

Program Visual Studio tworzy metody DBDirect, które mogą być wykonywane bezpośrednio w bazie danych. Te metody nie wymagają obiektów DataSet i DataTable.

|TableAdapter DBDirect — Metoda|Opis|
| - |-----------------|
|`TableAdapter.Insert`|Dodaje nowe rekordy do bazy danych, co umożliwia przekazywanie wartości poszczególnych kolumn jako parametrów metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. Metoda Update pobiera oryginalne i nowe wartości kolumn jako parametry metody. Oryginalne wartości są używane do lokalizowania oryginalnego rekordu, a nowe wartości są używane do aktualizowania tego rekordu.<br /><br /> Metoda `TableAdapter.Update` służy również do uzgadniania zmian w zestawie danych z powrotem do bazy danych, pobierając <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> lub tablicę <xref:System.Data.DataRow>s jako parametry metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych na podstawie wartości pierwotnej kolumny przekazaną jako parametry metody.|

Aby zapisać dane z kolekcji obiektów, należy wykonać pętlę przez kolekcję obiektów (na przykład przy użyciu pętli for Next). Wyślij wartości dla każdego obiektu do bazy danych przy użyciu metod DBDirect TableAdapter.

W poniższym przykładzie pokazano, jak za pomocą metody `TableAdapter.Insert` DBDirect dodać nowego klienta bezpośrednio do bazy danych:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)