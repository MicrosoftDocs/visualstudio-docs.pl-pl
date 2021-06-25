---
title: Widok VSTextView , | Microsoft Docs
description: Obiekt VSTextView to okno, które umożliwia użytkownikom wyświetlanie i edytowanie tekstu Unicode buforu tekstowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90fad54be26c11db31d649d0ae6b25c108a6b361
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905166"
---
# <a name="vstextview-object"></a>VSTextView, obiekt

Widok tekstowy to okno, które umożliwia użytkownikom wyświetlanie i edytowanie tekstu Unicode buforu tekstowego. Zasadniczo widok jest tym, co większość użytkowników odnosi się do edytora. Ponieważ widok jest oddzielony od buforu różnymi warstwami tekstu (zawijanie wyrazów, tekst wytyczania itp.), nie ma gwarancji, że widok będzie dokładną reprezentacją tekstu w buforze. Aby uzyskać więcej informacji na temat widoku tekstowego, zobacz Accessing theText view by using thelegacy API (Uzyskiwanie dostępu [do widoku tekstowego przy użyciu starszego interfejsu API).](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

W poniższej tabeli przedstawiono interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiekcie .

|Interfejs|Opis|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie złożonych akcji (czyli akcji pogrupowanych w jedną jednostkę cofania/ponownego tworzenia).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Udostępnia podstawowe metody zarządzania widokiem i uzyskiwania do niego dostępu. `IVsTextView` nie jest bezpieczny wątkami.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Tworzy okienko okna i zarządza tym okienkiem.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Współdziała z warstwami tekstu.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Wykonuje operacje w widoku z innego wątku.|

## <a name="see-also"></a>Zobacz też

- [Edycja figur](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer, obiekt](../extensibility/vstextbuffer-object.md)