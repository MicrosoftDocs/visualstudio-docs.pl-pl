---
title: 'Przewodnik: Wywoływanie kodu z VBA w projektach Visual Basic'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46fa903b0025279fec3b33d3c14ce1661d076926
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438667"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>Przewodnik: Wywoływanie kodu z VBA w projektach Visual Basic
  W tym instruktażu przedstawiono sposób wywołania metody w dostosowaniu na poziomie dokumentu dla programu Microsoft Office Word z Visual Basic for Applications (VBA) kod w dokumencie. Procedura obejmuje trzy podstawowe kroki: Dodaj metodę, która `ThisDocument` hosta klasy elementu, ujawnia metody dla kodu VBA, a następnie wywołaj metodę z kodu VBA w dokumencie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Chociaż ten przewodnik korzysta z programu Word w szczególności pojęcia dowodzą przewodnika są również zastosowanie do projektów na poziomie dokumentu dla programu Excel.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie dokumentu, który zawiera kod VBA.

- Ufanie lokalizację dokumentu przy użyciu Centrum zaufania w programie Word.

- Dodawanie metody do `ThisDocument` hosta klasy elementu.

- Udostępnia metody dla kodu VBA.

- Wywołanie metody z kodu VBA.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>Utworzyć dokument, który zawiera kod VBA
 Pierwszym krokiem jest utworzyć dokument z włączoną obsługą makr zawiera proste makro VBA. Przed utworzeniem projektu programu Visual Studio, który zależy od tego dokumentu, dokument musi zawierać projekt VBA. W przeciwnym razie program Visual Studio nie można zmodyfikować projekt VBA w celu włączenia kodu VBA w celu wywołania do zestawu dostosowywania.

 Jeśli masz już dokument, który zawiera kod VBA, którego chcesz użyć, możesz pominąć ten krok.

### <a name="to-create-a-document-that-contains-vba-code"></a>Aby utworzyć dokument, który zawiera kod VBA

1. Uruchom program Word.

2. Zapisz aktywny dokument programu Word **obsługą dokumentu (\*docm)** o nazwie **DocumentWithVBA**. Zapisz go w dogodnym miejscu, na przykład na pulpit.

3. Na wstążce kliknij **Developer** kartę.

    > [!NOTE]
    > Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W **kodu** grupy, kliknij przycisk **języka Visual Basic**.

     Zostanie otwarty Edytor kodu języka Visual Basic.

5. W **projektu** okna, kliknij dwukrotnie **ThisDocument**.

     Plik kodu dla `ThisDocument` obiektu zostanie otwarta.

6. Dodaj następujący kod VBA do pliku kodu. Ten kod definiuje prosty funkcja, która nie wykonuje żadnych działań. Jest jedynym celem tej funkcji, aby upewnić się, że projekt VBA istnieje w dokumencie. Jest to wymagane do wykonania kolejnych kroków tego przewodnika.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Zapisz dokument i zamknij program Word.

## <a name="create-the-project"></a>Utwórz projekt
 Teraz możesz utworzyć projekt na poziomie dokumentu dla programu Word, który korzysta z włączoną obsługą makr dokumentu, która została utworzona wcześniej.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**. Jeśli środowisko IDE jest ustawione na korzystanie z ustawienia programowania Visual Basic, **pliku** menu, kliknij przycisk **nowy projekt**.

3. W okienku szablonów, rozwiń **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. Wybierz **dodatków pakietu Office** węzła.

5. Na liście szablonów projektu wybierz **dokument programu Word 2010** lub **dokumentu programu Word 2013** projektu.

6. W **nazwa** wpisz **CallingCodeFromVBA**.

7. Kliknij przycisk **OK**.

     **Visual Studio Tools dla pakietu Office, Kreator projektu** zostanie otwarty.

8. Wybierz **Kopiuj istniejący dokument**, a następnie w **Pełna ścieżka istniejącego dokumentu** należy określić lokalizację **DocumentWithVBA** dokumentu, który został utworzony wcześniej . Jeśli używasz własnych dokumentów z włączoną obsługą makr, należy określić lokalizację tego dokumentu.

9. Kliknij przycisk **Zakończ**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **DocumentWithVBA** dokumentu w Projektancie i dodaje **CallingCodeFromVBA** projekt **Eksploratora rozwiązań**.

## <a name="trust-the-location-of-the-document"></a>Zaufanie do lokalizacji dokumentu
 Zanim za udostępnianie kodu w rozwiązaniu dla kodu VBA w dokumencie, muszą ufać VBA w dokumencie w celu uruchomienia. Istnieje kilka sposobów, aby to zrobić. W tym przewodniku ufa lokalizacji dokumentu w **Centrum zaufania** w programie Word.

### <a name="to-trust-the-location-of-the-document"></a>Aby zaufać lokalizację dokumentu

