---
title: Zapisywanie danych za pomocą TableAdapter dbdirect — metody | Dokumentacja firmy Microsoft
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cba6f91dd6dc0bb826531a312dc6ca5c94b21a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558745"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik zawiera szczegółowe instrukcje na temat uruchamiania instrukcji SQL bezpośrednio w odniesieniu do bazy danych przy użyciu dbdirect — metody TableAdapter. Dbdirect — metody TableAdapter zapewniają wystarczające poziom kontroli nad aktualizacje bazy danych. Umożliwia ich uruchamianie określonych instrukcji języka SQL i procedur składowanych, wywołując poszczególnych `Insert`, `Update`, i `Delete` metody, stosownie do potrzeb przez aplikację (w przeciwieństwie przeciążone `Update` metodę, która wykonuje AKTUALIZACJĘ Instrukcjami INSERT i DELETE wszystko w jednym wywołaniu).  
  
 Z tego instruktażu dowiesz się jak:  
  
- Utwórz nową **aplikacji Windows**.  
  
- Tworzenie i konfigurowanie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
- Wybierz kontrolkę do utworzenia w formularzu podczas przeciągania elementów z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
- Tworzenie formularza powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna na formularzu.  
  
- Dodaj metody do bezpośredniego dostępu do bazy danych oraz wykonać wstawiania, aktualizacji i usuwania...  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
- Dostęp do przykładowej bazy danych Northwind.
  
## <a name="create-a-windows-application"></a>Tworzenie aplikacji Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt Windows  
  
1. W programie Visual Studio na **pliku** menu Utwórz nową **projektu**.  
  
2. Nadaj projektowi nazwę **TableAdapterDbDirectMethodsWalkthrough**.  
  
3. Wybierz **aplikacji Windows**, a następnie wybierz pozycję **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **TableAdapterDbDirectMethodsWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych  
 Ten krok używa **Kreatora konfiguracji źródła danych** można utworzyć źródła danych, na podstawie `Region` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia.
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1. Na **danych** menu, wybierz opcję **Pokaż źródła danych**.  
  
2. W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
3. Na **wybierz typ źródła danych** ekranu, wybierz opcję **bazy danych**, a następnie wybierz pozycję **dalej**.  
  
4. Na **wybierz połączenie danych** ekranu, wykonaj jedną z następujących czynności:  
  
    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
         —lub—  
  
    - Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.  
  
5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz **dalej**.  
  
6. Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** ekranu, wybierz opcję **dalej**.  
  
7. Na **wybierz obiekty bazy danych** ekranu, a następnie rozwiń **tabel** węzła.  
  
8. Wybierz `Region` tabeli, a następnie wybierz **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu i `Region` tabela zostanie wyświetlona w **źródeł danych** okna.  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols do formularza, aby wyświetlić dane  
 Tworzenie formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć dane powiązane kontrolek w formularzu Windows  
  
- Przeciągnij główny **Region** węzła z **źródeł danych** okna na formularzu.  
  
     A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Aby dodać przyciski, który będzie wybierany poszczególnych TableAdapter dbdirect — metody  
  
1. Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na **Form1** (poniżej **RegionDataGridView**).  
  
2. Ustaw następujące **nazwa** i **tekstu** właściwości dla każdego przycisku.  
  
    |Nazwa|Tekst|  
    |----------|----------|  
    |`InsertButton`|**Wstaw**|  
    |`UpdateButton`|**Aktualizacja**|  
    |`DeleteButton`|**Delete**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Aby dodać kod, aby wstawianie nowych rekordów do bazy danych  
  
1. Wybierz **InsertButton** utworzyć program obsługi zdarzeń dla zdarzenia kliknięcia i Otwórz formularz w edytorze kodu.  
  
2. Zastąp `InsertButton_Click` programu obsługi zdarzeń z następującym kodem:  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Aby dodać kod do aktualizowania rekordów w bazie danych  
  
1. Kliknij dwukrotnie **UpdateButton** utworzyć program obsługi zdarzeń dla zdarzenia kliknięcia i Otwórz formularz w edytorze kodu.  
  
2. Zastąp `UpdateButton_Click` programu obsługi zdarzeń z następującym kodem:  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Aby dodać kod do usuwania rekordów z bazy danych  
  
1. Wybierz **DeleteButton** utworzyć program obsługi zdarzeń dla zdarzenia kliknięcia i Otwórz formularz w edytorze kodu.  
  
2. Zastąp `DeleteButton_Click` programu obsługi zdarzeń z następującym kodem:  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>Uruchamianie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
- Wybierz **F5** do uruchomienia aplikacji.  
  
- Wybierz **Wstaw** przycisk i sprawdź, czy nowy rekord jest wyświetlany w siatce.  
  
- Wybierz **aktualizacji** przycisk, a następnie sprawdź, czy rekord zostanie zaktualizowany w siatce.  
  
- Wybierz **Usuń** przycisk, a następnie sprawdź, czy rekord zostanie usunięty z siatki.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza powiązanych z danymi. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:  
  
- Dodawanie funkcji wyszukiwania do formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zapytania parametrycznego do Windows Forms aplikacji](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
- Dodawanie dodatkowych tabel do zestawu danych, wybierając **Konfigurowanie zestawu danych za pomocą kreatora** z poziomu **źródeł danych** okna. Można dodawać formanty, które wyświetlają pokrewne dane, przeciągając pokrewne węzły na formularzu. 
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
