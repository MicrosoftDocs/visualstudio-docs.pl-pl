---
title: Automatyzacja w zakresie konfiguracji i SelectedItem obiektów | Microsoft Docs
description: Dowiedz się, jak zautomatyzować procesy kompilacji i wybranych elementów programu Visual Studio przy użyciu obiektów Configuration i SelectedItem w elemencie Interop Shell.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a1316115ca3ebbd0f78249d1a73310fc06de688
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906078"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatyzacja dla obiektów Configuration i SelectedItem

Można zautomatyzować procesy kompilowania i wybranego elementu w programie Visual Studio.

## <a name="automation-for-builds"></a>Automatyzacja kompilacji

Kompilacja lub konfiguracja ma model automatyzacji, który jest dostarczany podczas wdrażania <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../../ide/understanding-build-configurations.md).

Jeśli utworzysz pakietu VSPackage i chcesz kontrolować opcje konfiguracji, musisz użyć modelu automatyzacji.

## <a name="automation-for-selecteditem"></a>Automatyzacja dla SelectedItem

Nie musisz podawać implementacji dla tego `SelectedItem` obiektu, ponieważ program Visual Studio zawiera standardową implementację. Można jednak zaimplementować `SelectedItem` obiekt, jeśli wolisz. Należy zaimplementować obiekt, który zawiera `SelectedItem` interfejs i zwrócić odpowiedź na wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody z `VSITEMID` ustawionym na [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Współtworzenie modelu automatyzacji](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md)
