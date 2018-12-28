---
title: Tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e2ac4dc4ac8a53c2833088f821a82ae00573a13b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648844"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Podczas wyświetlania danych w formularzach w aplikacjach Windows, można wybrać istniejące kontrolki z **przybornika**, lub możesz tworzyć niestandardowe formanty, jeśli aplikacja wymaga funkcji, która nie jest dostępna w standardowych kontrolek. W tym instruktażu pokazano, jak utworzyć formant, który implementuje <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Określa, które implementują <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> zawierają `DataSource` i `DataMember` właściwość, która może być powiązana z danymi. Te kontrolki są podobne do <xref:System.Windows.Forms.DataGridView> lub <xref:System.Windows.Forms.ListBox>.  
  
 Aby uzyskać więcej informacji na temat tworzenia formantu, zobacz [tworzenia kontrolek Windows Forms w czasie projektowania](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Podczas tworzenia kontrolki do użycia w scenariuszach powiązanie danych należy implementować jeden z następujących atrybutów powiązania danych:  
  
|Użycie atrybutu powiązania danych|  
|-----------------------------------|  
|Implementowanie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na proste formanty, takie jak <xref:System.Windows.Forms.TextBox>, który pojedynczej kolumny (lub wyświetlić właściwości) danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementowanie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.DataGridView>, wyświetlanie listy (lub tabele) danych. (Ten proces jest opisany na tej stronie wskazówki).|  
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.ComboBox>, który wyświetla listy lub tabele danych, ale również są potrzebne do pojedynczej kolumny lub właściwości. Aby uzyskać więcej informacji, zobacz [utworzyć formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Ten przewodnik tworzy formant złożony, który wyświetla wiersze danych z tabeli. W tym przykładzie użyto `Customers` tabeli w bazie danych Northwind. Kontrolka złożona użytkownika będzie wyświetlać tabelę Klienci w <xref:System.Windows.Forms.DataGridView> w formancie niestandardowym.  
  
 Z tego instruktażu dowiesz się jak:  
  
-   Utwórz nową **aplikacji Windows**.  
  
-   Dodaj nową **kontrolki użytkownika** do projektu.  
  
-   Wizualnie projektować kontrolkę użytkownika.  
  
-   Implementowanie `ComplexBindingProperty` atrybutu.  
  
-   Tworzenie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Ustaw **klientów** tabelę [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) używać nowego formantu złożonego.  
  
-   Dodawanie nowej kontrolki, przeciągając go z **okna źródeł danych** na **Form1**.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Dostęp do przykładowej bazy danych Northwind.
  
## <a name="create-a-windows-application"></a>Tworzenie aplikacji Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt Windows  
  
1.  W programie Visual Studio z **pliku** menu Utwórz nową **projektu**.  
  
2.  Nadaj projektowi nazwę **ComplexControlWalkthrough**.  
  
3.  Wybierz **aplikacji Windows**i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **ComplexControlWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu  
 Ponieważ ten przewodnik tworzy po złożone kontrolki możliwej do wiązania danych — od **kontrolki użytkownika**, należy dodać **kontrolki użytkownika** do projektu.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu  
  
1.  Z **projektu** menu, wybierz **Dodaj kontrolkę użytkownika**.  
  
2.  Typ **ComplexDataGridView** w **nazwa** obszaru, a następnie kliknij **Dodaj**.  
  
     **ComplexDataGridView** formant jest dodawany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.  
  
## <a name="design-the-complexdatagridview-control"></a>Projektowanie kontrolki ComplexDataGridView  
 Ten krok powoduje dodanie <xref:System.Windows.Forms.DataGridView> do kontrolki użytkownika.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Aby zaprojektować kontroli ComplexDataGridView  
  
-   Przeciągnij <xref:System.Windows.Forms.DataGridView> z **przybornika** na powierzchnię projektu kontrolki użytkownika.  
  
## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych  
 Złożone formantów to powiązanie danych pomocy technicznej, można zaimplementować <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Aby zaimplementować atrybutu ComplexBindingProperties  
  
1.  Przełącznik **ComplexDataGridView** formantu do widoku kodu. (Na **widoku** menu, wybierz opcję **kodu**.)  
  
2.  Zastąp kod w `ComplexDataGridView` następującym kodem:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Tworzenie źródła danych z bazy danych  
 Ten krok używa **konfiguracji źródła danych** kreatora w celu utworzenia źródła danych na podstawie `Customers` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [Instalowanie programu SQL Server przykładowych baz danych](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **konfiguracji źródła danych** kreatora.  
  
3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz połączenie danych** wykonaj strony, jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
    -   Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.  
  
6.  Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.  
  
7.  Na **wybierz obiekty bazy danych** rozwiń **tabel** węzła.  
  
8.  Wybierz `Customers` tabeli, a następnie kliknij przycisk **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu, a `Customers` tabela zostanie wyświetlona w **źródeł danych** okna.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Ustawianie tabeli Customers, aby użyć kontrolki ComplexDataGridView  
 W ramach **źródeł danych** okna, można ustawić formant aby je utworzyć przed przeciąganie elementów do formularza.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Aby ustawić tabeli Customers, aby powiązać formant ComplexDataGridView  
  
1.  Otwórz **Form1** w projektancie.  
  
2.  Rozwiń **klientów** w węźle **źródeł danych** okna.  
  
3.  Kliknij strzałkę listy rozwijanej **klientów** węzeł i wybierz polecenie **Dostosuj**.  
  
4.  Wybierz **ComplexDataGridView** z listy **skojarzonych formantów** w **opcje dostosowywania interfejsu użytkownika danych** okno dialogowe.  
  
5.  Kliknij strzałkę listy rozwijanej `Customers` tabeli, a następnie wybierz **ComplexDataGridView** na liście kontrolek.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols do formularza  
 Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formanty powiązane z danymi formularza  
  
-   Przeciągnij główny **klientów** węzła z **źródeł danych** okna na formularzu. Upewnij się, że **ComplexDataGridView** formant jest używany do wyświetlania danych w tabeli.  
  
## <a name="running-the-application"></a>Uruchamianie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
-   Naciśnij klawisz F5, aby uruchomić aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzenie kontrolki, która obsługuje powiązanie danych. Niektóre typowe następne kroki obejmują:  
  
-   Wprowadzenie do Kontrolki niestandardowe w bibliotece kontrolki, więc można go używać w innych aplikacjach.  
  
-   Tworzenie formantów, które obsługują scenariusze wyszukiwania. Aby uzyskać więcej informacji, zobacz [utworzyć formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Kontrolki formularzy Windows Forms](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
