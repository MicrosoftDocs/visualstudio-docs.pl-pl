---
title: Omówienie Relational Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4105a93d4ad459c8bc1cb3a7a20b37c69f311c12
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566421"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Narzędzi LINQ to SQL w programie Visual Studio

LINQ do SQL była pierwszym technologii mapowania obiektowo relacyjny, wydane przez firmę Microsoft. Działa dobrze w przypadku podstawowych scenariuszy i może być obsługiwany w programie Visual Studio, ale nie jest już opracowywane active. Użyj programu LINQ to SQL podczas obsługi starszych aplikacji, który już jest używany lub w prostej aplikacji, użyj programu SQL Server, które nie wymagają mapowania wielu tabel. Ogólnie rzecz biorąc nowe aplikacje powinny używać programu Entity Framework, gdy wymagana jest warstwa Mapowania obiektowo relacyjny.

W programie Visual Studio, tworzyć LINQ do klas SQL, które reprezentują tabele SQL za pomocą **Object Relational Designer** (**O/R Designer**).

**O/R Designer** ma dwa różne obszary, na jego powierzchnię projektową: jednostki w okienku po lewej stronie, a okienko metod po prawej stronie. W okienku jednostek jest główna powierzchnia projektowa wyświetlającą klas jednostek, skojarzeń i hierarchii dziedziczenia. Okienko metod jest powierzchni projektu, który wyświetla <xref:System.Data.Linq.DataContext> metod, które są mapowane do procedur przechowywanych i funkcji.

**O/R Designer** udostępnia powierzchnia projektowania wizualnego służące do tworzenia [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) klasy encji i skojarzeń (relacji), które są oparte na obiektach w bazie danych. Innymi słowy **O/R Designer** tworzy model obiektu w aplikacji, która mapuje do obiektów w bazie danych. Polecenie to generuje także silnie typizowanego <xref:System.Data.Linq.DataContext> , wysyła i odbiera dane między klasami jednostki i bazy danych. **O/R Designer** również zapewnia funkcje procedurom składowanym w mapie i funkcje <xref:System.Data.Linq.DataContext> metody zwracający dane i wypełnianie klas jednostek. Na koniec **O/R Designer** zapewnia możliwość projektowania relacje dziedziczenia między klasami jednostki.

## <a name="open-the-or-designer"></a>Otwórz projektanta O/R

Aby dodać LINQ w modelu entity SQL do projektu, wybierz **projektu** > **Dodaj nowy element**, a następnie wybierz pozycję **klasy LINQ do SQL** z listy elementów projektu:

