---
title: Aktualizator ma błędy podczas pobierania informacji
description: Instrukcje dotyczące sposobu rozwiązania, gdy zostanie wyświetlony błąd "Błąd podczas pobierania informacji o aktualizacji". in Visual Studio 2019 for Mac
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2b89ea7155b27f9c5b54dae38d4e823895fad705
ms.sourcegitcommit: 847d192013eb8225776243045c9b5a53d1ba4a59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2019
ms.locfileid: "59586368"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Rozwiązywanie problemów: Aktualizator ma błędy podczas pobierania informacji

W rzadkich przypadkach, może zostać wyświetlony błąd komunikat "błąd podczas pobierania zaktualizować informacje o" wyświetlany podczas próby [zaktualizować program Visual Studio dla komputerów Mac](update.md). Jeśli tak się stanie, spróbuj wykonać następujące kroki, aby rozwiązać ten problem:

- Sprawdź połączenie internetowe. Spadek połączenia jest Najczęstszą przyczyną tego błędu.
    - Składnik nie uda się pobrać, po kliknięciu przycisku ponów obok nazwy składnika, aby ponownie spróbować pobrać pliki.
- Uruchom ponownie środowisko IDE.
- Jeśli będziesz kontynuować wyświetlić ten komunikat o błędzie, możesz również spróbować zaktualizować za pomocą Instalatora programu, jeśli **dmg** nadal znajduje się na komputerze, lub możesz ją pobrać z [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
    - Instalator zaktualizuje wszystkie zainstalowane składniki na swojej maszynie.
    - Uruchamiając ponownie Instalatora, będziesz również mieć możliwość zainstalowanie brakujących składników, które nie było wcześniej zainstalowane.