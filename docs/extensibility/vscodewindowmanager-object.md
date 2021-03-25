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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 60093d237ed2aa7a14e5695efc66fe8edd515f4a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062398"
---
# <a name="vscodewindowmanager-object"></a>Obiekt VSCodeWindowManager

Usługa językowa implementuje Menedżera okien kodu i jest odpowiedzialna za zarządzanie zakończeniami (na przykład pasek listy rozwijanej). Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodu w systemie Windows przy użyciu starszego interfejsu API](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

W poniższej tabeli przedstawiono interfejsy w `VSCodeWindowManager` obiekcie.

|Interfejs|Opis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Zezwala na dodawanie, a także do usuwania z okna kodu lub usuwanie z niego.|