![Klasy LINQ do SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Program Visual Studio tworzy *dbml* plików i dodaje go do rozwiązania. Jest to plik mapowania XML i jego pliki kod pokrewny.

![Klasy LINQ do SQL w Eksploratorze rozwiązań](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Po wybraniu *dbml* pliku w Visual Studio Wyświetla **O/R Designer** powierzchni, która umożliwia wizualne Tworzenie modelu. Na poniższej ilustracji przedstawiono projektanta po Northwind `Customers` i `Orders` tabele mają zostało przeciągnięte z **Eksploratora serwera**. Należy pamiętać, relacji między tabelami.

![LINQ do SQL projektanta](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R Designer** jest mapowania relacyjnych prostego obiektu, ponieważ obsługuje on tylko relacji mapowanie 1:1. Innymi słowy klasa jednostka może mieć tylko relacji mapowanie 1:1 z tabeli bazy danych lub widoku. Mapowanie złożonych, takie jak mapowanie klasę jednostki do tabeli dołączonym do nie jest obsługiwana; na użytek złożonych mapowania Entity Framework. Ponadto projektanta jest generator kodu jednokierunkowe. Oznacza to, że tylko zmiany wprowadzone do powierzchni projektanta są odzwierciedlane w pliku kodu. Ręczne zmiany w pliku kodu nie są odzwierciedlane w **O/R Designer**. Wszelkie zmiany wprowadzone ręcznie w pliku kodu zostaną zastąpione, gdy projektant jest zapisywana i wygenerowania kodu. Aby uzyskać informacje o tym, jak dodać kod użytkownika i rozszerzać klasy generowane przez **O/R Designer**, zobacz [jak: Rozszerzanie kodu wygenerowanego przez projektanta O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Tworzenie i konfigurowanie kontekstu danych

Po dodaniu **klasy LINQ do SQL** elementu do projektu i Otwórz **O/R Designer**, powierzchni projektowej pusty reprezentuje pusty <xref:System.Data.Linq.DataContext> gotowe do skonfigurowania. <xref:System.Data.Linq.DataContext> jest skonfigurowany z informacjami o połączeniu, dostarczone przez pierwszy element, który jest zostało przeciągnięte na powierzchnię projektu. W związku z tym <xref:System.Data.Linq.DataContext> jest konfigurowana przy użyciu informacji o połączeniu z pierwszego elementu na powierzchni projektowej. Aby uzyskać więcej informacji na temat <xref:System.Data.Linq.DataContext> , zobacz klasę [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Tworzenie klas jednostek mapowane na bazę danych, tabele i widoki

Można utworzyć klasy jednostek zamapowanych na tabele i widoki, przeciągając bazy danych tabel i widoków z **Eksploratora serwera** lub **Eksplorator bazy danych** na **O/R Designer**. Jak wskazano w poprzedniej sekcji <xref:System.Data.Linq.DataContext> jest skonfigurowany z informacjami o połączeniu, dostarczone przez pierwszy element, który jest zostało przeciągnięte na powierzchnię projektu. Jeśli kolejne elementu, który używa innego połączenia jest dodawany do **O/R Designer**, można zmienić połączenia dla <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie typu LINQ do klas SQL zamapowanych na tabele i widoki (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Tworzenie metod DataContext, które wywołują procedur przechowywanych i funkcji

Możesz utworzyć <xref:System.Data.Linq.DataContext> metody, które wywołują (są mapowane na) procedur składowanych i funkcji, przeciągając je z **Eksploratora serwera** lub **Eksplorator bazy danych** na **Relational Designer** . Procedury składowane i funkcje, które są dodawane do **O/R Designer** jako metody <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Podczas przeciągania procedur przechowywanych i funkcji z **Eksploratora serwera** lub **Eksplorator bazy danych** na **O/R Designer**, zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda zależy od tego, gdzie można upuścić elementu. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurowanie DataContext zapisują dane pomiędzy klasami jednostki i bazy danych za pomocą procedur składowanych

Jak wspomniano wcześniej, możesz utworzyć <xref:System.Data.Linq.DataContext> metody, które wywołują procedur przechowywanych i funkcji. Ponadto można także przypisać procedur składowanych, które są używane do domyślnego LINQ to SQL zachowanie środowiska uruchomieniowego, które wykonuje wstawiania, aktualizacji i usuwania. Aby uzyskać więcej informacji, zobacz [jak: Przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Dziedziczenie i Relational designer

Podobnie jak inne obiekty można użyć dziedziczenia klasy LINQ do SQL i mogą pochodzić z innych klas. W bazie danych relacje dziedziczenia są tworzone na kilka sposobów. **O/R Designer** obsługuje dziedziczenia pojedynczej tabeli, co jest często stosowana w systemach relacyjnych. Aby uzyskać więcej informacji, zobacz [jak: Skonfigurować dziedziczenie za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Zapytania LINQ to SQL

Klas jednostek utworzonych przez **O/R Designer** są przeznaczone do użytku z programem [Language-Integrated query (LINQ)](/dotnet/csharp/linq/). Aby uzyskać więcej informacji, zobacz [jak: Zapytanie dotyczące informacji](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oddziel wygenerowanego kodu klasy DataContext i jednostek w różnych obszarach nazw

**O/R Designer** zapewnia **Namespace kontekstu** i **Namespace jednostki** właściwości <xref:System.Data.Linq.DataContext>. Te właściwości określają, jakie przestrzeni nazw <xref:System.Data.Linq.DataContext> i kodu klasy jednostki jest generowany na. Właściwości te są domyślnie pusta i <xref:System.Data.Linq.DataContext> i klas jednostek są generowane w przestrzeni nazw aplikacji. Aby wygenerować kod w przestrzeni nazw, innym niż przestrzeń nazw aplikacji, wprowadź wartość w **Namespace kontekstu** i/lub **Namespace jednostki** właściwości.

## <a name="reference-content"></a>Odwołania do zawartości

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Zobacz także

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Często zadawane pytania (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)