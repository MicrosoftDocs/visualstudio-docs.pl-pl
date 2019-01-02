---
title: Obsługiwanie wyjątku współbieżności
ms.date: 09/11/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b626aa489323d26ef439ade216d1fa97a52a8d13
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825649"
---
# <a name="handle-a-concurrency-exception"></a>Obsługiwanie wyjątku współbieżności

Wyjątki współbieżności (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) są wywoływane, gdy dwóch użytkowników podejmują próby zmiany te same dane w bazie danych, w tym samym czasie. W tym instruktażu utworzysz aplikacji Windows, który ilustruje sposób catch <xref:System.Data.DBConcurrencyException>, znajdź wiersz, który spowodował błąd i Dowiedz się, strategii, sposobu jego obsługi.

Ten przewodnik przeprowadzi Cię przez następujący proces:

1. Utwórz nową **aplikacja interfejsu Windows Forms** projektu.

2. Utwórz nowy zestaw danych na podstawie tabeli klientów Northwind.

3. Tworzenie formularza za pomocą <xref:System.Windows.Forms.DataGridView> do wyświetlania danych.

4. Wypełnianie zestawu danych danymi z tabeli Klienci w bazie danych Northwind.

5. Użyj **Pokaż dane tabeli** są wyposażone w **Eksploratora serwera** dostęp do danych z tabeli Customers i zmienić rekord.

6. Zmień ten sam rekord na inną wartość, zaktualizować zestaw danych, a próba zapisania zmian w bazie danych, co powoduje błąd współbieżności, są zgłaszane.

7. Wychwycić błąd, a następnie wyświetlić różne wersje rekordu, dzięki czemu użytkownik określić, czy chcesz kontynuować i aktualizują bazę danych lub anulować aktualizację.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Rozpocznij od utworzenia nowej aplikacji Windows Forms:

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **ConcurrencyWalkthrough**, a następnie wybierz **OK**.

     **ConcurrencyWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**, i nowy formularz zostanie otwarty w projektancie.

## <a name="create-the-northwind-dataset"></a>Tworzenie zestawu danych Northwind

Następnie należy utworzyć zestaw danych o nazwie **NorthwindDataSet**:

1. Na **danych** menu, wybierz **Dodaj nowe dane źródła**.

   Zostanie otwarty Kreator konfiguracji źródła danych.

2. Na **wybierz typ źródła danych** ekranu, wybierz opcję **bazy danych**.

   ![Kreator konfiguracji źródła danych w programie Visual Studio](media/data-source-configuration-wizard.png)

3. Wybierz połączenie z przykładową bazą danych Northwind, z listy dostępnych połączeń. Jeśli połączenie nie jest dostępne na liście połączeń, wybierz opcję **nowe połączenie**.

    > [!NOTE]
    > Jeśli łączysz się z plikiem lokalnej bazy danych, wybierz opcję **nie** po wyświetleniu monitu, jeśli w przypadku chcesz dodać plik do projektu.

4. Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** ekranu, wybierz opcję **dalej**.

5. Rozwiń **tabel** a następnie wybierz węzeł **klientów** tabeli. Domyślna nazwa zestawu danych powinny być **NorthwindDataSet**.

6. Wybierz **Zakończ** można dodać zestaw danych do projektu.

## <a name="create-a-data-bound-datagridview-control"></a>Tworzenie formantu DataGridView powiązanych z danymi

W tej sekcji utworzysz <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> , przeciągając **klientów** elementu z **źródeł danych** okna do formularza Windows.

1. Aby otworzyć **źródeł danych** okna na **danych** menu, wybierz **Pokaż źródła danych**.

2. W **źródeł danych** okna, rozwiń węzeł **NorthwindDataSet** węzeł, a następnie wybierz **klientów** tabeli.

3. Wybierz strzałkę w dół w węźle tabeli, a następnie wybierz **DataGridView** na liście rozwijanej.

4. Przeciągnij tabelę na wolne miejsce formularza.

     A <xref:System.Windows.Forms.DataGridView> formantu o nazwie **CustomersDataGridView**, a <xref:System.Windows.Forms.BindingNavigator> o nazwie **CustomersBindingNavigator**, są dodawane do formularza, który jest powiązany z <xref:System.Windows.Forms.BindingSource>. To z kolei wiązanie z tabeli Customers w NorthwindDataSet.

## <a name="test-the-form"></a>Przetestuj formularz

Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami do tej pory:

1. Wybierz **F5** do uruchomienia aplikacji.

     Zostanie wyświetlony formularz z <xref:System.Windows.Forms.DataGridView> formant na nim, który jest wypełniony przy użyciu danych z tabeli Customers.

2. Na **debugowania** menu, wybierz opcję **Zatrzymaj debugowanie**.

