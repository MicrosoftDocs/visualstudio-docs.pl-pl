---
title: Polecenie wdrożenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fad7d73522bed76960f8545514ffe6334f0434ae
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949622"
---
# <a name="command-implementation"></a>Implementacja poleceń
Aby zaimplementować polecenia w VSPackage, należy wykonać następujące zadania:  
  
1.  W *vsct* plików, skonfiguruj grupy poleceń, a następnie dodaj polecenie do niego. Aby uzyskać więcej informacji, zobacz [pliki tabeli (vsct) polecenia programu Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).
  
2.  Polecenie należy zarejestrować w usłudze Visual Studio.  
  
3.  Implementowanie polecenia.  
    
W poniższych sekcjach opisano, jak się zarejestrować i wdrożyć poleceń.  
  
## <a name="register-commands-with-visual-studio"></a>Zarejestruj się polecenia za pomocą programu Visual Studio  
 Jeśli polecenie jest wyświetlane w menu, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> pakietu VSPackage i używany jako wartość nazwy menu lub jego identyfikator zasobu.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Ponadto, musisz się zarejestrować, polecenie <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Tę usługę można uzyskać za pomocą <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodę, jeśli Twoja pakietu VSPackage jest tworzony na podstawie <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implement-commands"></a>Implementacja poleceń  
 Istnieje kilka sposobów implementowania poleceń. Polecenia menu statycznych, który jest zawsze wyświetlany taki sam sposób, jak i w tym samym menu polecenia, utworzyć polecenie przy użyciu <xref:System.ComponentModel.Design.MenuCommand> jak pokazano w przykładach w poprzedniej sekcji. Aby utworzyć statyczne polecenia, musisz podać program obsługi zdarzeń, który jest odpowiedzialny za wykonywanie polecenia. Ponieważ polecenie jest zawsze włączone i są widoczne, trzeba podać jego stan w programie Visual Studio. Jeśli chcesz zmienić stan polecenia, w zależności od określonych warunków, można utworzyć polecenie jako wystąpienie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> klasy, a w jego konstruktorze zapewniają program obsługi zdarzeń w celu wykonania tego polecenia i `QueryStatus` program obsługi, aby powiadomić Visual Studio po zmianie stanu polecenia. Możesz również wdrożyć <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> jako część klasy polecenia lub, można zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Jeśli udostępniasz polecenia jako część projektu. Dwa interfejsy i <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> wszystkie klasy mają metody, które powiadamiają o Visual Studio o zmianie stanu polecenia i innych metod, które zapewniają wykonanie polecenia.  
  
 Polecenie zostanie dodany do usługi polecenia, staje się jedną z łańcucha poleceń. Podczas implementowania stanu powiadomień i wykonywanie metod dla polecenia powinien zachować ostrożność, zapewnienie tylko tym konkretnym poleceniem i do przekazywania wszystkich innych przypadkach się do innych poleceń w łańcuchu. Jeśli nie zostanie ona przekazać polecenie (zwykle, zwracając <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), program Visual Studio mogą przestać działać prawidłowo.  
  
## <a name="querystatus-methods"></a>Metody QueryStatus  
 Przed zaimplementowaniem albo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metody, wyszukaj identyfikator GUID polecenia zestawu, do którego należy polecenia i identyfikator polecenia. Należy przestrzegać następujących wytycznych:  
  
-   Jeśli nie zostanie rozpoznany identyfikator GUID, implementacja jednej z metod musi zwracać <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Jeśli implementacja jednej z metod rozpoznaje identyfikatora GUID, ale nie została zaimplementowana polecenia, a następnie metoda powinna zwrócić <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Jeśli implementacja jednej z metod rozpoznaje zarówno identyfikatora GUID, a polecenie, a następnie metoda powinna być ustawiona na pole flag poleceń każdego polecenia (w `prgCmds` parametr) przy użyciu następujących <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> flag:  
  
    -   `OLECMDF_SUPPORTED`: Polecenie jest obsługiwane.  
  
    -   `OLECMDF_INVISIBLE`: Polecenie nie powinny być widoczne.  
  
    -   `OLECMDF_LATCHED`: Polecenie jest przełączona w i prawdopodobnie zostały zaewidencjonowane.  
  
    -   `OLECMDF_ENABLED`: Polecenie jest włączone.  
  
    -   `OLECMDF_DEFHIDEONCTXTMENU`: Polecenie powinna być ukryta, jeśli jest wyświetlana w menu skrótów.  
  
    -   `OLECMDF_NINCHED`: Polecenie kontroler menu i nie jest włączona, ale jego menu rozwijane listy nie jest pusta i jest nadal dostępna. (Ta flaga jest rzadko używany).  
  
-   Jeśli polecenie została zdefiniowana w *vsct* plik z `TextChanges` Flaga, ustaw następujące parametry:  
  
    -   Ustaw `rgwz` elementu `pCmdText` parametr nowego tekstu polecenia.  
  
    -   Ustaw `cwActual` elementu `pCmdText` parametru, aby rozmiar ciągu polecenia.  
  

Upewnij się również, że bieżący kontekst nie jest funkcją usługi automation, chyba że polecenie jest przeznaczony specjalnie do obsługi funkcji automatyzacji.  
  
Aby wskazać, że będziesz obsługiwał określonego polecenia, należy zwracać <xref:Microsoft.VisualStudio.VSConstants.S_OK>. W przypadku innych poleceń, zwracają <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
W poniższym przykładzie `QueryStatus` metoda najpierw sprawdza, czy kontekst nie jest funkcją usługi automation, a następnie znajduje poprawne GUID zestawu poleceń i identyfikator polecenia. Samo polecenie ustawiono włączony i obsługiwane. Inne polecenia są obsługiwane.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Metody wykonywania  
 Implementacja `Exec` metoda przypomina implementacji `QueryStatus` metody. Najpierw upewnij się, że kontekst nie jest funkcją usługi automation. Następnie sprawdź zarówno identyfikator GUID i identyfikator polecenia. Jeśli identyfikator GUID lub nie został rozpoznany identyfikator polecenia, zwróć <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 Do obsługi polecenia, należy ją wykonać i zwracają <xref:Microsoft.VisualStudio.VSConstants.S_OK> Jeśli wykonanie zakończy się powodzeniem. Polecenie jest odpowiedzialny za wykrywanie błędów oraz powiadomienia; Dlatego należy zwrócić kod błędu, jeśli wykonanie nie powiedzie się. W poniższym przykładzie pokazano, jak można zaimplementować metodę wykonywania.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)