---
title: Rejestrowanie pakietów VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 426adc0cd150d5867760a8570df5777fec8260a2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601580"
---
# <a name="registering-vspackages"></a>Rejestrowanie pakietów VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opiera się na plikach pkgdef do opisywania i zlokalizować pakietu VSPackage. Plik .pkgdef zawiera wszystkich informacji rejestracyjnych które w przeciwnym razie zostaną dodane do rejestru systemowego. Zarządzane pakietów VSPackage są rejestrowane przez dodawanie atrybutów do kodu źródłowego, a następnie uruchamiając [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) w zestawie wynikowym, aby wygenerować plik .pkgdef.

## <a name="in-this-section"></a>W tej sekcji
- [Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Opisuje ścieżkę ładowanie pakietów VSPackage.

- [Rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Wyjaśnia, jak zarejestrować pakietu VSPackage.
