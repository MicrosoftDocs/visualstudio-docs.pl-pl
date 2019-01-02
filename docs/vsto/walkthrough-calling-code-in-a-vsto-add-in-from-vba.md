---
title: 'Przewodnik: Wywoływanie kodu w dodatku VSTO z kodu VBA'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 89b03298d1a0bb180e3eab706383e48ecd75cd7f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915906"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Przewodnik: Wywoływanie kodu w dodatku VSTO z kodu VBA
  W tym przewodniku pokazano, jak udostępnić obiektu w dodatku narzędzi VSTO dla programów do innych rozwiązań programu Microsoft Office, w tym Visual Basic for Applications (VBA) i dodatki COM, VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Mimo że program Excel jest wykorzystywany w tym przewodniku szczegółowo, koncepcje dowodzą przewodnika są stosowane do dowolnego dodatku narzędzi VSTO dla programów project szablonu dostarczane przez program Visual Studio.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Definiowanie klasy, które mogą być udostępniane do innych rozwiązań pakietu Office.  
  
- Udostępnia klasy do innych rozwiązań pakietu Office.  
  
- Wywoływanie metody klasy z kodu VBA.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Excel  
  
## <a name="create-the-vsto-add-in-project"></a>Utwórz projekt dodatku narzędzi VSTO  
 Pierwszym krokiem jest utworzenie projektu dodatku narzędzi VSTO dla programu Excel.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Utwórz projekt dodatku narzędzi VSTO programu Excel o nazwie **ExcelImportData**, przy użyciu szablonu projektu dodatku narzędzi VSTO programu Excel. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** plik kodu i dodaje **ExcelImportData** projekt **Eksploratora rozwiązań**.  
  
## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definiowanie klasy, która może narazić do innych rozwiązań pakietu Office  
 Ten przewodnik ma na celu wywoływać `ImportData` metody klasy o nazwie `AddInUtilities` w dodatku VSTO z kodu VBA. Ta metoda zapisuje ciąg do komórki A1 aktywnego arkusza.  
  
 Aby udostępnić `AddInUtilities` klasy do innych rozwiązań pakietu Office należy klasa publiczna i widoczna dla modelu COM. Należy również udostępnić [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interfejsu w klasie. W poniższej procedurze demonstruje sposób spełniają te wymagania. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Aby zdefiniować klasę, która może narazić do innych rozwiązań pakietu Office  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj klasę**.  
  
2.  W **Dodaj nowy element** okna dialogowego pole, Zmień nazwę nowej klasy, aby **AddInUtilities**i kliknij przycisk **Dodaj**.  
  
     **AddInUtilities.cs** lub **AddInUtilities.vb** plik zostanie otwarty w edytorze kodu.  
  
3.  Dodaj następujące instrukcje na górze pliku.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]  
  
4.  Zastąp `AddInUtilities` klasy z następującym kodem.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
     Ten kod sprawia, że `AddInUtilities` klasy widoczne dla modelu COM, a następnie dodaje `ImportData` metodę do klasy. Aby udostępnić [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interfejsu `AddInUtilities` ma również klasy <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu który implementuje interfejs, który jest widoczny dla modelu COM.  
  
## <a name="expose-the-class-to-other-office-solutions"></a>Udostępnianie klas do innych rozwiązań pakietu Office  
 Aby udostępnić `AddInUtilities` klasy do innych rozwiązań pakietu Office, Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> method in Class metoda `ThisAddIn` klasy. W przypadku przesłonięcia, należy zwrócić wystąpienia `AddInUtilities` klasy.  
  
### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Aby udostępnić klasy AddInUtilities do innych rozwiązań pakietu Office  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **Excel**.  
  
2.  Kliknij prawym przyciskiem myszy **ThisAddIn.cs** lub **ThisAddIn.vb**, a następnie kliknij przycisk **Wyświetl kod**.  
  
3.  Dodaj następujący kod do `ThisAddIn` klasy.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
4.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Upewnij się, że rozwiązanie zostanie skompilowane bez błędów.  
  
## <a name="test-the-vsto-add-in"></a>Testowanie dodatku narzędzi VSTO  
 Można wywoływać `AddInUtilities` klasy z kilku różnych typów rozwiązań dla pakietu Office. W tym przewodniku użyje kodu z VBA w skoroszycie programu Excel. Aby uzyskać więcej informacji na temat innych rodzajów rozwiązań pakietu Office, można również użyć zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  W programie Excel skoroszyt active jako skoroszyt Excel Macro-Enabled (*.xlsm). Zapisz go w dogodnym miejscu, na przykład na pulpit.  
  
3.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  W **kodu** grupy, kliknij przycisk **języka Visual Basic**.  
  
     Zostanie otwarty Edytor kodu języka Visual Basic.  
  
5.  W **projektu** okna, kliknij dwukrotnie **ThisWorkbook**.  
  
     Plik kodu dla `ThisWorkbook` obiektu zostanie otwarta.  
  
6.  Dodaj następujący kod VBA do pliku kodu. Ten kod najpierw pobiera obiekt COMAddIn, który reprezentuje **ExcelImportData** dodatku narzędzi VSTO. Następnie kod używa obiektu COMAddIn właściwości obiektu do wywołania `ImportData` metody.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim addIn As COMAddIn  
        Dim automationObject As Object  
        Set addIn = Application.COMAddIns("ExcelImportData")  
        Set automationObject = addIn.Object  
        automationObject.ImportData  
    End Sub  
    ```  
  
7.  Naciśnij klawisz **F5**.  
  
8.  Upewnij się, że nowy **zaimportowane dane** arkusz został dodany do skoroszytu. Sprawdź także, że komórka A1 zawiera ciąg **to Moje dane**.  
  
9. Zakończ działanie programu Excel.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz dowiedzieć się więcej na temat programowania dodatków narzędzi VSTO dla programów w tych tematach:  
  
-   Użyj `ThisAddIn` klasy w celu zautomatyzowania aplikacji hosta oraz wykonywania innych zadań w projektach dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
-   Tworzenie niestandardowego okienka zadań w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md) i [jak: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Dostosuj Wstążkę w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md) i [jak: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
