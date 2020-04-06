---
title: Obsługa automatyzacji stron opcji | Dokumenty firmy Microsoft
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
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709930"
---
# <a name="automation-support-for-options-pages"></a>Obsługa automatyzacji stron opcji
Pakiety VSPackages mogą udostępniać niestandardowe **okna dialogowe Opcje** do menu **Narzędzia** (Strony**Opcje narzędzi)** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i udostępniać je modelowi automatyzacji.

## <a name="tools-options-pages"></a>strony opcji Narzędzi
 Aby utworzyć stronę **Opcje narzędzi,** VSPackage musi zapewnić implementacji kontroli użytkownika zwrócone do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> środowiska za pośrednictwem vsPackage implementacji metody. (Lub, dla kodu zarządzanego, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metoda.)

 Jest to opcjonalne, ale zdecydowanie zalecane, aby umożliwić dostęp do tej nowej strony za pośrednictwem modelu automatyzacji. Można to zrobić za pomocą następujących kroków:

1. Rozszerzanie <xref:EnvDTE._DTE.Properties%2A> obiektu poprzez implementację obiektu pochodnego IDispatch.

2. Zwraca implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody (lub dla <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> kodu zarządzanego metody) do obiektu pochodnego IDispatch.

3. Gdy konsument automatyzacji <xref:EnvDTE._DTE.Properties%2A> wywołuje metodę na niestandardowej option **strony** właściwości, środowisko używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody, aby uzyskać implementację automatyzacji niestandardowych opcji **narzędzi** strony.

4. Obiekt automatyzacji VSPackage jest następnie używany <xref:EnvDTE.Property> do <xref:EnvDTE._DTE.Properties%2A>zapewnienia każdego zwróconego przez .

   Aby zapoznać się z przykładową stroną implementującą niestandardową stronę **Opcje narzędzi,** zobacz [Przykłady programu VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Zobacz też
- [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)
