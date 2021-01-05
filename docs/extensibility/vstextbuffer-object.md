---
title: Obiekt VSTextBuffer | Microsoft Docs
description: Obiekt VSTextBuffer reprezentuje strumień tekstu Unicode, który jest zazwyczaj skojarzony z plikiem. W tym artykule wymieniono interfejsy VSTextBuffer.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e5c2afa08e9c480342bff95d417dfb9174250b83
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863949"
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