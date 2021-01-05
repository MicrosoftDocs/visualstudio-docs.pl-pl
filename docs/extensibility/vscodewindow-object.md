---
title: Obiekt VSCodeWindow | Microsoft Docs
description: Zapoznaj się z oknami kodu, które są wyspecjalizowanymi oknami dokumentów, które mogą zawierać jeden lub więcej widoków tekstu, zazwyczaj obiekt VsTextView.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a778cde66bc85a6f3cd8a13b5f2bb6fdb41844de
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864008"
---
# <a name="vscodewindow-object"></a>Obiekt VSCodeWindow
Okno kodu to wyspecjalizowane okno dokumentu, które może zawierać co najmniej jeden widok tekstowy, zazwyczaj ten <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiekt.

 W sposób architektoniczny okno kod jest oknem dokumentu, które znajduje się w obrębie ramki okna. Funkcjonalnie okno kod jest po prostu oknem dokumentu z dodatkowymi funkcjami. W trybie interfejsu wielu dokumentów (MDI) okno kod jest ramką podrzędną MDI. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodu w systemie Windows przy użyciu starszego interfejsu API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

 Poniższa tabela zawiera interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiekcie.

|Metoda|Opis|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Zapewnia ogólny mechanizm dostępu do lokalizowania usługi, która identyfikuje globalnie unikatowy identyfikator (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Reprezentuje element podrzędny interfejsu wielu dokumentów (MDI) zawierający co najmniej jeden widok kodu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Wypełnia ramkę okna.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edycja ilustracji](https://www.microsoft.com/download/details.aspx?id=55984)