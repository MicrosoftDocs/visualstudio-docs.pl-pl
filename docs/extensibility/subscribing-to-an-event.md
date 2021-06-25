---
title: Subskrybowanie usługi Event | Microsoft Docs
description: Dowiedz się, jak utworzyć okno narzędzi, które reaguje na zdarzenia w uruchomionej tabeli dokumentów w Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01271016eed9a4a157b333a2f0435589b0a028d5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899396"
---
# <a name="subscribing-to-an-event"></a>Subskrybowanie zdarzenia
W tym przewodniku wyjaśniono, jak utworzyć okno narzędzia, które reaguje na zdarzenia w uruchomionej tabeli dokumentów (RDT). Okno narzędzi hostuje kontrolkę użytkownika, która <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> implementuje . Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> łączy interfejs ze zdarzeniami.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od Visual Studio 2015 r., zestaw SDK usługi Visual Studio nie jest instalowany z Centrum pobierania. Jest ona dołączona jako opcjonalna funkcja w Visual Studio konfiguracji. Zestaw VS SDK można również zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="subscribing-to-rdt-events"></a>Subskrybowanie zdarzeń RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Aby utworzyć rozszerzenie za pomocą okna narzędzi

1. Utwórz projekt o nazwie **RDTExplorer** przy użyciu szablonu VSIX i dodaj szablon elementu niestandardowego okna narzędzi o nazwie **RDTExplorerWindow.**

     Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz Creating an Extension with a Tool Window (Tworzenie [rozszerzenia za pomocą okna narzędzi).](../extensibility/creating-an-extension-with-a-tool-window.md)

#### <a name="to-subscribe-to-rdt-events"></a>Aby zasubskrybować zdarzenia RDT

1. Otwórz plik RDTExplorerWindowControl.xaml i usuń przycisk o nazwie `button1` . Dodaj <xref:System.Windows.Forms.ListBox> kontrolkę i zaakceptuj nazwę domyślną. Element Grid powinien wyglądać tak:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Otwórz plik RDTExplorerWindow.cs w widoku kodu. Dodaj następujące dyrektywy using na początku pliku.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Zmodyfikuj klasę tak, aby oprócz wyprowadzania z klasy `RDTExplorerWindow` <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementował <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfejs .

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Zaim <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> implementuj .

    - Zaim implementuj interfejs . Umieść kursor na nazwie IVsRunningDocTableEvents. Na lewym marginesie powinna być widać żarówkę. Kliknij strzałkę w dół z prawej strony żarówki i wybierz pozycję **Implementuj interfejs**.

5. W każdej metodzie w interfejsie zastąp wiersz `throw new NotImplementedException();` tym:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Dodaj pole pliku cookie do klasy RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Plik cookie, który jest zwracany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodę .

7. Zastąp metodę Initialize() firmy RDTExplorerWindow, aby zarejestrować zdarzenia RDT. Zawsze należy uzyskać usługi w metodzie Initialize() klasy ToolWindowPane, a nie w konstruktorze.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Usługa <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> jest wywoływana w celu uzyskania <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfejsu. Metoda łączy zdarzenia RDT z obiektem, który implementuje , w tym <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> przypadku <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> obiekt RDTExplorer.

8. Zaktualizuj metodę Dispose() metody RDTExplorerWindow.

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

     Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> usuwa połączenie między usługą i `RDTExplorer` powiadomieniem o zdarzeniu RDT.

9. Dodaj następujący wiersz do treści procedury obsługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> tuż przed instrukcji `return` .

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Dodaj wiersz podobny do treści procedury obsługi i do innych zdarzeń, które chcesz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> zobaczyć w polu listy.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Skompilowanie projektu i rozpoczęcie debugowania. Zostanie Visual Studio wystąpienie eksperymentalne.

12. Otwórz okno **RDTExplorerWindow** (**Widok / Inne okna / RDTExplorerWindow).**

     Zostanie **otwarte okno RDTExplorerWindow** z pustą listą zdarzeń.

13. Otwórz lub utwórz rozwiązanie.

     Gdy `OnBeforeLastDocument` zdarzenia i są `OnAfterFirstDocument` wyzowane, powiadomienia o każdym zdarzeniu są wyświetlane na liście zdarzeń.
