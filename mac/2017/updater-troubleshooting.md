---
title: Podczas pobierania informacji występują błędy aktualizatora
description: Instrukcje dotyczące sposobu naprawy w przypadku wyświetlenia błędu "błąd podczas pobierania informacji o aktualizacji". w programie Visual Studio 2017 dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 8825BBAD-65C0-480F-9868-A01E64F28250
ms.topic: troubleshooting
ms.openlocfilehash: c631bae40d06a000e2e90c26ae5a9862c1e09aaa
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950578"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Rozwiązywanie problemów: Podczas pobierania informacji występują błędy aktualizatora

W rzadkich przypadkach może zostać wyświetlony komunikat o błędzie "błąd podczas pobierania informacji o aktualizacji" wyświetlany podczas próby [zaktualizowania Visual Studio dla komputerów Mac](update.md). W takim przypadku spróbuj wykonać następujące czynności, aby rozwiązać ten problem:

- Sprawdź połączenie internetowe. To najczęstsze przyczyny tego błędu.
  - Jeśli pobranie składnika nie powiedzie się, możesz kliknąć przycisk Ponów próbę obok nazwy składnika, aby ponowić próbę pobrania.
- Uruchom ponownie IDE.
- Jeśli ten komunikat o błędzie będzie nadal wyświetlany, możesz również spróbować zaktualizować za pomocą Instalatora programu Visual Studio 2017 dla komputerów Mac, jeśli **dmg** jest nadal na maszynie lub można pobrać z witryny [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%20for%20Mac)
  - Instalator zaktualizuje wszystkie zainstalowane składniki na komputerze.
  - Po ponownym uruchomieniu Instalatora można także zainstalować brakujące składniki, które nie zostały wcześniej zainstalowane.
