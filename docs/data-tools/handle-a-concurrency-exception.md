---
title: Obsługiwanie wyjątku współbieżności
description: Obsłuż wyjątek współbieżności (System. Data. DBConcurrencyException), który jest uruchamiany, gdy dwóch użytkowników spróbuje zmienić te same dane w bazie danych w tym samym czasie.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f84fbaae3273b8830cce1c39cc3e42b62e487d3e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216244"
---
# <a name="handle-a-concurrency-exception"></a>Obsługiwanie wyjątku współbieżności

Wyjątki współbieżności ( <xref:System.Data.DBConcurrencyException?displayProperty=fullName> ) są wywoływane, gdy dwóch użytkowników próbuje zmienić te same dane w bazie danych w tym samym czasie. W tym instruktażu utworzysz aplikację systemu Windows, która ilustruje sposób wychwycenia <xref:System.Data.DBConcurrencyException> , odnalezienie wiersza, który spowodował błąd, i zapoznanie się z strategią, jak ją obsłużyć.

Ten przewodnik przeprowadzi Cię przez następujący proces:

1. Utwórz nowy projekt **aplikacji Windows Forms** .

2. Utwórz nowy zestaw danych na podstawie tabeli Klienci Northwind.

3. Utwórz formularz z programem, <xref:System.Windows.Forms.DataGridView> Aby wyświetlić dane.

4. Wypełnianie zestawu danych danymi z tabeli Customers w bazie danych Northwind.

5. Użyj funkcji **Pokaż dane tabeli** w **Eksplorator serwera** , aby uzyskać dostęp do danych z tabeli Customers i zmienić rekord.

6. Zmień ten sam rekord na inną wartość, zaktualizuj zestaw danych i spróbuj zapisać zmiany w bazie danych, co powoduje błąd współbieżności.

7. Zapoznaj się z błędem, a następnie Wyświetl różne wersje rekordu, umożliwiając użytkownikowi określenie, czy chcesz kontynuować i zaktualizować bazę danych, albo Anuluj aktualizację.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio** można zainstalować SQL Server Express LocalDB jako część obciążenia **magazynu danych i przetwarzania** lub jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Zacznij od utworzenia nowej aplikacji Windows Forms:

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **ConcurrencyWalkthrough**, a następnie wybierz przycisk **OK**.

     Projekt **ConcurrencyWalkthrough** jest tworzony i dodawany do **Eksplorator rozwiązań**, a nowy formularz zostanie otwarty w projektancie.

## <a name="create-the-northwind-dataset"></a>Tworzenie zestawu danych Northwind

Następnie Utwórz zestaw danych o nazwie **NorthwindDataSet**:

1. W menu **dane** wybierz polecenie **Dodaj nowe źródło danych**.

   Zostanie otwarty Kreator konfiguracji źródła danych.

2. Na ekranie **Wybierz typ źródła danych** wybierz pozycję **baza danych**.

   ![Kreator konfiguracji źródła danych w programie Visual Studio](media/data-source-configuration-wizard.png)

3. Wybierz połączenie z przykładową bazą danych Northwind z listy dostępnych połączeń. Jeśli połączenie nie jest dostępne na liście połączeń, wybierz pozycję **nowe połączenie**.

    > [!NOTE]
    > Jeśli łączysz się z lokalnym plikiem bazy danych, wybierz opcję **nie** , jeśli chcesz dodać plik do projektu.

4. Na ekranie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej**.

5. Rozwiń węzeł **tabele** , a następnie wybierz tabelę **Customers** . Domyślną nazwą zestawu danych powinna być **NorthwindDataSet**.

6. Wybierz pozycję **Zakończ** , aby dodać zestaw danych do projektu.

## <a name="create-a-data-bound-datagridview-control"></a>Tworzenie kontrolki DataGridView powiązanej z danymi

W tej sekcji utworzysz, <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> przeciągając element **Customers** z okna **źródła danych** na formularz systemu Windows.

1. Aby otworzyć okno **źródła danych** , w menu **dane** wybierz polecenie **Pokaż źródła danych**.

2. W oknie **źródła danych** rozwiń węzeł **NorthwindDataSet** , a następnie wybierz tabelę **Customers** .

3. Wybierz strzałkę w dół w węźle tabela, a następnie na liście rozwijanej wybierz pozycję **DataGridView** .

4. Przeciągnij tabelę do pustego obszaru formularza.

     <xref:System.Windows.Forms.DataGridView>Kontrolka o nazwie **customersDataGridView** i <xref:System.Windows.Forms.BindingNavigator> nazwanym **CustomersBindingNavigator** są dodawane do formularza, który jest powiązany z <xref:System.Windows.Forms.BindingSource> . Jest to z kolei powiązane z tabelą Customers w NorthwindDataSet.

## <a name="test-the-form"></a>Testowanie formularza

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami do tego momentu:

1. Wybierz klawisz **F5** , aby uruchomić aplikację.

     Formularz zostanie wyświetlony z <xref:System.Windows.Forms.DataGridView> kontrolką, która jest wypełniana danymi z tabeli Customers.

