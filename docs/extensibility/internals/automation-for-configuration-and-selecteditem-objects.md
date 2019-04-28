---
title: Automatyzacja konfiguracji i obiektów SelectedItem | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ee4bcddd7c23f5178984c2c76b059209a965956
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910636"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatyzacja obiektów konfiguracji i SelectedItem

Można zautomatyzować, kompilacji i procesy wybranego elementu w programie Visual Studio.

## <a name="automation-for-builds"></a>Automatyzacja kompilacji

Kompilacji lub konfiguracji ma modelu automatyzacji, który znajduje się podczas implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Aby uzyskać więcej informacji, zobacz [konfiguracje kompilacji omówienie](../../ide/understanding-build-configurations.md).

Jeśli utworzysz pakietu VSPackage i chcesz określić opcje konfiguracji, należy użyć modelu automatyzacji.

## <a name="automation-for-selecteditem"></a>Automatyzacja SelectedItem

Nie trzeba dostarczyć implementację `SelectedItem` obiektu, ponieważ program Visual Studio zawiera standardowej implementacji. Jednakże, można zaimplementować `SelectedItem` obiektu, jeśli wolisz. Musisz zaimplementować obiekt, który zawiera `SelectedItem` interfejs i zwraca odpowiedź do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody z `VSITEMID` równa [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Współtworzenie modelu automatyzacji](../../extensibility/internals/contributing-to-the-automation-model.md)
- [O konfiguracjach kompilacji](../../ide/understanding-build-configurations.md)