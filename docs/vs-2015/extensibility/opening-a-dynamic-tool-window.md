---
title: Otwieranie dynamicznego okna narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 073e8a2e7ff13dad0e413aa47b7875260f612cd2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773798"
---
# <a name="opening-a-dynamic-tool-window"></a>Otwieranie dynamicznego okna narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okna narzędzi zwykle są otwierane polecenie menu lub równoważne skrót klawiaturowy. Czasami jednak możesz potrzebować okna narzędzi, które otwiera za każdym razem kontekstowi interfejsu użytkownika stosuje się i zostanie zamknięte po kontekstu interfejsu użytkownika nie ma już zastosowania. Okna narzędzi, takie jak te są nazywane *dynamiczne* lub *automatycznie widoczne*.  
  
> [!NOTE]
>  Aby uzyskać listę wstępnie zdefiniowane konteksty interfejsu użytkownika, zobacz <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Aby uzyskać  
  
 Jeśli chcesz otworzyć dynamicznego okna narzędzi w momencie uruchamiania i jest możliwe do utworzenia nie powiedzie się, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interfejs i przetestować warunki błędów w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metody. Aby powłoki dowiedzieć się, że masz dynamicznego okna narzędzi, który powinien zostać otwarty podczas uruchamiania, należy dodać `SupportsDynamicToolOwner` ma wartość (1) do rejestracji pakietu. Ta wartość nie jest częścią standardu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, dlatego należy utworzyć atrybut niestandardowy, aby ją dodać. Aby uzyskać więcej informacji na temat atrybutów niestandardowych, zobacz [za pomocą niestandardowego atrybutu rejestracji, aby zarejestrować rozszerzenie](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Użyj <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> można otworzyć okna narzędzi. Okno narzędzia jest tworzony, zgodnie z potrzebami.  
  
> [!NOTE]
>  Dynamicznego okna narzędzi, może zostać zamknięty przez użytkownika. Jeśli chcesz utworzyć polecenie menu, dzięki czemu użytkownik może ponownie otworzyć okna narzędzi, polecenia menu powinno być włączone w tym samym kontekście interfejsu użytkownika, który otwiera okno narzędzi oraz wyłączone, w przeciwnym razie.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Aby otworzyć dynamicznego okna narzędzi  
  
1.  Utwórz projekt VSIX, o nazwie **DynamicToolWindow** i dodać szablon elementu okno narzędzia o nazwie **DynamicWindowPane.cs**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  W pliku DynamicWindowPanePackage.cs odnaleźć deklaracji DynamicWindowPanePackage. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> i atrybuty T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute zarejestrować okna narzędzia.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Rejestruje to okna narzędzia o nazwie DynamicWindowPane jako przejściowe okno, które nie są zachowywane w przypadku zamknięcia i ponownego otworzenia programu Visual Studio. Zostanie otwarty DynamicWindowPane zawsze wtedy, gdy <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> stosuje i zamknięte w inny sposób.  
  
3.  Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona. Nie powinien być widoczny okna narzędzia.  
  
4.  Otwórz projekt w doświadczalnym wystąpieniu. Okno narzędzia powinna zostać wyświetlona.

