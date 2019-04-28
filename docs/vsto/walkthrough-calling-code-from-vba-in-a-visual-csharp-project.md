---
title: 'Przewodnik: Wywoływanie kodu z VBA w wizualizacji C# projektu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46f88b47e135331e5f1dc010aa4a73abed520f51
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438655"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Przewodnik: Wywoływanie kodu z VBA w wizualizacji C# projektu
  W tym instruktażu przedstawiono sposób wywołania metody w dostosowaniu na poziomie dokumentu dla programu Microsoft Office Excel z Visual Basic for Applications (VBA) kod w skoroszycie. Procedura obejmuje trzy podstawowe kroki: Dodaj metodę, która `Sheet1` hosta klasa elementu, ujawnia metody dla kodu VBA w skoroszycie i następnie wywołaj metodę z kodu VBA w skoroszycie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Mimo że program Excel jest wykorzystywany w tym przewodniku szczegółowo, koncepcje dowodzą Instruktaż mają również zastosowanie do projektów na poziomie dokumentu dla programu Word.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie skoroszytu, który zawiera kod VBA.

- Ufanie lokalizacji skoroszytu przy użyciu Centrum zaufania w programie Excel.

- Dodawanie metody do `Sheet1` hosta klasy elementu.

- Wyodrębnianie interfejsu `Sheet1` hosta klasy elementu.

- Udostępnia metody dla kodu VBA.

- Wywołanie metody z kodu VBA.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Program Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>Utwórz skoroszyt, który zawiera kod VBA
 Pierwszym krokiem jest w celu utworzenia skoroszytu z włączoną obsługą makr, zawierający prostą makro VBA. Zanim udostępnisz kodu w VBA dostosowanie, skoroszyt musi już zawierać kod VBA. W przeciwnym razie program Visual Studio nie można zmodyfikować projekt VBA w celu włączenia kodu VBA w celu wywołania do zestawu dostosowywania.

 Jeśli masz już skoroszytu, który zawiera kod VBA, którego chcesz użyć, możesz pominąć ten krok.

### <a name="to-create-a-workbook-that-contains-vba-code"></a>Aby utworzyć skoroszyt, który zawiera kod VBA

1. Uruchom program Excel.

2. Zapisz aktywny dokument jako **Excel Macro-Enabled skoroszytu (\*xlsm)** o nazwie **WorkbookWithVBA**. Zapisz go w dogodnym miejscu, na przykład na pulpit.

3. Na wstążce kliknij **Developer** kartę.

    > [!NOTE]
    > Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W **kodu** grupy, kliknij przycisk **języka Visual Basic**.

     Zostanie otwarty Edytor kodu języka Visual Basic.

5. W **projektu** okna, kliknij dwukrotnie **ThisWorkbook**.

     Plik kodu dla `ThisWorkbook` obiektu zostanie otwarta.

6. Dodaj następujący kod VBA do pliku kodu. Ten kod definiuje prosty funkcja, która nie wykonuje żadnych działań. Jest jedynym celem tej funkcji, aby upewnić się, że projekt VBA istnieje w skoroszycie. Jest to wymagane do wykonania kolejnych kroków tego przewodnika.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Zapisz dokument i zamknij program Excel.

## <a name="create-the-project"></a>Utwórz projekt
 Teraz możesz utworzyć projekt na poziomie dokumentu dla programu Excel, który korzysta z włączoną obsługą makr skoroszytu, która została utworzona wcześniej.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

3. W okienku szablonów, rozwiń **Visual C#**, a następnie rozwiń węzeł **Office/SharePoint**.

4. Wybierz **dodatków pakietu Office** węzła.

5. Na liście szablonów projektu wybierz **skoroszyt programu Excel 2010** lub **skoroszytu programu Excel 2013** projektu.

6. W **nazwa** wpisz **CallingCodeFromVBA**.

7. Kliknij przycisk **OK**.

     **Visual Studio Tools dla pakietu Office, Kreator projektu** zostanie otwarty.

