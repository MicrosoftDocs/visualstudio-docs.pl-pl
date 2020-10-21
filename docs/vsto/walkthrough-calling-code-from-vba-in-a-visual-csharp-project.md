---
title: 'Przewodnik: wywoływanie kodu z VBA w projekcie Visual C#'
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
ms.openlocfilehash: 1c089a3156d005da7d49976f6c96bb10daac0662
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "92297945"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Przewodnik: wywoływanie kodu z VBA w projekcie Visual C#
  W tym instruktażu pokazano, jak wywołać metodę w dostosowaniu na poziomie dokumentu dla Microsoft Office Excel z kodu Visual Basic for Applications (VBA) w skoroszycie. Procedura obejmuje trzy podstawowe kroki: Dodaj metodę do `Sheet1` klasy Item hosta, Uwidocznij metodę w kodzie VBA w skoroszycie, a następnie Wywołaj metodę z kodu VBA w skoroszycie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Mimo że ten przewodnik korzysta z programu Excel, koncepcje przedstawione w tym przewodniku dotyczą również projektów na poziomie dokumentu dla programu Word.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie skoroszytu zawierającego kod języka VBA.

- Ufanie lokalizacji skoroszytu przy użyciu Centrum zaufania w programie Excel.

- Dodawanie metody do `Sheet1` klasy elementu hosta.

- Wyodrębnianie interfejsu dla `Sheet1` klasy elementów hosta.

- Udostępnianie metody do kodu VBA.

- Wywoływanie metody z kodu VBA.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>Utwórz skoroszyt zawierający kod języka VBA
 Pierwszym krokiem jest utworzenie skoroszytu z obsługą makr zawierającego proste makro języka VBA. Aby można było uwidocznić kod w dostosowaniu do języka VBA, skoroszyt musi już zawierać kod języka VBA. W przeciwnym razie program Visual Studio nie może zmodyfikować projektu VBA, aby umożliwić wywoływanie kodu VBA w zestawie dostosowywania.

 Jeśli masz już skoroszyt zawierający kod języka VBA, którego chcesz użyć, możesz pominąć ten krok.

### <a name="to-create-a-workbook-that-contains-vba-code"></a>Aby utworzyć skoroszyt zawierający kod języka VBA

1. Uruchom program Excel.

2. Zapisz aktywny dokument jako **skoroszyt programu Excel Macro-Enabled ( \* xlsm)** o nazwie **WorkbookWithVBA**. Zapisz go w dogodnej lokalizacji, na przykład na pulpicie.

3. Na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W grupie **kod** kliknij przycisk **Visual Basic**.

     Zostanie otwarty Edytor Visual Basic.

5. W oknie **projektu** kliknij dwukrotnie pozycję **ThisWorkbook**.

     Plik kodu dla `ThisWorkbook` obiektu zostanie otwarty.

6. Dodaj następujący kod języka VBA do pliku kodu. Ten kod definiuje prostą funkcję, która nic nie robi. Jedynym celem tej funkcji jest upewnienie się, że projekt VBA istnieje w skoroszycie. Jest to wymagane do wykonania kolejnych kroków w tym instruktażu.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Zapisz dokument i Zamknij program Excel.

## <a name="create-the-project"></a>Tworzenie projektu
 Teraz można utworzyć projekt na poziomie dokumentu dla programu Excel, który używa wcześniej utworzonego skoroszytu z obsługą makr.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku szablony rozwiń pozycję **Visual C#**, a następnie rozwiń węzeł **Office/SharePoint**.

4. Wybierz węzeł **Dodatki pakietu Office** .

5. Na liście szablonów projektu wybierz **skoroszyt programu excel 2010** lub projekt **skoroszytu programu Excel 2013** .

6. W polu **Nazwa** wpisz **CallingCodeFromVBA**.

7. Kliknij przycisk **OK**.

     Zostanie otwarty **kreator Visual Studio Tools dla programu Office Project** .

