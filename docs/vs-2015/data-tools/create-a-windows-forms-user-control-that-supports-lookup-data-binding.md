---
title: Utwórz formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 786895d045b4ee43d9fbb8cb519fdd47d76b057a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792617"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Utwórz formant użytkownika Windows Forms, który obsługuje powiązanie danych wyszukiwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Podczas wyświetlania danych w formularzach Windows Forms, można wybrać istniejące kontrolki z **przybornika**, lub możesz tworzyć niestandardowe formanty, jeśli aplikacja wymaga funkcji, które nie są dostępne w standardowych kontrolek. W tym instruktażu pokazano, jak utworzyć formant, który implementuje <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Określa, które implementują <xref:System.ComponentModel.LookupBindingPropertiesAttribute> może zawierać trzy właściwości, które mogą być powiązane z danymi. Te kontrolki są podobne do <xref:System.Windows.Forms.ComboBox>.  
  
 Aby uzyskać więcej informacji na temat tworzenia formantu, zobacz [tworzenia kontrolek Windows Forms w czasie projektowania](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Podczas tworzenia kontrolki do użycia w scenariuszach powiązanie danych należy implementować jeden z następujących atrybutów powiązania danych:  
  
|Użycie atrybutu powiązania danych|  
|-----------------------------------|  
|Implementowanie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> na proste formanty, takie jak <xref:System.Windows.Forms.TextBox>, który pojedynczej kolumny (lub wyświetlić właściwości) danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementowanie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.DataGridView>, wyświetlanie listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolki użytkownika formularzy Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> kontrolek, takich jak <xref:System.Windows.Forms.ComboBox>, wyświetlanie listy lub tabele danych, ale również są potrzebne do pojedynczej kolumny lub właściwości. (Ten proces jest opisany na tej stronie wskazówki).|  
  
 Ten przewodnik tworzy kontrolkę wyszukiwania odnośników, który powiąże dane z dwóch tabel. W tym przykładzie użyto `Customers` i `Orders` tabel z przykładowej bazy danych Northwind. Będą powiązane kontrolkę wyszukiwania odnośników `CustomerID` pola z `Orders` tabeli. Ta wartość zostanie użyty do wyszukania `CompanyName` z `Customers` tabeli.  
  
 Z tego instruktażu dowiesz się jak:  
  
-   Utwórz nową **aplikacji Windows**.  
  
-   Dodaj nową **kontrolki użytkownika** do projektu.  
  
-   Wizualnie projektować kontrolkę użytkownika.  
  
-   Implementowanie `LookupBindingProperty` atrybutu.  
  
-   Tworzenie zestawu danych za pomocą **konfiguracji źródła danych** kreatora.  
  
-   Ustaw **CustomerID** kolumny na **zamówienia** tabeli w **źródeł danych** okna, aby użyć nowego formantu.  
  
-   Utwórz formularz do wyświetlania danych w nowej kontrolki.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Dostęp do przykładowej bazy danych Northwind.  
  
## <a name="create-a-windows-application"></a>Tworzenie aplikacji Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt Windows  
  
1.  W programie Visual Studio z **pliku** menu Utwórz nową **projektu**.  
  
2.  Nadaj projektowi nazwę **LookupControlWalkthrough**.  
  
3.  Wybierz **aplikacja interfejsu Windows Forms**i kliknij przycisk **OK**.  
  
     **LookupControlWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu  
 Ten poradnik tworzy kontrolkę wyszukiwania odnośników z **kontrolki użytkownika**, więc Dodaj **kontrolki użytkownika** elementu do **LookupControlWalkthrough** projektu.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu  
  
1.  Z **projektu** menu, wybierz opcję **Dodaj kontrolkę użytkownika**.  
  
2.  Typ `LookupBox` w **nazwa** obszaru, a następnie kliknij **Dodaj**.  
  
     **LookupBox** formant jest dodawany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.  
  
## <a name="design-the-lookupbox-control"></a>Projektowanie kontrolki LookupBox  
  
#### <a name="to-design-the-lookupbox-control"></a>Aby zaprojektować kontroli LookupBox  
  
-   Przeciągnij <xref:System.Windows.Forms.ComboBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.  
  
## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych  
 Wyszukiwanie formantów to powiązanie danych pomocy technicznej, można zaimplementować <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Aby zaimplementować atrybutu LookupBindingProperties  
  
1.  Przełącznik **LookupBox** formantu do widoku kodu. (Na **widoku** menu, wybierz **kodu**.)  
  
2.  Zastąp kod w `LookupBox` następującym kodem:  
  
     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]  
  
3.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych  
 Spowoduje to utworzenie źródła danych przy użyciu **konfiguracji źródła danych** kreatora, na podstawie `Customers` i `Orders` tabel w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [Instalowanie programu SQL Server przykładowych baz danych](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
8.  Wybierz `Customers` i `Orders` tabel, a następnie kliknij **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu, a `Customers` i `Orders` tabele są wyświetlane w **źródeł danych** okna.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Ustaw w kolumnie CustomerID w tabeli zamówienia, aby użyć kontrolki LookupBox  
 W ramach **źródeł danych** okna, można ustawić formant aby je utworzyć przed przeciąganie elementów do formularza.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Aby ustawić kolumnie CustomerID, aby powiązać formant LookupBox  
  
1.  Otwórz **Form1** w projektancie.  
  
2.  Rozwiń **klientów** w węźle **źródeł danych** okna.  
  
3.  Rozwiń **zamówienia** węzeł (w **klientów** poniżej węzła **faks** kolumny).  
  
4.  Kliknij strzałkę listy rozwijanej **zamówienia** węzeł i wybierz polecenie **szczegóły** na liście kontrolek.  
  
5.  Kliknij strzałkę listy rozwijanej **CustomerID** kolumny (w **zamówienia** węzła) i wybierz polecenie **Dostosuj**.  
  
6.  Wybierz **LookupBox** z listy **skojarzonych formantów** w **opcje dostosowywania interfejsu użytkownika danych** okno dialogowe.  
  
7.  Kliknij przycisk **OK**.  
  
8.  Kliknij strzałkę listy rozwijanej **CustomerID** kolumny, a wybierz **LookupBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols do formularza  
 Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna na **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć formanty powiązane z danymi w formularzu Windows  
  
-   Przeciągnij **zamówienia** węzła z **źródeł danych** okna na formularzu Windows i sprawdź, czy **LookupBox** formant jest używany do wyświetlania danych w `CustomerID` kolumna.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Powiąż formant aby wyszukać CompanyName z tabeli Customers  
  
#### <a name="to-setup-the-lookup-bindings"></a>Aby skonfigurować powiązania wyszukiwania odnośników  
  
-   Wybierz główny **klientów** w węźle **źródeł danych** okna, a następnie przeciągnij pole na kombi w **CustomerIDLookupBox** na **Form1** .  
  
     Spowoduje to utworzenie powiązania danych do wyświetlenia `CompanyName` z `Customers` tabeli przy zachowaniu `CustomerID` wartość z `Orders` tabeli.  
  
## <a name="running-the-application"></a>Uruchamianie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
-   Naciśnij klawisz F5, aby uruchomić aplikację.  
  
-   Nawigowanie po niektóre rekordy i upewnij się, że `CompanyName` pojawia się w `LookupBox` kontroli.  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
