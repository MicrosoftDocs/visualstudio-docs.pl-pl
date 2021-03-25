---
title: 'Instrukcje: dostarczanie automatyzacji dla systemu Windows | Microsoft Docs'
description: Dowiedz się, jak zapewnić automatyzację okien dokumentów i narzędzi w programie Visual Studio przy użyciu metod Microsoft. VisualStudio. Shell. Interop.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 774b32dc1554fb6d6466be7e915fbaeea8185798
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078750"
---
# <a name="how-to-provide-automation-for-windows"></a>Instrukcje: zapewnianie automatyzacji dla systemu Windows

Możesz zapewnić automatyzację okien dokumentów i narzędzi. Zapewnianie automatyzacji jest zalecane w każdym przypadku, gdy chcesz, aby obiekty automatyzacji były dostępne w oknie, a środowisko nie zapewnia jeszcze gotowego obiektu automatyzacji, tak jak na liście zadań.

## <a name="automation-for-tool-windows"></a>Automatyzacja dla okien narzędzi

Środowisko zapewnia automatyzację w oknie narzędzia przez zwrócenie standardowego <xref:EnvDTE.Window> obiektu, jak wyjaśniono w poniższej procedurze:

1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodę za pomocą środowiska z [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) jako `VSFPROPID` parametr do pobrania `Window` obiektu.

2. Gdy wywołujący żąda obiektu automatyzacji określonego przez pakietu VSPackage dla okna narzędzia przez <xref:EnvDTE.Window.Object%2A> , środowisko wywołuje `QueryInterface` dla `IExtensibleObject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> lub `IDispatch` interfejsy. Obie `IExtensibleObject` i `IVsExtensibleObject` zapewniają <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metodę.

3. Gdy środowisko następnie wywołuje `GetAutomationObject` metodę przekazującą `NULL` , należy odpowiedzieć przez przekazanie obiektu określonego przez pakietu VSPackage.

4. W przypadku wywołania `QueryInterface` elementu `IExtensibleObject` i `IVsExtensibleObject` niepowodzenia środowisko wywołuje program `QueryInterface` `IDispatch` .

## <a name="automation-for-document-windows"></a>Automatyzacja okien dokumentów

Obiekt standardowy <xref:EnvDTE.Document> jest również dostępny ze środowiska, chociaż Edytor może mieć własną implementację <xref:EnvDTE.Document> obiektu przez implementację `IExtensibleObject` interfejsu i odpowiadanie na `GetAutomationObject` .

Ponadto edytor może dostarczyć obiekt automatyzacji specyficzny dla pakietu VSPackage, pobrany przez <xref:EnvDTE.Document.Object%2A> metodę, implementując `IVsExtensibleObject` `IExtensibleObject` interfejsy lub. [Przykłady VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) współtworzą obiekt automatyzacji specyficzny dla dokumentu RTF.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
