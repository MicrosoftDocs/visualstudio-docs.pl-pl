---
title: 'Przewodnik: wywołanie kodu w dodatku VSTO z VBA'
description: Dowiedz się, jak uwidocznić obiekt w dodatku VSTO dla innych rozwiązań Microsoft Office, w tym dodatków VBA (Visual Basic for Applications) i COM VSTO.
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 21e0928396327911ea794c6270340c6efd27a43e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824604"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Przewodnik: wywołanie kodu w dodatku VSTO z VBA
  W tym przewodniku pokazano, jak uwidocznić obiekt w dodatku VSTO dla innych rozwiązań Microsoft Office, w tym dodatków VBA (Visual Basic for Applications) i COM VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Mimo że w tym przewodniku używany jest program Excel, koncepcje zademonstrowane w tym przewodniku mają zastosowanie do dowolnego szablonu projektu dodatku VSTO dostarczonego przez Visual Studio.

 W instruktażu przedstawiono następujące zagadnienia:

- Definiowanie klasy, która może być ujawniona innym rozwiązaniom pakietu Office.

- Udostępnianie klasy innym rozwiązaniom pakietu Office.

- Wywoływanie metody klasy z kodu VBA.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>Tworzenie projektu dodatku VSTO
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku VSTO programu Excel o nazwie **ExcelImportData** przy użyciu szablonu projektu dodatku VSTO programu Excel. Aby uzyskać więcej informacji, [zobacz How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera plik **kodu ThisAddIn.cs** lub **ThisAddIn.vb** i dodaje projekt **ExcelImportData** do **Eksplorator rozwiązań**.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definiowanie klasy, która może być uwidoczniana dla innych rozwiązań pakietu Office
 Celem tego przewodnika jest wywołanie metody klasy o nazwie w dodatku `ImportData` `AddInUtilities` VSTO z kodu VBA. Ta metoda zapisuje ciąg w komórce A1 aktywnego arkusza.

 Aby `AddInUtilities` uwidocznić klasę innym rozwiązaniom pakietu Office, należy udostępnić klasę jako publiczną i widoczną dla com. Należy również uwidocznić [interfejs IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) w klasie . Kod w poniższej procedurze przedstawia jeden ze sposobów spełnienia tych wymagań. Aby uzyskać więcej informacji, zobacz [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)(Wywoływanie kodu w dodatki VSTO z innych rozwiązań pakietu Office).

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Aby zdefiniować klasę, która może być uwidoczniana dla innych rozwiązań pakietu Office

1. W menu **Project (Projekt)** kliknij pozycję **Add Class (Dodaj klasę).**

2. W **oknie dialogowym Dodawanie** nowego elementu zmień nazwę nowej klasy na **AddInUtilities** i kliknij przycisk **Dodaj**.

     Plik **AddInUtilities.cs** lub **AddInUtilities.vb** zostanie otwarty w Edytorze kodu.

3. Dodaj następujące dyrektywy na początku pliku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet2":::

4. Zastąp `AddInUtilities` klasę poniższym kodem.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

     Ten kod sprawia, `AddInUtilities` że klasa jest widoczna dla com i `ImportData` dodaje metodę do klasy . Aby [uwidocznić interfejs IDispatch,](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) klasa ma również atrybut i implementuje interfejs, który `AddInUtilities` jest widoczny dla <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> com.

## <a name="expose-the-class-to-other-office-solutions"></a>Uwidocznij klasę innym rozwiązaniom pakietu Office
 Aby `AddInUtilities` uwidocznić klasę innym rozwiązaniom pakietu Office, <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> zastąp metodę w klasie `ThisAddIn` . W przesłonięciach zwróć wystąpienie `AddInUtilities` klasy .

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Aby uwidocznić klasę AddInUtilities innym rozwiązaniom pakietu Office

1. W **Eksplorator rozwiązań** rozwiń w **programie Excel**.

2. Kliknij prawym przyciskiem **myszy pozycję ThisAddIn.cs** lub **ThisAddIn.vb,** a następnie kliknij **polecenie Wyświetl kod.**

3. Dodaj poniższy kod do klasy `ThisAddIn`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

4. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Sprawdź, czy rozwiązanie jest kompilowane bez błędów.

## <a name="test-the-vsto-add-in"></a>Testowanie dodatku VSTO
 Możesz wywołać klasę `AddInUtilities` z kilku różnych typów rozwiązań pakietu Office. W tym przewodniku użyjemy kodu VBA w skoroszycie programu Excel. Aby uzyskać więcej informacji o innych typach rozwiązań pakietu Office, których można również użyć, zobacz [Call code in VSTO Add-ins from other Office solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)(Kod wywołań w dodatkich VSTO z innych rozwiązań pakietu Office).

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatek VSTO

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. W programie Excel zapisz aktywny skoroszyt jako skoroszyt programu Excel Macro-Enabled skoroszytu (*.xlsm). Zapisz go w dogodnym miejscu, takim jak pulpit.

3. Na wstążce kliknij **kartę Deweloper.**

    > [!NOTE]
    > Jeśli karta **Deweloper** nie jest widoczna, należy ją najpierw wyświetlić. Aby uzyskać więcej informacji, [zobacz Jak: pokazywać kartę dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W grupie **Kod** kliknij pozycję **Visual Basic**.

     Zostanie Edytor Visual Basic.

5. W **oknie Projekt** kliknij dwukrotnie pozycję **ThisWorkbook.**

     Zostanie otwarty plik kodu `ThisWorkbook` dla obiektu .

6. Dodaj następujący kod VBA do pliku kodu. Ten kod najpierw pobiera obiekt COMAddIn reprezentujący dodatek **ExcelImportData** VSTO. Następnie kod używa właściwości Object obiektu COMAddIn do wywołania `ImportData` metody .

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. Naciśnij klawisz **F5**.

8. Sprawdź, czy do **skoroszytu** dodano nowy importowany arkusz danych. Sprawdź również, czy komórka A1 zawiera ciąg **To są moje dane**.

9. Zamknij program Excel.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat programowania dodatków VSTO można znaleźć w tych tematach:

- Użyj klasy `ThisAddIn` , aby zautomatyzować aplikację hosta i wykonać inne zadania w projektach dodatków VSTO. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md)

- Tworzenie niestandardowego okienka zadań w dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań i](../vsto/custom-task-panes.md) Jak dodać niestandardowe okienko zadań do [aplikacji.](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

- Dostosowywanie wstążki w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md) i [Jak rozpocząć dostosowywanie wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

## <a name="see-also"></a>Zobacz też
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Wywołanie kodu w dodatki VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
