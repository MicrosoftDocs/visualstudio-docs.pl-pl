---
title: Tworzenie i konfigurowanie adapterów TableAdapter
ms.date: 09/01/2017
ms.topic: conceptual
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 7f43cbd8e9002d026fba632046907dfee969884d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948365"
---
# <a name="create-and-configure-tableadapters"></a>Tworzenie i konfigurowanie adapterów TableAdapter

TableAdapters zapewniają komunikację między aplikacją i bazą danych. Łączą się z bazą danych, wykonywania zapytań lub procedur przechowywanych i zwrócenie nowe dane tabeli lub wypełnij istniejącego <xref:System.Data.DataTable> ze zwracanych danych. TableAdapters można również wysyłać zaktualizowane dane z aplikacji w bazie danych.

TableAdapters są tworzone automatycznie, kiedy wykonujesz jedno z następujących czynności:

- Przeciągnij obiekty bazy danych z **Eksploratora serwera** do **Projektanta obiektów Dataset**.

- Uruchom Kreatora konfiguracji źródła danych, a następnie wybierz opcję **bazy danych** lub **usługi sieci Web** typ źródła danych.

   ![Kreator konfiguracji źródła danych w programie Visual Studio](media/data-source-configuration-wizard.png)

Można również utworzyć nowy obiekt TableAdapter i skonfigurować ją ze źródłem danych, przeciągając TableAdapter z **przybornika** do pustego regionu w **Projektanta obiektów Dataset** powierzchni.

Aby zapoznać się z wprowadzeniem do adapterów TableAdapter, zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Za pomocą Kreatora konfiguracji TableAdapter

Uruchom **Kreator konfiguracji TableAdapter** umożliwia tworzenie i edytowanie TableAdapters i ich skojarzone DataTable. Można skonfigurować istniejący obiekt TableAdapter, klikając prawym przyciskiem myszy na nim w **Projektanta obiektów Dataset**.

