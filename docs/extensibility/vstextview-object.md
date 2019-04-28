---
title: Obiekt VSTextView | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab54fce0271438f89ec66b4fc5d8db1ebe21634f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953091"
---
# <a name="vstextview-object"></a>Obiekt VSTextView
Widok tekstu jest oknem, pozwalającą użytkownikom na wyświetlanie i edytowanie tekst w formacie Unicode bufor tekstowy. Zasadniczo jest to widok co dotyczą większości użytkowników jako edytora. Ponieważ widok jest oddzielone z buforu różne warstwy tekstu (zawijanie wyrazów, konspektu tekstu i tak dalej), widoku nie może być dokładne reprezentacja tekstu w buforze. Aby uzyskać więcej informacji na temat widoku tekstu, zobacz [dostęp do widoku theText przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

 W poniższej tabeli przedstawiono interfejsów w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.

|Interface|Opis|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Włącza funkcję tworzenia działania złożonego (czyli akcje, które są grupowane w jednostce pojedynczego Cofnij/ponów).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Zawiera podstawowe metody do zarządzania i uzyskiwania dostępu do tego widoku. `IVsTextView` nie jest jednowątkowa bezpieczne.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Tworzy i zarządza okienka w oknie.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Współdziała z warstwami tekstu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Wykonuje operacje na widok z innego wątku.|

## <a name="see-also"></a>Zobacz także
- [Edytuj dane](https://www.microsoft.com/download/details.aspx?id=55984)
- [Obiekt VSTextBuffer](../extensibility/vstextbuffer-object.md)
- [Uzyskiwanie dostępu do widoku theText przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)