---
ms.openlocfilehash: f286002112667ba763419f0e3d6265dbe1942212
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173893"
---

1. Na komputerze, na którym jest otwarty projekt ASP.NET w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Publikuj**.

1. Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okienko **Publikowanie** . Kliknij pozycję **Utwórz nowy profil**.

1. W oknie dialogowym **Wybierz cel publikacji** kliknij przycisk **Importuj profil**.

    ![Wybierz pozycję Publikuj](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Przejdź do lokalizacji pliku ustawień publikowania, który został utworzony w poprzedniej sekcji.

1. W oknie dialogowym **Importowanie pliku ustawień publikowania** przejdź do i wybierz profil, który został utworzony w poprzedniej sekcji, a następnie kliknij przycisk **Otwórz**.

    Program Visual Studio rozpocznie proces wdrażania, a okno dane wyjściowe pokazuje postęp i wyniki.

    Jeśli wystąpią jakieś błędy wdrażania, kliknij przycisk **Ustawienia** , aby edytować ustawienia. Zmodyfikuj ustawienia i kliknij przycisk **Weryfikuj** , aby przetestować nowe ustawienia. Jeśli nazwa hosta nie zostanie znaleziona, spróbuj użyć adresu IP zamiast nazwy hosta w polach **serwer** i **docelowy adres URL** .

    ![Edytuj ustawienia w narzędziu do publikowania](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
