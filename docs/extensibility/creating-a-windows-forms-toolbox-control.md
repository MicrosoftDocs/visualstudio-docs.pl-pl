---
title: Tworzenie formantu zestawu narzędzi formularzy systemu Windows | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739580"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Tworzenie kontrolki zestawu narzędzi formularzy systemu Windows

Szablon elementu formant pakietu Windows Forms Toolbox, który znajduje się w narzędziach rozszerzalności programu Visual Studio (VS SDK), umożliwia utworzenie formantu **przybornika,** który jest automatycznie dodawany po zainstalowaniu rozszerzenia. W tym przewodniku pokazano, jak użyć szablonu do utworzenia prostego formantu licznika, który można rozpowszechniać wśród innych użytkowników.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Tworzenie kontrolki przybornika

Szablon Formant zestawu narzędzi formularzy systemu Windows tworzy niezdefiniowany formant użytkownika i zapewnia wszystkie funkcje wymagane do dodania formantu do **przybornika**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Tworzenie rozszerzenia za pomocą kontrolki zestawu narzędzi Windows Forms

1. Utwórz projekt VSIX o nazwie `MyWinFormsControl`. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Po otwarciu projektu dodaj szablon elementu **formantu zestawu narzędzi windows forms** o nazwie `Counter`. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji**Rozszerzalność** **programu Visual C#** > i wybierz **pozycję Formant zestawu narzędzi formularzy systemu Windows**

