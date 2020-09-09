---
title: Debugowanie formularza systemu Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6cec7b9bc2c56e16d1a5d59701d0953797ae00f4
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599477"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Przewodnik: Debugowanie formularza Windows Forms
Formularz systemu Windows jest jedną z najczęściej używanych aplikacji zarządzanych. Formularz systemu Windows tworzy standardową aplikację systemu Windows. Można wykonać instrukcje z tego przewodnika przy użyciu języka Visual Basic, C# lub C++.

 Po pierwsze, należy zamknąć wszystkie otwarte rozwiązania.

### <a name="to-prepare-for-this-walkthrough"></a>Aby przygotować się do tego przewodnika

- Jeśli masz już otwarte rozwiązanie, zamknij je. (W menu **plik** wybierz pozycję **Zamknij rozwiązanie**).

## <a name="create-a-new-windows-form"></a>Tworzenie nowego formularza systemu Windows
 Następnie można utworzyć nowy formularz systemu Windows.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Aby utworzyć formularz systemu Windows dla tego przewodnika

1. W menu **plik** wybierz polecenie **Nowy** , a następnie kliknij pozycję **projekt**.

     Zostanie wyświetlone okno dialogowe **Nowy projekt**.

2. W okienku typy projektów Otwórz węzeł **Visual Basic**, **Visual C#** lub **Visual C++** , a następnie

    1. W przypadku Visual Basic lub Visual C# wybierz pozycję **Windows Desktop**Windows  >  **form aplikacja**.

    2. W obszarze Visual C++ wybierz pozycję **aplikacja klasyczna systemu Windows**.

3. W polu **Nazwa** Nadaj projektowi unikatową nazwę (na przykład Walkthrough_SimpleDebug).

4. Kliknij pozycję **OK**.

     Visual Studio tworzy nowy projekt i wyświetla nowy formularz w Projektancie Windows Forms. Aby uzyskać więcej informacji, zobacz [Projektant formularzy systemu Windows](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).

5. W menu **Widok** wybierz pozycję **Przybornik**.

     Przybornik zostaje otwarty. Aby uzyskać więcej informacji, zobacz [Przybornik](../ide/reference/toolbox.md).

6. W przyborniku kliknij kontrolkę **przycisk** i przeciągnij formant na powierzchnię projektu formularza. Upuść przycisk na formularzu.

7. W przyborniku kliknij kontrolkę **TextBox** i przeciągnij formant na powierzchnię projektu formularza. Upuść **pole TextBox** w formularzu.

8. Na powierzchni projektowej formularza, dwukrotnie kliknij przycisk.

     Spowoduje to przejście do strony kodowej. Kursor powinien być w `button1_Click`.

10. W funkcji `button1_Click`, należy dodać następujący kod:

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. W menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.

     Projekt powinien być kompilowany bez błędów.

## <a name="debug-your-form"></a>Debugowanie formularza
 Teraz można rozpocząć debugowanie.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Aby debugować formularz systemu Windows utworzony dla tego przewodnika

1. W oknie źródłowym, należy kliknąć lewy margines w tym samym wierszu, co dodany tekst:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     Pojawi się czerwona kropka i tekst w wierszu zostanie wyróżniony czerwonym kolorem. Czerwona kropka reprezentuje punkt przerwania. Aby uzyskać więcej informacji, zobacz [punkty przerwania](/previous-versions/ktf38f66(v=vs.100)). Po uruchomieniu aplikacji w trybie debugowania, debuger zlokalizuje miejsce trafienia kodu i przerwie tam wykonywanie. Można wówczas wyświetlić stan aplikacji i zdebugować ją.

    > [!NOTE]
    > Możesz również kliknąć prawym przyciskiem myszy dowolny wiersz kodu, wskazać punkt **przerwania**, a następnie kliknąć polecenie **Wstaw punkt przerwania** , aby dodać punkt przerwania w tym wierszu.

2. W menu **debugowanie** wybierz polecenie **Uruchom**.

     Formularz systemu Windows zostaje uruchomiony.

3. W formularzu systemu Windows, należy kliknąć dodany przycisk.

     W programie Visual Studio powoduje to przejście do wiersza, w którym został ustawiony punkt przerwania na stronie kodowej. Ten wiersz powinien być wyróżniony żółtym kolorem. Można teraz wyświetlić zmienne w aplikacji i kontrolować jej wykonanie. Aplikacja zatrzymała teraz wykonywanie, czekając na akcję ze strony użytkownika.

4. W menu **Debuguj** wybierz pozycję **Windows**, następnie **Obejrzyj**i kliknij pozycję **Watch1**.

5. W oknie **Watch1** kliknij pusty wiersz. W kolumnie **Nazwa** wpisz `textBox1.Text` (jeśli używasz programu Visual Basic lub Visual C#) lub `textBox1->Text` (Jeśli używasz języka C++), naciśnij klawisz ENTER.

     W oknie **Watch1** jest wyświetlana wartość tej zmiennej w cudzysłowie:

    `""`

6. W menu **Debuguj** wybierz pozycję **krok do**.

     Wartość textBox1. Text zmienia się w oknie **Watch1** na:

    `Button was clicked!`

7. W menu **Debuguj** wybierz polecenie **Kontynuuj** , aby wznowić debugowanie programu.

8. W formularzu systemu Windows, należy ponownie kliknąć przycisk.

     Visual Studio ponownie przerywa wykonywanie.

9. Należy kliknąć czerwoną kropkę, która reprezentuje punkt przerwania.

     Spowoduje to usunięcie punktu przerwania z kodu.

10. W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie**.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>Dołącz do aplikacji formularza systemu Windows w celu debugowania
 W [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] można dołączyć debuger do działającego procesu. Jeśli użytkownik wykorzystuje Express Edition, ta funkcja nie jest obsługiwana.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Aby dołączyć do aplikacji formularza systemu Windows w celu debugowania

1. W projekcie utworzonym wcześniej, należy kliknąć na lewym marginesie, aby ponownie ustawić punkt przerwania w dodanym wierszu:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. W menu **debugowanie** wybierz polecenie **Uruchom bez debugowania**.

     Formularz systemu Windows zaczyna działanie w systemie Windows, tak jak gdyby użytkownik dwukrotnie kliknął jego plik wykonawczy. Debuger nie jest dołączony.

3. W menu **debugowanie** wybierz pozycję **Dołącz do procesu**. (To polecenie jest również dostępne w menu **Narzędzia** .)

     Zostanie wyświetlone okno dialogowe **Dołącz do procesu** .

4. W okienku **dostępne procesy** Znajdź nazwę procesu (Walkthrough_SimpleDebug.exe) w kolumnie **proces** i kliknij ją.

5. Kliknij przycisk **Dołącz** .

6. W formularzu systemu Windows, należy kliknąć jedyny przycisk.

     Debuger przerywa wykonywanie formularza systemu Windows w punkcie przerwania.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)