8. Wybierz pozycję **Kopiuj istniejący dokument**, a następnie w polu **pełna ścieżka istniejącego dokumentu** Określ lokalizację skoroszytu **WorkbookWithVBA** , który został utworzony wcześniej. Jeśli używasz własnego skoroszytu z obsługą makr, zamiast tego Określ lokalizację tego skoroszytu.

9. Kliknij przycisk **Finish** (Zakończ).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera skoroszyt **WorkbookWithVBA** w Projektancie i dodaje projekt **CallingCodeFromVBA** do **Eksplorator rozwiązań**.

## <a name="trust-the-location-of-the-workbook"></a>Ufaj lokalizacji skoroszytu
 Zanim będzie można uwidocznić kod w rozwiązaniu w kodzie VBA w skoroszycie, musisz ufać VBA w skoroszycie do uruchomienia. Może to być realizowane na kilka sposobów. W tym instruktażu należy wykonać to zadanie, ufając lokalizację skoroszytu w **Centrum zaufania** w programie Excel.

### <a name="to-trust-the-location-of-the-workbook"></a>Aby zaufać lokalizacji skoroszytu

1. Uruchom program Excel.

2. Kliknij kartę **plik** .

3. Kliknij przycisk **Opcje programu Excel** .

4. W okienku kategorie kliknij pozycję **Centrum zaufania**.

5. W okienku szczegółów kliknij pozycję **Ustawienia Centrum zaufania**.

6. W okienku kategorie kliknij pozycję **Zaufane lokalizacje**.

7. W okienku szczegółów kliknij pozycję **Dodaj nową lokalizację**.

8. W oknie dialogowym **Microsoft Office zaufanej lokalizacji** przejdź do folderu, który zawiera projekt **CallingCodeFromVBA** .

9. Wybrane **podfoldery tej lokalizacji również są zaufane**.

10. W oknie dialogowym **Microsoft Office zaufanej lokalizacji** kliknij przycisk **OK**.

11. W oknie dialogowym **Centrum zaufania** kliknij przycisk **OK**.

12. W oknie dialogowym **Opcje programu Excel** kliknij przycisk **OK**.

13. Zamknij **program Excel**.

## <a name="add-a-method-to-the-sheet1-class"></a>Dodawanie metody do klasy Arkusz1
 Po skonfigurowaniu projektu VBA należy dodać metodę publiczną do `Sheet1` klasy elementu hosta, która może być wywoływana z kodu VBA.

### <a name="to-add-a-method-to-the-sheet1-class"></a>Aby dodać metodę do klasy Arkusz1

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Sheet1.cs**, a następnie kliknij pozycję **Wyświetl kod**.

     Plik **Sheet1.cs** zostanie otwarty w edytorze kodu.

2. Dodaj poniższy kod do klasy `Sheet1`. `CreateVstoNamedRange`Metoda tworzy nowy <xref:Microsoft.Office.Tools.Excel.NamedRange> obiekt w określonym zakresie. Ta metoda tworzy również procedurę obsługi zdarzeń dla <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> zdarzenia <xref:Microsoft.Office.Tools.Excel.NamedRange> . W dalszej części tego instruktażu zostanie wywołana `CreateVstoNamedRange` Metoda z kodu VBA w dokumencie.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]

3. Dodaj następującą metodę do `Sheet1` klasy. Ta metoda przesłania <xref:Microsoft.Office.Tools.Excel.WorksheetBase.GetAutomationObject%2A> metodę w celu zwrócenia bieżącego wystąpienia `Sheet1` klasy.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]

4. Zastosuj następujące atrybuty przed pierwszym wierszem `Sheet1` deklaracji klasy. Te atrybuty sprawiają, że Klasa jest widoczna dla modelu COM, ale bez generowania interfejsu klasy.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]

## <a name="extract-an-interface-for-the-sheet1-class"></a>Wyodrębnij interfejs dla klasy Arkusz1
 Aby można było uwidocznić `CreateVstoNamedRange` metodę w kodzie VBA, należy utworzyć interfejs publiczny, który definiuje tę metodę, i należy uwidocznić ten interfejs w modelu com.

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Aby wyodrębnić interfejs dla klasy Arkusz1

1. W pliku kodu **Sheet1.cs** kliknij dowolne miejsce w `Sheet1` klasie.

