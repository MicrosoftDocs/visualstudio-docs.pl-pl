---
title: Aktualizator zawiera błędy podczas pobierania informacji
description: Instrukcje dotyczące sposobu naprawy w przypadku wyświetlenia błędu "błąd podczas pobierania informacji o aktualizacji". w programie Visual Studio 2019 dla komputerów Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75405477"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Rozwiązywanie problemów: Aktualizator zawiera błędy podczas pobierania informacji

W rzadkich przypadkach może zostać wyświetlony komunikat o błędzie "błąd podczas pobierania informacji o aktualizacji" wyświetlany podczas próby [zaktualizowania Visual Studio dla komputerów Mac](update.md). W takim przypadku spróbuj wykonać następujące czynności, aby rozwiązać ten problem:

- Sprawdź połączenie internetowe. To najczęstsze przyczyny tego błędu.
  - Jeśli pobranie składnika nie powiedzie się, możesz kliknąć przycisk Ponów próbę obok nazwy składnika, aby ponowić próbę pobrania.
- Uruchom ponownie IDE.
- Jeśli ten komunikat o błędzie będzie nadal wyświetlany, możesz również spróbować zaktualizować za pomocą Instalatora, jeśli **dmg** jest nadal na komputerze lub można go pobrać z witryny [VisualStudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - Instalator zaktualizuje wszystkie zainstalowane składniki na komputerze.
  - Po ponownym uruchomieniu Instalatora można także zainstalować brakujące składniki, które nie zostały wcześniej zainstalowane.
- Możesz również spróbować wyczyścić buforowane pliki do pobrania, usuwając plik znajdujący się w `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`.
- W przypadku korzystania ze starszej wersji programu Visual Studio dla komputerów Mac w katalogu `VisualStudio` mogą znajdować się inne numery wersji. Usuń również plik `index.xml` w tych ścieżkach.
