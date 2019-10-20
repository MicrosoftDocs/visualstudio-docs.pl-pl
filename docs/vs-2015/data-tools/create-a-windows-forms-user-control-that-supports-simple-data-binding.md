---
title: Tworzenie kontrolki użytkownika Windows Forms, która obsługuje proste powiązanie danych | Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf30a38384863c9ba5a8af35af3326a51058d831
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668768"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Tworzenie kontrolki użytkownika aplikacji Windows Forms obsługującej proste powiązanie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas wyświetlania danych w formularzach w aplikacjach systemu Windows można wybrać istniejące kontrolki z **przybornika**lub można utworzyć niestandardowe kontrolki, jeśli aplikacja wymaga funkcjonalności, która nie jest dostępna w kontrolkach standardowych. W tym instruktażu pokazano, jak utworzyć kontrolkę implementującą <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Kontrolki implementujące <xref:System.ComponentModel.DefaultBindingPropertyAttribute> mogą zawierać jedną właściwość, która może być powiązana z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.TextBox> lub <xref:System.Windows.Forms.CheckBox>.

 Aby uzyskać więcej informacji na temat tworzenia kontroli, zobacz [Opracowywanie formantów Windows Forms w czasie projektowania](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Podczas tworzenia formantów do użycia w scenariuszach powiązań danych należy zaimplementować jeden z następujących atrybutów powiązania danych:

|Użycie atrybutu powiązania danych|
|-----------------------------------|
|Zaimplementuj <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na prostych kontrolkach, takich jak <xref:System.Windows.Forms.TextBox>, które wyświetlają pojedynczą kolumnę (lub właściwość) danych. (Ten proces został opisany na stronie przewodnika).|
|Zaimplementuj <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> na kontrolkach, takich jak <xref:System.Windows.Forms.DataGridView>, które wyświetlają listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Zaimplementuj <xref:System.ComponentModel.LookupBindingPropertiesAttribute> na kontrolkach, takich jak <xref:System.Windows.Forms.ComboBox>, które wyświetlają listy (lub tabele) danych, ale również muszą przedstawić pojedynczą kolumnę lub właściwość. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms, która obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Ten Instruktaż tworzy prostą kontrolkę, która wyświetla dane z pojedynczej kolumny w tabeli. W tym przykładzie użyta zostanie kolumna `Phone` tabeli `Customers` z przykładowej bazy danych Northwind. Prosta kontrolka użytkownika będzie wyświetlać numery telefonów klientów w standardowym formacie numeru telefonu przy użyciu <xref:System.Windows.Forms.MaskedTextBox> i ustawiając maskę na numer telefonu.

 W tym instruktażu dowiesz się, jak:

- Utwórz nową **aplikację systemu Windows**.

- Dodaj nową **kontrolkę użytkownika** do projektu.

- Wizualne projektowanie kontrolki użytkownika.

- Zaimplementuj atrybut `DefaultBindingProperty`.

- Utwórz zestaw danych za pomocą kreatora **konfiguracji źródła danych** .

- Ustaw kolumnę **telefon** w oknie **źródła danych** , aby użyć nowej kontrolki.

- Utwórz formularz, aby wyświetlić dane w nowej kontrolce.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind.

## <a name="create-a-windows-application"></a>Tworzenie aplikacji systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji systemu Windows**.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt systemu Windows

1. W programie Visual Studio w menu **plik** Utwórz nowy **projekt**.

2. Nazwij projekt **SimpleControlWalkthrough**.

3. Wybierz pozycję **aplikacja systemu Windows** i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **SimpleControlWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodawanie kontrolki użytkownika do projektu
 Ten Instruktaż tworzy prostą kontrolkę z powiązaniem danych z **kontrolki użytkownika**, więc Dodaj element **kontrolki użytkownika** do projektu **SimpleControlWalkthrough** .

#### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu

1. W menu **projekt** wybierz polecenie **Dodaj kontrolkę użytkownika**.

2. Wpisz `PhoneNumberBox` w obszarze Nazwa, a następnie kliknij przycisk **Dodaj**.

     Formant **PhoneNumberBox** zostanie dodany do **Eksplorator rozwiązań**i otwarty w projektancie.

## <a name="design-the-phonenumberbox-control"></a>Zaprojektuj formant PhoneNumberBox
 Ten przewodnik rozszerza istniejący <xref:System.Windows.Forms.MaskedTextBox>, aby utworzyć kontrolkę `PhoneNumberBox`.

#### <a name="to-design-the-phonenumberbox-control"></a>Aby zaprojektować formant PhoneNumberBox

1. Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

2. Wybierz tag inteligentny na <xref:System.Windows.Forms.MaskedTextBox> przeciągniętej, a następnie wybierz pozycję **Ustaw maskę**.

3. W oknie dialogowym **maska wejścia** wybierz pozycję **numer telefonu** , a następnie kliknij przycisk **OK** , aby ustawić maskę.

## <a name="add-the-required-data-binding-attribute"></a>Dodawanie wymaganego atrybutu powiązania danych
 W przypadku prostych formantów, które obsługują wiązania z danymi, zaimplementuj <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Aby zaimplementować atrybut DefaultBindingProperty

1. Przełącz formant `PhoneNumberBox` do widoku kodu. (W menu **Widok** wybierz polecenie **kod**).

2. Zastąp kod w `PhoneNumberBox` następującym:

     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]

