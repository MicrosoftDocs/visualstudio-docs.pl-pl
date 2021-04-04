---
title: Tworzenie kontrolek użytkownika, które obsługują proste powiązanie danych
description: Dowiedz się, jak utworzyć formant użytkownika Windows Forms obsługujący proste powiązanie danych przy użyciu klasy DefaultBindingPropertyAttribute w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 7f26de2f26a132fc210920d94742ec7883612d66
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216309"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującej proste powiązanie danych

Podczas wyświetlania danych w formularzach w aplikacjach systemu Windows można wybrać istniejące kontrolki z **przybornika** lub można utworzyć niestandardowe kontrolki, jeśli aplikacja wymaga funkcjonalności, która nie jest dostępna w kontrolkach standardowych. W tym instruktażu pokazano, jak utworzyć kontrolkę implementującą <xref:System.ComponentModel.DefaultBindingPropertyAttribute> . Kontrolki implementujące <xref:System.ComponentModel.DefaultBindingPropertyAttribute> może zawierać jedną właściwość, która może być powiązana z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.TextBox> lub <xref:System.Windows.Forms.CheckBox> .

Aby uzyskać więcej informacji na temat tworzenia kontroli, zobacz [Opracowywanie formantów Windows Forms w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Podczas tworzenia formantów do użycia w scenariuszach powiązań danych należy zaimplementować jeden z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
| - |
|Zaimplementuj <xref:System.ComponentModel.DefaultBindingPropertyAttribute> proste kontrolki, takie jak <xref:System.Windows.Forms.TextBox> , które wyświetlają pojedynczą kolumnę (lub właściwość) danych. (Ten proces został opisany na stronie przewodnika).|
|Zaimplementuj <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolki on, na przykład <xref:System.Windows.Forms.DataGridView> , które wyświetlają listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Zaimplementuj <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolki on, na przykład <xref:System.Windows.Forms.ComboBox> , które wyświetla listę (lub tabele) danych, ale również muszą przedstawić pojedynczą kolumnę lub właściwość. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Ten Instruktaż tworzy prostą kontrolkę, która wyświetla dane z pojedynczej kolumny w tabeli. Ten przykład używa `Phone` kolumny `Customers` tabeli z przykładowej bazy danych Northwind. Prosta kontrolka użytkownika wyświetla numery telefonów klientów w standardowym formacie numeru telefonu przy użyciu <xref:System.Windows.Forms.MaskedTextBox> i ustawia maskę na numer telefonu.

W tym instruktażu dowiesz się, jak:

- Utwórz nową **aplikację Windows Forms**.

- Dodaj nową **kontrolkę użytkownika** do projektu.

- Wizualne projektowanie kontrolki użytkownika.

- Zaimplementuj `DefaultBindingProperty` atrybut.

- Utwórz zestaw danych za pomocą kreatora **konfiguracji źródła danych** .

- Ustaw kolumnę **telefon** w oknie **źródła danych** , aby użyć nowej kontrolki.

- Utwórz formularz, aby wyświetlić dane w nowej kontrolce.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio** można zainstalować SQL Server Express LocalDB jako część obciążenia **magazynu danych i przetwarzania** lub jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w **Instalator programu Visual Studio**). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**:

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **SimpleControlWalkthrough**, a następnie wybierz przycisk **OK**.

     Projekt **SimpleControlWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodawanie kontrolki użytkownika do projektu

Ten Instruktaż tworzy prostą kontrolkę z powiązaniem danych z **kontrolki użytkownika**. Dodaj element **kontrolki użytkownika** do projektu **SimpleControlWalkthrough** :

1. W menu **projekt** wybierz polecenie **Dodaj kontrolkę użytkownika**.

2. Wpisz **PhoneNumberBox** w obszarze Nazwa, a następnie kliknij przycisk **Dodaj**.

     Formant **PhoneNumberBox** zostanie dodany do **Eksplorator rozwiązań** i otwarty w projektancie.

## <a name="design-the-phonenumberbox-control"></a>Zaprojektuj formant PhoneNumberBox

Ten przewodnik rozszerza się na istniejący, <xref:System.Windows.Forms.MaskedTextBox> Aby utworzyć formant **PhoneNumberBox** :

1. Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

2. Wybierz tag inteligentny po <xref:System.Windows.Forms.MaskedTextBox> przeciągnięciu, a następnie wybierz pozycję **Ustaw maskę**.

3. W oknie dialogowym **maska wejścia** wybierz pozycję **numer telefonu** , a następnie kliknij przycisk **OK** , aby ustawić maskę.

## <a name="add-the-required-data-binding-attribute"></a>Dodawanie wymaganego atrybutu powiązania danych

W przypadku prostych formantów, które obsługują wiązania z danymi, zaimplementuj <xref:System.ComponentModel.DefaultBindingPropertyAttribute> :

1. Przełącz formant **PhoneNumberBox** do widoku kodu. (W menu **Widok** wybierz polecenie **kod**).

2. Zastąp kod w **PhoneNumberBox** następującym:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb" id="Snippet3":::

3. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Tworzenie źródła danych na podstawie bazy danych

Ten krok powoduje użycie kreatora **konfiguracji źródła danych** w celu utworzenia źródła danych na podstawie `Customers` tabeli w przykładowej bazie danych Northwind. Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [How to: Install Sample Bases](../data-tools/installing-database-systems-tools-and-samples.md).

1. Aby otworzyć okno **źródła danych** , w menu **dane** kliknij polecenie **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić kreatora **konfiguracji źródła danych** .

3. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz `Customers` tabelę, a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a `Customers` tabela pojawia się w oknie **źródła danych** .

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Ustaw kolumnę telefon, aby użyć kontrolki PhoneNumberBox

W oknie **źródła danych** można ustawić kontrolkę, która ma zostać utworzona przed przeciągnięciem elementów na formularz:

1. Otwórz **formularz Form1** w projektancie.

2. W oknie **źródła danych** rozwiń węzeł **Customers** .

3. Kliknij strzałkę listy rozwijanej w węźle **klienci** , a następnie wybierz **szczegóły** z listy kontrolek.

4. Kliknij strzałkę listy rozwijanej w kolumnie **telefon** , a następnie wybierz pozycję **Dostosuj**.

5. Wybierz **PhoneNumberBox** z listy **skojarzonych kontrolek** w oknie dialogowym **Opcje dostosowywania interfejsu użytkownika danych** .

6. Kliknij strzałkę listy rozwijanej w kolumnie **telefon** , a następnie wybierz pozycję **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Dodawanie kontrolek do formularza

Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

Aby utworzyć formanty powiązane z danymi w formularzu, przeciągnij główny węzeł **klienci** z okna **źródła danych** na formularz i sprawdź, czy kontrolka **PhoneNumberBox** jest używana do wyświetlania danych w kolumnie **telefon** .

Formanty powiązane z danymi, które mają opisowe etykiety, są wyświetlane w formularzu wraz z paskiem narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) na potrzeby nawigowania po rekordach. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

## <a name="run-the-application"></a>Uruchamianie aplikacji

Naciśnij klawisz **F5** , aby uruchomić aplikację.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu kontrolki, która obsługuje powiązanie danych. Oto kilka typowych kroków, które obejmują:

- Umieszczenie niestandardowych kontrolek w bibliotece kontrolek, aby można było użyć ich ponownie w innych aplikacjach.

- Tworzenie formantów, które obsługują bardziej złożone scenariusze powiązań danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms obsługującej złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) i [Tworzenie Windows Forms kontrolki użytkownika, która obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
