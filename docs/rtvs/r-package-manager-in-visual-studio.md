---
title: Menedżer pakietów dla R
description: Jak używać menedżera pakietów języka R w programie Visual Studio do instalowania i ładki pakietów języka R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d35bfd45e862912ff78ae600eed01ce8dc002493
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62998859"
---
# <a name="package-manager"></a>Menedżer pakietów

Menedżer pakietów R Tools for Visual Studio (RTVS) jest interfejsem użytkownika do zarządzania pakietami języka R. Aby go otworzyć, wybierz **pozycję R Tools** > **Windows** > **Packages** lub klawisz **Ctrl**+**7**.

Menedżer pakietów ma trzy karty. Każda karta wyświetla listę odpowiednich pakietów po lewej stronie i szczegółowe informacje dotyczące wybranego pakietu po prawej stronie, w tym wersję pakietu, opis, licencję, lokalizację instalacji i łącza do innych istotnych informacji. Pole wyszukiwania w prawym górnym rogu umożliwia filtrowanie listy.

> [!Tip]
> Termin w polu wyszukiwania pozostaje w mocy podczas przełączania między kartami.

- **Dostępne** umożliwia przeglądanie pakietów do zainstalowania. Jeśli pakiet jest już zainstalowany, przycisk **Zainstaluj** po prawej stronie zmieni się na **Odinstaluj**.

    ![Karta Dostępne pakiety w menedżerze pakietów Narzędzia języka R dla programu Visual Studio](media/package-manager-available.png)

- **Zainstalowany** pokazuje wszystkie zainstalowane i załadowane pakiety. Zielona kropka obok pakietu wskazuje, że jest ładowany do sesji R. Do odinstalowania pakietu można użyć czerwonej ikony X na liście po lewej stronie lub przycisku **Odinstaluj** po prawej stronie. Jeśli dostępna jest nowsza wersja zainstalowanego pakietu, niebieska strzałka w górę po prawej stronie pakietu wykonuje aktualizację.

    ![Karta Zainstalowane pakiety w menedżerze pakietów Narzędzia języka R dla programu Visual Studio](media/package-manager-installed.png)

- **Załadowane** wyświetla tylko te pakiety, które są ładowane do sesji R, z których wszystkie są wyświetlane z zieloną kropką. Możesz również odinstalować i zaktualizować pakiety tutaj.

    ![Karta Ładowane pakiety w menedżerze pakietów narzędzia języka R dla programu Visual Studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Lokalizacje pakietów

Pakiety są instalowane w następujących lokalizacjach:

- Pakiety podstawowe dołączone do RTVS są instalowane w *folderze C:\Program Files\Microsoft\R Client\R_SERVER\library*
- Dodatkowe pakiety są instalowane na *%userprofile%\Documents\R\win-library\3.3*
