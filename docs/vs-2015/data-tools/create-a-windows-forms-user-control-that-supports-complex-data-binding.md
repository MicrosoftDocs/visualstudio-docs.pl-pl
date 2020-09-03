---
title: Tworzenie kontrolki użytkownika Windows Forms, która obsługuje złożone powiązanie danych | Microsoft Docs
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c4a20939ed2e3a036831930749bb59b5a42315
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670052"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującej złożone powiązanie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas wyświetlania danych w formularzach w aplikacjach systemu Windows można wybrać istniejące kontrolki z **przybornika**lub można utworzyć niestandardowe kontrolki, jeśli aplikacja wymaga funkcjonalności, która nie jest dostępna w kontrolkach standardowych. W tym instruktażu pokazano, jak utworzyć kontrolkę implementującą <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> . Kontrolki implementujące <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> Właściwość zawiera `DataSource` i `DataMember` , które mogą być powiązane z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.DataGridView> lub <xref:System.Windows.Forms.ListBox> .

 Aby uzyskać więcej informacji na temat tworzenia kontroli, zobacz [Opracowywanie formantów Windows Forms w czasie projektowania](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Podczas tworzenia formantów do użycia w scenariuszach powiązania danych należy zaimplementować jeden z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
|-----------------------------------|
|Zaimplementuj <xref:System.ComponentModel.DefaultBindingPropertyAttribute> proste kontrolki, takie jak <xref:System.Windows.Forms.TextBox> , które wyświetlają pojedynczą kolumnę (lub właściwość) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Zaimplementuj <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolki on, na przykład <xref:System.Windows.Forms.DataGridView> , które wyświetlają listy (lub tabele) danych. (Ten proces został opisany na stronie przewodnika).|
|Zaimplementuj <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolki on, na przykład <xref:System.Windows.Forms.ComboBox> , które wyświetla listę (lub tabele) danych, ale również muszą przedstawić pojedynczą kolumnę lub właściwość. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Ten Instruktaż tworzy złożony formant, który wyświetla wiersze danych z tabeli. W tym przykładzie zastosowano `Customers` tabelę z przykładowej bazy danych Northwind. Złożona kontrolka użytkownika wyświetli tabelę Customers w <xref:System.Windows.Forms.DataGridView> kontrolce niestandardowej.

 W tym instruktażu dowiesz się, jak:

- Utwórz nową **aplikację systemu Windows**.

- Dodaj nową **kontrolkę użytkownika** do projektu.

- Wizualne projektowanie kontrolki użytkownika.

- Zaimplementuj `ComplexBindingProperty` atrybut.

- Utwórz zestaw danych za pomocą [Kreatora konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- W [oknie źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) Ustaw tabelę **Customers** , aby użyć nowej kontrolki złożonej.

- Dodaj nową kontrolkę, przeciągając ją z **okna źródła danych** na **formularz Form1**.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind.

## <a name="create-a-windows-application"></a>Tworzenie aplikacji systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji systemu Windows**.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt systemu Windows

1. W programie Visual Studio w menu **plik** Utwórz nowy **projekt**.

2. Nazwij projekt **ComplexControlWalkthrough**.

3. Wybierz pozycję **aplikacja systemu Windows**, a następnie kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **ComplexControlWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodawanie kontrolki użytkownika do projektu
 Ponieważ ten przewodnik tworzy złożoną kontrolkę umożliwiającą powiązanie danych z **kontrolki użytkownika**, należy dodać element **kontrolki użytkownika** do projektu.

#### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu

1. W menu **projekt** wybierz polecenie **Dodaj kontrolkę użytkownika**.

2. W obszarze **Nazwa** wpisz **ComplexDataGridView** , a następnie kliknij przycisk **Dodaj**.

     Formant **ComplexDataGridView** zostanie dodany do **Eksplorator rozwiązań**i otwarty w projektancie.

## <a name="design-the-complexdatagridview-control"></a>Zaprojektuj formant ComplexDataGridView
 Ten krok powoduje dodanie <xref:System.Windows.Forms.DataGridView> do kontrolki użytkownika.

#### <a name="to-design-the-complexdatagridview-control"></a>Aby zaprojektować formant ComplexDataGridView

- Przeciągnij <xref:System.Windows.Forms.DataGridView> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

## <a name="add-the-required-data-binding-attribute"></a>Dodawanie wymaganego atrybutu powiązania danych
 W przypadku złożonych formantów, które obsługują powiązanie danych, można zaimplementować <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> .

#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Aby zaimplementować atrybut ComplexBindingProperties

1. Przełącz formant **ComplexDataGridView** do widoku kodu. (W menu **Widok** wybierz pozycję **kod**).

2. Zastąp kod w `ComplexDataGridView` następującej postaci:

     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]

3. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

## <a name="creating-a-data-source-from-your-database"></a>Tworzenie źródła danych z bazy danych
 Ten krok powoduje użycie kreatora **konfiguracji źródła danych** w celu utworzenia źródła danych na podstawie `Customers` tabeli w przykładowej bazie danych Northwind. Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [instalowanie SQL Server przykładowych baz danych](../data-tools/install-sql-server-sample-databases.md).

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić kreatora **konfiguracji źródła danych** .

3. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz `Customers` tabelę, a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a `Customers` tabela pojawia się w oknie **źródła danych** .

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Ustaw tabelę Customers na używanie formantu ComplexDataGridView
 W oknie **źródła danych** można ustawić kontrolkę, która ma zostać utworzona przed przeciągnięciem elementów na formularz.

#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Aby ustawić tabelę Customers na powiązanie z kontrolką ComplexDataGridView

1. Otwórz **formularz Form1** w projektancie.

2. W oknie **źródła danych** rozwiń węzeł **Customers** .

3. Kliknij strzałkę listy rozwijanej w węźle **klienci** , a następnie wybierz pozycję **Dostosuj**.

4. Wybierz **ComplexDataGridView** z listy **skojarzonych kontrolek** w oknie dialogowym **Opcje dostosowywania interfejsu użytkownika danych** .

5. Kliknij strzałkę listy rozwijanej w `Customers` tabeli, a następnie wybierz pozycję **ComplexDataGridView** z listy kontrolek.

## <a name="addcontrols-to-the-form"></a>Addcontrols do formularza
 Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć kontrolki powiązane z danymi w formularzu

- Przeciągnij główny węzeł **Customers** z okna **źródła danych** na formularz. Sprawdź, czy kontrolka **ComplexDataGridView** jest używana do wyświetlania danych tabeli.

## <a name="running-the-application"></a>Uruchamianie aplikacji

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

- Naciśnij klawisz F5, aby uruchomić aplikację.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu kontrolki, która obsługuje powiązanie danych. Oto kilka typowych kroków, które obejmują:

- Umieszczenie niestandardowych kontrolek w bibliotece kontrolek, aby można było użyć ich ponownie w innych aplikacjach.

- Tworzenie kontrolek obsługujących scenariusze wyszukiwania. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Zobacz też
 [Powiązywanie formantów Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [Ustaw kontrolkę, która ma zostać utworzona podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md) [Windows Forms formantów](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
