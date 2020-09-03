---
title: Udostępnione usługi (pakietu VSPackage kontroli źródła) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 750710cdc381573f8aa6fd064e1fc980030cf359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202709"
---
# <a name="services-provided-source-control-vspackage"></a>Świadczone usługi (pakiet VSPackage kontroli kodu źródłowego)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługi są podstawowym mechanizmem, za pomocą którego funkcje są współużytkowane przez pakietów VSPackage oraz między zintegrowanym środowiskiem programistycznym (IDE) programu Visual Studio i zainstalowaną pakietów VSPackage. Aby uzyskać szczegółowy opis usług i ich znaczenie w środowisku IDE programu Visual Studio, zobacz[Używanie i świadczenie usług](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Usługa kontroli źródła  
 Program Visual Studio oferuje dwie warstwy usług, usług na poziomie IDE i usług na poziomie pakietu. Środowisko IDE programu Visual Studio natywnie zapewnia usługi na poziomie IDE. Pakiet kontroli źródła zużywa niektóre z tych usług. Pakiet kontroli źródła jako pakietu VSPackage udostępnia swoją funkcję kontroli źródła, zapewniając własną prywatną usługę kontroli źródła. Pakiet kontroli źródła hermetyzuje zestaw interfejsów związanych z kontrolą źródła wdrożonych przez nią w formie kontraktu, który może być używany przez środowisko IDE programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
