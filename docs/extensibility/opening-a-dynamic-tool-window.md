---
title: Otwieranie okna narzędzia dynamicznego | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a06cea6d9de4271572457dc9fe6473b5c969b66
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903715"
---
# <a name="open-a-dynamic-tool-window"></a>Otwieranie okna narzędzia dynamicznego
Okna narzędzi są zwykle otwierane za pomocą polecenia w menu lub równoważnego skrótu klawiaturowego. Czasami jednak może być konieczne okno narzędzi, które jest otwierane za każdym razem, gdy określony kontekst interfejsu użytkownika zostanie zastosowany, i zamyka się, gdy kontekst interfejsu użytkownika już nie ma zastosowania. Te typy okien narzędzi są nazywane *dynamicznym* lub *autowidocznością*.

> [!NOTE]
> Aby uzyskać listę wstępnie zdefiniowanych kontekstów interfejsu użytkownika, zobacz <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> .

 Jeśli chcesz otworzyć dynamiczne okno narzędzi przy uruchamianiu i można utworzyć błąd, musisz zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interfejs i przetestować warunki awarii w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metodzie. Aby powłoka wiedzieli, że masz dynamiczne okno narzędzi, które ma być otwierane podczas uruchamiania, należy dodać `SupportsDynamicToolOwner` wartość (ustawienie 1) do rejestracji pakietu. Ta wartość nie jest częścią standardu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , dlatego należy utworzyć atrybut niestandardowy w celu dodania go. Aby uzyskać więcej informacji o atrybutach niestandardowych, zobacz [Używanie niestandardowego atrybutu rejestracji do rejestrowania rozszerzenia](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Służy <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> do otwierania okna narzędzi. Okno narzędzia jest tworzone w razie konieczności.

> [!NOTE]
> Okno narzędzia dynamicznego może zostać zamknięte przez użytkownika. Jeśli chcesz utworzyć polecenie menu, aby użytkownik mógł ponownie otworzyć okno narzędzia, polecenie menu powinno być włączone w tym samym kontekście interfejsu użytkownika, który otwiera okno narzędzia i wyłączone w przeciwnym razie.

## <a name="to-open-a-dynamic-tool-window"></a>Aby otworzyć okno narzędzia dynamicznego

1. Utwórz projekt VSIX o nazwie **DynamicToolWindow** i Dodaj szablon elementu okna narzędzia o nazwie *DynamicWindowPane.cs*. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia przy użyciu okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md).

2. W pliku *DynamicWindowPanePackage.cs* Znajdź deklarację DynamicWindowPanePackage. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atrybuty i, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> Aby zarejestrować okno narzędzi.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     Powyższe atrybuty rejestrują okno narzędzia o nazwie DynamicWindowPane jako okno przejściowe, które nie jest utrwalane po zamknięciu i ponownym otwarciu programu Visual Studio. DynamicWindowPane jest otwierana za każdym razem <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> , gdy ma zastosowanie, i zamknięty w przeciwnym razie.

3. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne. Nie powinno być widoczne okno narzędzia.

4. Otwórz projekt w eksperymentalnym wystąpieniu. Powinno zostać wyświetlone okno narzędzia.
