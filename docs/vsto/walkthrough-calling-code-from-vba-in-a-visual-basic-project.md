---
title: 'Przewodnik: wywołanie kodu z VBA w Visual Basic projektu'
description: Dowiedz się, jak wywołać metodę w dostosowywaniu na poziomie dokumentu dla programu Microsoft Word z Visual Basic for Applications (VBA) w dokumencie.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f4fe056f70e0af03809b43d60968bd8a1a50bf08
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824487"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>Przewodnik: wywołanie kodu z VBA w Visual Basic projektu
  W tym przewodniku pokazano, jak wywołać metodę w dostosowywaniu na poziomie dokumentu dla programu Microsoft Office Word z Visual Basic for Applications (VBA) w dokumencie. Procedura obejmuje trzy podstawowe kroki: dodanie metody do klasy elementu hosta, uwidoczninie metody kodowi VBA, a następnie wywołanie metody z kodu `ThisDocument` VBA w dokumencie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Chociaż w tym przewodniku użyto programu Word, koncepcje zademonstrowane w tym przewodniku dotyczą również projektów na poziomie dokumentu dla programu Excel.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie dokumentu zawierającego kod VBA.

- Ufanie lokalizacji dokumentu przy użyciu Centrum zaufania w programie Word.

- Dodanie metody do `ThisDocument` klasy elementu hosta.

- Udostępnianie metody kodowi VBA.

- Wywoływanie metody z kodu VBA.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>Tworzenie dokumentu zawierającego kod VBA
 Pierwszym krokiem jest utworzenie dokumentu z włączoną obsługą makr, który zawiera proste makro VBA. Dokument musi zawierać projekt VBA przed utworzeniem projektu Visual Studio opartego na tym dokumencie. W przeciwnym Visual Studio nie można zmodyfikować projektu VBA, aby umożliwić kodowi VBA wywołanie do zestawu dostosowywania.

 Jeśli masz już dokument zawierający kod VBA, którego chcesz użyć, możesz pominąć ten krok.

### <a name="to-create-a-document-that-contains-vba-code"></a>Aby utworzyć dokument zawierający kod VBA

1. Uruchom program Word.

2. Zapisz aktywny dokument jako dokument z włączoną obsługą makr programu Word **\* (docm)** o nazwie **DocumentWithVBA.** Zapisz go w dogodnym miejscu, takim jak pulpit.

3. Na wstążce kliknij **kartę Deweloper.**

    > [!NOTE]
    > Jeśli karta **Deweloper** nie jest widoczna, musisz ją najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz How to: Show the developer tab on the ribbon (Jak [wyświetlić kartę dewelopera na wstążce).](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. W grupie **Kod** kliknij pozycję **Visual Basic**.

     Zostanie Edytor Visual Basic.

5. W **oknie Projekt** kliknij dwukrotnie pozycję **ThisDocument**.

     Zostanie otwarty plik kodu `ThisDocument` dla obiektu .

6. Dodaj następujący kod VBA do pliku kodu. Ten kod definiuje prostą funkcję, która nic nie robi. Jedynym celem tej funkcji jest zapewnienie, że projekt VBA istnieje w dokumencie. Jest to wymagane w kolejnych krokach tego przewodnika.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Zapisz dokument i zamknij program Word.

## <a name="create-the-project"></a>Tworzenie projektu
 Teraz możesz utworzyć projekt na poziomie dokumentu dla programu Word, który używa utworzonego wcześniej dokumentu z włączoną obsługą makr.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).** Jeśli twoje idee są ustawione do używania Visual Basic dewelopera, w menu **Plik** kliknij pozycję **Nowy projekt.**

3. W okienku szablonów rozwiń Visual Basic , **a** następnie **rozwiń pozycję Office/SharePoint.**

4. Wybierz węzeł **Dodatki pakietu Office.**

5. Na liście szablonów projektów wybierz projekt Dokument programu **Word 2010** lub **Dokument programu Word 2013.**

6. W polu **Nazwa** wpisz **CallingCodeFromVBA.**

7. Kliknij przycisk **OK**.

     Zostanie **Visual Studio Tools kreatora projektu pakietu Office.**

8. Wybierz **pozycję Kopiuj istniejący dokument**  i w polu Pełna ścieżka istniejącego dokumentu określ lokalizację utworzonego wcześniej dokumentu **DocumentWithVBA.** Jeśli używasz własnego dokumentu z włączoną obsługą makr, określ lokalizację tego dokumentu.

9. Kliknij przycisk **Finish** (Zakończ).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera dokument **DocumentWithVBA** w projektancie i dodaje projekt **CallingCodeFromVBA** **do** Eksplorator rozwiązań .

## <a name="trust-the-location-of-the-document"></a>Ufaj lokalizacji dokumentu
 Aby można było uwidocznić kod w rozwiązaniu dla kodu VBA w dokumencie, należy ufać VBA w dokumencie do uruchomienia. Może to być realizowane na kilka sposobów. W tym przewodniku ufaj lokalizacji dokumentu  w Centrum zaufania programu Word.

### <a name="to-trust-the-location-of-the-document"></a>Ufanie lokalizacji dokumentu

1. Uruchom program Word.

2. Kliknij **kartę** Plik.

3. Kliknij przycisk **Opcje programu Word.**

