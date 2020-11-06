---
title: Obiekt VSCodeWindow | Microsoft Docs
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
ms.openlocfilehash: 5d2cdbe12146dd5d3010b9bf8ffcdd130a0ea4bb
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414363"
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