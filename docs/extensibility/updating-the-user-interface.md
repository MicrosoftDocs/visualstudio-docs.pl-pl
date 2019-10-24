---
title: Aktualizowanie interfejsu użytkownika | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718788"
---
# <a name="updating-the-user-interface"></a>Aktualizowanie interfejsu użytkownika
Po zaimplementowaniu polecenia można dodać kod, aby zaktualizować interfejs użytkownika do stanu nowych poleceń.

 W typowej aplikacji Win32 zestaw poleceń może być ciągle sondowany, a stan poszczególnych poleceń można dostosować podczas wyświetlania ich przez użytkownika. Jednak ponieważ powłoka [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] może obsługiwać nieograniczoną liczbę pakietów VSPackage, rozbudowane sondowanie może zmniejszyć czas odpowiedzi, szczególnie w przypadku sondowania zestawów międzyoperacyjnych między kodem zarządzanym i modelem COM.

### <a name="to-update-the-ui"></a>Aby zaktualizować interfejs użytkownika

1. Wykonaj jedną z następujących czynności:

    - Wywołaj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.

         Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> można uzyskać z usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> w następujący sposób.

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

         Jeśli parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> ma wartość różną od zera (`TRUE`), aktualizacja zostanie przeprowadzona synchronicznie i natychmiast. Zalecamy przekazanie wartości zero (`FALSE`) dla tego parametru, aby pomóc w utrzymaniu dobrej wydajności. Jeśli chcesz uniknąć buforowania, Zastosuj flagę `DontCache` podczas tworzenia polecenia w pliku. vsct. Niemniej jednak należy zachować ostrożność lub zmniejszyć wydajność. Aby uzyskać więcej informacji na temat flag poleceń, zobacz dokumentację [elementu flagi polecenia](../extensibility/command-flag-element.md) .

    - W pakietów VSPackage, który hostuje formant ActiveX przy użyciu modelu aktywacji w miejscu w oknie, może być wygodniejszy do użycia metody <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> w interfejsie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> i Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> w interfejsie <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> są funkcjonalnie równoważne. Oba te elementy powodują ponowne badanie stanu wszystkich poleceń w środowisku. Zwykle aktualizacja nie jest przeprowadzana natychmiast. Zamiast tego, aktualizacja jest opóźniona do czasu bezczynności. Powłoka buforuje stan polecenia, aby pomóc w utrzymaniu dobrej wydajności. Jeśli chcesz uniknąć buforowania, Zastosuj flagę `DontCache` podczas tworzenia polecenia w pliku. vsct. Niemniej jednak należy zachować ostrożność przy użyciu flagi, ponieważ wydajność może ulec zmniejszeniu.

         Należy zauważyć, że można uzyskać interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>, wywołując metodę `QueryInterface` na obiekcie <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> lub pobierając interfejs z usługi <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>.

## <a name="see-also"></a>Zobacz także
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementacja](../extensibility/internals/command-implementation.md)