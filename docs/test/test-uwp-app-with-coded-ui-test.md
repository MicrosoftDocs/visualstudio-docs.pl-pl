---
title: Testowanie aplikacji platformy uniwersalnej systemu zrzeszoną za pomocą zakodowanego testu interfejsu użytkownika
ms.date: 05/31/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: fdd3d98bd848bb6fe679809a58f2e316a316f012
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590361"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Tworzenie zakodowany test interfejsu użytkownika, aby przetestować aplikację platformy uniwersalnej systemu i platformy uniwersalnej

W tym artykule wyjaśniono, jak utworzyć kodowany test interfejsu użytkownika dla aplikacji platformy uniwersalnej systemu Windows (UWP).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Tworzenie aplikacji platformy uniwersalnej systemuśpiłnie do testowania

Pierwszym krokiem jest utworzenie prostej aplikacji platformy uniwersalnej systemuśpiłka, aby uruchomić test przeciwko.

1. W programie Visual Studio utwórz nowy projekt przy użyciu szablonu **Pusta aplikacja (uniwersalny system Windows)** dla języka Visual C# lub Visual Basic.

   ::: moniker range="vs-2017"

   ![Pusta aplikacja Uniwersalny szablon systemu Windows](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. W oknie dialogowym **Nowy projekt platformy uniwersalnej systemu Windows** wybierz przycisk **OK,** aby zaakceptować domyślne wersje platformy.

1. W **Eksploratorze rozwiązań**otwórz stronę *MainPage.xaml*.

   Plik zostanie otwarty w **projektancie XAML**.

1. Przeciągnij kontrolkę przycisku i formant pola tekstowego z **przybornika** na powierzchnię projektu.

     ![Projektowanie aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu](../test/media/toolbox-controls.png)

1. Nadaj nazwy formantom. Zaznacz kontrolkę pola tekstowego, a następnie w oknie **Właściwości** wprowadź **pole textBox** w polu **Nazwa.** Wybierz kontrolka przycisku, a następnie w oknie **Właściwości** wprowadź **przycisk** w polu **Nazwa.**

1. Kliknij dwukrotnie formant przycisku i dodaj następujący `Button_Click` kod do treści metody. Ten kod po prostu ustawia tekst w textbox do nazwy formantu przycisku, tylko dać nam coś do sprawdzenia za pomocą kodowane go test interfejsu użytkownika utworzymy później.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Naciśnij **klawisz Ctrl**+**F5,** aby uruchomić aplikację. Powinna zostać wyświetlona zawartość podobna do tej:

   ![Aplikacja platformy uniwersalnej systemu ws. z przyciskiem i polem tekstowym](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Tworzenie zakodowany test interfejsu użytkownika

1. Aby dodać projekt testowy do rozwiązania, kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj** > **nowy projekt**.

1. Wyszukaj i wybierz szablon **zakodowany projekt testu interfejsu użytkownika (universal windows).**

   ::: moniker range="vs-2017"

   ![Nowy kodowany projekt testowy interfejsu użytkownika](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Jeśli nie widzisz szablonu **projektu testu interfejsu użytkownika kodowane (Universal Windows),** należy zainstalować [zakodowany składnik testu interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. W oknie dialogowym **Generowanie kodu dla zakodowanych testów interfejsu użytkownika** wybierz pozycję **Ręcznie edytuj test**.

   ![Generowanie kodu dla zakodowanego okna dialogowego testu interfejsu użytkownika](../test/media/manually-edit-the-test.png)

1. Jeśli aplikacja platformy uniwersalnej systemuśpig nie jest jeszcze uruchomiona, uruchom ją, naciskając klawisz **Ctrl**+**F5**.

1. Otwórz okno dialogowe **Konstruktora testów interfejsu** użytkownika `CodedUITestMethod1` kodowanych, umieszczając kursor w metodzie, a następnie wybierając **opcję Testuj** > **generowanie kodu dla kodowanych** > **kreatorów testów**interfejsu użytkownika .

1. Dodaj formanty do mapy sterowania interfejsu użytkownika. Użyj narzędzia **Konstruktor testów interfejsu** użytkownika, aby wybrać kontrolka przycisku w aplikacji platformy uniwersalnej systemu Windows. W oknie dialogowym **Dodawanie potwierdzeń** rozwiń okienko Mapa sterowania interfejsu **użytkownika,** jeśli to konieczne, a następnie wybierz pozycję **Dodaj kontrolkę do mapy sterowania interfejsu użytkownika**.

     ![Dodawanie formantu do mapy interfejsu użytkownika](../test/media/add-control-to-ui-control-map.png)

1. Powtórz poprzedni krok, aby dodać formant pola tekstowego do mapy sterowania interfejsu użytkownika.

1. W oknie dialogowym **Konstruktora testów kodowanych** wybierz pozycję **Generuj kod** lub naciśnij klawisz **Ctrl**+**G**. Następnie wybierz **pozycję Generuj,** aby utworzyć kod dla zmian na mapie sterowania interfejsu użytkownika.

     ![Generowanie kodu dla mapy interfejsu użytkownika](../test/media/generate-code-dialog.png)

1. Aby sprawdzić, czy tekst w obszarze tekstowym zmienia się na **przycisk** po kliknięciu przycisku, kliknij przycisk.

     ![Kliknij przycisk, aby ustawić wartość pola tekstowego](../test/media/uwp-app-button-textbox.png)

1. Dodaj asercja, aby zweryfikować tekst w formancie pola tekstowego. Użyj narzędzia cross-hair, aby zaznaczyć kontrolkę pola tekstowego, a następnie zaznacz właściwość **Tekst** w oknie dialogowym **Dodawanie potwierdzeń.** Następnie wybierz pozycję **Dodaj asercja** lub naciśnij klawisz **Alt**+**A**. W polu **Błąd komunikatu o asercji** wprowadź **wartość pola tekstowego jest nieoczekiwana.** a następnie wybierz **przycisk OK**.

     ![Wybierz pole tekstowe z krzyżykiem i dodaj asercja](../test/media/add-assertion-for-text.png)

1. Generowanie kodu testowego dla potwierdzenia. W oknie dialogowym **Konstruktora testów kodowanych** wybierz pozycję **Generuj kod**. W oknie dialogowym **Generowanie kodu** wybierz pozycję **Dodaj i generuj**.

     ![Generowanie kodu dla potwierdzenia pola tekstowego](../test/media/add-and-generate-assert-method.png)

   W **Eksploratorze rozwiązań**otwórz *UIMap.Designer.cs,* aby wyświetlić dodany kod metody potwierdzenia i formantów.

   > [!TIP]
   > Jeśli używasz języka Visual Basic, otwórz *codedUitest1.vb*. Następnie w `CodedUITestMethod1()` kodzie metody testowej kliknij prawym przyciskiem `Me.UIMap.AssertMethod1()` myszy wywołanie metody assert i wybierz polecenie **Przejdź do definicji**. *UIMap.Designer.vb* otwiera się w edytorze kodu i można wyświetlić dodany kod dla metody assert i formantów.

    > [!WARNING]
    > Nie należy modyfikować bezpośrednio *plików UIMap.designer.cs* lub *UIMap.Designer.vb.* Jeśli to zrobisz, zmiany zostaną zastąpione po wygenerowaniu testu.

    Assert Metoda wygląda następująco:

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

1. Następnie musimy uzyskać **AutomationId** aplikacji platformy uniwersalnej [systemu](#create-a-uwp-app-to-test) i odpowiedzi, które chcemy przetestować. Otwórz menu **Start** systemu Windows, aby wyświetlić kafelek aplikacji. Następnie przeciągnij ikonę ![](media/target-icon.png) narzędzia docelowych na krzyżyku z okna dialogowego **Konstruktora testów interfejsu** użytkownika kodowanych do kafelka aplikacji. Gdy kafelek otacza niebieskie pole, zwolnij mysz.

   ![Narzędzie do krzyżowania włosów](media/cross-hair-tool.png)

   Zostanie otwarte okno dialogowe **Dodawanie potwierdzeń** i zostanie wyświetlony **identyfikator AutomationId** dla aplikacji. Kliknij prawym przyciskiem myszy **pozycję AutomationId** i wybierz polecenie **Kopiuj wartość do Schowka**.

   ![AutomationID w oknie dialogowym Dodawanie potwierdzenia](../test/media/automation-id.png)

1. Dodaj kod do metody testowej, aby uruchomić aplikację platformy uniwersalnej systemuśpiłnie. W **Eksploratorze rozwiązań**otwórz *CodedUITest1.cs* lub *CodedUITest1.vb*. Powyżej połączenia `AssertMethod1`, dodaj kod, aby uruchomić aplikację platformy uniwersalnej systemuśpiłnie:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Zastąp identyfikator automatyzacji w przykładowym kodzie wartością skopiowaną do schowka w poprzednim kroku.

   > [!IMPORTANT]
   > Przytnij początek identyfikatora automatyzacji, aby usunąć znaki, takie jak **P~**. Jeśli nie przytnij tych znaków, test `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` zgłasza podczas próby uruchomienia aplikacji.

1. Następnie dodaj kod do metody testowej, aby kliknąć przycisk. W wierszu `XamlWindow.Launch`po , dodaj gest, aby dotknąć kontrolki przycisku:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Po dodaniu kodu `CodedUITestMethod1` pełna metoda badania powinna być następująca:

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

1. Skompiluj projekt testowy, a następnie otwórz **Eksploratora testów,** wybierając **pozycję Test** > **Windows** > **Test Explorer**.

1. Wybierz **uruchom wszystko,** aby uruchomić test.

   Aplikacja zostanie otwarta, przycisk zostanie stuknięty, a właściwość **Text** pola tekstowego zostanie wypełniona. Assert Metoda sprawdza poprawność textbox's **Text** właściwości.

   Po zakończeniu testu **Eksplorator testów** wyświetla, że test nie przeszedł.

   ![Przekazano ekrany testowe w Eksploratorze testów](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Pyt.: Dlaczego nie widzę opcji rejestrowania kodu interfejsu użytkownika w oknie dialogowym Generowanie kodu dla zakodowanych testów interfejsu użytkownika?

**A:** Opcja nagrywania nie jest obsługiwana dla aplikacji platformy uniwersalnej systemu Windows.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Pyt.: Czy można utworzyć kodowany test interfejsu użytkownika dla moich aplikacji platformy uniwersalnej systemu Windows na podstawie systemu WinJS?

**A:** Nie, obsługiwane są tylko aplikacje oparte na języku XAML.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>P: Dlaczego nie mogę zmodyfikować kodu w pliku UIMap.Designer?

**A:** Wszelkie zmiany kodu wprowadzone w pliku *UIMapDesigner.cs* są zastępowane za każdym razem, gdy generujesz kod przy użyciu **konstruktora testów interfejsu użytkownika kodowanych**. Jeśli musisz zmodyfikować zarejestrowaną metodę, skopiuj ją do *pliku UIMap.cs* i zmień jego nazwę. UIMap.cs *UIMap.cs* plik może służyć do zastępowania metod i właściwości w pliku *UIMapDesigner.cs.* Usuń odwołanie do oryginalnej metody w pliku *CodedUITest.cs* i zastąp go nazwą metody o zmienionej nazwie.

## <a name="see-also"></a>Zobacz też

- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Ustawianie unikatowych właściwości automatyzacji dla formantów platformy uniwersalnej systemu](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
