---
ms.openlocfilehash: 94c2c733b631ef5e727c79a6e093bb224aec38c4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249866"
---

1. Na komputerze, na którym jest otwarty projekt ASP.NET w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Publikuj**.

   Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okienko **Publikowanie** . Kliknij pozycję **Nowy** lub **Utwórz nowy profil**.

1. Wybierz opcję importowania profilu.

   ::: moniker range=">=vs-2019"
   W oknie dialogowym **Publikowanie** kliknij pozycję **Importuj profil**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   W oknie dialogowym **Wybierz cel publikacji** kliknij przycisk **Importuj profil**.
   ::: moniker-end

   ![Wybierz pozycję Publikuj](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Przejdź do lokalizacji pliku ustawień publikowania, który został utworzony w poprzedniej sekcji.

1. W oknie dialogowym **Importowanie pliku ustawień publikowania** przejdź do i wybierz profil, który został utworzony w poprzedniej sekcji, a następnie kliknij przycisk **Otwórz**.

   ::: moniker range=">=vs-2019"
   Kliknij przycisk **Zakończ** , aby zapisać profil publikowania, a następnie kliknij przycisk **Publikuj**.

   Program Visual Studio rozpocznie proces wdrażania, a okno dane wyjściowe pokazuje postęp i wyniki.

   Jeśli pojawią się jakiekolwiek błędy wdrażania, kliknij przycisk **Edytuj** , aby edytować ustawienia. Zmodyfikuj ustawienia i kliknij przycisk **Weryfikuj** , aby przetestować nowe ustawienia. Jeśli nazwa hosta nie zostanie znaleziona, spróbuj użyć adresu IP zamiast nazwy hosta w polach **serwer** i **docelowy adres URL** .
   ::: moniker-end
   ::: moniker range="vs-2017"
   Program Visual Studio rozpocznie proces wdrażania, a okno dane wyjściowe pokazuje postęp i wyniki.

   Jeśli wystąpią jakieś błędy wdrażania, kliknij przycisk **Ustawienia** , aby edytować ustawienia. Zmodyfikuj ustawienia i kliknij przycisk **Weryfikuj** , aby przetestować nowe ustawienia. Jeśli nazwa hosta nie zostanie znaleziona, spróbuj użyć adresu IP zamiast nazwy hosta w polach **serwer** i **docelowy adres URL** .
   ::: moniker-end

   ![Edytuj ustawienia w narzędziu do publikowania](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
