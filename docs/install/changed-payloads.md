---
title: Gdy pakiet ładunków zmienia się po wydania
description: Podczas tworzenia układu, Dowiedz się, jak ustalić, czy pakiet ładunków zmieniony po wydaniu już zostało wysłane.
ms.date: 05/22/2019
ms.topic: conceptual
author: et13
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6a4eb286344b6dce7a4814089db013965eb34c98
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66411160"
---
# <a name="package-payload-changes"></a>Zmiany do ładunku pakietu

Niektóre ładunków pakietu mogą zmieniać po wydaniu już zostało wysłane. Gdy Ty lub inna osoba tworzy układu, to zachowanie może prowadzić do zawartości innego układu, w zależności od utworzenia układu.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Sprawdź, że układ zawiera zmiany do ładunku pakietu

Oto jak określić, jeśli układ, który został wcześniej utworzony uzyskał ładunków pakietu, które zostały zmodyfikowane po wydaniu wersji:

1. Otwórz dziennik instalacji. Dziennik jest zwykle w `%TEMP%\dd_setup_[date].log` gdzie `[date]` jest w przypadku operacji układu pracę w `yyyyMMddHHmmss` formatu.

2. Zwróć uwagę na wiersz w dzienniku, które są skonstruowane, podobnie jak następujący tekst:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Następnie poszukaj wiersze później w dzienniku, które wskazują, że pobieranie zakończyło się pomyślnie [ścieżka]. Może wyglądać podobnie do następującego tekstu:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Zobacz także

* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizowanie instalacji opartej na sieci, programu Visual Studio](update-a-network-installation-of-visual-studio.md)