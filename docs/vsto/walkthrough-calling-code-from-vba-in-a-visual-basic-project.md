---
title: 'Przewodnik: wywoływanie kodu z VBA w projekcie Visual Basic'
description: Dowiedz się, jak wywołać metodę w dostosowaniu na poziomie dokumentu dla programu Microsoft Word z kodu Visual Basic for Applications (VBA) w dokumencie.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6016dbf53413f6e55c88edfe930af677472bdaf5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527384"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>Przewodnik: wywoływanie kodu z VBA w projekcie Visual Basic
  W tym instruktażu pokazano, jak wywołać metodę w dostosowaniu na poziomie dokumentu dla Microsoft Office Word z kodu Visual Basic for Applications (VBA) w dokumencie. Procedura obejmuje trzy podstawowe kroki: Dodaj metodę do `ThisDocument` klasy Item hosta, Uwidocznij metodę w kodzie VBA, a następnie Wywołaj metodę z kodu VBA w dokumencie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Chociaż w tym instruktażu jest stosowane słowo kluczowe, koncepcje przedstawione w tym przewodniku dotyczą również projektów na poziomie dokumentu dla programu Excel.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie dokumentu zawierającego kod języka VBA.

- Zaufanie lokalizacji dokumentu przy użyciu Centrum zaufania w programie Word.

- Dodawanie metody do `ThisDocument` klasy elementu hosta.

- Udostępnianie metody do kodu VBA.

- Wywoływanie metody z kodu VBA.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>Tworzenie dokumentu zawierającego kod języka VBA
 Pierwszym krokiem jest utworzenie dokumentu z obsługą makr zawierającego proste makro języka VBA. Dokument musi zawierać projekt VBA przed utworzeniem projektu programu Visual Studio, który jest oparty na tym dokumencie. W przeciwnym razie program Visual Studio nie może zmodyfikować projektu VBA, aby umożliwić wywoływanie kodu VBA w zestawie dostosowywania.

 Jeśli masz już dokument zawierający kod języka VBA, którego chcesz użyć, możesz pominąć ten krok.

### <a name="to-create-a-document-that-contains-vba-code"></a>Aby utworzyć dokument zawierający kod języka VBA

1. Uruchom program Word.

2. Zapisz aktywny dokument jako **dokument z obsługą makr programu Word ( \* . docm)** o nazwie **DocumentWithVBA**. Zapisz ją w wygodnej lokalizacji, na przykład na pulpicie.

3. Na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W grupie **kod** kliknij przycisk **Visual Basic**.

     Zostanie otwarty Edytor Visual Basic.

5. W oknie **projektu** kliknij dwukrotnie pozycję **ThisDocument**.

     Plik kodu dla `ThisDocument` obiektu zostanie otwarty.

6. Dodaj następujący kod języka VBA do pliku kodu. Ten kod definiuje prostą funkcję, która nic nie robi. Jedynym celem tej funkcji jest upewnienie się, że projekt VBA istnieje w dokumencie. Jest to wymagane do wykonania kolejnych kroków w tym instruktażu.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Zapisz dokument i Zakończ działanie programu Word.

## <a name="create-the-project"></a>Tworzenie projektu
 Teraz można utworzyć projekt na poziomie dokumentu dla programu Word, który używa wcześniej utworzonego dokumentu z obsługą makr.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**. Jeśli środowisko IDE jest skonfigurowane do korzystania z ustawień tworzenia Visual Basic, w menu **plik** kliknij pozycję **Nowy projekt**.

3. W okienku szablony rozwiń węzeł **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. Wybierz węzeł **Dodatki pakietu Office** .

5. Na liście szablonów projektu wybierz **dokument word 2010** lub projekt **dokumentu programu Word 2013** .

6. W polu **Nazwa** wpisz **CallingCodeFromVBA**.

7. Kliknij przycisk **OK**.

     Zostanie otwarty **kreator Visual Studio Tools dla programu Office Project** .

8. Wybierz pozycję **Kopiuj istniejący dokument**, a następnie w polu **pełna ścieżka istniejącego dokumentu** Określ lokalizację utworzonego wcześniej pliku **DocumentWithVBA** . Jeśli używasz własnego dokumentu z obsługą makr, zamiast tego Określ lokalizację tego dokumentu.

9. Kliknij przycisk **Finish** (Zakończ).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera dokument **DocumentWithVBA** w Projektancie i dodaje projekt **CallingCodeFromVBA** do **Eksplorator rozwiązań**.

## <a name="trust-the-location-of-the-document"></a>Ufaj lokalizacji dokumentu
 Zanim będzie można uwidocznić kod w rozwiązaniu w kodzie VBA w dokumencie, musisz ufać VBA w dokumencie do uruchomienia. Może to być realizowane na kilka sposobów. W tym instruktażu należy zaufać lokalizacji dokumentu w **Centrum zaufania** w programie Word.

