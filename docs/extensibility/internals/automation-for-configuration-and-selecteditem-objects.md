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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f6e7f153e7d5b32e54cc51e3b7af06f14545cea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086264"
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
