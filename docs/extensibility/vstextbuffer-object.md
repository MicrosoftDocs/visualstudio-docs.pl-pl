---
title: VsTextBuffer, obiekt | Microsoft Docs
description: Obiekt VSTextBuffer reprezentuje strumień tekstu Unicode, który jest zazwyczaj skojarzony z plikiem. W tym artykule wymieniono interfejsy usługi VSTextBuffer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3660a8dbb4a0a1280d5a3f428f73f3498244af7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905179"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer, obiekt
Obiekt buforu tekstowego reprezentuje strumień tekstu Unicode, który jest zazwyczaj skojarzony z plikiem. Obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> można używać poza kontekstem edytora podstawowego, jak w kreatorze.

 W poniższej tabeli przedstawiono interfejsy programu `VSTextBuffer` .

|Metoda|Opis|
|------------|-----------------|
|[Iolecommandtarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standardowy interfejs OLE. Służy do obsługi cofania/ponownego cofania w buforze.|
|[Ipersistfile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standardowy interfejs OLE.|
|[Ipersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie akcji pogotowień (czyli akcji pogrupowanych w jedną jednostkę cofania/ponownego tworzenia).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Umożliwia trwałość danych dokumentów zarządzanych przez bufor tekstowy.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Zapewnia podstawowe usługi; używany przez wielu klientów.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Służy do przeszukiwania buforu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Zapewnia możliwości odczytu i zapisu przy użyciu współrzędnych dwuwymiarowych. Dziedziczy z `IVsTextBuffer` .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Zapewnia możliwości odczytu i zapisu przy użyciu współrzędnych jednowymiarowych. Dziedziczy z `IVsTextBuffer` .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Zapewnia szybki, zorientowany na strumień sekwencyjny dostęp do tekstu w buforze.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Zapewnia dostęp do ogólnej kolekcji właściwości. Najważniejszą właściwością jest nazwa lub moniker buforu. Możesz przechowywać własne losowe dane w buforze za pomocą tego interfejsu, tworząc identyfikator GUID i używając go jako klucza.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Obsługuje punkty połączenia dla zdarzeń.|

## <a name="remarks"></a>Uwagi
 Zazwyczaj `VSTextBuffer` znajduje się on w `QueryInterface` wywołaniu w . `IVsTextBuffer` Aby uzyskać więcej informacji, zobacz [Bufor tekstowy](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Edycja figur](https://www.microsoft.com/download/details.aspx?id=55984)