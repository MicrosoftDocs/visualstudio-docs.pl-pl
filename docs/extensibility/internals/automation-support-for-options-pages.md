---
title: Obsługa automatyzacji dla stron opcji | Microsoft Docs
description: Dowiedz się, jak udostępnić niestandardowe strony opcji narzędzi w pakietów VSPackage dla modelu automatyzacji programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e15b1f8bdd27e013e1ef2060d9867a81e8ddde3
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190034"
---
# <a name="automation-support-for-options-pages"></a>Obsługa automatyzacji dla stron opcji
Pakietów VSPackage mogą udostępniać okna dialogowe **opcji** niestandardowych do menu **Narzędzia** (strony **opcji narzędzia** ) w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i mogą być dostępne dla modelu automatyzacji.

## <a name="tools-options-pages"></a>strony opcji Narzędzi
 Aby utworzyć stronę **opcji narzędzi** , pakietu VSPackage musi dostarczyć implementację kontroli użytkownika, która jest zwracana do środowiska przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody pakietu VSPackage. (Lub, dla kodu zarządzanego, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody).

 Jest to opcjonalne, ale zdecydowanie zalecane, aby umożliwić dostęp do tej nowej strony za pomocą modelu automatyzacji. Można to zrobić, wykonując następujące czynności:

1. Rozszerzając <xref:EnvDTE._DTE.Properties%2A> obiekt przez implementację obiektu pochodnego IDispatch.

2. Zwróć implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody (lub dla kodu zarządzanego <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> Metoda) do obiektu pochodnego IDispatch.

3. Gdy odbiorca automatyzacji wywołuje <xref:EnvDTE._DTE.Properties%2A> metodę na niestandardowej stronie właściwości **opcji** , środowisko używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody, aby uzyskać implementację automatyzacji strony **opcji narzędzi** niestandardowych.

4. Obiekt automatyzacji elementu pakietu VSPackage jest następnie używany do dostarczania każdej <xref:EnvDTE.Property> zwróconej przez <xref:EnvDTE._DTE.Properties%2A> .

   Aby zapoznać się z przykładem implementującym niestandardowe **Opcje narzędzi** , zobacz [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Zobacz też
- [Uwidacznianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)
