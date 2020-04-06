---
title: Automatyzacja konfiguracji i wybranych obiektówitem | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709972"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatyzacja dla obiektów konfiguracji i selecteditem

Można zautomatyzować procesy kompilacji i wybranego elementu w programie Visual Studio.

## <a name="automation-for-builds"></a>Automatyzacja kompilacji

Kompilacja lub konfiguracja ma model automatyzacji, który jest dostarczany podczas implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Aby uzyskać więcej informacji, zobacz [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md).

Jeśli tworzysz VSPackage i chcesz kontrolować opcje konfiguracji, należy użyć modelu automatyzacji.

## <a name="automation-for-selecteditem"></a>Automatyzacja dla selectedItem

Nie trzeba podać implementacji dla `SelectedItem` obiektu, ponieważ visual studio zawiera standardową implementację. Jednak można zaimplementować obiekt, `SelectedItem` jeśli wolisz. Należy zaimplementować `SelectedItem` obiekt, który zawiera interfejs i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> zwrócić `VSITEMID` odpowiedź na wywołanie metody z zestawem [do __VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Współtworzenie modelu automatyzacji](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md)
