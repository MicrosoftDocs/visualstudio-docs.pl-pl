---
title: Subskrybowanie zdarzenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5dbb3c9db722ff335fd8dddadfffed57457d23ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916929"
---
# <a name="subscribing-to-an-event"></a>Subskrybowanie zdarzenia
W tym przewodniku opisano sposób tworzenia okna narzędzi, które reaguje na zdarzenia w uruchomionej tabeli dokumentu (Normalizacją). Okno narzędzia obsługuje formant użytkownika, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Metoda nawiązanie połączenia z interfejsu zdarzenia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Subskrybowanie zdarzeń Normalizacją  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Aby utworzyć rozszerzenie za pomocą okna narzędzi  
  
1.  Utwórz projekt o nazwie **RDTExplorer** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okno o nazwie **RDTExplorerWindow**.  
  
     Aby uzyskać więcej informacji na temat tworzenia rozszerzenia za pomocą okna narzędzi, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Aby subskrybować zdarzenia Normalizacją  
  
1.  Otwórz plik RDTExplorerWindowControl.xaml i usuń przycisk o nazwie `button1`. Dodaj <xref:System.Windows.Forms.ListBox> kontroli i zaakceptuj nazwę domyślną. Element siatki powinien wyglądać następująco:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Otwórz plik RDTExplorerWindow.cs w widoku kodu. Dodaj następujące instrukcje using na początku pliku.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Modyfikowanie `RDTExplorerWindow` klasy, tak że oprócz pochodząca od <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementuje klasa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfejsu.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Implementowanie interfejsu. Umieść kursor na nazwie IVsRunningDocTableEvents. Powinien zostać wyświetlony żarówek na lewym marginesie. Kliknij strzałkę po prawej stronie żarówki, a następnie wybierz pozycję **implementuj interfejs**.  
  
5.  W każdej metody w interfejsie, Zastąp wiersz `throw new NotImplementedException();` w tym:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Dodaj pole pliku cookie do klasy RDTExplorerWindow.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Przechowuje ten plik cookie, który jest zwracany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metody.  
  
7.  Zastąpienie metody Initialize() RDTExplorerWindow dla Normalizacją zdarzeń. Należy zawsze uzyskać usług w przypadku metody Initialize() obiektu ToolWindowPane nie znajduje się w konstruktorze.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Usługi jest wywoływana w celu uzyskania <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfejsu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Metoda łączy Normalizacją zdarzenia do obiektu, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, w tym przypadku obiekt RDTExplorer.  
  
8.  Zaktualizuj metodę Dispose() RDTExplorerWindow.  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Metoda usuwa połączenie między `RDTExplorer` i powiadomień o zdarzeniach Normalizacją.  
  
9. Dodaj następujący wiersz do treści <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> obsługi, tuż przed `return` instrukcji.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Dodaj wiersz podobny do treści <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> obsługi i inne zdarzenia, które mają być wyświetlane w polu listy.  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne programu Visual Studio.  
  
12. Otwórz **RDTExplorerWindow** (**widok / inne Windows / RDTExplorerWindow**).  
  
     **RDTExplorerWindow** zostanie otwarte okno z listy zdarzeń puste.  
  
13. Otwórz lub Utwórz rozwiązanie.  
  
     Jako `OnBeforeLastDocument` i `OnAfterFirstDocument` zdarzenia są uruchamiane, każdego zdarzenia jest wyświetlane powiadomienie w przypadku listy.