---
title: Tworzenie Windows Forms kontrolki przybornika | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57b711d91e50d0aecb579f7d02afe2123e365425
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316590"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Tworzenie kontrolki przybornika Windows Forms
Szablon elementu kontrolki formularzy Windows Forms przybornika, który znajduje się w Visual Studio Tools Extensibility (zestaw SDK programu VS) pozwala utworzyć formant, który jest automatycznie dodawany do **przybornika** po zainstalowaniu rozszerzenia. W tym temacie pokazano, jak utworzyć formant prostego licznika, który można rozdystrybuować innym użytkownikom za pomocą szablonu.

## <a name="prerequisites"></a>Wymagania wstępne
Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-windows-forms-toolbox-control"></a>Tworzenie kontrolki przybornika Windows Forms
Szablon kontrolki Przybornika formularzy Windows tworzy kontrolkę użytkownika niezdefiniowane i zawiera wszystkie funkcje, które jest wymagane, aby dodać formant do **przybornika**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Tworzenie rozszerzenia za pomocą kontrolki przybornika Windows Forms

1. Utwórz projekt VSIX, o nazwie `MyWinFormsControl`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C#** > **rozszerzalności**.

2. Po otwarciu projektu, Dodaj **kontrolki formularzy Windows Forms przybornika** szablon elementu o nazwie `Counter`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C#** > **rozszerzalności** i wybierz **kontrolki formularzy Windows Forms przybornika**

