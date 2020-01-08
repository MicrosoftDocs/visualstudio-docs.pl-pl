---
title: Tworzenie kontrolki użytkownika Windows Forms z powiązaniem danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 97d9e64a0fcabb207d4606d4819f6afcb61b1043
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586851"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującej złożone powiązanie danych

Podczas wyświetlania danych w formularzach w aplikacjach systemu Windows można wybrać istniejące kontrolki z **przybornika**. Można też tworzyć niestandardowe kontrolki, jeśli aplikacja wymaga funkcjonalności, która nie jest dostępna w kontrolkach standardowych. W tym instruktażu pokazano, jak utworzyć kontrolkę implementującą <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Kontrolki implementujące <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> zawierają Właściwość `DataSource` i `DataMember`, która może być powiązana z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.DataGridView> lub <xref:System.Windows.Forms.ListBox>.

Aby uzyskać więcej informacji na temat tworzenia kontroli, zobacz [Opracowywanie formantów Windows Forms w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Podczas tworzenia formantów do użycia w scenariuszach powiązania danych należy zaimplementować jeden z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
| - |
|Zaimplementuj <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na prostych kontrolkach, takich jak <xref:System.Windows.Forms.TextBox>, które wyświetlają pojedynczą kolumnę (lub właściwość) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Zaimplementuj <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na kontrolkach, takich jak <xref:System.Windows.Forms.DataGridView>, które wyświetlają listy (lub tabele) danych. (Ten proces został opisany na stronie przewodnika).|
|Zaimplementuj <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na kontrolkach, takich jak <xref:System.Windows.Forms.ComboBox>, które wyświetlają listy (lub tabele) danych, ale również muszą przedstawić pojedynczą kolumnę lub właściwość. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Ten Instruktaż tworzy złożony formant, który wyświetla wiersze danych z tabeli. Ten przykład używa tabeli `Customers` z przykładowej bazy danych Northwind. Złożona kontrolka użytkownika wyświetli tabelę Customers w <xref:System.Windows.Forms.DataGridView> w kontrolce niestandardową.

W tym instruktażu dowiesz się, jak:

- Dodaj nową **kontrolkę użytkownika** do projektu.

- Wizualne projektowanie kontrolki użytkownika.

- Zaimplementuj atrybut `ComplexBindingProperty`.

- Utwórz zestaw danych za pomocą [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

- W [oknie źródła danych](add-new-data-sources.md#data-sources-window) Ustaw tabelę **Customers** , aby użyć nowej kontrolki złożonej.

- Dodaj nową kontrolkę, przeciągając ją z okna **źródła danych** na **formularz Form1**.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio**można zainstalować SQL Server Express LocalDB jako część obciążenia **magazynu danych i przetwarzania** lub jako pojedynczy składnik.

1. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    1. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    1. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-a-windows-forms-app-project"></a>Tworzenie projektu aplikacji Windows Forms

Pierwszym krokiem jest utworzenie projektu **aplikacji Windows Forms** dla obu C# lub Visual Basic. Nazwij projekt **ComplexControlWalkthrough**.

## <a name="add-a-user-control-to-the-project"></a>Dodawanie kontrolki użytkownika do projektu

Ponieważ ten przewodnik tworzy złożoną kontrolkę z powiązaniem danych z **kontrolki użytkownika**, Dodaj element **kontrolki użytkownika** do projektu:

1. W menu **projekt** wybierz polecenie **Dodaj kontrolkę użytkownika**.

1. W obszarze **Nazwa** wpisz **ComplexDataGridView** , a następnie kliknij przycisk **Dodaj**.

    Formant **ComplexDataGridView** zostanie dodany do **Eksplorator rozwiązań**i otwarty w projektancie.

## <a name="design-the-complexdatagridview-control"></a>Zaprojektuj formant ComplexDataGridView

Aby dodać <xref:System.Windows.Forms.DataGridView> do kontrolki użytkownika, przeciągnij <xref:System.Windows.Forms.DataGridView> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

## <a name="add-the-required-data-binding-attribute"></a>Dodawanie wymaganego atrybutu powiązania danych

W przypadku złożonych formantów, które obsługują powiązanie danych, można zaimplementować <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Przełącz formant **ComplexDataGridView** do widoku kodu. (W menu **Widok** wybierz pozycję **kod**).

1. Zastąp kod w `ComplexDataGridView` następującym:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Tworzenie źródła danych na podstawie bazy danych

Użyj kreatora **konfiguracji źródła danych** , aby utworzyć źródło danych na podstawie tabeli `Customers` w przykładowej bazie danych Northwind:

1. Aby otworzyć okno **źródła danych** , w menu **dane** kliknij polecenie **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić kreatora **konfiguracji źródła danych** .

3. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

   - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

   - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz tabelę `Customers` a następnie kliknij przycisk **Zakończ**.

   **NorthwindDataSet** jest dodawany do projektu, a tabela `Customers` zostanie wyświetlona w oknie **źródła danych** .

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Ustaw tabelę Customers na używanie formantu ComplexDataGridView

W oknie **źródła danych** można ustawić kontrolkę, która ma zostać utworzona przed przeciągnięciem elementów na formularz:

1. Otwórz **formularz Form1** w projektancie.

1. W oknie **źródła danych** rozwiń węzeł **Customers** .

1. Kliknij strzałkę listy rozwijanej w węźle **klienci** , a następnie wybierz pozycję **Dostosuj**.

1. Wybierz **ComplexDataGridView** z listy **skojarzonych kontrolek** w oknie dialogowym **Opcje dostosowywania interfejsu użytkownika danych** .

1. Kliknij strzałkę listy rozwijanej w tabeli `Customers` i wybierz pozycję **ComplexDataGridView** z listy kontrolek.

## <a name="add-controls-to-the-form"></a>Dodawanie kontrolek do formularza

Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz. Przeciągnij główny węzeł **Customers** z okna **źródła danych** na formularz. Sprawdź, czy kontrolka **ComplexDataGridView** jest używana do wyświetlania danych tabeli.

## <a name="run-the-application"></a>Uruchamianie aplikacji

Naciśnij klawisz **F5**, aby uruchomić aplikację.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu kontrolki, która obsługuje powiązanie danych. Oto kilka typowych kroków, które obejmują:

- Umieszczenie niestandardowych kontrolek w bibliotece kontrolek, aby można było użyć ich ponownie w innych aplikacjach.

- Tworzenie kontrolek obsługujących scenariusze wyszukiwania. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Kontrolki formularzy Windows Forms](/dotnet/framework/winforms/controls/index)
