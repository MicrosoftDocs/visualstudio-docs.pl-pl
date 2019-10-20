---
title: Zapisywanie danych w transakcji | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671089"
---
# <a name="save-data-in-a-transaction"></a>zapisywanie danych w transakcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób zapisywania danych w transakcji przy użyciu przestrzeni nazw <xref:System.Transactions>. Ten przykład używa tabel `Customers` i `Orders` z przykładowej bazy danych Northwind.

## <a name="prerequisites"></a>Wymagania wstępne
 Ten Instruktaż wymaga dostępu do przykładowej bazy danych Northwind.

## <a name="create-a-windows-application"></a>Tworzenie aplikacji systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji systemu Windows**.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt systemu Windows

1. W programie Visual Studio w menu **plik** Utwórz nowy **projekt**.

2. Nazwij projekt **SavingDataInATransactionWalkthrough**.

3. Wybierz pozycję **aplikacja systemu Windows**, a następnie wybierz przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **SavingDataInATransactionWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="create-a-database-data-source"></a>Tworzenie źródła danych bazy danych
 Ten krok powoduje użycie [Kreatora konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) w celu utworzenia źródła danych opartego na `Customers` i `Orders` tabelach w przykładowej bazie danych Northwind.

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** wybierz pozycję**Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Na ekranie **Wybierz typ źródła danych**wybierz pozycję **baza danych**, a następnie wybierz przycisk **dalej**.

4. Na ekranie **Wybierz połączenie danych**wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         —lub—

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** i utworzyć połączenie z bazą danych Northwind.

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz przycisk **dalej**.

6. Na ekranie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej**.

7. Na ekranie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Zaznacz tabele `Customers` i `Orders`, a następnie wybierz pozycję **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a tabele `Customers` i `Orders` są wyświetlane w oknie **źródła danych** .

## <a name="addcontrols-to-the-form"></a>Addcontrols do formularza
 Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć kontrolki powiązane z danymi w formularzu systemu Windows

- W oknie **źródła danych** rozwiń węzeł **klienci** .

- Przeciągnij główny węzeł **Customers** z okna **źródła danych** na **formularz Form1**.

     Kontrolka <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania po rekordach pojawiają się w formularzu. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

- Przeciągnij węzeł powiązane **zamówienia** (nie główny węzeł **zamówienia** , ale węzeł powiązanej tabeli podrzędnej poniżej kolumny **faks** ) na formularzu poniżej **customersDataGridView**.

     @No__t_0 pojawi się w formularzu. OrdersTableAdapter i <xref:System.Windows.Forms.BindingSource> pojawiają się na pasku składnika.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Dodawanie odwołania do zestawu System. Transactions
 Transakcje używają przestrzeni nazw <xref:System.Transactions>. Odwołanie projektu do zestawu System. Transactions nie jest domyślnie dodawane, więc należy je dodać ręcznie.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Aby dodać odwołanie do pliku DLL system. Transactions

1. W menu **projekt** wybierz polecenie**Dodaj odwołanie**.

2. Wybierz pozycję **System. Transactions**(na karcie **.NET** ), a następnie wybierz przycisk **OK**.

     Odwołanie do elementu **System. Transactions** jest dodawane do projektu.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Kod Modifythe na przycisku SaveItem BindingNavigator
 W przypadku pierwszej tabeli opuszczonej w formularzu kod jest domyślnie dodawany do zdarzenia `click` przycisku Zapisz na <xref:System.Windows.Forms.BindingNavigator>. Musisz ręcznie dodać kod, aby zaktualizować wszystkie dodatkowe tabele. W tym instruktażu Refaktoryzacja istniejący kod Zapisz z programu obsługi zdarzeń kliknięcia przycisku Zapisz. Tworzymy również kilka metod, aby zapewnić określoną funkcję aktualizacji w zależności od tego, czy należy dodać czy usunąć wiersz.

#### <a name="to-modify-the-auto-generated-save-code"></a>Aby zmodyfikować wygenerowany automatycznie kod zapisu

1. Wybierz przycisk **Zapisz** na **CustomersBindingNavigator** (przycisk z ikoną dyskietki).

2. Zastąp metodę `CustomersBindingNavigatorSaveItem_Click` następującym kodem:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   Kolejność uzgadniania zmian związanych z danymi jest następująca:

- Usuń rekordy podrzędne. (W tym przypadku Usuń rekordy z tabeli `Orders`).

- Usuń rekordy nadrzędne. (W tym przypadku Usuń rekordy z tabeli `Customers`).

- Wstaw rekordy nadrzędne. (W tym przypadku Wstaw rekordy w tabeli `Customers`).

- Wstaw rekordy podrzędne. (W tym przypadku Wstaw rekordy w tabeli `Orders`).

#### <a name="to-delete-existing-orders"></a>Aby usunąć istniejące zamówienia

- Dodaj następującą metodę `DeleteOrders` do **formularza Form1**:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Aby usunąć istniejących klientów

- Dodaj następującą metodę `DeleteCustomers` do **formularza Form1**:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Aby dodać nowych klientów

- Dodaj następującą metodę `AddNewCustomers` do **formularza Form1**:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Aby dodać nowe zamówienia

- Dodaj następującą metodę `AddNewOrders` do **formularza Form1**:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Uruchom aplikację

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

- Wybierz klawisz **F5** , aby uruchomić aplikację.

## <a name="see-also"></a>Zobacz też
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
