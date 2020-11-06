---
title: Obiekt VSTextBuffer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 193d96be91839143893ac0798db723f3e94ea26c
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2020
ms.locfileid: "93413919"
---
# <a name="vstextbuffer-object"></a>Obiekt VSTextBuffer
Obiekt buforu tekstu reprezentuje strumień tekstu Unicode, który jest zazwyczaj skojarzony z plikiem. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>Obiekt może być używany poza kontekstem podstawowego edytora, jak w, w kreatorze.

 W poniższej tabeli przedstawiono interfejsy `VSTextBuffer` .

|Metoda|Opis|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standardowy interfejs OLE. Używany do obsługi operacji cofania/ponawiania w buforze.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standardowy interfejs OLE.|
|[Funkcja](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Włącza akcje tworzenia związków (czyli akcje, które są pogrupowane w jednej jednostce cofania/ponawiania).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Włącza trwałość danych dokumentu zarządzanych przez bufor tekstu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Zapewnia podstawowe usługi; używany przez wielu klientów.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Służy do przeszukiwania buforu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Zapewnia możliwości odczytu i zapisu przy użyciu współrzędnych dwuwymiarowych. Dziedziczy z `IVsTextBuffer` .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Zapewnia możliwości odczytu i zapisu przy użyciu współrzędnych jednowymiarowych. Dziedziczy z `IVsTextBuffer` .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Zapewnia szybki, zorientowany na strumień, sekwencyjny dostęp do tekstu w buforze.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Zapewnia dostęp do ogólnej kolekcji właściwości. Najważniejszym właściwość jest nazwa lub moniker buforu. Możesz przechowywać własne dane losowe w buforze przy użyciu tego interfejsu, tworząc identyfikator GUID i używając go jako klucz.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Obsługuje punkty połączenia dla zdarzeń.|

## <a name="remarks"></a>Uwagi
 `VSTextBuffer`Zwykle jest to spowodowane `QueryInterface` wywołaniem `IVsTextBuffer` . Aby uzyskać więcej informacji, zobacz [bufor tekstu](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Edycja ilustracji](https://www.microsoft.com/download/details.aspx?id=55984)