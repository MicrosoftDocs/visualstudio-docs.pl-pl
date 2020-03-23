---
ms.openlocfilehash: 8adac174fbc78778e7154a205088fb9e9a57ae4a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143552"
---

1. Na komputerze, na którym projekt ASP.NET jest otwarty w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz polecenie **Publikuj**.

1. Jeśli wcześniej skonfigurowano profile publikowania, zostanie wyświetlone okienko **Publikowania.** Kliknij **pozycję Utwórz nowy profil**.

1. W oknie **dialogowym Wybieranie celu publikacji** kliknij pozycję **Importuj profil**.

    ![Wybierz pozycję Publikuj](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Przejdź do lokalizacji pliku ustawień publikowania utworzonego w poprzedniej sekcji.

1. W oknie dialogowym **Importowanie ustawień publikowania** przejdź do profilu utworzonego w poprzedniej sekcji i wybierz go, a następnie kliknij przycisk **Otwórz**.

    Visual Studio rozpoczyna proces wdrażania, a okno Dane wyjściowe pokazuje postęp i wyniki.

    Jeśli zostanie wyświetlony błąd wdrożenia, kliknij pozycję **Ustawienia,** aby edytować ustawienia. Modyfikuj ustawienia i kliknij przycisk **Sprawdź poprawność,** aby przetestować nowe ustawienia. Jeśli nazwa hosta nie zostanie znaleziona, spróbuj użyć adresu IP zamiast nazwy hosta w polach **Serwer** i **Docelowy adres URL.**

    ![Edytowanie ustawień w narzędziu Publikowanie](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
