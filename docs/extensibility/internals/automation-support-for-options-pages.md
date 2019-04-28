---
title: Obsługa automatyzacji dla stron opcji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81cf358d3dfb8fc45a4f696b0483e28673094d44
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862033"
---
# <a name="automation-support-for-options-pages"></a>Automatyzacja obsługi dla stron opcji
Pakietów VSPackage może zapewnić niestandardowy **opcje** do okien dialogowych **narzędzia** menu (**opcje narzędzi** stron) w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i udostępnić je do usługi automation model.

## <a name="tools-options-pages"></a>strony opcji Narzędzi
 Aby utworzyć **opcje narzędzi** stronie pakietu VSPackage należy podać implementacja kontrolki użytkownika, powrót do środowiska poprzez implementację pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody. (Lub dla kodu zarządzanego, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody.)

 Jest opcjonalny, ale zalecamy, aby umożliwić dostęp do tej nowej strony za pomocą modelu automatyzacji. Można to zrobić wykonując następujące kroki:

1. Rozszerzanie <xref:EnvDTE._DTE.Properties%2A> obiektu za pomocą implementacji obiektu klasy pochodnej IDispatch.

2. Zwraca implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> — metoda (lub dla kodu zarządzanego <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metody) do obiektu klasy pochodnej IDispatch.

3. Kiedy wywołuje konsumenta automatyzacji <xref:EnvDTE._DTE.Properties%2A> metody na niestandardowy **opcji** używa środowiska strony właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodę, aby uzyskać niestandardowy **opcje narzędzi** automatyzacji strony Implementacja.

4. Obiektu automatyzacji pakietu VSPackage jest następnie używany do zapewnienia każdego <xref:EnvDTE.Property> zwrócone przez <xref:EnvDTE._DTE.Properties%2A>.

   Przykład implementacji niestandardowego **opcje narzędzi** stronie, zobacz [przykłady VSSDK](https://aka.ms/vs2015sdksamples).

## <a name="see-also"></a>Zobacz także
- [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)