---
title: Tworzenie i konfigurowanie adapterów TableAdapter
description: Zapoznaj się z tematem jak utworzyć i skonfigurować TableAdapter w programie Visual Studio. TableAdapters zapewnia komunikację między aplikacją a bazą danych.
ms.custom: SEO-VS-2020
ms.date: 09/01/2017
ms.topic: how-to
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a9ab54b358125e45cfb0d6a4df30989cf679ab2d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867154"
---
# <a name="create-and-configure-tableadapters"></a>Tworzenie i konfigurowanie adapterów TableAdapter

TableAdapters zapewnia komunikację między aplikacją a bazą danych. Łączą się z bazą danych, uruchamiają zapytania lub procedury składowane i zwracają nową tabelę danych lub wypełniają istniejące <xref:System.Data.DataTable> dane danymi zwracanymi. TableAdapters może również wysyłać zaktualizowane dane z aplikacji z powrotem do bazy danych.

TableAdapters są tworzone podczas wykonywania jednej z następujących czynności:

- Przeciągnij obiekty bazy danych z **Eksplorator serwera** do **Projektant obiektów DataSet**.

- Uruchom Kreatora konfiguracji źródła danych, a następnie wybierz typ źródła **danych** lub **usługi sieci Web** .

   ![Kreator konfiguracji źródła danych w programie Visual Studio](media/data-source-configuration-wizard.png)

Możesz również utworzyć nowy TableAdapter i skonfigurować go ze źródłem danych, przeciągając TableAdapter z **przybornika** do pustego regionu na powierzchni **Projektant obiektów DataSet** .

