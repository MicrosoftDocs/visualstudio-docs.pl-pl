---
title: Obsługuj wyjątek współbieżności | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670039"
---
# <a name="handle-a-concurrency-exception"></a>Obsługiwanie wyjątku współbieżności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyjątki współbieżności (<xref:System.Data.DBConcurrencyException>) są wywoływane, gdy dwóch użytkowników próbuje zmienić te same dane w bazie danych w tym samym czasie. W tym instruktażu utworzysz aplikację systemu Windows, która ilustruje sposób przechwytywania <xref:System.Data.DBConcurrencyException>, lokalizowania wiersza, który spowodował błąd, oraz informacje o strategii ich obsługi.

 Ten przewodnik przeprowadzi Cię przez następujący proces:

1. Utwórz nowy projekt **aplikacji systemu Windows** .

2. Utwórz nowy zestaw danych oparty na tabeli `Customers` Northwind.

3. Utwórz formularz z <xref:System.Windows.Forms.DataGridView>, aby wyświetlić dane.

4. Wypełnianie zestawu danych danymi z tabeli `Customers` w bazie danych Northwind.

5. Użyj [narzędzi graficznych bazy danych](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) w programie Visual Studio, aby uzyskać bezpośredni dostęp do tabeli danych `Customers` i zmienić rekord.

6. Zmień ten sam rekord na inną wartość, zaktualizuj zestaw danych i spróbuj zapisać zmiany w bazie danych, co powoduje błąd współbieżności.

7. Przechwyć błąd, a następnie Wyświetl różne wersje rekordu, umożliwiając użytkownikowi określenie, czy chcesz kontynuować i zaktualizować bazę danych, czy też anulować aktualizację.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind z uprawnieniem do wykonywania aktualizacji.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub używanej wersji. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Przewodnik rozpoczyna się od utworzenia nowej aplikacji systemu Windows.

#### <a name="to-create-a-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji systemu Windows

1. W menu **plik** Utwórz nowy projekt.

2. W okienku **typy projektów** wybierz język programowania.

3. W okienku **Szablony** wybierz pozycję **aplikacja systemu Windows**.

4. Nazwij projekt `ConcurrencyWalkthrough`, a następnie wybierz przycisk **OK**.

     Program Visual Studio dodaje projekt do **Eksplorator rozwiązań** i wyświetla nowy formularz w projektancie.

## <a name="create-the-northwind-dataset"></a>Tworzenie zestawu danych Northwind
 W tej sekcji utworzysz zestaw danych o nazwie `NorthwindDataSet`.

#### <a name="to-create-the-northwinddataset"></a>Aby utworzyć NorthwindDataSet

1. W menu **dane** wybierz polecenie **Dodaj nowe źródło danych**.

     Zostanie otwarty [Kreator konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) .

2. Na ekranie **Wybierz typ źródła danych**wybierz pozycję **baza danych**.

3. Wybierz połączenie z przykładową bazą danych Northwind z listy dostępnych połączeń. Jeśli połączenie nie jest dostępne na liście połączeń, wybierz pozycję**nowe połączenie** .

    > [!NOTE]
    > Jeśli łączysz się z lokalnym plikiem bazy danych, wybierz opcję **nie** , gdy chcesz dodać plik do projektu.

4. Na ekranie **Zapisz parametry połączenia do pliku konfiguracji aplikacji**wybierz pozycję **dalej**.

5. Rozwiń węzeł **tabele** i wybierz tabelę `Customers`. Domyślna nazwa zestawu danych powinna być `NorthwindDataSet`.

6. Wybierz pozycję **Zakończ** , aby dodać zestaw danych do projektu.

## <a name="create-a-data-bound-datagridview-control"></a>Tworzenie kontrolki DataGridView powiązanej z danymi
 W tej sekcji utworzysz <xref:System.Windows.Forms.DataGridView>, przeciągając element **Customers** z okna **źródła danych** na formularz systemu Windows.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Aby utworzyć formant DataGridView, który jest powiązany z tabelą Customers

1. W menu **dane** wybierz **Pokaż źródła danych** , aby otworzyć **okno źródła danych**.

2. W oknie **źródła danych** rozwiń węzeł **NorthwindDataSet** , a następnie wybierz tabelę **Customers** .

3. Wybierz strzałkę w dół w węźle tabela, a następnie na liście rozwijanej wybierz pozycję **DataGridView** .

4. Przeciągnij tabelę do pustego obszaru formularza.

     Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `CustomersDataGridView` i <xref:System.Windows.Forms.BindingNavigator> o nazwie `CustomersBindingNavigator` są dodawane do formularza, który jest powiązany z <xref:System.Windows.Forms.BindingSource>. jest to w, a następnie jest powiązane z tabelą `Customers` w `NorthwindDataSet`.

## <a name="test-the-form"></a>Testowanie formularza
 Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami do tego momentu.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

1. Wybierz klawisz **F5** , aby uruchomić aplikację

     Formularz zostanie wyświetlony z kontrolką <xref:System.Windows.Forms.DataGridView>, która jest wypełniana danymi z tabeli `Customers`.

2. W menu **Debuguj** wybierz polecenie**Zatrzymaj debugowanie**.

