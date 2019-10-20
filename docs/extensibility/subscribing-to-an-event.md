---
title: Subskrybowanie zdarzenia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647927"
---
# <a name="subscribing-to-an-event"></a>Subskrybowanie zdarzenia
W tym instruktażu wyjaśniono, jak utworzyć okno narzędzi, które reaguje na zdarzenia w uruchomionej tabeli dokumentu (RDT). Okno narzędzi hostuje kontrolkę użytkownika, która implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> łączy interfejs ze zdarzeniami.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Subskrybowanie zdarzeń RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Aby utworzyć rozszerzenie przy użyciu okna narzędziowego

1. Utwórz projekt o nazwie **RDTExplorer** przy użyciu szablonu VSIX i Dodaj szablon elementu niestandardowego okna narzędzi o nazwie **RDTExplorerWindow**.

     Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Aby subskrybować zdarzenia RDT

1. Otwórz plik RDTExplorerWindowControl. XAML i Usuń przycisk o nazwie `button1`. Dodaj kontrolkę <xref:System.Windows.Forms.ListBox> i zaakceptuj nazwę domyślną. Element Grid powinien wyglądać następująco:

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

3. Zmodyfikuj klasę `RDTExplorerWindow` tak, aby oprócz wyprowadzania z klasy <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementuje interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Zaimplementuj interfejs. Umieść kursor na nazwie IVsRunningDocTableEvents. Na lewym marginesie powinna zostać wyświetlona żarówka. Kliknij strzałkę w dół znajdującą się po prawej stronie żarówki i wybierz pozycję **Implementuj interfejs**.

5. W każdej metodzie w interfejsie Zastąp wiersz `throw new NotImplementedException();`:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Dodaj pole cookie do klasy RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Zawiera plik cookie, który jest zwracany przez metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>.

7. Zastąp metodę Initialize () RDTExplorerWindow, aby zarejestrować zdarzenia RDT. Należy zawsze pobierać usługi w metodzie Initialize () elementu toolwindowpane (), a nie w konstruktorze.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Usługa <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> jest wywoływana w celu uzyskania interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> łączy zdarzenia RDT z obiektem, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, w tym przypadku obiekt RDTExplorer.

8. Zaktualizuj metodę Dispose () RDTExplorerWindow.

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

     Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> usuwa połączenie między `RDTExplorer` i powiadomienia o zdarzeniu RDT.

9. Dodaj następujący wiersz do treści procedury obsługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>, tuż przed instrukcją `return`.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Dodaj podobny wiersz do treści procedury obsługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> i innych zdarzeń, które mają być widoczne w polu listy.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne programu Visual Studio.

12. Otwórz **RDTExplorerWindow** (**Wyświetl/inne okna/RDTExplorerWindow**).

     Zostanie otwarte okno **RDTExplorerWindow** z pustą listą zdarzeń.

13. Otwórz lub Utwórz rozwiązanie.

     Po uruchomieniu zdarzeń `OnBeforeLastDocument` i `OnAfterFirstDocument` zostanie wyświetlone powiadomienie o każdym zdarzeniu na liście zdarzeń.