Aby zapoznać się z wprowadzeniem do TableAdapters, zobacz [Wypełnij zestawy danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Korzystanie z Kreatora konfiguracji TableAdapter

Uruchom **Kreatora konfiguracji TableAdapter** , aby utworzyć lub edytować TableAdapters i powiązane z nimi tabele DataTables. Istniejący TableAdapter można skonfigurować, klikając go prawym przyciskiem myszy w **Projektant obiektów DataSet**.

![Kreator konfiguracji adaptera raddata Table](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

Jeśli przeciągniesz nowy TableAdapter z przybornika, gdy **Projektant obiektów DataSet** ma fokus, zostanie uruchomiony Kreator i zostanie wyświetlony komunikat z prośbą o określenie źródła danych, z którym ma nastąpić połączenie. Na następnej stronie Kreator zapyta, jakiego rodzaju poleceń należy użyć do komunikacji z bazą danych, instrukcji SQL lub procedur składowanych. (Ta wartość nie zostanie wyświetlona, jeśli konfigurujesz TableAdapter, która jest już skojarzona ze źródłem danych).

- Istnieje możliwość utworzenia nowej procedury składowanej w źródłowej bazie danych, jeśli masz odpowiednie uprawnienia do bazy danych. Jeśli nie masz tych uprawnień, nie będzie to możliwe.

- Możesz również uruchomić istniejące procedury składowane dla poleceń **SELECT**, **INSERT**, **Update** i **delete** elementu TableAdapter. Procedura składowana przypisana do polecenia **Update** , na przykład, jest uruchamiana, gdy `TableAdapter.Update()` wywoływana jest metoda.

Mapuj parametry z wybranej procedury przechowywanej do odpowiednich kolumn w tabeli danych. Na przykład jeśli procedura składowana akceptuje parametr o nazwie `@CompanyName` przekazane do `CompanyName` kolumny w tabeli, należy ustawić **kolumnę źródłową** `@CompanyName` parametru na `CompanyName` .

> [!NOTE]
> Procedura składowana, która jest przypisana do polecenia SELECT, jest uruchamiana przez wywołanie metody TableAdapter, która została nazwana w następnym kroku kreatora. Metoda domyślna to `Fill` , więc kod, który jest zazwyczaj używany do uruchamiania procedury SELECT, to `TableAdapter.Fill(tableName)` . W przypadku zmiany nazwy domyślnej z programu `Fill` należy zastąpić `Fill` nazwą, którą chcesz przypisać, i Zastąp ciąg "TableAdapter" rzeczywistą nazwą TableAdapter (na przykład `CustomersTableAdapter` ).

- Wybranie opcji **Utwórz metody, aby wysłać aktualizacje bezpośrednio do bazy danych,** jest równoznaczne z ustawieniem `GenerateDBDirectMethods` właściwości na true. Opcja jest niedostępna, gdy pierwotna instrukcja SQL nie dostarcza wystarczającej ilości informacji lub zapytanie nie jest aktualizowalnym zapytaniem. Taka sytuacja może wystąpić na przykład w kwerendach **sprzężenia** i zapytaniach zwracających pojedynczą wartość (skalarną).

**Opcje zaawansowane** w kreatorze umożliwiają:

- Generuj instrukcje INSERT, UPDATE i DELETE na podstawie instrukcji SELECT zdefiniowanej na stronie **generowanie instrukcji SQL**
- Korzystanie z optymistycznej współbieżności
- Określ, czy tabela danych ma być odświeżana po uruchomieniu instrukcji INSERT i UPDATE

## <a name="configure-a-tableadapters-fill-method"></a>Konfigurowanie metody Fill elementu TableAdapter

Czasami może zajść potrzeba zmiany schematu tabeli TableAdapter. W tym celu należy zmodyfikować podstawową `Fill` metodę TableAdapter. TableAdapters są tworzone za pomocą `Fill` metody podstawowej, która definiuje schemat skojarzonej tabeli danych. Podstawowa `Fill` Metoda jest oparta na zapytaniu lub procedurze przechowywanej wprowadzonej podczas początkowego konfigurowania TableAdapter. Jest to pierwsza (najwyżej) Metoda w tabeli danych w Projektancie obiektów DataSet.

![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif)

Wszelkie zmiany wprowadzone w `Fill` metodzie Main TableAdapter są odzwierciedlane w schemacie skojarzonej tabeli danych. Na przykład usunięcie kolumny z zapytania w `Fill` metodzie Main spowoduje również usunięcie kolumny ze skojarzonej tabeli danych. Ponadto usunięcie kolumny z `Fill` metody Main spowoduje usunięcie kolumny z dowolnych dodatkowych zapytań dla tego TableAdapter.

Za pomocą Kreatora konfiguracji zapytania TableAdapter można tworzyć i edytować dodatkowe zapytania dla TableAdapter. Te dodatkowe zapytania muszą być zgodne ze schematem tabeli, chyba że zwracają wartość skalarną.  Każde dodatkowe zapytanie ma określoną nazwę.

Poniższy przykład pokazuje, jak wywołać dodatkowe zapytanie o nazwie `FillByCity` :

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Aby uruchomić Kreatora konfiguracji zapytania TableAdapter z nowym zapytaniem

1. Otwórz zestaw danych w **Projektant obiektów DataSet**.

2. W przypadku tworzenia nowego zapytania przeciągnij obiekt **zapytania** z karty **zestaw danych** **przybornika** do <xref:System.Data.DataTable> lub wybierz polecenie **Dodaj zapytanie** z menu skrótów programu TableAdapter. Możesz również przeciągnąć obiekt **zapytania** do pustego obszaru **Projektant obiektów DataSet**, który tworzy TableAdapter bez skojarzonego <xref:System.Data.DataTable> . Te zapytania mogą zwracać tylko pojedyncze (skalarne) wartości lub uruchamiać polecenia UPDATE, INSERT lub DELETE względem bazy danych.

3. Na ekranie **Wybierz połączenie danych** wybierz lub Utwórz połączenie, które będzie używane przez zapytanie.

    > [!NOTE]
    > Ten ekran jest wyświetlany tylko wtedy, gdy projektant nie może określić odpowiedniego połączenia do użycia lub gdy żadne połączenia nie są dostępne.

4. Na ekranie **Wybieranie typu polecenia** wybierz jedną z następujących metod pobierania danych z bazy danych:

    - **Użycie instrukcji SQL** umożliwia wpisanie instrukcji SQL w celu wybrania danych z bazy danych.

    - Polecenie **Utwórz nową procedurę składowaną** umożliwia utworzenie przez Kreatora nowej procedury składowanej (w bazie danych) w oparciu o określoną instrukcję SELECT.

    - **Użyj istniejących procedur składowanych** umożliwia uruchomienie istniejącej procedury składowanej podczas wykonywania zapytania.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Aby uruchomić Kreatora konfiguracji zapytania TableAdapter na istniejącym zapytaniu

- Jeśli edytujesz istniejące zapytanie TableAdapter, kliknij je prawym przyciskiem myszy, a następnie wybierz polecenie **Konfiguruj** z menu skrótów.

    > [!NOTE]
    > Kliknięcie prawym przyciskiem myszy głównego zapytania TableAdapter ponownie konfiguruje TableAdapter i <xref:System.Data.DataTable> schemat. Jednak kliknij prawym przyciskiem myszy dodatkowe zapytanie na TableAdapter, skonfiguruje tylko wybrane zapytanie. **Kreator konfiguracji TableAdapter** ponownie konfiguruje definicję TableAdapter, podczas gdy **Kreator konfiguracji zapytania TableAdapter** ponownie konfiguruje tylko wybrane zapytanie.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>Aby dodać zapytanie globalne do elementu TableAdapter

- Zapytania globalne to zapytania SQL zwracające pojedynczą (skalarną) wartość lub brak wartości. Zazwyczaj funkcje globalne wykonują operacje bazy danych, takie jak wstawienia, aktualizacje i usunięcia. Łączą one również informacje, takie jak liczba klientów w tabeli lub łączna opłata za wszystkie elementy w określonej kolejności.

     Zapytania globalne są dodawane przez przeciąganie obiektu **zapytania** z karty **zestaw danych** **przybornika** do pustego obszaru **Projektant obiektów DataSet**.

- Podaj zapytanie, które wykonuje odpowiednie zadanie, na przykład `SELECT COUNT(*) AS CustomerCount FROM Customers` .

    > [!NOTE]
    > Przeciąganie obiektu **zapytania** bezpośrednio do **Projektant obiektów DataSet** tworzy metodę zwracającą tylko wartość skalarną (pojedynczą). Mimo że wybrana procedura zapytania lub procedury składowanej może zwrócić więcej niż jedną wartość, Metoda utworzona przez kreatora zwróci tylko jedną wartość. Na przykład zapytanie może zwrócić pierwszą kolumnę pierwszego wiersza zwracanych danych.

## <a name="see-also"></a>Zobacz też

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
