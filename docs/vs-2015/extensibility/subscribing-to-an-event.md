---
title: Subskrybowanie zdarzenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 324e74c78f01da47c544b5f640ad0bd9052a1bb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160548"
---
# <a name="subscribing-to-an-event"></a>Subskrybowanie zdarzenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu wyjaśniono, jak utworzyć okno narzędzi, które reaguje na zdarzenia w uruchomionej tabeli dokumentu (RDT). Okno narzędzi hostuje kontrolkę użytkownika, która implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Metoda łączy interfejs ze zdarzeniami.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Subskrybowanie zdarzeń RDT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Aby utworzyć rozszerzenie przy użyciu okna narzędziowego  
  
1. Utwórz projekt o nazwie **RDTExplorer** przy użyciu szablonu VSIX i Dodaj szablon elementu niestandardowego okna narzędzi o nazwie **RDTExplorerWindow**.  
  
     Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Aby subskrybować zdarzenia RDT  
  
1. Otwórz plik RDTExplorerWindowControl. XAML i Usuń przycisk o nazwie `button1` . Dodaj <xref:System.Windows.Forms.ListBox> kontrolkę i zaakceptuj nazwę domyślną. Element Grid powinien wyglądać następująco:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2. Otwórz plik RDTExplorerWindow.cs w widoku kodu. Dodaj następujące instrukcje using na początku pliku.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3. Zmodyfikuj `RDTExplorerWindow` klasę, tak aby oprócz wyprowadzania z <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> klasy implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfejs.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4. Implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> .  
  
    - Zaimplementuj interfejs. Umieść kursor na nazwie IVsRunningDocTableEvents. Na lewym marginesie powinna zostać wyświetlona żarówka. Kliknij strzałkę w dół znajdującą się po prawej stronie żarówki i wybierz pozycję **Implementuj interfejs**.  
  
5. W każdej metodzie w interfejsie Zastąp wiersz `throw new NotImplementedException();` tym:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6. Dodaj pole cookie do klasy RDTExplorerWindow.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Zawiera plik cookie, który jest zwracany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodę.  
  
7. Zastąp metodę Initialize () RDTExplorerWindow, aby zarejestrować zdarzenia RDT. Należy zawsze pobierać usługi w metodzie Initialize () elementu toolwindowpane (), a nie w konstruktorze.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>Usługa jest wywoływana w celu uzyskania <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfejsu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Metoda łączy zdarzenia RDT z obiektem, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> , w tym przypadku obiekt RDTExplorer.  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>Metoda usuwa połączenie między programem `RDTExplorer` a powiadomieniem o zdarzeniu RDT.  
  
9. Dodaj następujący wiersz do treści <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> procedury obsługi, tuż przed `return` instrukcją.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Dodaj podobny wiersz do treści <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> programu obsługi i innych zdarzeń, które chcesz zobaczyć w polu listy.  
  
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
  
     Po `OnBeforeLastDocument` uruchomieniu `OnAfterFirstDocument` zdarzenia i powiadomienia dla każdego zdarzenia pojawiają się na liście zdarzeń.