3. Z menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Tworzenie źródła danych na podstawie bazy danych
 Ten krok powoduje użycie kreatora **konfiguracji źródła danych** w celu utworzenia źródła danych na podstawie tabeli `Customers` w przykładowej bazie danych Northwind. Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind.

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić kreatora **konfiguracji źródła danych** .

3. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

6. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz tabelę `Customers` a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a tabela `Customers` zostanie wyświetlona w oknie **źródła danych** .

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Ustaw kolumnę telefon, aby użyć kontrolki PhoneNumberBox
 W oknie **źródła danych** można ustawić kontrolkę, która ma zostać utworzona przed przeciągnięciem elementów na formularz.

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Aby ustawić kolumnę telefon na powiązanie z kontrolką PhoneNumberBox

1. Otwórz **formularz Form1** w projektancie.

2. W oknie **źródła danych** rozwiń węzeł **Customers** .

3. Kliknij strzałkę listy rozwijanej w węźle **klienci** , a następnie wybierz **szczegóły** z listy kontrolek.

4. Kliknij strzałkę listy rozwijanej w kolumnie **telefon** , a następnie wybierz pozycję **Dostosuj**.

5. Wybierz **PhoneNumberBox** z listy **skojarzonych kontrolek** w oknie dialogowym **Opcje dostosowywania interfejsu użytkownika danych** .

6. Kliknij strzałkę listy rozwijanej w kolumnie **telefon** , a następnie wybierz pozycję **PhoneNumberBox**.

## <a name="addcontrols-to-the-form"></a>Addcontrols do formularza
 Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć kontrolki powiązane z danymi w formularzu

- Przeciągnij węzeł główni **klienci** z okna **źródła danych** na formularz i sprawdź, czy formant `PhoneNumberBox` jest używany do wyświetlania danych w kolumnie `Phone`.

     Formanty powiązane z danymi z opisowymi etykietami są wyświetlane w formularzu wraz z paskiem narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania po rekordach. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

## <a name="run-the-application"></a>Uruchom aplikację

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

- Naciśnij klawisz F5, aby uruchomić aplikację.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu kontrolki, która obsługuje powiązanie danych. Oto kilka typowych kroków, które obejmują:

- Umieszczenie niestandardowych kontrolek w bibliotece kontrolek, aby można było użyć ich ponownie w innych aplikacjach.

- Tworzenie formantów, które obsługują bardziej złożone scenariusze powiązań danych. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki użytkownika Windows Forms obsługującej złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) i [Tworzenie Windows Forms kontrolki użytkownika, która obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Zobacz też
 [Powiązywanie formantów Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
