---
title: Usługi świadczone (pakiet VSPackage kontroli) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f94efff27ea45dc070e34f26d85be4bd7ff5b50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936908"
---
# <a name="services-provided-source-control-vspackage"></a>Świadczone usługi (pakiet VSPackage kontroli kodu źródłowego)
Podstawowy mechanizm, za pomocą którego funkcja jest udostępniana między pakietami VSPackage oraz między Visual Studio zintegrowane środowisko projektowe (IDE) i jego zainstalowanych pakietów VSPackage są usługi. Aby uzyskać szczegółowy opis usług i ich znaczenie w środowisku IDE programu Visual Studio, zobacz[Using i dostarczanie usług](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Usługi kontroli źródła  
 Program Visual Studio oferuje dwie warstwy usług, usługi na poziomie środowiska IDE i usługi na poziomie pakietu. Środowiska IDE programu Visual Studio zapewnia natywnie usługi na poziomie środowiska IDE. Pakiet kontrolki źródła zużywa niektórych z tych usług. Pakiet kontroli źródła jako pakietu VSPackage udziałów jej funkcji kontroli źródła, zapewniając usługi kontroli źródła prywatne swój własny. Pakiet kontrolki źródła hermetyzuje zestaw powiązanych z kontroli źródła w interfejsy implementowane przez je w formie kontraktu, który może być używany przez program Visual Studio IDE.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)