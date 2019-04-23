---
title: Rozszerzanie paska stanu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 499e6c2b34fcc5261ab8fb3a87a24e2cc0959d8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113745"
---
# <a name="extend-the-status-bar"></a>Rozszerzanie paska stanu
Na pasku stanu programu Visual Studio w dolnej części IDE służy do wyświetlania informacji.

 Podczas rozszerzania paska stanu w czterech regionach można wyświetlać informacje i interfejsu użytkownika: region opinii, pasek postępu, region animacji i projektanta regionów. Region opinii pozwala na wyświetlanie tekstu i wyróżnić tekst wyświetlany. Pasek postępu pokazuje przyrostowy postęp krótko działających operacje, takie jak zapisywanie pliku. Region animacji Wyświetla animację stale zwracane do operacji długotrwałych lub operacji o nieustalonym długości, takie jak tworzenie wielu projektów w rozwiązaniu. I projektanta region pokazuje numer wiersza i kolumny lokalizacji kursora.

 Na pasku stanu można uzyskać za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfejsu (z <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> usługi). Ponadto każdy obiekt ulokowany na ramkę okna może być rejestrowany jako stanu paska obiektu klienta przez zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfejsu. Zawsze, gdy okno jest aktywna, program Visual Studio zapytania obiektu ulokowany w tym oknie dla `IVsStatusbarUser` interfejsu. Jeśli znaleziono, wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodę na zwrócony interfejs, a obiekt można zaktualizować pasek stanu z w ramach tej metody. Dokumentowanie systemu windows, na przykład, można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodę, aby zaktualizować dane w regionie projektanta, gdy tylko staną się aktywne.

 W poniższych procedurach założono, że rozumiesz, jak utworzyć projekt VSIX i dodać polecenie menu niestandardowych. Aby uzyskać informacje, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modyfikowanie paska stanu
 Ta procedura pokazuje, jak ustawić tekstu, wyświetlać statyczny tekst i wyróżnić wyświetlanego tekstu w regionie opinii na pasku stanu.

### <a name="read-and-write-to-the-status-bar"></a>Odczyt i zapis do paska stanu

1. Utwórz projekt VSIX, o nazwie **TestStatusBarExtension** i dodać polecenie menu o nazwie **TestStatusBarCommand**.

2. W *TestStatusBarCommand.cs*, Zastąp kod metody procedury obsługi poleceń (`MenuItemCallback`) z następujących czynności:

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

3. Skompilować kod i rozpocząć debugowanie.

4. Otwórz **narzędzia** menu w eksperymentalnym wystąpieniu programu Visual Studio. Kliknij przycisk **wywołania TestStatusBarCommand** przycisku.

     Powinien zostać wyświetlony, tekst w pasku odczyty teraz stanu **napisany przed chwilą na pasku stanu.** i zostanie wyświetlone okno komunikatu ma ten sam tekst.

### <a name="update-the-progress-bar"></a>Aktualizacja pasek postępu

1. W tej procedurze, firma Microsoft pokazują, jak zainicjować i zaktualizuj pasek postępu.

2. Otwórz *TestStatusBarCommand.cs* i Zastęp `MenuItemCallback` metoda następującym kodem:

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

3. Skompilować kod i rozpocząć debugowanie.

4. Otwórz **narzędzia** menu w eksperymentalnym wystąpieniu programu Visual Studio. Kliknij przycisk **wywołania TestStatusBarCommand** przycisku.

     Powinien zostać wyświetlony, tekst w pasku odczyty teraz stanu **zapisywania pasek postępu.** Powinien być też widoczny pasek postępu pobierania aktualizacji co sekundę 20 sekund. Po tym zostaną wyczyszczone, pasek stanu i pasek postępu.

### <a name="display-an-animation"></a>Wyświetlanie animacji

1. Na pasku stanu wyświetlane animacji pętli, która wskazuje długotrwała operacja (np. Tworzenie wielu projektów w rozwiązaniu). Jeśli nie widzisz tą animację, upewnij się, że masz właściwą **narzędzia** > **opcje** ustawienia:

     Przejdź do **narzędzia** > **opcje** > **ogólne** kartę i usuń zaznaczenie pola wyboru **automatycznie Dostosuj wygląd bazując na kliencie wydajność**. Następnie zaznacz opcję podrzędnych **Włącz bogate doświadczenia wizualne**. Teraz można wyświetlać animacji, gdy kompilujesz projekt eksperymentalne wystąpienia programu Visual Studio.

     W tej procedurze wyświetlana standardowa animacji programu Visual Studio, który reprezentuje budowania projektu lub rozwiązania.

2. Otwórz *TestStatusBarCommand.cs* i Zastęp `MenuItemCallback` metoda następującym kodem:

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

3. Skompilować kod i rozpocząć debugowanie.

4. Otwórz **narzędzia** w doświadczalnym wystąpieniu programu Visual Studio, a następnie kliknij przycisk menu **wywołania TestStatusBarCommand**.

     Gdy pojawi się okno komunikatu, również powinny animacji w pasku stanu na końcu z prawej strony. Podczas odrzucania okno komunikatu znika animacji.