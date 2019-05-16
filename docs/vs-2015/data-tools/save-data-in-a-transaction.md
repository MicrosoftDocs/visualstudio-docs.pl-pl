---
title: Zapisywanie danych w ramach transakcji | Dokumentacja firmy Microsoft
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 08480e46ab492acb1c7ab10c8514897721708aba
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692455"
---
# <a name="save-data-in-a-transaction"></a>zapisywanie danych w transakcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak zapisywanie danych w ramach transakcji przy użyciu <xref:System.Transactions> przestrzeni nazw. W tym przykładzie użyto `Customers` i `Orders` tabel z przykładowej bazy danych Northwind.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten przewodnik wymaga dostępu do przykładowej bazy danych Northwind.
  
## <a name="create-a-windows-application"></a>Tworzenie aplikacji Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt Windows  
  
1. W programie Visual Studio na **pliku** menu Utwórz nową **projektu**.  
  
2. Nadaj projektowi nazwę **SavingDataInATransactionWalkthrough**.  
  
3. Wybierz **aplikacji Windows**, a następnie wybierz pozycję **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **SavingDataInATransactionWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="create-a-database-data-source"></a>Tworzenie źródła danych bazy danych  
 Ten krok używa [Kreatora konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) można utworzyć źródła danych, na podstawie `Customers` i `Orders` tabel w bazie danych Northwind.  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1. Na **danych** menu, wybierz opcję**Pokaż źródła danych**.  
  
2. W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
3. Na **wybierz typ źródła danych**ekranu, wybierz opcję **bazy danych**, a następnie wybierz pozycję **dalej**.  
  
4. Na **wybierz połączenie danych**wykonaj ekranu, jedną z następujących czynności:  
  
    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
         —lub—  
  
    - Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okna dialogowego pole, a następnie utwórz połączenie z bazą danych Northwind.  
  
5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz **dalej**.  
  
6. Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** ekranu, wybierz opcję **dalej**.  
  
7. Na **wybierz obiekty bazy danych** ekranu, a następnie rozwiń **tabel** węzła.  
  
8. Wybierz `Customers` i `Orders` tabel, a następnie wybierz **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu i `Customers` i `Orders` tabele są wyświetlane w **źródeł danych** okna.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols do formularza  
 Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć dane powiązane kontrolek w formularzu Windows  
  
- W **źródeł danych** okna, rozwiń węzeł **klientów** węzła.  
  
- Przeciągnij główny **klientów** węzła z **źródeł danych** okna na **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
- Przeciągnij powiązane **zamówienia** węzła (nie main **zamówienia** węzła, ale poniżej węzła powiązanej tabeli podrzędnej **faks** kolumny) do poniższego formularza  **CustomersDataGridView**.  
  
     A <xref:System.Windows.Forms.DataGridView> pojawia się w formularzu. OrdersTableAdapter i <xref:System.Windows.Forms.BindingSource> są wyświetlane w zasobniku składnika.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Dodaj odwołanie do zestawu System.Transactions  
 Użyj transakcji <xref:System.Transactions> przestrzeni nazw. Odwołanie do zestawu System.Transactions nie zostanie dodany domyślnie, więc trzeba ręcznie dodać ją.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Aby dodać odwołanie do pliku System.Transactions DLL  
  
1. Na **projektu** menu, wybierz opcję**Dodaj odwołanie**.  
  
2. Wybierz **System.Transactions**(na **.NET** karty), a następnie wybierz pozycję **OK**.  
  
     Odwołanie do **System.Transactions** zostanie dodany do projektu.  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Kod Modifythe BindingNavigator SaveItem przycisku  
 Jako pierwszą tabelę upuszczone na formularzu, kod jest dodawany domyślnie `click` zdarzeń zapisu znajdujący się na <xref:System.Windows.Forms.BindingNavigator>. Należy ręcznie dodać kod, aby zaktualizować wszystkie dodatkowe tabele. W tym przewodniku refaktoryzacji istniejącego Zapisz kod poza zapisywania program obsługi zdarzeń kliknięcia przycisku. Musimy również utworzyć kilka więcej metod, które umożliwiają korzystanie z funkcji określonej aktualizacji oparte na tego, czy wiersz musi być dodane lub usunięte.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>Aby zmodyfikować wygenerowaną automatycznie zapisać kod  
  
1. Wybierz **Zapisz** znajdujący się na **CustomersBindingNavigator** (przycisk z ikoną dyskietki).  
  
2. Zastąp `CustomersBindingNavigatorSaveItem_Click` metoda następującym kodem:  
  
    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
   Uzgadnianie zmian do powiązanych danych kolejność jest następująca:  
  
- Usuń rekordy podrzędne. (W tym przypadku usuwania rekordów z `Orders` tabeli.)  
  
- Usuwanie rekordów nadrzędnych. (W tym przypadku usuwania rekordów z `Customers` tabeli.)  
  
- Wstawianie rekordów nadrzędnych. (W tym przypadku wstawiania rekordów w `Customers` tabeli.)  
  
- Wstaw rekordy podrzędne. (W tym przypadku wstawiania rekordów w `Orders` tabeli.)  
  
#### <a name="to-delete-existing-orders"></a>Aby usunąć istniejące zamówienia  
  
- Dodaj następujący kod `DeleteOrders` metody **Form1**:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>Aby usunąć istniejący klienci  
  
- Dodaj następujący kod `DeleteCustomers` metody **Form1**:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>Aby dodać nowych klientów  
  
- Dodaj następujący kod `AddNewCustomers` metody **Form1**:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>Aby dodać nowe zamówienia  
  
- Dodaj następujący kod `AddNewOrders` metody **Form1**:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>Uruchamianie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
- Wybierz **F5** do uruchomienia aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