2. W menu **refaktoryzacji** kliknij pozycję **Wyodrębnij interfejs**.

3. W oknie dialogowym **wyodrębnianie interfejsu** w polu **Wybierz publiczny element członkowski do interfejsu formularza** kliknij wpis dla `CreateVstoNamedRange` metody.

4. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] generuje nowy interfejs o nazwie `ISheet1` i modyfikuje definicję `Sheet1` klasy, tak aby implementuje `ISheet1` interfejs. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera również plik **ISheet1.cs** w edytorze kodu.

5. W pliku **ISheet1.cs** Zastąp `ISheet1` deklarację interfejsu następującym kodem. Ten kod udostępnia `ISheet1` interfejs publiczny i stosuje <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut, aby był widoczny dla interfejsu com.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]

6. Skompiluj projekt.

## <a name="expose-the-method-to-vba-code"></a>Uwidacznianie metody w kodzie VBA
 Aby udostępnić `CreateVstoNamedRange` metodę do kodu VBA w skoroszycie, ustaw właściwość **ReferenceAssemblyFromVbaProject** dla `Sheet1` elementu hosta na **wartość true**.

### <a name="to-expose-the-method-to-vba-code"></a>Aby udostępnić metodę do kodu VBA

1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **Sheet1.cs**.

     Plik **WorkbookWithVBA** zostanie otwarty w projektancie, a obszar Arkusz1 widoczny.

2. W oknie **Właściwości** wybierz właściwość **ReferenceAssemblyFromVbaProject** i zmień wartość na **true**.

3. Kliknij przycisk **OK** w wyświetlonym komunikacie.

4. Skompiluj projekt.

## <a name="call-the-method-from-vba-code"></a>Wywoływanie metody z kodu VBA
 Teraz można wywołać `CreateVstoNamedRange` metodę z kodu VBA w skoroszycie.

> [!NOTE]
> W tym instruktażu dodasz kod VBA do skoroszytu podczas debugowania projektu. Kod VBA dodany do tego dokumentu zostanie zastąpiony przy następnym skompilowaniu projektu, ponieważ program Visual Studio zastępuje dokument w folderze danych wyjściowych kompilacji kopią dokumentu z głównego folderu projektu. Jeśli chcesz zapisać kod VBA, możesz skopiować go do dokumentu w folderze projektu. Aby uzyskać więcej informacji, zobacz [łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>Aby wywołać metodę z kodu VBA

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Na karcie **deweloper** w grupie **kod** kliknij przycisk **Visual Basic**.

     Zostanie otwarty Edytor Visual Basic.

3. W menu **Wstaw** kliknij pozycję **moduł**.

4. Dodaj następujący kod do nowego modułu.

     Ten kod wywołuje `CreateTable` metodę w zestawie dostosowywania. Makro uzyskuje dostęp do tej metody przy użyciu `GetManagedClass` metody globalnej w celu uzyskania dostępu do `Sheet1` klasy elementu hosta, która została udostępniona do kodu VBA. `GetManagedClass`Metoda została wygenerowana automatycznie po ustawieniu właściwości **ReferenceAssemblyFromVbaProject** wcześniej w tym instruktażu.

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. Naciśnij klawisz **F5**.

6. W otwartym skoroszycie kliknij komórkę **a1** w **arkuszu Arkusz1**. Sprawdź, czy pojawi się okno komunikatu.

7. Zamknij program Excel bez zapisywania zmian.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat wywoływania kodu w rozwiązaniach pakietu Office z poziomu języka VBA można znaleźć w następujących tematach:

- Wywoływanie kodu w elemencie hosta w Visual Basic dostosowania z poziomu języka VBA. Ten proces różni się od procesu Visual C#. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywoływanie kodu z VBA w projekcie Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).

- Wywoływanie kodu w dodatku VSTO z poziomu języka VBA. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Zobacz też
- [Łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: Uwidacznianie kodu w języku VBA w projekcie Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Instrukcje: Uwidacznianie kodu w języku VBA w projekcie programu Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Przewodnik: wywoływanie kodu z VBA w projekcie Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