![raddata Kreatora konfiguracji adaptera tabeli](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

Jeśli przeciągniesz nowy obiekt TableAdapter z przybornika po **Projektanta obiektów Dataset** skupić się uruchamia kreatora i monitów, można określić dane, które źródła TableAdapter powinien łączyć się z. Na następnej stronie Kreator zapyta, jakiego rodzaju poleceń, jego powinna być używana do komunikacji z bazą danych, instrukcji SQL lub procedur składowanych. (Nie zobaczysz to w przypadku konfigurowania TableAdapter, która jest już skojarzona ze źródłem danych.)

- Masz opcję, aby utworzyć nową procedurę składowaną w bazie danych, jeśli masz odpowiednie uprawnienia do bazy danych. Jeśli nie masz tych uprawnień, będzie to opcja.

- Istnieje także możliwość uruchamiania istniejących procedur składowanych dla **wybierz**, **Wstaw**, **aktualizacji**, i **Usuń** polecenia TableAdapter. Procedura składowana, która jest przypisana do **aktualizacji** , na przykład polecenie kiedy `TableAdapter.Update()` metoda jest wywoływana.

Mapowanie parametrów przy użyciu wybranej procedury składowanej odpowiednich kolumn w tabeli danych. Na przykład, jeśli Twoja procedura składowana akceptuje parametr o nazwie `@CompanyName` przesyłanego do `CompanyName` zestawu kolumn w tabeli, **kolumny źródłowej** z `@CompanyName` parametr `CompanyName`.

> [!NOTE]
> Procedura składowana, która jest przypisana do polecenia SELECT jest uruchamiane przez wywołanie metody TableAdapter o nazwie w następnym kroku kreatora. Jest to domyślna metoda `Fill`, więc jest kod, który zazwyczaj jest używane do uruchamiania procedury SELECT `TableAdapter.Fill(tableName)`. Jeśli zmienisz nazwę domyślną z `Fill`, Zastąp `Fill` o nazwie możesz przypisać, a następnie Zamień "TableAdapter" rzeczywistą nazwą TableAdapter (na przykład `CustomersTableAdapter`).

- Wybieranie **utworzyć metody, aby wysłać aktualizacje bezpośrednio z bazą danych** opcja jest równoznaczna z ustawienie `GenerateDBDirectMethods` właściwości na wartość true. Opcja jest niedostępna, gdy oryginalny instrukcji SQL nie dostarczać wystarczających informacji lub zapytanie jest zapytaniem można aktualizować. Taka sytuacja może wystąpić, na przykład w **Dołącz** zapytań oraz zapytań zwracających pojedynczą wartość (skalarną).

**Zaawansowane opcje** w Kreatorze umożliwiają:

- Generuj instrukcje INSERT, UPDATE i DELETE na instrukcji SELECT, która jest zdefiniowana na podstawie **instrukcji SQL Generowanie** strony
- Używaj optymistycznej współbieżności
- Określ, czy Odśwież tabelę danych po WSTAWIENIU i uruchamiania instrukcji UPDATE

## <a name="configure-a-tableadapters-fill-method"></a>Konfiguruj TableAdapter metody Fill

Czasami możesz chcieć zmienić schemat tabeli TableAdapter. W tym celu należy zmodyfikować podstawowy TableAdapter `Fill` metody. TableAdapters są tworzone przy użyciu podstawowego `Fill` metodę, która definiuje schemat tabeli powiązane dane. Podstawowy `Fill` Metoda opiera się na zapytanie lub procedura składowana wprowadzone podczas pierwotnie skonfigurowane TableAdapter. Jest to pierwszy metoda (najwyższego poziomu) w tabeli danych w Projektancie obiektów DataSet.

![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif)

Wszelkie zmiany wprowadzone do elementu TableAdapter w głównym `Fill` metody są odzwierciedlane w schemat tabeli powiązane dane. Na przykład, usunięcie kolumny z zapytania w głównym `Fill` metoda spowoduje również usunięcie kolumny z tabeli powiązane dane. Ponadto usunięcie kolumny z głównym `Fill` metoda usuwa kolumnę z żadnych dodatkowych zapytań dla tego TableAdapter.

Kreator konfiguracji zapytania TableAdapter służy do tworzenia i edytowania dodatkowych zapytań do TableAdapter. Te dodatkowe zapytania musi być zgodna z schemat tabeli, chyba że zwracają wartość skalarną.  Każde dodatkowe zapytanie o nazwie określonej.

Poniższy przykład pokazuje sposób wywoływania dodatkowych kwerendę o nazwie `FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Aby uruchomić Kreatora konfiguracji zapytania TableAdapter za pomocą nowego zapytania

1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**.

2.  W przypadku tworzenia nowego zapytania, przeciągnij **zapytania** obiektu z **DataSet** karcie **przybornika** na <xref:System.Data.DataTable>, lub wybierz **Dodaj zapytanie**z menu skrótów TableAdapter. Możesz również przeciągnąć **zapytania** obiektu w pustym obszarem **Projektanta obiektów Dataset**, co powoduje utworzenie TableAdapter bez skojarzonego <xref:System.Data.DataTable>. Te zapytania można tylko zwraca pojedyncze wartości (skalarne) lub wykonywania UPDATE, INSERT lub usunąć poleceń w bazie danych.

3.  Na **wybierz połączenie danych** ekranu, wybierz lub Utwórz połączenie, które będą używane zapytanie.

    > [!NOTE]
    > Ten ekran jest wyświetlany tylko wtedy, gdy projektant nie może określić odpowiednie połączenie lub gdy będzie dostępnych żadnych połączeń.

4.  Na **wybierz typ polecenia** ekranu, wybierz jedną z następujących metod pobierania danych z bazy danych:

    - **Użyj instrukcji SQL** umożliwia wpisanie instrukcję SQL, aby wybrać dane z bazy danych.

    - **Utwórz nową procedurę składowaną** umożliwia, aby Kreator tworzenia nowego przechowywane procedury (w bazie danych), oparte na określonej instrukcji SELECT.

    - **Używanie istniejących procedur składowanych** pozwala na uruchamianie istniejącą procedurę składowaną, podczas uruchamiania zapytania.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Aby uruchomić Kreatora konfiguracji zapytania TableAdapter na istniejące zapytanie

- Jeśli edytujesz istniejące zapytanie TableAdapter, kliknij prawym przyciskiem myszy zapytanie, a następnie wybierz **Konfiguruj** z menu skrótów.

    > [!NOTE]
    > Kliknij prawym przyciskiem myszy główne zapytanie TableAdapter ponownie konfiguruje TableAdapter i <xref:System.Data.DataTable> schematu. Kliknij prawym przyciskiem myszy dodatkowych kwerend w metodzie TableAdapter, jednak służy do konfigurowania wybranego zapytania. **Kreator konfiguracji TableAdapter** ponownie konfiguruje definicji TableAdapter, podczas gdy **Kreatora konfiguracji zapytania TableAdapter** ponownie konfiguruje wybrane zapytanie.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>Aby dodać zapytanie globalne do adaptera TableAdapter

- Zapytania globalne są zapytania SQL, które zwraca pojedynczą wartość (skalarną) lub nie ma wartości. Zwykle funkcje globalne wykonywania operacji bazy danych, takich jak wstawiania, aktualizacji i usuwania. Łączą one również informacje, takie jak liczba klientów w tabeli lub łączne opłaty dla wszystkich elementów w określonej kolejności.

     Dodawanie zapytań globalnych, przeciągając **zapytania** obiektu z **zestawu danych** karcie **przybornika** na pustym obszarem **Projektanta obiektów Dataset**.

- Podaj zapytania, który wykonuje odpowiednie zadanie, na przykład `SELECT COUNT(*) AS CustomerCount FROM Customers`.

    > [!NOTE]
    > Przeciąganie **zapytania** obiektu bezpośrednio na **Projektanta obiektów Dataset** tworzy metodę, która zwraca tylko (pojedyncze) wartość skalarną. Gdy zapytanie lub procedura składowana, którą wybierzesz może zwrócić więcej niż jedną wartość, metody, która jest tworzony przez kreatora tylko zwraca pojedynczą wartość. Na przykład zapytanie może zwrócić pierwszą kolumnę pierwszego wiersza zwrócone dane.

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)