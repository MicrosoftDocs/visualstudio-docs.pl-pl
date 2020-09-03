---
title: Obiekt VSTextBuffer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b68d443e542b6bd707aacc2b22d0efc1064152c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690642"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer, obiekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obiekt buforu tekstu reprezentuje strumień tekstu Unicode, który jest zazwyczaj skojarzony z plikiem. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>Obiekt może być używany poza kontekstem podstawowego edytora, tak jak w przypadku kreatora.  
  
 W poniższej tabeli przedstawiono interfejsy `VSTextBuffer` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standardowy interfejs OLE. Używane głównie do obsługi operacji cofania/ponawiania w buforze.|  
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
 `VSTextBuffer`Zwykle jest to spowodowane `QueryInterface` wywołaniem `IVsTextBuffer` . Aby uzyskać więcej informacji, zobacz [bufor tekstu](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edycja ilustracji](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
