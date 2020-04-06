---
title: Aktualizowanie interfejsu użytkownika | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698888"
---
# <a name="updating-the-user-interface"></a>Aktualizowanie interfejsu użytkownika
Po zaimplementacji polecenia można dodać kod, aby zaktualizować interfejs użytkownika o stanie nowych poleceń.

 W typowej aplikacji Win32 zestaw poleceń może być stale sondowany, a stan poszczególnych poleceń można dostosować, gdy użytkownik je wyświetla. Jednak ponieważ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powłoki może obsługiwać nieograniczoną liczbę VSPackages, obszerne sondowania może zmniejszyć szybkość reakcji, zwłaszcza sondowania między zestawami między kodem zarządzanym i COM.

### <a name="to-update-the-ui"></a>Aby zaktualizować interfejs użytkownika

1. Wykonaj jedną z następujących czynności:

    - Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metody.

         Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> można uzyskać z <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługi, w następujący sposób.

        ```csharp
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)
        {
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));
            if (vsShell != null)
            {
                int hr = vsShell.UpdateCommandUI(0);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
            }
        }

        ```

         Jeśli parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> jest niezerowy`TRUE`( ), aktualizacja jest wykonywana synchronicznie i natychmiast. Zaleca się, aby`FALSE`przekazać zero ( ) dla tego parametru, aby pomóc utrzymać dobrą wydajność. Jeśli chcesz uniknąć buforowania, zastosuj `DontCache` flagę podczas tworzenia polecenia w pliku vsct. Niemniej jednak należy użyć flagi ostrożnie lub wydajność może zmniejszyć. Aby uzyskać więcej informacji na temat flag poleceń, zobacz [dokumentację elementu flagi polecenia.](../extensibility/command-flag-element.md)

    - W vspackages, które hostują formant ActiveX przy użyciu modelu aktywacji w miejscu <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> w oknie, może być bardziej wygodne do korzystania z metody. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsie <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> i metoda <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> w interfejsie są funkcjonalnie równoważne. Oba powodują, że środowisko ponownie kwerendy stan wszystkich poleceń. Zazwyczaj aktualizacja nie jest wykonywana natychmiast. Zamiast tego aktualizacja jest opóźniona do czasu bezczynnego. Powłoka buforuje stan polecenia, aby pomóc w utrzymaniu dobrej wydajności. Jeśli chcesz uniknąć buforowania, zastosuj `DontCache` flagę podczas tworzenia polecenia w pliku vsct. Niemniej jednak należy użyć flagi ostrożnie, ponieważ wydajność może zmniejszyć.

         Należy zauważyć, że <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> można uzyskać `QueryInterface` interfejs, <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> wywołując metodę na obiekcie <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> lub uzyskując interfejs z usługi.

## <a name="see-also"></a>Zobacz też
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Wdrażanie](../extensibility/internals/command-implementation.md)
