---
title: W powiązaniu danych - kontrolek formularzy Windows Forms przy użyciu tabel odnośników | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 770564291870095e55dcc3de2fdb555aaebf6a2b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914610"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Utwórz formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania

Podczas wyświetlania danych w formularzach Windows Forms, można wybrać istniejące kontrolki z **przybornika**, lub możesz tworzyć niestandardowe formanty, jeśli aplikacja wymaga funkcji, które nie są dostępne w standardowych kontrolek. W tym instruktażu pokazano, jak utworzyć formant, który implementuje <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Określa, które implementują <xref:System.ComponentModel.LookupBindingPropertiesAttribute> może zawierać trzy właściwości, które mogą być powiązane z danymi. Te kontrolki są podobne do <xref:System.Windows.Forms.ComboBox>.

Aby uzyskać więcej informacji na temat tworzenia formantu, zobacz [kontrolek tworzenia formularzy Windows w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Użycie opcji tworzenia kontrolki w scenariuszach wiązania danych, musisz wdrożyć jedną z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
| - |
|Implementowanie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na proste formanty, takie jak <xref:System.Windows.Forms.TextBox>, który pojedynczej kolumny (lub wyświetlić właściwości) danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementowanie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.DataGridView>, wyświetlanie listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.ComboBox>, wyświetlanie listy lub tabele danych, ale również są potrzebne do pojedynczej kolumny lub właściwości. (Ten proces jest opisany na tej stronie wskazówki).|

Ten przewodnik tworzy kontrolkę wyszukiwania odnośników, który powiąże dane z dwóch tabel. W tym przykładzie użyto `Customers` i `Orders` tabel z przykładowej bazy danych Northwind. Kontrolka wyszukiwania jest powiązana z `CustomerID` pola z `Orders` tabeli. Używa tej wartości w celu wyszukania `CompanyName` z `Customers` tabeli.

Z tego instruktażu dowiesz się, jak:

-   Utwórz nową **aplikacja interfejsu Windows Forms**.

-   Dodaj nową **kontrolki użytkownika** do projektu.

-   Wizualnie projektować kontrolkę użytkownika.

-   Implementowanie `LookupBindingProperty` atrybutu.

-   Tworzenie zestawu danych za pomocą **konfiguracji źródła danych** kreatora.

-   Ustaw **CustomerID** kolumny na **zamówienia** tabeli w **źródeł danych** okna, aby użyć nowego formantu.

-   Utwórz formularz do wyświetlania danych w nowej kontrolki.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-a-windows-forms-app-project"></a>Tworzenie projektu aplikacji Windows Forms

Pierwszym krokiem jest utworzenie **aplikacja interfejsu Windows Forms** projektu.

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **LookupControlWalkthrough**, a następnie wybierz **OK**.

     **LookupControlWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu

Ten poradnik tworzy kontrolkę wyszukiwania odnośników z **kontrolki użytkownika**, więc Dodaj **kontrolki użytkownika** elementu do **LookupControlWalkthrough** projektu.

1.  Z **projektu** menu, wybierz opcję **Dodaj kontrolkę użytkownika**.

2.  Typ `LookupBox` w **nazwa** obszaru, a następnie kliknij **Dodaj**.

     **LookupBox** formant jest dodawany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.

## <a name="design-the-lookupbox-control"></a>Projektowanie kontrolki LookupBox

Aby projektować kontrolkę LookupBox, przeciągnij <xref:System.Windows.Forms.ComboBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych

Wyszukiwanie formantów to powiązanie danych pomocy technicznej, można zaimplementować <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1.  Przełącznik **LookupBox** formantu do widoku kodu. (Na **widoku** menu, wybierz **kodu**.)

2.  Zastąp kod w `LookupBox` następującym kodem:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych

Spowoduje to utworzenie źródła danych przy użyciu **konfiguracji źródła danych** kreatora, na podstawie `Customers` i `Orders` tabel w bazie danych Northwind.

1.  Aby otworzyć **źródeł danych** okna na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **konfiguracji źródła danych** kreatora.

3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.

4.  Na **wybierz połączenie danych** wykonaj strony, jedną z następujących czynności:

    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    -   Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.

5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6.  Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.

7.  Na **wybierz obiekty bazy danych** rozwiń **tabel** węzła.

8.  Wybierz `Customers` i `Orders` tabel, a następnie kliknij **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu, a `Customers` i `Orders` tabele są wyświetlane w **źródeł danych** okna.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Ustaw w kolumnie CustomerID w tabeli zamówienia, aby użyć kontrolki LookupBox

W ramach **źródeł danych** okna, można ustawić formant aby je utworzyć przed przeciąganie elementów do formularza.

1.  Otwórz **Form1** w projektancie.

2.  Rozwiń **klientów** w węźle **źródeł danych** okna.

3.  Rozwiń **zamówienia** węzeł (w **klientów** poniżej węzła **faks** kolumny).

4.  Kliknij strzałkę listy rozwijanej **zamówienia** węzeł i wybierz polecenie **szczegóły** na liście kontrolek.

5.  Kliknij strzałkę listy rozwijanej **CustomerID** kolumny (w **zamówienia** węzła) i wybierz polecenie **Dostosuj**.

6.  Wybierz **LookupBox** z listy **skojarzonych formantów** w **opcje dostosowywania interfejsu użytkownika danych** okno dialogowe.

7.  Kliknij przycisk **OK**.

8.  Kliknij strzałkę listy rozwijanej **CustomerID** kolumny, a wybierz **LookupBox**.

## <a name="add-controls-to-the-form"></a>Dodawanie formantów do formularza

Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna na **Form1**.

Aby utworzyć formanty powiązane z danymi w formularzu Windows, przeciągnij **zamówienia** węzła z **źródeł danych** okna na formularzu Windows i sprawdź, czy **LookupBox** formant jest używany do wyświetlania danych w `CustomerID` kolumny.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Powiąż formant aby wyszukać CompanyName z tabeli Customers

Aby skonfigurować powiązania wyszukiwania odnośników, wybierz główny **klientów** w węźle **źródeł danych** okna, a następnie przeciągnij pole na kombi w **CustomerIDLookupBox** na **Form1**.

Spowoduje to utworzenie powiązania danych do wyświetlenia `CompanyName` z `Customers` tabeli przy zachowaniu `CustomerID` wartość z `Orders` tabeli.

## <a name="run-the-application"></a>Uruchamianie aplikacji

-   Naciśnij klawisz **F5** do uruchomienia aplikacji.

-   Nawigowanie po niektóre rekordy i upewnij się, że `CompanyName` pojawia się w `LookupBox` kontroli.

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)