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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36b7e0e6806f88efe373dffa3f21ba79baefb281
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189054"
---
# <a name="vscodewindow-object"></a>Obiekt VSCodeWindow
Okno kodu to wyspecjalizowane okno dokumentu, które może zawierać jeden lub więcej widoków tekstu, zazwyczaj obiekt <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 W sposób architektoniczny okno kod jest oknem dokumentu, które znajduje się w obrębie ramki okna. Funkcjonalnie okno kod jest po prostu oknem dokumentu z dodatkowymi funkcjami. W trybie interfejsu wielu dokumentów (MDI) okno kod jest ramką podrzędną MDI. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodu w systemie Windows przy użyciu starszego interfejsu API](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 Poniższa tabela zawiera interfejsy w obiekcie <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>.

|Metoda|Opis|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Zapewnia ogólny mechanizm dostępu do lokalizowania usługi, która identyfikuje globalnie unikatowy identyfikator (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Reprezentuje element podrzędny interfejsu wielu dokumentów (MDI) zawierający co najmniej jeden widok kodu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Wypełnia ramkę okna.|

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edycja ilustracji](https://www.microsoft.com/download/details.aspx?id=55984)