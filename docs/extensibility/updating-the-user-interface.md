---
title: Aktualizowanie interfejsu użytkownika | Microsoft Docs
description: Dowiedz się, jak dodać kod, aby zaktualizować interfejs użytkownika po zaimplementowaniu nowego polecenia w pakietu VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fd088d6887e7c7b60ea5a4101de050149583c5a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893454"
---
# <a name="updating-the-user-interface"></a>Aktualizowanie interfejsu użytkownika
Po zaimplementowaniu polecenia można dodać kod, aby zaktualizować interfejs użytkownika do stanu nowych poleceń.

 W typowej aplikacji Win32 zestaw poleceń może być ciągle sondowany, a stan poszczególnych poleceń można dostosować podczas wyświetlania ich przez użytkownika. Jednak ponieważ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powłoka może obsługiwać nieograniczoną liczbę pakietów VSPackage, rozbudowane sondowanie może zmniejszyć czas odpowiedzi, szczególnie w przypadku sondowania zestawów międzyoperacyjnych między kodem zarządzanym i modelem com.

### <a name="to-update-the-ui"></a>Aby zaktualizować interfejs użytkownika

1. Wykonaj jedną z następujących czynności:

    - Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metodę.

         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>Interfejs można uzyskać z <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługi w następujący sposób.

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

         Jeśli parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> ma wartość różną od zera ( `TRUE` ), aktualizacja jest wykonywana synchronicznie i natychmiast. Zalecamy przekazanie wartości zero ( `FALSE` ) dla tego parametru, aby pomóc w utrzymaniu dobrej wydajności. Jeśli chcesz uniknąć buforowania, Zastosuj `DontCache` flagę podczas tworzenia polecenia w pliku. vsct. Niemniej jednak należy zachować ostrożność lub zmniejszyć wydajność. Aby uzyskać więcej informacji na temat flag poleceń, zobacz dokumentację [elementu flagi polecenia](../extensibility/command-flag-element.md) .

    - W pakietów VSPackage, który hostuje formant ActiveX przy użyciu modelu aktywacji w miejscu w oknie, może być wygodniejszy do używania <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metody. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>Metoda w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsie i <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> Metoda w <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfejsie są funkcjonalnie równoważne. Oba te elementy powodują ponowne badanie stanu wszystkich poleceń w środowisku. Zwykle aktualizacja nie jest przeprowadzana natychmiast. Zamiast tego, aktualizacja jest opóźniona do czasu bezczynności. Powłoka buforuje stan polecenia, aby pomóc w utrzymaniu dobrej wydajności. Jeśli chcesz uniknąć buforowania, Zastosuj `DontCache` flagę podczas tworzenia polecenia w pliku. vsct. Niemniej jednak należy zachować ostrożność przy użyciu flagi, ponieważ wydajność może ulec zmniejszeniu.

         Należy zauważyć, że można uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfejs, wywołując `QueryInterface` metodę na <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> obiekcie lub pobierając interfejs z <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi.

## <a name="see-also"></a>Zobacz też
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementacja](../extensibility/internals/command-implementation.md)
