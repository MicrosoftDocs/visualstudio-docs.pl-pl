---
title: Używanie procedur składowanych w składniku LINQ to SQL, aby zaktualizować dane (O/R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 58dfb1016097429eeab10c3b50262adc7015e818
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260796"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)

Procedury składowane mogą być dodawane do **O/R Designer** i wykonywane co typowe <xref:System.Data.Linq.DataContext> metody. One może również zastąpić to ustawienie domyślne LINQ do zachowania w czasie wykonywania SQL wykonuje operacje wstawiania, aktualizacji i usuwa podczas zmiany są zapisywane z klas jednostek bazy danych (na przykład w przypadku, gdy wywołanie <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody).

> [!NOTE]
> Jeśli Twoja procedura składowana ma zwracać wartości, które muszą zostać odesłany do klienta (na przykład wartości obliczane w procedurze składowanej), utworzyć parametry wyjściowe w przechowywanych procedur. Jeśli nie możesz użyć parametrów wyjściowych, zapisu przesłonięcia implementację metody częściowej, zamiast polegania na generowany przez projektanta O/R. Wartości wygenerowanych w bazie danych elementów członkowskich muszą być podane odpowiednie wartości po pomyślnym ukończeniu operacji WSTAWIANIA lub aktualizacji. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w zastępowanie domyślne zachowanie](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ do SQL obsługuje wygenerowanych w bazie danych wartości automatycznie tożsamości (automatycznego przyrostu), rowguidcol (identyfikator GUID generowany przez bazy danych) i kolumn sygnatur czasowych. Wartości generowanych przez bazę danych w innych typów kolumn spowoduje nieoczekiwane wartości null. Aby zwrócić wartości wygenerowanych w bazie danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> do **true** i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> do jednej z następujących czynności: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), lub [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Konfigurowanie zachowania aktualizacji klasy jednostki

Domyślnie logika aktualizacji bazy danych (operacje wstawiania, aktualizacji i usunięć) za pomocą zmian wprowadzonych do danych w LINQ do klas jednostek SQL znajduje się w składniku LINQ to SQL w czasie wykonywania. Środowisko uruchomieniowe tworzy domyślne polecenia INSERT, UPDATE i DELETE, które opierają się na schemat tabeli (kolumny i informacje o kluczu podstawowym). Gdy zachowanie domyślne jest niepożądany, możesz skonfigurować zachowanie aktualizacji, przypisując określonych procedur składowanych do wykonywania niezbędne operacje wstawiania, aktualizacji i usuwania wymagane do manipulowania danymi w tabeli. Ponadto można to zrobić, jeśli domyślne zachowanie nie jest generowany, na przykład, gdy Twoje klas jednostek mapy do widoków. Na koniec można zastąpić domyślne zachowanie aktualizacji, gdy baza danych wymaga dostępu do tabel za pomocą procedur składowanych.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Aby przypisać procedur składowanych, aby zastąpić domyślne zachowanie klasę jednostki

1. Otwórz **LINQ to SQL** pliku w projektancie. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań**.)

2. W **Eksploratora serwera** lub **Eksplorator bazy danych**, rozwiń węzeł **procedur składowanych** i Znajdź procedur przechowywanych, które chcesz na użytek Insert, Update i/lub usuwania polecenia Klasa jednostki.

3. Przeciągnij procedurę składowaną do **O/R Designer**.

     Procedura składowana jest dodawany do okienka metod jako <xref:System.Data.Linq.DataContext> metody. Aby uzyskać więcej informacji, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wybierz klasę jednostki, dla którego chcesz użyć procedury składowanej do wykonywania aktualizacji.

5. W **właściwości** okna, wybierz polecenie, aby zastąpić (**Wstaw**, **aktualizacji**, lub **Usuń**).

6. Kliknij przycisk wielokropka (...) obok wyrazy **Użyj środowiska uruchomieniowego** otworzyć **Konfigurowanie zachowania** okno dialogowe.

7. Wybierz **dostosować**.

8. Wybierz odpowiednią procedurę składowaną w **Dostosuj** listy.

9. Sprawdź listę **argumenty metody** i **właściwości klasy** do sprawdzenia, czy **argumenty metody** mapy do odpowiedniego **właściwości klasy**. Mapowanie oryginalnego argumenty metody (`Original_<ArgumentName>`) do oryginalne właściwości (`<PropertyName> (Original)`) dla `Update` i `Delete` poleceń.

    > [!NOTE]
    > Domyślnie argumenty metody są mapowane na właściwości klasy, gdy nazwy są zgodne. Zmieniona właściwość, których nazwy nie są już zgodne między tabelą i Klasa jednostki, trzeba wybrać właściwość odpowiednik klasy do mapowania na, jeśli projektant nie może określić poprawne mapowania.

10. Kliknij przycisk **OK** lub **zastosować**.

    > [!NOTE]
    > Można kontynuować, skonfiguruj zachowanie dla każdej kombinacji klasę i zachowanie, tak długo, jak możesz kliknąć pozycję **Zastosuj** po wprowadzeniu każdej zmiany. Jeśli zmienisz klasy lub zachowania przed kliknięciem przycisku **Zastosuj**, okno dialogowe ostrzeżenia pojawia się i oferuje możliwość zastosowania zmian.

Aby przywrócić za pomocą domyślnej logiki czasu wykonywania aktualizacji, kliknij przycisk wielokropka **Wstaw**, **aktualizacji**, lub **Usuń** polecenia w pliku **właściwości**  okna, a następnie wybierz **korzystania ze środowiska uruchomieniowego** w **Konfigurowanie zachowania** okno dialogowe.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Wstawianie, aktualizowanie i usuwanie operacji (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
