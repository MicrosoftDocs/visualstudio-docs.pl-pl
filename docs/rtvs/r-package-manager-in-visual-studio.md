---
title: Menedżer pakietów dla języka R
description: Jak używać Menedżera pakietów języka R w Visual Studio, aby zainstalować i R Menedżera pakietów.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 495ee638e954c2f99f0ac3273edf67dc48991451
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846655"
---
# <a name="package-manager"></a>Menedżer pakietów

R Tools for Visual Studio (RTVS) Menedżera pakietów jest interfejsem użytkownika do zarządzania pakietami języka R. Aby go otworzyć, wybierz **R Tools** > **Windows** > **pakietów** lub naciskając **Ctrl** + **7**.

Menedżer pakietów zawiera trzy karty. Każda karta zawiera listę odpowiednich pakietów po lewej stronie, i szczegółowe informacje dotyczące wybranego pakietu po prawej stronie, w tym wersja pakietu, opis i licencji, zainstaluj lokalizacji i łącza do innych istotnych informacji. Pole wyszukiwania w prawym górnym rogu umożliwia filtrowanie listy.

> [!Tip]
> Termin w polu wyszukiwania pozostaje, jak przełączać się między kartami.

- **Dostępne** pozwala przeglądać pakiety do zainstalowania. Jeśli pakiet jest już zainstalowany, **zainstalować** przycisk po prawej stronie zmienia się **Odinstaluj**.

    ![Dostępne pakiety karcie R Tools for Visual Studio Menedżera pakietów](media/package-manager-available.png)

- **Zainstalowane** pokazuje wszystkie zainstalowane i ładowane pakietów. Zieloną kropkę obok pakietu wskazuje, że jest załadowany do sesji języka R. Czerwona X ikonę na liście po lewej stronie lub **Odinstaluj** przycisk po prawej stronie można odinstalować pakiet. Jeśli dostępna jest nowsza wersja zainstalowanego pakietu, niebieski Strzałka w prawo pakietu w górę przeprowadza aktualizację.

    ![Zainstalowane pakiety kartę w R Tools for Visual Studio Menedżera pakietów](media/package-manager-installed.png)

- **Załadowano** wyświetla tylko te pakiety, które są ładowane do sesji języka R, które są wyświetlane z zieloną kropkę. Możesz również odinstalować i aktualizowanie pakietów w tym miejscu.

    ![Załadowano karcie pakiety R Tools for Visual Studio Menedżera pakietów](media/package-manager-loaded.png)

## <a name="package-locations"></a>Lokalizacje pakietów

Pakiety są instalowane w następujących lokalizacjach:

- Pakietami podstawowymi, które są dołączone RTVS są zainstalowane w *C:\Program Files\Microsoft\R Client\R_SERVER\library*
- Dodatkowe pakiety są instalowane na *%userprofile%\Documents\R\win-library\3.3*
