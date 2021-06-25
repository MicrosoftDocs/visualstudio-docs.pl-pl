---
title: Automatyzacja konfiguracji i obiektów SelectedItem | Microsoft Docs
description: Dowiedz się, jak zautomatyzować procesy kompilacji Visual Studio elementów przy użyciu obiektów Configuration i SelectedItem w interopie powłoki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a95fc06c5d84a936cdb1ada3369f584381dfe7f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901633"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatyzacja obiektów Configuration i SelectedItem

Procesy kompilacji i wybranych elementów można zautomatyzować w Visual Studio.

## <a name="automation-for-builds"></a>Automatyzacja kompilacji

Kompilacja lub konfiguracja ma model automatyzacji, który jest dostarczany podczas wdrażania <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> programu . Aby uzyskać więcej informacji, zobacz [Understand build configurations (Opis konfiguracji kompilacji).](../../ide/understanding-build-configurations.md)

Jeśli tworzysz pakiet VSPackage i chcesz kontrolować opcje konfiguracji, musisz użyć modelu automatyzacji.

## <a name="automation-for-selecteditem"></a>Automatyzacja dla SelectedItem

Nie trzeba dostarczać implementacji dla obiektu, ponieważ Visual Studio `SelectedItem` zawiera standardową implementację. Jeśli jednak wolisz, `SelectedItem` możesz zaimplementować obiekt . Należy zaimplementować obiekt zawierający interfejs i zwrócić odpowiedź na wywołanie metody z ustawionym na `SelectedItem` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> `VSITEMID` [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Współtworowanie modelu automatyzacji](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md)
