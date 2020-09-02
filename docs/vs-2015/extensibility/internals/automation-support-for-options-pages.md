---
title: Obsługa automatyzacji dla stron opcji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157244"
---
# <a name="automation-support-for-options-pages"></a>Obsługa automatyzacji dla stron opcji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietów VSPackage mogą udostępniać okna dialogowe **opcji** niestandardowych do menu **Narzędzia** (strony opcji narzędzia) w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i mogą być dostępne dla modelu automatyzacji.  
  
## <a name="tools-options-pages"></a>Strony opcji narzędzi  
 Aby utworzyć stronę **opcji narzędzi** , pakietu VSPackage musi dostarczyć implementację kontroli użytkownika, która została zwrócona do środowiska przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody (lub do kodu zarządzanego <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Metoda).  
  
 Jest to opcjonalne, ale zdecydowanie zalecane, aby umożliwić dostęp do tej nowej strony za pomocą modelu automatyzacji. Można to zrobić, wykonując następujące czynności:  
  
1. Rozszerzając <xref:EnvDTE._DTE.Properties%2A> obiekt przez implementację obiektu pochodnego IDispatch.  
  
2. Zwróć implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody (lub dla kodu zarządzanego <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> Metoda) do obiektu pochodnego IDispatch.  
  
3. Gdy odbiorca automatyzacji wywołuje <xref:EnvDTE._DTE.Properties%2A> metodę na niestandardowej stronie właściwości **opcji** , środowisko używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody, aby uzyskać implementację automatyzacji strony **opcji narzędzi** niestandardowych.  
  
4. Obiekt automatyzacji elementu pakietu VSPackage jest następnie używany do dostarczania każdej <xref:EnvDTE.Property> zwróconej przez <xref:EnvDTE._DTE.Properties%2A> .  
  
   Aby zapoznać się z przykładem implementującym niestandardowe opcje narzędzi, zobacz [VSSDK Samples](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)