4. W okienku kategorii kliknij pozycję **Centrum zaufania.**

5. W okienku szczegółów kliknij pozycję **Ustawienia Centrum zaufania.**

6. W okienku kategorii kliknij pozycję **Zaufane lokalizacje.**

7. W okienku szczegółów kliknij pozycję **Dodaj nową lokalizację.**

8. W **oknie dialogowym Microsoft Office Trusted Location** (Zaufana lokalizacja) przejdź do folderu zawierającego projekt **CallingCodeFromVBA.**

9. Wybierz **podfoldery tej lokalizacji są również zaufane.**

10. W **oknie Microsoft Office zaufanej** lokalizacji kliknij przycisk **OK.**

11. W **oknie dialogowym Centrum** zaufania kliknij przycisk **OK.**

12. W **oknie dialogowym Opcje** programu Word kliknij przycisk **OK.**

13. Zamknij program Word.

## <a name="add-a-method-to-the-thisdocument-class"></a>Dodawanie metody do klasy ThisDocument
 Po skonfigurowaniu projektu VBA dodaj metodę do klasy elementów hosta, która można wywołać `ThisDocument` z kodu VBA.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>Aby dodać metodę do klasy ThisDocument

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję ThisDocument.vb,** a następnie kliknij polecenie **Wyświetl kod.**

     Plik **ThisDocument.vb zostanie** otwarty w Edytorze kodu.

2. Dodaj następującą metodę do `ThisDocument` klasy . Ta metoda tworzy tabelę z dwoma wierszami i dwiema kolumnami na początku dokumentu. Parametry określają tekst wyświetlany w pierwszym wierszu. W dalszej części tego przewodnika wywołasz tę metodę z kodu VBA w dokumencie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb" id="Snippet1":::

3. Skompiluj projekt.

## <a name="expose-the-method-to-vba-code"></a>Uwidocznij metodę kodowi VBA
 Aby uwidocznić metodę dla kodu VBA w dokumencie, ustaw właściwość `CreateTable` **EnableVbaCallers** elementu `ThisDocument` hosta na wartość **True**.

### <a name="to-expose-the-method-to-vba-code"></a>Aby uwidocznić metodę dla kodu VBA

1. W **Eksplorator rozwiązań** kliknij dwukrotnie **pozycję ThisDocument.vb.**

     Plik **DocumentWithVBA zostanie** otwarty w projektancie.

2. W **oknie** Właściwości wybierz właściwość **EnableVbaCallers** i zmień wartość na **True**.

3. Kliknij **przycisk OK** w wyświetlonym komunikacie.

4. Skompiluj projekt.

## <a name="call-the-method-from-vba-code"></a>Wywołanie metody z kodu VBA
 Teraz możesz wywołać metodę `CreateTable` z kodu VBA w dokumencie.

> [!NOTE]
> W tym przewodniku dodasz kod VBA do dokumentu podczas debugowania projektu. Kod VBA, który dodasz do tego dokumentu, zostanie zastąpiony przy następnej kompilacji projektu, ponieważ program Visual Studio zastąpi dokument w folderze danych wyjściowych kompilacji kopią dokumentu z głównego folderu projektu. Jeśli chcesz zapisać kod VBA, możesz skopiować go do dokumentu w folderze projektu. Aby uzyskać więcej informacji, zobacz Łączenie dostosowań na poziomie dokumentu i [VBA.](../vsto/combining-vba-and-document-level-customizations.md)

### <a name="to-call-the-method-from-vba-code"></a>Aby wywołać metodę z kodu VBA

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Na karcie **Deweloper** w grupie **Kod** kliknij pozycję **Visual Basic**.

     Zostanie Edytor Visual Basic.

3. W menu **Wstaw** kliknij pozycję **Moduł**.

4. Dodaj następujący kod do nowego modułu.

     Ten kod wywołuje `CreateTable` metodę w zestawie dostosowywania. Makro uzyskuje dostęp do tej metody przy `CallVSTOAssembly` użyciu właściwości `ThisDocument` obiektu . Ta właściwość została wygenerowana automatycznie podczas ustawienia właściwości **EnableVbaCallers** wcześniej w tym przewodniku.

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. Naciśnij klawisz **F5**.

6. Sprawdź, czy do dokumentu dodano nową tabelę.

7. Zamknij program Word bez zapisywania zmian.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat wywoływania kodu w rozwiązaniach pakietu Office z VBA można znaleźć w tych tematach:

- Wywołaj kod w dostosowań Visual C# z kodu VBA. Ten proces różni się od Visual Basic procesu. Aby uzyskać więcej informacji, zobacz Przewodnik: wywołanie kodu [z VBA w projekcie visual C&#35; .](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)

- Wywołaj kod w dodatku VSTO z VBA. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywołanie kodu w dodatku VSTO z VBA.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

## <a name="see-also"></a>Zobacz też
- [Łączenie dostosowań na poziomie dokumentu i VBA](../vsto/combining-vba-and-document-level-customizations.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [How to: Expose code to VBA in a Visual Basic project (Jak uwidocznić kod vBA w Visual Basic projektu)](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [How to: Expose code to VBA in a Visual C&#35; project (Jak uwidocznić kod vBA w projekcie visual C)](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Przewodnik: wywołanie kodu z VBA w projekcie visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
