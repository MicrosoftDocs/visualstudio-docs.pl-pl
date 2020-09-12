---
title: Używanie tabel odnośników w powiązaniu danych — Windows Forms
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fe2289a54dba0c3b3e34de54991e9b7cfbee4c93
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037396"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującej powiązanie danych wyszukiwania

Gdy dane są wyświetlane na Windows Forms, można wybrać istniejące kontrolki z **przybornika**lub można utworzyć niestandardowe kontrolki, jeśli aplikacja wymaga funkcjonalności niedostępnej w standardowych kontrolkach. W tym instruktażu pokazano, jak utworzyć kontrolkę implementującą <xref:System.ComponentModel.LookupBindingPropertiesAttribute> . Kontrolki implementujące interfejs <xref:System.ComponentModel.LookupBindingPropertiesAttribute> mogą zawierać trzy właściwości, które można powiązać z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.ComboBox> .

Aby uzyskać więcej informacji na temat tworzenia kontroli, zobacz [Opracowywanie formantów Windows Forms w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Podczas tworzenia formantów do użycia w scenariuszach powiązań danych należy zaimplementować jeden z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
| - |
|Zaimplementuj <xref:System.ComponentModel.DefaultBindingPropertyAttribute> proste kontrolki, takie jak <xref:System.Windows.Forms.TextBox> , które wyświetlają pojedynczą kolumnę (lub właściwość) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Zaimplementuj <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolki on, na przykład <xref:System.Windows.Forms.DataGridView> , które wyświetlają listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Zaimplementuj <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolki na, takie jak <xref:System.Windows.Forms.ComboBox> ,, które wyświetlają listy (lub tabele) danych, ale muszą również przedstawić pojedynczą kolumnę lub właściwość. (Ten proces został opisany na stronie przewodnika).|

Ten Instruktaż tworzy formant wyszukiwania, który wiąże się z danymi z dwóch tabel. Ten przykład używa `Customers` tabel i `Orders` z przykładowej bazy danych Northwind. Formant wyszukiwania jest powiązany z `CustomerID` polem z `Orders` tabeli. Używa tej wartości do wyszukania `CompanyName` z `Customers` tabeli.

W tym instruktażu dowiesz się, jak:

- Utwórz nową **aplikację Windows Forms**.

- Dodaj nową **kontrolkę użytkownika** do projektu.

- Wizualne projektowanie kontrolki użytkownika.

- Zaimplementuj `LookupBindingProperty` atrybut.

- Utwórz zestaw danych za pomocą kreatora **konfiguracji źródła danych** .

- Ustaw kolumnę **CustomerID** w tabeli **Orders** w oknie **źródła danych** , aby użyć nowej kontrolki.

- Utwórz formularz, aby wyświetlić dane w nowej kontrolce.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio**można zainstalować SQL Server Express LocalDB jako część obciążenia **magazynu danych i przetwarzania** lub jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-a-windows-forms-app-project"></a>Tworzenie projektu aplikacji Windows Forms

Pierwszym krokiem jest utworzenie projektu **aplikacji Windows Forms** .

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **LookupControlWalkthrough**, a następnie wybierz przycisk **OK**.

     Projekt **LookupControlWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodawanie kontrolki użytkownika do projektu

W tym instruktażu tworzony jest formant wyszukiwania z **kontrolki użytkownika**, więc Dodaj element **kontrolki użytkownika** do projektu **LookupControlWalkthrough** .

1. W menu **projekt** wybierz polecenie **Dodaj kontrolkę użytkownika**.

2. Wpisz `LookupBox` w obszarze **Nazwa** , a następnie kliknij przycisk **Dodaj**.

     Formant **LookupBox** zostanie dodany do **Eksplorator rozwiązań**i otwarty w projektancie.

## <a name="design-the-lookupbox-control"></a>Zaprojektuj formant LookupBox

Aby zaprojektować formant LookupBox, przeciągnij <xref:System.Windows.Forms.ComboBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

## <a name="add-the-required-data-binding-attribute"></a>Dodawanie wymaganego atrybutu powiązania danych

W przypadku formantów wyszukiwania, które obsługują powiązanie danych, można zaimplementować <xref:System.ComponentModel.LookupBindingPropertiesAttribute> .

1. Przełącz formant **LookupBox** do widoku kodu. (W menu **Widok** wybierz polecenie **kod**).

2. Zastąp kod w `LookupBox` następującej postaci:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Tworzenie źródła danych na podstawie bazy danych

Ten krok polega na utworzeniu źródła danych przy użyciu kreatora **konfiguracji źródła danych** na podstawie `Customers` tabel i `Orders` w przykładowej bazie danych Northwind.

1. Aby otworzyć okno **źródła danych** , w menu **dane** kliknij polecenie **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić kreatora **konfiguracji źródła danych** .

3. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz `Customers` tabele i `Orders` , a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a `Customers` `Orders` tabele i są wyświetlane w oknie **źródła danych** .

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Ustaw kolumnę CustomerID tabeli Orders, aby używać kontrolki LookupBox

W oknie **źródła danych** można ustawić kontrolkę, która ma zostać utworzona przed przeciągnięciem elementów na formularz.

1. Otwórz **formularz Form1** w projektancie.

2. W oknie **źródła danych** rozwiń węzeł **Customers** .

3. Rozwiń węzeł **zamówienia** (jeden w węźle **klienci** poniżej kolumny **faks** ).

4. Kliknij strzałkę listy rozwijanej w węźle **zamówienia** , a następnie wybierz **szczegóły** z listy kontrolek.

5. Kliknij strzałkę listy rozwijanej w kolumnie **IDKlienta** (w węźle **zamówienia** ), a następnie wybierz pozycję **Dostosuj**.

6. Wybierz **LookupBox** z listy **skojarzonych kontrolek** w oknie dialogowym **Opcje dostosowywania interfejsu użytkownika danych** .

7. Kliknij pozycję **OK**.

8. Kliknij strzałkę listy rozwijanej w kolumnie **IDKlienta** i wybierz pozycję **LookupBox**.

## <a name="add-controls-to-the-form"></a>Dodawanie kontrolek do formularza

Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na **formularz Form1**.

Aby utworzyć formanty powiązane z danymi w formularzu systemu Windows, przeciągnij węzeł **zamówienia** z okna **źródła danych** na formularz systemu Windows i sprawdź, czy kontrolka **LookupBox** jest używana do wyświetlania danych w `CustomerID` kolumnie.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Powiąż formant, aby wyszukać NazwaFirmy z tabeli Customers

Aby skonfigurować powiązania wyszukiwania, wybierz węzeł główni **klienci** w oknie **źródła danych** , a następnie przeciągnij go do pola kombi w **CustomerIDLookupBox** na **formularzu Form1**.

Spowoduje to skonfigurowanie powiązania danych w celu wyświetlenia `CompanyName` z `Customers` tabeli, przy zachowaniu `CustomerID` wartości z `Orders` tabeli.

## <a name="run-the-application"></a>Uruchamianie aplikacji

- Naciśnij klawisz **F5** , aby uruchomić aplikację.

- Nawiguj po kilku rekordach i sprawdź, czy `CompanyName` pojawia się w `LookupBox` kontrolce.

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
