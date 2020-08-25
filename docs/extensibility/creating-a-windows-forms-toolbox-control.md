---
title: Tworzenie kontrolki przybornika Windows Forms | Microsoft Docs
description: W tym instruktażu pokazano, jak za pomocą szablonu kontrolki przybornika Windows Forms utworzyć prostą kontrolkę licznika przy użyciu zestawu Visual Studio SDK.
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8dd62c01bad3ac50a57062729fe96588a7ef5be
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801870"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Tworzenie kontrolki przybornika Windows Forms

Szablon elementu formantu Windows Forms przybornika, który jest zawarty w Visual Studio Extensibility Tools (VS SDK), umożliwia utworzenie kontrolki **przybornika** , która jest automatycznie dodawana po zainstalowaniu rozszerzenia. W tym instruktażu pokazano, jak za pomocą szablonu utworzyć prostą kontrolkę licznika, którą można dystrybuować do innych użytkowników.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Tworzenie kontrolki przybornika

Szablon kontrolki przybornika Windows Forms tworzy niezdefiniowaną kontrolkę użytkownika i udostępnia wszystkie funkcje wymagane do dodania formantu do **przybornika**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Tworzenie rozszerzenia za pomocą kontrolki przybornika Windows Forms

1. Utwórz projekt VSIX o nazwie `MyWinFormsControl` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".

2. Po otwarciu projektu Dodaj szablon elementu **formantu Windows Forms przybornika** o nazwie `Counter` . W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do rozszerzalności **Visual C#**  >  **Extensibility** i wybierz **formant Windows Forms przybornika**