## <a name="handleconcurrency-errors"></a>Błędy Handleconcurrency
 Sposób obsługi błędów zależy od konkretnych reguł firmy, które regulują aplikację. W tym instruktażu używamy następującej strategii jako przykładu, aby tohandle błąd współbieżności.

 Applicationpresents użytkownika na trzy wersje rekordu:

- Bieżący rekord w bazie danych

- Oryginalny rekord, który jest ładowany do zestawu danych

- Proponowane zmiany w zestawie danych

  Użytkownik może zastąpić bazę danych zaproponowaną wersją lub anulować aktualizację i odświeżyć zestaw danych przy użyciu nowych wartości z bazy danych.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Aby włączyć obsługę błędów współbieżności

1. Utwórz niestandardową procedurę obsługi błędów.

2. Wyświetl opcje dla użytkownika.

3. Przetwórz odpowiedź użytkownika.

4. Wyślij ponownie aktualizację lub zresetuj dane w zestawie danych.

### <a name="addcode-to-handle-the-concurrency-exception"></a>AddCode obsługujący wyjątek współbieżności
 Podczas próby wykonania aktualizacji, gdy zostanie zgłoszony wyjątek, zazwyczaj trzeba wykonać coś z informacjami podanymi przez zgłoszony wyjątek.

 W tej sekcji dodasz kod, który próbuje zaktualizować bazę danych. Obsługiwane są również wszystkie <xref:System.Data.DBConcurrencyException>, które mogą zostać podniesione, a także inne wyjątki.

> [!NOTE]
> Metody `CreateMessage` i `ProcessDialogResults` zostaną dodane w dalszej części tego przewodnika.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Aby dodać obsługę błędów dla błędu współbieżności

1. Dodaj następujący kod poniżej metody `Form1_Load`:

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. Zastąp metodę `CustomersBindingNavigatorSaveItem_Click`, aby wywołać metodę `UpdateDatabase`, tak aby wyglądała następująco:

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>Displaychoices użytkownikowi
 Właśnie napisany kod wywołuje procedurę `CreateMessage`, aby wyświetlić informacje o błędzie dla użytkownika. W tym instruktażu należy użyć okna komunikatu, aby wyświetlić różne wersje rekordu dla użytkownika. Dzięki temu użytkownik może wybrać, czy rekord ma zostać zastąpiony zmianami, czy anulować edycję. Gdy użytkownik wybierze opcję (kliknie przycisk) w oknie komunikatu, odpowiedź jest przesyłana do metody `ProcessDialogResult`.

##### <a name="to-create-the-message-to-display-to-the-user"></a>Aby utworzyć komunikat, który ma być wyświetlany użytkownikowi

- Utwórz komunikat, dodając następujący kod do **edytora kodu**. Wprowadź ten kod poniżej metody `UpdateDatabase`.

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>Przetwórz odpowiedź użytkownika
 Musisz również mieć kod, aby przetworzyć odpowiedź użytkownika do okna komunikatu. Dostępne są opcje zastępowania bieżącego rekordu w bazie danych z proponowaną zmianą lub porzucenia lokalnych zmian i odświeżenia tabeli danych z rekordem, który jest obecnie w bazie danych. Jeśli użytkownik wybierze wartość tak, Metoda <xref:System.Data.DataTable.Merge%2A> zostanie wywołana z argumentem *PreserveChanges* ustawionym na `true`. Powoduje to pomyślną próbę aktualizacji, ponieważ oryginalna wersja rekordu jest teraz zgodna z rekordem w bazie danych.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Aby przetworzyć dane wejściowe użytkownika z okna komunikatu

- Dodaj następujący kod poniżej kodu, który został dodany w poprzedniej sekcji.

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Testowanie formularza
 Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami. Aby symulować naruszenie współbieżności, należy zmienić dane w bazie danych po wypełnieniu NorthwindDataSet.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

1. Wybierz klawisz **F5** , aby uruchomić aplikację.

2. Po wyświetleniu formularza, pozostaw go uruchomiony i przejdź do środowiska IDE programu Visual Studio.

3. W menu **Widok** wybierz **Eksplorator serwera**.

4. W **Eksplorator serwera**rozwiń połączenie używane przez aplikację, a następnie rozwiń węzeł **tabele** .

5. Kliknij prawym przyciskiem myszy tabelę **Customers** , a następnie wybierz polecenie **Pokaż dane tabeli**.

6. W pierwszym rekordzie (`ALFKI`) Zmień `ContactName` na `Maria Anders2`.

    > [!NOTE]
    > Przejdź do innego wiersza, aby zatwierdzić zmianę.

7. Przejdź do formularza z uruchomioną `ConcurrencyWalkthrough`.

8. W pierwszym rekordzie w formularzu (`ALFKI`) Zmień `ContactName` na `Maria Anders1`.

9. Wybierz przycisk **Zapisz** .

     Wystąpił błąd współbieżności i pojawia się okno komunikatu.

10. Wybranie pozycji **nie** powoduje anulowania aktualizacji i zaktualizowanie zestawu danych wartościami, które znajdują się obecnie w bazie danych. Wybranie pozycji **tak** zapisuje proponowaną wartość do bazy danych.

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)