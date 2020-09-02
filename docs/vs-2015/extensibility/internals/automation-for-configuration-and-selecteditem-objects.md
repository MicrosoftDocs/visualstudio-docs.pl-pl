---
title: Automatyzacja w zakresie konfiguracji i SelectedItem obiektów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157259"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatyzacja konfiguracji i obiektów SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W programie można zautomatyzować procesy kompilacji i wybranego elementu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Automatyzacja kompilacji  
 Kompilacja lub konfiguracja ma model automatyzacji, który jest dostarczany podczas wdrażania <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Aby uzyskać więcej informacji, zobacz [Omówienie konfiguracji kompilacji](../../ide/understanding-build-configurations.md).  
  
 Jeśli utworzysz pakietu VSPackage i chcesz kontrolować opcje konfiguracji, musisz użyć modelu automatyzacji.  
  
## <a name="automation-for-selecteditem"></a>Automatyzacja dla SelectedItem  
 Nie musisz podawać implementacji dla tego `SelectedItem` obiektu, ponieważ program Visual Studio zawiera standardową implementację. Można jednak zaimplementować `SelectedItem` obiekt, jeśli wolisz. Należy zaimplementować obiekt, który zawiera `SelectedItem` interfejs i zwrócić odpowiedź do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody z VSITEMID ustawioną na <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Współtworzenie modelu automatyzacji](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Informacje o konfiguracjach kompilacji](../../ide/understanding-build-configurations.md)
