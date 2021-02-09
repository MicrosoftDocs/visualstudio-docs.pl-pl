---
title: 'Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA'
description: Dowiedz się, jak uwidocznić obiekt w dodatku VSTO do innych rozwiązań Microsoft Office, w tym Visual Basic for Applications (VBA) i dodatków VSTO dla modelu COM.
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
ms.openlocfilehash: 61e729113ecfa988f424e2182662d506377d33e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882391"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA
  W tym instruktażu pokazano, jak uwidocznić obiekt w dodatku narzędzi VSTO do innych rozwiązań Microsoft Office, w tym Visual Basic for Applications (VBA) i dodatków VSTO dla modelu COM.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Chociaż ten Instruktaż korzysta z programu Excel, koncepcje przedstawione w tym przewodniku dotyczą dowolnego szablonu projektu dodatku VSTO dostarczonego przez program Visual Studio.

 W instruktażu przedstawiono następujące zagadnienia:

- Definiowanie klasy, która może być narażona na inne rozwiązania pakietu Office.

- Udostępnianie klasy innym rozwiązań pakietu Office.

- Wywoływanie metody klasy z kodu VBA.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>Utwórz projekt dodatku VSTO
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku VSTO programu Excel o nazwie **ExcelImportData** przy użyciu szablonu projektu dodatku programu Excel VSTO. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera plik kodu **ThisAddIn.cs** lub **ThisAddIn. vb** i dodaje projekt **ExcelImportData** do **Eksplorator rozwiązań**.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definiowanie klasy, którą można uwidocznić dla innych rozwiązań pakietu Office
 Celem tego instruktażu jest wywołanie `ImportData` metody klasy o nazwie `AddInUtilities` w dodatku VSTO z kodu VBA. Ta metoda zapisuje ciąg w komórce A1 aktywnego arkusza.

 Aby uwidocznić `AddInUtilities` klasę dla innych rozwiązań pakietu Office, należy uczynić klasę publiczną i widoczną dla modelu com. Należy również uwidocznić Interfejs [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) w klasie. Kod w poniższej procedurze pokazuje jeden ze sposobów spełniania tych wymagań. Aby uzyskać więcej informacji, zobacz [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Aby zdefiniować klasę, którą można uwidocznić dla innych rozwiązań pakietu Office

1. W menu **projekt** kliknij polecenie **Dodaj klasę**.

2. W oknie dialogowym **Dodaj nowy element** Zmień nazwę nowej klasy na **AddInUtilities**, a następnie kliknij przycisk **Dodaj**.

     Plik **AddInUtilities.cs** lub **AddInUtilities. vb** zostanie otwarty w edytorze kodu.

3. Dodaj następujące dyrektywy na początku pliku.

     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]

4. Zastąp `AddInUtilities` klasę poniższym kodem.

     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

     Ten kod sprawia `AddInUtilities` , że Klasa jest widoczna dla modelu COM i dodaje `ImportData` metodę do klasy. Aby uwidocznić Interfejs [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) , `AddInUtilities` Klasa ma także <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut i implementuje interfejs, który jest widoczny dla modelu com.

## <a name="expose-the-class-to-other-office-solutions"></a>Uwidacznianie klasy innym rozwiązań pakietu Office
 Aby uwidocznić `AddInUtilities` klasę w innych rozwiązaniach pakietu Office, Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodę w `ThisAddIn` klasie. W zastąpieniu Zwróć wystąpienie `AddInUtilities` klasy.

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Aby uwidocznić klasę AddInUtilities w innych rozwiązaniach pakietu Office

1. W **Eksplorator rozwiązań** rozwiń węzeł **Excel**.

2. Kliknij prawym przyciskiem myszy pozycję **ThisAddIn.cs** lub **ThisAddIn. vb**, a następnie kliknij polecenie **Wyświetl kod**.

3. Dodaj poniższy kod do klasy `ThisAddIn`.

     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

4. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Sprawdź, czy rozwiązanie nie ma błędów.

## <a name="test-the-vsto-add-in"></a>Testowanie dodatku VSTO
 Można wywołać `AddInUtilities` klasy z kilku różnych typów rozwiązań pakietu Office. W tym instruktażu zostanie użyty kod języka VBA w skoroszycie programu Excel. Aby uzyskać więcej informacji o innych typach rozwiązań pakietu Office, których można również użyć, zobacz [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. W programie Excel Zapisz aktywny skoroszyt jako skoroszyt programu Excel Macro-Enabled (*. xlsm). Zapisz ją w wygodnej lokalizacji, na przykład na pulpicie.

3. Na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W grupie **kod** kliknij przycisk **Visual Basic**.

     Zostanie otwarty Edytor Visual Basic.

5. W oknie **projektu** kliknij dwukrotnie pozycję **ThisWorkbook**.

     Plik kodu dla `ThisWorkbook` obiektu zostanie otwarty.

6. Dodaj następujący kod języka VBA do pliku kodu. Ten kod najpierw pobiera obiekt COMAddIn, który reprezentuje dodatek VSTO **ExcelImportData** . Następnie kod używa właściwości Object obiektu COMAddIn, aby wywołać `ImportData` metodę.

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

8. Sprawdź, czy nowy **zaimportowany arkusz danych** został dodany do skoroszytu. Sprawdź również, czy komórka a1 zawiera ciąg, który to **są moje dane**.

9. Zamknij program Excel.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji o programowaniu dodatków VSTO można znaleźć w następujących tematach:

- Użyj `ThisAddIn` klasy do automatyzowania aplikacji hosta i wykonywania innych zadań w projektach dodatku VSTO. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

- Utwórz niestandardowe okienko zadań w dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md) i [instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

- Dostosuj Wstążkę w dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md) i [instrukcje: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

## <a name="see-also"></a>Zobacz też
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
