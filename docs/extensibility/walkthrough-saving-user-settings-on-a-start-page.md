---
title: 'Przewodnik: Zapisywanie ustawień użytkownika na stronie początkowej | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2362bda715a95e4228b6e4f882f1f8fb708667dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62964784"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Przewodnik: Zapisz ustawienia użytkownika na stronie sieci uruchomić

Jednak można utrwalić ustawienia użytkownika dla stronę początkową. Dzięki temu przewodnikowi, można utworzyć formant, który zapisuje ustawienie w rejestrze, gdy użytkownik kliknie przycisk, a następnie pobiera ustawienie za każdym razem, gdy ładowania strony początkowej. Ponieważ szablon projektu strona początkowa zawiera kontrolki użytkownika można dostosowywać, a domyślny Start strony XAML wywołuje tę kontrolkę, nie trzeba modyfikować strony początkowej, sam.

Ustawienia magazynu, który zostanie uruchomiony w ramach tego przewodnika jest wystąpieniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interfejs, który odczytuje i zapisuje je w następującej lokalizacji rejestru, gdy wywoływana jest: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<CollectionName>**

Gdy uruchomiona jest w doświadczalnym wystąpieniu programu Visual Studio, z magazynu ustawień wykonującej Odczyt i zapis **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<nazwa_kolekcji >.**

Aby uzyskać więcej informacji o tym, jak w celu utrzymania ustawień, zobacz [rozszerzanie ustawień użytkownika ani opcji](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Wymagania wstępne

> [!NOTE]
> Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Szablon projektu strona startowa można pobrać przy użyciu **Menedżera rozszerzeń**.

## <a name="set-up-the-project"></a>Konfigurowanie projektu

1. Utwórz projekt strony początkowej, zgodnie z opisem w [Tworzenie niestandardowej strony początkowej](creating-a-custom-start-page.md). Nadaj projektowi nazwę **SaveMySettings**.

2. W **Eksploratora rozwiązań**, Dodaj następujące odwołania do zestawów do projektu StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Otwórz *MyControl.xaml*.

4. Z poziomu okienka XAML w najwyższego poziomu <xref:System.Windows.Controls.UserControl> definicja elementu, dodaj następującą deklarację zdarzeń po deklaracjach przestrzeni nazw.

    ```xml
    Loaded="OnLoaded"
    ```

5. W okienku projektowania kliknij główny obszar formantu, a następnie naciśnij klawisz **Usuń**.

     Ten krok usuwa <xref:System.Windows.Controls.Border> elementu, a cała zawartość i pozostawienie tylko najwyższego poziomu <xref:System.Windows.Controls.Grid> elementu.

6. Z **przybornika**, przeciągnij <xref:System.Windows.Controls.StackPanel> formant do siatki.

7. Teraz przeciągnij <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>oraz przycisk umożliwiający wymianę <xref:System.Windows.Controls.StackPanel>.

8. Dodaj **x: Name** atrybutu dla <xref:System.Windows.Controls.TextBox>, a `Click` zdarzenia <xref:System.Windows.Controls.Button>, jak pokazano w poniższym przykładzie.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementowanie formantu użytkownika

1. W okienku XAML, kliknij prawym przyciskiem myszy `Click` atrybutu <xref:System.Windows.Controls.Button> elementu, a następnie kliknij przycisk **przejdź do procedury obsługi zdarzeń**.

     Ten krok otwiera *MyControl.xaml.cs*i tworzy obsługi wycinka `Button_Click` zdarzeń.

2. Dodaj następujący kod `using` instrukcji na górze pliku.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Dodaj prywatnej `SettingsStore` właściwości, jak pokazano w poniższym przykładzie.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Ta właściwość najpierw pobiera odwołanie do <xref:EnvDTE80.DTE2> interfejs, który zawiera model obiektowy automatyzacji z <xref:System.Windows.FrameworkElement.DataContext%2A> kontrolki użytkownika, a następnie używa DTE wystąpienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interfejsu. Następnie używa tego wystąpienia, aby przywrócić bieżące ustawienia użytkownika.

4. Wypełnij `Button_Click` zdarzeń w następujący sposób.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     To zapisuje zawartość pola tekstowego do pola "MySetting" w kolekcji "MySettings" w rejestrze. Jeśli kolekcja nie istnieje, zostanie utworzony.

5. Dodaj następujący program obsługi dla `OnLoaded` zdarzeń kontrolki użytkownika.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Ten kod ustawia tekst pola tekstowego do bieżącej wartości "MySetting".

6. Tworzenie kontrolki użytkownika.

7. W **Eksploratora rozwiązań**, otwórz *source.extension.vsixmanifest*.

8. W edytorze manifestu zestawu **nazwa produktu** do **Zapisz moje ustawienia strony początkowej**.

     Ta funkcja ustawia nazwę strony początkowej, jak pojawiają się w **Dostosuj stronę początkową** listy w **opcje** okno dialogowe.

9. Tworzenie *StartPage.xaml*.

## <a name="test-the-control"></a>Przetestować formant

1. Naciśnij klawisz **F5**.

     Otwiera doświadczalne wystąpienie programu Visual Studio.

2. W doświadczalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **opcje**.

3. W **środowiska** węzła, kliknij przycisk **uruchamiania**, a następnie w **Dostosuj stronę początkową** listy wybierz **[zainstalowane rozszerzenie] Zapisz moje ustawienia stronę początkową** .

     Kliknij przycisk **OK**.

4. Zamknij stronę początkową, jeśli jest otwarty, a następnie na **widoku** menu, kliknij przycisk **strona startowa**.

5. Na stronie początkowej kliknij **MójFormant** kartę.

6. W polu tekstowym wpisz **Cat**, a następnie kliknij przycisk **Zapisz moje ustawienia**.

7. Zamknij stronę początkową, a następnie otwórz go ponownie.

     Słowo "Cat" powinna być wyświetlana w polu tekstowym.

8. Zastąp słowo "Cat" słowa "Dog". Nie klikaj przycisku.

9. Zamknij stronę początkową, a następnie otwórz go ponownie.

     Słowo "Dog" powinna być wyświetlana w polu tekstowym, mimo że nawet jeśli ich zostaną zamknięte, aż do zamknięcia programu Visual Studio nie został zapisany ustawienie ponieważ Visual Studio przechowuje okien narzędzi w pamięci.

10. Zamknij wystąpienie doświadczalne programu Visual Studio.

11. Naciśnij klawisz **F5** ponownie otworzyć wystąpienie eksperymentalne.

12. Słowo "Cat" powinna być wyświetlana w polu tekstowym.

## <a name="next-steps"></a>Następne kroki

Można zmodyfikować ten formant użytkownika, aby zapisać i pobrać dowolną liczbę niestandardowych ustawień przy użyciu różnych wartości z procedury obsługi zdarzeń do pobierania i ustawiania `SettingsStore` właściwości. Tak długo, jak możesz użyć innego `propertyName` parametrów dla każdego wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, wartości nie zastępowały siebie nawzajem w rejestrze.

## <a name="see-also"></a>Zobacz także

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)