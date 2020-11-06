---
title: Obiekt VSTextView | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a52b1d480aaef11296517f1b9c5bb049f2488a8d
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2020
ms.locfileid: "93413934"
---
# <a name="vstextview-object"></a>Obiekt VSTextView

Widok tekstu to okno, które umożliwia użytkownikom wyświetlanie i edytowanie tekstu w formacie Unicode w buforze tekstu. W rzeczywistości widok jest tym, czego większość użytkowników odwołuje się jako edytor. Ponieważ widok jest oddzielony od buforu przez różne warstwy tekstu (Zawijanie wierszy, tekst konspektu itd.), widok nie musi być dokładną reprezentacją tekstu w buforze. Aby uzyskać więcej informacji na temat widoku tekstu, zobacz [dostęp do widoku TheText przy użyciu starszego interfejsu API](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

W poniższej tabeli przedstawiono interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiekcie.

|Interfejs|Opis|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie akcji złożonych (czyli akcji, które są pogrupowane w jednej jednostce cofania/ponawiania).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Zapewnia podstawowe metody zarządzania widokiem i uzyskiwania do niego dostępu. `IVsTextView` nie jest bezpieczny wątkowo.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Tworzy okienko okna i zarządza nim.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Współdziała z warstwami tekstu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Wykonuje operacje w widoku z innego wątku.|

## <a name="see-also"></a>Zobacz też

- [Edycja ilustracji](https://www.microsoft.com/download/details.aspx?id=55984)
- [Obiekt VSTextBuffer](../extensibility/vstextbuffer-object.md)