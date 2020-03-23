---
title: Gdy ładunki pakietów zmieniają się po wydaniu
description: Podczas tworzenia układu, dowiedz się, jak ustalić, czy ładunki pakietów zmienione po wydaniu już wysłane.
ms.date: 05/22/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dec1478314e752ddace8fae822747e7c8e328b70
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114585"
---
# <a name="package-payload-changes"></a>Zmiany ładunku pakietu

Niektóre ładunki pakietów mogą ulec zmianie po wydaniu. Gdy ty lub inna osoba tworzy układ, to zachowanie może spowodować inną zawartość układu, w zależności od tego, kiedy układ został utworzony.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Sprawdź, czy układ zawiera zmiany ładunku pakietu

Oto jak ustalić, czy układ, który został wcześniej utworzony nabył ładunki pakietu, które zostały zmodyfikowane po wydaniu wydania:

1. Otwórz dziennik konfiguracji. Dziennik jest zazwyczaj `%TEMP%\dd_setup_[date].log` w `[date]` miejscu, gdzie jest, gdy operacja układu rozpoczęła się w `yyyyMMddHHmmss` formacie.

2. Poszukaj wiersza w dzienniku, który jest skonstruowany w następujący sposób:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Następnie poszukaj wierszy w dalszej części dziennika, które wskazują, że pobieranie zakończyło się pomyślnie dla [ścieżki]. Mogą one wyglądać podobnie do następującego tekstu:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Zobacz też

* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizowanie instalacji programu Visual Studio opartej na sieci](update-a-network-installation-of-visual-studio.md)
