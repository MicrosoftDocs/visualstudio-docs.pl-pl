---
title: Aktualizator zawiera błędy podczas pobierania informacji
description: Instrukcje dotyczące sposobu naprawy w przypadku wyświetlenia błędu "błąd podczas pobierania informacji o aktualizacji". w programie Visual Studio 2019 dla komputerów Mac
ms.topic: troubleshooting
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 5ba295defe19c6f3c6c56d5bccc7cc3fa367bb50
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107794"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Rozwiązywanie problemów: Aktualizator zawiera błędy podczas pobierania informacji

W rzadkich przypadkach może zostać wyświetlony komunikat o błędzie "błąd podczas pobierania informacji o aktualizacji" wyświetlany podczas próby [zaktualizowania Visual Studio dla komputerów Mac](update.md). W takim przypadku spróbuj wykonać następujące czynności, aby rozwiązać ten problem:

- Sprawdź połączenie internetowe. To najczęstsze przyczyny tego błędu.
  - Jeśli pobranie składnika nie powiedzie się, możesz kliknąć przycisk Ponów próbę obok nazwy składnika, aby ponowić próbę pobrania.
- Uruchom ponownie IDE.
- Jeśli ten komunikat o błędzie będzie nadal wyświetlany, możesz również spróbować zaktualizować za pomocą Instalatora, jeśli **dmg** jest nadal na komputerze lub można go pobrać z witryny [VisualStudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - Instalator zaktualizuje wszystkie zainstalowane składniki na komputerze.
  - Po ponownym uruchomieniu Instalatora można także zainstalować brakujące składniki, które nie zostały wcześniej zainstalowane.
- Możesz również spróbować wyczyścić buforowane pliki do pobrania, usuwając plik znajdujący się w `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml`lokalizacji.
