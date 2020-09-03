---
title: Zapisywanie danych w bazie danych (wiele tabel) | Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655464"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Zapisywanie danych w bazie danych (wiele tabel)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jednym z najczęstszych scenariuszy tworzenia aplikacji jest wyświetlanie danych w formularzu w aplikacji systemu Windows, edytowanie danych i wysyłanie zaktualizowanych danych z powrotem do bazy danych. Ten Instruktaż tworzy formularz, który wyświetla dane z dwóch powiązanych tabel i pokazuje, jak edytować rekordy i zapisywać zmiany z powrotem w bazie danych. Ten przykład używa `Customers` tabel i `Orders` z przykładowej bazy danych Northwind.

 Dane w aplikacji można zapisywać z powrotem do bazy danych przez wywołanie `Update` metody TableAdapter. Gdy przeciągniesz tabele z okna **źródła danych** na formularz, zostanie automatycznie dodany kod wymagany do zapisania danych. Wszelkie dodatkowe tabele dodawane do formularza wymagają ręcznego dodania tego kodu. W tym instruktażu pokazano, jak dodać kod, aby zapisać aktualizacje z więcej niż jednej tabeli.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub używanej wersji. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie nowego projektu **aplikacji systemu Windows** .

- Tworzenie i Konfigurowanie źródła danych w aplikacji za pomocą [Kreatora konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Ustawianie kontrolek elementów w [oknie źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Tworzenie kontrolek powiązanych z danymi przez przeciąganie elementów z okna **źródła danych** na formularz.

- Modyfikowanie kilku rekordów w każdej tabeli w zestawie danych.

- Modyfikowanie kodu w celu wysyłania zaktualizowanych danych z powrotem do bazy danych.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind.

## <a name="create-the-windows-application"></a>Tworzenie aplikacji systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji systemu Windows**. Przypisanie nazwy do projektu jest opcjonalne w tym kroku, ale przekażemy mu nazwę, ponieważ planujemy ją zapisać później.

#### <a name="to-create-the-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji systemu Windows

1. W menu **plik** Utwórz nowy projekt.

2. Nadaj nazwę projektowi `UpdateMultipleTablesWalkthrough` .

3. Wybierz pozycję **aplikacja systemu Windows**, a następnie wybierz przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **UpdateMultipleTablesWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych
 Ten krok powoduje utworzenie źródła danych z bazy danych Northwind przy użyciu **Kreatora konfiguracji źródła danych**. Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind.

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** wybierz pozycję**Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję**Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Na ekranie **Wybierz typ źródła danych**wybierz pozycję **baza danych**, a następnie wybierz przycisk **dalej**.

4. Na ekranie **Wybierz połączenie danych**wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         -lub-

    - Wybierz pozycję **nowe połączenie** , aby otworzyć okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz przycisk **dalej**.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji**wybierz pozycję **dalej**.

7. Na ekranie **Wybierz obiekty bazy danych**rozwiń węzeł **tabele** .

8. Wybierz tabele **Customers** i **Orders** , a następnie wybierz pozycję **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a tabele są wyświetlane w oknie **źródła danych** .

## <a name="set-the-controls-to-be-created"></a>Ustaw kontrolki do utworzenia
 W tym instruktażu dane w `Customers` tabeli znajdują się w układzie **szczegółów** , w którym dane są wyświetlane w poszczególnych kontrolkach. Dane z `Orders` tabeli są w układzie **siatki** , który jest wyświetlany w <xref:System.Windows.Forms.DataGridView> kontrolce.

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Aby ustawić typ upuszczenia dla elementów w oknie źródła danych

1. W oknie **źródła danych** rozwiń węzeł **klienci** .

2. W węźle **klienci** wybierz pozycję **szczegóły** z listy kontrolki, aby zmienić formant tabeli **Customers** na poszczególne kontrolki. Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Tworzenie formularza powiązanego z danymi
 Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć kontrolki powiązane z danymi w formularzu

1. Przeciągnij główny węzeł **Customers** z okna **źródła danych** na **formularz Form1**.

     Formanty powiązane z danymi, które mają opisowe etykiety, są wyświetlane w formularzu wraz z paskiem narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) na potrzeby nawigowania po rekordach. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

2. Przeciągnij węzeł powiązane **zamówienia** z okna **źródła danych** na **formularz Form1**.

    > [!NOTE]
    > Węzeł powiązane **zamówienia** znajduje się poniżej kolumny **faks** i jest węzłem podrzędnym węzła **Customers** .

     <xref:System.Windows.Forms.DataGridView>Kontrolka i pasek narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) na potrzeby nawigowania po rekordach pojawiają się w formularzu. OrdersTableAdapter i <xref:System.Windows.Forms.BindingSource> pojawia się na pasku składnika.

## <a name="addcode-to-update-the-database"></a>AddCode w celu zaktualizowania bazy danych
 Bazę danych można zaktualizować, wywołując `Update` metody TableAdapters **klientów** i **zamówień** . Domyślnie program obsługi zdarzeń dla przycisku **Zapisz** <xref:System.Windows.Forms.BindingNavigator> jest dodawany do kodu formularza w celu wysyłania aktualizacji do bazy danych programu. Ta procedura modyfikuje kod w celu wysłania aktualizacji w odpowiedniej kolejności. Eliminuje to możliwość podnoszenia błędów integralności referencyjnej. Kod implementuje również obsługę błędów przez zawijanie wywołania aktualizacji w bloku try-catch. Możesz zmodyfikować kod, aby spełniał wymagania aplikacji.

> [!NOTE]
> Dla jasności ten przewodnik nie korzysta z transakcji. Jeśli jednak aktualizujesz dwie lub więcej powiązanych tabel, Uwzględnij całą logikę aktualizacji w ramach transakcji. Transakcja to proces, który gwarantuje, że wszystkie powiązane zmiany w bazie danych zakończą się pomyślnie przed zatwierdzeniem jakichkolwiek zmian. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).

#### <a name="to-add-update-logic-to-the-application"></a>Aby dodać logikę aktualizacji do aplikacji

1. Wybierz przycisk **Zapisz** na stronie <xref:System.Windows.Forms.BindingNavigator> . Spowoduje to otwarcie edytora kodu w programie `bindingNavigatorSaveItem_Click` obsługi zdarzeń.

2. Zastąp kod w programie obsługi zdarzeń, aby wywołać `Update` metody powiązanej TableAdapters. Poniższy kod najpierw tworzy trzy tymczasowe tabele danych do przechowywania zaktualizowanych informacji dla każdego <xref:System.Data.DataRowState> ( <xref:System.Data.DataRowState> , <xref:System.Data.DataRowState> i <xref:System.Data.DataRowState> ). Następnie aktualizacje są uruchamiane w odpowiedniej kolejności. Kod powinien wyglądać następująco:

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>Testowanie aplikacji

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Wybierz klawisz **F5**.

2. Wprowadź pewne zmiany w danych co najmniej jednego rekordu w każdej tabeli.

3. Wybierz ikonę **Zapisz**.

4. Sprawdź wartości w bazie danych, aby sprawdzić, czy zmiany zostały zapisane.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza powiązanego z danymi w aplikacji systemu Windows. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

- Dodawanie funkcji wyszukiwania do formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zapytania parametrycznego do aplikacji Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Edytowanie źródła danych w celu dodania lub usunięcia obiektów bazy danych. Aby uzyskać więcej informacji, zobacz [How to: Edit a DataSet](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).

## <a name="see-also"></a>Zobacz też
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
