---
title: Obsługa automatyzacji dla stron opcji | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157244"
---
# <a name="automation-support-for-options-pages"></a>Obsługa automatyzacji dla stron opcji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietów VSPackage może zapewnić niestandardowy **opcje** do okien dialogowych **narzędzia** menu (strony opcji narzędzi) w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i udostępnić je do modelu automatyzacji.  
  
## <a name="tools-options-pages"></a>Strony opcji narzędzi  
 Aby utworzyć **opcje narzędzi** stronie pakietu VSPackage należy podać implementacja kontrolki użytkownika, powrót do środowiska poprzez implementację pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody (lub dla kodu zarządzanego <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Metoda).  
  
 Jest opcjonalny, ale zalecamy, aby umożliwić dostęp do tej nowej strony za pomocą modelu automatyzacji. Można to zrobić przez następujące kroki:  
  
1. Rozszerzanie <xref:EnvDTE._DTE.Properties%2A> obiektu za pomocą implementacji obiektu klasy pochodnej IDispatch.  
  
2. Zwraca implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> — metoda (lub dla kodu zarządzanego <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metody) do obiektu klasy pochodnej IDispatch.  
  
3. Kiedy wywołuje konsumenta automatyzacji <xref:EnvDTE._DTE.Properties%2A> metody na niestandardowy **opcji** używa środowiska strony właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodę, aby uzyskać niestandardowy **opcje narzędzi** automatyzacji strony Implementacja.  
  
4. Obiektu automatyzacji pakietu VSPackage jest następnie używany do zapewnienia każdego <xref:EnvDTE.Property> zwrócone przez <xref:EnvDTE._DTE.Properties%2A>.  
  
   Przykład wykonania niestandardowej strony opcji narzędzi, zobacz [przykłady VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)
