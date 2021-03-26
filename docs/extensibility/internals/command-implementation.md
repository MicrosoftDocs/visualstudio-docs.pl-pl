---
title: Implementacja polecenia | Microsoft Docs
description: Dowiedz się więcej na temat implementacji poleceń w programie Visual Studio, jak skonfigurować grupę poleceń w pakietu VSPackage, dodać do niej polecenie, zarejestrować polecenie i wdrożyć je.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 93c99b131340d2e53b931619d4e5742d9e19f570
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091142"
---
# <a name="command-implementation"></a>Implementacja polecenia
Aby zaimplementować polecenie w pakietu VSPackage, należy wykonać następujące zadania:

1. W pliku *. vsct* Skonfiguruj grupę poleceń, a następnie Dodaj do niej polecenie. Aby uzyskać więcej informacji, zobacz [pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Zarejestruj polecenie w programie Visual Studio.

3. Zaimplementuj polecenie.

W poniższych sekcjach opisano sposób rejestrowania i implementowania poleceń.

## <a name="register-commands-with-visual-studio"></a>Rejestrowanie poleceń w programie Visual Studio
 Jeśli polecenie ma być wyświetlane w menu, należy dodać <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> do pakietu VSPackage i użyć jako wartość jako nazwę menu lub jego identyfikator zasobu.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Ponadto należy zarejestrować polecenie przy użyciu <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . Tę usługę można uzyskać, korzystając <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> z metody, jeśli pakietu VSPackage pochodzi od <xref:Microsoft.VisualStudio.Shell.Package> .

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

## <a name="implement-commands"></a>Implementuj polecenia
 Istnieje kilka sposobów implementacji poleceń. Jeśli chcesz użyć statycznego polecenia menu, które jest zawsze wyświetlane w taki sam sposób i w tym samym menu, Utwórz polecenie za pomocą, <xref:System.ComponentModel.Design.MenuCommand> jak pokazano w przykładach w poprzedniej sekcji. Aby utworzyć polecenie statyczne, należy podać procedurę obsługi zdarzeń, która jest odpowiedzialna za wykonywanie polecenia. Ponieważ polecenie jest zawsze włączone i widoczne, nie trzeba podawać jego statusu do programu Visual Studio. Jeśli chcesz zmienić stan polecenia w zależności od określonych warunków, można utworzyć polecenie jako wystąpienie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> klasy i, w konstruktorze, dostarczyć procedurę obsługi zdarzeń w celu wykonania polecenia i programu `QueryStatus` obsługi, aby powiadomić program Visual Studio o zmianie stanu polecenia. Można również zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> jako część klasy polecenia lub, można zaimplementować, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Jeśli podajesz polecenie jako część projektu. Dwa interfejsy i <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Klasa mają metody, które powiadamiają program Visual Studio o zmianie stanu polecenia i innych metodach, które zapewniają wykonanie polecenia.

 Po dodaniu polecenia do usługi poleceń zostanie on jeden z łańcuchu poleceń. W przypadku zaimplementowania metody powiadamiania o stanie i wykonywania dla polecenia należy zachować ostrożność w przypadku tego konkretnego polecenia i przekazać wszystkie inne przypadki do innych poleceń w łańcuchu. Jeśli nie powiodło się przekazanie polecenia (zazwyczaj przez zwrócenie <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> ), program Visual Studio może przestać działać poprawnie.

## <a name="querystatus-methods"></a>Metody QueryStatus
 Jeśli wdrażasz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metodę, Sprawdź identyfikator GUID zestawu poleceń, do którego należy to polecenie, i identyfikator polecenia. Postępuj zgodnie z następującymi wskazówkami:

- Jeśli identyfikator GUID nie zostanie rozpoznany, implementacja obu metod musi zwracać <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> .

- Jeśli implementacja obu metod rozpoznaje identyfikator GUID, ale nie zaimplementowano polecenia, metoda powinna zwrócić <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

- Jeśli implementacja obu metod rozpoznaje identyfikator GUID i polecenie, wówczas metoda powinna ustawić pole flags każdego polecenia (w `prgCmds` parametrze) przy użyciu następujących <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> flag:

  - `OLECMDF_SUPPORTED`: Polecenie jest obsługiwane.

  - `OLECMDF_INVISIBLE`: Polecenie nie powinno być widoczne.

  - `OLECMDF_LATCHED`: Polecenie jest włączane i pojawia się jako zaznaczone.

  - `OLECMDF_ENABLED`: Polecenie jest włączone.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Polecenie powinno być ukryte, jeśli pojawia się w menu skrótów.

  - `OLECMDF_NINCHED`: Polecenie jest kontrolerem menu i nie jest włączone, ale jego lista rozwijana nie jest pusta i jest nadal dostępna. (Ta flaga jest rzadko używana).

- Jeśli polecenie zostało zdefiniowane w pliku *vsct* z `TextChanges` flagą, ustaw następujące parametry:

  - Ustaw `rgwz` element `pCmdText` parametru na nowy tekst polecenia.

  - Ustaw `cwActual` element `pCmdText` parametru na rozmiar ciągu polecenia.

Upewnij się również, że bieżący kontekst nie jest funkcją automatyzacji, chyba że polecenie jest przeznaczone wyłącznie do obsługi funkcji automatyzacji.

Aby wskazać, że obsługujesz określone polecenie, zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Dla wszystkich innych poleceń Zwróć <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

W poniższym przykładzie `QueryStatus` Metoda najpierw upewnia się, że kontekst nie jest funkcją automatyzacji, a następnie znajduje prawidłowy identyfikator GUID i ID polecenia zestawu poleceń. Samo polecenie jest ustawione na włączone i obsługiwane. Nie są obsługiwane żadne inne polecenia.

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
 Implementacja `Exec` metody przypomina implementację `QueryStatus` metody. Najpierw upewnij się, że kontekst nie jest funkcją automatyzacji. Następnie przetestuj dla identyfikatora GUID i identyfikatora polecenia. Jeśli nie rozpoznano identyfikatora GUID lub identyfikatora polecenia, Return <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

 Aby obsłużyć polecenie, należy wykonać to działanie i zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> w przypadku pomyślnego wykonania. Polecenie jest odpowiedzialne za wykrywanie błędów i powiadamianie; w związku z tym Zwróć kod błędu, jeśli wykonanie nie powiedzie się. W poniższym przykładzie pokazano, jak metoda wykonywania powinna być zaimplementowana.

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

- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
