---
title: 'Przewodnik: wywołanie kodu z VBA w projekcie Visual C#'
description: Dowiedz się, jak wywołać metodę w dostosowywaniu na poziomie dokumentu dla programu Microsoft Excel z Visual Basic for Applications (VBA) w skoroszycie.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 260872096f36f91a2618f636e297d3c48b3fe51b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824474"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Przewodnik: wywołanie kodu z VBA w projekcie Visual C#
  W tym przewodniku pokazano, jak wywołać metodę w dostosowywaniu na poziomie dokumentu dla programu Microsoft Office Excel z Visual Basic for Applications (VBA) w skoroszycie. Procedura obejmuje trzy podstawowe kroki: dodanie metody do klasy elementu hosta, uwidoczninie metody kodowi VBA w skoroszycie, a następnie wywołanie metody z kodu VBA w `Sheet1` skoroszycie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Chociaż w tym przewodniku jest używany program Excel, koncepcje zademonstrowane w tym przewodniku mają również zastosowanie do projektów na poziomie dokumentu dla programu Word.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie skoroszytu zawierającego kod VBA.

- Ufanie lokalizacji skoroszytu przy użyciu Centrum zaufania w programie Excel.

- Dodanie metody do `Sheet1` klasy elementu hosta.

- Wyodrębnianie interfejsu dla `Sheet1` klasy elementu hosta.

- Udostępnianie metody kodowi VBA.

- Wywoływanie metody z kodu VBA.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>Tworzenie skoroszytu zawierającego kod VBA
 Pierwszym krokiem jest utworzenie skoroszytu z włączoną obsługą makr, który zawiera proste makro VBA. Aby można było uwidocznić kod w dostosowywaniu dla VBA, skoroszyt musi już zawierać kod VBA. W przeciwnym Visual Studio nie można zmodyfikować projektu VBA, aby umożliwić kodowi VBA wywołanie do zestawu dostosowywania.

 Jeśli masz już skoroszyt zawierający kod VBA, którego chcesz użyć, możesz pominąć ten krok.

### <a name="to-create-a-workbook-that-contains-vba-code"></a>Aby utworzyć skoroszyt zawierający kod VBA

1. Uruchom program Excel.

2. Zapisz aktywny dokument jako skoroszyt programu **Excel Macro-Enabled \* (xlsm)** o nazwie **WorkbookWithVBA.** Zapisz go w dogodnym miejscu, takim jak pulpit.