3. Spowoduje to dodanie formantu użytkownika, a `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> do umieszczenia formantu w **przyborniku**i **wpisu zasobu Microsoft.VisualStudio.ToolboxControl** w manifeście VSIX do wdrożenia.

### <a name="build-a-user-interface-for-the-control"></a>Tworzenie interfejsu użytkownika dla formantu

Formant `Counter` wymaga dwóch elementów sterujących podrzędnych: a <xref:System.Windows.Forms.Label> do wyświetlania bieżącej liczby i a, <xref:System.Windows.Forms.Button> aby zresetować liczbę do 0. Nie są wymagane żadne inne formanty podrzędne, ponieważ wywołujący będą zwiększać licznik programowo.

#### <a name="to-build-the-user-interface"></a>Aby utworzyć interfejs użytkownika

1. W **Eksploratorze rozwiązań**kliknij dwukrotnie *Counter.cs,* aby otworzyć go w projektancie.

2. Usuń **Kliknij tutaj!** przycisk, który jest domyślnie dołączony podczas dodawania szablonu elementu kontrolki zestawu narzędzi formularzy windows.

3. Z **przybornika**przeciągnij `Label` formant, a następnie formant `Button` pod nim na powierzchnię projektową.

4. Zmienić rozmiar ogólnego formantu użytkownika do 150, 50 pikseli i zmienić rozmiar formantu przycisku do 50, 20 pikseli.

5. W oknie **Właściwości** ustaw następujące wartości formantu na powierzchni projektowej.

    |Kontrola|Właściwość|Wartość|
    |-------------|--------------|-----------|
    |`Label1`|**Tekst**|""|
    |`Button1`|**Nazwa**|btnReset (zestaw btnReset)|
    |`Button1`|**Tekst**|Reset|

### <a name="code-the-user-control"></a>Kodowanie formantu użytkownika

Formant `Counter` będzie uwidaczniać metodę, aby przyrost licznika, zdarzenie, które mają być wywoływane, gdy licznik jest zwiększany, **reset** przycisk i trzy właściwości do przechowywania bieżącej liczby, wyświetlany tekst i czy pokazać lub ukryć **przycisk Reset.** Atrybut `ProvideToolboxControl` określa, gdzie w **przyborniku** `Counter` pojawi się formant.

#### <a name="to-code-the-user-control"></a>Aby zakodować formant użytkownika

1. Kliknij dwukrotnie formularz, aby otworzyć jego program obsługi zdarzeń ładowania w oknie kodu.

2. Powyżej metody obsługi zdarzeń w klasie formantu utwórz całkowitą do przechowywania wartości licznika i ciąg do przechowywania tekstu wyświetlanego, jak pokazano w poniższym przykładzie.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Utwórz następujące deklaracje właściwości publicznych.

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

    Osoby dzwoniące mogą uzyskać dostęp do tych właściwości, aby uzyskać i ustawić wyświetlany tekst licznika oraz pokazać lub ukryć przycisk **Reset.** Obiekt wywołujący można uzyskać bieżącą `Value` wartość właściwości tylko do odczytu, ale nie można ustawić wartość bezpośrednio.

4. Umieść następujący kod `Load` w zdarzeniu dla formantu.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Ustawienie **Label** tekst <xref:System.Windows.Forms.UserControl.Load> w zdarzeniu umożliwia właściwości docelowe, aby załadować przed ich wartości są stosowane. Ustawienie tekstu **etykiety** w konstruktorze spowodowałoby powstanie pustej **etykiety**.

5. Utwórz następującą metodę publiczną, aby zwiększać licznik.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Dodaj deklarację `Incremented` dla zdarzenia do klasy kontrolnej.

    ```csharp
    public event EventHandler Incremented;
    ```

    Obiekty wywołujące można dodać programy obsługi do tego zdarzenia, aby odpowiedzieć na zmiany wartości licznika.

7. Wróć do widoku projektu i kliknij dwukrotnie `btnReset_Click` przycisk **Reset,** aby wygenerować program obsługi zdarzeń, a następnie wypełnij go, jak pokazano w poniższym przykładzie.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Bezpośrednio powyżej definicji klasy `ProvideToolboxControl` w deklaracji atrybutu zmień wartość `"MyWinFormsControl.Counter"` pierwszego `"General"`parametru z . Spowoduje to ustawienie nazwy grupy elementów, która będzie obsługiwać formant w **przyborniku**.

    Poniższy przykład `ProvideToolboxControl` przedstawia atrybut i definicji klasy dostosowane.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Przetestuj formant

 Aby przetestować formant **przybornika,** najpierw przetestuj go w środowisku programistycznym, a następnie przetestuj w skompilowaną aplikację.

#### <a name="to-test-the-control"></a>Aby przetestować formant

1. Naciśnij **klawisz F5,** aby **rozpocząć debugowanie**.

    To polecenie tworzy projekt i otwiera drugie eksperymentalne wystąpienie programu Visual Studio, w których zainstalowano formant.

2. W eksperymentalnym wystąpieniu programu Visual Studio utwórz projekt **aplikacji formularzy systemu Windows.**

3. W **Eksploratorze rozwiązań**kliknij dwukrotnie *Form1.cs,* aby otworzyć go w projektancie, jeśli nie jest jeszcze otwarty.

4. W **przyborniku**formant `Counter` powinien być wyświetlany w sekcji **Ogólne.**

5. Przeciągnij `Counter` formant do formularza, a następnie zaznacz go. `Message` `ShowReset` Właściwości `Value`i właściwości zostaną wyświetlone w oknie **Właściwości** wraz z właściwościami dziedziczonymi po <xref:System.Windows.Forms.UserControl>.

6. Ustaw `Message` właściwość `Count:`na .

7. Przeciągnij <xref:System.Windows.Forms.Button> formant do formularza, a następnie ustaw nazwę i `Test`właściwości tekstu przycisku na .

8. Kliknij dwukrotnie przycisk, aby otworzyć *Form1.cs* w widoku kodu i utworzyć program obsługi kliknięć.

9. W programie obsługi `counter1.Increment()`kliknięć zadzwoń .

10. W funkcji konstruktora po `InitializeComponent`wywołaniu do , wpisz, `counter1``.``Incremented +=` a następnie naciśnij tab dwa razy. **Tab**

    Visual Studio generuje program obsługi na `counter1.Incremented` poziomie formularza dla zdarzenia.

11. Wyróżnij `Throw` instrukcję w programie `mbox`obsługi zdarzeń, wpisz , a następnie naciśnij dwukrotnie **klawisz Tab,** aby wygenerować okno komunikatu z fragmentu kodu mbox.

12. W następnym wierszu dodaj `if` / `else` następujący blok, aby ustawić widoczność przycisku **Reset.**

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Naciśnij klawisz **F5**.

    Zostanie otwarty formularz. W `Counter` formancie wyświetlany jest następujący tekst.

    **Liczba: 0**

14. Kliknij **przycisk Testuj**.

    Licznik przyrosty i Visual Studio wyświetla okno komunikatu.

15. Zamknij okno komunikatu.

    Przycisk **Reset zniknie.**

16. Kliknij **przycisk Testuj,** aż licznik osiągnie **5** zamykających pola wiadomości za każdym razem.

    Przycisk **Resetuj** pojawi się ponownie.

17. Kliknij **przycisk Resetuj**.

    Licznik resetuje się do **0**.

## <a name="next-steps"></a>Następne kroki

Podczas tworzenia formantu **przybornika** program Visual Studio tworzy plik o nazwie *ProjectName.vsix* w folderze \bin\debug\ projektu. Formant można wdrożyć, przekazując plik *vsix* do sieci lub do witryny sieci Web. Gdy użytkownik otworzy plik *vsix,* formant jest instalowany i dodawany do **zestawu narzędzi** Visual Studio na komputerze użytkownika. Alternatywnie można przekazać plik *vsix* do [programu Visual Studio Marketplace,](https://marketplace.visualstudio.com/) dzięki czemu użytkownicy mogą go znaleźć, przeglądając w oknie dialogowym**Rozszerzenia i aktualizacje** **narzędzi.** > 

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Tworzenie kontrolki przybornika WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Podstawowe informacje o rozwoju formularzy systemu Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
