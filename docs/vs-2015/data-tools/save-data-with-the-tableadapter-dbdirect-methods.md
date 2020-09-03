---
title: Zapisz dane przy użyciu metod TableAdapter DBDirect | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655418"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten Instruktaż zawiera szczegółowe instrukcje dotyczące uruchamiania instrukcji SQL bezpośrednio w bazie danych przy użyciu metod DBDirect klasy TableAdapter. Metody DBDirect TableAdapter zapewniają poziom kontroli nad aktualizacjami bazy danych. Można ich używać do uruchamiania określonych instrukcji SQL i procedur składowanych przez wywoływanie pojedynczych `Insert` `Update` metod, i, w `Delete` zależności od potrzeb aplikacji (w przeciwieństwie do przeciążonej `Update` metody, która wykonuje instrukcje Update, INSERT i DELETE w jednym wywołaniu).

 W tym instruktażu dowiesz się, jak:

- Utwórz nową **aplikację systemu Windows**.

- Utwórz i skonfiguruj zestaw danych za pomocą [Kreatora konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Wybierz kontrolkę, która ma zostać utworzona w formularzu podczas przeciągania elementów z okna **źródła danych** . Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Utwórz formularz powiązany z danymi, przeciągając elementy z okna **źródła danych** na formularz.

- Dodawanie metod w celu bezpośredniego dostępu do bazy danych i wykonywania operacji wstawiania, aktualizacji i usuwania.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind.

## <a name="create-a-windows-application"></a>Tworzenie aplikacji systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji systemu Windows**.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt systemu Windows

1. W programie Visual Studio w menu **plik** Utwórz nowy **projekt**.

2. Nazwij projekt **TableAdapterDbDirectMethodsWalkthrough**.

3. Wybierz pozycję **aplikacja systemu Windows**, a następnie wybierz przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **TableAdapterDbDirectMethodsWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="create-a-data-source-from-your-database"></a>Tworzenie źródła danych na podstawie bazy danych
 Ten krok powoduje użycie **Kreatora konfiguracji źródła danych** w celu utworzenia źródła danych na podstawie `Region` tabeli w przykładowej bazie danych Northwind. Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind.

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** wybierz pozycję **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Na ekranie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie wybierz przycisk **dalej**.

4. Na ekranie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         -lub-

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz przycisk **dalej**.

6. Na ekranie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej**.

7. Na ekranie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz `Region` tabelę, a następnie wybierz pozycję **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a `Region` tabela pojawia się w oknie **źródła danych** .

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols do formularza w celu wyświetlenia danych
 Utwórz formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć kontrolki powiązane z danymi w formularzu systemu Windows

- Przeciągnij węzeł **regionu** głównego z okna **źródła danych** na formularz.

     <xref:System.Windows.Forms.DataGridView>Kontrolka i pasek narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) na potrzeby nawigowania po rekordach pojawiają się w formularzu. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Aby dodać przyciski, które będą wywoływały poszczególne metody TableAdapter DBDirect

1. Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na **formularz Form1** (poniżej **RegionDataGridView**).

2. Dla każdego przycisku Ustaw następujące właściwości **nazwy** i **tekstu** .

    |Nazwa|Tekst|
    |----------|----------|
    |`InsertButton`|**Insert**|
    |`UpdateButton`|**Aktualizowanie**|
    |`DeleteButton`|**Usuń**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Aby dodać kod umożliwiający wstawianie nowych rekordów do bazy danych

1. Wybierz pozycję **InsertButton** , aby utworzyć procedurę obsługi zdarzeń dla zdarzenia kliknięcia i otworzyć formularz w edytorze kodu.

2. Zastąp `InsertButton_Click` procedurę obsługi zdarzeń następującym kodem:

     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Aby dodać kod w celu zaktualizowania rekordów w bazie danych

1. Kliknij dwukrotnie **UpdateButton** , aby utworzyć procedurę obsługi zdarzeń dla zdarzenia kliknięcia i otworzyć formularz w edytorze kodu.

2. Zastąp `UpdateButton_Click` procedurę obsługi zdarzeń następującym kodem:

     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Aby dodać kod do usuwania rekordów z bazy danych

1. Wybierz pozycję **DeleteButton** , aby utworzyć procedurę obsługi zdarzeń dla zdarzenia kliknięcia i otworzyć formularz w edytorze kodu.

2. Zastąp `DeleteButton_Click` procedurę obsługi zdarzeń następującym kodem:

     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

- Wybierz klawisz **F5** , aby uruchomić aplikację.

- Wybierz przycisk **Wstaw** i sprawdź, czy nowy rekord pojawia się w siatce.

- Wybierz przycisk **Aktualizuj** i sprawdź, czy rekord został zaktualizowany w siatce.

- Wybierz przycisk **Usuń** i sprawdź, czy rekord został usunięty z siatki.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza powiązanego z danymi. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

- Dodawanie funkcji wyszukiwania do formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zapytania parametrycznego do aplikacji Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Dodając dodatkowe tabele do zestawu danych, wybierając pozycję **Konfiguruj zestaw danych z kreatorem** w oknie **źródła danych** . Można dodać kontrolki, które wyświetlają powiązane dane, przeciągając powiązane węzły do formularza.

## <a name="see-also"></a>Zobacz też
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
