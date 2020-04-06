---
title: 'Jak: Zapewnienie automatyzacji dla systemu Windows | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707951"
---
# <a name="how-to-provide-automation-for-windows"></a>Jak: Zapewnienie automatyzacji dla okien

Można zapewnić automatyzację okien dokumentów i narzędzi. Zapewnienie automatyzacji jest wskazane, gdy chcesz udostępnić obiekty automatyzacji w oknie, a środowisko nie zapewnia już gotowego obiektu automatyzacji, tak jak ma to miejsce w przypadku listy zadań.

## <a name="automation-for-tool-windows"></a>Automatyzacja okien narzędzi

Środowisko zapewnia automatyzację w oknie narzędzia, <xref:EnvDTE.Window> zwracając standardowy obiekt, jak wyjaśniono w poniższej procedurze:

1. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody za pośrednictwem środowiska z [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) jako `VSFPROPID` parametr, aby `Window` uzyskać obiekt.

2. Gdy obiekt wywołujący żąda obiektu automatyzacji specyficzne dla <xref:EnvDTE.Window.Object%2A>vspackage `QueryInterface` dla `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>okna narzędzia `IDispatch` za pośrednictwem , środowisko wymaga , lub interfejsów. Oba `IExtensibleObject` `IVsExtensibleObject` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> zapewnić metodę.

3. Gdy środowisko następnie `GetAutomationObject` wywołuje `NULL`metodę przekazywania, odpowiadaj, przekazując z powrotem obiekt specyficzny dla vspackage.

4. Jeśli `QueryInterface` wywołanie `IExtensibleObject` i `IVsExtensibleObject` niepowodzenie, `QueryInterface` środowisko `IDispatch`wymaga .

## <a name="automation-for-document-windows"></a>Automatyzacja okien dokumentów

Obiekt <xref:EnvDTE.Document> standardowy jest również dostępny w środowisku, chociaż edytor <xref:EnvDTE.Document> może mieć `IExtensibleObject` własną implementację `GetAutomationObject`obiektu, implementując interfejs i odpowiadając na .

Ponadto edytor może zapewnić obiekt automatyzacji specyficzne dla VSPackage, pobrane za pośrednictwem <xref:EnvDTE.Document.Object%2A> metody, implementując `IVsExtensibleObject` lub `IExtensibleObject` interfejsów. [Próbki vssdk](https://github.com/Microsoft/VSSDK-Extensibility-Samples) przyczynia rtf obiektu automatyzacji specyficzne dla dokumentu.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
