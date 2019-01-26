---
title: Utwórz formant użytkownika interfejsu Windows Forms przy użyciu powiązania danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 8e8a78db0d63edc90cbeb36120cc457edd74d25b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001320"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych

Podczas wyświetlania danych w formularzach w aplikacjach Windows, można wybrać istniejące kontrolki z **przybornika**, lub możesz tworzyć niestandardowe formanty, jeśli aplikacja wymaga funkcji, która nie jest dostępna w standardowych kontrolek. W tym instruktażu pokazano, jak utworzyć formant, który implementuje <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Określa, które implementują <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> zawierają `DataSource` i `DataMember` właściwość, która może być powiązana z danymi. Te kontrolki są podobne do <xref:System.Windows.Forms.DataGridView> lub <xref:System.Windows.Forms.ListBox>.

Aby uzyskać więcej informacji na temat tworzenia formantu, zobacz [kontrolek tworzenia formularzy Windows w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Podczas tworzenia kontrolki do użycia w scenariuszach powiązanie danych należy implementować jeden z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
| - |
|Implementowanie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na proste formanty, takie jak <xref:System.Windows.Forms.TextBox>, który pojedynczej kolumny (lub wyświetlić właściwości) danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementowanie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.DataGridView>, wyświetlanie listy (lub tabele) danych. (Ten proces jest opisany na tej stronie wskazówki).|
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.ComboBox>, który wyświetla listy lub tabele danych, ale również są potrzebne do pojedynczej kolumny lub właściwości. Aby uzyskać więcej informacji, zobacz [utworzyć formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Ten przewodnik tworzy formant złożony, który wyświetla wiersze danych z tabeli. W tym przykładzie użyto `Customers` tabeli w bazie danych Northwind. Kontrolka złożona użytkownika będzie wyświetlać tabelę Klienci w <xref:System.Windows.Forms.DataGridView> w formancie niestandardowym.

Z tego instruktażu dowiesz się jak:

- Utwórz nową **aplikacja interfejsu Windows Forms**.

- Dodaj nową **kontrolki użytkownika** do projektu.

- Wizualnie projektować kontrolkę użytkownika.

- Implementowanie `ComplexBindingProperty` atrybutu.

- Tworzenie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

- Ustaw **klientów** tabelę [okna źródeł danych](add-new-data-sources.md#data-sources-window) używać nowego formantu złożonego.

- Dodawanie nowej kontrolki, przeciągając go z **źródeł danych** okna na **Form1**.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

1. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    1. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    1. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Pierwszym krokiem jest utworzenie **aplikacja interfejsu Windows Forms**:

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

1. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

1. W środkowym okienku wybierz **Windows Forms App** typ projektu.

1. Nadaj projektowi nazwę **ComplexControlWalkthrough**, a następnie wybierz **OK**.

    **ComplexControlWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu

Ponieważ ten przewodnik tworzy po złożone kontrolki możliwej do wiązania danych — od **kontrolki użytkownika**, Dodaj **kontrolki użytkownika** do projektu:

1. Z **projektu** menu, wybierz **Dodaj kontrolkę użytkownika**.

1. Typ **ComplexDataGridView** w **nazwa** obszaru, a następnie kliknij **Dodaj**.

    **ComplexDataGridView** formant jest dodawany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.

## <a name="design-the-complexdatagridview-control"></a>Projektowanie kontrolki ComplexDataGridView

Aby dodać <xref:System.Windows.Forms.DataGridView> do formantu użytkownika przeciągnij <xref:System.Windows.Forms.DataGridView> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych

Złożone formantów to powiązanie danych pomocy technicznej, można zaimplementować <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Przełącznik **ComplexDataGridView** formantu do widoku kodu. (Na **widoku** menu, wybierz opcję **kodu**.)

1. Zastąp kod w `ComplexDataGridView` następującym kodem:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych

Użyj **konfiguracji źródła danych** kreatora w celu utworzenia źródła danych na podstawie `Customers` tabeli w bazie danych Northwind:

1.  Aby otworzyć **źródeł danych** okna na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **konfiguracji źródła danych** kreatora.

3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.

4.  Na **wybierz połączenie danych** wykonaj strony, jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.

5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6.  Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.

7.  Na **wybierz obiekty bazy danych** rozwiń **tabel** węzła.

8.  Wybierz `Customers` tabeli, a następnie kliknij przycisk **Zakończ**.

    **NorthwindDataSet** zostanie dodany do projektu, a `Customers` tabela zostanie wyświetlona w **źródeł danych** okna.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Ustawianie tabeli Customers, aby użyć kontrolki ComplexDataGridView

W ramach **źródeł danych** okna, można ustawić formant aby je utworzyć przed przeciąganie elementów na formularzu:

1. Otwórz **Form1** w projektancie.

1. Rozwiń **klientów** w węźle **źródeł danych** okna.

1. Kliknij strzałkę listy rozwijanej **klientów** węzeł i wybierz polecenie **Dostosuj**.

1. Wybierz **ComplexDataGridView** z listy **skojarzonych formantów** w **opcje dostosowywania interfejsu użytkownika danych** okno dialogowe.

1. Kliknij strzałkę listy rozwijanej `Customers` tabeli, a następnie wybierz **ComplexDataGridView** na liście kontrolek.

## <a name="add-controls-to-the-form"></a>Dodawanie formantów do formularza

Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza. Przeciągnij główny **klientów** węzła z **źródeł danych** okna na formularzu. Upewnij się, że **ComplexDataGridView** formant jest używany do wyświetlania danych w tabeli.

## <a name="run-the-application"></a>Uruchamianie aplikacji

Naciśnij klawisz **F5** do uruchomienia aplikacji.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzenie kontrolki, która obsługuje powiązanie danych. Niektóre typowe następne kroki obejmują:

- Wprowadzenie do Kontrolki niestandardowe w bibliotece kontrolki, więc można go używać w innych aplikacjach.

- Tworzenie formantów, które obsługują scenariusze wyszukiwania. Aby uzyskać więcej informacji, zobacz [utworzyć formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Kontrolki formularzy Windows Forms](/dotnet/framework/winforms/controls/index)