3. Spowoduje to dodanie kontrolkę użytkownika `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> aby umieścić kontrolkę w **przybornika**, a **Microsoft.VisualStudio.ToolboxControl** wpis zawartości w manifestu VSIX do wdrożenia.

### <a name="build-a-user-interface-for-the-control"></a>Tworzenie interfejsu użytkownika dla formantu
`Counter` Formant wymaga dwóch kontrolek podrzędnych: <xref:System.Windows.Forms.Label> Aby wyświetlić bieżącą liczbę i <xref:System.Windows.Forms.Button> zresetować liczby 0. Brak kontrolek podrzędnych są wymagane, ponieważ obiekty wywołujące powoduje zwiększenie licznika programowo.

#### <a name="to-build-the-user-interface"></a>Tworzenie interfejsu użytkownika

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie *Counter.cs* aby go otworzyć w projektancie.

2. Usuń **kliknij tutaj!** przycisk, który jest domyślnie podczas dodawania szablonu elementu kontrolki formularzy Windows Forms przybornika.

3. Z **przybornika**, przeciągnij `Label` kontroli i następnie `Button` kontroli poniżej go do powierzchni projektowej.

4. Zmień rozmiar ogólną kontrolkę użytkownika do 150, 50 pikseli, a następnie zmień rozmiar przycisku sterowania do 50, 20 pikseli.

5. W **właściwości** okna, ustaw następujące wartości dla formantów na powierzchni projektowej.

    |formant|Właściwość|Wartość|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**Nazwa**|btnReset|
    |`Button1`|**Text**|Resetuj|

### <a name="code-the-user-control"></a>Kod kontroli użytkownika
`Counter` Kontroli udostępni metodę, aby zwiększyć licznik, wystąpienie zdarzenia wywoływane, gdy licznik jest zwiększany, **resetowania** przycisk i trzy właściwości do przechowywania bieżąca liczba, tekst wyświetlany i czy ma być wyświetlana lub ukryć **resetowania** przycisku. `ProvideToolboxControl` Atrybut określa, w którym miejscu **przybornika** `Counter` pojawi się kontrolka.

#### <a name="to-code-the-user-control"></a>Do kodu kontrolki użytkownika

1. Kliknij dwukrotnie formularza, aby otworzyć jej obciążenia obsługi zdarzeń w oknie kodu.

2. Powyżej metodę programu obsługi zdarzeń w klasie kontrolki, należy utworzyć na liczbę całkowitą określającą wartość licznika i ciągu do przechowywania tekstu wyświetlanego, jak pokazano w poniższym przykładzie.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Utwórz następujące deklaracje właściwości publicznej.

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

    Obiekty wywołujące dostęp tych właściwości, pobieranie i ustawianie wyświetlanego tekstu licznika, jak i aby pokazać lub ukryć **resetowania** przycisku. Obiekty wywołujące można uzyskać bieżącą wartość tylko do odczytu `Value` właściwości, ale nie można ustawić wartość bezpośrednio.

4. Umieść następujący kod `Load` zdarzeń dla formantu.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Ustawienie **etykiety** tekstu w <xref:System.Windows.Forms.UserControl.Load> zdarzeń umożliwia właściwości obiektu docelowego załadować przed ich wartości są stosowane. Ustawienie **etykiety** tekstu w Konstruktorze mogłoby spowodować pustą **etykiety**.

5. Utwórz następującą metodę publicznej, aby zwiększyć licznik.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Dodaj deklarację dla `Incremented` zdarzeń do klasy formantu.

    ```csharp
    public event EventHandler Incremented;
    ```

    Obiekty wywołujące można dodać procedury obsługi do tego zdarzenia, aby odpowiadanie na zmiany w wartość licznika.

7. Powrót do widoku projektu, a następnie kliknij dwukrotnie ikonę **resetowania** przycisk, aby wygenerować `btnReset_Click` programu obsługi zdarzeń i wypełnić ją w, jak pokazano w poniższym przykładzie.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Bezpośrednio nad definicji klasy w `ProvideToolboxControl` atrybutu deklaracji, zmień wartość pierwszego parametru z `"MyWinFormsControl.Counter"` do `"General"`. Spowoduje to nazwa grupy elementów, który będzie obsługiwać formant w **przybornika**.

    W poniższym przykładzie przedstawiono `ProvideToolboxControl` atrybut i definicji klasy dostosowane.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Przetestować formant
 Aby przetestować **przybornika** kontrolować, najpierw przetestować w środowisku deweloperskim i przetestować go skompilowanej aplikacji.

#### <a name="to-test-the-control"></a>Aby przetestować formant

1. Naciśnij klawisz **F5**.

    Tworzy projekt i otwiera drugie wystąpienie eksperymentalne programu Visual Studio ma kontrolę zainstalowane.

2. W doświadczalnym wystąpieniu programu Visual Studio, należy utworzyć **aplikacja interfejsu Windows Forms** projektu.

3. W **Eksploratora rozwiązań**, kliknij dwukrotnie *Form1.cs* aby otworzyć go w projektancie, jeśli nie jest jeszcze otwarty.

4. W **przybornika**, `Counter` powinien być wyświetlany formantu w **ogólne** sekcji.

5. Przeciągnij `Counter` sterowania do formularza, a następnie wybierz ją. `Value`, `Message`, I `ShowReset` właściwości będą wyświetlane w **właściwości** okna wraz z właściwościami, które są dziedziczone z <xref:System.Windows.Forms.UserControl>.

6. Ustaw `Message` właściwość `Count:`.

7. Przeciągnij <xref:System.Windows.Forms.Button> sterowania do formularza, a następnie ustaw właściwości name i tekstu przycisku, aby `Test`.

8. Kliknij dwukrotnie przycisk aby otworzyć *Form1.cs* w widok kodu i obsługi kliknij przycisk Utwórz.

9. W procedurze obsługi kliknij przycisk Wywołaj `counter1.Increment()`.

10. W funkcji konstruktora, po wywołaniu `InitializeComponent`, typ `counter1``.``Incremented +=` , a następnie naciśnij klawisz **kartę** dwa razy.

    Program Visual Studio generuje procedury obsługi na poziomie formularza potrzeby `counter1.Incremented` zdarzeń.

11. Wyróżnij `Throw` instrukcji w obsłudze zdarzeń typu `mbox`, a następnie naciśnij klawisz **kartę** dwa razy, aby wygenerować okno komunikatu z mbox fragmentu kodu.

12. W następnym wierszu, Dodaj następujący kod `if` / `else` bloku, aby ustawić widoczność **resetowania** przycisku.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Naciśnij klawisz **F5**.

    Po otwarciu formularza. `Counter` Następujący tekst jest wyświetlany formantu.

    **Liczba: 0**

14. Kliknij przycisk **testu**.

    Zwiększa licznik i programu Visual Studio Wyświetla okno komunikatu.

15. Zamknij okno komunikatu.

    **Resetowania** przycisk zniknie.

16. Kliknij przycisk **testu** do momentu osiągnięcia licznik **5** zamknięciu komunikatu pola każdorazowo.

    **Resetowania** przycisk ponownie jest wyświetlany.

17. Kliknij przycisk **resetowania**.

    Resetuje licznik **0**.

## <a name="next-steps"></a>Następne kroki
Podczas kompilowania **przybornika** formant, Visual Studio tworzy plik o nazwie *ProjectName.vsix* w folderze \bin\debug\ projektu. Kontrolki można wdrożyć, przekazując *.vsix* plików do sieci lub do witryny sieci Web. Gdy użytkownik uruchomi *.vsix* plik, formant został zainstalowany i dodane do programu Visual Studio **przybornika** na komputerze użytkownika. Alternatywnie, możesz przekazać *.vsix* plik [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkID=123847) tak, aby użytkownicy mogli ją znaleźć, przechodząc w **narzędzia**  >   **Rozszerzenia i aktualizacje** okna dialogowego.

## <a name="see-also"></a>Zobacz także
[Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
[Tworzenie kontrolki przybornika WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
[Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
[Podstawy programowania dla formantu Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