2. W menu **Debugowanie** wybierz polecenie **Zatrzymaj debugowanie**.

## <a name="handle-concurrency-errors"></a>Obsługa błędów współbieżności

Sposób obsługi błędów zależy od konkretnych reguł firmy, które regulują aplikację. W tym instruktażu używamy następującej strategii jako przykładu, aby obsłużyć błąd współbieżności.

Aplikacja prezentuje użytkownikowi trzy wersje rekordu:

- Bieżący rekord w bazie danych

- Oryginalny rekord, który jest ładowany do zestawu danych

- Proponowane zmiany w zestawie danych

Użytkownik może zastąpić bazę danych zaproponowaną wersją lub anulować aktualizację i odświeżyć zestaw danych przy użyciu nowych wartości z bazy danych.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Aby włączyć obsługę błędów współbieżności

1. Utwórz niestandardową procedurę obsługi błędów.

2. Wyświetl opcje dla użytkownika.

3. Przetwórz odpowiedź użytkownika.

4. Wyślij ponownie aktualizację lub zresetuj dane w zestawie danych.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Dodaj kod obsługujący wyjątek współbieżności

Podczas próby wykonania aktualizacji i zgłoszenia wyjątku zazwyczaj trzeba wykonać coś z informacjami podanymi przez zgłoszony wyjątek. W tej sekcji dodasz kod, który próbuje zaktualizować bazę danych. Obsługiwane są również wszystkie <xref:System.Data.DBConcurrencyException> inne wyjątki, które mogą zostać zgłoszone.

> [!NOTE]
> `CreateMessage`Metody i `ProcessDialogResults` są dodawane w dalszej części przewodnika.

1. Dodaj następujący kod poniżej `Form1_Load` metody:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet1":::

2. Zastąp `CustomersBindingNavigatorSaveItem_Click` metodę, aby wywołać `UpdateDatabase` metodę, tak aby wyglądała następująco:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet2":::

### <a name="display-choices-to-the-user"></a>Wyświetl opcje dla użytkownika

Właśnie zapisany kod wywołuje `CreateMessage` procedurę, aby wyświetlić informacje o błędzie dla użytkownika. W tym instruktażu należy użyć okna komunikatu, aby wyświetlić różne wersje rekordu dla użytkownika. Dzięki temu użytkownik może wybrać, czy rekord ma zostać zastąpiony zmianami, czy anulować edycję. Gdy użytkownik wybierze opcję (kliknie przycisk) w oknie komunikatu, odpowiedź jest przesyłana do `ProcessDialogResult` metody.

Utwórz komunikat, dodając następujący kod do **edytora kodu**. Wprowadź następujący kod poniżej `UpdateDatabase` metody:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet4":::

### <a name="process-the-users-response"></a>Przetwórz odpowiedź użytkownika

Musisz również mieć kod, aby przetworzyć odpowiedź użytkownika do okna komunikatu. Dostępne są opcje zastępowania bieżącego rekordu w bazie danych z proponowaną zmianą lub porzucenia lokalnych zmian i odświeżenia tabeli danych z rekordem, który jest obecnie w bazie danych. Jeśli użytkownik wybierze **wartość tak**, <xref:System.Data.DataTable.Merge%2A> Metoda zostanie wywołana z argumentem *PreserveChanges* ustawionym na **wartość true**. Powoduje to pomyślną próbę aktualizacji, ponieważ oryginalna wersja rekordu jest teraz zgodna z rekordem w bazie danych.

Dodaj następujący kod poniżej kodu, który został dodany w poprzedniej sekcji:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form-behavior"></a>Testowanie zachowania formularza

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami. W celu zasymulowania naruszenia współbieżności dane w bazie danych są zmieniane po wypełnieniu NorthwindDataSet.

1. Wybierz klawisz **F5** , aby uruchomić aplikację.

2. Po wyświetleniu formularza, pozostaw go uruchomiony i przejdź do środowiska IDE programu Visual Studio.

3. W menu **Widok** wybierz **Eksplorator serwera**.

4. W **Eksplorator serwera** rozwiń połączenie używane przez aplikację, a następnie rozwiń węzeł **tabele** .

5. Kliknij prawym przyciskiem myszy tabelę **Customers** , a następnie wybierz polecenie **Pokaż dane tabeli**.

6. W pierwszym rekordzie (**ALFKI**) Zmień wartość **ContactName** na **Mariany Anders2**.

    > [!NOTE]
    > Przejdź do innego wiersza, aby zatwierdzić zmianę.

7. Przejdź do formularza ConcurrencyWalkthrough.

8. W pierwszym rekordzie w formularzu (**ALFKI**) Zmień wartość **ContactName** na **Mariany Anders1**.

9. Wybierz ikonę **Zapisz**.

     Wystąpił błąd współbieżności i pojawia się okno komunikatu.

   Wybranie pozycji **nie** powoduje anulowania aktualizacji i zaktualizowanie zestawu danych wartościami, które znajdują się obecnie w bazie danych. Wybranie pozycji **tak** zapisuje proponowaną wartość do bazy danych.

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
