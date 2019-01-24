---
title: Automatyzacja konfiguracji i obiektów SelectedItem | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777856"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatyzacja konfiguracji i obiektów SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Można zautomatyzować kompilacji i procesy wybranego elementu w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="automation-for-builds"></a>Automatyzacja kompilacji  
 Kompilacji lub konfiguracji ma modelu automatyzacji, który znajduje się podczas implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Aby uzyskać więcej informacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../../ide/understanding-build-configurations.md).  
  
 Jeśli utworzysz pakietu VSPackage i chcesz określić opcje konfiguracji, należy użyć modelu automatyzacji.  
  
## <a name="automation-for-selecteditem"></a>Automatyzacja SelectedItem  
 Nie trzeba dostarczyć implementację `SelectedItem` obiektu, ponieważ program Visual Studio zawiera standardowej implementacji. Jednakże, można zaimplementować `SelectedItem` obiektu, jeśli wolisz. Musisz zaimplementować obiekt, który zawiera `SelectedItem` interfejs i zwraca odpowiedź do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody z VSITEMID ustawienie <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Współtworzenie modelu automatyzacji](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Ogólne informacje o konfiguracjach kompilacji](../../ide/understanding-build-configurations.md)
