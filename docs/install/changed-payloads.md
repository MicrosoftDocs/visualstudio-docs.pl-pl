---
title: Gdy ładunki pakietów zmieniają się po wydaniu
description: Podczas tworzenia układu należy dowiedzieć się, jak ustalić, czy ładunki pakietów uległy zmianie po wydaniu wersji.
ms.date: 05/22/2019
ms.topic: how-to
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e773ddf85df1d7f71b1ed929b8f942a5f3b36421
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295300"
---
# <a name="package-payload-changes"></a>Zmiany ładunku pakietu

Niektóre ładunki pakietów mogą ulec zmianie po wydaniu wersji. Gdy ty lub ktoś inny utworzy układ, to zachowanie może spowodować powstanie innej zawartości układu w zależności od tego, kiedy układ został utworzony.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Sprawdź, czy układ obejmuje zmiany ładunku pakietu

Oto jak ustalić, czy utworzony wcześniej układ uzyskał ładunki pakietów, które zostały zmodyfikowane po wydaniu wydania:

1. Otwórz dziennik instalacji. Dziennik zazwyczaj ma miejsce, `%TEMP%\dd_setup_[date].log` `[date]` gdy operacja układu została rozpoczęta w `yyyyMMddHHmmss` formacie.

2. Wyszukaj wiersz w dzienniku, który jest taki sam jak poniższy tekst:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Następnie poszukaj wierszy w dalszej części dziennika, co oznacza, że pobieranie powiodło się dla elementu [path]. Mogą wyglądać podobnie do następującego tekstu:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Zobacz też

* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizowanie instalacji opartej na sieci w programie Visual Studio](update-a-network-installation-of-visual-studio.md)
