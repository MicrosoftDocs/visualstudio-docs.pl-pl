---
title: VSCodeWindow Object | Microsoft Docs
description: Dowiedz się więcej o oknach kodu, które są wyspecjalizowanymi oknami dokumentów, które mogą zawierać co najmniej jeden widok tekstowy, zazwyczaj obiekt VsTextView.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9803132605ee81c67785c8c0154861b26730ca5f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905335"
---
# <a name="vscodewindow-object"></a>VSCodeWindow, obiekt
Okno kodu to wyspecjalizowane okno dokumentu, które może zawierać co najmniej jeden widok tekstu, zazwyczaj <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiekt .

 W architekturze okno kodu jest oknem dokumentu, które znajduje się w ramce okna. Funkcjonalnie okno kodu jest po prostu oknem dokumentu z dodatkowymi funkcjami. W trybie interfejsu wielu dokumentów (MDI) okno kodu jest ramką podrzędną MDI. Aby uzyskać więcej informacji, zobacz [Dostosowywanie okien kodu przy użyciu starszego interfejsu API.](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

 W poniższej tabeli przedstawiono interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiekcie .

|Metoda|Opis|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Udostępnia ogólny mechanizm dostępu do lokalizowania usługi, która identyfikuje unikatowy identyfikator globalny (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Reprezentuje podrzędny interfejs wielu dokumentów (MDI) zawierający co najmniej jeden widok kodu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Wypełnia ramkę okna.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edycja figur](https://www.microsoft.com/download/details.aspx?id=55984)