## <a name="handle-concurrency-errors"></a>Obsługa współbieżności błędów

Sposób obsługi błędów jest zależna od firmy zasady aplikacji. W tym przewodniku używamy strategia jako przykładu sposobu obsługi błąd współbieżności.

Aplikacja wyświetli użytkownika z trzech wersjach rekordu:

- Bieżący rekord w bazie danych

- Oryginalny rekord, który jest ładowany do zestawu danych

- Proponowane zmiany w zestawie danych

Następnie użytkownik będzie mógł zastąpienia bazy danych przy użyciu proponowanych wersji lub anulować aktualizację i odświeżyć zestaw danych z nowymi wartościami z bazy danych.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Aby włączyć obsługę błędów współbieżności

1. Utwórz procedurę obsługi błędów niestandardowych.

2. Wyświetlanie opcji dla użytkownika.

3. Przetwarzanie odpowiedzi użytkownika.

4. Wyślij ponownie aktualizację, lub przywrócić dane w zestawie danych.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Dodaj kod obsługi wyjątku współbieżności

Gdy użytkownik podejmie próbę przeprowadzenia aktualizacji, a wyjątek jest zgłaszany, zazwyczaj chcesz zrobić coś z informacjami, które są dostarczane przez zgłoszony wyjątek. W tej sekcji dodasz kod, który próbuje zaktualizować bazę danych. Możesz również obsługiwać dowolne <xref:System.Data.DBConcurrencyException> , może zostać wywołane, a także inne wyjątki.

> [!NOTE]
> `CreateMessage` i `ProcessDialogResults` metody zostaną dodane w dalszej części przewodnika.

1. Dodaj następujący kod poniżej `Form1_Load` metody:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Zastąp `CustomersBindingNavigatorSaveItem_Click` metodę do wywołania `UpdateDatabase` metoda tak, aby wyglądał następująco:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Wyświetl opcje użytkownika

Kod został właśnie powstała z jednego wywołania `CreateMessage` procedury, aby wyświetlić informacje o błędzie dla użytkownika. W tym przewodniku używasz okno komunikatu do wyświetlania różnych wersji rekordu użytkownika. Dzięki temu użytkownikowi określenie, czy chcesz zastąpić rekord zmiany lub anulowania edycji. Gdy użytkownik wybierze opcję (kliknie przycisk) w oknie komunikatu, odpowiedź jest przekazywany do `ProcessDialogResult` metody.

Utwórz wiadomość, dodając następujący kod, aby **Edytor kodu**. Wprowadź poniżej kod `UpdateDatabase` metody:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Przetwarzanie odpowiedzi użytkownika

Należy również kod, aby przetworzyć odpowiedzi użytkownika w oknie komunikatu. Dostępne opcje to można zastąpić proponowanej zmiany bieżącego rekordu w bazie danych lub Porzuć zmiany lokalne i Odśwież tabelę danych z rekordu, który jest obecnie dostępna w bazie danych. Jeśli użytkownik wybierze **tak**, <xref:System.Data.DataTable.Merge%2A> metoda jest wywoływana z *preserveChanges* argument wartość **true**. Powoduje to próba aktualizacji był udany, ponieważ oryginalną wersję rekordu jest teraz zgodna rekord w bazie danych.

Dodaj następujący kod poniższego kodu, który został dodany w poprzedniej sekcji:

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Przetestuj formularz

Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami. Aby zasymulować Naruszenie współbieżności, możesz zmienić dane z bazy danych po wypełnieniu NorthwindDataSet.

1. Wybierz **F5** do uruchomienia aplikacji.

2. Gdy zostanie wyświetlony formularz, będzie działać, a następnie przełącz się do środowiska IDE programu Visual Studio.

3. Na **widoku** menu, wybierz **Eksploratora serwera**.

4. W **Eksploratora serwera**, rozwiń węzeł połączenia aplikacji za pomocą, a następnie rozwiń **tabel** węzła.

5. Kliknij prawym przyciskiem myszy **klientów** tabeli, a następnie wybierz **Pokaż dane tabeli**.

6. W pierwszym rekordzie (**ALFKI**), zmień **ContactName** do **Maria Anders2**.

    > [!NOTE]
    > Przejdź do innego wiersza, aby zatwierdzić zmiany.

7. Przełącz do ConcurrencyWalkthrough uruchomiona formularza.

8. W pierwszym rekordzie na formularzu (**ALFKI**), zmień **ContactName** do **Maria Anders1**.

9. Wybierz ikonę **Zapisz**.

     Błąd współbieżności, a pojawi się okno komunikatu.

   Wybieranie **nie** anuluje aktualizacji i aktualizuje zestaw danych o wartości, które są obecnie dostępne w bazie danych. Wybieranie **tak** zapisuje proponowana wartość w bazie danych.

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)