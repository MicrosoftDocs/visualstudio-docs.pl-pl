---
title: Rejestracja pakietów VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705742"
---
# <a name="registering-vspackages"></a>Rejestrowanie pakietów VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]opiera się na plikach pkgdef do opisania i zlokalizowania vspackage. Plik pkgdef zawiera wszystkie informacje rejestracyjne, które w przeciwnym razie zostałyby dodane do rejestru systemowego. Zarządzane pakiety VSPackages są rejestrowane przez dodanie atrybutów do kodu źródłowego, a następnie uruchomienie [CreatePkgDef Utility](../../extensibility/internals/createpkgdef-utility.md) w wynikowym zestawie do generowania pliku pkgdef.

## <a name="in-this-section"></a>W tej sekcji
- [Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Opisuje ścieżkę ładowania dla vspackages.

- [Rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 W tym artykule wyjaśniono, jak zarejestrować vspackage.
