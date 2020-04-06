---
title: Subskrybowanie wydarzenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699685"
---
# <a name="subscribing-to-an-event"></a>Subskrybowanie zdarzenia
W tym przewodniku wyjaśniono, jak utworzyć okno narzędzia, które reaguje na zdarzenia w uruchomionej tabeli dokumentów (RDT). Okno narzędzia obsługuje formant użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>implementujące . Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> łączy interfejs ze zdarzeniami.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Subskrybowanie zdarzeń RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Aby utworzyć rozszerzenie z oknem narzędzia

1. Utwórz projekt o nazwie **RDTExplorer** przy użyciu szablonu VSIX i dodaj szablon elementu niestandardowego okna narzędzia o nazwie **RDTExplorerWindow**.

     Aby uzyskać więcej informacji na temat tworzenia rozszerzenia z oknem narzędzia, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Aby subskrybować zdarzenia RDT

1. Otwórz plik RDTExplorerWindowControl.xaml i usuń `button1`przycisk o nazwie . Dodaj <xref:System.Windows.Forms.ListBox> formant i zaakceptuj nazwę domyślną. Grid element powinien wyglądać następująco:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Otwórz plik RDTExplorerWindow.cs w widoku kodu. Dodaj następujące za pomocą dyrektyw na początku pliku.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Zmodyfikuj `RDTExplorerWindow` klasę tak, aby <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> oprócz wyprowadzania <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> z klasy implementuje interfejs.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>plik .

    - Zaimplementuj interfejs. Umieść kursor na nazwie IVsRunningDocTableEvents. Powinieneś zobaczyć żarówkę na lewym marginesie. Kliknij strzałkę w dół po prawej stronie żarówki i wybierz pozycję **Zaimplementuj interfejs**.

5. W każdej metodzie w interfejsie zastąp linię `throw new NotImplementedException();` tą:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Dodaj pole pliku cookie do klasy RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Spowoduje to blokadę pliku <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> cookie zwracany przez metodę.

7. Zastąp metodę initialize() systemu RDTExplorerWindow, aby zarejestrować się dla zdarzeń RDT. Zawsze należy uzyskać usługi w ToolWindowPane's Initialize(), a nie w konstruktorze.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Usługa <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> jest wywoływana <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> w celu uzyskania interfejsu. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> łączy zdarzenia RDT z obiektem, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, w tym przypadku obiekt RDTExplorer.

8. Zaktualizuj metodę dispose() systemu RDTExplorerWindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> usuwa połączenie między `RDTExplorer` i powiadomienie o zdarzeniu RDT.

9. Dodaj następujący wiersz do treści <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> programu obsługi, `return` tuż przed instrukcją.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Dodaj podobny wiersz do treści <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> programu obsługi i do innych zdarzeń, które chcesz wyświetlić w polu listy.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie programu Visual Studio.

12. Otwórz **okno RDTExplorerWindow** (**Widok / Inne okna / RDTExplorerWindow**).

     Okno **RDTExplorerWindow** zostanie otwarte z pustą listą zdarzeń.

13. Otwórz lub utwórz rozwiązanie.

     Gdy `OnBeforeLastDocument` `OnAfterFirstDocument` zdarzenia są uruchamiane, powiadomienie o każdym zdarzeniu pojawia się na liście zdarzeń.
