---
title: Obiekt VSTextBuffer | Dokumenty firmy Microsoft
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
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697725"
---
# <a name="vstextbuffer-object"></a>OBIEKT VSTextBuffer
Obiekt buforu tekstu reprezentuje strumień tekstu Unicode, który jest zazwyczaj skojarzony z plikiem. Obiekt <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> może być używany poza kontekstem edytora podstawowego, jak w kreatorze.

 W poniższej tabeli `VSTextBuffer`przedstawiono interfejsy programu .

|Metoda|Opis|
|------------|-----------------|
|[Iolecommandtarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standardowy interfejs OLE. Służy do cofania/ponawiania obsługi w buforze.|
|[Ipersistfile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standardowy interfejs OLE.|
|[Ipersiststream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie akcji związków (czyli akcji zgrupowanych w jedną jednostkę cofania/ponawiania).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Umożliwia trwałość danych dokumentu zarządzanych przez bufor tekstu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Świadczy podstawowe usługi; przez wielu klientów.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Służy do wyszukiwania buforu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Zapewnia możliwości odczytu i zapisu przy użyciu współrzędnych dwuwymiarowych. Dziedziczy `IVsTextBuffer`po pliku .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Zapewnia możliwości odczytu i zapisu przy użyciu współrzędnych jednowymiarowych. Dziedziczy `IVsTextBuffer`po pliku .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Zapewnia szybki, zorientowany na strumień, sekwencyjny dostęp do tekstu w buforze.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Zapewnia dostęp do ogólnej kolekcji właściwości. Najważniejszą właściwością jest nazwa lub moniker buforu. Można przechowywać własne losowe dane w buforze za pomocą tego interfejsu, tworząc identyfikator GUID i używając go jako klucza.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Obsługuje punkty połączenia dla zdarzeń.|

## <a name="remarks"></a>Uwagi
 Zwykle `VSTextBuffer` znajduje się `QueryInterface` przez `IVsTextBuffer`połączenie na . Aby uzyskać więcej informacji, zobacz [Bufor tekstu](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015).

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Edytuj rysunki](https://www.microsoft.com/download/details.aspx?id=55984)