8. Wybierz **Kopiuj istniejący dokument**, a następnie w **Pełna ścieżka istniejącego dokumentu** należy określić lokalizację **WorkbookWithVBA** skoroszytu, który został utworzony wcześniej . Jeśli używasz własny skoroszyt z włączoną obsługą makr, należy określić lokalizację tego skoroszytu.

9. Kliknij przycisk **Zakończ**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **WorkbookWithVBA** skoroszytu w Projektancie i dodaje **CallingCodeFromVBA** projekt **Eksploratora rozwiązań**.

## <a name="trust-the-location-of-the-workbook"></a>Zaufanie do lokalizacji, skoroszytu
 Zanim za udostępnianie kodu w rozwiązaniu dla kodu VBA w skoroszycie, muszą ufać VBA w skoroszycie, aby uruchomić. Istnieje kilka sposobów, aby to zrobić. W tym przewodniku będzie wykonać to zadanie przez zaufanie do lokalizacji skoroszytu w **Centrum zaufania** w programie Excel.

### <a name="to-trust-the-location-of-the-workbook"></a>Aby zaufać lokalizacji skoroszytu

1. Uruchom program Excel.

2. Kliknij przycisk **pliku** kartę.

3. Kliknij przycisk **opcje programu Excel** przycisku.

4. W okienku kategorii kliknij **Centrum zaufania**.

5. W okienku szczegółów kliknij **ustawienia Centrum zaufania**.

6. W okienku kategorii kliknij **zaufane lokalizacje**.

7. W okienku szczegółów kliknij **Dodaj nową lokalizację**.

8. W **Microsoft Office zaufanej lokalizacji** okno dialogowe, przejdź do folderu, który zawiera **CallingCodeFromVBA** projektu.

9. Wybierz **podfoldery tej lokalizacji są także zaufane**.

10. W **Microsoft Office zaufanej lokalizacji** okno dialogowe, kliknij przycisk **OK**.

11. W **Centrum zaufania** okno dialogowe, kliknij przycisk **OK**.

12. W **opcje programu Excel** okno dialogowe, kliknij przycisk **OK**.

13. Zakończ **Excel**.

## <a name="add-a-method-to-the-sheet1-class"></a>Dodawanie metody do Sheet1 — klasa
 Po skonfigurowaniu projektu VBA dodać metodę publiczną do `Sheet1` hosta klasa elementu, który można wywoływać z kodu VBA.

### <a name="to-add-a-method-to-the-sheet1-class"></a>Aby dodać metodę do klasy Arkusz1

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.cs**, a następnie kliknij przycisk **Wyświetl kod**.

     **Sheet1.cs** plik zostanie otwarty w edytorze kodu.

2. Dodaj następujący kod do `Sheet1` klasy. `CreateVstoNamedRange` Metoda tworzy nowy <xref:Microsoft.Office.Tools.Excel.NamedRange> obiektu w określonym zakresie. Ta metoda również tworzy program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> zdarzenia <xref:Microsoft.Office.Tools.Excel.NamedRange>. W dalszej części tego przewodnika, będzie wywoływać `CreateVstoNamedRange` metody z kodu VBA w dokumencie.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]

3. Dodaj następującą metodę do `Sheet1` klasy. Ta metoda zastępuje <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> metodę, aby powrócić do bieżącego wystąpienia `Sheet1` klasy.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]

4. Stosuje się następujące atrybuty przed pierwszym wierszem `Sheet1` deklaracji klasy. Te atrybuty widoczności klasy dla modelu COM, ale bez generowania interfejsu klasy.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]

## <a name="extract-an-interface-for-the-sheet1-class"></a>Wyodrębnij interfejs dla Sheet1 — klasa
 Aby udostępnić `CreateVstoNamedRange` metody dla kodu VBA, należy utworzyć publiczny interfejs, który definiuje tę metodę, i musi uwidaczniać tego interfejsu COM.

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Można wyodrębnić interfejsu Sheet1 — klasa

1. W **Sheet1.cs** plik kodu, kliknij w dowolnym miejscu `Sheet1` klasy.

