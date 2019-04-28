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
ms.openlocfilehash: 4f9a4a873f2b6b3f41bd86d046bc187c17f063f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908738"
---
# <a name="services-provided-source-control-vspackage"></a>Świadczone usługi (pakiet VSPackage kontroli kodu źródłowego)
Podstawowy mechanizm, za pomocą którego funkcja jest udostępniana między pakietami VSPackage oraz między Visual Studio zintegrowane środowisko projektowe (IDE) i jego zainstalowanych pakietów VSPackage są usługi. Aby uzyskać szczegółowy opis usług i ich znaczenie w środowisku IDE programu Visual Studio, zobacz[Using i dostarczanie usług](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Usługi kontroli źródła
 Program Visual Studio oferuje dwie warstwy usług, usługi na poziomie środowiska IDE i usługi na poziomie pakietu. Środowiska IDE programu Visual Studio zapewnia natywnie usługi na poziomie środowiska IDE. Pakiet kontrolki źródła zużywa niektórych z tych usług. Pakiet kontroli źródła jako pakietu VSPackage udziałów jej funkcji kontroli źródła, zapewniając usługi kontroli źródła prywatne swój własny. Pakiet kontrolki źródła hermetyzuje zestaw powiązanych z kontroli źródła w interfejsy implementowane przez je w formie kontraktu, który może być używany przez program Visual Studio IDE.

## <a name="see-also"></a>Zobacz też
- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)