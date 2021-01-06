---
title: Udostępnione usługi (pakietu VSPackage kontroli źródła) | Microsoft Docs
description: Dowiedz się, w jaki sposób pakietów VSPackage udostępniać funkcje za pomocą usług, w tym współpracy ze środowiskiem IDE programu Visual Studio i jej pakietów VSPackage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4a97ed69d37330132196f0334f5684c0704c5fd2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876080"
---
# <a name="services-provided-source-control-vspackage"></a>Świadczone usługi (pakiet VSPackage kontroli kodu źródłowego)
Usługi są podstawowym mechanizmem, za pomocą którego funkcje są współużytkowane przez pakietów VSPackage oraz między zintegrowanym środowiskiem programistycznym (IDE) programu Visual Studio i zainstalowaną pakietów VSPackage. Aby uzyskać szczegółowy opis usług i ich znaczenie w środowisku IDE programu Visual Studio, zobacz[Używanie i świadczenie usług](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Usługa kontroli źródła
 Program Visual Studio oferuje dwie warstwy usług, usług na poziomie IDE i usług na poziomie pakietu. Środowisko IDE programu Visual Studio natywnie zapewnia usługi na poziomie IDE. Pakiet kontroli źródła zużywa niektóre z tych usług. Pakiet kontroli źródła jako pakietu VSPackage udostępnia swoją funkcję kontroli źródła, zapewniając własną prywatną usługę kontroli źródła. Pakiet kontroli źródła hermetyzuje zestaw interfejsów związanych z kontrolą źródła wdrożonych przez nią w formie kontraktu, który może być używany przez środowisko IDE programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
