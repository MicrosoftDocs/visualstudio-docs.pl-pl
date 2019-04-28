---
title: Obsługiwanie wyjątku współbieżności | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 421360421a732935d452053630c17cda319f4b0d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434501"
---
# <a name="handle-a-concurrency-exception"></a>Obsługiwanie wyjątku współbieżności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyjątki współbieżności (<xref:System.Data.DBConcurrencyException>) są wywoływane, gdy dwóch użytkowników podejmują próby zmiany te same dane w bazie danych, w tym samym czasie. W tym instruktażu utworzysz aplikacji Windows, który ilustruje sposób catch <xref:System.Data.DBConcurrencyException>, znajdź wiersz, który spowodował błąd i Dowiedz się, strategii, sposobu jego obsługi.  
  
 Ten przewodnik przeprowadzi Cię przez następujący proces:  
  
1. Utwórz nową **aplikacji Windows** projektu.  
  
2. Utwórz nowy zestaw danych oparty na Northwind `Customers` tabeli.  
  
3. Tworzenie formularza za pomocą <xref:System.Windows.Forms.DataGridView> do wyświetlania danych.  
  
4. Wypełnianie zestawu danych danymi z `Customers` tabeli w bazie danych Northwind.  
  
5. Użyj [narzędzia graficzne bazy danych](http://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) w programie Visual Studio do uzyskiwania bezpośredniego dostępu do `Customers` tabela danych i zmienić rekord.  
  
6. Zmień ten sam rekord na inną wartość, zaktualizować zestaw danych, a próba zapisania zmian w bazie danych, co powoduje błąd współbieżności, są zgłaszane.  
  
7. Wychwycić błąd, a następnie wyświetlić różne wersje rekordu, dzięki czemu użytkownik określić, czy należy kontynuować, a także zaktualizować bazę danych lub anulować aktualizację.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu, należy:  
  
- Dostęp do przykładowej bazy danych Northwind z uprawnieniami do wykonywania aktualizacji.
  
> [!NOTE]
> Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji, którego używasz. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Tworzenie nowego projektu  
 Swoje Instruktaż należy rozpocząć od tworzenia nowej aplikacji Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows  
  
1. Na **pliku** menu, Utwórz nowy projekt.  
  
2. W **typów projektów** okienku, wybierz język programowania.  
  
3. W **szablony** okienku wybierz **aplikacji Windows**.  
  
4. Nadaj projektowi nazwę `ConcurrencyWalkthrough`, a następnie wybierz pozycję **OK**.  
  
     Program Visual Studio dodaje projekt do **Eksploratora rozwiązań** i wyświetla nowy formularz w projektancie.  
  
## <a name="create-the-northwind-dataset"></a>Tworzenie zestawu danych Northwind  
 W tej sekcji utworzysz zestaw danych o nazwie `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>Aby utworzyć NorthwindDataSet.  
  
1. Na **danych** menu, wybierz **Dodaj nowe dane źródła**.  
  
     [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) zostanie otwarty.  
  
2. Na **wybierz typ źródła danych**ekranu, wybierz opcję **bazy danych**.  
  
3. Wybierz połączenie z przykładową bazą danych Northwind, z listy dostępnych połączeń. Jeśli połączenie nie jest dostępne na liście połączeń, wybierz opcję**nowe połączenie**  
  
    > [!NOTE]
    > Jeśli łączysz się z plikiem lokalnej bazy danych, wybierz opcję **nie** po wyświetleniu monitu, jeśli w przypadku chcesz dodać plik do projektu.  
  
4. Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji**ekranu, wybierz opcję **dalej**.  
  
5. Rozwiń **tabel** a następnie wybierz węzeł `Customers` tabeli. Domyślna nazwa zestawu danych powinny być `NorthwindDataSet`.  
  
6. Wybierz **Zakończ** można dodać zestaw danych do projektu.  
  
## <a name="create-a-data-bound-datagridview-control"></a>Tworzenie formantu DataGridView powiązanych z danymi  
 W tej sekcji utworzysz <xref:System.Windows.Forms.DataGridView> , przeciągając **klientów** elementu z **źródeł danych** okna do formularza Windows.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Aby utworzyć formant DataGridView, który jest powiązany z tabeli Customers  
  
1. Na **danych** menu, wybierz **Pokaż źródła danych** otworzyć **okna źródeł danych**.  
  
2. W **źródeł danych** okna, rozwiń węzeł **NorthwindDataSet** węzeł, a następnie wybierz **klientów** tabeli.  
  
3. Wybierz strzałkę w dół w węźle tabeli, a następnie wybierz **DataGridView** na liście rozwijanej.  
  
4. Przeciągnij tabelę na wolne miejsce formularza.  
  
     A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `CustomersDataGridView` i <xref:System.Windows.Forms.BindingNavigator> o nazwie `CustomersBindingNavigator` są dodawane do formularza, który jest powiązany z <xref:System.Windows.Forms.BindingSource>. Jest to, in, Włącz powiązany jest `Customers` tabelę `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Przetestuj formularz  
 Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami do tej pory.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
1. Wybierz **F5** do uruchamiania aplikacji  
  
     Zostanie wyświetlony formularz z <xref:System.Windows.Forms.DataGridView> formant na nim, który jest wypełniony przy użyciu danych z `Customers` tabeli.  
  
2. Na **debugowania** menu, wybierz opcję**Zatrzymaj debugowanie**.  
  
## <a name="handleconcurrency-errors"></a>Błędy Handleconcurrency  
 Sposób obsługi błędów jest jest zależny od firmy zasady aplikacji. W tym przewodniku używamy strategia na przykład dotyczące tohandle błąd współbieżności.  
  
 Applicationpresents użytkownika za pomocą trzech wersjach rekordu:  
  
- Bieżący rekord w bazie danych  
  
- Oryginalny rekord, który jest ładowany do zestawu danych  
  
- Proponowane zmiany w zestawie danych  
  
  Następnie użytkownik będzie mógł zastąpienia bazy danych przy użyciu proponowanych wersji lub anulować aktualizację i odświeżyć zestaw danych z nowymi wartościami z bazy danych.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Aby włączyć obsługę błędów współbieżności  
  
1. Utwórz procedurę obsługi błędów niestandardowych.  
  
2. Wyświetlanie opcji dla użytkownika.  
  
3. Przetwarzanie odpowiedzi użytkownika.  
  
4. Wyślij ponownie aktualizację, lub przywrócić dane w zestawie danych.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode do obsługi wyjątku współbieżności  
 Gdy użytkownik podejmie próbę przeprowadzenia aktualizacji, a następnie pobiera zgłoszony wyjątek, zazwyczaj chcesz zrobić coś z informacjami, które są dostarczane przez zgłoszony wyjątek.  
  
 W tej sekcji dodasz kod, który próbuje zaktualizować bazę danych. Możesz również obsługiwać dowolne <xref:System.Data.DBConcurrencyException> , może uzyskać wywołane, a także inne wyjątki.  
  
> [!NOTE]
> `CreateMessage` i `ProcessDialogResults` metody zostaną dodane w dalszej części tego przewodnika.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Aby dodać obsługę błędów dla błąd współbieżności  
  
1. Dodaj następujący kod poniżej `Form1_Load` metody:  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2. Zastąp `CustomersBindingNavigatorSaveItem_Click` metodę do wywołania `UpdateDatabase` metoda tak, aby wyglądał następująco:  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Displaychoices do użytkownika  
 Kod został właśnie powstała z jednego wywołania `CreateMessage` procedury, aby wyświetlić informacje o błędzie dla użytkownika. W tym przewodniku używasz okno komunikatu do wyświetlania różnych wersji rekordu użytkownika. Dzięki temu użytkownikowi określenie, czy chcesz zastąpić rekord zmiany lub anulowania edycji. Gdy użytkownik wybierze opcję (kliknie przycisk) w oknie komunikatu, odpowiedź jest przekazywany do `ProcessDialogResult` metody.  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>Aby utworzyć komunikat wyświetlany użytkownikowi  
  
- Utwórz wiadomość, dodając następujący kod, aby **Edytor kodu**. Wprowadź poniżej kod `UpdateDatabase` metody.  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>Przetwarzanie odpowiedzi użytkownika  
 Należy również kod, aby przetworzyć odpowiedzi użytkownika w oknie komunikatu. Dostępne opcje to można zastąpić proponowanej zmiany bieżącego rekordu w bazie danych lub Porzuć zmiany lokalne i Odśwież tabelę danych z rekordu, który jest obecnie dostępna w bazie danych. Jeśli użytkownik zdecyduje się tak, <xref:System.Data.DataTable.Merge%2A> metoda jest wywoływana z *preserveChanges* argument wartość `true`. Powoduje to próba aktualizacji był udany, ponieważ oryginalną wersję rekordu jest teraz zgodna rekord w bazie danych.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>Użytkownik przetworzyć dane wejściowe z okna komunikatu  
  
- Dodaj następujący kod poniższego kodu, który został dodany w poprzedniej sekcji.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Przetestuj formularz  
 Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami. Aby symulować Naruszenie współbieżności, musisz zmienić dane z bazy danych po wypełnieniu NorthwindDataSet.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
1. Wybierz **F5** do uruchomienia aplikacji.  
  
2. Gdy zostanie wyświetlony formularz, będzie działać, a następnie przełącz się do środowiska IDE programu Visual Studio.  
  
3. Na **widoku** menu, wybierz **Eksploratora serwera**.  
  
4. W **Eksploratora serwera**, rozwiń węzeł połączenia aplikacji za pomocą, a następnie rozwiń **tabel** węzła.  
  
5. Kliknij prawym przyciskiem myszy **klientów** tabeli, a następnie wybierz **Pokaż dane tabeli**.  
  
6. W pierwszym rekordzie (`ALFKI`) Zmień `ContactName` do `Maria Anders2`.  
  
    > [!NOTE]
    > Przejdź do innego wiersza, aby zatwierdzić zmiany.  
  
7. Przełącz się do `ConcurrencyWalkthrough`korzysta z formularza.  
  
8. W pierwszym rekordzie na formularzu (`ALFKI`), zmień`ContactName` do `Maria Anders1`.  
  
9. Wybierz ikonę **Zapisz**.  
  
     Błąd współbieżności, a pojawi się okno komunikatu.  
  
10. Wybieranie **nie** anuluje aktualizacji i aktualizuje zestaw danych o wartości, które są obecnie dostępne w bazie danych. Wybieranie **tak** zapisuje proponowana wartość w bazie danych.
  
## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)