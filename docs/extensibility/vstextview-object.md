---
title: Obiekt VSTextView | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697710"
---
# <a name="vstextview-object"></a>Obiekt VSTextView

Widok tekstu jest oknem, które umożliwia użytkownikom wyświetlanie i edytowanie tekstu Unicode buforu tekstowego. Zasadniczo widok jest tym, co większość użytkowników określa jako edytor. Ponieważ widok jest oddzielony od bufora różnymi warstwami tekstu (zawijanie wyrazów, tworzenie tekstu i tak dalej), widok nie jest gwarantowany jako dokładna reprezentacja tekstu w buforze. Aby uzyskać więcej informacji na temat widoku tekstu, zobacz [Uzyskiwanie dostępu do widoku Tekst przy użyciu starszego interfejsu API](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

W poniższej tabeli przedstawiono interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiekcie.

|Interface|Opis|
|---------------|-----------------|
|[Źródło IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardowy interfejs OLE.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie akcji złożonych (czyli akcji zgrupowanych w pojedynczą jednostkę cofania/ponawiania).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Zawiera podstawowe metody zarządzania i uzyskiwania do niego dostępu. `IVsTextView`nie jest bezpieczny gwintowany.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Tworzy okienko okna i zarządza nim.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Współdziała z warstwami tekstowymi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Wykonuje operacje w widoku z innego wątku.|

## <a name="see-also"></a>Zobacz też

- [Edytuj rysunki](https://www.microsoft.com/download/details.aspx?id=55984)
- [OBIEKT VSTextBuffer](../extensibility/vstextbuffer-object.md)
