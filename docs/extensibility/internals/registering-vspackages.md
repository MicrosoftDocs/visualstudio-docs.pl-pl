---
title: Rejestrowanie pakietów VSPackage | Microsoft Docs
description: Plik. pkgdef zawiera informacje, które w przeciwnym razie byłyby dodawane do rejestru systemowego. Dowiedz się, jak program Visual Studio używa plików. pkgdef do opisywania/lokalizowania pakietu VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 111debccd1623901790c83e743469327ffdd667e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905832"
---
# <a name="registering-vspackages"></a>Rejestrowanie pakietów VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opiera się na plikach. pkgdef do opisywania i lokalizowania pakietu VSPackage. Plik. pkgdef zawiera wszystkie informacje rejestracyjne, które w przeciwnym razie byłyby dodawane do rejestru systemowego. Zarządzane pakietów VSPackage są rejestrowane przez dodanie atrybutów do kodu źródłowego, a następnie uruchomienie [Narzędzia CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) na zestawie danych wyjściowych w celu wygenerowania pliku. pkgdef.

## <a name="in-this-section"></a>W tej sekcji
- [Określanie lokalizacji pliku pakietu VSPackage dla powłoki VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Opisuje ścieżkę ładowania dla pakietów VSPackage.

- [Rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md)

 Wyjaśnia, jak zarejestrować pakietu VSPackage.