3. Spowoduje to dodanie kontrolki użytkownika, a następnie `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> umieszczenie kontrolki w **przyborniku**i wpisu zasobu **Microsoft. VISUALSTUDIO. ToolboxControl** w manifeście VSIX dla wdrożenia.

### <a name="build-a-user-interface-for-the-control"></a>Tworzenie interfejsu użytkownika dla kontrolki

`Counter`Kontrolka wymaga dwóch formantów podrzędnych:, <xref:System.Windows.Forms.Label> Aby wyświetlić bieżącą liczbę i a <xref:System.Windows.Forms.Button> do resetowania liczby do 0. Nie są wymagane żadne inne kontrolki podrzędne, ponieważ wywołujący zwiększą licznik programowo.

#### <a name="to-build-the-user-interface"></a>Aby skompilować interfejs użytkownika

1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję *Counter.cs* , aby otworzyć ją w projektancie.

2. Usuń **kliknięcie tutaj!** przycisk, który jest uwzględniany domyślnie po dodaniu szablonu elementu formantu Windows Forms przybornika.

3. Z **przybornika**przeciągnij `Label` kontrolkę, a następnie `Button` kontrolkę poniżej do powierzchni projektowej.

4. Zmień rozmiar ogólnej kontrolki użytkownika na 150, 50 pikseli i Zmień rozmiar kontrolki przycisku na 50, 20 pikseli.

5. W oknie **Właściwości** ustaw następujące wartości dla kontrolek na powierzchni projektowej.

    |Kontrola|Właściwość|Wartość|
    |-------------|--------------|-----------|
    |`Label1`|**Tekst**|""|
    |`Button1`|**Nazwa**|btnReset|
    |`Button1`|**Tekst**|Reset|

### <a name="code-the-user-control"></a>Kod kontrolki użytkownika

`Counter`Kontrolka będzie uwidaczniać metodę zwiększającą licznik, zdarzenie, które ma być wywoływane za każdym razem, gdy licznik zostanie zwiększony, przycisk **Reset** i trzy właściwości do przechowywania bieżącej liczby, wyświetlanego tekstu oraz czy ukrywania przycisku **resetowania** . `ProvideToolboxControl`Atrybut określa, gdzie w **przyborniku** `Counter` zostanie wyświetlony formant.

#### <a name="to-code-the-user-control"></a>Aby zakodować kontrolkę użytkownika

1. Kliknij dwukrotnie formularz, aby otworzyć jego procedurę obsługi zdarzeń ładowania w oknie kod.

2. Powyżej metody obsługi zdarzeń w klasie Control Utwórz liczbę całkowitą do przechowywania wartości licznika i ciąg do przechowywania wyświetlanego tekstu, jak pokazano w poniższym przykładzie.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Utwórz następujące publiczne deklaracje właściwości.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Obiekty wywołujące mogą uzyskać dostęp do tych właściwości, aby uzyskać i ustawić wyświetlany tekst licznika oraz wyświetlić lub ukryć przycisk **Resetuj** . Obiekty wywołujące mogą uzyskać bieżącą wartość właściwości tylko do odczytu `Value` , ale nie mogą ustawiać wartości bezpośrednio.

4. Umieść poniższy kod w `Load` zdarzeniu dla kontrolki.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Ustawienie tekstu **etykiety** w <xref:System.Windows.Forms.UserControl.Load> zdarzeniu umożliwia załadowanie właściwości docelowych przed zastosowaniem ich wartości. Ustawienie tekstu **etykiety** w konstruktorze spowoduje powstanie pustej **etykiety**.

5. Utwórz poniższą metodę publiczną w celu zwiększenia licznika.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Dodaj deklarację dla `Incremented` zdarzenia do klasy Control.

    ```csharp
    public event EventHandler Incremented;
    ```

    Obiekty wywołujące mogą dodawać programy obsługi do tego zdarzenia w celu reagowania na zmiany wartości licznika.

7. Wróć do widoku projektu i kliknij dwukrotnie przycisk **Resetuj** , aby wygenerować `btnReset_Click` procedurę obsługi zdarzeń. Następnie wypełnij go, tak jak pokazano w poniższym przykładzie.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Bezpośrednio powyżej definicji klasy w `ProvideToolboxControl` deklaracji atrybutu Zmień wartość pierwszego parametru z `"MyWinFormsControl.Counter"` na `"General"` . Ustawia nazwę grupy elementów, która będzie hostować formant w **przyborniku**.

    Poniższy przykład pokazuje `ProvideToolboxControl` atrybut i dostosowaną definicję klasy.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Testowanie kontrolki

 Aby przetestować kontrolkę **przybornika** , najpierw przetestuj ją w środowisku programistycznym, a następnie przetestuj ją w skompilowanej aplikacji.

#### <a name="to-test-the-control"></a>Aby przetestować kontrolkę

1. Naciśnij klawisz **F5** , aby **rozpocząć debugowanie**.

    To polecenie kompiluje projekt i otwiera drugie doświadczalne wystąpienie programu Visual Studio z zainstalowanym formantem.

2. W eksperymentalnym wystąpieniu programu Visual Studio Utwórz projekt **aplikacji Windows Forms** .

3. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję *Form1.cs* , aby otworzyć ją w projektancie, jeśli nie jest jeszcze otwarta.

4. W **przyborniku** `Counter` kontrolka powinna być wyświetlana w sekcji **Ogólne** .

5. Przeciągnij `Counter` formant do formularza, a następnie wybierz go. `Value`Właściwości, `Message` , i `ShowReset` będą wyświetlane w oknie **Właściwości** wraz z właściwościami dziedziczonymi z <xref:System.Windows.Forms.UserControl> .

6. Ustaw `Message` Właściwość na wartość `Count:` .

7. Przeciągnij <xref:System.Windows.Forms.Button> formant do formularza, a następnie ustaw właściwości Nazwa i tekst przycisku na `Test` .

8. Kliknij dwukrotnie przycisk, aby otworzyć *Form1.cs* w widoku kodu i utworzyć procedurę obsługi kliknięcia.

9. W procedurze obsługi kliknij polecenie Wywołaj `counter1.Increment()` .

10. W funkcji konstruktora po wywołaniu do `InitializeComponent` wpisz, `counter1``.``Incremented +=` a następnie naciśnij klawisz **Tab** dwa razy.

    Program Visual Studio generuje procedurę obsługi dla `counter1.Incremented` zdarzenia.

11. Zaznacz `Throw` instrukcję w programie obsługi zdarzeń, wpisz `mbox` , a następnie naciśnij dwukrotnie klawisz **Tab** , aby wygenerować okno komunikatu na podstawie fragmentu kodu mbox.

12. W następnym wierszu Dodaj następujący `if` / `else` blok, aby ustawić widoczność przycisku **Resetuj** .

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Naciśnij klawisz **F5**.

    Zostanie otwarty formularz. `Counter`Kontrolka wyświetla następujący tekst.

    **Liczba: 0**

14. Kliknij przycisk **Testuj**.

    Licznik rośnie i program Visual Studio Wyświetla okno komunikatu.

15. Zamknij okno komunikatu.

    Przycisk **Resetuj** znika.

16. Wybierz **test** , dopóki licznik osiągnie **5** , zamykając pola komunikatów za każdym razem.

    Przycisk **Resetuj** zostanie wyświetlony ponownie.

17. Wybierz pozycję **Resetuj**.

    Licznik resetuje do wartości **0**.

## <a name="next-steps"></a>Następne kroki

Po utworzeniu kontrolki **przybornika** program Visual Studio tworzy plik o nazwie *ProjectName. vsix* w folderze \bin\debug\ projektu. Formant można wdrożyć, przekazując plik *. vsix* do sieci lub do witryny sieci Web. Gdy użytkownik otworzy plik *. vsix* , formant zostanie zainstalowany i dodany do **przybornika** programu Visual Studio na komputerze użytkownika. Alternatywnie można przekazać plik *VSIX* do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , aby użytkownicy mogli go znaleźć, przechodząc do **Tools**  >  okna dialogowego**rozszerzenia i aktualizacje** narzędzi.

## <a name="see-also"></a>Zobacz też

- [Rozszerzając inne części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Tworzenie kontrolki przybornika WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Rozszerzając inne części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Podstawowe informacje dotyczące programowania formantów Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
