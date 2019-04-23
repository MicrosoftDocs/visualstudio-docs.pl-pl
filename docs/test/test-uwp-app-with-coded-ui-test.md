---
title: Testowanie aplikacji platformy uniwersalnej systemu Windows za pomocą kodowanych testów interfejsu użytkownika
ms.date: 05/31/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: d50972ccb68ba43e8ebefa0d69fdfff8f7fc5be4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103263"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Tworzenie kodowanego interfejsu użytkownika testu do testowania aplikacji platformy uniwersalnej systemu Windows

W tym artykule wyjaśniono, jak utworzyć kodowany test interfejsu użytkownika dla aplikacji uniwersalnych platformy Windows (UWP).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Tworzenie aplikacji platformy uniwersalnej systemu Windows do testowania

Pierwszym krokiem jest, aby utworzyć prostą aplikację platformy uniwersalnej systemu Windows, aby uruchomić test przed.

1. W programie Visual Studio Utwórz nowy projekt za pomocą **pusta aplikacja (Windows Universal)** szablonu dla języka Visual C# lub Visual Basic.

   ::: moniker range="vs-2017"

   ![Pusta aplikacja Windows Universal szablonu](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. W **nowy projekt platformy Windows Universal** okno dialogowe, wybierz opcję **OK** aby zaakceptować domyślne wersje platformy.

1. Z **Eksploratora rozwiązań**, otwórz *MainPage.xaml*.

   Plik zostanie otwarty w **projektanta XAML**.

1. Przeciągnij formant przycisku i formant pola tekstowego z **przybornika** do powierzchni projektowej.

     ![Projekt aplikacji platformy uniwersalnej systemu Windows](../test/media/toolbox-controls.png)

1. Nadaj nazwy do kontrolek. Zaznacz formant pola tekstowego, a następnie w polu **właściwości** oknie wprowadź **pole tekstowe** w **nazwa** pola. Zaznacz formant przycisku, a następnie w **właściwości** oknie wprowadź **przycisk** w **nazwa** pola.

1. Kliknij dwukrotnie formant przycisku i Dodaj następujący kod do treści `Button_Click` metody. Ten kod po prostu ustawia tekst w polu tekstowym nazwę kontrolki przycisku, po prostu dla nas coś, aby sprawdzić z kodowanego testu interfejsu użytkownika, który utworzymy w dalszej części.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Naciśnij klawisz **Ctrl**+**F5** do uruchomienia aplikacji. Powinien zostać wyświetlony podobny do poniższego:

   ![Aplikacja platformy uniwersalnej systemu Windows z przycisk i pole tekstowe](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Tworzenie kodowanego testu interfejsu użytkownika

1. Aby dodać projekt testu do rozwiązania, kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**.

1. Wyszukaj i wybierz pozycję **kodowanego projektu testu interfejsu użytkownika (Windows Universal)** szablonu.

   ::: moniker range="vs-2017"

   ![Nowy projekt kodowanego testu interfejsu użytkownika](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Jeśli nie widzisz **projekt kodowanego interfejsu użytkownika testu (Windows Universal)** szablonu, trzeba [instalacji składnika należy kodowanego testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. W **Generuj kod dla kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz opcję **ręcznie Edytuj test**.

   ![Generuj kod dla kodowanego interfejsu użytkownika test dialogowy](../test/media/manually-edit-the-test.png)

1. Jeśli aplikacja platformy uniwersalnej systemu Windows nie jest już uruchomiona, uruchom ją, naciskając klawisz **Ctrl**+**F5**.

1. Otwórz **kodowanego testu interfejsu użytkownika** okna dialogowego, umieszczając kursor w `CodedUITestMethod1` metody, a następnie wybierając **testu** > **Generuj kod dla kodowanego testu interfejsu użytkownika**  >  **Użyj kodowanego konstruktora testu interfejsu użytkownika**.

1. Dodaj formanty do mapy formantów interfejsu użytkownika. Użyj **kodowanego testu interfejsu użytkownika** narzędzia krzyżyk, aby zaznaczyć formant przycisku w aplikacji platformy uniwersalnej systemu Windows. W **dodawania potwierdzeń** okna dialogowego, rozwiń węzeł **mapy formantów UI** okienko, jeśli to konieczne, a następnie wybierz **dodać formant do mapy formantów UI**.

     ![Dodać formant do mapy interfejsu użytkownika](../test/media/add-control-to-ui-control-map.png)

1. Powtórz poprzedni krok, aby dodać formant pola tekstowego do mapy formantów interfejsu użytkownika.

1. W **kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz opcję **Generuj kod** lub naciśnij **Ctrl**+**G**. Następnie wybierz pozycję **Generuj** utworzyć kod dla zmiany mapy formantów interfejsu użytkownika.

     ![Generuj kod dla mapy interfejsu użytkownika](../test/media/generate-code-dialog.png)

1. Aby sprawdzić, czy tekst w polu tekstowym zmienia się na **przycisk** po kliknięciu przycisku, kliknij przycisk.

     ![Kliknij formant przycisku, aby ustawić wartość w polu tekstowym](../test/media/uwp-app-button-textbox.png)

1. Dodaj potwierdzenie, aby sprawdzić tekstu w formancie textbox. Użyj narzędzia krzyżyk aby zaznaczyć formant pola tekstowego, a następnie wybierz **tekstu** właściwość **dodawania potwierdzeń** okna dialogowego. Następnie wybierz **Dodaj potwierdzenie** lub naciśnij **Alt**+**A**. W **komunikat o błędzie potwierdzenia** wprowadź **wartość w polu tekstowym jest nieoczekiwany.** a następnie wybierz **OK**.

     ![Wybierz pole tekstowe z krzyżyk, a następnie dodaj potwierdzenie](../test/media/add-assertion-for-text.png)

1. Generuj kod testu do potwierdzenia. W **kodowanego testu interfejsu użytkownika** okno dialogowe, wybierz opcję **Generuj kod**. W **Generuj kod** okno dialogowe, wybierz opcję **Dodaj i Generuj**.

     ![Generuj kod dla potwierdzenia textbox](../test/media/add-and-generate-assert-method.png)

   W **Eksploratora rozwiązań**, otwórz *UIMap.Designer.cs* Aby wyświetlić dodany kod dla metody assert i formantów.

   > [!TIP]
   > Jeśli używasz języka Visual Basic, otwórz *CodedUITest1.vb*. Następnie w `CodedUITestMethod1()` test kodu metody, kliknij prawym przyciskiem myszy na wywołanie metody assert `Me.UIMap.AssertMethod1()` i wybierz polecenie **przejdź do definicji**. *UIMap.Designer.vb* zostanie otwarty w edytorze kodu, a można wyświetlić dodany kod dla metody assert i formantów.

    > [!WARNING]
    > Nie należy modyfikować *UIMap.designer.cs* lub *UIMap.Designer.vb* pliki bezpośrednio. Jeśli to zrobisz, zmiany zostaną zastąpione, gdy test jest generowany.

    Metody assert wygląda następująco:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. Następnie należy uzyskać **AutomationId** dla platformy UWP [aplikacji](#create-a-uwp-app-to-test) który chcemy przetestować. Otwórz Windows **Start** menu, aby wyświetlić na kafelku aplikacji. Następnie przeciągnij narzędzie krzyżyka ![ikonę docelową](media/target-icon.png) z **kodowanego testu interfejsu użytkownika** okno dialogowe, aby Kafelek aplikacji. Gdy niebieski prostokąt otacza kafelka, zwolnij myszy.

   ![Narzędzia krzyżyk](media/cross-hair-tool.png)

   **Dodawania potwierdzeń** okno dialogowe otwiera i wyświetla **AutomationId** dla aplikacji. Kliknij prawym przyciskiem myszy **AutomationId** i wybierz polecenie **wartość kopiowania do Schowka**.

   ![AutomationID w oknie dialogowym Dodaj potwierdzenia](../test/media/automation-id.png)

1. Dodaj kod do metody testowej, aby uruchomić aplikację platformy uniwersalnej systemu Windows. W **Eksploratora rozwiązań**, otwórz *CodedUITest1.cs* lub *CodedUITest1.vb*. Powyższe wywołanie `AssertMethod1`, Dodaj kod, aby uruchomić aplikację platformy uniwersalnej systemu Windows:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Zastąp identyfikator automatyzacji w przykładowym kodzie wartości, w której został skopiowany do Schowka w poprzednim kroku.

   > [!IMPORTANT]
   > TRIM początku Identyfikatora automatyzacji, aby usunąć znaki, takie jak **P ~**. Jeśli nie trim te znaki, test zgłasza `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` podczas próby uruchomienia aplikacji.

1. Następnie dodaj kod do metody testowej, kliknięcie przycisku. W wierszu po `XamlWindow.Launch`, Dodaj gest, aby dotknąć przycisku sterowania:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Po dodaniu kodu pełne `CodedUITestMethod1` metoda testowa powinna wyglądać następująco:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Tworzenie projektu testowego, a następnie otwórz **Eksploratora testów** , wybierając **Test** > **Windows** > **Eksploratora testów**.

1. Wybierz **Uruchom wszystkie** do uruchomienia testu.

   Dotknięcie aplikacja otworzy przycisk i pole tekstowe **tekstu** właściwość jest wypełnione. Metody assert weryfikuje pole tekstowe **tekstu** właściwości.

   Po zakończeniu testu **Eksploratora testów** wyświetla tę test zakończył się powodzeniem.

   ![W programie Test Explorer wyświetla testów zakończonych powodzeniem](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>PYT.: Dlaczego nie widzę opcji zapisu mojego kodowanego testu interfejsu użytkownika w Generuj kod dla kodowanego testu interfejsu użytkownika okna dialogowego

**A**: Opcja zapisu nie jest obsługiwana dla aplikacji platformy uniwersalnej systemu Windows.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>PYT.: Czy można utworzyć kodowany test interfejsu użytkownika, dla mojej aplikacji platformy uniwersalnej systemu Windows oparte na WinJS?

**A**: Nie są obsługiwane tylko aplikacje oparte na XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>PYT.: Dlaczego nie można zmodyfikować kod w pliku UIMap.Designer?

**A**: Dowolny kod zmiany wprowadzone w oknie *UIMapDesigner.cs* pliku zostaną zastąpione za każdym razem, gdy generowane za pomocą kodu **kodowanego testu interfejsu użytkownika**. Jeśli trzeba zmodyfikować nagraną metodę, skopiuj go do *UIMap.cs* plików i zmień jego nazwę. *UIMap.cs* pliku może służyć do zastępowania metod i właściwości w *UIMapDesigner.cs* pliku. Usuń odwołanie do oryginalnej metody w *CodedUITest.cs* plik i zastąp go nazwą metody o zmienionej nazwie.

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Ustaw właściwości Unikatowy automatyzacji dla kontrolek platformy UWP](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)