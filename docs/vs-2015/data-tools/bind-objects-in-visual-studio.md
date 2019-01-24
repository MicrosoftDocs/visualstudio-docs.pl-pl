---
title: Powiązanie obiektów
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dedfc71636983a9cbe634551a88eb3de45cb1d99
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776878"
---
# <a name="bind-objects-in-visual-studio"></a>Powiązanie obiektów w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio zapewnia narzędzia projektowania do pracy z niestandardowych obiektów jako źródło danych w aplikacji. Jeśli chcesz przechowywać dane z bazy danych w obiekcie, który możesz powiązać formanty interfejsu użytkownika, zalecanym podejściem jest używać programu Entity Framework do generowania klasy lub klas. Jednostka Frameworkautogenerates wszystkich standardowy śledzenia zmian kodu, co oznacza, że wszelkie zmiany lokalne obiekty automatycznie są zachowywane do bazy danych, po wywołaniu funkcji AcceptChanges w obiekcie DbSet.    Aby uzyskać więcej informacji, zobacz [dokumentacja programu Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
>  Podejścia do powiązania obiektu, w tym artykule należy rozważyć tylko, jeśli aplikacja już opiera się na zestawach danych. Te metody mogą również jeśli już znasz z zestawami danych, a dane, które będą przetwarzać jest tabelarycznym i nie jest zbyt złożony lub zbyt duży. Aby uzyskać przykład jeszcze prostsze, dotyczące ładowania danych bezpośrednio do obiektów przy użyciu elementu DataReader i ręczne aktualizowanie interfejsu użytkownika bez wiązania danych, zobacz [Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Wymagania dotyczące obiektu
 Jedynym wymaganiem dla obiektów niestandardowych pracować z danymi narzędzia do projektowania w programie Visual Studio jest, że obiekt wymaga co najmniej jedną właściwość publiczną.

 Ogólnie rzecz biorąc niestandardowe obiekty nie wymagają żadnych określonych interfejsów konstruktorów i atrybutów, które mają działać jako źródło danych dla aplikacji. Jednak jeśli chcesz przeciągnąć obiekt z **źródeł danych** okna do powierzchni projektu, aby utworzyć formant powiązany z danymi i jeśli obiekt implementuje <xref:System.ComponentModel.ITypedList> lub <xref:System.ComponentModel.IListSource> interfejsu, obiekt musi mieć domyślny Konstruktor. W przeciwnym razie program Visual Studio nie można utworzyć wystąpienia obiektu źródła danych, a następnie wyświetla komunikat o błędzie, jeśli przeciągniesz element do powierzchni projektowej.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Przykłady użycia niestandardowych obiektów jako źródła danych
 Są niezliczone sposoby zaimplementować logikę aplikacji, podczas pracy z obiektami jako źródło danych, SQL bazy danych są kilka standardowych operacji, które można uprościć za pomocą obiektów TableAdapter generowane — Visual Studio. Tej stronie wyjaśniamy sposób implementacji tych standardowych procesów przy użyciu TableAdapters.It nie jest przeznaczony jako wskazówki dotyczące tworzenia niestandardowych obiektów. Na przykład będzie zazwyczaj wykonywać następujące operacje standardowe niezależnie od konkretnej implementacji obiektów lub aplikacji logiki:

-   Ładowanie danych w obiektach (zazwyczaj z bazy danych).

-   Tworzenie typizowanego kolekcji obiektów.

-   Dodawanie obiektów do i usuwanie obiektów z kolekcji.

-   Dane obiektu są wyświetlane użytkownikom w formularzu.

-   Zmienianie/edytowanie danych w obiekcie.

-   Zapisywanie danych z obiektów w bazie danych.

> [!NOTE]
>  Aby lepiej zrozumieć i dostarczanie kontekstu przykładach na tej stronie, zalecamy wykonanie następujących czynności: [Przewodnik: O łączeniu z danymi w obiektach (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Ten przewodnik tworzy obiekty omówionych w tym miejscu.

### <a name="loaddata-into-objects"></a>Loaddata na obiekty
 W tym przykładzie dane zostały załadowane do obiektów za pomocą adapterów TableAdapter. Domyślnie TableAdapters są tworzone za pomocą dwóch rodzajów metod, które pobierania danych z bazy danych i wypełnianie tabel danych.

- `TableAdapter.Fill` Metoda wypełni istniejącej tabeli danych z danymi zwracanymi.

- `TableAdapter.GetData` Metoda zwraca tabelę danych wypełniony danymi.

  Najprostszym sposobem załadowania niestandardowych obiektów z danymi jest wywołać `TableAdapter.GetData` metody w pętli poprzez Kolekcja wierszy w tabeli zwracanych danych i wypełnić każdego obiektu z wartościami w każdym wierszu. Możesz utworzyć `GetData` metodę zwracającą tabelę danych wypełnione dla dowolnego zapytania, które dodano do TableAdapter.

> [!NOTE]
>  Visual Studio nazw zapytań TableAdapter `Fill` i `GetData` domyślnie, ale można zmienić tych nazw z nazwą prawidłowej metody.

 Poniższy przykład pokazuje, jak w pętli poprzez wierszy w tabeli danych w celu wypełnienia obiektu z danymi:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Tworzenie typizowanego kolekcji obiektów
 Tworzenie klas kolekcji dla obiektów, lub użyj kolekcje wpisane, które są automatycznie udostępniane przez [BindingSource, składnik](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Tworząc klasę kolekcji niestandardowej dla obiektów, zaleca się dziedziczenie z <xref:System.ComponentModel.BindingList%601>. Ta klasa ogólna zapewnia funkcje do administrowania kolekcji, a także możliwość wywoływać zdarzenia, które wysyłać powiadomienia do infrastruktury powiązanie danych w formularzach Windows Forms.

 Automatycznie generowanych przez kolekcję w <xref:System.Windows.Forms.BindingSource> używa <xref:System.ComponentModel.BindingList%601> dla jego typizowaną kolekcją. Jeśli aplikacja nie wymaga dodatkowych funkcji, a następnie może zachować kolekcji w ramach <xref:System.Windows.Forms.BindingSource>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.BindingSource.List%2A> właściwość <xref:System.Windows.Forms.BindingSource> klasy.

> [!NOTE]
>  Jeśli Twoja kolekcja wymaga funkcji, nie został dostarczony przez implementację podstawową <xref:System.ComponentModel.BindingList%601>, należy utworzyć kolekcję niestandardową, więc można dodać do klasy, zgodnie z potrzebami.

 Poniższy kod przedstawia sposób tworzenia klasy kolekcji silnie typizowane `Order` obiektów:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects do kolekcji
 Dodać obiekty do kolekcji, wywołując `Add` metody klasy kolekcji niestandardowej lub z <xref:System.Windows.Forms.BindingSource>.

 Na przykład dodanie do kolekcji za pomocą <xref:System.Windows.Forms.BindingSource>, zobacz `LoadCustomers` method in Class metoda [instruktażu: O łączeniu z danymi w obiektach (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Na przykład dodawania obiektów do niestandardowej kolekcji, zobacz `LoadOrders` method in Class metoda [instruktażu: O łączeniu z danymi w obiektach (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
>  `Add` Metody jest dostarczana automatycznie dla niestandardowej kolekcji, gdy dziedziczą z <xref:System.ComponentModel.BindingList%601>.

 Poniższy kod przedstawia sposób dodawania obiektów do typizowaną kolekcją w <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Poniższy kod przedstawia sposób dodawania obiektów do typizowaną kolekcją, której dziedziczy <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
>  W tym przykładzie `Orders` kolekcji jest właściwością `Customer` obiektu.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Removeobjects z kolekcji
 Usuwanie obiektów z kolekcji, wywołując `Remove` lub `RemoveAt` metody klasy kolekcji niestandardowej lub z <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
>  `Remove` i `RemoveAt` metody automatycznie dostarczane dla niestandardowej kolekcji dziedziczą z <xref:System.ComponentModel.BindingList%601>.

 Poniższy kod przedstawia sposób Znajdź i usuwanie obiektów z kontrolą typów kolekcji w <xref:System.Windows.Forms.BindingSource> z <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> metody:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>Dane DisplayObject użytkownikom
 Aby wyświetlić dane w obiekty do użytkowników, tworzenie obiektu źródła danych przy użyciu **konfiguracji źródła danych** kreatora, a następnie przeciągnij indywidualne właściwości lub cały obiekt na formularz z **źródeł danych**okna.

### <a name="modify-the-data-in-objects"></a>Modyfikowanie danych w obiektach
 Aby edytować danych w obiektach niestandardowych, które są powiązane z danymi do kontrolek formularzy Windows Forms, prosto edytować dane w powiązanej kontrolki (lub bezpośrednio we właściwościach obiektu). Powiązanie danych architektury aktualizuje dane w obiekcie.

 Jeśli aplikacja wymaga śledzenia zmian i stopniowe tylnej stronie proponowanych zmian do ich oryginalnych wartości, musisz zaimplementować tę funkcję w modelu obiektu. Przykłady sposobu tabel danych śledzenie pracy proponowane, zobacz <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, i <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData w obiektach w bazie danych
 Zapisywanie danych w bazie danych przez przekazanie wartości z obiektu do TableAdapter dbdirect — metody.

 Program Visual Studio tworzy dbdirect — metody, które mogą być wykonywane bezpośrednio w bazie danych. Te metody nie wymagają obiektów DataSet lub DataTable.

|TableAdapter dbdirect — metody|Opis|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Dodaje nowe rekordy w bazie danych, dzięki czemu możesz podawać wartości poszczególnych kolumn jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. Metoda aktualizacji przyjmuje wartości oryginalnego i nowych kolumn jako parametry metody. Oryginalne wartości są używane do lokalizowania oryginalnego rekordu, a nowe wartości są używane na zaktualizowanie rekordu.<br /><br /> `TableAdapter.Update` Metoda umożliwia również uzgadniają zmiany w zestawie danych w bazie danych, wykonując <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, tablica lub <xref:System.Data.DataRow>określane jako parametry metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych oparte na oryginalnych wartości kolumny przekazanych jako parametry metody.|

 Aby zapisać dane z kolekcji obiektów, w pętli poprzez kolekcji obiektów (na przykład za pomocą pętli for dalej). Wyślij wartości dla każdego obiektu do bazy danych za pomocą TableAdapter dbdirect — metody.

 Poniższy przykład pokazuje, jak używać `TableAdapter.Insert` dbdirect — metody w celu dodania nowego klienta bezpośrednio do bazy danych:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
