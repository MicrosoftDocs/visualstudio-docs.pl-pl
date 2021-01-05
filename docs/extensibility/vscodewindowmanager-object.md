---
title: Obiekt VSCodeWindowManager | Microsoft Docs
description: Zapoznaj się z obiektem VSCodeWindowManager, który jest odpowiedzialny za zarządzanie zakończeniami, na przykład pasek listy rozwijanej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5c602a1cf46382e5a8b5c688501b2406e4a6d0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863991"
---
# <a name="vscodewindowmanager-object"></a>Obiekt VSCodeWindowManager

Usługa językowa implementuje Menedżera okien kodu i jest odpowiedzialna za zarządzanie zakończeniami (na przykład pasek listy rozwijanej). Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodu w systemie Windows przy użyciu starszego interfejsu API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

W poniższej tabeli przedstawiono interfejsy w `VSCodeWindowManager` obiekcie.

|Interfejs|Opis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Zezwala na dodawanie, a także do usuwania z okna kodu lub usuwanie z niego.|