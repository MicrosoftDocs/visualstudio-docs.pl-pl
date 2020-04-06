---
title: Otwieranie dynamicznego okna narzędzia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702262"
---
# <a name="open-a-dynamic-tool-window"></a>Otwieranie dynamicznego okna narzędzia
Okna narzędzi są zazwyczaj otwierane z polecenia w menu lub równoważnego skrótu klawiaturowego. Czasami jednak może być potrzebne okno narzędzia, które otwiera się za każdym razem, gdy stosuje się określony kontekst interfejsu użytkownika i zamyka się, gdy kontekst interfejsu użytkownika nie ma już zastosowania. Te typy okien narzędzi są nazywane *dynamicznymi* lub *automatycznie widocznymi*.

> [!NOTE]
> Aby uzyskać listę wstępnie zdefiniowanych kontekstów <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>interfejsu użytkownika, zobacz .

 Jeśli chcesz otworzyć okno narzędzia dynamicznego podczas uruchamiania i jest możliwe, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> tworzenie nie powiodło <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> się, należy zaimplementować interfejs i przetestować warunki awarii w metodzie. Aby powłoka wiedziała, że masz dynamiczne okno narzędzia, które powinno zostać `SupportsDynamicToolOwner` otwarte podczas uruchamiania, należy dodać wartość (ustawioną na 1) do rejestracji pakietu. Ta wartość nie jest <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>częścią standardu, więc należy utworzyć atrybut niestandardowy, aby go dodać. Aby uzyskać więcej informacji na temat atrybutów niestandardowych, zobacz [Rejestrowanie rozszerzenia za pomocą atrybutu rejestracji niestandardowej.](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)

 Służy <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> do otwierania okna narzędzia. Okno narzędzia zostanie utworzone zgodnie z potrzebami.

> [!NOTE]
> Dynamiczne okno narzędzia może być zamknięte przez użytkownika. Jeśli chcesz utworzyć polecenie menu, aby użytkownik mógł ponownie otworzyć okno narzędzia, polecenie menu powinno być włączone w tym samym kontekście interfejsu użytkownika, który otwiera okno narzędzia, i wyłączone w przeciwnym razie.

## <a name="to-open-a-dynamic-tool-window"></a>Aby otworzyć dynamiczne okno narzędzia

1. Utwórz projekt VSIX o nazwie **DynamicToolWindow** i dodaj szablon elementu okna narzędzia o nazwie *DynamicWindowPane.cs*. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z oknem narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).

2. W pliku *DynamicWindowPanePackage.cs* znajdź deklarację DynamicWindowPanePackage. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> atrybuty, aby zarejestrować okno narzędzia.

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

     Powyższe atrybuty rejestrują okno narzędzia o nazwie DynamicWindowPane jako okno przejściowe, które nie jest utrwalone, gdy program Visual Studio jest zamknięty i ponownie otwarty. DynamicWindowPane jest otwierany zawsze, gdy <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> ma zastosowanie, i zamknięty w inny sposób.

3. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne. Nie powinno być widoczne okno narzędzia.

4. Otwórz projekt w wystąpieniu eksperymentalnym. Powinno pojawić się okno narzędzia.
