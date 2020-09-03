---
title: 'Instrukcje: dostarczanie automatyzacji dla systemu Windows | Microsoft Docs'
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
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191844"
---
# <a name="how-to-provide-automation-for-windows"></a>Instrukcje: zapewnianie automatyzacji dla systemu Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Możesz zapewnić automatyzację okien dokumentów i narzędzi. Zapewnianie automatyzacji jest zalecane w każdym przypadku, gdy chcesz, aby obiekty automatyzacji były dostępne w oknie, a środowisko nie zapewnia jeszcze gotowego obiektu automatyzacji, tak jak na liście zadań.  
  
## <a name="automation-for-tool-windows"></a>Automatyzacja dla okien narzędzi  
 Środowisko zapewnia automatyzację w oknie narzędzia przez zwrócenie standardowego <xref:EnvDTE.Window> obiektu, jak wyjaśniono w poniższej procedurze:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Aby zapewnić automatyzację okien narzędzi  
  
1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodę przez środowisko z <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> `VSFPROPID` parametrem AS, aby uzyskać `Window` obiekt.  
  
2. Gdy wywołujący żąda obiektu automatyzacji określonego przez pakietu VSPackage dla okna narzędzia przez <xref:EnvDTE.Window.Object%2A> , środowisko wywołuje `QueryInterface` dla `IExtensibleObject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> lub `IDispatch` interfejsy. Obie `IExtensibleObject` i `IVsExtensibleObject` zapewniają <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metodę.  
  
3. Gdy środowisko następnie wywołuje `GetAutomationObject` metodę przekazującą `NULL` , należy odpowiedzieć przez przekazanie obiektu określonego przez pakietu VSPackage.  
  
4. W przypadku wywołania `QueryInterface` elementu `IExtensibleObject` i `IVsExtensibleObject` niepowodzenia środowisko wywołuje program `QueryInterface` `IDispatch` .  
  
## <a name="automation-for-document-windows"></a>Automatyzacja okien dokumentów  
 Obiekt standardowy <xref:EnvDTE.Document> jest również dostępny ze środowiska, chociaż Edytor może mieć własną implementację `T:EnvDTE.Document` obiektu przez implementację `IExtensibleObject` interfejsu i odpowiadanie na `GetAutomationObject` .  
  
 Ponadto edytor może dostarczyć obiekt automatyzacji specyficzny dla pakietu VSPackage, pobrany przez <xref:EnvDTE.Document.Object%2A> metodę, implementując `IVsExtensibleObject` `IExtensibleObject` interfejsy lub. [Przykłady VSSDK](../../misc/vssdk-samples.md) współtworzą obiekt automatyzacji specyficzny dla dokumentu RTF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
