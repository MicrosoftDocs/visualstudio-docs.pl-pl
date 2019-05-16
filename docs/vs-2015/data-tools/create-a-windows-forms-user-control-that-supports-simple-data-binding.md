---
title: Tworzenie kontrolki użytkownika formularzy Windows obsługującego proste powiązanie danych | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ac931dfcf7b56619707a2bd42a32f5a369b04d9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704992"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Tworzenie kontrolki użytkownika formularzy Windows obsługującego proste powiązanie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas wyświetlania danych w formularzach w aplikacjach Windows, można wybrać istniejące kontrolki z **przybornika**, lub możesz tworzyć niestandardowe formanty, jeśli aplikacja wymaga funkcji, która nie jest dostępna w standardowych kontrolek. W tym instruktażu pokazano, jak utworzyć formant, który implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Określa, które implementują <xref:System.ComponentModel.DefaultBindingPropertyAttribute> może zawierać jedną właściwość, która może być powiązana z danymi. Te kontrolki są podobne do <xref:System.Windows.Forms.TextBox> lub <xref:System.Windows.Forms.CheckBox>.  
  
 Aby uzyskać więcej informacji na temat tworzenia formantu, zobacz [tworzenia kontrolek Windows Forms w czasie projektowania](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Podczas tworzenia kontrolki do użycia w scenariuszach wiązania danych, powinny implementować jeden z następujących atrybutów powiązania danych:  
  
|Użycie atrybutu powiązania danych|  
|-----------------------------------|  
|Implementowanie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na proste formanty, takie jak <xref:System.Windows.Forms.TextBox>, który pojedynczej kolumny (lub wyświetlić właściwości) danych. (Ten proces jest opisany na tej stronie wskazówki).|  
|Implementowanie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.DataGridView>, wyświetlanie listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.ComboBox>, który wyświetla listy lub tabele danych, ale również są potrzebne do pojedynczej kolumny lub właściwości. Aby uzyskać więcej informacji, zobacz [utworzyć formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Ten przewodnik tworzy prosty formant, który wyświetla dane z jednej kolumny w tabeli. W tym przykładzie użyto `Phone` kolumny `Customers` tabeli w bazie danych Northwind. Proste kontrolki będą wyświetlane numery telefonów klientów w standardowym formacie numeru telefonu, przy użyciu <xref:System.Windows.Forms.MaskedTextBox> i ustawienie maski numeru telefonu.  
  
 Z tego instruktażu dowiesz się jak:  
  
- Utwórz nową **aplikacji Windows**.  
  
- Dodaj nową **kontrolki użytkownika** do projektu.  
  
- Wizualnie projektować kontrolkę użytkownika.  
  
- Implementowanie `DefaultBindingProperty` atrybutu.  
  
- Tworzenie zestawu danych za pomocą **konfiguracji źródła danych** kreatora.  
  
- Ustaw **Phone** kolumny w **źródeł danych** okno, aby użyć nowego formantu.  
  
- Utwórz formularz do wyświetlania danych w nowej kontrolki.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
- Dostęp do przykładowej bazy danych Northwind.
  
## <a name="create-a-windows-application"></a>Tworzenie aplikacji Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt Windows  
  
1. W programie Visual Studio z **pliku** menu Utwórz nową **projektu**.  
  
2. Nadaj projektowi nazwę **SimpleControlWalkthrough**.  
  
3. Wybierz **aplikacji Windows** i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **SimpleControlWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu  
 Ten przewodnik tworzy po prostego formantu powiązać dane z **kontrolki użytkownika**, więc Dodaj **kontrolki użytkownika** elementu do **SimpleControlWalkthrough** projektu.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu  
  
1. Z **projektu** menu, wybierz **Dodaj kontrolkę użytkownika**.  
  
2. Typ `PhoneNumberBox` w obszarze nazw, a następnie kliknij przycisk **Dodaj**.  
  
     **PhoneNumberBox** formant jest dodawany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.  
  
## <a name="design-the-phonenumberbox-control"></a>Projektowanie kontrolki PhoneNumberBox  
 W tym przewodniku rozszerza istniejący <xref:System.Windows.Forms.MaskedTextBox> utworzyć `PhoneNumberBox` kontroli.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Aby zaprojektować kontroli PhoneNumberBox  
  
1. Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.  
  
2. Wybierz tag inteligentny <xref:System.Windows.Forms.MaskedTextBox> możesz po prostu przeciągnąć i wybierz polecenie **ustawić maskę**.  
  
3. Wybierz **numer telefonu** w **maska wprowadzania** okno dialogowe, a następnie kliknij przycisk **OK** ustalenie maski.  
  
## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych  
 Implementowanie prostego formantów tego wiązania danych pomocy technicznej, <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Aby zaimplementować atrybutu DefaultBindingProperty  
  
1. Przełącznik `PhoneNumberBox` formantu do widoku kodu. (Na **widoku** menu, wybierz **kodu**.)  
  
2. Zastąp kod w `PhoneNumberBox` następującym kodem:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych  
 Ten krok używa **konfiguracji źródła danych** kreatora w celu utworzenia źródła danych na podstawie `Customers` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia.
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1. Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
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
 W ramach **źródeł danych** okna, można ustawić formant aby je utworzyć przed przeciąganie elementów do formularza.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Aby ustawić kolumny telefonu, aby powiązać formant PhoneNumberBox  
  
1. Otwórz **Form1** w projektancie.  
  
2. Rozwiń **klientów** w węźle **źródeł danych** okna.  
  
3. Kliknij strzałkę listy rozwijanej **klientów** węzeł i wybierz polecenie **szczegóły** na liście kontrolek.  
  
4. Kliknij strzałkę listy rozwijanej **Phone** kolumny i wybierz polecenie **Dostosuj**.  
  
5. Wybierz **PhoneNumberBox** z listy **skojarzonych formantów** w **opcje dostosowywania interfejsu użytkownika danych** okno dialogowe.  
  
6. Kliknij strzałkę listy rozwijanej **Phone** kolumny, a wybierz **PhoneNumberBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols do formularza  
 Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna na formularzu.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formanty powiązane z danymi formularza  
  
- Przeciągnij główny **klientów** węzła z **źródeł danych** okna do formularza i upewnij się, że `PhoneNumberBox` formant jest używany do wyświetlania danych w `Phone` kolumny.  
  
     Formanty powiązane z danymi z etykietami opisowymi są wyświetlane w formularzu, oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
## <a name="run-the-application"></a>Uruchamianie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
- Naciśnij klawisz F5, aby uruchomić aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzenie kontrolki, która obsługuje powiązanie danych. Niektóre typowe następne kroki obejmują:  
  
- Wprowadzenie do Kontrolki niestandardowe w bibliotece kontrolki, więc można go używać w innych aplikacjach.  
  
- Tworzenie formantów, które obsługują bardziej złożonych scenariuszy powiązanie danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) i [utworzyć formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
