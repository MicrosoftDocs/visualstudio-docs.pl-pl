---
title: 'Instrukcje: Zapewnianie automatyzacji dla Windows | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a4482069d16ef6f0f64472b838057949890a6d3
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335158"
---
# <a name="how-to-provide-automation-for-windows"></a>Instrukcje: Zapewnianie automatyzacji dla systemu windows

Możesz podać automatyzacji dla dokumentu i narzędzi systemu windows. Udostępnienie usługi automation zalecane jest zawsze wtedy, gdy chcesz udostępnić obiektów automatyzacji w oknie, a środowisko nie zawiera już obiekt automatyzacji gotowych do użycia, jak w przypadku listy zadań.

## <a name="automation-for-tool-windows"></a>Automatyzacji dla okien narzędzi

Środowisko zapewnia automatyzację w oknie narzędzi, zwracając standardowego <xref:EnvDTE.Window> obiektu zgodnie z opisem w poniższej procedurze:

1.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodę za pomocą środowiska z [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) jako `VSFPROPID` parametru, aby pobrać `Window` obiektu.

2.  Gdy obiekt wywołujący żąda obiekt automatyzacji specyficzne dla pakietu VSPackage dla okna narzędzia za pomocą <xref:EnvDTE.Window.Object%2A>, wywołania środowiska `QueryInterface` dla `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, lub `IDispatch` interfejsów. Zarówno `IExtensibleObject` i `IVsExtensibleObject` zapewniają <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metody.

3.  Gdy środowisko następnie wywołuje `GetAutomationObject` metoda przekazywania `NULL`, Odpowiedz, przekazując kopii obiektu specyficzne dla pakietu VSPackage.

4.  Jeśli wywołanie `QueryInterface` dla `IExtensibleObject` i `IVsExtensibleObject` zakończy się niepowodzeniem, a następnie wywołuje środowisko `QueryInterface` dla `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatyzacja okna dokumentu

Standardowa <xref:EnvDTE.Document> obiektu jest również dostępna w środowisku, chociaż Edytor może mieć własną implementację <xref:EnvDTE.Document> obiekt poprzez implementację `IExtensibleObject` interfejsu i reagowanie na nie `GetAutomationObject`.

Ponadto, edytor może zapewnić obiektu automatyzacji specyficzne dla pakietu VSPackage, pobierane w drodze <xref:EnvDTE.Document.Object%2A> metody, implementując `IVsExtensibleObject` lub `IExtensibleObject` interfejsów. [Przykłady VSSDK](http://aka.ms/vs2015sdksamples) przyczynia się do obiektu automatyzacji specyficzne dla dokumentu w formacie RTF.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>