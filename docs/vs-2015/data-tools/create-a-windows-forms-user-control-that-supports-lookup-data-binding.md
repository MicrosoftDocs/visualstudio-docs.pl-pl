---
title: Tworzenie kontrolki użytkownika Windows Forms, która obsługuje powiązanie danych wyszukiwania | Microsoft Docs
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
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 48891f82667270f04af49c60122c63f8d3a943f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668776"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującej powiązanie danych wyszukiwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy dane są wyświetlane na Windows Forms, można wybrać istniejące kontrolki z **przybornika**lub można utworzyć niestandardowe kontrolki, jeśli aplikacja wymaga funkcjonalności niedostępnej w standardowych kontrolkach. W tym instruktażu pokazano, jak utworzyć kontrolkę implementującą <xref:System.ComponentModel.LookupBindingPropertiesAttribute> . Kontrolki implementujące interfejs <xref:System.ComponentModel.LookupBindingPropertiesAttribute> mogą zawierać trzy właściwości, które można powiązać z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.ComboBox> .

 Aby uzyskać więcej informacji na temat tworzenia kontroli, zobacz [Opracowywanie formantów Windows Forms w czasie projektowania](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Podczas tworzenia formantów do użycia w scenariuszach powiązania danych należy zaimplementować jeden z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
|-----------------------------------|
|Zaimplementuj <xref:System.ComponentModel.DefaultBindingPropertyAttribute> proste kontrolki, takie jak <xref:System.Windows.Forms.TextBox> , które wyświetlają pojedynczą kolumnę (lub właściwość) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Zaimplementuj <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolki on, na przykład <xref:System.Windows.Forms.DataGridView> , które wyświetlają listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Zaimplementuj <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolki na, takie jak <xref:System.Windows.Forms.ComboBox> ,, które wyświetlają listy (lub tabele) danych, ale muszą również przedstawić pojedynczą kolumnę lub właściwość. (Ten proces został opisany na stronie przewodnika).|

 Ten Instruktaż tworzy formant wyszukiwania, który wiąże się z danymi z dwóch tabel. Ten przykład używa `Customers` tabel i `Orders` z przykładowej bazy danych Northwind. Kontrolka wyszukiwania zostanie powiązana z `CustomerID` polem z `Orders` tabeli. Ta wartość zostanie użyta do wyszukania `CompanyName` z `Customers` tabeli.

 W tym instruktażu dowiesz się, jak:

- Utwórz nową **aplikację systemu Windows**.

- Dodaj nową **kontrolkę użytkownika** do projektu.

- Wizualne projektowanie kontrolki użytkownika.

- Zaimplementuj `LookupBindingProperty` atrybut.

- Utwórz zestaw danych za pomocą kreatora **konfiguracji źródła danych** .

- Ustaw kolumnę **CustomerID** w tabeli **Orders** w oknie **źródła danych** , aby użyć nowej kontrolki.

- Utwórz formularz, aby wyświetlić dane w nowej kontrolce.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind.

## <a name="create-a-windows-application"></a>Tworzenie aplikacji systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji systemu Windows**.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt systemu Windows

1. W programie Visual Studio w menu **plik** Utwórz nowy **projekt**.

2. Nazwij projekt **LookupControlWalkthrough**.

3. Wybierz pozycję **aplikacja Windows Forms**i kliknij przycisk **OK**.

     Projekt **LookupControlWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodawanie kontrolki użytkownika do projektu
 W tym instruktażu tworzony jest formant wyszukiwania z **kontrolki użytkownika**, więc Dodaj element **kontrolki użytkownika** do projektu **LookupControlWalkthrough** .

#### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu

1. W menu **projekt** wybierz polecenie **Dodaj kontrolkę użytkownika**.

2. Wpisz `LookupBox` w obszarze **Nazwa** , a następnie kliknij przycisk **Dodaj**.

     Formant **LookupBox** zostanie dodany do **Eksplorator rozwiązań**i otwarty w projektancie.

## <a name="design-the-lookupbox-control"></a>Zaprojektuj formant LookupBox

#### <a name="to-design-the-lookupbox-control"></a>Aby zaprojektować formant LookupBox

- Przeciągnij <xref:System.Windows.Forms.ComboBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

## <a name="add-the-required-data-binding-attribute"></a>Dodawanie wymaganego atrybutu powiązania danych
 W przypadku formantów wyszukiwania, które obsługują powiązanie danych, można zaimplementować <xref:System.ComponentModel.LookupBindingPropertiesAttribute> .

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Aby zaimplementować atrybut LookupBindingProperties

1. Przełącz formant **LookupBox** do widoku kodu. (W menu **Widok** wybierz polecenie **kod**).

2. Zastąp kod w `LookupBox` następującej postaci:

     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]

3. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Tworzenie źródła danych na podstawie bazy danych
 Ten krok polega na utworzeniu źródła danych przy użyciu kreatora **konfiguracji źródła danych** na podstawie `Customers` tabel i `Orders` w przykładowej bazie danych Northwind. Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [instalowanie SQL Server przykładowych baz danych](../data-tools/install-sql-server-sample-databases.md).

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

8. Wybierz `Customers` tabele i `Orders` , a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a `Customers` `Orders` tabele i są wyświetlane w oknie **źródła danych** .

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Ustaw kolumnę CustomerID tabeli Orders, aby używać kontrolki LookupBox
 W oknie **źródła danych** można ustawić kontrolkę, która ma zostać utworzona przed przeciągnięciem elementów na formularz.

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Aby ustawić kolumnę CustomerID do powiązania z kontrolką LookupBox

1. Otwórz **formularz Form1** w projektancie.

2. W oknie **źródła danych** rozwiń węzeł **Customers** .

3. Rozwiń węzeł **zamówienia** (jeden w węźle **klienci** poniżej kolumny **faks** ).

4. Kliknij strzałkę listy rozwijanej w węźle **zamówienia** , a następnie wybierz **szczegóły** z listy kontrolek.

5. Kliknij strzałkę listy rozwijanej w kolumnie **IDKlienta** (w węźle **zamówienia** ), a następnie wybierz pozycję **Dostosuj**.

6. Wybierz **LookupBox** z listy **skojarzonych kontrolek** w oknie dialogowym **Opcje dostosowywania interfejsu użytkownika danych** .

7. Kliknij przycisk **OK**.

8. Kliknij strzałkę listy rozwijanej w kolumnie **IDKlienta** i wybierz pozycję **LookupBox**.

## <a name="addcontrols-to-the-form"></a>Addcontrols do formularza
 Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na **formularz Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć formanty powiązane z danymi w formularzu systemu Windows

- Przeciągnij węzeł **zamówienia** z okna **źródła danych** na formularz systemu Windows i sprawdź, czy kontrolka **LookupBox** jest używana do wyświetlania danych w `CustomerID` kolumnie.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Powiąż formant, aby wyszukać NazwaFirmy z tabeli Customers

#### <a name="to-setup-the-lookup-bindings"></a>Aby skonfigurować powiązania wyszukiwania

- W oknie **źródła danych** wybierz węzeł główni **klienci** , a następnie przeciągnij go do pola kombi w **CustomerIDLookupBox** na **formularzu Form1**.

     Spowoduje to skonfigurowanie powiązania danych w celu wyświetlenia `CompanyName` z `Customers` tabeli, przy zachowaniu `CustomerID` wartości z `Orders` tabeli.

## <a name="running-the-application"></a>Uruchamianie aplikacji

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

- Naciśnij klawisz F5, aby uruchomić aplikację.

- Nawiguj po kilku rekordach i sprawdź, czy `CompanyName` pojawia się w `LookupBox` kontrolce.

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