3. Na wstążce kliknij **kartę Deweloper.**

    > [!NOTE]
    > Jeśli karta **Deweloper** nie jest widoczna, musisz ją najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz How to: Show the developer tab on the ribbon (Jak [wyświetlić kartę dewelopera na wstążce).](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. W grupie **Kod** kliknij pozycję **Visual Basic**.

     Zostanie Edytor Visual Basic.

5. W **oknie Projekt** kliknij dwukrotnie pozycję **ThisWorkbook.**

     Zostanie otwarty plik kodu `ThisWorkbook` dla obiektu .

6. Dodaj następujący kod VBA do pliku kodu. Ten kod definiuje prostą funkcję, która nic nie robi. Jedynym celem tej funkcji jest zapewnienie, że projekt VBA istnieje w skoroszycie. Jest to wymagane w kolejnych krokach tego przewodnika.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Zapisz dokument i zamknij program Excel.

## <a name="create-the-project"></a>Tworzenie projektu
 Teraz możesz utworzyć projekt na poziomie dokumentu dla programu Excel, który używa utworzonego wcześniej skoroszytu z włączoną obsługą makr.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

3. W okienku szablonów rozwiń **pozycję Visual C#**, a następnie **rozwiń pozycję Office/SharePoint.**

4. Wybierz węzeł **Dodatki pakietu Office.**

5. Na liście szablonów projektów wybierz projekt Skoroszyt programu **Excel 2010** **lub Skoroszyt programu Excel 2013.**

6. W polu **Nazwa** wpisz **CallingCodeFromVBA.**

7. Kliknij przycisk **OK**.

     Zostanie **Visual Studio Tools kreatora projektu pakietu Office.**

8. Wybierz **pozycję Kopiuj istniejący dokument**  i w polu Pełna ścieżka istniejącego dokumentu określ lokalizację utworzonego wcześniej skoroszytu **WorkbookWithVBA.** Jeśli używasz własnego skoroszytu z włączoną obsługą makr, określ lokalizację tego skoroszytu.

9. Kliknij przycisk **Finish** (Zakończ).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera skoroszyt **WorkbookWithVBA** w projektancie i dodaje projekt **CallingCodeFromVBA** do **Eksplorator rozwiązań**.

## <a name="trust-the-location-of-the-workbook"></a>Ufaj lokalizacji skoroszytu
 Aby można było uwidocznić kod w rozwiązaniu dla kodu VBA w skoroszycie, musisz ufać VBA w skoroszycie, aby go uruchomić. Może to być realizowane na kilka sposobów. W tym przewodniku to zadanie zostanie zrealizowane przez ufanie lokalizacji skoroszytu w Centrum zaufania w **programie** Excel.

### <a name="to-trust-the-location-of-the-workbook"></a>Ufanie lokalizacji skoroszytu

1. Uruchom program Excel.

2. Kliknij **kartę** Plik.

3. Kliknij przycisk **Opcje programu Excel.**

4. W okienku kategorii kliknij pozycję **Centrum zaufania.**

5. W okienku szczegółów kliknij pozycję **Ustawienia Centrum zaufania.**

6. W okienku kategorii kliknij pozycję **Zaufane lokalizacje.**

7. W okienku szczegółów kliknij pozycję **Dodaj nową lokalizację.**

8. W **oknie dialogowym Microsoft Office Trusted Location** (Zaufana lokalizacja) przejdź do folderu zawierającego projekt **CallingCodeFromVBA.**

9. Wybierz **podfoldery tej lokalizacji są również zaufane.**

10. W **oknie Microsoft Office zaufanej** lokalizacji kliknij przycisk **OK.**

11. W **oknie dialogowym Centrum** zaufania kliknij przycisk **OK.**

12. W **oknie dialogowym Opcje** programu Excel kliknij przycisk **OK.**

13. Zamknij **program Excel.**

## <a name="add-a-method-to-the-sheet1-class"></a>Dodawanie metody do klasy Sheet1
 Po skonfigurowaniu projektu VBA dodaj publiczną metodę do klasy elementów hosta, która można wywołać `Sheet1` z kodu VBA.

### <a name="to-add-a-method-to-the-sheet1-class"></a>Aby dodać metodę do klasy Sheet1

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję Sheet1.cs,** a następnie kliknij **polecenie Wyświetl kod.**

     Plik **Sheet1.cs** zostanie otwarty w Edytorze kodu.

2. Dodaj poniższy kod do klasy `Sheet1`. Metoda `CreateVstoNamedRange` tworzy nowy obiekt w określonym <xref:Microsoft.Office.Tools.Excel.NamedRange> zakresie. Ta metoda tworzy również program obsługi zdarzeń <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> dla zdarzenia <xref:Microsoft.Office.Tools.Excel.NamedRange> . W dalszej części tego przewodnika wywołasz metodę `CreateVstoNamedRange` z kodu VBA w dokumencie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet2":::

3. Dodaj następującą metodę do `Sheet1` klasy . Ta metoda zastępuje <xref:Microsoft.Office.Tools.Excel.WorksheetBase.GetAutomationObject%2A> metodę w celu zwrócenia bieżącego wystąpienia `Sheet1` klasy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet3":::

4. Zastosuj następujące atrybuty przed pierwszym wierszem deklaracji `Sheet1` klasy. Te atrybuty sprawiają, że klasa jest widoczna dla com, ale bez generowania interfejsu klasy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet1":::

## <a name="extract-an-interface-for-the-sheet1-class"></a>Wyodrębnianie interfejsu dla klasy Sheet1
 Aby można było uwidocznić metodę w kodzie VBA, należy utworzyć interfejs publiczny definiujący tę metodę i uwidocznić ten interfejs dla `CreateVstoNamedRange` com.

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Aby wyodrębnić interfejs dla klasy Sheet1

1. W pliku **kodu Sheet1.cs** kliknij dowolne miejsce w `Sheet1` klasie .

2. W menu **Refaktoryzacja** kliknij pozycję **Wyodrębnij interfejs.**

3. W **oknie dialogowym** Wyodrębnij interfejs w polu **Wybierz publiczne** elementy członkowskie do formularza kliknij wpis `CreateVstoNamedRange` metody .

4. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Generuje nowy interfejs o nazwie i modyfikuje definicję klasy tak, aby `ISheet1` `Sheet1` implementował `ISheet1` interfejs. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Spowoduje to również **otwarcie pliku ISheet1.cs** w Edytorze kodu.

5. W pliku **ISheet1.cs** zastąp deklarację `ISheet1` interfejsu następującym kodem. Ten kod `ISheet1` sprawia, że interfejs jest publiczny i stosuje atrybut , <xref:System.Runtime.InteropServices.ComVisibleAttribute> aby interfejs był widoczny dla com.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs" id="Snippet4":::

6. Skompiluj projekt.

## <a name="expose-the-method-to-vba-code"></a>Uwidocznij metodę kodowi VBA
 Aby uwidocznić metodę kodowi VBA w skoroszycie, ustaw właściwość `CreateVstoNamedRange` **ReferenceAssemblyFromVbaProject** elementu hosta `Sheet1` na wartość **True**.

### <a name="to-expose-the-method-to-vba-code"></a>Aby uwidocznić metodę dla kodu VBA

1. W **Eksplorator rozwiązań** kliknij dwukrotnie **pozycję Sheet1.cs.**

     Plik **WorkbookWithVBA** zostanie otwarty w projektancie z widocznym arkuszem Sheet1.

2. W **oknie** Właściwości wybierz właściwość **ReferenceAssemblyFromVbaProject** i zmień wartość na **True.**

3. Kliknij **przycisk OK** w wyświetlonym komunikacie.

4. Skompiluj projekt.

## <a name="call-the-method-from-vba-code"></a>Wywołanie metody z kodu VBA
 Teraz możesz wywołać metodę `CreateVstoNamedRange` z kodu VBA w skoroszycie.

> [!NOTE]
> W tym przewodniku dodasz kod VBA do skoroszytu podczas debugowania projektu. Kod VBA, który dodasz do tego dokumentu, zostanie zastąpiony przy następnej kompilacji projektu, ponieważ program Visual Studio zastąpi dokument w folderze danych wyjściowych kompilacji kopią dokumentu z głównego folderu projektu. Jeśli chcesz zapisać kod VBA, możesz skopiować go do dokumentu w folderze projektu. Aby uzyskać więcej informacji, zobacz Łączenie dostosowań na poziomie dokumentu i [VBA.](../vsto/combining-vba-and-document-level-customizations.md)

### <a name="to-call-the-method-from-vba-code"></a>Aby wywołać metodę z kodu VBA

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Na karcie **Deweloper** w grupie **Kod** kliknij pozycję **Visual Basic**.

     Zostanie Edytor Visual Basic.

3. W menu **Wstaw** kliknij pozycję **Moduł**.

4. Dodaj następujący kod do nowego modułu.

     Ten kod wywołuje `CreateTable` metodę w zestawie dostosowywania. Makro uzyskuje dostęp do tej metody przy użyciu metody globalnej w celu uzyskania dostępu do klasy elementu hosta, `GetManagedClass` `Sheet1` która została ujawniona w kodzie VBA. Metoda została wygenerowana automatycznie podczas ustawienia właściwości `GetManagedClass` **ReferenceAssemblyFromVbaProject** wcześniej w tym przewodniku.

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. Naciśnij klawisz **F5**.

6. W otwartym skoroszycie kliknij **komórkę A1** w **arkuszu Arkusz1.** Sprawdź, czy zostanie wyświetlone okno komunikatu.

7. Zamknij program Excel bez zapisywania zmian.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat wywoływania kodu w rozwiązaniach pakietu Office z VBA można znaleźć w tych tematach:

- Wywołaj kod w pozycji hosta w pliku Visual Basic dostosowania z VBA. Ten proces różni się od procesu Visual C#. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywołanie kodu z VBA w Visual Basic projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).

- Wywołaj kod w dodatku VSTO z VBA. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywołanie kodu w dodatku VSTO z VBA.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

## <a name="see-also"></a>Zobacz też
- [Łączenie dostosowań na poziomie dokumentu i VBA](../vsto/combining-vba-and-document-level-customizations.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [How to: Expose Code to VBA in a Visual Basic project (Jak uwidocznić kod vBA w Visual Basic projektu)](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [How to: Expose Code to VBA in a Visual C&#35; project (Jak uwidocznić kod vBA w projekcie visual C)](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Przewodnik: wywołanie kodu z VBA w Visual Basic projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
