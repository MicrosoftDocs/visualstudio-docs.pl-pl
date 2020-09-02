---
title: 'Przewodnik: zapisywanie ustawień użytkownika na stronie startowej | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8dd20513defd1db8848cf6a80a29e04c127c9dd4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903162"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Przewodnik: zapisywanie ustawień użytkownika na stronie początkowej

Ustawienia użytkownika można zachować na stronie początkowej. Postępując zgodnie z tym przewodnikiem, można utworzyć formant, który zapisuje ustawienie w rejestrze, gdy użytkownik kliknie przycisk, a następnie pobiera to ustawienie za każdym razem, gdy strona początkowa zostanie załadowana. Ponieważ szablon projektu strony startowej zawiera dostosowywalną kontrolkę użytkownika i domyślne wywołania XAML strony początkowej tego formantu, nie trzeba modyfikować samej strony początkowej.

Magazyn ustawień, który jest skonkretyzowany w tym instruktażu, jest wystąpieniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interfejsu, który odczytuje i zapisuje w następującej lokalizacji rejestru, gdy jest wywoływana: **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName> **

Gdy jest uruchomiona w eksperymentalnym wystąpieniu programu Visual Studio, ustawienia są przechowywane i zapisywane w **HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName> .**

Więcej informacji o sposobie utrwalania ustawień znajduje się w temacie [rozszerzanie ustawień i opcji użytkownika](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Wymagania wstępne

> [!NOTE]
> Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Szablon projektu strony początkowej można pobrać za pomocą **Menedżera rozszerzeń**.

## <a name="set-up-the-project"></a>Konfigurowanie projektu

1. Utwórz projekt strony startowej zgodnie z opisem w temacie [Tworzenie niestandardowej strony początkowej](creating-a-custom-start-page.md). Nazwij projekt **SaveMySettings**.

2. W **Eksplorator rozwiązań**Dodaj następujące odwołania do zestawu do projektu StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. Shell. Interop. 11.0

3. Otwórz *formant. XAML*.

4. W okienku XAML w definicji elementu najwyższego poziomu <xref:System.Windows.Controls.UserControl> Dodaj następującą deklarację zdarzenia po deklaracjach przestrzeni nazw.

    ```xml
    Loaded="OnLoaded"
    ```

5. W okienku projekt kliknij obszar główny kontrolki, a następnie naciśnij klawisz **delete**.

     Ten krok polega na usunięciu <xref:System.Windows.Controls.Border> elementu i wszystkich jego elementów i pozostawieniu tylko elementu najwyższego poziomu <xref:System.Windows.Controls.Grid> .

6. Z **przybornika**przeciągnij <xref:System.Windows.Controls.StackPanel> kontrolkę do siatki.

7. Teraz przeciągnij <xref:System.Windows.Controls.TextBlock> , a <xref:System.Windows.Controls.TextBox> i przycisk do <xref:System.Windows.Controls.StackPanel> .

8. Dodaj atrybut **x:Name** dla <xref:System.Windows.Controls.TextBox> i `Click` zdarzenia dla <xref:System.Windows.Controls.Button> , jak pokazano w poniższym przykładzie.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementowanie kontrolki użytkownika

1. W okienku XAML kliknij prawym przyciskiem myszy `Click` atrybut <xref:System.Windows.Controls.Button> elementu, a następnie kliknij polecenie **Przejdź do programu obsługi zdarzeń**.

     W tym kroku zostanie otwarty *MyControl.XAML.cs*i zostanie utworzona procedura obsługi dla `Button_Click` zdarzenia.

2. Dodaj następujące `using` dyrektywy na początku pliku.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Dodaj prywatną `SettingsStore` Właściwość, jak pokazano w poniższym przykładzie.

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

     Ta właściwość najpierw pobiera odwołanie do <xref:EnvDTE80.DTE2> interfejsu, który zawiera model obiektów automatyzacji, z <xref:System.Windows.FrameworkElement.DataContext%2A> kontrolki użytkownika, a następnie używa DTE do uzyskania wystąpienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interfejsu. Następnie używa tego wystąpienia do zwrócenia bieżących ustawień użytkownika.

4. Wypełnij zdarzenie w `Button_Click` następujący sposób.

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

     Spowoduje to zapisanie zawartości pola tekstowego w polu "Moje ustawienie" w kolekcji "Moje ustawienia" w rejestrze. Jeśli kolekcja nie istnieje, zostanie utworzona.

5. Dodaj następujący program obsługi dla `OnLoaded` zdarzenia kontrolki użytkownika.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Ten kod ustawia tekst pola tekstowego na bieżącą wartość "Ustawienia".

6. Utwórz kontrolkę użytkownika.

7. W **Eksplorator rozwiązań**, Open *source. Extension. vsixmanifest*.

8. W edytorze manifestu Ustaw **nazwę produktu** , aby **zapisać stronę początkową moje ustawienia**.

     Ta funkcja ustawia nazwę strony początkowej, która ma być wyświetlana na liście **Dostosuj stronę początkową** w oknie dialogowym **Opcje** .

9. Kompiluj *kod Startpage. XAML*.

## <a name="test-the-control"></a>Testowanie kontrolki

1. Naciśnij klawisz **F5**.

     Zostanie otwarte doświadczalne wystąpienie programu Visual Studio.

2. W eksperymentalnym wystąpieniu, w menu **Narzędzia** , kliknij przycisk **Opcje**.

3. W węźle **środowisko** kliknij pozycję **Uruchamianie**, a następnie na liście **Dostosuj stronę początkową** wybierz pozycję **[zainstalowane rozszerzenie] Zapisz stronę początkową moje ustawienia**.

     Kliknij przycisk **OK**.

4. Zamknij stronę początkową, jeśli jest otwarta, a następnie w menu **Widok** kliknij pozycję **Strona początkowa**.

5. Na stronie startowej kliknij kartę **formant** .

6. W polu tekstowym wpisz **kot**, a następnie kliknij pozycję **Zapisz moje ustawienie**.

7. Zamknij stronę początkową, a następnie otwórz ją ponownie.

     W polu tekstowym powinna zostać wyświetlona słowo "Cat".

8. Zastąp słowo "Cat" słowem "Dog". Nie klikaj przycisku.

9. Zamknij stronę początkową, a następnie otwórz ją ponownie.

     Słowo "Dog" powinno być wyświetlane w polu tekstowym, nawet jeśli nie zapisano tego ustawienia, ponieważ program Visual Studio utrzymuje okna narzędzi w pamięci, nawet jeśli są zamknięte, do momentu zamknięcia programu Visual Studio.

10. Zamknij wystąpienie eksperymentalne programu Visual Studio.

11. Naciśnij klawisz **F5** , aby ponownie otworzyć wystąpienie eksperymentalne.

12. W polu tekstowym powinna zostać wyświetlona słowo "Cat".

## <a name="next-steps"></a>Następne kroki

Można zmodyfikować tę kontrolkę użytkownika w celu zapisania i pobrania dowolnej liczby ustawień niestandardowych przy użyciu różnych wartości z różnych programów obsługi zdarzeń w celu uzyskania i ustawienia `SettingsStore` właściwości. Tak długo, jak używasz innego `propertyName` parametru dla każdego wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , wartości nie zastępują siebie nawzajem w rejestrze.

## <a name="see-also"></a>Zobacz też

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Dodawanie poleceń programu Visual Studio do strony początkowej](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
