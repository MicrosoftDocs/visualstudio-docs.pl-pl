---
title: Obiekt VSCodeWindow | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697959"
---
# <a name="vscodewindow-object"></a>Obiekt VSCodeWindow
Okno kodu to okno dokumentu specjalistycznego, które może zawierać <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> jeden lub więcej widoków tekstu, zwykle obiektu.

 Architektonicznie okno kodu jest oknem dokumentu, które znajduje się w ramce okna. Funkcjonalnie okno kodu jest po prostu okno dokumentu z dodatkowymi funkcjami. W trybie interfejsu wielu dokumentów (MDI) okno kodu jest ramką podrzędną MDI. Aby uzyskać więcej informacji, zobacz [Dostosowywanie okien kodu przy użyciu starszego interfejsu API](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 Poniższa tabela zawiera interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiekcie.

|Metoda|Opis|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Udostępnia ogólny mechanizm dostępu do lokalizowania usługi, która identyfikuje globalnie unikatowy identyfikator (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Reprezentuje wiele wiązeku interfejsu dokumentu (MDI) podrzędnego zawierającego jeden lub więcej widoków kodu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Wypełnia ramkę okna.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edytuj rysunki](https://www.microsoft.com/download/details.aspx?id=55984)