### <a name="to-trust-the-location-of-the-document"></a>Aby zaufać lokalizacji dokumentu

1. Uruchom program Word.

2. Kliknij kartę **plik** .

3. Kliknij przycisk **Opcje słowa** .

4. W okienku kategorie kliknij pozycję **Centrum zaufania**.

5. W okienku szczegółów kliknij pozycję **Ustawienia Centrum zaufania**.

6. W okienku kategorie kliknij pozycję **Zaufane lokalizacje**.

7. W okienku szczegółów kliknij pozycję **Dodaj nową lokalizację**.

8. W oknie dialogowym **Microsoft Office zaufanej lokalizacji** przejdź do folderu, który zawiera projekt **CallingCodeFromVBA** .

9. Wybrane **podfoldery tej lokalizacji również są zaufane**.

10. W oknie dialogowym **Microsoft Office zaufanej lokalizacji** kliknij przycisk **OK**.

11. W oknie dialogowym **Centrum zaufania** kliknij przycisk **OK**.

12. W oknie dialogowym **Opcje programu Word** kliknij przycisk **OK**.

13. Zamknij program Word.

## <a name="add-a-method-to-the-thisdocument-class"></a>Dodawanie metody do klasy ThisDocument
 Po skonfigurowaniu projektu VBA należy dodać metodę do `ThisDocument` klasy elementu hosta, którą można wywołać z kodu VBA.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>Aby dodać metodę do klasy ThisDocument

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **ThisDocument. vb**, a następnie kliknij polecenie **Wyświetl kod**.

     Plik **ThisDocument. vb** zostanie otwarty w edytorze kodu.

2. Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda tworzy tabelę z dwoma wierszami i dwiema kolumnami na początku dokumentu. Parametry określają tekst, który jest wyświetlany w pierwszym wierszu. W dalszej części tego instruktażu ta metoda zostanie wywołana z kodu VBA w dokumencie.

     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]

3. Skompiluj projekt.

## <a name="expose-the-method-to-vba-code"></a>Uwidacznianie metody w kodzie VBA
 Aby udostępnić `CreateTable` metodę do kodu VBA w dokumencie, ustaw właściwość **EnableVbaCallers** dla `ThisDocument` elementu hosta na **wartość true**.

### <a name="to-expose-the-method-to-vba-code"></a>Aby udostępnić metodę do kodu VBA

1. W **Eksplorator rozwiązań** kliknij dwukrotnie pozycję **ThisDocument. vb**.

     Plik **DocumentWithVBA** zostanie otwarty w projektancie.

2. W oknie **Właściwości** wybierz właściwość **EnableVbaCallers** i zmień wartość na **true**.

3. Kliknij przycisk **OK** w wyświetlonym komunikacie.

4. Skompiluj projekt.

## <a name="call-the-method-from-vba-code"></a>Wywoływanie metody z kodu VBA
 Teraz można wywołać `CreateTable` metodę z kodu VBA w dokumencie.

> [!NOTE]
> W tym instruktażu dodasz kod VBA do dokumentu podczas debugowania projektu. Kod VBA dodany do tego dokumentu zostanie zastąpiony przy następnym skompilowaniu projektu, ponieważ program Visual Studio zastępuje dokument w folderze danych wyjściowych kompilacji kopią dokumentu z głównego folderu projektu. Jeśli chcesz zapisać kod VBA, możesz skopiować go do dokumentu w folderze projektu. Aby uzyskać więcej informacji, zobacz [łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>Aby wywołać metodę z kodu VBA

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Na karcie **deweloper** w grupie **kod** kliknij przycisk **Visual Basic**.

     Zostanie otwarty Edytor Visual Basic.

3. W menu **Wstaw** kliknij pozycję **moduł**.

4. Dodaj następujący kod do nowego modułu.

     Ten kod wywołuje `CreateTable` metodę w zestawie dostosowywania. Makro uzyskuje dostęp do tej metody przy użyciu `CallVSTOAssembly` właściwości `ThisDocument` obiektu. Ta właściwość została wygenerowana automatycznie po ustawieniu właściwości **EnableVbaCallers** wcześniej w tym instruktażu.

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. Naciśnij klawisz **F5**.

6. Sprawdź, czy nowa tabela została dodana do dokumentu.

7. Zamknij program Word bez zapisywania zmian.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat wywoływania kodu w rozwiązaniach pakietu Office z poziomu języka VBA można znaleźć w następujących tematach:

- Wywoływanie kodu w Visual C# dostosowania z języka VBA. Proces ten różni się od procesu Visual Basic. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywoływanie kodu z VBA w projekcie Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

- Wywoływanie kodu w dodatku VSTO z poziomu języka VBA. Aby uzyskać więcej informacji, zobacz [Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Zobacz też
- [Łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: Uwidacznianie kodu w języku VBA w projekcie Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Instrukcje: Uwidacznianie kodu w języku VBA w projekcie programu Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Przewodnik: wywoływanie kodu z VBA w projekcie Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
