---
title: Obsługa automatyzacji dla stron opcji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848970"
---
# <a name="automation-support-for-options-pages"></a>Obsługa automatyzacji dla stron opcji
Pakietów VSPackage mogą udostępniać okna dialogowe **opcji** niestandardowych do menu **Narzędzia** (strony**opcji narzędzia** ) w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i mogą być dostępne dla modelu automatyzacji.

## <a name="tools-options-pages"></a>strony opcji Narzędzi
 Aby utworzyć stronę **opcji narzędzi** , pakietu VSPackage musi dostarczyć implementację kontroli użytkownika, która została zwrócona do środowiska za pomocą implementacji pakietu vspackage metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>. (Lub, dla kodu zarządzanego, Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>).

 Jest to opcjonalne, ale zdecydowanie zalecane, aby umożliwić dostęp do tej nowej strony za pomocą modelu automatyzacji. Można to zrobić, wykonując następujące czynności:

1. Poszerzenie obiektu <xref:EnvDTE._DTE.Properties%2A> przez implementację obiektu pochodnego IDispatch.

2. Zwróć implementację metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (lub dla kodu zarządzanego Metoda <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>) do obiektu pochodnego IDispatch.

3. Gdy odbiorca usługi Automation wywołuje metodę <xref:EnvDTE._DTE.Properties%2A> na niestandardowej stronie właściwości **opcji** , środowisko używa metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>, aby uzyskać implementację automatyzacji strony **opcji narzędzi** niestandardowych.

4. Obiekt automatyzacji pakietu VSPackage jest następnie używany do zapewnienia każdej <xref:EnvDTE.Property> zwróconej przez <xref:EnvDTE._DTE.Properties%2A>.

   Aby zapoznać się z przykładem implementującym niestandardowe **Opcje narzędzi** , zobacz [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Zobacz także
- [Uwidacznianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)
