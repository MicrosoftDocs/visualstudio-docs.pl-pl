---
title: 'Instrukcje: Zapewnianie automatyzacji dla Windows | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 38e15c19ad5f9b0596240f473e078ebb6452c22b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773307"
---
# <a name="how-to-provide-automation-for-windows"></a>Instrukcje: Zapewnianie automatyzacji dla systemu Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Możesz podać automatyzacji dla dokumentu i narzędzi systemu windows. Udostępnienie usługi automation zalecane jest zawsze wtedy, gdy chcesz udostępnić obiektów automatyzacji w oknie, a środowisko nie zawiera już obiekt automatyzacji gotowych do użycia, jak w przypadku listy zadań.  
  
## <a name="automation-for-tool-windows"></a>Automatyzacja narzędzi Windows  
 Środowisko zapewnia automatyzację w oknie narzędzi, zwracając standardowego <xref:EnvDTE.Window> obiektu zgodnie z opisem w poniższej procedurze:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Aby zapewnić automatyzacji dla okien narzędzi  
  
1.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodę za pomocą środowiska z <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> jako `VSFPROPID` parametru, aby pobrać `Window` obiektu.  
  
2.  Gdy obiekt wywołujący żąda obiekt automatyzacji specyficzne dla pakietu VSPackage dla okna narzędzia za pomocą <xref:EnvDTE.Window.Object%2A>, wywołania środowiska `QueryInterface` dla `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, lub `IDispatch` interfejsów. Zarówno `IExtensibleObject` i `IVsExtensibleObject` zapewniają <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metody.  
  
3.  Gdy środowisko następnie wywołuje `GetAutomationObject` metoda przekazywania `NULL`, Odpowiedz, przekazując kopii obiektu specyficzne dla pakietu VSPackage.  
  
4.  Jeśli wywołanie `QueryInterface` dla `IExtensibleObject` i `IVsExtensibleObject` zakończy się niepowodzeniem, a następnie wywołuje środowisko `QueryInterface` dla `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automatyzacja Windows dokumentu  
 Standardowa <xref:EnvDTE.Document> obiektu jest również dostępna w środowisku, chociaż Edytor może mieć własną implementację `T:EnvDTE.Document` obiekt poprzez implementację `IExtensibleObject` interfejsu i reagowanie na nie `GetAutomationObject`.  
  
 Ponadto, edytor może zapewnić obiektu automatyzacji specyficzne dla pakietu VSPackage, pobierane w drodze <xref:EnvDTE.Document.Object%2A> metody, implementując `IVsExtensibleObject` lub `IExtensibleObject` interfejsów. [Przykłady VSSDK](../../misc/vssdk-samples.md) przyczynia się do obiektu automatyzacji specyficzne dla dokumentu w formacie RTF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
