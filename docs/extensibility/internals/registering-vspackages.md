---
title: Rejestrowanie pakietów VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ac51f23132d855c3da921cc2743c3064a353524
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331318"
---
# <a name="registering-vspackages"></a>Rejestrowanie pakietów VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opiera się na plikach pkgdef do opisywania i zlokalizować pakietu VSPackage. Plik .pkgdef zawiera wszystkich informacji rejestracyjnych które w przeciwnym razie zostaną dodane do rejestru systemowego. Zarządzane pakietów VSPackage są rejestrowane przez dodawanie atrybutów do kodu źródłowego, a następnie uruchamiając [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) w zestawie wynikowym, aby wygenerować plik .pkgdef.

## <a name="in-this-section"></a>W tej sekcji
- [Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Opisuje ścieżkę ładowanie pakietów VSPackage.

- [Rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Wyjaśnia, jak zarejestrować pakietu VSPackage.
