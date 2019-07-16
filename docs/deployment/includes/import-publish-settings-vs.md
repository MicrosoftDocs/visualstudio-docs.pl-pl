---
ms.openlocfilehash: 8adac174fbc78778e7154a205088fb9e9a57ae4a
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "68143552"
---

1. Na komputerze, na którym znajduje się projekt ASP.NET jest otwarty w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Publikuj**.

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko. Kliknij przycisk **Utwórz nowy profil**.

1. W **wybierz lokalizację docelową publikowania** okno dialogowe, kliknij przycisk **Importuj profil**.

    ![Wybierz polecenie Publikuj](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Przejdź do lokalizacji pliku ustawień publikowania, który został utworzony w poprzedniej sekcji.

1. W **Importuj plik ustawień publikowania** okno dialogowe, przejdź do i wybierz profil, który został utworzony w poprzedniej sekcji i kliknij **Otwórz**.

    Visual Studio rozpoczyna proces wdrażania, a następnie w oknie danych wyjściowych Pokazuje postęp i wyniki.

    Jeśli wszystkie wdrożenia występują błędy, kliknij przycisk **ustawienia** Aby edytować ustawienia. Zmodyfikuj ustawienia i kliknij przycisk **weryfikacji** do testowania nowych ustawień. Jeśli nazwa hosta nie zostanie znaleziony, spróbuj adres IP zamiast nazwy hosta w **serwera** i **docelowy adres URL** pola.

    ![Edytuj ustawienia w narzędziu do publikowania](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
