---
title: Podczas pobierania informacji występują błędy aktualizatora
description: Instrukcje dotyczące naprawy po wyświetleniu błędu "Błąd podczas pobierania informacji o aktualizacji". w programie Visual Studio 2017 dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 8825BBAD-65C0-480F-9868-A01E64F28250
ms.openlocfilehash: 2ff0703171f5854baed2dd9be3767571a930bcb7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983484"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Rozwiązywanie problemów: Updater ma błędy pobierania informacji

W rzadkich przypadkach podczas próby aktualizacji programu Visual Studio dla komputerów [Mac](update.md)może zostać wyświetlony komunikat o błędzie "Informacje o błędzie podczas pobierania aktualizacji". Jeśli tak się stanie, spróbuj wykonać następujące czynności, aby to naprawić:

- Sprawdź połączenie internetowe. Spadek połączenia jest najczęstszą przyczyną tego błędu.
  - Jeśli nie można pobrać składnika, można kliknąć przycisk ponowienia próby obok nazwy składnika, aby spróbować pobrać ponownie.
- Uruchom ponownie ide.
- Jeśli ten komunikat o błędzie nadal jest wyświetlany, możesz również spróbować zaktualizować za pomocą programu Visual Studio 2017 dla mac Installer, jeśli **plik dmg** jest nadal na komputerze lub można go pobrać z [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%20for%20Mac)
  - Instalator zaktualizuje wszystkie zainstalowane składniki na komputerze.
  - Po ponownym uruchomieniu instalatora można również zainstalować brakujące składniki, które nie zostały wcześniej zainstalowane.
