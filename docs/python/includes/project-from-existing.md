---
ms.topic: include
ms.openlocfilehash: 47c390fbc7a6f84c25d4bde0317985bd149cae2f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429094"
---
1. Uruchom program Visual Studio i wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** okno dialogowe, wyszukaj "Python", wybierz **kodu z istniejących Python** szablonu, należy nadać projektowi nazwę i lokalizację, a następnie wybierz pozycję **OK**.

1. W oknie kreatora należy ustawić ścieżkę do istniejącego kodu, ustawić filtr dla typów plików i określić wszelkie ścieżki wyszukiwania, które projektu wymaga, a następnie wybierz **dalej**. Jeśli nie wiesz, jakie wyszukiwania ścieżki, pozostaw to pole puste.

    ![Nowy projekt z istniejącego kodu, krok 1](../media/projects-from-existing-1.png)

1. W następnym oknie dialogowym Wybierz plik startowy dla projektu i wybierz **dalej**. (Jeśli to konieczne, wybierz środowisko; w przeciwnym razie Zaakceptuj ustawienia domyślne.) Należy pamiętać, że okno dialogowe zawiera tylko pliki w folderze głównym; Jeśli plik ma znajduje się w podfolderze, pozostaw pusty plik startowy i ustaw ją później w **Eksploratora rozwiązań** (opisanych poniżej).

    ![Nowy projekt z istniejącego kodu, krok 2](../media/projects-from-existing-2.png)

1. Wybierz lokalizację, w której chcesz zapisać plik projektu (czyli *.pyproj* pliku na dysku). Jeśli to konieczne, możesz również obejmować automatyczne wykrywanie środowisk wirtualnych i dostosować projekt dla innej witryny sieci web platform. Jeśli masz pewności co do tych opcji, należy pozostawić je ustawiane na wartości domyślne.

    ![Nowy projekt z istniejącego kodu, krok 3](../media/projects-from-existing-3.png)

1. Wybierz **Zakończ** i Visual Studio tworzy projekt i otworzy go w **Eksploratora rozwiązań**. Jeśli chcesz przenieść *.pyproj* pliku w innym miejscu, wybierz je w **Eksploratora rozwiązań** i wybierz polecenie **pliku** > **Zapisz jako**. Ta akcja aktualizacji odwołania do pliku w projekcie, ale nie przenosi wszystkie pliki kodu.

1. Aby ustawić innego pliku startowego, zlokalizuj plik w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy, a następnie wybierz **Ustaw jako plik startowy**.