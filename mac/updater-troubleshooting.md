---
title: Podczas pobierania informacji występują błędy aktualizatora
description: Instrukcje dotyczące naprawy po wyświetleniu błędu "Błąd podczas pobierania informacji o aktualizacji". w programie Visual Studio 2019 dla komputerów Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405477"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Rozwiązywanie problemów: Updater ma błędy pobierania informacji

W rzadkich przypadkach podczas próby aktualizacji programu Visual Studio dla komputerów [Mac](update.md)może zostać wyświetlony komunikat o błędzie "Informacje o błędzie podczas pobierania aktualizacji". Jeśli tak się stanie, spróbuj wykonać następujące czynności, aby to naprawić:

- Sprawdź połączenie internetowe. Spadek połączenia jest najczęstszą przyczyną tego błędu.
  - Jeśli nie można pobrać składnika, można kliknąć przycisk ponowienia próby obok nazwy składnika, aby spróbować pobrać ponownie.
- Uruchom ponownie ide.
- Jeśli ten komunikat o błędzie nadal jest wyświetlany, możesz również spróbować zaktualizować go za pomocą Instalatora, jeśli **plik dmg** nadal znajduje się na komputerze lub można go pobrać z [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - Instalator zaktualizuje wszystkie zainstalowane składniki na komputerze.
  - Po ponownym uruchomieniu instalatora można również zainstalować brakujące składniki, które nie zostały wcześniej zainstalowane.
- Możesz również spróbować wyczyścić pliki do pobrania w pamięci podręcznej, usuwając plik znajdujący się pod adresem `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`.
- Jeśli pracujesz ze starszą wersją programu Visual Studio dla komputerów `VisualStudio` Mac, w katalogu mogą znajdować się inne numery wersji. Usuń `index.xml` również plik w tych ścieżkach.
