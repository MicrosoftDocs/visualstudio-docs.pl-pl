---
title: Aktualizowanie interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db5be965119d1564f2a4bf8a15892af7142663e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186359"
---
# <a name="updating-the-user-interface"></a>Aktualizowanie interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zaimplementowaniu polecenia można dodać kod, aby zaktualizować interfejs użytkownika do stanu nowych poleceń.  
  
 W typowej aplikacji Win32 zestaw poleceń może być ciągle sondowany, a stan poszczególnych poleceń można dostosować podczas wyświetlania ich przez użytkownika. Jednak ponieważ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] powłoka może obsługiwać nieograniczoną liczbę pakietów VSPackage, rozbudowane sondowanie może zmniejszyć czas odpowiedzi, szczególnie w przypadku sondowania zestawów międzyoperacyjnych między kodem zarządzanym i modelem com.  
  
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
 [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementacja](../extensibility/internals/command-implementation.md)
