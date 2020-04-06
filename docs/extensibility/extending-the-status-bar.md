---
title: Rozszerzanie paska stanu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711541"
---
# <a name="extend-the-status-bar"></a>Rozszerzanie paska stanu
Można użyć paska stanu programu Visual Studio u dołu IDE do wyświetlania informacji.

 Po rozszerzeniu paska stanu można wyświetlać informacje i interfejs użytkownika w czterech regionach: regionie opinii, pasku postępu, regionie animacji i regionie projektanta. Obszar sprzężenia zwrotnego umożliwia wyświetlanie tekstu i wyróżnianie wyświetlanego tekstu. Pasek postępu pokazuje przyrostowy postęp dla operacji krótkokładowych, takich jak zapisywanie pliku. Region animacji wyświetla animację w pętli w pętli dla długotrwałych operacji lub operacji o nieokreślonej długości, takich jak tworzenie wielu projektów w rozwiązaniu. Region projektanta pokazuje numer linii i kolumny lokalizacji kursora.

 Pasek stanu można uzyskać za <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> pomocą interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> (z usługi). Ponadto każdy obiekt umiejscowiony w ramce okna może zarejestrować się <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> jako obiekt klienta paska stanu, implementując interfejs. Za każdym razem, gdy okno jest aktywowane, Visual Studio `IVsStatusbarUser` wysyła zapytanie do obiektu umiejscowionego w tym oknie dla interfejsu. Jeśli zostanie znaleziony, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> wywołuje metodę na zwróconym interfejsie i obiekt może zaktualizować pasek stanu z poziomu tej metody. Okna dokumentu, na przykład, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> można użyć metody, aby zaktualizować informacje w regionie projektanta, gdy stają się aktywne.

 W poniższych procedurach przyjęto założenie, że rozumiesz, jak utworzyć projekt VSIX i dodać polecenie menu niestandardowego. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modyfikowanie paska stanu
 W tej procedurze pokazano, jak ustawić i uzyskać tekst, wyświetlić tekst statyczny i wyróżnić wyświetlany tekst w regionie opinii paska stanu.

### <a name="read-and-write-to-the-status-bar"></a>Odczyt i zapis na pasku stanu

1. Utwórz projekt VSIX o nazwie **TestStatusBarExtension** i dodaj polecenie menu o nazwie **TestStatusBarCommand**.

2. W *TestStatusBarCommand.cs*, zastąp kod`MenuItemCallback`metody obsługi poleceń ( ) następującymi:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Skompiluj kod i rozpocznij debugowanie.

4. Otwórz menu **Narzędzia** w eksperymentalnym wystąpieniu programu Visual Studio. Kliknij przycisk **Invoke TestStatusBarCommand.**

     Powinieneś zobaczyć, że tekst na pasku stanu teraz brzmi **Właśnie napisałem do paska stanu.** a wyświetlenie okna komunikatu ma ten sam tekst.

### <a name="update-the-progress-bar"></a>Aktualizowanie paska postępu

1. W tej procedurze pokażemy, jak zainicjować i zaktualizować pasek postępu.

2. Otwórz plik *TestStatusBarCommand.cs* i zastąp `MenuItemCallback` metodę następującym kodem:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Skompiluj kod i rozpocznij debugowanie.

4. Otwórz menu **Narzędzia** w eksperymentalnym wystąpieniu programu Visual Studio. Kliknij przycisk **Wywołaj teststatusbarkommand.**

     Powinieneś zobaczyć, że tekst na pasku stanu teraz odczytuje **Pisanie na pasku postępu.** Powinieneś również zobaczyć pasek postępu aktualizowany co sekundę przez 20 sekund. Następnie pasek stanu i pasek postępu zostaną wyczyszczone.

### <a name="display-an-animation"></a>Wyświetlanie animacji

1. Pasek stanu wyświetla animację pętli, która wskazuje, że operacja długotrwała (na przykład tworzenie wielu projektów w rozwiązaniu). Jeśli ta animacja nie jest widoczna, upewnij się, że masz poprawne ustawienia**opcji** **narzędzi:** > 

     Przejdź do**karty** **Ogólne Opcje** >  **narzędzi** > i wyelikonuj zaznacz **opcję Automatycznie dopasowuj środowisko wizualne na podstawie wydajności klienta**. Następnie sprawdź opcję podrzędną **Włącz bogate środowisko wizualne klienta**. Teraz powinien być w stanie zobaczyć animacji podczas tworzenia projektu w eksperymentalnym wystąpieniu programu Visual Studio.

     W tej procedurze wyświetlamy standardową animację programu Visual Studio, która reprezentuje tworzenie projektu lub rozwiązania.

2. Otwórz plik *TestStatusBarCommand.cs* i zastąp `MenuItemCallback` metodę następującym kodem:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Skompiluj kod i rozpocznij debugowanie.

4. Otwórz menu **Narzędzia** w eksperymentalnym wystąpieniu programu Visual Studio i kliknij przycisk **Wywołaj teststatusbarcommand**.

     Gdy zostanie wyświetlenie okna komunikatu, animacja powinna być również widoczna na pasku stanu po prawej stronie. Po odrzuceniu okna komunikatu animacja zniknie.
