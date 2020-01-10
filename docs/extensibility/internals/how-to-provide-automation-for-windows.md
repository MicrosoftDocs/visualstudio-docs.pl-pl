---
title: 'Instrukcje: dostarczanie automatyzacji dla systemu Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848853"
---
# <a name="how-to-provide-automation-for-windows"></a>Instrukcje: zapewnianie automatyzacji dla systemu Windows

Możesz zapewnić automatyzację okien dokumentów i narzędzi. Zapewnianie automatyzacji jest zalecane w każdym przypadku, gdy chcesz, aby obiekty automatyzacji były dostępne w oknie, a środowisko nie zapewnia jeszcze gotowego obiektu automatyzacji, tak jak na liście zadań.

## <a name="automation-for-tool-windows"></a>Automatyzacja dla okien narzędzi

Środowisko zapewnia automatyzację w oknie narzędzia przez zwrócenie standardowego obiektu <xref:EnvDTE.Window>, jak wyjaśniono w poniższej procedurze:

1. Wywołaj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> za pośrednictwem środowiska z [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) jako parametr `VSFPROPID`, aby uzyskać `Window` obiekt.

2. Gdy wywołujący żąda obiektu automatyzacji określonego przez pakietu VSPackage dla okna narzędzia przez <xref:EnvDTE.Window.Object%2A>, środowisko wywołuje `QueryInterface` `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>lub interfejsów `IDispatch`. Zarówno `IExtensibleObject`, jak i `IVsExtensibleObject` zapewniają metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>.

3. Gdy środowisko wywoła następnie `GetAutomationObject` przekazanie metody `NULL`, należy odpowiedzieć przez przekazanie obiektu określonego pakietu VSPackage.

4. Jeśli wywołanie `QueryInterface` dla `IExtensibleObject` i `IVsExtensibleObject` nie powiedzie się, środowisko wywoła `QueryInterface` dla `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatyzacja okien dokumentów

Standardowy obiekt <xref:EnvDTE.Document> jest również dostępny ze środowiska, chociaż Edytor może mieć własną implementację obiektu <xref:EnvDTE.Document> przez implementację `IExtensibleObject` interfejs i odpowiadanie na `GetAutomationObject`.

Ponadto edytor może dostarczyć obiekt automatyzacji specyficzny dla pakietu VSPackage, pobrany przez metodę <xref:EnvDTE.Document.Object%2A>, implementując interfejsy `IVsExtensibleObject` lub `IExtensibleObject`. [Przykłady VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) współtworzą obiekt automatyzacji specyficzny dla dokumentu RTF.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
