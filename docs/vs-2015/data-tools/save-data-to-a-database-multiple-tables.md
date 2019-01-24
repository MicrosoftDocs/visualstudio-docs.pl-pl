---
title: Zapisywanie danych w bazie danych (wiele tabel) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84b4ee6cba98e18379dc0e0e4fd81d8c10e37d7b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764540"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Zapisywanie danych w bazie danych (wiele tabel)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Jedną z najbardziej typowych scenariuszy w tworzeniu aplikacji jest wyświetlenie danych z formularza w aplikacji Windows, edytować dane i wysyłać zaktualizowane dane w bazie danych. Ten poradnik tworzy formularz, który wyświetla dane z dwóch pokrewnych tabel i pokazuje, jak edytować rekordy i zapisać zmiany w bazie danych. W tym przykładzie użyto `Customers` i `Orders` tabel z przykładowej bazy danych Northwind.  
  
 Dane można zapisać w aplikacji w bazie danych, wywołując `Update` metody TableAdapter. Podczas przeciągania tabel z **źródeł danych** okna na formularzu, kod, który jest wymagany w celu zapisywania danych jest automatycznie dodawany. Dodatkowe tabele, które są dodawane do formularza wymaga ręcznego dodawania tego kodu. W tym instruktażu pokazano, jak dodać kod, aby zapisać aktualizacje z więcej niż jedną tabelą.  
  
> [!NOTE]
>  Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji, którego używasz. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie nowego **aplikacji Windows** projektu.  
  
-   Tworzenie i konfigurowanie źródła danych w aplikacji za pomocą [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Określa elementy w [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Tworzenie formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.  
  
-   Modyfikowanie kilku rekordów w każdej tabeli w zestawie danych.  
  
-   Modyfikowanie kodu wysyłać zaktualizowane dane w zestawie danych w bazie danych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Dostęp do przykładowej bazy danych Northwind.
  
## <a name="create-the-windows-application"></a>Tworzenie aplikacji Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows**. Przypisanie nazwy do projektu jest opcjonalny w tym kroku, ale firma Microsoft będzie nadaj jej nazwę, ponieważ planujemy zapisanie go później.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows  
  
1.  Na **pliku** menu, Utwórz nowy projekt.  
  
2.  Nadaj projektowi nazwę `UpdateMultipleTablesWalkthrough`.  
  
3.  Wybierz **aplikacji Windows**, a następnie wybierz pozycję **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **UpdateMultipleTablesWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="create-the-data-source"></a>Utwórz źródło danych  
 Spowoduje to utworzenie źródła danych z bazy danych Northwind przy użyciu **Kreatora konfiguracji źródła danych**. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia.
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, wybierz opcję**Pokaż źródła danych**.  
  
2.  W **źródeł danych** wybierz**Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
3.  Na **wybierz typ źródła danych**ekranu, wybierz opcję **bazy danych**, a następnie wybierz pozycję **dalej**.  
  
4.  Na **wybierz połączenie danych**wykonaj ekranu, jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
         —lub—  
  
    -   Wybierz **nowe połączenie** otworzyć **Dodawanie/modyfikowanie połączenia** okno dialogowe.  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz **dalej**.  
  
6.  Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji**, wybierz opcję **dalej**.  
  
7.  Na **wybierz obiekty bazy danych**ekranu, a następnie rozwiń **tabel** węzła.  
  
8.  Wybierz **klientów** i **zamówienia** tabel, a następnie wybierz **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu, a tabele są wyświetlane w **źródeł danych** okna.  
  
## <a name="set-the-controls-to-be-created"></a>Ustawienie kontroli ma zostać utworzony  
 W tym przewodniku dane w `Customers` tabela znajduje się w **szczegóły** układu, w którym dane są wyświetlane w poszczególnych formantów. Dane z `Orders` tabela znajduje się w **siatki** układ, który jest wyświetlany w <xref:System.Windows.Forms.DataGridView> kontroli.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Aby ustawić upuszczany typ elementów w oknie źródeł danych  
  
1.  W **źródeł danych** okna, rozwiń węzeł **klientów** węzła.  
  
2.  Na **klientów** węzeł **szczegóły** z listy kontroli, aby zmienić kontrolę nad **klientów** tabeli do poszczególnych formantów. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Tworzenie formularza powiązanych z danymi  
 Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formanty powiązane z danymi formularza  
  
1.  Przeciągnij główny **klientów** węzła z **źródeł danych** okna na **Form1**.  
  
     Formanty powiązane z danymi z etykietami opisowymi są wyświetlane w formularzu, oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
2.  Przeciągnij powiązane **zamówienia** węzła z **źródeł danych** okna na **Form1**.  
  
    > [!NOTE]
    >  Powiązane **zamówienia** węzeł znajduje się poniżej **faks** kolumny, a jest elementem podrzędnym **klientów** węzła.  
  
     A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. OrdersTableAdapter i <xref:System.Windows.Forms.BindingSource> są wyświetlane w zasobniku składnika.  
  
## <a name="addcode-to-update-the-database"></a>Addcode aktualizacji bazy danych  
 Zaktualizuj bazy danych, wywołując `Update` metody **klientów** i **zamówienia** adapterów TableAdapter. Domyślnie program obsługi zdarzeń dla **Zapisz** przycisk<xref:System.Windows.Forms.BindingNavigator> zostanie dodany do kodu formularza w celu wysyłania aktualizacji do bazy danych. Ta procedura modyfikuje kod, aby wysłać aktualizacje we właściwej kolejności. Pozwala to wyeliminować możliwość zgłaszania błędów więzów integralności. Kod implementuje również dodanymi komentarzami opakowując wywołania aktualizacji w bloku try-catch. Można zmodyfikować kod odpowiednio do potrzeb aplikacji.  
  
> [!NOTE]
>  Dla jasności ten przewodnik nie używa transakcji. Jeśli aktualizujesz, dwa lub więcej powiązanych tabel, obejmuje jednak logika aktualizacji w obrębie transakcji. Transakcja jest procesem, który gwarantuje, że wszystkie powiązane zmiany w bazie danych są pomyślnie, zanim wszelkie zmiany zostaną zatwierdzone. Aby uzyskać więcej informacji, zobacz [transakcje i współbieżność](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Aby dodać logikę aktualizacji do aplikacji  
  
1.  Wybierz **Zapisz** znajdujący się na <xref:System.Windows.Forms.BindingNavigator>. Spowoduje to otwarcie edytora kodu, aby `bindingNavigatorSaveItem_Click` programu obsługi zdarzeń.  
  
2.  Zastąp kod w obsłudze zdarzeń, aby wywołać `Update` metody powiązanych elementów TableAdapter. Poniższy kod najpierw tworzy trzy tabele dane tymczasowe do przechowywania zaktualizowanych informacji dla każdego <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, i <xref:System.Data.DataRowState>). Następnie aktualizacje są uruchamiane w odpowiedniej kolejności. Kod powinien wyglądać następująco:  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Wybierz **F5**.  
  
2.  Należy wprowadzić pewne zmiany do danych z co najmniej jednego rekordu w każdej tabeli.  
  
3.  Wybierz ikonę **Zapisz**.  
  
4.  Sprawdź wartości w bazie danych, aby sprawdzić, czy zmiany zostały zapisane.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza powiązanych z danymi w aplikacji Windows. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:  
  
-   Dodawanie funkcji wyszukiwania do formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zapytania parametrycznego do Windows Forms aplikacji](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Edytowanie źródła danych, aby dodać lub usunąć obiekty bazy danych. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie zestawu danych](http://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