2. Na **Refaktoryzuj** menu, kliknij przycisk **Wyodrębnij interfejs**.

3. W **Wyodrębnij interfejs** dialogowym **wybierz publiczne elementy członkowskie do interfejsu formularza** kliknij wpis dla `CreateVstoNamedRange` metody.

4. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] generuje nowy interfejs o nazwie `ISheet1`, oraz modyfikuje definicji `Sheet1` klasy tak, aby implementuje `ISheet1` interfejsu. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera również **ISheet1.cs** plik w edytorze kodu.

5. W **ISheet1.cs** pliku, Zastąp `ISheet1` interfejsu deklaracji z następującym kodem. Ten kod sprawia, że `ISheet1` interfejsu publicznego i są one stosowane <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutu, aby uwidocznić interfejsu COM.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]

6. Skompiluj projekt.

## <a name="expose-the-method-to-vba-code"></a>Ujawnia metody dla kodu VBA
 Do udostępnienia `CreateVstoNamedRange` metody dla kodu VBA w skoroszycie, ustawienie **ReferenceAssemblyFromVbaProject** właściwość `Sheet1` element hosta do **True**.

### <a name="to-expose-the-method-to-vba-code"></a>Aby udostępnić metody dla kodu VBA

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **Sheet1.cs**.

     **WorkbookWithVBA** plik zostanie otwarty w projektancie, za pomocą Arkusz1 widoczne.

2. W **właściwości** wybierz **ReferenceAssemblyFromVbaProject** właściwości i zmień wartość na **True**.

3. Kliknij przycisk **OK** wiadomości, która jest wyświetlana.

4. Skompiluj projekt.

## <a name="call-the-method-from-vba-code"></a>Wywołaj metodę z kodu VBA
 Teraz można wywołać `CreateVstoNamedRange` metody z kodu VBA w skoroszycie.

> [!NOTE]
> W tym przewodniku dodasz kod VBA w skoroszycie podczas debugowania projektu. Kod VBA dodawany do tego dokumentu zostaną zastąpione przy następnym uruchomieniu kompilacji projektu, ponieważ program Visual Studio zastępuje dokument w folderze wyjściowym kompilacji kopię dokumentu z folderu głównego projektu. Jeśli chcesz zapisać ten kod, skopiuj go do dokumentu w folderze projektu. Aby uzyskać więcej informacji, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>Aby wywołać metodę z kodu VBA

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Na **Developer** na karcie **kodu** grupy, kliknij przycisk **języka Visual Basic**.

     Zostanie otwarty Edytor kodu języka Visual Basic.

3. Na **Wstaw** menu, kliknij przycisk **modułu**.

4. Dodaj następujący kod do nowego modułu.

     Ten kod wywołuje `CreateTable` metody w zestawie dostosowywania. Makro uzyskuje dostęp do tej metody za pomocą globalnego `GetManagedClass` metody w celu uzyskania dostępu do `Sheet1` hosta klasa elementu, który jest udostępniana dla kodu VBA. `GetManagedClass` Metoda została wygenerowana automatycznie po ustawieniu **ReferenceAssemblyFromVbaProject** właściwości we wcześniejszej części tego przewodnika.

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. Naciśnij klawisz **F5**.

6. W skoroszycie, Otwórz, kliknij komórkę **A1** na **Arkusz1**. Sprawdź, czy pojawi się okno komunikatu.

7. Zamknij program Excel bez zapisywania zmian.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej informacji na temat wywoływanie kodu w rozwiązaniach pakietu Office z VBA w następujących tematach:

- Wywoływanie kodu w elemencie hosta w dostosowaniu języka Visual Basic z kodu VBA. Ten proces różni się od procesu Visual C#. Aby uzyskać więcej informacji, zobacz [instruktażu: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).

- Wywoływanie kodu w dodatku narzędzi VSTO z kodu VBA. Aby uzyskać więcej informacji, zobacz [instruktażu: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Zobacz także
- [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: Udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Instrukcje: Udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Przewodnik: Wywoływanie kodu z VBA w projektach Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
