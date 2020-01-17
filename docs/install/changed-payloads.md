---
title: Gdy ładunki pakietów zmieniają się po wydaniu
description: Podczas tworzenia układu należy dowiedzieć się, jak ustalić, czy ładunki pakietów uległy zmianie po wydaniu wersji.
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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114585"
---
# <a name="package-payload-changes"></a>Zmiany ładunku pakietu

Niektóre ładunki pakietów mogą ulec zmianie po wydaniu wersji. Gdy ty lub ktoś inny utworzy układ, to zachowanie może spowodować powstanie innej zawartości układu w zależności od tego, kiedy układ został utworzony.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Sprawdź, czy układ obejmuje zmiany ładunku pakietu

Oto jak ustalić, czy utworzony wcześniej układ uzyskał ładunki pakietów, które zostały zmodyfikowane po wydaniu wydania:

1. Otwórz dziennik instalacji. Dziennik jest zwykle w `%TEMP%\dd_setup_[date].log` gdzie `[date]` jest w momencie rozpoczęcia operacji układu w `yyyyMMddHHmmss` formacie.

2. Wyszukaj wiersz w dzienniku, który jest taki sam jak poniższy tekst:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Następnie poszukaj wierszy w dalszej części dziennika, co oznacza, że pobieranie powiodło się dla elementu [path]. Mogą wyglądać podobnie do następującego tekstu:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Zobacz także

* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizowanie instalacji opartej na sieci, programu Visual Studio](update-a-network-installation-of-visual-studio.md)
