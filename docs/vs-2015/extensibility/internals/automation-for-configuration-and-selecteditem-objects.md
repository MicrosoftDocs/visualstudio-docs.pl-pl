---
title: Automatyzacja konfiguracji i obiektów SelectedItem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 612916da7922900a1054d785dad86ed448aa1f12
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733470"
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

