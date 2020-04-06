---
title: 'Przewodnik: Zapisywanie ustawień użytkownika na stronie startowej | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697069"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Instruktaż: zapisywanie ustawień użytkownika na stronie początkowej

Możesz upierać się ustawienia użytkownika strony początkowej. Wykonując ten instruktaż, można utworzyć formant, który zapisuje ustawienie w rejestrze, gdy użytkownik kliknie przycisk, a następnie pobiera to ustawienie za każdym razem, gdy strona początkowa jest wczytyty. Ponieważ szablon projektu strona początkowa zawiera konfigurowalny formant użytkownika, a domyślny element XAML strony początkowej wywołuje tę kontrolkę, nie trzeba modyfikować samej strony początkowej.

Magazyn ustawień, który jest wystąpienia w tym instruktażu jest wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interfejsu, który odczytuje i zapisuje do następującej lokalizacji rejestru, gdy jest wywoływana: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<CollectionName>**

Po uruchomieniu w eksperymentalnym wystąpieniu programu Visual Studio magazyn ustawień odczytuje i zapisuje w **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<CollectionName>.**

Aby uzyskać więcej informacji na temat zachowywania ustawień, zobacz [Rozszerzanie ustawień i opcji użytkownika](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Wymagania wstępne

> [!NOTE]
> Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Szablon projektu Strona początkowa można pobrać za pomocą **Menedżera rozszerzeń**.

## <a name="set-up-the-project"></a>Konfigurowanie projektu

1. Tworzenie projektu strony początkowej zgodnie z opisem w [polu Tworzenie niestandardowej strony początkowej](creating-a-custom-start-page.md). Nazwij projekt **SaveMySettings**.

2. W **Eksploratorze rozwiązań**dodaj następujące odwołania do zestawu do projektu StartPageControl:

    - Envdte

    - EnvDTE80 ( EnvDTE0 )

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Otwórz *plik MyControl.xaml*.

4. W okienku XAML w definicji <xref:System.Windows.Controls.UserControl> elementu najwyższego poziomu dodaj następującą deklarację zdarzeń po deklaracjach obszaru nazw.

    ```xml
    Loaded="OnLoaded"
    ```

5. W okienku projektowym kliknij główny obszar formantu, a następnie naciśnij klawisz **Delete**.

     Ten krok usuwa <xref:System.Windows.Controls.Border> element i wszystko w nim i <xref:System.Windows.Controls.Grid> pozostawia tylko najwyższego poziomu elementu.

6. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Controls.StackPanel> do siatki.

7. Teraz przeciągnij <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox>, , i <xref:System.Windows.Controls.StackPanel>przycisk do .

8. Dodaj atrybut **x:Name** dla <xref:System.Windows.Controls.TextBox>, `Click` i zdarzenie <xref:System.Windows.Controls.Button>dla , jak pokazano w poniższym przykładzie.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementowanie formantu użytkownika

1. W okienku XAML kliknij prawym `Click` przyciskiem <xref:System.Windows.Controls.Button> myszy atrybut elementu, a następnie kliknij polecenie **Przejdź do programu Obsługi zdarzeń**.

     Ten krok otwiera *MyControl.xaml.cs*i tworzy program obsługi `Button_Click` skrótowej dla zdarzenia.

2. Dodaj następujące `using` dyrektywy do górnej części pliku.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Dodaj własność `SettingsStore` prywatną, jak pokazano w poniższym przykładzie.

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

     Ta właściwość najpierw pobiera <xref:EnvDTE80.DTE2> odwołanie do interfejsu, który zawiera <xref:System.Windows.FrameworkElement.DataContext%2A> model obiektu automatyzacji, z formantu użytkownika, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> a następnie używa DTE, aby uzyskać wystąpienie interfejsu. Następnie używa tego wystąpienia, aby zwrócić bieżące ustawienia użytkownika.

4. Wypełnij `Button_Click` zdarzenie w następujący sposób.

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

     Spowoduje to zapisanie zawartości pola tekstowego w polu "MySetting" w kolekcji "MySettings" w rejestrze. Jeśli kolekcja nie istnieje, jest tworzony.

5. Dodaj następujący program `OnLoaded` obsługi dla zdarzenia formantu użytkownika.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Ten kod ustawia tekst pola tekstowego na bieżącą wartość "MySetting".

6. Tworzenie kontroli użytkownika.

7. W **Eksploratorze rozwiązań**, open *source.extension.vsixmanifest*.

8. W edytorze manifestów ustaw **nazwę produktu** tak, aby **strona początkowa zapisywania moich ustawień**.

     Ta funkcja ustawia nazwę strony początkowej, która ma być wyświetlana na liście **Dostosowywanie strony początkowej** w oknie dialogowym **Opcje.**

9. Tworzenie *strony StartPage.xaml*.

## <a name="test-the-control"></a>Przetestuj formant

1. Naciśnij klawisz **F5**.

     Zostanie otwarte eksperymentalne wystąpienie programu Visual Studio.

2. W przypadku wystąpienia eksperymentalnego w menu **Narzędzia** kliknij polecenie **Opcje**.

3. W węźle **Środowisko** kliknij pozycję **Uruchamianie**, a następnie na liście **Dostosuj stronę startową** wybierz pozycję **[Zainstalowane rozszerzenie] Zapisz stronę początkową moich ustawień**.

     Kliknij przycisk **OK**.

4. Zamknij stronę początkową, jeśli jest otwarta, a następnie w menu **Widok** kliknij polecenie **Strona początkowa**.

5. Na stronie początkowej kliknij kartę **MyControl.**

6. W polu tekstowym wpisz polecenie **Kot**, a następnie kliknij pozycję **Zapisz moje ustawienie**.

7. Zamknij stronę początkową, a następnie otwórz ją ponownie.

     W polu tekstowym powinno być wyświetlane słowo "Kot".

8. Zastąp słowo "Kot" słowem "Pies". Nie klikaj przycisku.

9. Zamknij stronę początkową, a następnie otwórz ją ponownie.

     Słowo "Pies" powinny być wyświetlane w polu tekstowym, nawet jeśli nie zapisać ustawienie, ponieważ visual studio przechowuje okna narzędzia w pamięci, nawet jeśli są one zamknięte, dopóki visual studio się zamyka.

10. Zamknij eksperymentalne wystąpienie programu Visual Studio.

11. Naciśnij **klawisz F5,** aby ponownie otworzyć wystąpienie eksperymentalne.

12. W polu tekstowym powinno być wyświetlane słowo "Kot".

## <a name="next-steps"></a>Następne kroki

Można zmodyfikować ten formant użytkownika, aby zapisać i pobrać dowolną liczbę ustawień niestandardowych `SettingsStore` przy użyciu różnych wartości z różnych programów obsługi zdarzeń, aby uzyskać i ustawić właściwość. Tak długo, jak `propertyName` używasz innego <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>parametru dla każdego wywołania, wartości nie zastępują się nawzajem w rejestrze.

## <a name="see-also"></a>Zobacz też

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