1. Uruchom program Word.

2. Kliknij przycisk **pliku** kartę.

3. Kliknij przycisk **Word, opcje** przycisku.

4. W okienku kategorii kliknij **Centrum zaufania**.

5. W okienku szczegółów kliknij **ustawienia Centrum zaufania**.

6. W okienku kategorii kliknij **zaufane lokalizacje**.

7. W okienku szczegółów kliknij **Dodaj nową lokalizację**.

8. W **Microsoft Office zaufanej lokalizacji** okno dialogowe, przejdź do folderu, który zawiera **CallingCodeFromVBA** projektu.

9. Wybierz **podfoldery tej lokalizacji są także zaufane**.

10. W **Microsoft Office zaufanej lokalizacji** okno dialogowe, kliknij przycisk **OK**.

11. W **Centrum zaufania** okno dialogowe, kliknij przycisk **OK**.

12. W **Word, opcje** okno dialogowe, kliknij przycisk **OK**.

13. Zamknij program Word.

## <a name="add-a-method-to-the-thisdocument-class"></a>Dodawanie metody do ThisDocument — klasa
 Teraz, gdy projekt VBA jest skonfigurowany, Dodaj metodę, która `ThisDocument` hosta klasa elementu, który można wywoływać z kodu VBA.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>Aby dodać metodę do ThisDocument — klasa

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument.vb**, a następnie kliknij przycisk **Wyświetl kod**.

     **ThisDocument.vb** plik zostanie otwarty w edytorze kodu.

2. Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda tworzy tabelę z wierszami i dwie kolumny na początku dokumentu. Parametry Określ tekst, który jest wyświetlany w pierwszym wierszu. W dalszej części tego przewodnika będzie wywołać tej metody z kodu VBA w dokumencie.

     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]

3. Skompiluj projekt.

## <a name="expose-the-method-to-vba-code"></a>Ujawnia metody dla kodu VBA
 Do udostępnienia `CreateTable` metody dla kodu VBA w dokumencie, ustawienie **EnableVbaCallers** właściwość `ThisDocument` element hosta do **True**.

### <a name="to-expose-the-method-to-vba-code"></a>Aby udostępnić metody dla kodu VBA

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **ThisDocument.vb**.

     **DocumentWithVBA** plik zostanie otwarty w projektancie.

2. W **właściwości** wybierz **EnableVbaCallers** właściwości i zmień wartość na **True**.

3. Kliknij przycisk **OK** wiadomości, która jest wyświetlana.

4. Skompiluj projekt.

## <a name="call-the-method-from-vba-code"></a>Wywołaj metodę z kodu VBA
 Teraz można wywołać `CreateTable` metody z kodu VBA w dokumencie.

> [!NOTE]
> W tym przewodniku dodasz kod VBA w dokumencie podczas debugowania projektu. Kod VBA dodawany do tego dokumentu zostaną zastąpione przy następnym uruchomieniu kompilacji projektu, ponieważ program Visual Studio zastępuje dokument w folderze wyjściowym kompilacji kopię dokumentu z folderu głównego projektu. Jeśli chcesz zapisać ten kod, skopiuj go do dokumentu w folderze projektu. Aby uzyskać więcej informacji, zobacz [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>Aby wywołać metodę z kodu VBA

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Na **Developer** na karcie **kodu** grupy, kliknij przycisk **języka Visual Basic**.

     Zostanie otwarty Edytor kodu języka Visual Basic.

3. Na **Wstaw** menu, kliknij przycisk **modułu**.

4. Dodaj następujący kod do nowego modułu.

     Ten kod wywołuje `CreateTable` metody w zestawie dostosowywania. Makro uzyskuje dostęp do tej metody za pomocą `CallVSTOAssembly` właściwość `ThisDocument` obiektu. Tej właściwości został wygenerowany automatycznie po ustawieniu **EnableVbaCallers** właściwości we wcześniejszej części tego przewodnika.

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. Naciśnij klawisz **F5**.

6. Sprawdź, czy nowa tabela został dodany do dokumentu.

7. Zamknij program Word bez zapisywania zmian.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej informacji na temat wywoływanie kodu w rozwiązaniach pakietu Office z VBA w następujących tematach:

- Wywołaj kod w dostosowaniu Visual C# z języka VBA. Ten proces różni się od procesu języka Visual Basic. Aby uzyskać więcej informacji, zobacz [instruktażu: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

- Wywoływanie kodu w dodatku narzędzi VSTO z kodu VBA. Aby uzyskać więcej informacji, zobacz [instruktażu: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Zobacz także
- [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: Udostępnianie kodu z VBA w projektach Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Instrukcje: Udostępnianie kodu z VBA w Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Przewodnik: Wywoływanie kodu z VBA w Visual C&#35; projektu](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
