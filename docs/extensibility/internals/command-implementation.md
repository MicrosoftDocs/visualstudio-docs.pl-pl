---
title: Implementacja polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709579"
---
# <a name="command-implementation"></a>Implementacja polecenia
Aby zaimplementować polecenie w programie VSPackage, należy wykonać następujące zadania:

1. W pliku *vsct* skonfiguruj grupę poleceń, a następnie dodaj do niej polecenie. Aby uzyskać więcej informacji, zobacz [Pliki tabeli poleceń programu Visual Studio (vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Zarejestruj polecenie w programie Visual Studio.

3. Zaimplementuj polecenie.

W poniższych sekcjach wyjaśniono, jak zarejestrować i zaimplementować polecenia.

## <a name="register-commands-with-visual-studio"></a>Rejestrowanie poleceń w programie Visual Studio
 Jeśli polecenie ma pojawić się w menu, <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> należy dodać do VSPackage i użyć jako wartość albo nazwę menu lub jego identyfikator zasobu.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Ponadto należy zarejestrować polecenie za <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>pomocą pliku . Tę usługę można uzyskać <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> przy użyciu metody, jeśli vspackage pochodzi od <xref:Microsoft.VisualStudio.Shell.Package>.

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

## <a name="implement-commands"></a>Implementowanie poleceń
 Istnieje wiele sposobów implementacji poleceń. Jeśli chcesz statyczne polecenie menu, które jest poleceniem, które zawsze pojawia się w <xref:System.ComponentModel.Design.MenuCommand> ten sam sposób i w tym samym menu, utwórz polecenie za pomocą jak pokazano w przykładach w poprzedniej sekcji. Aby utworzyć polecenie statyczne, należy podać program obsługi zdarzeń, który jest odpowiedzialny za wykonanie polecenia. Ponieważ polecenie jest zawsze włączone i widoczne, nie trzeba podać jego stan visual studio. Jeśli chcesz zmienić stan polecenia w zależności od określonych warunków, można utworzyć <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> polecenie jako wystąpienie klasy i, w jego konstruktorze, podać program obsługi zdarzeń do wykonania polecenia i `QueryStatus` program obsługi, aby powiadomić Visual Studio, gdy stan polecenia ulegnie zmianie. Można również <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zaimplementować jako część klasy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> polecenia lub można zaimplementować, jeśli dostarczasz polecenia jako część projektu. Dwa interfejsy i <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> klasa mają wszystkie metody, które powiadamiają Visual Studio o zmianie stanu polecenia i inne metody, które zapewniają wykonanie polecenia.

 Po dodaniu polecenia do usługi poleceń staje się ono jednym z łańcuchów poleceń. Po zaimplementowanie stanu powiadomień i metod wykonywania polecenia, należy dbać, aby zapewnić tylko dla tego konkretnego polecenia i przekazać wszystkie inne przypadki do innych poleceń w łańcuchu. Jeśli polecenie nie zostanie przekazane (zwykle <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>przez powrót), program Visual Studio może przestać działać poprawnie.

## <a name="querystatus-methods"></a>Metody QueryStatus
 Jeśli implementujesz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metodę, sprawdź identyfikator GUID zestawu poleceń, do którego należy polecenie, oraz identyfikator polecenia. Postępuj zgodnie z tymi wskazówkami:

- Jeśli identyfikator GUID nie jest rozpoznawany, implementacja jednej z tych metod musi zostać odesłana. <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>

- Jeśli implementacja jednej z tych metod rozpoznaje identyfikator GUID, ale nie <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>zaimplementowała polecenia, metoda powinna zwrócić .

- Jeśli implementacja jednej z tych metod rozpoznaje zarówno identyfikator GUID, jak i polecenie, metoda `prgCmds` powinna ustawić pole <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> flagi poleceń każdego polecenia (w parametrze) przy użyciu następujących flag:

  - `OLECMDF_SUPPORTED`: Polecenie jest obsługiwane.

  - `OLECMDF_INVISIBLE`: Polecenie nie powinno być widoczne.

  - `OLECMDF_LATCHED`: Polecenie jest włączone i wydaje się, że zostało sprawdzone.

  - `OLECMDF_ENABLED`: Polecenie jest włączone.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Polecenie powinno być ukryte, jeśli pojawia się w menu skrótów.

  - `OLECMDF_NINCHED`: Polecenie jest kontrolerem menu i nie jest włączone, ale jego lista menu rozwijanego nie jest pusta i nadal jest dostępna. (Ta flaga jest rzadko używana.)

- Jeśli polecenie zostało zdefiniowane w pliku `TextChanges` *vsct* z flagą, ustaw następujące parametry:

  - Ustaw `rgwz` element parametru na `pCmdText` nowy tekst polecenia.

  - Ustaw `cwActual` element parametru na `pCmdText` rozmiar ciągu polecenia.

Ponadto upewnij się, że bieżący kontekst nie jest funkcją automatyzacji, chyba że polecenie jest specjalnie przeznaczone do obsługi funkcji automatyzacji.

Aby wskazać, że obsługujesz <xref:Microsoft.VisualStudio.VSConstants.S_OK>określone polecenie, wróć . W przypadku wszystkich innych <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>poleceń zwróć .

W poniższym przykładzie `QueryStatus` metoda najpierw upewnia się, że kontekst nie jest funkcją automatyzacji, a następnie znajduje poprawny identyfikator GUID zestawu poleceń i identyfikator polecenia. Samo polecenie jest ustawione na włączenie i obsługę. Żadne inne polecenia nie są obsługiwane.

```csharp
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
 Implementacja `Exec` metody przypomina implementację `QueryStatus` metody. Najpierw upewnij się, że kontekst nie jest funkcją automatyzacji. Następnie przetestuj identyfikator GUID i identyfikator polecenia. Jeśli identyfikator guid lub polecenia nie <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>jest rozpoznawany, zwróć .

 Aby obsłużyć polecenie, należy wykonać go i powrócić, <xref:Microsoft.VisualStudio.VSConstants.S_OK> jeśli wykonanie zakończy się pomyślnie. Twoje polecenie jest odpowiedzialne za wykrywanie błędów i powiadamianie; w związku z tym zwraca kod błędu, jeśli wykonanie nie powiedzie się. Poniższy przykład pokazuje, jak należy zaimplementować metodę wykonywania.

```csharp
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

## <a name="see-also"></a>Zobacz też

- [Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
