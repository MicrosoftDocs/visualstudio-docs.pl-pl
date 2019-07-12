---
title: Aktualizator ma błędy podczas pobierania informacji
description: Instrukcje dotyczące sposobu rozwiązania, gdy zostanie wyświetlony błąd "Błąd podczas pobierania informacji o aktualizacji". in Visual Studio 2017 for Mac
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 8825BBAD-65C0-480F-9868-A01E64F28250
ms.openlocfilehash: 6996bd56571c75f31893d7df5b8237fc52b378ae
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824082"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Rozwiązywanie problemów: Aktualizator ma błędy podczas pobierania informacji

W rzadkich przypadkach, może zostać wyświetlony błąd komunikat "błąd podczas pobierania zaktualizować informacje o" wyświetlany podczas próby [zaktualizować program Visual Studio dla komputerów Mac](update.md). Jeśli tak się stanie, spróbuj wykonać następujące kroki, aby rozwiązać ten problem:

- Sprawdź połączenie internetowe. Spadek połączenia jest Najczęstszą przyczyną tego błędu.
  - Składnik nie uda się pobrać, po kliknięciu przycisku ponów obok nazwy składnika, aby ponownie spróbować pobrać pliki.
- Uruchom ponownie środowisko IDE.
- Jeśli nadal jest wyświetlany ten komunikat o błędzie, możesz również spróbować zaktualizować przy użyciu programu Visual Studio 2017 for Mac Installer, jeśli **dmg** nadal znajduje się na komputerze, lub możesz ją pobrać z [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%20for%20Mac)
  - Instalator zaktualizuje wszystkie zainstalowane składniki na swojej maszynie.
  - Uruchamiając ponownie Instalatora, będziesz również mieć możliwość zainstalowanie brakujących składników, które nie było wcześniej zainstalowane.
