---
title: Świadczone usługi (Kontrola źródła VSPackage) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705408"
---
# <a name="services-provided-source-control-vspackage"></a>Świadczone usługi (pakiet VSPackage kontroli kodu źródłowego)
Usługi są podstawowym mechanizmem, za pomocą którego funkcje są współużytkowane przez VSPackages i między zintegrowanym środowiskiem programistycznym Visual Studio (IDE) i jego zainstalowanymi pakietami VSPackage. Aby uzyskać szczegółowy opis usług i ich znaczenie w ide programu Visual Studio, zobacz[Korzystanie z usług i dostarczanie usług](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Usługa kontroli źródła
 Visual Studio udostępnia dwie warstwy usług, usługi na poziomie IDE i usługi na poziomie pakietu. Ide programu Visual Studio natywnie zapewnia usługi na poziomie IDE. Pakiet kontroli źródła zużywa niektóre z tych usług. Pakiet kontroli źródła jako VSPackage współużytkuje swoją funkcję kontroli źródła, zapewniając własną usługę kontroli źródła prywatnego. Pakiet kontroli źródła hermetyzuje zestaw interfejsów związanych z kontrolą źródła zaimplementowanych przez niego w postaci kontraktu, który może być używany przez IDE programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
