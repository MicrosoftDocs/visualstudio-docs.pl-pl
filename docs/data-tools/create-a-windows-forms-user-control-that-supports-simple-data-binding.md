---
title: Tworzenie kontrolki użytkownika obsługującej proste powiązanie danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d1584f0d6a772a6f24578f9693832fb6b0812444
ms.sourcegitcommit: 3cc73e74921a9ceb622542e0e263abeebc455c00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624492"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującej proste powiązanie danych

Podczas wyświetlania danych w formularzach w aplikacjach Windows, można wybrać istniejące kontrolki z **przybornika**, lub możesz tworzyć niestandardowe formanty, jeśli aplikacja wymaga funkcji, która nie jest dostępna w standardowych kontrolek. W tym instruktażu pokazano, jak utworzyć formant, który implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Określa, które implementują <xref:System.ComponentModel.DefaultBindingPropertyAttribute> może zawierać jedną właściwość, która może być powiązana z danymi. Te kontrolki są podobne do <xref:System.Windows.Forms.TextBox> lub <xref:System.Windows.Forms.CheckBox>.

Aby uzyskać więcej informacji na temat tworzenia formantu, zobacz [tworzenia kontrolek Windows Forms w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Podczas tworzenia kontrolki do użycia w scenariuszach wiązania danych, powinny implementować jeden z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
| - |
|Implementowanie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na proste formanty, takie jak <xref:System.Windows.Forms.TextBox>, który pojedynczej kolumny (lub wyświetlić właściwości) danych. (Ten proces jest opisany na tej stronie wskazówki).|
|Implementowanie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.DataGridView>, wyświetlanie listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.ComboBox>, który wyświetla listy lub tabele danych, ale również są potrzebne do pojedynczej kolumny lub właściwości. Aby uzyskać więcej informacji, zobacz [utworzyć formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Ten przewodnik tworzy prosty formant, który wyświetla dane z jednej kolumny w tabeli. W tym przykładzie użyto `Phone` kolumny `Customers` tabeli w bazie danych Northwind. Proste kontrolki Wyświetla numery telefonów klientów w standardowym formacie numeru telefonu, przy użyciu <xref:System.Windows.Forms.MaskedTextBox> i ustawienie maski numeru telefonu.

Z tego instruktażu dowiesz się jak:

- Utwórz nową **aplikacja interfejsu Windows Forms**.

- Dodaj nową **kontrolki użytkownika** do projektu.

- Wizualnie projektować kontrolkę użytkownika.

- Implementowanie `DefaultBindingProperty` atrybutu.

- Tworzenie zestawu danych za pomocą **konfiguracji źródła danych** kreatora.

- Ustaw **Phone** kolumny w **źródeł danych** okno, aby użyć nowego formantu.

- Utwórz formularz do wyświetlania danych w nowej kontrolki.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w **Instalatora programu Visual Studio**.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Pierwszym krokiem jest utworzenie **aplikacja interfejsu Windows Forms**:

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **SimpleControlWalkthrough**, a następnie wybierz **OK**.

     **SimpleControlWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu

Ten przewodnik tworzy po prostego formantu powiązać dane z **kontrolki użytkownika**. Dodaj **kontrolki użytkownika** elementu do **SimpleControlWalkthrough** projektu:

1. Z **projektu** menu, wybierz **Dodaj kontrolkę użytkownika**.

2. Typ **PhoneNumberBox** w obszarze nazw, a następnie kliknij przycisk **Dodaj**.

     **PhoneNumberBox** formant jest dodawany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.

## <a name="design-the-phonenumberbox-control"></a>Projektowanie kontrolki PhoneNumberBox

W tym przewodniku rozszerza istniejący <xref:System.Windows.Forms.MaskedTextBox> utworzyć **PhoneNumberBox** sterowania:

1. Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

2. Wybierz tag inteligentny <xref:System.Windows.Forms.MaskedTextBox> możesz po prostu przeciągnąć i wybierz polecenie **ustawić maskę**.

3. Wybierz **numer telefonu** w **maska wprowadzania** okno dialogowe, a następnie kliknij przycisk **OK** ustalenie maski.

## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych

Implementowanie prostego formantów tego wiązania danych pomocy technicznej, <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1. Przełącznik **PhoneNumberBox** formantu do widoku kodu. (Na **widoku** menu, wybierz **kodu**.)

2. Zastąp kod w **PhoneNumberBox** następującym kodem:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych

Ten krok używa **konfiguracji źródła danych** kreatora w celu utworzenia źródła danych na podstawie `Customers` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [jak: Zainstalować przykładowe bazy danych](../data-tools/installing-database-systems-tools-and-samples.md).

1. Aby otworzyć **źródeł danych** okna na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

2. W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **konfiguracji źródła danych** kreatora.

3. Na **wybierz typ źródła danych** wybierz opcję **bazy danych**, a następnie kliknij przycisk **dalej**.

4. Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6. Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.

7. Na **wybierz obiekty bazy danych** rozwiń **tabel** węzła.

8. Wybierz `Customers` tabeli, a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu, a `Customers` tabela zostanie wyświetlona w **źródeł danych** okna.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Należy ustawić kolumny telefonu, aby użyć kontrolki PhoneNumberBox

W ramach **źródeł danych** okna, można ustawić formant aby je utworzyć przed przeciąganie elementów na formularzu:

1. Otwórz **Form1** w projektancie.

2. Rozwiń **klientów** w węźle **źródeł danych** okna.

3. Kliknij strzałkę listy rozwijanej **klientów** węzeł i wybierz polecenie **szczegóły** na liście kontrolek.

4. Kliknij strzałkę listy rozwijanej **Phone** kolumny i wybierz polecenie **Dostosuj**.

5. Wybierz **PhoneNumberBox** z listy **skojarzonych formantów** w **opcje dostosowywania interfejsu użytkownika danych** okno dialogowe.

6. Kliknij strzałkę listy rozwijanej **Phone** kolumny, a wybierz **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Dodawanie formantów do formularza

Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna na formularzu.

Do tworzenia formantów powiązanych z danymi w formularzu, przeciągnij główny **klientów** węzła z **źródeł danych** okna do formularza i upewnij się, że **PhoneNumberBox** formant jest używany do wyświetlania danych w **Phone** kolumny.

Formanty powiązane z danymi z etykietami opisowymi są wyświetlane w formularzu, oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.

## <a name="run-the-application"></a>Uruchamianie aplikacji

Naciśnij klawisz **F5** do uruchomienia aplikacji.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzenie kontrolki, która obsługuje powiązanie danych. Niektóre typowe następne kroki obejmują:

- Wprowadzenie do Kontrolki niestandardowe w bibliotece kontrolki, więc można go używać w innych aplikacjach.

- Tworzenie formantów, które obsługują bardziej złożonych scenariuszy powiązanie danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) i [utworzyć formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)